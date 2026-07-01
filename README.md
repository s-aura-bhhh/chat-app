# Anonymous Chat

A real-time, anonymous group chat app with persistent message history and a dark/light theme toggle.

## Tech Stack

- **Backend:** Flask + Flask-SocketIO (WebSocket-based real-time messaging)
- **Database:** MongoDB Atlas (message persistence, timestamped in IST)
- **Frontend:** HTML, CSS, vanilla JavaScript, Bootstrap 5
- **Real-time layer:** Socket.IO (client ↔ server bidirectional events)

## How It Works

- On connect, the server loads full chat history from MongoDB and emits it to the client (`load_messages`).
- New messages are sent via a `message` Socket.IO event, stored in MongoDB, and **broadcast** to all connected clients in real time — no page refresh needed.
- Nicknames are stored client-side in `localStorage` and attached to each outgoing message.
- Timestamps are stored in UTC and converted to IST for display.
- A theme toggle switches between dark/light CSS states, purely client-side.

## Run Locally

```bash
pip install -r requirements.txt
python app.py
```

Set `MONGO_URI` and `SECRET_KEY` as environment variables (falls back to defaults if unset). Visit `http://localhost:5000`.

## Project Structure

```
├── app.py              # Flask app + Socket.IO event handlers
├── templates/index.html
└── static/
    ├── style.css
    └── script.js
```
