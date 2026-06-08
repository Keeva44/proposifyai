# ProposifyAI — B2B SaaS AI Estimator & Proposal Builder

ProposifyAI is a fully functional, high-fidelity B2B SaaS platform engineered for general contractors, landscaping professionals, design studios, and freelance professionals. It automates high-polish project scoping, material estimates, timeline planning, and professional contract letterhead printing through deep server-side AI integrations.

## 🚀 Live Preview URLs
- **Development App Preview:** [Vite Hot Reload Sandbox](https://ais-dev-3avtgb37vouls5imkgfhtp-31149740503.europe-west3.run.app)
- **Shared App Link:** [ProposifyAI Live Link](https://ais-pre-3avtgb37vouls5imkgfhtp-31149740503.europe-west3.run.app)

---

## 🔥 Key Product Features

- **Multi-Industry Intake Form Wizard**
  Surgical three-step intake funnel for collecting client names, industry categories, scope narratives, styling aesthetics, and budget brackets.
- **Dynamic Letterhead Blueprint Printing**
  Generates clean, modular, client-facing contract proposals featuring structured executive summaries, checkbox deliverables, cost lines, and timeline phases. Optimized for standard native printer-friendly exports.
- **Relational Cloud Storage (Firestore)**
  Authenticated users can securely save, manage, and instantly reload prior estimating blueprints directly from a real-time sidebar archive.
- **Mock & Live Dual-Processing Engines**
  Includes a fully customized offline mock generator for rapid product testing, alongside a robust Node.js server route connecting directly to Google Gemini 3.5.
- **Stripe Subscription Billing & Tier Limitations**
  Features Contractor Starter ($29/mo), Professional Team ($79/mo), and Enterprise Scale ($199/mo) plans with an intelligent checkout simulation sandbox as well as live Stripe API capabilities.

---

## 🛠️ Technical Stack & Architecture

- **Frontend:** React 18 with Vite, Tailwind CSS, and `lucide-react` icons. Focuses on Inter UI typography and refined JetBrains Mono accents.
- **Backend:** Node.js Express server running on standard port `3000` with native ESM type translation.
- **Identity & Store:** Cloud Firestore and Google Federated Login (fully isolated via firestore-blueprint rules).
- **Bundler:** Built using `esbuild` to compile high-performance backend units safely into CJS modules inside `/dist`.

---

## 💻 Developer Installation & Setup

1. **Clone the project & Install dependencies:**
   ```bash
   npm install
   ```

2. **Configure Environment Variables:**
   Create a standard `.env` configuration file in the project root:
   ```env
   # Node environment state
   NODE_ENV="development"
   APP_URL="http://localhost:3000"

   # Server-side secrets for AI copywriter
   GEMINI_API_KEY="AI_Studio_API_Key"

   # Stripe Subscriptions Integration
   STRIPE_SECRET_KEY="sk_live_..."
   STRIPE_PUBLISHABLE_KEY="pk_live_..."
   STRIPE_WEBHOOK_SECRET="whsec_..."
   ```

3. **Start the local server:**
   ```bash
   npm run dev
   ```
   *Your live application will boot directly on http://localhost:3000.*

4. **Production Build Compilation:**
   To bundle static frontend components and server files:
   ```bash
   npm run build
   npm start
   ```

---
*For a step-by-step buyer acquisition and transfer checklist, review the `/ACQUIRE_TRANSFER_GUIDE.md` document.*
