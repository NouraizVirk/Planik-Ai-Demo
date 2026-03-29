<div align="center">
  <img src="https://via.placeholder.com/150x150/0f172a/ffffff?text=Planik+AI" alt="Planik AI Logo" width="120" />

  <h1 align="center">Planik AI 🏠🏗️</h1>

  <p align="center">
    <strong>Revolutionizing Architectural Planning with Generative AI & Seamless Contractor Collaboration</strong>
  </p>

  <p align="center">
    <a href="https://planik-ai.vercel.app/"><strong>🔗 View Live Production Demo</strong></a>
  </p>

  <p align="center">
    <img src="https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js" alt="Next.js" />
    <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
    <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind CSS" />
    <img src="https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white" alt="Supabase" />
    <img src="https://img.shields.io/badge/AI_Powered-8A2BE2?style=for-the-badge&logo=openai&logoColor=white" alt="AI Powered" />
  </p>
</div>

---

# 🌟 Part 1: Product Overview & Vision

**Planik AI** is a next-generation SaaS digital marketplace that fundamentally disrupts traditional architectural planning and construction bidding. By harnessing the capabilities of Generative AI, Planik AI acts as a digital bridge connecting homeowners/clients with verified construction contractors. 

Instead of waiting weeks for preliminary architectural drafts, clients can instantly generate a highly detailed, proportional floor plan using natural language and structured inputs. Once generated, clients can publish their blueprints to an active marketplace where contractors bid on timelines and costs. From the first AI-generated pixel to the final construction milestone, Planik AI handles the entire project lifecycle in one secure ecosystem.

### 💡 Core Value Propositions
* **Instant Ideation:** Days of architectural back-and-forth are reduced to seconds via our AI generation models.
* **Radical Transparency:** A fully transparent bidding system ensures clients get fair market value for construction, while contractors get equal visibility to win projects.
* **Frictionless Collaboration:** Integrated real-time messaging, milestone tracking, and progress percentage updates eliminate the need for third-party comms like WhatsApp or Email.

---

## 🎯 The Multi-Sided Platform Experience

Planik AI features three uniquely engineered, distinct environments, each tailored precisely to the needs of its specific user role.

### 👤 1. The Client Command Center
Crafted for users looking to dream, plan, and build. 
* **The AI Generation Studio:** Clients input specific spatial parameters (e.g., number of rooms, total square footage, specific architectural styles, and budget constraints). The AI engine processes these constraints to output a high-fidelity floor plan.
* **Project Publishing & Management:** Generated plans can be converted into active project listings. Clients define project scope, upload supplementary requirements, and post them to the marketplace.
* **Intelligent Bid Review:** As contractors submit varying quotes and delivery timelines, clients interact with a dynamic comparison dashboard. They can review contractor profiles, past ratings, bids, and securely award the project with a single click.
* **Live Progress Monitoring:** A dynamic timeline tracks exactly how the project is proceeding. Clients view incremental percentage completions natively uploaded by their assigned contractor.
* **Real-Time Communications Hub:** Direct, built-in chatting mechanism with the assigned contractor to clarify details, request changes, or approve milestones.
* **Feedback & Rating Engine:** Upon project completion, clients submit verified reviews which permanently impact a contractor's marketplace standing.

### 👷 2. The Contractor Workspace
A comprehensive, streamlined pipeline for professionals to find work, negotiate, and deliver.
* **The Project Discovery Marketplace:** A live feed of all unassigned projects globally. Contractors can browse structural descriptions, view the AI-generated blueprints, and decide what matches their expertise.
* **Bid Submission Engine:** Contractors evaluate a listing and submit a binding bid dictating their proposed cost and estimated timeframe. The system tracks the status of all submitted bids (Pending, Accepted, Rejected).
* **Active Assignments Dashboard:** Once awarded a project, the contractor's dashboard shifts to an execution view, detailing client contact info, finalized blueprints, and agreed-upon financial terms.
* **Milestone Delivery System:** Contractors control the timeline reporting. They securely submit progress updates ("Foundation Laid - 25%", "Framing Complete - 50%"), instantly notifying the client.
* **Client Chat Interface:** Native messaging prevents communication silos, allowing contractors to instantly ping clients from the job site.

### 🛡️ 3. The Administrative Oversight Dashboard
The ultimate control panel meant for platform owners to maintain quality, security, and growth.
* **Central Analytics Brain:** A high-level, birds-eye view reporting on gross platform volume, total active/completed projects, user registration velocity, and AI utilization metrics.
* **User & Role Management:** Admins possess absolute control to view, suspend, or permanently ban accounts. They can manage bidding limits for contractors to prevent spam.
* **Global Project Moderation:** Complete visibility into every project state. Admins can intervene in disputes, forcibly close stale projects, or moderate inappropriate listings.
* **Immutable Audit Logging:** Every critical action taken on the platform (logins, bid placements, state changes, password resets) is fundamentally logged to an unalterable ledger to ensure platform integrity and immediate traceability in case of malicious activity.

---

<br/>

# � Part 2: Engineering & Technical Deep Dive

Planik AI is not just a standard CRUD application; it is a highly complex, state-driven platform built entirely on the bleeding edge of modern web development. Below is a breakdown of the architectural decisions, tech stack, and underlying logical flows that power the application.

## 🛠️ The Technology Stack

| Technology | Purpose & Implementation Justification |
| :--- | :--- |
| **Next.js 15 (App Router)** | Powers the entirety of the frontend and backend API. Chosen for its native React Server Components (RSC) which drastically reduce client-side JavaScript bundles, alongside robust Server Actions for high-security data mutations without exposing API endpoints. |
| **TypeScript (Strict)** | Enforces rigorous end-to-end type safety. Every Supabase database schema is dynamically mapped into TypeScript interfaces, ensuring that a change in a database column automatically flags compiler errors in the UI, virtually eliminating runtime crashes. |
| **Tailwind CSS & Framer** | Tailwind is utilized for atomic, utility-first styling, ensuring zero dead CSS code. Combined with custom CSS utility classes, it powers the platform's proprietary "Glassmorphism" aesthetic, providing a highly premium, translucent, dark-mode native interface. |
| **Supabase (PostgreSQL)** | Functions as the core backend infrastructure. Far more capable than NoSQL alternatives, the Postgres relational structure is vital for mapping the complex, many-to-many relationships between Users, Projects, Bids, Messages, and Audit Logs. |
| **Supabase Auth** | Handles secure user authentication, hashing, and session management. It issues secure JWTs (JSON Web Tokens) which dictate exactly what data the DB returns based on the user's role. |
| **Generative AI API** | Processes complex, tokenized architectural parameters from the frontend, compiles them into optimized system prompts, and routes them to a diffusion model to systematically map out logical architectural floor plans. |
| **Vercel Edge Network** | Hosts the deployed application. Chosen for its zero-configuration CI/CD pipeline and ability to run Next.js Route Handlers on Edge networks, providing dramatically faster TTFB (Time to First Byte) globally. |

---

## 🧠 Core System Logic & Architectural Flows

### 1. Robust Role-Based Access Control (RBAC) & Next.js Middleware
Security is paramount in a multi-sided marketplace. Planik AI enforces RBAC at three completely different layers to ensure absolute security:
1. **The Edge Middleware Layer:** Next.js `middleware.ts` intercepts every single incoming HTTP request *before* it hits the server. It decodes the user's secure HTTP-only cookie to determine their role (`client`, `contractor`, or `admin`). If a Client tries to type `/app/contractor/dashboard` into their URL bar, the Middleware instantly bounces them before the page even begins to render.
2. **The Server Component Layer:** As pages render on the server, they fetch the user's verified role directly from Supabase, dynamically hiding UI elements (like removing the "Bid" button if the user is a Client instead of a Contractor).
3. **Database Row Level Security (RLS):** Supabase Postgres heavily utilizes RLS policies. Even if a malicious user bypasses the UI and attempts to query the database directly for another user's private project details, the database itself will reject the query. For instance, the SQL policy `current_user_id() = client_id` ensures a client can literally only fetch data they own.

### 2. The Project Lifecycle State Machine
Projects in Planik AI are not static; they operate on a strict logical state machine governed by the backend.
* **State `open`:** The project is visible in the Contractor Marketplace. Bidding is enabled.
* **State `in_progress`:** Triggered the exact millisecond a Client hits "Accept Bid". The backend begins a transaction:
  * It marks the project as `in_progress`.
  * It assigns the `selected_bid_id` and the winner's `contractor_id` to the project row.
  * It automatically iterates through all *other* competing bids on that specific project and forcibly updates their state to `rejected`, cleaning up the database and notifying the losers.
  * It creates an empty progress initialization row to start tracking milestones.
* **State `completed`:** Triggered when the final milestone crosses 100%. The system closes the messaging tunnel, halts new updates, and triggers the UI prompt for the client to leave a review.

### 3. The Generative AI Prompt Pipeline
The AI floor plan generation does not rely on simple prompts. It uses a structured prompt compilation engine. 
1. The user selects visual UI constraints (Bedrooms: 3, Style: Modern, Square Footage: 2500).
2. The frontend strips these down into a structured JSON payload to the Next.js API route.
3. The API securely loads hidden environment variables, injects the user's parameters into a highly optimized, secret "System Prompt Template" designed specifically for architectural diagramming (preventing prompt-injection attacks).
4. The generation model returns a high-res image buffer, which the server compresses and dynamically pipes to Supabase Cloud Storage.
5. A signed, public URL is returned to the frontend rendering the newly generated plan instantly.

### 4. Real-Time Data Synchronization
Instead of forcing users to constantly refresh pages to see if they got a new bid or message, the platform embraces modern real-time paradigms. While initial loads are heavily Server-Side Rendered (SSR) for SEO and speed, interactive components (like the Contractor Marketplace or the Chat interface) utilize client-side polling and Supabase Realtime (WebSockets) to instantly push new database rows (like a new chat message) directly into the user's UI without a hard refresh.

## 🛡️ Uncompromising Data Integrity
To protect against fraud or disputes between clients and contractors, the backend employs a strict **Immutable Audit Logger**. Every API route wraps its execution in a `writeAuditLog` utility. 

If a contractor changes a bid, or an admin deletes a toxic user, a secure service-role key writes an event log detailing the User Matrix ID, the timestamp, the action context, and the metadata payload. This table strictly denies any `UPDATE` or `DELETE` SQL commands, ensuring that the historical timeline of the platform can never be altered or erased by any user.

---
<p align="center">
  <i>Engineered with an obsession for performance, security, and exceptional user experience.</i><br/>
  <b>Designed & Developed by Nouraiz Virk </b>
</p>
