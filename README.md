# AI Resume Analyzer

A polished resume intelligence platform for PDF analysis, ATS-style scoring, and job-description matching.

The app is designed as a product-style demo with a clean dashboard, structured AI output, local history, exportable reports, and a light/dark theme toggle.

## Live Site

- Deployed site: https://ai-resume-analyzer-bkxh.onrender.com/

## What You Can Do

- Upload a PDF resume for analysis.
- Compare the resume against a job description for keyword alignment and role fit.
- See structured insights such as overall score, ATS readiness, gaps, strengths, and next steps.
- Save recent runs locally in the browser.
- Export the current report as JSON or copy a short summary.
- Switch between light and dark themes.

## Key Features

- Dual analysis modes: resume-only and resume vs JD.
- Structured dashboard output instead of raw markdown.
- Professional UI with responsive layout and motion-based feedback.
- Local history for recent analyses.
- Export and copy actions for quick sharing.
- Theme toggle for light and dark viewing modes.

## Tech Stack

- Frontend: React 19, Vite, framer-motion, custom CSS
- Backend: Node.js, Express, Multer, pdf-parse
- AI: Groq SDK
- Storage: Browser localStorage for demo history

## Project Structure

- [Backend/Server.js](Backend/Server.js) - analysis API and PDF text extraction
- [Frontend/src/App.jsx](Frontend/src/App.jsx) - dashboard UI and theme-aware analysis workspace
- [Frontend/src/App.css](Frontend/src/App.css) - component styling, layout, and responsive polish
- [Frontend/src/index.css](Frontend/src/index.css) - theme tokens and global base styling
- [docs/API_CONTRACT.md](docs/API_CONTRACT.md) - API request and response contract

## How It Works

1. Upload a PDF resume.
2. Optionally paste a job description.
3. The backend extracts resume text and sends it to the AI model.
4. The response is normalized into structured analysis data.
5. The UI renders the report as score cards, lists, and actionable guidance.

## Environment Variables

Backend:

- `GROQ_API_KEY` - required for AI analysis
- `GROQ_MODEL` - optional, defaults to `llama-3.1-8b-instant`
- `CORS_ORIGIN` - optional comma-separated allowed origins
- `PORT` - optional server port, defaults to `5000`

Frontend:

- `VITE_BACKEND_URL` - backend base URL, defaults to `http://localhost:5000`

## Run Locally

1. Install backend dependencies:

   ```bash
   cd Backend
   npm install
   ```

2. Install frontend dependencies:

   ```bash
   cd Frontend
   npm install
   ```

3. Create `Backend/.env`:

   ```bash
   GROQ_API_KEY=your_api_key_here
   GROQ_MODEL=llama-3.1-8b-instant
   CORS_ORIGIN=http://localhost:5173
   PORT=5000
   ```

4. Start the backend:

   ```bash
   cd Backend
   npm start
   ```

5. Start the frontend:

   ```bash
   cd Frontend
   npm run dev
   ```

## API Reference

See [docs/API_CONTRACT.md](docs/API_CONTRACT.md) for the full request and response schema.

## Notes

- This project is a demo-grade product experience, not a production SaaS stack.
- Saved history is browser-local only and does not require user accounts.
- The backend falls back to a local heuristic summary if the AI response is not valid JSON.
