# 📄 ATS Resume Checker

A Streamlit app that scores your resume for ATS (Applicant Tracking System) friendliness and suggests concrete improvements, powered by Google's Gemini Flash model.

## Features
- Upload a resume as **PDF, DOCX or TXT**
- Optional **job description** for keyword matching
- ATS score out of 100 with a category breakdown
- Strengths, weaknesses, missing keywords
- Prioritized improvements and bullet-point rewrite examples
- Download the report as JSON

> Scores are AI estimates, not the output of a real ATS. Use them as guidance.

## Run locally
1. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
2. Install and run:
   ```bash
   pip install -r requirements.txt
   streamlit run app.py
   ```
3. Paste your key in the sidebar, or set it ahead of time:
   - Environment variable: `GEMINI_API_KEY=your_key`
   - Or create `.streamlit/secrets.toml` with:
     ```toml
     GEMINI_API_KEY = "your_key"
     ```

Optional: set `GEMINI_MODEL` (default `gemini-2.5-flash`) if you want a different Gemini model.

## Deploy on Streamlit Community Cloud
1. Push this repo to GitHub (never commit your API key or `secrets.toml`).
2. Go to [share.streamlit.io](https://share.streamlit.io), click **Create app**, and pick your repo, branch `main`, and main file `app.py`.
3. Open **Advanced settings → Secrets** and add:
   ```toml
   GEMINI_API_KEY = "your_key"
   ```
4. Click **Deploy**.

## Project structure
```
app.py             # Streamlit app
requirements.txt   # Python dependencies
README.md          # This file
```

## Limitations
- Scanned/image-only PDFs can't be read; use a text-based PDF or DOCX.
- Very long resumes are truncated to the first ~20,000 characters.
