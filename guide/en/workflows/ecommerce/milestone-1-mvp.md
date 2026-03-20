# Milestone 1: E-Commerce MVP — Browse, Cart & Pay

> **Stack:** Next.js 14 (App Router) + Express.js + MongoDB Atlas + Stripe
> **Deploy:** Vercel (frontend) + Docker (backend)
> **Time estimate:** 8–12 hours across all phases
> **Prerequisite:** You should be comfortable with Claude Code basics — running skills, reviewing generated code, and using the terminal.

---

## Phase 1.1: Project Planning & Setup

**What you'll get:** A fully scaffolded monorepo with a Next.js 14 frontend and an Express.js backend, organized folder structure, shared types, and all core dependencies installed — ready to build on.

**Skills to activate:**
- `/blueprint`
- `/writing-plans`

**Prompt to use:**
> /blueprint
> Plan and scaffold a full-stack e-commerce application with the following architecture:
>
> **Frontend:** Next.js 14 with App Router, TypeScript, Tailwind CSS, and the `src/` directory convention. Include folders for `components/`, `lib/`, `hooks/`, `types/`, and `app/` with route groups for `(shop)` and `(checkout)`.
>
> **Backend:** Express.js with TypeScript in a separate `/server` directory. Include folders for `routes/`, `controllers/`, `models/`, `middleware/`, `config/`, and `utils/`.
>
> **Shared:** A `/shared` directory with TypeScript interfaces for Product, Category, Cart, Order, and User.
>
> Create a root `package.json` with workspaces, install all dependencies, set up `.env.example` files for both frontend and backend with placeholders for `MONGODB_URI`, `STRIPE_SECRET_KEY`, `STRIPE_PUBLISHABLE_KEY`, `NEXT_PUBLIC_API_URL`, and `STRIPE_WEBHOOK_SECRET`.
>
> Add a root `docker-compose.yml` for the backend service. Add scripts: `dev:client`, `dev:server`, `dev` (runs both concurrently). Initialize a `.gitignore` that covers Node, Next.js, and environment files.
>
> The product theme is a bold, colorful Shopify-style storefront — keep that in mind for the folder naming and component planning.

**Checkpoint:**
- [ ] Root folder has `/client` (Next.js), `/server` (Express), and `/shared` directories
- [ ] Running `npm run dev` starts both frontend (port 3000) and backend (port 5000) without errors
- [ ] `.env.example` files exist in both `/client` and `/server` with all required variables
- [ ] `docker-compose.yml` exists at the root and defines the backend service
- [ ] TypeScript compiles cleanly in both projects (`npx tsc --noEmit`)

**Troubleshooting:**
- `npm run dev` fails with missing modules → Run `npm install` at the root first; workspaces should hoist dependencies
- Port 3000 already in use → Kill existing processes with `npx kill-port 3000` or change the port in `next.config.js`
- TypeScript path aliases not resolving → Ensure `tsconfig.json` has `baseUrl` set to `"."` and `paths` mapped correctly

---

## Phase 1.2: MongoDB Atlas + Schema Design

**What you'll get:** A live MongoDB Atlas connection from your Express server and fully defined Mongoose schemas for Products, Categories, Carts, and Orders — with validation rules, indexes, and virtual fields ready for querying.

**Skills to activate:**
- `/database-design`

**Prompt to use:**
> /database-design
> Design and implement MongoDB schemas using Mongoose for an e-commerce application. Connect to MongoDB Atlas using an environment variable `MONGODB_URI`.
>
> Create the following schemas in `/server/models/`:
>
> **Product** (`Product.ts`):
> - `name`: String, required, trimmed, max 200 chars, indexed
> - `slug`: String, unique, auto-generated from name using `slugify`
> - `description`: String, required, max 2000 chars
> - `price`: Number, required, min 0, stored in cents (integer)
> - `compareAtPrice`: Number, optional (for showing discounts)
> - `images`: Array of `{ url: String, alt: String }`, at least 1 required
> - `category`: ObjectId ref to Category, required, indexed
> - `stock`: Number, required, default 0, min 0
> - `sku`: String, unique
> - `ratings`: `{ average: Number (0-5, default 0), count: Number (default 0) }`
> - `tags`: Array of Strings, indexed
> - `isActive`: Boolean, default true
> - `createdAt`, `updatedAt`: timestamps
> Add a text index on `name` and `description` for search. Add a compound index on `category` + `price`.
>
> **Category** (`Category.ts`):
> - `name`: String, required, unique
> - `slug`: String, unique, auto-generated
> - `description`: String
> - `image`: String (URL)
> - `parentCategory`: ObjectId ref to Category (self-ref for subcategories), nullable
> - `isActive`: Boolean, default true
> Add a virtual `productCount` field.
>
> **Cart** (`Cart.ts`):
> - `sessionId`: String, required, indexed (for guest carts)
> - `items`: Array of `{ product: ObjectId ref Product, quantity: Number (min 1), priceAtAdd: Number }`
> - `expiresAt`: Date, default 7 days from now, TTL indexed
> Add a virtual `totalAmount` that sums `quantity * priceAtAdd` for all items.
>
> **Order** (`Order.ts`):
> - `orderNumber`: String, unique, auto-generated (e.g., `ORD-20240101-XXXX`)
> - `items`: Array of `{ product: ObjectId, name: String, price: Number, quantity: Number, image: String }`
> - `subtotal`: Number, required
> - `shipping`: Number, default 0
> - `tax`: Number, default 0
> - `total`: Number, required
> - `shippingAddress`: `{ fullName, line1, line2, city, state, postalCode, country }`
> - `paymentStatus`: Enum `['pending', 'paid', 'failed', 'refunded']`, default `'pending'`
> - `stripePaymentIntentId`: String
> - `stripeSessionId`: String
> - `status`: Enum `['processing', 'shipped', 'delivered', 'cancelled']`, default `'processing'`
> - `createdAt`, `updatedAt`: timestamps
>
> Create a `/server/config/database.ts` file that connects to MongoDB Atlas with retry logic and connection event logging. Export a `connectDB()` function and call it in the server entry point.

**Checkpoint:**
- [ ] Server starts and logs `MongoDB connected: <cluster-name>` without errors
- [ ] All four models are importable and TypeScript types match the schema definitions
- [ ] Running `mongoose.connection.db.listCollections().toArray()` in a test script shows all collections
- [ ] Indexes are created (check with `Model.collection.getIndexes()`)

**Troubleshooting:**
- `MongoServerSelectionError: connection timed out` → Go to MongoDB Atlas > Network Access > Add your current IP address (or `0.0.0.0/0` for development)
- `Authentication failed` → Double-check the username and password in your connection string — special characters in the password must be URL-encoded
- `MONGODB_URI is undefined` → Make sure your `/server/.env` file exists and you are loading it with `dotenv.config()` at the very top of your entry file, before any other imports
- `buffered timeout` error on first query → Your Atlas cluster may be paused (free tier). Go to Atlas dashboard and resume it

---

## Phase 1.3: Node.js REST API (Products & Categories)

**What you'll get:** A complete RESTful API with CRUD endpoints for products and categories, including pagination, full-text search, multi-field filtering, and 20+ seeded sample products to work with immediately.

**Skills to activate:**
- `/nodejs-backend-patterns`
- `/api-endpoint-builder`

**Prompt to use:**
> /api-endpoint-builder
> Build a complete REST API for products and categories in the Express server at `/server`. Use the Mongoose models from Phase 1.2. Follow controller-route-middleware pattern.
>
> **Product Endpoints** (prefix: `/api/products`):
> - `GET /` — List all active products. Support these query params:
>   - `page` (default 1), `limit` (default 12)
>   - `search` — full-text search on name and description
>   - `category` — filter by category slug
>   - `minPrice`, `maxPrice` — filter by price range (values in dollars, convert to cents)
>   - `sort` — options: `price_asc`, `price_desc`, `newest`, `rating`, `name_asc`
>   - `tags` — comma-separated tag filter
>   - Return: `{ products: [...], pagination: { page, limit, total, pages } }`
> - `GET /:slug` — Get single product by slug, populate category
> - `POST /` — Create product (admin, no auth for now)
> - `PUT /:id` — Update product
> - `DELETE /:id` — Soft delete (set `isActive: false`)
> - `GET /featured` — Return 8 random active products with stock > 0
>
> **Category Endpoints** (prefix: `/api/categories`):
> - `GET /` — List all active categories with product counts
> - `GET /:slug` — Get category by slug
> - `POST /` — Create category
> - `PUT /:id` — Update category
> - `DELETE /:id` — Soft delete
>
> **Middleware:**
> - Global error handler with proper HTTP status codes and JSON error responses
> - Request validation middleware using `express-validator` for POST/PUT routes
> - CORS configured to allow the frontend origin
> - Rate limiting: 100 requests per minute per IP
>
> **Seed Script** (`/server/scripts/seed.ts`):
> Create a seed script that populates the database with:
> - 6 categories: Electronics, Clothing, Home & Kitchen, Books, Sports, Accessories
> - 24 sample products (4 per category) with realistic names, descriptions, prices ($9.99–$999.99), placeholder image URLs from `https://placehold.co/600x600/EEE/333?text=ProductName`, varied stock levels (0–100), random ratings (3.0–5.0), and relevant tags
> - Include a few products with `compareAtPrice` set higher than `price` to test discount badges
> - Run with: `npx ts-node server/scripts/seed.ts`
>
> Add proper TypeScript types for all request/response shapes. Use async/await with try-catch in all controllers.

**Checkpoint:**
- [ ] `GET http://localhost:5000/api/products` returns paginated products with 12 items per page
- [ ] `GET http://localhost:5000/api/products?search=wireless&sort=price_asc&minPrice=10&maxPrice=100` returns filtered, sorted results
- [ ] `GET http://localhost:5000/api/categories` returns all 6 categories with product counts
- [ ] `GET http://localhost:5000/api/products/featured` returns 8 random products
- [ ] Seed script runs successfully and populates 6 categories + 24 products
- [ ] Sending an invalid POST body returns a 400 error with validation messages

**Troubleshooting:**
- `Cannot GET /api/products` → Verify your routes are mounted in the Express app: `app.use('/api/products', productRoutes)`
- Search returns empty results → Text index might not be built yet; run `db.products.getIndexes()` in MongoDB shell to verify; try `Product.syncIndexes()`
- Pagination returns wrong total → Make sure you are using `countDocuments()` with the same filter object as the `find()` query
- CORS errors in browser → Check that `cors({ origin: process.env.CLIENT_URL || 'http://localhost:3000' })` is applied before routes

---

## Phase 1.4: Product Catalog UI

**What you'll get:** A vibrant, Shopify-quality product browsing experience with a bold hero section, product grid with hover effects, working search and filters, responsive design, and smooth loading states.

**Skills to activate:**
- `/react-nextjs-development`
- `/tailwind-patterns`

**Prompt to use:**
> /react-nextjs-development
> Build the product catalog frontend in the Next.js 14 app at `/client` using App Router and Tailwind CSS. Connect to the Express API at `NEXT_PUBLIC_API_URL`. Design a bold, colorful Shopify-style UI.
>
> **Layout & Navigation** (`app/layout.tsx`):
> - Header with: store logo/name ("ShopBolt" in bold gradient text `bg-gradient-to-r from-purple-600 to-pink-500`), navigation links (Home, Shop, Categories), cart icon with item count badge (red circle), mobile hamburger menu
> - Background: clean white `#FFFFFF`, text: `slate-800`
> - Footer with minimal links and copyright
>
> **Home Page** (`app/page.tsx`):
> - Hero section: full-width gradient background `from-purple-600 via-pink-500 to-orange-400`, large white headline "Discover Bold. Shop Smart.", subtitle, and a "Shop Now" button with white bg, bold text, rounded-full, hover scale effect
> - Featured products section: "Trending Now" heading, horizontal scroll or 4-column grid of ProductCards, fetched from `/api/products/featured`
> - Category showcase: 3-column grid of category cards with images, hover overlay effect
>
> **Product Card Component** (`components/ProductCard.tsx`):
> - White card with `rounded-2xl`, `shadow-md`, `hover:shadow-xl` transition, `hover:-translate-y-1`
> - Product image (aspect-square, object-cover, rounded-t-2xl)
> - Category label: small pill badge, `bg-purple-100 text-purple-700`
> - Product name: `font-semibold text-slate-800`, truncated to 2 lines
> - Star rating: yellow filled stars + gray empty stars, `text-amber-400`, with review count
> - Price: large bold `text-slate-900`. If `compareAtPrice` exists, show it struck through in `text-slate-400` and show a red "SALE" badge
> - "Add to Cart" button: full-width, `bg-gradient-to-r from-purple-600 to-pink-500 text-white`, `rounded-xl`, `hover:from-purple-700 hover:to-pink-600`, `active:scale-95` transition
>
> **Shop Page** (`app/shop/page.tsx`):
> - Left sidebar (hidden on mobile, toggleable):
>   - Category list with radio buttons, active state `text-purple-600 font-bold`
>   - Price range filter: dual slider or min/max inputs, "Apply" button
>   - Sort dropdown: `border-2 border-purple-200 rounded-xl`, options: Newest, Price Low→High, Price High→Low, Top Rated, Name A→Z
>   - "Clear All Filters" link
> - Right content area:
>   - Search bar: `rounded-full border-2 border-purple-200 focus:border-purple-500`, search icon, debounced (300ms)
>   - Results count: "Showing X of Y products"
>   - Product grid: 3 columns desktop, 2 tablet, 1 mobile
>   - Pagination: numbered buttons with `bg-purple-600 text-white` active state
> - Loading state: skeleton cards with `animate-pulse` matching the card layout
> - Empty state: illustration-style message "No products found" with "Clear filters" button
>
> **Product Detail Page** (`app/product/[slug]/page.tsx`):
> - Image gallery: main large image + thumbnail row
> - Product info: name (2xl bold), star rating, price (3xl bold), description
> - Stock indicator: green "In Stock" or red "Out of Stock"
> - Quantity selector: styled +/- buttons
> - "Add to Cart" button: large, same gradient style, `disabled:opacity-50` when out of stock
>
> Create a `/client/lib/api.ts` with typed fetch functions for all product and category endpoints. Use `useSearchParams` for filter state in the URL. All pages should have proper `<title>` and meta tags.

**Checkpoint:**
- [ ] Home page loads with hero section, featured products, and category showcase
- [ ] Product cards display image, name, price, rating stars, category badge, and "Add to Cart" button
- [ ] Shop page search filters products with 300ms debounce
- [ ] Category filter, price range, and sort all work and update the URL params
- [ ] Product detail page loads at `/product/[slug]` with full product info
- [ ] Layout is fully responsive: 1 column on mobile, 2 on tablet, 3–4 on desktop
- [ ] Skeleton loading states appear while data is fetching
- [ ] Discount badges appear on products with a `compareAtPrice`

**Troubleshooting:**
- API calls return `CORS error` → Verify Express CORS middleware allows `http://localhost:3000`; restart the backend
- Images not loading → Placehold.co images need `remotePatterns` in `next.config.js`: `{ protocol: 'https', hostname: 'placehold.co' }`
- Hydration mismatch errors → Ensure client-side state (like cart count) is wrapped with a check for `typeof window !== 'undefined'` or uses `useEffect`
- Filters not updating URL → Make sure you are using `useRouter().push()` or `useRouter().replace()` with the updated search params

---

## Phase 1.5: Shopping Cart + Checkout

**What you'll get:** A fully functional shopping cart with add/remove/update quantities, persistent state across page refreshes, and a checkout page with a shipping address form and order summary — ready to connect to payments.

**Skills to activate:**
- `/react-nextjs-development`
- `/react-state-management`

**Prompt to use:**
> /react-state-management
> Build a complete shopping cart and checkout flow for the Next.js e-commerce app. Use React Context + useReducer for cart state, persisted to localStorage.
>
> **Cart Context** (`context/CartContext.tsx`):
> - State shape: `{ items: CartItem[], isOpen: boolean }` where `CartItem = { productId, name, price, image, quantity, stock, slug }`
> - Actions: `ADD_ITEM` (increment quantity if exists, else add), `REMOVE_ITEM`, `UPDATE_QUANTITY` (validate against stock), `CLEAR_CART`, `TOGGLE_CART`
> - Derived values: `totalItems` (sum of quantities), `subtotal` (sum of price * quantity), `itemCount`
> - Persist to localStorage on every state change; hydrate from localStorage on mount
> - Wrap the entire app with `<CartProvider>`
>
> **Cart Slide-Over Panel** (`components/CartDrawer.tsx`):
> - Slides in from the right when cart icon is clicked, with dark overlay backdrop
> - Header: "Your Cart" + item count + close (X) button
> - Each item row: small product image (64x64, rounded-lg), name (linked to product page), price, quantity controls (styled -/+ buttons with `border-2 border-purple-200 rounded-lg`), remove button (trash icon, `text-red-500 hover:text-red-700`)
> - Subtotal at bottom: `text-xl font-bold`
> - "View Cart" button: outlined style, `border-2 border-purple-600 text-purple-600 rounded-xl`
> - "Checkout" button: full gradient `from-purple-600 to-pink-500 text-white rounded-xl`
> - Empty cart state: shopping bag icon, "Your cart is empty", "Continue Shopping" button
> - Animate entry with `transition-transform duration-300`
>
> **Cart Page** (`app/cart/page.tsx`):
> - Full-page cart view with a table-like layout on desktop, card layout on mobile
> - Columns: Product (image + name), Price, Quantity (with +/- controls), Total
> - Each row has a remove button
> - Right sidebar or bottom section: Order Summary card with `bg-gradient-to-br from-purple-50 to-pink-50 rounded-2xl`
>   - Subtotal, Shipping (show "Free" if > $50, else "$5.99"), Estimated Tax (calculated at 8.5%)
>   - Total in `text-2xl font-bold`
>   - "Proceed to Checkout" button: large gradient button
> - "Continue Shopping" link back to `/shop`
>
> **Checkout Page** (`app/checkout/page.tsx`):
> - Two-column layout: left = form, right = order summary
> - Shipping Address Form with labeled inputs (`rounded-xl border-2 border-slate-200 focus:border-purple-500`):
>   - Full Name, Email, Address Line 1, Address Line 2 (optional), City, State/Province (dropdown), Postal Code, Country (dropdown, default "United States")
>   - Client-side validation: required fields, email format, postal code format
>   - Error messages in `text-red-500` below each invalid field
> - Order Summary (right side): compact list of cart items (image + name + qty + price), subtotal, shipping, tax, total
> - "Pay with Stripe" button: large, full-width gradient, disabled until form is valid
> - Store checkout data in state — the Stripe integration in Phase 1.6 will use it
>
> **Update ProductCard and Product Detail page** to use the cart context's `addItem` action. Show a brief toast notification "Added to cart!" using a simple toast component with `bg-green-500 text-white rounded-xl` that auto-dismisses after 2 seconds.
>
> Update the header cart icon to show the live `totalItems` count in a `bg-red-500 text-white text-xs rounded-full` badge.

**Checkpoint:**
- [ ] Clicking "Add to Cart" on any product card or detail page adds the item to the cart
- [ ] Cart icon in header updates with the correct item count
- [ ] Cart drawer slides open showing all added items with correct prices and quantities
- [ ] Quantity +/- buttons update correctly and respect stock limits
- [ ] Removing an item updates both the drawer and the cart page
- [ ] Refreshing the page preserves all cart items (localStorage persistence)
- [ ] Checkout page shows shipping form with validation errors for empty/invalid fields
- [ ] Order summary shows correct subtotal, shipping (free over $50), tax, and total
- [ ] "Pay with Stripe" button is disabled until all required fields are filled correctly
- [ ] Toast notification appears when adding items to cart

**Troubleshooting:**
- Cart resets on page refresh → Ensure `useEffect` hydrates from `localStorage` only on mount (empty dependency array) and check that `JSON.parse` is wrapped in a try-catch
- Hydration mismatch on cart count → Initialize cart state as empty on the server; load from localStorage in `useEffect` on the client
- Quantity buttons allow exceeding stock → Add a guard in the `UPDATE_QUANTITY` reducer case: `Math.min(action.quantity, item.stock)`
- Toast appears behind the cart drawer → Set toast `z-index` to `z-[60]` (higher than the drawer's `z-50`)

---

## Phase 1.6: Stripe Payment Integration

**What you'll get:** Real payment processing (in test mode) with Stripe Checkout, a backend endpoint to create sessions, webhook handling to confirm payments, and polished success/cancel pages — completing the end-to-end purchase flow.

**Skills to activate:**
- `/stripe-integration`

**Prompt to use:**
> /stripe-integration
> Integrate Stripe Checkout into the e-commerce app. Use Stripe's hosted checkout page for payment. Configure everything in test mode.
>
> **Backend — Payment Endpoints** (`/server/routes/checkout.ts`):
>
> `POST /api/checkout/create-session`:
> - Accept `{ items: [{ productId, quantity }], shippingAddress: {...} }` in the request body
> - Validate that all products exist, are active, and have sufficient stock
> - Calculate subtotal, shipping ($5.99 or free if subtotal > $50), and tax (8.5%)
> - Create a Stripe Checkout Session with:
>   - `mode: 'payment'`
>   - `line_items` built from the validated products (name, image, unit_amount in cents, quantity)
>   - A separate line item for shipping (if applicable)
>   - `metadata` containing the order details as a JSON string
>   - `success_url`: `${CLIENT_URL}/order/success?session_id={CHECKOUT_SESSION_ID}`
>   - `cancel_url`: `${CLIENT_URL}/cart`
> - Create an Order document with `paymentStatus: 'pending'` and save the `stripeSessionId`
> - Return `{ sessionId: session.id, url: session.url }`
>
> `POST /api/webhooks/stripe`:
> - Use `express.raw({ type: 'application/json' })` for this route (before the JSON body parser)
> - Verify the webhook signature using `STRIPE_WEBHOOK_SECRET`
> - Handle `checkout.session.completed`:
>   - Find the Order by `stripeSessionId`
>   - Update `paymentStatus` to `'paid'` and save the `stripePaymentIntentId`
>   - Decrement stock for each product in the order
> - Handle `checkout.session.expired`:
>   - Update order `paymentStatus` to `'failed'`
> - Return 200 for all received events
>
> `GET /api/checkout/session/:sessionId`:
> - Return the order details for a given Stripe session ID (for the success page)
>
> **Frontend — Checkout Integration**:
>
> Update the Checkout page (`app/checkout/page.tsx`):
> - When "Pay with Stripe" is clicked: POST cart items and shipping address to `/api/checkout/create-session`, then redirect to `session.url` (Stripe's hosted page)
> - Show a loading spinner on the button while the session is being created
> - Handle errors: display an inline error message in `text-red-500` if the API call fails
>
> **Success Page** (`app/order/success/page.tsx`):
> - Fetch order details using the `session_id` query param from `/api/checkout/session/:sessionId`
> - Display: green checkmark icon (large, `text-green-500`), "Order Confirmed!" heading, order number, list of purchased items, total paid, shipping address
> - Styled card: `bg-gradient-to-br from-green-50 to-emerald-50 rounded-2xl shadow-lg p-8`
> - "Continue Shopping" button: gradient style
> - Clear the cart on this page (call `clearCart()` from context)
>
> **Cancel/Return Page:**
> - Redirect `/cart` already handles this — the user returns to their cart with items intact
>
> **Environment Variables Needed:**
> - Backend: `STRIPE_SECRET_KEY`, `STRIPE_WEBHOOK_SECRET`, `CLIENT_URL`
> - Frontend: `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY`
>
> Use Stripe test keys (starting with `sk_test_` and `pk_test_`). Add a comment in the checkout page explaining how to switch to live keys for production.

**Checkpoint:**
- [ ] Clicking "Pay with Stripe" on the checkout page redirects to Stripe's hosted checkout
- [ ] Using test card `4242 4242 4242 4242` (any future date, any CVC) completes the payment
- [ ] After payment, the user is redirected to `/order/success` showing the order confirmation
- [ ] The Order document in MongoDB has `paymentStatus: 'paid'` after webhook fires
- [ ] Product stock is decremented correctly after a successful payment
- [ ] Cart is cleared after reaching the success page
- [ ] Using test card `4000 0000 0000 0002` (decline) shows an error on Stripe's page and returns to cart
- [ ] The webhook endpoint returns 200 for all Stripe events

**Troubleshooting:**
- `No such API key` error → Make sure you are using Stripe **test mode** keys. Find them at [dashboard.stripe.com/test/apikeys](https://dashboard.stripe.com/test/apikeys). Keys start with `sk_test_` and `pk_test_`
- Webhook signature verification fails → You need to use a separate webhook secret. For local development, install the Stripe CLI and run: `stripe listen --forward-to localhost:5000/api/webhooks/stripe`. Copy the `whsec_...` signing secret it outputs into your `.env`
- `req.body` is undefined in webhook route → The webhook route MUST use `express.raw()` middleware, NOT `express.json()`. Mount the webhook route before the global JSON body parser
- Redirect to Stripe fails silently → Check the browser console for errors. Ensure the API response includes `session.url` and you are using `window.location.href = url` (not Next.js router) for the external redirect
- Order not found after payment → Verify the `stripeSessionId` is saved to the Order document when creating the checkout session
- Stock not updating → Check that the webhook handler is awaiting the `Product.updateOne()` calls and that you are using `$inc: { stock: -quantity }` with the correct sign

---

## Milestone 1 Complete!

**What you have now:** A working online store where customers can browse a catalog of 24+ products, search and filter by category/price/rating, view detailed product pages, add items to a persistent shopping cart, fill out shipping details, and complete a real payment through Stripe — with order confirmation and stock management.

**What's running:**
| Component | URL | Purpose |
|-----------|-----|---------|
| Next.js Frontend | `http://localhost:3000` | Storefront UI |
| Express API | `http://localhost:5000` | REST API |
| MongoDB Atlas | Cloud | Database |
| Stripe (Test Mode) | Hosted | Payment processing |

**Key test flow:** Home → Shop → Filter by "Electronics" → Click a product → Add to Cart → View Cart → Proceed to Checkout → Fill shipping form → Pay with Stripe (card: `4242 4242 4242 4242`) → See order confirmation.

---

**Next: [Continue to Milestone 2 — Full Features](milestone-2-features.md)** — User accounts, order history, reviews, admin dashboard, and email notifications.
