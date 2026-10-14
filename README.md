# MindTech AI Support Assistant

A Python chatbot built with **Google Gemini** and **Gradio**. It answers questions about the MindTech product information included in `app.py`.

## Features

- Gemini-powered technical support chat
- Knowledge-base context for four MindTech products
- Product setup and troubleshooting guidance
- Purchase guidance to the official website
- Gradio chat interface with example prompts
- API key loaded from an environment variable
- Render deployment configuration included

## Project structure

```text
mindtech-ai-support-assistant/
├── app.py
├── requirements.txt
├── runtime.txt
├── render.yaml
├── .env.example
├── .gitignore
└── README.md
```

## Requirements

- Python 3.10 or newer (Python 3.11 recommended)
- A Gemini API key from [Google AI Studio](https://aistudio.google.com/apikey)

## Run locally

### 1. Download or clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/mindtech-ai-support-assistant.git
cd mindtech-ai-support-assistant
```

Or download this repository ZIP and extract it.

### 2. Create a virtual environment

Windows PowerShell:

```powershell
py -3.11 -m venv .venv
.venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set your API key

**Windows PowerShell:**

```powershell
$env:GEMINI_API_KEY="YOUR_NEW_GEMINI_API_KEY"
$env:GEMINI_MODEL="gemini-2.5-flash"
```

**macOS/Linux:**

```bash
export GEMINI_API_KEY="YOUR_NEW_GEMINI_API_KEY"
export GEMINI_MODEL="gemini-2.5-flash"
```

You may copy `.env.example` to `.env` for reference, but this project does not automatically load `.env`; set environment variables in your shell or hosting dashboard. Never commit `.env` or a real API key.

### 5. Start the app

```bash
python app.py
```

Open the local URL printed by Gradio, normally `http://127.0.0.1:7860`.

## Deploy to Render

1. Push this project to a GitHub repository.
2. In Render, choose **New + → Web Service** and connect the repository.
3. Render should detect the included `render.yaml`; if asked, choose **Python** as the runtime/language.
4. Use build command `pip install -r requirements.txt`.
5. Use start command `python app.py`.
6. In the Render service's **Environment** settings, add:
   - `GEMINI_API_KEY` = your newly generated Gemini API key
   - `GEMINI_MODEL` = `gemini-2.5-flash`
7. Deploy and open the service URL shown by Render.

The app listens on `0.0.0.0` and uses Render's `PORT` environment variable.

## Deploy to Hugging Face Spaces

Create a new **Gradio** Space, upload `app.py`, `requirements.txt`, and this README, then add `GEMINI_API_KEY` under the Space's **Settings → Variables and secrets → Secrets**. Add `GEMINI_MODEL` as a variable if desired.

## Security notes

- The API key pasted into the original source should be considered exposed. Revoke it in Google AI Studio and create a replacement before deployment.
- Do not store API keys in source code, GitHub commits, screenshots, or public issue reports.
- The included `render.yaml` intentionally does not contain a secret; set it in the Render dashboard.
- Review usage limits and billing settings for your Google AI project.

## Customising the knowledge base

Edit `KNOWLEDGE_BASE` in `app.py` with verified company information. The current product and support details are the information supplied with the original example and have not been independently verified.

## Troubleshooting

- **`GEMINI_API_KEY is not set`**: configure the environment variable and restart the app.
- **Authentication or quota errors**: verify the key in Google AI Studio, API access, and quota.
- **Model not found**: set `GEMINI_MODEL` to a model available to your Gemini API key.
- **Dependency errors**: use Python 3.11 and run `pip install -r requirements.txt` again.
