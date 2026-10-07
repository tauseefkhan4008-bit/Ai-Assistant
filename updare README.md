# 📄 ATS Resume Checker

A Streamlit app that scores a resume for ATS (Applicant Tracking System) compatibility and gives concrete improvement tips, powered by Google Gemini Flash.

## Features
- Upload a resume as **PDF, DOCX or TXT**
- Optional **job description** for a role-specific score
- Overall **ATS score (0-100)** plus scores per section
- Strengths, weaknesses, missing keywords, formatting issues
- Actionable improvements with rewritten examples
- Download the report as JSON

## Run locally
```bash
git clone <your-repo-url>
cd <your-repo>
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Get a free API key at https://aistudio.google.com/apikey, then either:

- paste it into the app sidebar, **or**
- create `.streamlit/secrets.toml` (never commit this file):
  ```toml
  GEMINI_API_KEY = "your-key-here"
  # GEMINI_MODEL = "gemini-2.5-flash"   # optional
  ```

Start the app:
```bash
streamlit run app.py
```

## Deploy on Streamlit Community Cloud
1. Push `app.py`, `requirements.txt` and `README.md` to a GitHub repo.
2. Go to https://share.streamlit.io and sign in with GitHub.
3. Click **Create app**, pick your repo, branch `main`, main file `app.py`.
4. Open **Advanced settings → Secrets** and add:
   ```toml
   GEMINI_API_KEY = "your-key-here"
   ```
5. Click **Deploy**.

## Notes
- Scanned/image-only PDFs have no extractable text; use a text-based PDF or DOCX.
- The resume text is sent to Google's Gemini API. Don't upload anything you aren't comfortable sharing.
- The score is an AI estimate, not the output of a real ATS.
- To use another Gemini model, set `GEMINI_MODEL` in secrets.

## Project structure
```
app.py             # Streamlit app
requirements.txt   # dependencies
README.md
```
