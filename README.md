# Invoicing ROI Simulator

This repository contains a minimal, ready-to-run prototype for the Invoicing ROI Simulator:
- Server: Express.js server with simulation, scenario storage (file-based), and PDF report generation via Puppeteer.
- Client: Minimal Create-React-App front-end that calls the server APIs.

## Quick Start (local)

### Server
1. cd server
2. npm install
3. node server.js
Server runs at http://localhost:4000

Important: Puppeteer will download Chromium during `npm install`. If you're deploying to some hosts, ensure the environment supports headless chrome. Alternatively, you can replace puppeteer with `html-pdf` or `pdfkit`.

### Client
1. cd client
2. npm install
3. npm start
Open http://localhost:3000

## Notes & Security
- Internal constants and biasing are intentionally kept on the server in `utils/calculations.js`.
- The report endpoint requires a valid email in the request body, but the server does not send any real email.
- Scenario data is stored in `server/db/storage.json`.

## Deploying
- Backend can be deployed to platforms supporting Node.js (Render, Heroku, Railway). Ensure `PUPPETEER_SKIP_CHROMIUM_DOWNLOAD` is not set if you need Chromium.
- Frontend can be built and deployed to Netlify, Vercel, or served via static hosting.

- Invoicing ROI Simulator — Python Version

This repository contains a minimal, ready-to-run Python prototype for the Invoicing ROI Simulator.

Frontend & Backend: Single Streamlit app (app.py) handling inputs, live ROI calculation, scenario storage, and PDF report generation.

Database: SQLite (db/scenarios.db) for scenario persistence.

PDF Generation: WeasyPrint generates reports from HTML templates.

Quick Start (Local)
1. Clone / Extract Repository
git clone <your-repo-url>
cd roi_simulator_full_docker

2. Install Dependencies
pip install -r requirements.txt


Installs Streamlit, WeasyPrint, pandas.

Note: WeasyPrint may require additional system dependencies like libffi or cairo depending on your OS.

3. Run the App
streamlit run app.py


Streamlit will start a local server.

Terminal prints:

Local URL: http://localhost:8501
Network URL: http://<your-network-ip>:8501


Open the Local URL in your browser.

4. Using the App

Fill in the inputs:

Invoice Volume

Staff Count

Average Wage per Staff

Email (optional — only for report gating)

Click “Calculate ROI” → results display live.

Save Scenario → persists scenario in db/scenarios.db.

Generate PDF Report → generates a PDF in the project folder (or browser if updated).

5. Scenario Management

All saved scenarios are displayed in the Streamlit UI.

Scenarios are stored in SQLite for persistence.

You can manually inspect using:

sqlite3 db/scenarios.db
sqlite> SELECT * FROM scenarios;

Notes & Security

Internal constants and biasing are kept in calculations.py.

Email input is only for gating PDF generation; no real email is sent.

Scenario data persists locally via SQLite.

PDF reports are generated locally, no server-side emailing.

Optional: Docker Deployment

The project includes a Docker setup:

docker-compose up --build


Runs Streamlit app in a container.

App available at http://localhost:8501

SQLite database persists via volume ./db:/app/db.

Deploying

Local: Run directly with streamlit run app.py

Docker: Use docker-compose up --build

Cloud Deployment: Streamlit apps can be deployed to:

Streamlit Cloud (https://streamlit.io/cloud
)

Render / Railway (using Docker)

Project Structure
/roi_simulator
 ├─ app.py            # Streamlit frontend + backend
 ├─ calculations.py   # ROI calculations and bias factor
 ├─ db.py             # SQLite scenario storage
 ├─ report.py         # PDF generation via WeasyPrint
 ├─ requirements.txt  # Python dependencies
 ├─ Dockerfile        # Container setup
 ├─ docker-compose.yml
 └─ db/
      └─ scenarios.db


✅ This Python version replaces Node.js + React entirely, keeping all functionality:

Live ROI calculations

Scenario save/load/delete

PDF report generation (gated by email)

Optional Docker deployment
