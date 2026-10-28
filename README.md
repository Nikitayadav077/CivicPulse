# CivicPulse — Open-Source AI Smart City Command Center

**Empowering citizens to fix their neighborhoods in one tap while giving municipal authorities a nationwide, AI-driven telemetry and dispatch dashboard.**
--

##Live Prototype & Deployment Links 

* Live Frontend Application (Netlify):** [https://groundtruthers.netlify.app](https://groundtruthers.netlify.app)
* Live Backend API Server (PythonAnywhere):** [https://anshitajoshi.pythonanywhere.com](https://anshitajoshi.pythonanywhere.com)
* Demo Admin Portal PIN:** `9675059250`

---

## The Problem & Our Vision

Every day across India, citizens walk past broken streetlights, deep potholes, water leaks, and overflowing sanitation hazards. While citizens want to report these issues, existing municipal portals are complex, single-language, and disconnected. Meanwhile, city administrators lack real-time visibility into which state, city, or neighborhood requires urgent repair crews first.

**CivicPulse** bridges this gap by turning every citizen's smartphone into an intelligent civic sensor and providing authorities with a live **National India Telemetry Map & AI State Command Center**.

---

## Open-Source & Open-Weight AI Architecture
*(Built for the **DigitalOcean Best Open-Source AI Project** Category)*

Instead of relying on closed-source, proprietary black-box APIs, CivicPulse is built around a custom **Open-Weight AI Model Harness** (`call_open_weight_llm`) in our Python Flask backend that integrates open-weight vision and language models:

1. **Open-Weight Multimodal Vision Classification (`Llama-3.2-11B-Vision-Instruct`):**
   * **Endpoint:** `POST /api/classify`
   * **How it works:** When a citizen snaps a photo of a civic hazard, the image payload is processed through our open-weight vision harness to automatically classify the issue into actionable municipal categories: *Road Damage*, *Electrical Danger*, *Water Leak*, *Sanitation*, or *Other*.
2. **Municipal Triage Agent Skill (`Gemma-2-9B-IT`):**
   * **Endpoint:** `POST /api/agent-triage`
   * **How it works:** A custom AI agent skill (`civic-triage-agent-v1`) that ingests live state-level and city-level hazard telemetry from our database, identifies the primary city hotspot and dominant hazard category, and generates an actionable 24-hour crew dispatch and budget prioritization plan.
3. **24/7 Bilingual Open-Weight Gov-Bot Assistant (`Gemma-2-9B-IT` / `Llama-3.1-8B`):**
   * **Endpoint:** `POST /api/govbot`
   * **How it works:** An interactive citizen assistant grounded in live city telemetry (total reports, resolved counts, emergency helplines, and Karma rewards) capable of responding in both **English** and **Hindi**.
4. **Resilient Fail-Safe Model Harness:**
   * Designed for 100% uptime in civic environments—supports live cloud open-weight inference (via Groq / Hugging Face endpoints) with an automatic deterministic local agent fallback so field operations never go offline.

---

## Key Features

### For Citizens (Accessibility & Gamified Civic Engagement)
* **Instant Bilingual Toggle (`EN / HI`):** Seamlessly switches the entire UI and AI Gov-Bot between English and Hindi with a single tap.
* **AI Camera & Auto-Geolocation:** Captures hazard photos, auto-detects the issue category via Vision AI, and reverse-geocodes the user's live GPS coordinates into their exact **State** and **City/District**.
* **Gamified Civic Karma System:** Citizens earn **+50 Karma Points** per reported hazard and level up from *Citizen* to *City Guardian*.
* **Community Board & Crowd-Prioritization:** Citizens can view local issues reported in their city and **Upvote** critical hazards so admins know what to fix first.
* **4-Stage Resolution Timeline:** Visual progress tracker (*Reported* $\rightarrow$ *Verified* $\rightarrow$ *Assigned* $\rightarrow$ *Resolved*) with scheduled crew dates and toast notifications.
* **Live City Campaigns & SOS Quick-Dial:** Citizens receive real-time broadcasts for local cleanliness/awareness drives and have 1-tap access to emergency lines (Police `112`, Fire `101`, Medic `102`, Civic `155304`).

### For Administrators (National Telemetry & Dispatch Portal)
* **Interactive India State & City Command Map:**
  * Displays live report counters pinned across all Indian states (e.g., *Delhi*, *Maharashtra*, *Karnataka*, *Uttar Pradesh*).
  * **State-to-City Drill-Down:** Clicking on any state (such as **Maharashtra**) dynamically zooms the map into that state, drops city-level pins (*Mumbai*, *Pune*, *Nagpur*, *Nashik*), and displays a percentage breakdown of which city the problems came from.
  * Clicking a specific city filters the hazard tickets below the map in real time.
* **One-Click Open-Weight AI Action Plan:** Executes the `Gemma-2-9B` Triage Skill on the currently selected state to recommend immediate crew deployment.
* **Live Dispatch Queue & Campaign Broadcaster:** Admins can update ticket statuses, schedule repair dates, open exact GPS pins in Google Maps, and push live event banners to all citizen dashboards.

---

## Technology Stack

* **Frontend:** HTML5, Tailwind CSS, Vanilla JavaScript (ES6+), Leaflet.js (Interactive Geo-Telemetry), FontAwesome Icons, Progressive Web App (PWA) Manifest.
* **Backend:** Python 3, Flask, Custom CORS Middleware, RESTful API Architecture.
* **AI & Agent Harness:** Open-Weight `Llama-3.2-11B-Vision` (Image Classification) & `Gemma-2-9B-IT` (Gov-Bot & Municipal Triage Agent Skill).
* **Database:** Lightweight JSON Flat-File Telemetry Stores (`database.json`, `users.json`, `campaign.json`) for rapid zero-latency reads/writes.
* **Hosting:** Netlify (Frontend CDN) & PythonAnywhere (WSGI Python Backend).

## Local Installation & Setup

To run CivicPulse locally on your machine:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/sidsidhu-ui/CivicPulse.git
   cd CivicPulse
   ```

2. **Install Flask & start the Python backend:**
   ```bash
   pip install flask
   python flask_app.py
   ```
   *(Optional: Export `OPEN_WEIGHT_API_KEY="your_key"` in your environment to enable live cloud open-weight inference).*

3. **Launch the Frontend:**
   * Open `index.html` directly in any modern web browser or serve it via VS Code Live Server.

---

## 📄 License

This project is open-source and released under the **MIT License**.
