# ☕ AQUA - Starbucks AI Voice Agent

**AQUA** is an intelligent, voice-activated AI agent designed to simulate a real-world Starbucks barista experience. It listens to customer orders, understands context, manages order state (drink type, size, milk, extras), and responds with a natural AI voice.

## 🚀 Features

* **🎙️ Real-time Speech-to-Text**: Converts user speech into text using **AssemblyAI**.
* **🧠 Intelligent Order Management**: Uses **Google Gemini 2.0 Flash** to process natural language, update the order state (JSON), and generate friendly responses.
* **🗣️ High-Quality Voice Output**: Converts the AI's text response back into speech using **Murf AI** for a realistic conversation.
* **📝 State Persistence**: Tracks the order status (Drink, Size, Milk, Extras) across the conversation and saves completed orders to a JSON file.
* **💻 Interactive UI**: A clean, responsive frontend built with **HTML**, **Tailwind CSS**, and **Vanilla JavaScript** that displays the live order receipt.

## 🛠️ Tech Stack

* **Backend:** Python, FastAPI, Uvicorn
* **AI Services:**
    * **Logic & NLU:** Google Gemini (Gemini-2.0-Flash)
    * **Speech-to-Text (STT):** AssemblyAI
    * **Text-to-Speech (TTS):** Murf AI
* **Frontend:** HTML5, JavaScript (ES6), Tailwind CSS (via CDN)
* **HTTP Client:** Axios

## 📂 Project Structure

```bash
day-2-starbucks-agent/
├── backend/
│   ├── main.py              # FastAPI entry point
│   ├── routes.py            # Main logic (STT -> Gemini -> TTS flow)
│   ├── models.py            # Pydantic models
│   ├── completed_orders.json # Database of confirmed orders
│   └── requirement.txt      # Python dependencies
├── frontend/
│   ├── index.html           # User Interface
│   ├── index.js             # Audio recording & API logic
│   └── package.json
└── .env                     # API Keys (Not included in repo)
```
