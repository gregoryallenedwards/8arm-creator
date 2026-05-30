# Tech Stack Reference

White-label boilerplate layers and tools to know / demonstrate.

---

## White-Label Boilerplate (Standard Template)

### I. Telemetry & LiveOps
- **TelemetryDeck** — privacy-first user behavior tracking
- **Sentry** — crash reporting, stack traces
- **ConfigCat / Firebase Remote Config** — feature flags, remote LiveOps variables
- **Aptabase** — edge device / desktop telemetry

### II. Database, Auth & State
- **Supabase** — PostgreSQL, real-time webhooks, RLS
- **Clerk** — social logins, magic links, biometric auth
- **Qdrant (Cloud)** — vector database for semantic search / RAG
- **Riverpod / BLoC** — Flutter state management scaffold

### III. Monetization & Billing
- **RevenueCat** — cross-platform mobile subscriptions, receipt validation
- **Stripe Checkout** — web-based B2B micro-SaaS billing
- **Glassfy** — paywall drop-testing, revenue analytics
- **Superwall** — mobile paywall optimization

### IV. Communication & Feedback
- **Resend** — transactional email, lifecycle alerts
- **Discord / Slack Webhooks** — diagnostic pings on signups, paywalls, errors
- **Instabug / Shake** — beta user bug reports via shake gesture
- **Canny / Featurebase** — feature request boards

### V. CI/CD & Delivery
- **Fastlane** — automated screenshots, packaging, TestFlight/Play Console
- **Codemagic** — cloud CI/CD for mobile builds
- **GitHub Actions** — unit tests, JSON validation, license checks on every PR

### VI. Legal & Compliance
- **Iubenda / Termly** — Privacy Policy, Terms of Service generators
- **Apple Privacy Manifest (.xcprivacy)** — pre-configured for App Store review

### VII. Growth & SEO
- **Branch.io** — deep linking across platforms
- **RevenueCat A/B Tester** — swap subscription pricing without code updates
- **Dynamic UTM Tag Injectors** — track which Reddit/LinkedIn drop drove traffic

### VIII. Substack Funnel
- **Substack API Webhooks** — push in-app email captures to newsletter
- **"Pay-with-a-Subscribe" Gate** — unlock features with email opt-in
- **RSS-to-In-App Feed** — latest Substack articles in app discovery tab

### IX. AI & LLM Layer
- **LangSmith / Helicone** — prompt observability, token burn monitoring
- **Vercel AI SDK** — streaming text output to web UI
- **System Prompt Master Config** — remote-updatable JSON for agent rules

### X. UI/UX
- **Flutter themes / Shadcn UI** — locked-in responsive component library
- **Crowdin / Localizely** — OTA translation, no store update needed
- **Lottie / Rive** — lightweight JSON animations

### XI. Edge & Performance
- **SQLite → Supabase sync** — offline-first caching
- **Cloudflare Workers** — zero-cold-start edge functions
- **ImageKit / Cloudinary** — WebP asset compression by screen resolution
- **DeX Manifest configs** — resizable activity for desktop-class Android

### XII. Security
- **Cloudflare Turnstile** — zero-friction CAPTCHA
- **DeviceCheck / Play Integrity** — block emulated scraper farms
- **Rate-limiting middleware** — protect AI endpoints
- **ProGuard / obfuscation** — scramble production code

---

## Technologies to Demonstrate (Resume / Portfolio)

**Languages & Frameworks:**
Flutter, React, WebGL, Android Kotlin + Jetpack, Python, Node

**AI Tools:**
Claude Code, Google ADK, LangGraph, Crew AI, MCP, Pydantic AI, Google AI Studio

**Dev Tools:**
Cursor, Windsurf, Replit, Lovable.dev, Bolt.new, V0 (Vercel), Reflex

**Data & Backend:**
Supabase, Firebase, Streamlit, Python Pandas, Zod Schema, Redix UI

**Infrastructure:**
AWS, Azure, Google Cloud, GitHub Actions, Codemagic, Fastlane

**Other:**
Firecrawl, Jina AI Reader, Stripe, Shadcn/UI blocks, Tailwind / Material UI
BLOC, Riverpod, iCloud databases, local SLMs
