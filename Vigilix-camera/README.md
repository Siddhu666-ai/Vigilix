# Vigilix Camera (WebWatch)

Turn any old smartphone or device with a camera into a local-network security camera with live browser streaming, recording, and playback.

## Features

- **Live Video Streaming** — Stream real-time video from your phone directly to any browser on your local network.
- **Recording & Playback** — Record live feeds and review saved footage.
- **Multi-Camera Support** — Pair and manage multiple cameras using 6-digit room codes.
- **Local HTTPS** — Runs over HTTPS on your local network using a generated self-signed SSL certificate.

## Tech Stack

- **Backend:** Python, Flask
- **Frontend:** React (`WebWatch/`)

## Project Structure

```text
Vigilix-camera/
├── backend/        # Flask server, database setup, SSL cert generation, and video streaming
├── WebWatch/       # React web interface
└── README.md
```

## Getting Started

### Prerequisites

- Python 3.7+
- Node.js & npm

### 1. Start the Backend

```bash
cd backend
pip install -r requirements.txt
python setup_db.py
python generate_cert.py
python app.py
```

### 2. Start the Frontend

In a separate terminal:

```bash
cd WebWatch
npm install
npm start
```

### 3. Open the App

Navigate to `https://<YOUR_LOCAL_IP>:3000` in your browser.

- **Default login:** `admin` / `123` *(change this before exposing to any untrusted network)*
- To check your local IP manually, run `python get_ip.py` inside `backend/`.

## Usage

1. Open the web interface and log in.
2. Click **Generate Camera Code** to create a 6-digit pairing code.
3. Open the camera page on your phone and enter the 6-digit code.
4. Watch and record the live feed from your browser.

## Troubleshooting

- **SSL / Certificate warnings:** Your browser will warn about the self-signed certificate on first visit—accept/proceed to continue, or re-run `python generate_cert.py` in `backend/`.
- **Can't connect from phone:** Ensure both devices are on the same Wi-Fi network and that your firewall allows incoming connections on the backend/frontend ports.
- **Port already in use:** Stop the conflicting process or change the port configuration before restarting.
