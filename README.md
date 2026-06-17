# ERP Assistant — Frontend

Streamlit chat UI for the ERP Assistant backend.

## Setup

```bash
pip install -r requirements.txt
```

## Configuration

| Variable | Purpose |
|---|---|
| `BACKEND_URL` | Backend base URL. Default `http://localhost:8000`. For RunPod: `https://<ENDPOINT_ID>.api.runpod.ai` |
| `API_KEY` | Bearer token sent as `Authorization: Bearer <API_KEY>`. Required only if the backend sets `API_KEY`. |

**Locally**, copy `.env.example` to `.env` and fill in the values — the app loads
`.env` automatically (via `python-dotenv`). You can also override per-run with
inline env vars.

### Local FastAPI mode
```bash
cp .env.example .env   # then edit if needed; defaults to http://localhost:8000
streamlit run streamlit_app.py
```

### RunPod mode
Set in `.env`, or inline:
```bash
BACKEND_URL=https://<ENDPOINT_ID>.api.runpod.ai API_KEY=your_key \
  streamlit run streamlit_app.py
```

## Deploy (Streamlit Community Cloud)

Streamlit Cloud does **not** read `.env`. Instead, paste the same `KEY = value`
lines into the dashboard — Streamlit exposes them as environment variables, so
the app reads them with `os.getenv` exactly like local.

1. Push this folder as its own repo
2. Go to [share.streamlit.io](https://share.streamlit.io) → New app
3. Set main file to `streamlit_app.py`
4. Add `BACKEND_URL` and `API_KEY` under **Settings → Secrets**, e.g.:
   ```toml
   BACKEND_URL = "https://<ENDPOINT_ID>.api.runpod.ai"
   API_KEY = "your_key"
   ```
