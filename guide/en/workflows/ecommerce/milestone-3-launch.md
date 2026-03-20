# Milestone 3: Launch — SEO, Mobile, Docker, Deploy & Security

> **Prerequisites:** You completed [Milestone 1](milestone-1-foundation.md) (Next.js storefront, Express API, MongoDB, auth) and [Milestone 2](milestone-2-features.md) (3 payment gateways, reviews, admin dashboard, email notifications). Your store is feature-complete. Time to ship it.

This milestone takes your working e-commerce store and makes it production-ready. You will optimize for search engines, lock down the mobile experience, containerize the backend, deploy the full stack, and run a security audit before going live.

**Milestone 3 phases:**

| Phase | What | Skills |
|-------|------|--------|
| 3.1 | SEO Optimization | `seo-fundamentals`, `schema-markup` |
| 3.2 | Responsive Mobile-First Design | `tailwind-patterns`, `mobile-design` |
| 3.3 | Docker Setup for Backend | `docker-expert` |
| 3.4 | Deploy to Production | `vercel-deployment` |
| 3.5 | Security Audit | `security-audit` |

---

## Phase 3.1: SEO Optimization for Product Pages

**What you'll get:** Every product page will have unique meta titles and descriptions pulled from your database, Open Graph tags so products look great when shared on social media, JSON-LD structured data so Google can show rich results with price, availability, and star ratings, and an auto-generated sitemap for search engine crawlers.

**Skills to activate:**
- `/seo-fundamentals`
- `/schema-markup`

**Prompt to use:**
> /seo-fundamentals
> /schema-markup
>
> Add comprehensive SEO to my existing Next.js e-commerce product pages. The app uses the App Router and fetches product data from an Express API at `process.env.NEXT_PUBLIC_API_URL`. Each product has: name, description, price, images (array of URLs), category, averageRating, reviewCount, stock (number), and slug.
>
> Implement the following:
>
> 1. **Dynamic metadata per product page** — In `app/products/[slug]/page.tsx`, export a `generateMetadata` function that fetches the product and returns a unique `<title>` (format: "Product Name — Store Name"), `description` (truncated product description, max 160 chars), and canonical URL.
>
> 2. **Open Graph and Twitter Card tags** — Add `openGraph` and `twitter` fields to the metadata: og:title, og:description, og:image (first product image), og:type "product", og:url, twitter:card "summary_large_image". This ensures products display correctly when shared on Facebook, Twitter, LinkedIn, etc.
>
> 3. **JSON-LD Product schema markup** — Create a `ProductJsonLd` component that outputs a `<script type="application/ld+json">` tag with Schema.org Product markup. Include: name, description, image, sku, brand, offers (price, priceCurrency USD, availability InStock/OutOfStock based on stock count, url), and aggregateRating (ratingValue from averageRating, reviewCount). Render this component on every product page.
>
> 4. **JSON-LD BreadcrumbList** — Add breadcrumb structured data: Home > Category > Product Name.
>
> 5. **Sitemap generation** — Create `app/sitemap.ts` that exports a `sitemap()` function. Fetch all products and categories from the API. Generate entries for: homepage, all category pages (`/category/[slug]`), all product pages (`/products/[slug]`). Set `changeFrequency` to "daily" for products and "weekly" for categories. Set `priority` 1.0 for homepage, 0.8 for categories, 0.9 for products.
>
> 6. **robots.ts** — Create `app/robots.ts` that allows all crawlers, points to the sitemap URL, and disallows `/admin`, `/api`, `/checkout`, `/account`.
>
> 7. **Default metadata in root layout** — Set fallback title template "%s | Your Store Name", default description, and default OG image in `app/layout.tsx`.
>
> Make sure all meta tags work with Server Components. Do not install extra SEO libraries — use the built-in Next.js Metadata API.

**Checkpoint:**
- [ ] Run `curl http://localhost:3000/products/your-product-slug` and verify `<title>`, `<meta name="description">`, and `<meta property="og:*">` tags in the HTML
- [ ] Paste the product URL into the [Rich Results Test](https://search.google.com/test/rich-results) — it should detect Product schema with price, rating, and availability
- [ ] Visit `http://localhost:3000/sitemap.xml` and confirm all product and category URLs are listed
- [ ] Visit `http://localhost:3000/robots.txt` and confirm `/admin` and `/checkout` are disallowed
- [ ] Share a product URL in a Slack or Discord chat and confirm the preview card shows the product image, title, and description

**Troubleshooting:**
- JSON-LD not detected by Rich Results Test → Make sure the `<script>` tag is inside the page component's return, not in `<Head>`. With App Router, render it directly in the JSX body.
- `generateMetadata` not working → Confirm you are exporting it from a Server Component (no `"use client"` at the top of the page file).
- Sitemap returns 404 → File must be `app/sitemap.ts` (not `pages/sitemap.ts`). Restart the dev server after creating it.
- Open Graph images not showing in previews → Some platforms cache aggressively. Use [Facebook's Sharing Debugger](https://developers.facebook.com/tools/debug/) to clear cache and re-scrape.
- Metadata showing the fallback instead of product-specific data → Your `generateMetadata` function might be failing silently. Add a `try/catch` and log errors.

---

## Phase 3.2: Responsive Mobile-First Design

**What you'll get:** Every page in the store — homepage, product listing, product detail, cart, checkout, account, and admin — will be fully responsive. Mobile users get a hamburger menu, touch-friendly tap targets, a bottom navigation bar, and a checkout flow optimized for thumb reach. The product grid gracefully adapts from 1 column on phones to 2 on tablets to 3-4 on desktops.

**Skills to activate:**
- `/tailwind-patterns`
- `/mobile-design`

**Prompt to use:**
> /tailwind-patterns
> /mobile-design
>
> Audit and fix the responsive design across all pages of my Next.js e-commerce store. The app uses Tailwind CSS and has these pages: homepage, product listing (grid), product detail, cart, checkout (multi-step), user account/orders, and admin dashboard. Currently, the layout was built desktop-first and breaks on mobile.
>
> Implement the following changes using a mobile-first approach (style mobile by default, use `sm:`, `md:`, `lg:` breakpoints to scale up):
>
> 1. **Navigation bar** — Replace the current desktop nav with a responsive header:
>    - Mobile (< `md`): Logo on the left, cart icon with badge + hamburger menu icon on the right. Hamburger opens a full-screen overlay menu with links: Home, Shop, Categories, Account, and a close button. Animate the overlay sliding in from the right.
>    - Desktop (`md`+): Standard horizontal nav with all links visible. Cart icon with item count badge. User dropdown for account/logout.
>
> 2. **Bottom navigation bar (mobile only)** — Add a fixed bottom nav visible only below `md` breakpoint. Five icons: Home, Search, Categories, Cart (with badge), Account. Highlight the active page. Use `pb-safe` or bottom padding to avoid overlap with phone gesture bars. Hide it on the checkout page to avoid distraction.
>
> 3. **Product grid** — Update the product listing grid:
>    - Mobile: `grid-cols-1` with horizontal card layout (image left, details right) OR `grid-cols-2` with compact vertical cards.
>    - Tablet (`sm`): `grid-cols-2`
>    - Desktop (`lg`): `grid-cols-3` or `grid-cols-4`
>    - Product cards: image with `aspect-square object-cover`, product name truncated to 2 lines (`line-clamp-2`), price, and star rating. "Add to Cart" button at least 44x44px touch target.
>
> 4. **Product detail page** — Mobile: full-width image carousel (swipeable), sticky "Add to Cart" bar fixed at the bottom of the screen. Desktop: side-by-side layout (image gallery left, product info right). Ensure quantity selector buttons are large enough for touch.
>
> 5. **Cart page** — Mobile: stack items vertically, each as a card with product image, name, quantity adjuster (- / count / +) with large buttons, price, and remove link. Show order summary as a sticky footer with total and "Proceed to Checkout" button. Desktop: table layout.
>
> 6. **Checkout** — Mobile: single-column form, large input fields (min height 48px), clearly labeled. Step indicator at the top. "Place Order" button full-width and prominent. Ensure payment form inputs are thumb-reachable (important fields in the lower half of the screen where thumbs naturally rest).
>
> 7. **Touch targets** — Audit all interactive elements. Every button, link, and form control must be at least 44x44px. Add padding where needed. Increase tap target size for filter chips, pagination buttons, and star ratings.
>
> 8. **Typography scaling** — Headings should scale: `text-xl md:text-2xl lg:text-3xl`. Body text minimum `text-sm` (14px). Ensure readable contrast on all backgrounds.
>
> 9. **Images** — Use `next/image` with responsive `sizes` attribute everywhere. Set sizes to `(max-width: 640px) 100vw, (max-width: 1024px) 50vw, 25vw` for product grid images. This ensures the browser downloads appropriately sized images per screen.
>
> 10. **Admin dashboard** — Mobile: collapsible sidebar as a slide-out drawer. Data tables become card lists on mobile (each row becomes a card). Desktop: standard sidebar layout.
>
> Do not install extra UI libraries. Use only Tailwind CSS utility classes. Test all changes at 375px (phone), 768px (tablet), and 1280px (desktop) widths.

**Checkpoint:**
- [ ] Open Chrome DevTools, toggle device toolbar, select iPhone SE (375px) — navigate every page and confirm nothing overflows horizontally
- [ ] Hamburger menu opens and closes smoothly, all links work
- [ ] Bottom navigation bar is visible on mobile, hidden on desktop, and highlights the current page
- [ ] Product grid shows 1-2 columns on phone, 2 on tablet, 3-4 on desktop
- [ ] "Add to Cart" button on product detail page is sticky at the bottom on mobile
- [ ] All buttons and links are easily tappable — no misclicks due to small targets
- [ ] Checkout form inputs are comfortable to fill on a phone held one-handed
- [ ] Run Lighthouse mobile audit — Performance and Accessibility scores should be 80+

**Troubleshooting:**
- Horizontal scroll on mobile → Look for elements with fixed widths (`w-[600px]`) or content overflowing its container. Add `overflow-x-hidden` to the main wrapper as a last resort, but fix the root cause.
- Bottom nav overlaps page content → Add `pb-20` (or similar) to the main content area so the last items are not hidden behind the fixed bottom bar.
- Images look squished or stretched → Ensure you are using `object-cover` with a defined `aspect-ratio` (e.g., `aspect-square` or `aspect-[4/3]`).
- Hamburger menu stays open after clicking a link → Add an `onClick` handler on each link that closes the menu state.
- Sticky "Add to Cart" bar doesn't stick on iOS Safari → Use `fixed` instead of `sticky` for bottom bars, and add `-webkit-overflow-scrolling: touch` if needed. Also check z-index.

---

## Phase 3.3: Docker Setup for Backend

**What you'll get:** Your Express API runs inside a Docker container with a production-ready Dockerfile. A `docker-compose.yml` file lets you spin up the API and a local MongoDB instance with a single command. Environment variables are managed through `.env` files, and a health check endpoint confirms the service is running correctly.

**Skills to activate:**
- `/docker-expert`

**Prompt to use:**
> /docker-expert
>
> Dockerize my existing Express.js e-commerce API for production deployment. The API is in the `server/` directory, uses Node.js, Express, Mongoose (MongoDB), and has these npm scripts: `npm start` (runs `node src/index.js`), `npm run dev` (runs with nodemon). The API runs on port 5000 by default.
>
> Create the following:
>
> 1. **`server/Dockerfile`** — Multi-stage production Dockerfile:
>    - Stage 1 (`builder`): Use `node:20-alpine`. Set working directory to `/app`. Copy `package.json` and `package-lock.json`, run `npm ci --only=production`. Copy the rest of the source code.
>    - Stage 2 (`production`): Use `node:20-alpine`. Create a non-root user (`appuser`). Copy `--from=builder /app` to the final image. Expose port 5000. Set `NODE_ENV=production`. Add a `HEALTHCHECK` instruction that curls `http://localhost:5000/api/health` every 30 seconds. Run as `appuser`. CMD `node src/index.js`.
>    - Add a `.dockerignore` file: `node_modules`, `.env`, `.git`, `npm-debug.log`, `Dockerfile`, `docker-compose*.yml`, `*.md`, `.vscode`, `coverage`, `tests`.
>
> 2. **`server/src/routes/health.js`** — Health check endpoint `GET /api/health` that returns:
>    ```json
>    {
>      "status": "ok",
>      "timestamp": "ISO date",
>      "uptime": "process.uptime() in seconds",
>      "mongodb": "connected" or "disconnected"
>    }
>    ```
>    Check `mongoose.connection.readyState`. Register this route in the Express app.
>
> 3. **`docker-compose.yml`** (project root) — For local development:
>    ```yaml
>    services:
>      api:
>        build: ./server
>        ports: ["5000:5000"]
>        env_file: ./server/.env
>        depends_on:
>          mongodb:
>            condition: service_healthy
>        restart: unless-stopped
>
>      mongodb:
>        image: mongo:7
>        ports: ["27017:27017"]
>        volumes: [mongo-data:/data/db]
>        healthcheck:
>          test: mongosh --eval "db.adminCommand('ping')"
>          interval: 10s
>          timeout: 5s
>          retries: 5
>
>    volumes:
>      mongo-data:
>    ```
>
> 4. **`docker-compose.dev.yml`** — Override for development that adds volume mounts for hot-reloading:
>    ```yaml
>    services:
>      api:
>        build:
>          context: ./server
>          dockerfile: Dockerfile.dev
>        volumes:
>          - ./server/src:/app/src
>        command: npm run dev
>    ```
>
> 5. **`server/Dockerfile.dev`** — Development Dockerfile that installs all dependencies (including devDependencies) and runs with nodemon.
>
> 6. **Environment variables** — Create `server/.env.example` with all required variables and placeholder values:
>    ```
>    NODE_ENV=production
>    PORT=5000
>    MONGODB_URI=mongodb://mongodb:27017/ecommerce
>    JWT_SECRET=your-secret-here
>    STRIPE_SECRET_KEY=sk_test_xxx
>    PAYPAL_CLIENT_ID=xxx
>    PAYPAL_CLIENT_SECRET=xxx
>    SMTP_HOST=smtp.gmail.com
>    SMTP_PORT=587
>    SMTP_USER=your-email
>    SMTP_PASS=your-app-password
>    FRONTEND_URL=http://localhost:3000
>    ```
>    Make sure the actual `.env` is in `.gitignore` and `.dockerignore`.
>
> Make sure the Docker setup works with the existing code — do not restructure the project. The health endpoint should be the only new code in the Express app.

**Checkpoint:**
- [ ] Run `docker compose up --build` and both `api` and `mongodb` containers start without errors
- [ ] `docker compose ps` shows both services as "healthy"
- [ ] `curl http://localhost:5000/api/health` returns `{"status":"ok","mongodb":"connected",...}`
- [ ] The frontend at `localhost:3000` can still communicate with the API at `localhost:5000`
- [ ] Run `docker compose -f docker-compose.yml -f docker-compose.dev.yml up` — edit a file in `server/src/` and confirm nodemon restarts automatically
- [ ] `docker image ls` — the production image is under 200MB

**Troubleshooting:**
- `ECONNREFUSED` when API tries to connect to MongoDB → In `docker-compose.yml`, the MongoDB hostname is `mongodb` (the service name), not `localhost`. Make sure `MONGODB_URI` uses `mongodb://mongodb:27017/ecommerce`.
- Container crashes with "permission denied" → The `COPY` in the Dockerfile may not preserve correct permissions. Add `--chown=appuser:appuser` to the `COPY` instruction in the production stage.
- Hot reload not working with dev compose → On Windows/Mac, file watching inside Docker may not work with default polling. Add `CHOKIDAR_USEPOLLING=true` environment variable for the api service in `docker-compose.dev.yml`.
- MongoDB data lost after `docker compose down` → Data persists in the named volume `mongo-data`. It only resets if you run `docker compose down -v` (which removes volumes). This is expected behavior.
- Image too large → Make sure you are using `node:20-alpine` (not `node:20`) and that `node_modules` is not being copied from the host (check `.dockerignore`).

---

## Phase 3.4: Deploy to Production

**What you'll get:** Your Next.js frontend running on Vercel with automatic deployments from GitHub, your Dockerized Express API running on Railway (or Render/any Docker host), your MongoDB database on MongoDB Atlas, custom domain configured, and all services connected with proper environment variables and CORS settings.

**Skills to activate:**
- `/vercel-deployment`

**Prompt to use:**
> /vercel-deployment
>
> Deploy my full-stack e-commerce application to production. The stack is:
> - Frontend: Next.js (App Router) in the root directory or `client/` directory
> - Backend: Express.js API in `server/`, already Dockerized
> - Database: MongoDB (currently local via Docker)
>
> Walk me through the complete deployment, step by step:
>
> **Step 1: MongoDB Atlas setup**
> - Create a free M0 cluster on MongoDB Atlas (I will do this manually in the Atlas UI).
> - Generate a connection string in the format: `mongodb+srv://username:password@cluster.xxxxx.mongodb.net/ecommerce?retryWrites=true&w=majority`
> - Whitelist `0.0.0.0/0` for now (we will restrict IPs later).
> - Create the database user with read/write permissions.
>
> **Step 2: Deploy Express API to Railway**
> - Add a `railway.toml` or `Procfile` if needed by the platform.
> - Configure the Railway project to build from the `server/` directory using the existing Dockerfile.
> - Set all environment variables in Railway's dashboard:
>   - `MONGODB_URI` = Atlas connection string from Step 1
>   - `JWT_SECRET` = a strong random string (generate one with `openssl rand -hex 32`)
>   - `NODE_ENV` = production
>   - `PORT` = 5000 (or let Railway assign one via `$PORT`)
>   - `STRIPE_SECRET_KEY`, `PAYPAL_CLIENT_ID`, `PAYPAL_CLIENT_SECRET` = production keys
>   - `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS` = production email credentials
>   - `FRONTEND_URL` = the Vercel URL (set after Step 3, then come back and update)
> - Verify the API is live: `curl https://your-api.up.railway.app/api/health`
>
> **Step 3: Deploy Next.js to Vercel**
> - Connect the GitHub repository to Vercel.
> - If the Next.js app is in a subdirectory, set the "Root Directory" in Vercel project settings.
> - Set environment variables in Vercel:
>   - `NEXT_PUBLIC_API_URL` = the Railway API URL from Step 2 (e.g., `https://your-api.up.railway.app`)
>   - Any other public env vars the frontend needs.
> - Deploy. Vercel will auto-detect Next.js and configure the build.
>
> **Step 4: Connect everything**
> - Update `FRONTEND_URL` in Railway to the Vercel production URL (e.g., `https://your-store.vercel.app`).
> - Update CORS in the Express app:
>   ```javascript
>   const allowedOrigins = [
>     process.env.FRONTEND_URL,
>     'http://localhost:3000' // keep for local dev
>   ];
>   app.use(cors({
>     origin: function(origin, callback) {
>       if (!origin || allowedOrigins.includes(origin)) {
>         callback(null, true);
>       } else {
>         callback(new Error('Not allowed by CORS'));
>       }
>     },
>     credentials: true
>   }));
>   ```
> - Redeploy the API after the CORS update.
>
> **Step 5: Custom domain (optional)**
> - In Vercel, go to Settings > Domains > add your domain.
> - Add the DNS records Vercel provides (CNAME or A record) at your domain registrar.
> - Vercel provisions SSL automatically.
> - Update `FRONTEND_URL` in Railway to the custom domain.
> - Update `NEXT_PUBLIC_API_URL` if you also set up a custom API domain.
>
> **Step 6: Verify production**
> - Create a `scripts/verify-production.sh` script that checks:
>   - API health endpoint returns 200
>   - Frontend loads (curl the Vercel URL, check for 200)
>   - API can connect to MongoDB Atlas (health endpoint shows `"mongodb":"connected"`)
>   - A test product page returns correct meta tags
>   - CORS headers are present on API responses when Origin header is set
>
> Generate all configuration files and the verification script. For manual steps (Atlas UI, Railway dashboard, Vercel dashboard), give me clear numbered instructions with exact field names and values.

**Checkpoint:**
- [ ] `https://your-api.up.railway.app/api/health` returns `{"status":"ok","mongodb":"connected"}`
- [ ] `https://your-store.vercel.app` loads the homepage with products fetched from the production API
- [ ] Create a test account, add items to cart, and complete a test purchase with Stripe test mode
- [ ] Share a product URL on social media — preview card shows product image and details (OG tags working)
- [ ] Verification script passes all checks
- [ ] Check Vercel deployment logs — no build errors, no runtime errors in Functions tab

**Troubleshooting:**
- API returns CORS error in production → Double-check that `FRONTEND_URL` in Railway exactly matches the Vercel URL (including `https://`, no trailing slash). Redeploy after changing env vars.
- Frontend shows "Failed to fetch" for API calls → Make sure `NEXT_PUBLIC_API_URL` in Vercel does not have a trailing slash. Must be `https://your-api.up.railway.app` not `https://your-api.up.railway.app/`.
- MongoDB Atlas connection timeout → Ensure you whitelisted `0.0.0.0/0` in Atlas Network Access (or the specific IP range of your hosting provider). Also check the connection string has the correct password (no special characters unescaped).
- Railway build fails → Check that the Dockerfile path is correct and the build context is set to `server/`. Railway needs to find the Dockerfile in the root of the build context.
- Vercel build fails with "module not found" → If the Next.js app uses path aliases, make sure `tsconfig.json` paths are correct. Also check that all dependencies are in `dependencies`, not just `devDependencies`.
- Images not loading in production → If you use `next/image` with external URLs, add the production image domains to `next.config.js` under `images.remotePatterns`.
- Environment variables not available in the browser → Only `NEXT_PUBLIC_*` variables are exposed to the client. Server-side env vars are not accessible in client components.

---

## Phase 3.5: Security Audit

**What you'll get:** A hardened e-commerce API with rate limiting to prevent brute-force attacks, input validation on every endpoint, secure HTTP headers via Helmet.js, protection against MongoDB injection, proper CORS configuration, secure secret management, and HTTPS enforcement. Your store will be safe for handling real customer data and payment information.

**Skills to activate:**
- `/security-audit`

**Prompt to use:**
> /security-audit
>
> Perform a comprehensive security audit and hardening of my Node.js/Express e-commerce API. This application handles user authentication (JWT), stores customer data (names, emails, addresses), and processes payments through Stripe, PayPal, and cash-on-delivery. The database is MongoDB via Mongoose. The frontend is a Next.js app on a separate domain.
>
> Implement ALL of the following security measures:
>
> **1. Rate Limiting**
> - Install `express-rate-limit`.
> - Global rate limit: 100 requests per 15 minutes per IP.
> - Strict rate limit on auth routes (`/api/auth/login`, `/api/auth/register`, `/api/auth/forgot-password`): 5 requests per 15 minutes per IP. Return 429 with message "Too many attempts, please try again later."
> - Strict rate limit on payment routes (`/api/orders/*/pay`, `/api/checkout`): 10 requests per 15 minutes per IP.
> - Rate limit on review submission: 3 reviews per hour per user.
> - Use the `express-rate-limit` `standardHeaders` and `legacyHeaders` options.
>
> **2. Input Validation and Sanitization**
> - Install `express-validator`.
> - Add validation middleware to every route:
>   - Registration: email must be valid, password min 8 chars with at least one number and one uppercase letter, name must be 2-50 chars, sanitize all strings with `trim()` and `escape()`.
>   - Login: validate email format, password is not empty.
>   - Product creation (admin): name required 1-200 chars, price must be positive number, description max 5000 chars, category required.
>   - Review: rating must be integer 1-5, comment max 1000 chars.
>   - Order: validate shipping address fields (street, city, zip, country), validate that product IDs are valid MongoDB ObjectIds, quantities are positive integers.
>   - Search/filter: sanitize query parameters to prevent injection.
> - Create a reusable `validate` middleware that checks `validationResult` and returns 400 with specific error messages.
>
> **3. MongoDB Injection Prevention**
> - Install `express-mongo-sanitize`.
> - Apply it globally: `app.use(mongoSanitize())`. This strips `$` and `.` from user input to prevent operators like `$gt`, `$ne` in queries.
> - In Mongoose schemas, set `sanitizeFilter: true` globally.
> - Audit all `.find()`, `.findOne()`, and `.findById()` calls — ensure none directly pass unsanitized `req.query` or `req.body` into query objects.
>
> **4. HTTP Security Headers (Helmet.js)**
> - Install and configure `helmet`:
>   ```javascript
>   app.use(helmet({
>     contentSecurityPolicy: {
>       directives: {
>         defaultSrc: ["'self'"],
>         scriptSrc: ["'self'"],
>         styleSrc: ["'self'", "'unsafe-inline'"],
>         imgSrc: ["'self'", "data:", "https:"],
>         connectSrc: ["'self'", process.env.FRONTEND_URL]
>       }
>     },
>     crossOriginEmbedderPolicy: false, // needed if embedding external images
>     hsts: { maxAge: 31536000, includeSubDomains: true, preload: true }
>   }));
>   ```
> - This sets X-Content-Type-Options, X-Frame-Options, Strict-Transport-Security, and more.
>
> **5. CORS Hardening**
> - Restrict CORS to only the frontend origin:
>   ```javascript
>   app.use(cors({
>     origin: [process.env.FRONTEND_URL, 'http://localhost:3000'],
>     credentials: true,
>     methods: ['GET', 'POST', 'PUT', 'DELETE', 'PATCH'],
>     allowedHeaders: ['Content-Type', 'Authorization'],
>     maxAge: 86400
>   }));
>   ```
> - Remove any `cors({ origin: '*' })` or `cors()` with no options.
>
> **6. Authentication & JWT Security**
> - Ensure JWT secret is at least 32 characters (validate at startup, refuse to start if too short).
> - Set JWT expiration to 1 hour for access tokens.
> - Implement refresh tokens (7-day expiry, stored in httpOnly cookie, rotated on use).
> - Add `httpOnly`, `secure`, `sameSite: 'strict'` flags to all cookies.
> - Implement token blacklisting on logout (store invalidated tokens in Redis or a MongoDB collection with TTL index).
> - Hash passwords with bcrypt (cost factor 12, verify this is already the case).
>
> **7. API Key and Secret Management**
> - Audit all environment variables — no secrets hardcoded in source code.
> - Create a `config/secrets.js` that validates all required env vars are present at startup. If any are missing, log which ones and exit with code 1.
> - Ensure `.env` is in `.gitignore`.
> - Stripe webhook signature verification: verify the `stripe-signature` header on webhook endpoints using `stripe.webhooks.constructEvent()`. Reject any webhook that fails verification.
> - PayPal: verify IPN/webhook notifications server-side before processing.
>
> **8. HTTPS Enforcement**
> - Add middleware that redirects HTTP to HTTPS in production:
>   ```javascript
>   if (process.env.NODE_ENV === 'production') {
>     app.use((req, res, next) => {
>       if (req.headers['x-forwarded-proto'] !== 'https') {
>         return res.redirect(301, `https://${req.hostname}${req.url}`);
>       }
>       next();
>     });
>   }
>   ```
> - Set `trust proxy` to 1 for Express (needed behind Railway/Render reverse proxy).
>
> **9. Additional Hardening**
> - Disable `X-Powered-By` header (Helmet does this, but verify).
> - Add request size limits: `app.use(express.json({ limit: '10kb' }))` to prevent large payload attacks. Allow larger limit (5MB) only on image upload routes.
> - Add `hpp` (HTTP Parameter Pollution) protection: `npm install hpp` and `app.use(hpp())`.
> - Log all failed authentication attempts with IP address and timestamp for monitoring.
> - Add a `security.txt` endpoint at `/.well-known/security.txt` with contact info for responsible disclosure.
> - Prevent user enumeration: login and forgot-password should return the same generic message whether the email exists or not ("If this email is registered, you will receive...").
>
> **10. Dependency Security**
> - Run `npm audit` and fix all high/critical vulnerabilities.
> - Add an `npm audit` step to the Dockerfile build so the image fails to build if critical vulns are found.
>
> Apply all changes to the existing Express codebase. Do not restructure the project. Show me which files were modified and which packages were installed. After all changes, list any remaining security considerations I should handle manually (like enabling 2FA for admin accounts).

**Checkpoint:**
- [ ] Start the server — it boots without errors and all env var validation passes
- [ ] `curl -I https://your-api.up.railway.app/api/products` — response includes `X-Content-Type-Options: nosniff`, `Strict-Transport-Security`, and no `X-Powered-By` header
- [ ] Hit `/api/auth/login` 6 times rapidly with wrong credentials — the 6th request returns 429 (rate limited)
- [ ] Try to register with password "abc" — returns 400 with validation error about minimum length
- [ ] Send `{"email": {"$gt": ""}, "password": "test"}` to login endpoint — should fail with validation error, not return all users
- [ ] `npm audit` shows 0 critical and 0 high vulnerabilities
- [ ] Stripe webhook endpoint rejects requests without a valid `stripe-signature` header
- [ ] Server refuses to start if `JWT_SECRET` is missing or shorter than 32 characters
- [ ] Failed login attempts appear in server logs with IP and timestamp
- [ ] `curl http://your-api.up.railway.app/anything` in production redirects to `https://`

**Troubleshooting:**
- Rate limiter blocks legitimate users in development → The rate limits above are for production. In development, increase the limits or disable rate limiting when `NODE_ENV === 'development'`.
- `express-mongo-sanitize` breaks legitimate queries → If any of your features use `$` operators in user-facing queries (e.g., price range filters with `$gte`/`$lte`), sanitize those routes individually rather than globally, or construct the query operators server-side from plain number inputs.
- Helmet CSP blocks your frontend → Since your frontend is on a separate domain, you might not need CSP on the API. If API routes return HTML (like email previews), adjust the `connectSrc` and `scriptSrc` directives.
- JWT refresh token rotation causes logouts → Make sure the refresh token endpoint returns a new refresh token AND a new access token. The client must store and use the new refresh token immediately.
- `trust proxy` not working → Railway and Render set `X-Forwarded-Proto`. Make sure `app.set('trust proxy', 1)` is called before any middleware that checks the protocol.
- `express-validator` errors not showing up → Make sure the validation middleware array comes before the route handler in the route definition: `router.post('/login', [validations], validate, loginController)`.

---

## Your Store is Live!

Congratulations! You have built and deployed a production-ready e-commerce store from scratch using Claude Code skills.

Here is everything your store includes:

- **Full product catalog** with categories, search, and filtering
- **User authentication** with registration, login, JWT tokens, and refresh tokens
- **Shopping cart** with persistent state and quantity management
- **Three payment methods**: Stripe (cards), PayPal, and Cash on Delivery
- **Order management** with status tracking and order history
- **Product reviews and ratings** with verified purchase badges
- **Admin dashboard** for managing products, orders, and users
- **Transactional emails** for order confirmation, shipping, and password reset
- **SEO optimization** with dynamic meta tags, JSON-LD schema, and sitemap
- **Production-grade security** with rate limiting, input validation, and secure headers

**Tech stack:** Next.js (App Router) + Tailwind CSS | Express.js + Mongoose | MongoDB Atlas | Docker | Vercel + Railway

**Payment processing:** Stripe + PayPal + Cash on Delivery

### What's Next?

Your store is live, but there is always room to grow. Here are skills to explore next:

- Monitor uptime and performance with `/observability-engineer`
- Add Google Analytics and conversion tracking with `/analytics-tracking`
- Improve conversion rates with A/B testing using `/page-cro`
- Scale the backend with `/microservices-patterns` when traffic grows
- Add more products and optimize listings with `/seo-content-writer` + `/social-content`
- Set up CI/CD pipelines with `/ci-cd-pipelines`
- Add real-time features (live chat, inventory updates) with `/websocket-guide`

### Skills Used in This Workflow

| Skill | Phase | Purpose |
|-------|-------|---------|
| `nextjs-developer` | 1.1 | Next.js storefront setup |
| `api-developer` | 1.2 | Express API and REST endpoints |
| `mongodb-expert` | 1.3 | Database schemas and queries |
| `auth-specialist` | 1.4 | JWT authentication and registration |
| `tailwind-patterns` | 1.5, 3.2 | UI styling and responsive design |
| `stripe-integration` | 2.1 | Stripe payment processing |
| `paypal-integration` | 2.2 | PayPal payment processing |
| `api-developer` | 2.3 | Cash-on-delivery order flow |
| `review-system` | 2.4 | Product reviews and ratings |
| `admin-dashboard` | 2.5 | Admin panel for store management |
| `email-notifications` | 2.6 | Transactional email system |
| `seo-fundamentals` | 3.1 | Meta tags and sitemap |
| `schema-markup` | 3.1 | JSON-LD structured data |
| `mobile-design` | 3.2 | Mobile-first responsive design |
| `docker-expert` | 3.3 | Backend containerization |
| `vercel-deployment` | 3.4 | Production deployment |
| `security-audit` | 3.5 | Security hardening |

---

Built with Claude Code skills. [Back to Skill Combos](../../skill-combos.md) | [Back to README](../../../../README.md)
