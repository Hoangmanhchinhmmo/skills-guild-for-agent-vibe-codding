# Milestone 2: Core Features — Auth, Admin, Payments & More

> **Prerequisites:** Milestone 1 complete — Next.js storefront, Express API, MongoDB Atlas, and Stripe checkout all working.
>
> **What you'll build:** User accounts with OAuth, order management, a full admin dashboard, coupons, product reviews, two additional payment gateways, and automated email notifications.

---

## Phase 2.1: Authentication + OAuth

**What you'll get:** A complete login system — email/password registration, Google and Facebook sign-in buttons, password reset flow, and protected pages that redirect unauthenticated visitors to the login screen. Users get a profile page to manage their info.

**Skills to activate:**
- `/auth-implementation-patterns`
- `/clerk-auth`

**Prompt to use:**
> /auth-implementation-patterns
> /clerk-auth
>
> Set up Clerk authentication for my existing Next.js + Express e-commerce app. Here is exactly what I need:
>
> **Clerk Setup:**
> - Install @clerk/nextjs and configure it with environment variables (NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY, CLERK_SECRET_KEY).
> - Wrap the app in ClerkProvider in layout.tsx.
> - Create middleware.ts to define public routes (home, product listing, product detail, API webhooks) and protected routes (cart, checkout, order history, profile).
>
> **Auth Pages:**
> - Create /sign-in and /sign-up pages using Clerk's prebuilt components (<SignIn /> and <SignUp />).
> - Configure OAuth providers: enable Google and Facebook sign-in in the Clerk component appearance settings.
> - Add a forgot password flow (Clerk handles this automatically, but make sure the sign-in page shows the "Forgot password?" link).
>
> **Protected Routes:**
> - /cart, /checkout, /orders, /profile — redirect to /sign-in if not authenticated.
> - In middleware.ts, use clerkMiddleware() with createRouteMatcher to protect these paths.
>
> **User Profile Page:**
> - Create /profile page that shows the user's name, email, profile picture, and order count.
> - Use Clerk's useUser() hook to get user data.
> - Add an "Edit Profile" section using Clerk's <UserProfile /> component.
>
> **Backend Integration:**
> - On the Express API, install @clerk/express and add clerkMiddleware() to verify tokens.
> - Create a requireAuth middleware that checks req.auth.userId and returns 401 if missing.
> - Apply requireAuth to POST /api/orders, GET /api/orders/my-orders, and all cart API routes.
> - When a new user signs up, use Clerk webhooks to create a user document in MongoDB with fields: clerkId, email, name, role (default "customer"), createdAt.
>
> **Navigation Bar Update:**
> - Show "Sign In" / "Sign Up" buttons when logged out.
> - Show user avatar + dropdown (Profile, My Orders, Sign Out) when logged in.
>
> My existing stack: Next.js 14 app router, Express.js API on port 5000, MongoDB with Mongoose, Stripe checkout already working.

**Checkpoint:**
- [ ] Can register a new account with email and password
- [ ] Can sign in with Google OAuth
- [ ] Visiting /checkout while logged out redirects to /sign-in
- [ ] After signing in, redirected back to the page you were trying to visit
- [ ] Profile page shows user info and lets you edit name/avatar
- [ ] Express API returns 401 when calling protected endpoints without a valid token
- [ ] New user document created in MongoDB after first sign-up

**Troubleshooting:**
- Clerk components not rendering → Make sure `ClerkProvider` wraps the entire app in the root `layout.tsx`, not inside a nested layout
- OAuth buttons not appearing → Enable Google and Facebook providers in the Clerk Dashboard under "User & Authentication > Social Connections"
- 401 errors on API calls after login → Confirm the frontend sends the token via `getToken()` from `useAuth()` and the backend verifies it with `@clerk/express` middleware
- Webhook not creating user in MongoDB → Check that the Clerk webhook endpoint URL is correct in the Clerk Dashboard, and the route is listed as a public route in your Next.js middleware

---

## Phase 2.2: Order Management

**What you'll get:** After a successful Stripe payment, an order is automatically created in the database. Customers see their full order history with real-time status tracking. Each order moves through a clear lifecycle: pending, confirmed, shipped, delivered.

**Skills to activate:**
- `/nodejs-backend-patterns`

**Prompt to use:**
> /nodejs-backend-patterns
>
> Build a complete order management system for my e-commerce app. The app uses Express.js, MongoDB with Mongoose, Clerk auth, and Stripe checkout (already working). Here is what I need:
>
> **Order Model (Mongoose):**
> ```
> Order {
>   orderNumber: String (auto-generate like "ORD-20260320-XXXX"),
>   userId: String (Clerk user ID),
>   items: [{
>     productId: ObjectId (ref Product),
>     name: String,
>     price: Number,
>     quantity: Number,
>     image: String
>   }],
>   subtotal: Number,
>   discount: Number (default 0),
>   shipping: Number,
>   total: Number,
>   status: String (enum: "pending", "confirmed", "shipped", "delivered", "cancelled"),
>   paymentMethod: String,
>   paymentId: String (Stripe payment intent ID),
>   shippingAddress: {
>     fullName: String,
>     address: String,
>     city: String,
>     state: String,
>     zipCode: String,
>     country: String,
>     phone: String
>   },
>   statusHistory: [{ status: String, date: Date, note: String }],
>   createdAt: Date,
>   updatedAt: Date
> }
> ```
>
> **Stripe Webhook Update:**
> - Modify the existing Stripe webhook handler for checkout.session.completed.
> - When payment succeeds: create an Order document with status "confirmed", save all cart items into the order, clear the user's cart, and record the payment ID.
> - Store the Clerk userId in the Stripe checkout session metadata so the webhook can link the order to the user.
>
> **API Endpoints (all require auth except webhook):**
> - GET /api/orders/my-orders — return current user's orders sorted by newest first, with pagination (page, limit query params).
> - GET /api/orders/:id — return a single order (only if it belongs to the current user OR the user is admin).
> - PATCH /api/orders/:id/status — admin only: update order status, push to statusHistory array with timestamp and optional note.
> - GET /api/orders/admin/all — admin only: return all orders with filters (status, date range), sorting, and pagination.
>
> **Frontend Pages (Next.js):**
> - /orders — Order history page showing a list of order cards. Each card shows: order number, date, status badge (color-coded: pending=yellow, confirmed=blue, shipped=purple, delivered=green, cancelled=red), item count, total amount, and a "View Details" button.
> - /orders/[id] — Order detail page showing: order number, placed date, status badge, status timeline (visual stepper showing all status transitions with dates), shipping address, list of items with images, and price breakdown (subtotal, discount, shipping, total).
> - After successful Stripe checkout, redirect to /orders/[newOrderId] showing "Order Confirmed!" with confetti or a success animation.
>
> My existing Stripe webhook is at POST /api/webhooks/stripe. Products are in a Product model with fields: name, price, images, description, category, stock.

**Checkpoint:**
- [ ] After completing a Stripe payment, a new order appears in MongoDB with status "confirmed"
- [ ] /orders page shows all past orders for the logged-in user
- [ ] /orders/[id] shows full order details with a status timeline
- [ ] Cart is cleared after successful payment
- [ ] Order number is auto-generated and unique
- [ ] Unauthenticated users cannot access /orders

**Troubleshooting:**
- Order not created after payment → Check Stripe webhook logs in the Stripe Dashboard for errors; ensure `userId` is included in `checkout.session.metadata` when creating the session
- Order shows "pending" instead of "confirmed" → The webhook might be failing silently; add try/catch logging inside the webhook handler and verify the signing secret matches
- Duplicate orders → Add an idempotency check using the Stripe `paymentIntentId` — if an order with that payment ID already exists, skip creation
- Items missing from order → Make sure you are reading items from the cart (or Stripe line items) at webhook time, not from the request body

---

## Phase 2.3: Admin Dashboard

**What you'll get:** A polished, colorful admin panel at /admin with a sidebar, revenue charts, order management table, and full product CRUD with image upload via Cloudinary. The dashboard uses bold colors and data-rich cards to give you a birds-eye view of your store.

**Skills to activate:**
- `/react-nextjs-development`
- `/tailwind-patterns`

**Prompt to use:**
> /react-nextjs-development
> /tailwind-patterns
>
> Build a complete admin dashboard for my e-commerce app at /admin. I use Next.js 14 app router, Tailwind CSS, Express API on port 5000, MongoDB, and Clerk auth. Only users with role "admin" in the MongoDB user document should access /admin routes. Here is the full specification:
>
> **Access Control:**
> - Create a Next.js middleware or layout check: fetch the user's role from the API using their Clerk token. If role !== "admin", redirect to /.
> - Create an Express middleware isAdmin that checks the user's role in MongoDB before allowing admin API routes.
>
> **Layout — /admin/layout.tsx:**
> - Fixed left sidebar (width 260px, dark background #1e1e2d) with:
>   - Store logo at the top
>   - Nav links with icons: Dashboard, Products, Orders, Coupons (for Phase 2.4), Customers
>   - Active link highlighted with a gradient left border (blue to purple)
>   - User avatar and "Sign Out" at the bottom
> - Main content area with a light gray background (#f5f5f9) and top header bar showing page title and admin name.
>
> **Dashboard Page — /admin (default):**
> - Top row: 4 stat cards in a grid, each with a bold colored icon background:
>   - Total Revenue (green icon bg, dollar sign icon) — sum of all orders
>   - Total Orders (blue icon bg, shopping bag icon) — count of all orders
>   - Total Customers (purple icon bg, users icon) — count of all users
>   - Pending Orders (orange icon bg, clock icon) — orders with status "pending" or "confirmed"
> - Middle row: Revenue chart (line chart, last 30 days, gradient fill under the line in blue-to-purple). Use recharts library. X-axis = dates, Y-axis = revenue.
> - Bottom row split into two columns:
>   - Left (60%): Recent Orders table — last 10 orders showing order number, customer name, total, status badge (color-coded), date. Each row clickable to go to order detail.
>   - Right (40%): Top 5 Products card — list showing product image thumbnail, name, units sold, and revenue. Ordered by revenue descending.
> - All cards should have white backgrounds, subtle shadows (shadow-md), rounded corners (rounded-xl), and generous padding.
>
> **API Endpoints for Dashboard:**
> - GET /api/admin/stats — returns totalRevenue, totalOrders, totalCustomers, pendingOrders.
> - GET /api/admin/revenue-chart — returns array of { date, revenue } for the last 30 days, aggregated from orders using MongoDB aggregation pipeline.
> - GET /api/admin/top-products — returns top 5 products by revenue.
>
> **Products Management — /admin/products:**
> - Table view with columns: Image (thumbnail), Name, Price, Stock, Category, Actions (Edit, Delete).
> - "Add Product" button (top right, gradient blue-purple button) opens /admin/products/new.
> - /admin/products/new and /admin/products/[id]/edit — Product form with fields:
>   - Name (text input)
>   - Description (textarea)
>   - Price (number input)
>   - Stock (number input)
>   - Category (dropdown select)
>   - Images (drag-and-drop upload area, max 5 images)
> - Image upload to Cloudinary: install cloudinary and multer. Create POST /api/admin/upload endpoint that accepts an image, uploads to Cloudinary, and returns the URL. On the frontend, show upload preview and progress bar.
> - Delete product with confirmation modal.
>
> **API Endpoints for Products:**
> - GET /api/admin/products — all products with pagination, search by name, filter by category.
> - POST /api/admin/products — create product.
> - PUT /api/admin/products/:id — update product.
> - DELETE /api/admin/products/:id — delete product.
> - POST /api/admin/upload — upload image to Cloudinary and return URL.
>
> **Orders Management — /admin/orders:**
> - Table with columns: Order Number, Customer, Items Count, Total, Status (dropdown to change), Date, Actions (View).
> - Status dropdown lets admin change status directly from the table — when changed, call PATCH /api/orders/:id/status.
> - Status badges: pending (bg-yellow-100 text-yellow-800), confirmed (bg-blue-100 text-blue-800), shipped (bg-purple-100 text-purple-800), delivered (bg-green-100 text-green-800), cancelled (bg-red-100 text-red-800).
> - Filter bar at the top: filter by status (multi-select), date range picker, search by order number.
>
> **Customers Page — /admin/customers:**
> - Table showing: Avatar, Name, Email, Total Orders, Total Spent, Join Date.
> - Click a customer row to see their order history.
>
> **Style Guidelines:**
> - Use Tailwind CSS exclusively, no other CSS framework.
> - Bold and vibrant color palette: primary gradient (from-blue-600 to-purple-600), success green-500, warning amber-500, danger red-500.
> - All tables should have hover row highlight (hover:bg-gray-50), striped rows are optional.
> - Use lucide-react for all icons.
> - Add subtle entrance animations using Tailwind animate classes or framer-motion for stat cards loading.
>
> Install recharts, lucide-react, cloudinary, multer, and any needed dependencies.

**Checkpoint:**
- [ ] /admin is only accessible by admin users — regular users are redirected
- [ ] Dashboard shows 4 stat cards with real data from the database
- [ ] Revenue chart renders a line chart for the last 30 days
- [ ] Can create a new product with images uploaded to Cloudinary
- [ ] Can edit an existing product and see changes on the storefront
- [ ] Can delete a product with confirmation
- [ ] Can change an order's status from the orders table
- [ ] Recent orders and top products sections display real data

**Troubleshooting:**
- Admin page accessible by non-admin users → Verify the role check runs in the layout.tsx server component before rendering children; the API must also validate on every admin endpoint
- Cloudinary upload fails → Check that CLOUDINARY_CLOUD_NAME, CLOUDINARY_API_KEY, and CLOUDINARY_API_SECRET are set in your Express .env file; test the upload endpoint directly with Postman
- Revenue chart shows no data → Ensure orders exist in the database with a `createdAt` field; check the MongoDB aggregation pipeline groups by day correctly using `$dateToString`
- Stat cards show 0 → The aggregation queries might be filtering out orders unintentionally; remove status filters during development to confirm data exists
- Images not displaying after upload → Make sure the Cloudinary URL is saved to the product's `images` array in MongoDB, and the frontend reads from the correct field

---

## Phase 2.4: Coupon & Discount System

**What you'll get:** Admins can create discount coupons from the dashboard. Customers enter a coupon code at checkout, the discount is validated server-side, and the total adjusts in real time. Supports both percentage-off and fixed-amount discounts with expiry dates and minimum order requirements.

**Skills to activate:**
- `/nodejs-backend-patterns`

**Prompt to use:**
> /nodejs-backend-patterns
>
> Build a coupon and discount system for my e-commerce app. Stack: Express.js, MongoDB/Mongoose, Next.js 14 frontend, Clerk auth. Here is what I need:
>
> **Coupon Model (Mongoose):**
> ```
> Coupon {
>   code: String (unique, uppercase, trimmed),
>   type: String (enum: "percentage", "fixed"),
>   value: Number (e.g., 10 for 10% or 10 for $10 off),
>   minOrderAmount: Number (default 0),
>   maxDiscount: Number (only for percentage type, caps the discount amount),
>   expiresAt: Date,
>   usageLimit: Number (total times this coupon can be used, 0 = unlimited),
>   usedCount: Number (default 0),
>   isActive: Boolean (default true),
>   createdAt: Date
> }
> ```
>
> **Admin API Endpoints (all require admin auth):**
> - GET /api/admin/coupons — list all coupons with pagination.
> - POST /api/admin/coupons — create a new coupon.
> - PUT /api/admin/coupons/:id — update a coupon.
> - DELETE /api/admin/coupons/:id — delete a coupon.
> - PATCH /api/admin/coupons/:id/toggle — toggle isActive on/off.
>
> **Customer API Endpoint:**
> - POST /api/coupons/validate — accepts { code, subtotal }. Validates the coupon:
>   1. Check if coupon exists and isActive is true.
>   2. Check if it has not expired (expiresAt > now).
>   3. Check if usageLimit is 0 or usedCount < usageLimit.
>   4. Check if subtotal >= minOrderAmount.
>   5. Calculate discount: if type is "percentage", discount = subtotal * value / 100 (capped at maxDiscount if set). If type is "fixed", discount = value.
>   6. Return { valid: true, discount, newTotal: subtotal - discount, message: "Coupon applied!" } or { valid: false, message: "reason" }.
>
> **Checkout Integration:**
> - On the checkout page, add a "Have a coupon?" collapsible section above the order summary.
> - Input field for coupon code + "Apply" button.
> - When applied: show the discount as a line item in the price breakdown (Subtotal, Discount: -$X.XX in green, Shipping, Total).
> - If invalid, show the error message in red below the input.
> - Pass the coupon code and discount amount to the Stripe checkout session metadata.
> - In the Stripe webhook (order creation), read the coupon from metadata, increment the coupon's usedCount, and save the discount amount on the order.
>
> **Admin Dashboard — /admin/coupons page:**
> - Table with columns: Code, Type, Value, Min Order, Expires, Used/Limit, Status (active badge green / inactive badge gray), Actions (Edit, Toggle, Delete).
> - "Create Coupon" button opens a modal or /admin/coupons/new page with the form.
> - Expired coupons should show a red "Expired" badge automatically.
>
> Make sure all validation happens server-side. The frontend discount display is just for UX — the actual discount is recalculated and verified in the webhook/order creation.

**Checkpoint:**
- [ ] Can create a coupon in the admin dashboard with all fields
- [ ] Entering a valid coupon code at checkout shows the discount in the price breakdown
- [ ] Entering an expired or invalid coupon shows a clear error message
- [ ] Discount is correctly saved on the order after payment
- [ ] Coupon usedCount increments after a successful order
- [ ] Percentage coupons respect the maxDiscount cap

**Troubleshooting:**
- Coupon code not found → Ensure the code is converted to uppercase both when saving and when querying; use `.toUpperCase().trim()` on both sides
- Discount not reflected in Stripe amount → Remember Stripe calculates the total from line items; pass the coupon as a Stripe coupon object or adjust the line item amounts before creating the session
- usedCount not incrementing → The increment must happen in the webhook handler after order creation, not in the validate endpoint; use `$inc: { usedCount: 1 }` in a Mongoose updateOne
- Coupon applied but order shows no discount → Confirm the webhook reads `session.metadata.couponCode` and `session.metadata.discountAmount` and saves them to the Order document

---

## Phase 2.5: Product Reviews & Ratings

**What you'll get:** Customers who purchased a product can leave a star rating (1-5) and a written review. Product cards show the average rating with stars. The product detail page has a review section with pagination. Only verified purchasers can submit reviews.

**Skills to activate:**
- `/nodejs-backend-patterns`
- `/react-nextjs-development`

**Prompt to use:**
> /nodejs-backend-patterns
> /react-nextjs-development
>
> Add a product review and rating system to my e-commerce app. Stack: Express.js, MongoDB/Mongoose, Next.js 14, Clerk auth, Tailwind CSS. Here is the full spec:
>
> **Review Model (Mongoose):**
> ```
> Review {
>   productId: ObjectId (ref Product),
>   userId: String (Clerk user ID),
>   userName: String,
>   userAvatar: String,
>   rating: Number (1-5, required),
>   title: String (max 100 chars),
>   comment: String (max 1000 chars),
>   isVerifiedPurchase: Boolean (default true),
>   createdAt: Date
> }
> ```
> Add a compound unique index on { productId, userId } so each user can only review a product once.
>
> **Update Product Model:**
> - Add fields to Product: averageRating (Number, default 0), reviewCount (Number, default 0).
> - After every review create/update/delete, recalculate these using an aggregation pipeline and update the product document.
>
> **API Endpoints:**
> - GET /api/products/:productId/reviews — return reviews for a product with pagination (page, limit). Sort by newest first. Include average rating and count in the response.
> - POST /api/products/:productId/reviews — create a review (requires auth). Before saving, verify the user has a delivered order containing this product. If not, return 403 "You can only review products you have purchased."
> - PUT /api/products/:productId/reviews/:reviewId — update own review.
> - DELETE /api/products/:productId/reviews/:reviewId — delete own review (or admin can delete any).
>
> **Frontend — Product Detail Page Update:**
> - Below the product description, add a "Customer Reviews" section.
> - At the top of the reviews section: show the average rating as large text (e.g., "4.3 out of 5"), filled star icons next to it, and total review count ("Based on 47 reviews").
> - Rating breakdown bar: show a horizontal bar chart — 5 rows, one for each star level (5 stars, 4 stars, ..., 1 star). Each row shows the star label, a progress bar (colored gold, width proportional to percentage), and the count.
> - "Write a Review" button — only visible if the user is logged in and has purchased this product. Opens a form with: star selector (clickable stars that fill on hover), title input, comment textarea, and Submit button.
> - Review list: each review card shows user avatar, name, star rating (filled stars), date (relative like "3 days ago"), "Verified Purchase" badge, title in bold, and comment text.
> - Pagination: "Load More" button at the bottom, loading 10 reviews at a time.
>
> **Frontend — Product Card Update:**
> - On the product listing page, each product card should show the average rating as small stars (filled/empty) and review count text like "(23)" next to the stars.
>
> **Star Component:**
> - Create a reusable StarRating component that accepts a rating value (can be decimal like 4.3) and renders 5 stars — fully filled, partially filled, or empty. Use gold/amber color (#F59E0B). Make it available in both read-only and interactive (clickable) modes.

**Checkpoint:**
- [ ] Only users with a delivered order for that product see the "Write a Review" button
- [ ] Submitting a review updates the product's average rating and review count
- [ ] Product cards on the listing page show star ratings
- [ ] Product detail page shows the rating breakdown bar chart
- [ ] A user cannot review the same product twice (gets an error message)
- [ ] Reviews paginate correctly with "Load More"

**Troubleshooting:**
- "You can only review products you have purchased" when the user did purchase → Ensure the order status check looks for "delivered" specifically and the productId comparison uses `.toString()` on both sides for ObjectId matching
- Average rating not updating → The recalculation function might not be triggered; use a Mongoose post-save hook on the Review model or call the recalculation explicitly after create/update/delete
- Stars not rendering correctly for decimal values (e.g., 4.3) → Use a clip-path or width percentage technique for the partial star; make sure the component handles values between 0 and 5, not just integers
- Duplicate review error not user-friendly → Catch the MongoDB duplicate key error (code 11000) and return a clear message like "You have already reviewed this product"

---

## Phase 2.6: VNPay + PayPal Integration

**What you'll get:** Customers can choose between three payment methods at checkout — Stripe (credit card), VNPay (for the Vietnam market), and PayPal. All three flow into the same order management system with unified status tracking.

**Skills to activate:**
- `/payment-integration`
- `/paypal-integration`

**Prompt to use:**
> /payment-integration
> /paypal-integration
>
> Add VNPay and PayPal payment methods alongside my existing Stripe checkout. Stack: Express.js, MongoDB/Mongoose, Next.js 14, Clerk auth. The current flow: user clicks checkout → Stripe session created → redirect to Stripe → webhook creates order. I need the same flow pattern for VNPay and PayPal. Here is the full spec:
>
> **Checkout Page Update:**
> - Replace the single "Pay with Stripe" button with a payment method selector.
> - Show 3 options as styled radio cards (each card has the payment logo, name, and a short description):
>   1. Credit/Debit Card (Stripe) — Visa, Mastercard logo icons
>   2. VNPay — VNPay logo, text: "Pay with Vietnamese bank account or e-wallet"
>   3. PayPal — PayPal logo, text: "Pay with your PayPal account"
> - The selected card gets a blue border and checkmark icon.
> - A single "Place Order" button at the bottom triggers the selected payment flow.
>
> **VNPay Integration (Express.js):**
> - Install vnpay or implement manually using VNPay's hash-based redirect API.
> - Environment variables: VNPAY_TMN_CODE, VNPAY_HASH_SECRET, VNPAY_URL (sandbox: https://sandbox.vnpayment.vn/paymentv2/vpcpay.html), VNPAY_RETURN_URL.
> - POST /api/payments/vnpay/create — accepts { orderId, amount, orderDescription, language }. Create a pending order in MongoDB first, then generate the VNPay payment URL with these params: vnp_Version, vnp_Command (pay), vnp_TmnCode, vnp_Amount (amount * 100, VNPay uses VND smallest unit), vnp_CreateDate, vnp_CurrCode (VND), vnp_IpAddr, vnp_Locale, vnp_OrderInfo, vnp_OrderType, vnp_ReturnUrl, vnp_TxnRef (use the MongoDB order ID), vnp_SecureHash (HMAC SHA512). Redirect the user to the generated URL.
> - GET /api/payments/vnpay/return — VNPay redirects here after payment. Verify the secure hash from query params. If vnp_ResponseCode === "00" (success), update the order status to "confirmed" and redirect to /orders/[orderId] with success message. If failed, update order to "cancelled" and redirect with error.
> - GET /api/payments/vnpay/ipn — VNPay's server-to-server notification (IPN). Verify hash, update order status, return { RspCode: "00", Message: "Confirm Success" } to VNPay.
>
> **PayPal Integration (Express.js):**
> - Install @paypal/checkout-server-sdk.
> - Environment variables: PAYPAL_CLIENT_ID, PAYPAL_CLIENT_SECRET, PAYPAL_MODE (sandbox or live).
> - POST /api/payments/paypal/create — create a pending order in MongoDB, then create a PayPal order using the Orders API. Return the PayPal approval URL.
> - POST /api/payments/paypal/capture — after user approves on PayPal, capture the payment. If successful, update order status to "confirmed". Return the order ID.
> - On the frontend, after PayPal approval and capture, redirect to /orders/[orderId].
>
> **Unified Order Flow:**
> - All three payment methods create orders using the same Order model.
> - Save paymentMethod field as "stripe", "vnpay", or "paypal" on the Order.
> - Save the respective payment/transaction ID in the paymentId field.
> - The order status flow remains the same regardless of payment method.
> - If a coupon was applied, pass it through for all three payment methods and apply the discount.
>
> **Currency Handling:**
> - Stripe and PayPal: USD (or your store's base currency).
> - VNPay: VND. If your store uses USD, add a simple conversion note or handle VND pricing separately.
>
> Existing Stripe webhook is at POST /api/webhooks/stripe and creates orders on checkout.session.completed. Keep Stripe working exactly as before.

**Checkpoint:**
- [ ] Checkout page shows three payment method options with logos
- [ ] Can complete a purchase via Stripe (existing flow still works)
- [ ] Can complete a purchase via VNPay (redirects to VNPay sandbox, then back)
- [ ] Can complete a purchase via PayPal (redirects to PayPal sandbox, then back)
- [ ] All three payment methods create orders with the correct paymentMethod field
- [ ] Order history shows orders from all payment methods
- [ ] Coupon discounts apply correctly for all payment methods

**Troubleshooting:**
- VNPay hash verification fails → Ensure you sort the vnp_ parameters alphabetically before hashing, exclude `vnp_SecureHash` and `vnp_SecureHashType` from the hash input, and use HMAC SHA512 (not MD5 or SHA256)
- VNPay returns error code 97 (invalid checksum) → Double-check that VNPAY_HASH_SECRET is correct and the query string encoding matches VNPay's format
- PayPal "INSTRUMENT_DECLINED" error → This happens in sandbox when the test buyer has no funds; use the default sandbox personal account which has a pre-loaded balance
- PayPal capture returns 422 → The order might already be captured; add a check for order status before calling capture
- Orders created but status stuck on "pending" → The return URL handler or IPN might not be updating the order; add logging to both endpoints and verify they are hit

---

## Phase 2.7: Email Notifications

**What you'll get:** Customers automatically receive beautifully branded HTML emails — a welcome email on sign-up, an order confirmation with full details after purchase, and a shipping notification when their order ships. All emails match your store's visual identity.

**Skills to activate:**
- `/email-systems`

**Prompt to use:**
> /email-systems
>
> Set up transactional email notifications for my e-commerce app. Stack: Express.js, MongoDB/Mongoose, Next.js 14, Clerk auth. I want to use Resend (https://resend.com) as the email provider. Here is the full spec:
>
> **Setup:**
> - Install resend package on the Express server.
> - Environment variable: RESEND_API_KEY, EMAIL_FROM (e.g., "MyStore <orders@mystore.com>").
> - Create an email service module at /services/emailService.js with a generic sendEmail function that accepts { to, subject, html }.
>
> **Email Templates:**
> - Create an /emails directory with 3 HTML email template functions. Each template function accepts data and returns an HTML string. All templates should share a consistent layout:
>   - Header: store logo centered, background color matching your brand (use a gradient or solid brand color).
>   - Body: white background, max-width 600px, centered, clean typography.
>   - Footer: store name, address, "You received this email because..." text, unsubscribe link placeholder, social media icons.
>   - Use inline CSS only (for email client compatibility). Mobile-responsive with max-width and percentage widths.
>
> **Template 1 — Welcome Email:**
> - Triggered when: Clerk webhook fires for user.created event.
> - Subject: "Welcome to MyStore! 🎉"
> - Content: greeting with user's first name, a brief welcome message ("Thanks for joining! Explore our collection and find something you love."), a bold CTA button "Start Shopping" linking to the store homepage, and a section showing 3 featured/popular products with images and prices.
> - Data needed: { firstName, email, shopUrl, featuredProducts: [{ name, image, price, url }] }.
>
> **Template 2 — Order Confirmation Email:**
> - Triggered when: an order is created (after successful payment from any method — Stripe/VNPay/PayPal).
> - Subject: "Order Confirmed — #ORD-20260320-XXXX"
> - Content:
>   - Success banner: green background with checkmark icon and "Your order is confirmed!"
>   - Order number and date
>   - Ordered items table: rows with product image (small thumbnail), name, quantity, price
>   - Price breakdown: subtotal, discount (if coupon used, show "Coupon SAVE10: -$5.00"), shipping, total (bold, larger font)
>   - Shipping address block
>   - Payment method used
>   - "View Order" CTA button linking to /orders/[orderId]
>   - "Need help?" section with support email
> - Data needed: { order (full order object with items, totals, address, etc.) }.
>
> **Template 3 — Shipping Update Email:**
> - Triggered when: admin changes order status to "shipped" (in the PATCH /api/orders/:id/status endpoint).
> - Subject: "Your order #ORD-20260320-XXXX has shipped! 📦"
> - Content:
>   - Blue banner with truck/shipping icon and "Your order is on its way!"
>   - Order number
>   - Tracking info section (if tracking number and carrier are provided in the status update note, display them; otherwise show "Tracking information will be updated soon")
>   - List of shipped items with thumbnails
>   - Estimated delivery text (e.g., "Expected delivery: 3-5 business days")
>   - "Track Order" CTA button linking to /orders/[orderId]
> - Data needed: { order, trackingNumber (optional), carrier (optional) }.
>
> **Integration Points:**
> 1. In the Clerk user.created webhook handler: after creating the user in MongoDB, call sendWelcomeEmail(user).
> 2. In the order creation logic (after Stripe webhook, VNPay return, PayPal capture): call sendOrderConfirmationEmail(order).
> 3. In PATCH /api/orders/:id/status: if the new status is "shipped", call sendShippingUpdateEmail(order, trackingNumber, carrier).
>
> **Error Handling:**
> - Wrap all email sends in try/catch. Log errors but never let email failures break the main flow (order creation, status update, etc.).
> - Add a console.log for every email sent: "Email sent: [type] to [email]".
>
> Make sure the emails look professional. Use a clean, modern design with proper spacing, readable fonts (Arial/Helvetica fallback stack), and clear CTAs.

**Checkpoint:**
- [ ] New user registration triggers a welcome email
- [ ] Completing a purchase (any payment method) sends an order confirmation email
- [ ] Admin changing order status to "shipped" sends a shipping notification email
- [ ] Emails render correctly in Gmail, Outlook, and Apple Mail (test with Resend's preview or send to yourself)
- [ ] Email failures do not break the order creation or status update flows
- [ ] All emails include consistent store branding (logo, colors, footer)

**Troubleshooting:**
- Emails not sending → Verify RESEND_API_KEY is correct; check the Resend dashboard for failed sends and error messages
- Emails going to spam → Set up SPF and DKIM records for your domain in the Resend dashboard; avoid spam trigger words in the subject line
- Images not loading in email → Use absolute URLs for all images (full https:// paths), not relative paths; some email clients block images by default, always include alt text
- HTML layout broken in Outlook → Outlook uses Word's rendering engine; use `<table>` layout instead of CSS flexbox/grid for the email structure, and always set `width` attributes on table cells
- Welcome email not triggered → Check that the Clerk webhook for `user.created` is configured and the endpoint URL is reachable; test by creating a new test user

---

## Milestone 2 Complete!

**What you have now:** A full-featured e-commerce store with user accounts, admin panel, 3 payment methods, coupon system, product reviews, and automated emails.

You have built:
- User authentication with email/password and Google/Facebook OAuth
- Complete order lifecycle management with status tracking
- A rich admin dashboard with revenue analytics, product CRUD, and order management
- A coupon and discount system with server-side validation
- Product reviews and ratings from verified purchasers
- Three payment gateways: Stripe, VNPay, and PayPal
- Automated transactional emails for key customer touchpoints

**Next:** [Continue to Milestone 3 — Production Launch](milestone-3-launch.md)
