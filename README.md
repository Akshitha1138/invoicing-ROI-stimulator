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
