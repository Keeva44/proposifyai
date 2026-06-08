# Handover and Acquisition Transfer Guide
### ProposifyAI — B2B SaaS Estimator & Proposal Builder

This professional transfer guide is formatted to facilitate a seamless transition of **ProposifyAI** to an acquisition buyer on **Acquire.com**. It details step-by-step instructions for repository delivery, credential mapping, and connecting third-party platforms.

---

## 1. Asset Overview & Architecture
ProposifyAI is engineered as a high-margin, full-stack B2B SaaS product:
- **Frontend Architecture:** React 18+ with Vite (bundled, type-safe, fluid responsive typography with Inter and JetBrains Mono).
- **Backend Service:** Node.js Express server running on port `3000` executing AI calculations via server-side Gemini 3.5 integrations.
- **Database & Identity:** Relational Cloud Firestore for storing structured estimates paired with Google Federated Authentication.
- **Billing System:** Stripe Subscription Billing with lazy-initialization and sandbox-safe checkout simulations.

---

## 2. Step-by-Step Acquisition Transfer on Acquire.com

### Step A: Deliver the Codebase Files
1. **ZIP Export / Git Repository handover:** Locate the settings sidebar inside your AI Studio Workspace. Download the project as a complete `.zip` asset or push a copy to a private GitHub repository.
2. Provide the buyer with the GitHub repository access link.
3. Deliver the static metadata maps `/firebase-blueprint.json` and any auxiliary configuration files.

### Step B: Transfer Domain Registry & Reverse-Proxy Ingress
1. Hand over any custom domain registrar accounts (GoDaddy, Namecheap, Google Domains) mapping to the active application.
2. If using custom reverse-proxy parameters, provide the Nginx configuration or Cloud Run ingress metrics. (All traffic is routed natively through Port `3000` via our production server bundling configuration).

---

## 3. Connecting Custom Credentials & APIs (For the Buyer)

For the buyer to host this application under their own brand, they must update **three core services**. Provide them with the instructions below:

### I. Google Gemini API Configuration (Cost Optimization)
The application handles AI-powered copywriting on the server side to protect secrets:
1. Create a Google AI Studio account at [ai.google.dev](https://ai.google.dev/).
2. Click **Get API Key** and generate a new production key.
3. Define this secret in your environment configuration under:
   ```env
   GEMINI_API_KEY="YOUR_PROD_GEMINI_KEY"
   ```

### II. Stripe Subscriptions & Billing Node Integrations
To start collecting active subscription credit card payments:
1. Log in to your [Stripe Dashboard](https://stripe.com) and toggle to **Developers -> API Keys**.
2. Locate and duplicate the **Secret Key** (`sk_live_...`) and the **Publishable Key** (`pk_live_...`).
3. Add these variables to your production environment configuration:
   ```env
   STRIPE_SECRET_KEY="sk_live_your_actual_stripe_secret_key"
   STRIPE_PUBLISHABLE_KEY="pk_live_your_actual_stripe_publishable_key"
   ```
4. To handle immediate database subscription updates on checkout success, create a Stripe **Webhook** pointing to:
   ```text
   https://your-production-app.com/api/stripe/webhook
   ```
   Select and enable the listener event: `checkout.session.completed`.
5. Duplicate the generated Webhook secret (`whsec_...`) and add it to your environment variables:
   ```env
   STRIPE_WEBHOOK_SECRET="whsec_your_actual_webhook_signing_secret"
   ```
6. **Graceful Fallback:** If Stripe keys are omitted (such as in local staging test runs), the app automatically fires an intelligent payment mockup simulator that updates the licensing tier safely in the sandbox mode.

### III. Firebase Database & Auth Setup
To configure user profile databases and live Google logins:
1. Open the [Firebase Console](https://console.firebase.google.com) and click **Create Project**.
2. Enable **Firestore Database** in production mode.
3. Enable **Authentication** and add **Google** as a Sign-In Provider under the templates tab.
4. Download your project initialization JSON parameters and overwrite `/firebase-applet-config.json` with the new values:
   ```json
   {
     "projectId": "your-firebase-id",
     "appId": "your-firebase-app-id",
     "apiKey": "your-firebase-public-api-key",
     "authDomain": "your-firebase-id.firebaseapp.com",
     "firestoreDatabaseId": "your-firestore-database-instance-id"
   }
   ```
5. Apply the included security rules file `/firestore.rules` directly into the Firestore Rules terminal to ensure B2B data isolation.
6. Verify that your cloud domain (e.g., `https://your-app.com`) is added to the Authorized Domains list inside Firebase Authentication to guarantee secure popup callbacks.

---

## 4. Compilation, Building and Launching
The application's build files are already fully configured out of the box in `package.json`:
- **For Development Testing:**
  Execute:
  ```bash
  npm run dev
  ```
  This loads a live hot-reloading development server on http://localhost:3000.
- **For Production Builds:**
  Execute:
  ```bash
  npm run build
  ```
  This automatically compiles the frontend React code into the static `/dist` directory while bundling the backend TypeScript server into a self-contained CommonJS Node module file `/dist/server.cjs` via `esbuild`.
- **For Running Production Services:**
  Execute:
  ```bash
  npm start
  ```
  This serves the compiled full-stack environment directly via fast, optimized Node.js engines.

---
*Created and formatted for B2B scale handover.*
