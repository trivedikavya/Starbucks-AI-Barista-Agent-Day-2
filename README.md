# ☕ AQUA - Starbucks AI Voice Agent

**AQUA** is an intelligent, voice-activated AI agent designed to simulate a real-world Starbucks barista experience. It listens to customer orders, understands context, manages order state (drink type, size, milk, extras), and responds with a natural AI voice.

## Features

* **Real-time Speech-to-Text**: Converts user speech into text using **AssemblyAI**.
* **Intelligent Order Management**: Uses **Google Gemini 2.0 Flash** to process natural language, update the order state (JSON), and generate friendly responses.
* **High-Quality Voice Output**: Converts the AI's text response back into speech using **Murf AI** for a realistic conversation.
* **State Persistence**: Tracks the order status (Drink, Size, Milk, Extras) across the conversation and saves completed orders to a JSON file.
* **Interactive UI**: A clean, responsive frontend built with **HTML**, **Tailwind CSS**, and **Vanilla JavaScript** that displays the live order receipt.

## Tech Stack

* **Backend:** Python, FastAPI, Uvicorn
* **AI Services:**
    * **Logic & NLU:** Google Gemini (Gemini-2.0-Flash)
    * **Speech-to-Text (STT):** AssemblyAI
    * **Text-to-Speech (TTS):** Murf AI
* **Frontend:** HTML5, JavaScript (ES6), Tailwind CSS (via CDN)
* **HTTP Client:** Axios

## Project Structure

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

## Setup & Installation
### 1. Clone the Repository
```Bash
git clone <your-repo-url>
cd day-2-starbucks-agent
```

### 2. Backend Setup
Navigate to the backend folder and install the dependencies.

```Bash
cd backend
python -m venv venv
# Windows
venv\Scripts\activate
# Mac/Linux
source venv/bin/activate

pip install -r requirement.txt
```

### 3. Environment Variables
Create a .env file in the backend/ directory and add your API keys:

```Code snippet
GOOGLE_API_KEY=your_gemini_api_key
ASSEMBLYAI_API_KEY=your_assemblyai_api_key
MURF_AI_API_KEY=your_murf_api_key
```

### 4. Run the Backend Server
Start the FastAPI server. It will run on http://0.0.0.0:5000.

```Bash
python main.py
# OR
uvicorn main:app --host 0.0.0.0 --port 5000 --reload
```

### 5. Frontend Setup
Simply open `frontend/index.html` in your browser.

> **Recommended:** Use the "Live Server" extension in VS Code to serve the HTML file to avoid CORS issues with local files.

##  How It Works

1. **Click "Start Ordering"**: The app connects to the backend and welcomes you.
2. **Speak**: Click the Mic button 🎙️ and say your order (e.g., *"I want a Grande Latte with Oat milk"*).
3. **Processing**:
    * The audio is sent to the backend.
    * **AssemblyAI** transcribes the audio to text.
    * **Gemini** analyzes the text, updates the `current_state` JSON, and formulates a reply.
    * **Murf AI** generates audio for the reply.
4. **Response**: The frontend plays the audio response and updates the visual receipt.
5. **Completion**: Once all details (Drink, Size, Milk) are gathered, the order is marked complete and saved to `completed_orders.json`.

##  API Endpoints

* `GET /health`: Checks if the server is running.
* `POST /server`: Generates the initial greeting audio.
* `POST /chat-with-voice`: Handles the full conversation loop (Audio Input -> State Update -> Audio Output).

##  Future Improvements

* Add payment integration simulation.
* Implement WebSocket for lower latency streaming.
* Add multiple voice options for the barista.
