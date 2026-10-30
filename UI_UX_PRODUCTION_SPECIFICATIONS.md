# UI/UX Production Specifications & Frontend Architecture
**Panda Labs AI SaaS MVP Portfolio & Master Showcase**
*Target Valuation Tier: $3,500 – $15,000+ Production Client Deliverables*
*Author: Pixel (Frontend Engineer)*

---

## 1. Executive Summary & Design System Foundations

This specification defines the production-grade frontend engineering architecture, styling tokens, responsive behaviors, component states, and micro-interactions for the Panda Labs 5-app portfolio and Master Showcase. The objective is to elevate existing demo prototypes into commercial-grade software assets capable of commanding premium Upwork enterprise contract values.

### 1.1 Global Design Language: Dark Precision Glassmorphism
The visual system employs deep midnight-slate backgrounds accented with semi-translucent backdrop-filtered surfaces, ultra-thin luminescent borders (1px 8–12% white alpha), and high-contrast semantic accents.

#### Core CSS Design Tokens (`:root`)
```css
:root {
  /* Surface Color Primitives */
  --bg-canvas: #07090e;
  --bg-surface-1: rgba(17, 24, 39, 0.75);
  --bg-surface-2: rgba(30, 41, 59, 0.65);
  --bg-surface-elevated: rgba(31, 41, 55, 0.85);
  --bg-modal: rgba(10, 15, 26, 0.95);

  /* Border & Rim Light Tokens */
  --border-subtle: rgba(255, 255, 255, 0.08);
  --border-default: rgba(255, 255, 255, 0.12);
  --border-active: rgba(99, 102, 241, 0.5);
  --glass-highlight: inset 0 1px 0 0 rgba(255, 255, 255, 0.1);

  /* Typography Colors */
  --text-primary: #f8fafc;
  --text-secondary: #94a3b8;
  --text-tertiary: #64748b;
  --text-inverse: #020617;

  /* Semantic Palettes */
  --accent-indigo: #6366f1;
  --accent-indigo-hover: #4f46e5;
  --accent-cyan: #06b6d4;
  --success-emerald: #10b981;
  --warning-amber: #f59e0b;
  --danger-rose: #f43f5e;

  /* Elevation Shadows */
  --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.4);
  --shadow-md: 0 4px 16px -1px rgba(0, 0, 0, 0.5), 0 2px 4px -2px rgba(0, 0, 0, 0.5);
  --shadow-lg: 0 12px 32px -4px rgba(0, 0, 0, 0.6), 0 4px 8px -2px rgba(0, 0, 0, 0.4);
  --shadow-modal: 0 24px 64px -12px rgba(0, 0, 0, 0.8);
  --glow-accent: 0 0 24px -4px rgba(99, 102, 241, 0.35);

  /* Timing & Motion Functions */
  --ease-snappy: cubic-bezier(0.16, 1, 0.3, 1);
  --ease-smooth: cubic-bezier(0.4, 0, 0.2, 1);
  --duration-fast: 150ms;
  --duration-normal: 250ms;
  --duration-slow: 400ms;
}
```

### 1.2 Responsive Breakpoint Architecture
All layouts strictly support viewports from 360px up to 1440px+:
- **Mobile (360px – 640px):** Single-column flex/grid stack, min 44px touch targets, sticky compact bottom/top toolbars, full-bleed modal sheets.
- **Tablet (641px – 1024px):** 2-column adaptive flow, collapsible sidebars into bottom drawers, auto-scrolling horizontal overflow tables with boundary indicators.
- **Desktop (1025px – 1440px+):** Fixed multi-pane workspaces (e.g. DocuQuery split-pane), persistent navigation, multi-column dashboard KPI arrays.

---

## 2. Specification: Master Portfolio Showcase (`index.html`)

### 2.1 Purpose & Commercial Framing
Panda Labs client-facing portfolio landing page designed for Upwork enterprise clients seeking turnkey $3,500 – $15,000+ AI SaaS systems delivered in 2–4 weeks.

### 2.2 Component Hierarchy & Specifications
1. **Hero Section:**
   - **Upwork Top-Rated Agency Pill:** Radial pulse glow (`animate-pulse`) with live status text (*Panda Labs • Top 1% AI Engineering Agency*).
   - **Key Metrics Grid:** 3 mini-stat badges (*2–4 Week Delivery*, *Zero Cloud Lock-in*, *Production-Ready FastAPI + Next.js*).
2. **Category Filter Bar:**
   - Pills: `All Solutions`, `B2B Sales`, `LegalTech`, `FinTech`, `HealthTech`, `Creative AI`.
   - Interaction State: Clicking a pill filters grid cards instantly with CSS fade/scale animation without layout jumps.
3. **Showcase Grid Cards:**
   - Glassmorphic card surface with hover elevation (`transform: translateY(-4px)`), ambient gradient border highlight.
   - Deliverable Valuation Chip: Semantic badge displaying estimated contract valuation (`$4,500 – $9,000`).
   - Two CTA Buttons per card:
     * *Launch Interactive Demo →* (Opens modal with live iframe preview).
     * *Tech Deep Dive ℹ* (Slides open architectural drawer detailing stack, DB schema, and API latency).
4. **Interactive Demo Preview Modal:**
   - Fullscreen viewport container with blurred backdrop.
   - **Responsive Device Switcher:** Toolbar with buttons for `Desktop (100%)`, `Tablet (768px)`, and `Mobile (375px)`.
   - Device frame emulation with centered viewport alignment, realistic bezels, and viewport dimension indicators.
   - External link button (*Open Fullscreen in New Tab ↗*).
5. **Architectural Deep Dive Drawer:**
   - Slide-over sheet from right margin detailing backend stack, vector models, data pipelines, and security guardrails for each project.

---

## 3. Specification: LeadScout AI (`01-leadscout-ai/index.html`)

### 3.1 Domain
Autonomous B2B Prospect Enrichment & Outreach Dashboard ($4,500 – $9,000 MVP).

### 3.2 UI/UX States & Component Specifications
1. **Pipeline Metric Banner:**
   - 4 glass KPI cards: *Active Prospects (1,248)*, *Enriched % (86.4%)*, *Buying Signals Detected (312)*, *Available API Credits (3,840)*.
   - Shimmer animation on credit consumption.
2. **Enrichment Action & Progress Micro-Interaction:**
   - *Batch AI Enrichment* button with loading spinner state and button text toggle (*⚡ Mining Buying Intent...*).
   - Leads transition row-by-row from `Pending` (amber badge) to `Enriched` (emerald badge) with a subtle green flash highlight.
3. **Slide-Out Prospect Lead Drawer:**
   - Triggered via *Inspect AI Hook* action button.
   - Details pane: Avatar, verified email with copy icon, buying intent rationale, and custom generated cold email hook.
   - Copy Action: Native `navigator.clipboard` integration paired with custom UI Toast Notification (*Copied cold email hook to clipboard*), eliminating disruptive native browser alerts.
4. **Table States:**
   - *Search Input:* Debounced instant text filter across Name, Company, and Intent.
   - *Empty State:* Graceful fallback graphic when search yields 0 matches (*No prospects found matching "query"* with clear button).

---

## 4. Specification: DocuQuery AI (`02-docuquery/index.html`)

### 4.1 Domain
Enterprise Legal & Contract Intelligence Portal ($6,000 – $14,000 MVP).

### 4.2 Split-Pane Layout & Citation Interaction
1. **Split-Screen Workspace:**
   - Left Pane (48% width on desktop, 100% on mobile via tab toggle): Document Viewer styled as high-contrast legal paper with clean typography.
   - Right Pane (52% width): Citations-grounded conversational RAG assistant.
2. **Citation-Grounding Jump & Flash Highlight:**
   - User query generates assistant response containing citation anchor tag (*e.g., Jump to §14.2 Citation*).
   - On click: Smooth scrolls left document container to exact bounding element, executes 2-second glowing amber highlight animation (`@keyframes citationPulse`), and draws focus.
3. **Document Management Sidebar:**
   - Indexed document list with chunk counters (*42 Pages • 186 Chunks Indexed*) and pgvector HNSW query latency badge (*⚡ 42ms*).
   - Simulated upload modal with drag-and-drop zone and simulated vectorization progress bar.

---

## 5. Specification: MetricFlow (`03-metricflow/index.html`)

### 5.1 Domain
FinTech Subscription Analytics & ML Churn Prediction ($5,000 – $11,000 MVP).

### 5.2 Dynamic Visualizations & Data Modes
1. **Live Stripe vs. Sandbox Mode Toggle:**
   - Segmented pill control toggling production Stripe telemetry vs. seed sandbox simulation.
   - Smoothly interpolates KPI numbers (*$64,820 MRR* vs. *$14,200 MRR*) and updates Chart.js line dataset without re-mounting canvas.
2. **Interactive Charting:**
   - MRR Growth Spline: Gradient area fill (`rgba(99, 102, 241, 0.15)` to transparent), smooth tension curve (0.35), custom tooltip formatting with dollar values.
   - Plan Tier Doughnut: Segmented breakdown with clean legend below.
3. **High-Value Churn Risk Radar:**
   - Table sorting high-risk accounts by behavioral decay (*High Risk / 34 Health Score*).
   - Action triggers per row: *Dispatch CSM*, *Send Dunning SMS*, *Offer Enterprise*.
   - Global CTA: *Trigger Auto-Retention Playbook* opens confirmation modal previewing scheduled outreach.

---

## 6. Specification: ClinicPulse (`04-clinicpulse/index.html`)

### 6.1 Domain
HealthTech Patient Intake & Automated Clinical Triage Portal ($4,000 – $8,500 MVP).

### 6.2 3-Step Wizard & Clinical Stepper Architecture
1. **Stepper Header:**
   - 3 visually connected step circles: `1. Patient Intake` → `2. AI Triage & Slot` → `3. Confirmation`.
   - Active, completed (checkmark), and upcoming states with connecting progress track.
2. **Step 1 (Demographics & Symptoms):**
   - Clean form layout: Name, SMS phone, visit reason dropdown, and freeform symptom textarea.
   - Live validation requiring required fields before unlocking Step 2.
3. **Step 2 (AI Clinical Triage & Dynamic Booking):**
   - Triage Urgency Assessment Box: Dynamic severity color (*Moderate Urgency — Schedule within 48h*) and recommended medical specialist.
   - Interactive Slot Grid: Time chips with radio selection highlight (`09:00 AM`, `10:30 AM`, etc.).
4. **Step 3 (Confirmation & Calendar Integration):**
   - Success state graphic with confirmed appointment overview.
   - Dispatched SMS preview box showing live simulated text alert.
   - 1-click `.ics` calendar file generator for Google Calendar / Apple iCal download.
5. **Collapsible Admin Queue Toggle:**
   - Header button toggling an off-canvas drawer showing hospital staff live triage queue and room utilization stats.

---

## 7. Specification: BrandForge AI (`05-brandforge/index.html`)

### 7.1 Domain
MarTech Autonomous Multi-Channel Social Content Engine ($3,500 – $7,500 MVP).

### 7.2 Multi-Format Engine & Live Asset Customizer
1. **Dual Column Studio Layout:**
   - Left Column: Campaign Brief Controls (Brand name, offer theme, tone of voice, and interactive primary brand color picker).
   - Right Column: Multi-channel preview switcher and live banner canvas.
2. **Multi-Format Preview Tabs:**
   - Tabs: `LinkedIn Thought Leadership`, `Twitter / X Viral Thread`, `Instagram Caption & Tags`.
   - Character and token counters per channel with instant copy button.
3. **Live SVG / DOM Banner Generator with Real-Time Hue Sync:**
   - Changing the primary brand color input (`<input type="color">`) dynamically updates the banner border, accent badges, and gradient glow in real-time.
4. **1-Click Export Pack:**
   - Header export button generating a consolidated campaign asset zip bundle simulation with toast confirmation.

---

## 8. Universal Accessibility & Micro-Interaction Guidelines

1. **Keyboard Accessibility (WCAG 2.1 AA):**
   - Visible focus ring on all interactive elements: `outline: 2px solid var(--accent-indigo); outline-offset: 2px;`.
   - Accessible ARIA attributes (`aria-expanded`, `aria-controls`, `role="dialog"`, `aria-modal="true"`).
   - Modal focus trapping and `Escape` key close handlers across all dialogs and drawers.
2. **Non-Blocking Feedback (Replacing Native Alerts):**
   - All legacy JavaScript `alert()` and `confirm()` calls are replaced with unified in-app toast notifications featuring auto-dismiss timers (3500ms) and action icons.
3. **Touch Friendliness:**
   - All interactive targets (buttons, pills, tabs) conform to minimum 44px x 44px tap area on viewports <= 640px.
