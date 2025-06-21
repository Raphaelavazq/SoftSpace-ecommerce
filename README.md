# E-Commerce Full Stack App (Next.js 14, Payload CMS, Stripe)



A modern, production-ready e-commerce platform built with [Next.js 14](https://nextjs.org/), [Payload CMS](https://payloadcms.com/), [MongoDB](https://www.mongodb.com/), and [Stripe](https://stripe.com/) for payments.  
Includes a powerful admin dashboard, CMS, and a customizable storefront.

---

## 🚀 Features

- Full-featured e-commerce storefront (SSR/SSG)
- Powerful admin dashboard (Payload CMS)
- Stripe payments integration (test & live)
- MongoDB for data storage (Dockerized)
- TypeScript, modular codebase, and best practices

---

# Project Setup Guide

Follow these steps to set up the project locally.

---

## 1. Clone the Repository

```bash
git clone https://github.com/adrianhajdin/ecommerce.git
cd ecommerce-main
```

---

## 2. Install All Dependencies

```bash
yarn install
# or
npm install --legacy-peer-deps
```
This installs Next.js, Payload CMS, Stripe, and all required npm packages.

---

## 3. Configure Environment Variables

Copy the example file and fill in your secrets:

```bash
cp .env.example .env
cp .env.example .env.local
```

Edit `.env` and `.env.local` with your keys:

```env
# Payload vars
PORT=3000
DATABASE_URI=mongodb://mongo:27017/payload-template-ecommerce
PAYLOAD_SECRET=<your_generated_secret>
PAYLOAD_PUBLIC_SERVER_URL=http://localhost:3000
STRIPE_SECRET_KEY=<your_stripe_secret_key>
PAYLOAD_PUBLIC_STRIPE_IS_TEST_KEY=true
STRIPE_WEBHOOKS_SIGNING_SECRET=<your_stripe_webhook_secret>
PAYLOAD_PUBLIC_DRAFT_SECRET=demo-draft-secret
REVALIDATION_KEY=demo-revalation-key

# Next.js vars
NEXT_PUBLIC_SERVER_URL=http://localhost:3000
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=<your_stripe_publishable_key>
NEXT_PUBLIC_IS_LIVE=false
NEXT_PRIVATE_DRAFT_SECRET=demo-draft-secret
NEXT_PRIVATE_REVALIDATION_KEY=demo-revalation-key
```

**How to get these keys:**
- **PAYLOAD_SECRET:**  
  Generate with  
  ```bash
  openssl rand -hex 32
  ```
- **Stripe keys:**  
  Get from [Stripe Dashboard → Developers → API keys](https://dashboard.stripe.com/apikeys)
- **STRIPE_WEBHOOKS_SIGNING_SECRET:**  
  Use Stripe CLI:  
  ```bash
  stripe listen --forward-to localhost:3000/api/stripe/webhooks
  ```
  Copy the `whsec_...` value shown.

---

## 4. Key Config Files

- [`package.json`](package.json ): Project dependencies and scripts.
- [`src/payload/payload.config.ts`](src/payload/payload.config.ts ): Payload CMS collections, access, plugins, etc.
- `.env.local` and `.env`: All runtime secrets and API keys.
- [`docker-compose.yml`](docker-compose.yml ): Used for running MongoDB in Docker.

---

## 5. Set Up MongoDB via Docker

Start MongoDB and your app:

```bash
docker compose up -d
```

This will:
- Start MongoDB in a container
- Start your app in a Node.js container, install dependencies, and run the dev server

---

## 6. Run the Payload Admin Panel

Open your browser and go to:

```
http://localhost:3000/admin
```

On your first visit, create your admin user or log in with the seeded credentials.

---

## 7. Run the Next.js Storefront

Open:

```
http://localhost:3000
```

This is your public-facing e-commerce storefront.

---

## 8. How Everything Works Together

- **Next.js**: Handles the storefront UI and SSR.
- **Payload CMS**: Provides the admin panel and API for managing shop data.
- **MongoDB**: Stores all CMS and shop data (runs in Docker).
- **Stripe**: Handles payments (test keys for dev, live keys for production).
- **TypeScript**: Ensures type safety across the codebase.

---

## 9. Common Troubleshooting Tips

- **Port 3000 in use:**  
  Only one process can use port 3000. If you use Docker Compose, do not run `yarn dev` at the same time.
- **MongoDB connection errors:**  
  Make sure `DATABASE_URI` is set to `mongodb://mongo:27017/payload-template-ecommerce` for Docker.
- **Environment variable issues:**  
  Double-check `.env` and `.env.local` and restart Docker Compose after changes.
- **Stripe webhook issues:**  
  Make sure Stripe CLI is running with  
  ```bash
  stripe listen --forward-to localhost:3000/api/stripe/webhooks
  ```
  and that your `STRIPE_WEBHOOKS_SIGNING_SECRET` matches the one shown by the CLI.

---

## 10. Customization

- Update collections and fields in [`src/payload/payload.config.ts`](src/payload/payload.config.ts )
- Customize the storefront in [`src/app`](src/app )
- Add new features, styles, and integrations as needed

---

## License

This project is for educational purposes.  
For commercial use, review the original repository’s license and terms.

---

**Built with ❤️ following the tuturials by  [JavaScript Mastery](https://jsmastery.pro/next15) and [Adrian Hajdin](https://youtu.be/3JUsg-WsU9o?si=YzrJY-W19jrRRJhD)**
