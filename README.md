# JARVIS - AI Voice Assistant

JARVIS is a voice-activated, multi-functional desktop assistant built in Python. By merging a responsive graphical interface with background voice command processing, JARVIS acts as an interactive companion capable of handling local system operations, calling external web APIs, and engaging in human-like dialogue through generative AI.

The assistant operates in two distinct states:
* Sleep Mode: Monitors the microphone with minimal overhead, waiting to catch a designated wake word.
* Active Mode: Wakes up to process diverse voice commands—either executing structural desktop tasks locally or passing queries to a generative model for conversational answers.

---

## Key Features

### Voice Processing & Speech
* Ambient-Aware Wake Detection: Listens continuously for "Hey JARVIS", "JARVIS", or "Okay JARVIS" before unlocking full interaction.
* Text-to-Speech (TTS): Translates text replies back into fluid speech audio dynamically, allowing for a fully hands-free experience.

### Core Intelligence
* Powered by Gemini AI: Uses generative AI models to deliver intuitive, natural language replies for unmapped or generalized queries.
* Session Memory: Persists conversation state locally in a structured JSON file (chat_history.json) to retain contextual knowledge during ongoing discussions.

### Local Desktop Control
* Application Launcher: Spawns standard OS utilities and programs (e.g., Notepad, Chrome, VS Code, Calculator) on command.
* File Assistant: Searches across primary system directories (Desktop, Documents, Downloads) for custom filenames or lists the current project working directory out loud.
* System Actions: Triggers built-in utility operations like locking your workstation interface or initiating timed system power-downs and restarts.

### Modular API Integration
* Weather Forecasts: Connects to OpenWeatherMap to deliver instant atmospheric readings based on local temperature preferences.
* Gmail Engine: Fully configured to handle OAuth 2.0 desktop authorization, enabling you to draft and send emails directly through the official Google API.
* Spotify Playback: Employs spotipy wrapper bindings to inspect live playback media, pause/resume active streams, skip tracks, or pull metadata from an active Premium session.

---

## The Tech Stack

* Language: Python 3.8+
* GUI Framework: Tkinter (Custom dark-theme layout with reactive status indicators)
* Voice-to-Text: speech_recognition (Google Web Speech API backend)
* Text-to-Speech: gTTS (Google Text-to-Speech)
* Audio Mixer: pygame.mixer
* AI SDK: google-genai
* API Clients: spotipy (Spotify Developer API), google-api-python-client (Gmail v1), requests (OpenWeatherMap API)

---

## Prerequisites & Installation

### 1. Clone the Repository

git clone [https://github.com/YOUR_USERNAME/AI-Assistant-main.git](https://github.com/YOUR_USERNAME/AI-Assistant-main.git)
cd AI-Assistant-main

2. Install Dependencies
Install all required platform and API bindings using pip:

pip install speech_recognition gtts pygame google-generativeai python-dotenv google-auth-oauthlib google-auth-httplib2 google-api-python-client spotipy requests

3. Environment Configuration
Create a .env file in the root directory of your project and populate it with your respective keys:

Ini, TOML
API_KEY=your_gemini_api_key_here
WEATHER_API_KEY=your_openweathermap_api_key_here
SPOTIFY_CLIENT_ID=your_spotify_client_id_here
SPOTIFY_CLIENT_SECRET=your_spotify_client_secret_here
SPOTIFY_REDIRECT_URI=http://localhost:8888/callback

4. Setting up Google Cloud for Gmail (Optional)
Head over to the Google Cloud Console.

Create a new project and enable the Gmail API.

Configure the OAuth Consent Screen and create OAuth 2.0 Client IDs selecting Desktop App as the application type.

Download the client secret JSON file, rename it to credentials.json, and place it in the root folder of this project.


Project ArchitectureThis structure matches the layout found in the AI-Assistant-main.zip archive:  

AI-Assistant-main/
│
├── testv5.py                 # Core application running the GUI and background loop
├── test_gmail.py             # Isolated unit testing script for Gmail OAuth & sending
├── test_spotify.py           # Playback controller and authentication test for Spotify
├── test_weather.py           # OpenWeatherMap fetch validation script
│
├── .env                      # Local environment storage for secret API keys (Git ignored)
├── credentials.json          # Google Cloud client secrets downloaded by the developer
├── token.json                # Cached Gmail OAuth user token (Auto-generated)
├── .spotify_cache            # Cached Spotify token refresh credentials (Auto-generated)
├── chat_history.json         # Logged context used by Gemini AI (Auto-generated)
└── README.md                 # Project documentation[cite: 1]

Usage Guide
To kickstart the assistant with its visual dashboard interface, execute the main entry point[cite: 1]:

python testv5.py

Voice Commands
Wake Up JARVIS:

"Hey JARVIS"
"JARVIS"
"Okay JARVIS"
Sleep Mode:

"Go to sleep"
"Sleep mode"
General Queries:

"What's the weather?"
"What time is it?"
"What's the date?"
"Calculate 25 times 4"
Web Commands:

"Open YouTube"
"Open Google"
"Open GitHub"
File Operations:

"Search for [filename]"
"Open folder Desktop"
"List files"
Application Control:

"Open Chrome"
"Launch Spotify"
"Start Calculator"
Spotify Commands:

"Play music"
"Pause music"
"Next song"
"Previous song"
"What's playing?"
System Commands:

"Lock screen"
"Shutdown"
"Restart"
Exit:

"Exit"
"Quit"
"Goodbye"

```markdown
# JARVIS - AI Voice Assistant

JARVIS is a voice-activated, multi-functional desktop assistant built in Python. By merging a responsive graphical interface with background voice command processing, JARVIS acts as an interactive companion capable of handling local system operations, calling external web APIs, and engaging in human-like dialogue through generative AI.

The assistant operates in two distinct states:
* Sleep Mode: Monitors the microphone with minimal overhead, waiting to catch a designated wake word.
* Active Mode: Wakes up to process diverse voice commands—either executing structural desktop tasks locally or passing queries to a generative model for conversational answers.

---

## Key Features

### Voice Processing & Speech
* Ambient-Aware Wake Detection: Listens continuously for "Hey JARVIS", "JARVIS", or "Okay JARVIS" before unlocking full interaction.
* Text-to-Speech (TTS): Translates text replies back into fluid speech audio dynamically, allowing for a fully hands-free experience.

### Core Intelligence
* Powered by Gemini AI: Uses generative AI models to deliver intuitive, natural language replies for unmapped or generalized queries.
* Session Memory: Persists conversation state locally in a structured JSON file (chat_history.json) to retain contextual knowledge during ongoing discussions.

### Local Desktop Control
* Application Launcher: Spawns standard OS utilities and programs (e.g., Notepad, Chrome, VS Code, Calculator) on command.
* File Assistant: Searches across primary system directories (Desktop, Documents, Downloads) for custom filenames or lists the current project working directory out loud.
* System Actions: Triggers built-in utility operations like locking your workstation interface or initiating timed system power-downs and restarts.

### Modular API Integration
* Weather Forecasts: Connects to OpenWeatherMap to deliver instant atmospheric readings based on local temperature preferences.
* Gmail Engine: Fully configured to handle OAuth 2.0 desktop authorization, enabling you to draft and send emails directly through the official Google API.
* Spotify Playback: Employs spotipy wrapper bindings to inspect live playback media, pause/resume active streams, skip tracks, or pull metadata from an active Premium session.

---

## The Tech Stack

* Language: Python 3.8+
* GUI Framework: Tkinter (Custom dark-theme layout with reactive status indicators)
* Voice-to-Text: speech_recognition (Google Web Speech API backend)
* Text-to-Speech: gTTS (Google Text-to-Speech)
* Audio Mixer: pygame.mixer
* AI SDK: google-genai
* API Clients: spotipy (Spotify Developer API), google-api-python-client (Gmail v1), requests (OpenWeatherMap API)

---

## Prerequisites & Installation

### 1. Clone the Repository
```bash
git clone [https://github.com/YOUR_USERNAME/AI-Assistant-main.git](https://github.com/YOUR_USERNAME/AI-Assistant-main.git)
cd AI-Assistant-main

```

### 2. Install Dependencies

Install all required platform and API bindings using pip:

```bash
pip install speech_recognition gtts pygame google-generativeai python-dotenv google-auth-oauthlib google-auth-httplib2 google-api-python-client spotipy requests

```

### 3. Environment Configuration

Create a `.env` file in the root directory of your project and populate it with your respective keys:

```ini
API_KEY=your_gemini_api_key_here
WEATHER_API_KEY=your_openweathermap_api_key_here
SPOTIFY_CLIENT_ID=your_spotify_client_id_here
SPOTIFY_CLIENT_SECRET=your_spotify_client_secret_here
SPOTIFY_REDIRECT_URI=http://localhost:8888/callback

```

### 4. Setting up Google Cloud for Gmail (Optional)

1. Head over to the Google Cloud Console.
2. Create a new project and enable the Gmail API.
3. Configure the OAuth Consent Screen and create OAuth 2.0 Client IDs selecting Desktop App as the application type.
4. Download the client secret JSON file, rename it to `credentials.json`, and place it in the root folder of this project.

---

## Project Architecture

This structure matches the layout found in the `AI-Assistant-main.zip` archive:

```text
AI-Assistant-main/
│
├── testv5.py                 # Core application running the GUI and background loop[cite: 1]
├── test_gmail.py             # Isolated unit testing script for Gmail OAuth & sending[cite: 1]
├── test_spotify.py           # Playback controller and authentication test for Spotify[cite: 1]
├── test_weather.py           # OpenWeatherMap fetch validation script[cite: 1]
│
├── .env                      # Local environment storage for secret API keys (Git ignored)
├── credentials.json          # Google Cloud client secrets downloaded by the developer
├── token.json                # Cached Gmail OAuth user token (Auto-generated)
├── .spotify_cache            # Cached Spotify token refresh credentials (Auto-generated)
├── chat_history.json         # Logged context used by Gemini AI (Auto-generated)
└── README.md                 # Project documentation[cite: 1]

```

---

## Usage Guide

To kickstart the assistant with its visual dashboard interface, execute the main entry point:

```bash
python testv5.py

```

### Supported Voice Directives

| Domain | Voice Command Examples | Description |
| --- | --- | --- |
| **State Control** | "Hey JARVIS", "Wake up", "Go to sleep" | Toggles assistant between Active and Sleep state |
| **General Info** | "What time is it?", "What's the date today?" | Pulls standard system time-date info |
| **Calculation** | "Calculate 450 divided by 5", "What is 12 times 12" | Computes basic algebraic strings safely |
| **Browsing** | "Open YouTube", "Open Google", "Open GitHub" | Spawns target addresses in default system browser |
| **File Systems** | "Search file documentation", "List files", "Open folder Desktop" | Navigates directories and finds local documents |
| **Applications** | "Open Chrome", "Launch VS Code", "Start Calculator" | Automates desktop execution paths via application names |
| **Media** | "Play music", "Pause song", "Next track", "What's playing?" | Modifies Spotify context values over active devices

 |
| **Power Automation** | "Lock screen", "Shutdown", "Cancel shutdown" | Issues low-level OS level administrative instructions |
| **Termination** | "Exit", "Quit", "Goodbye" | Gracefully closes connections and deletes local chat logs |

---

## Notes & Troubleshooting

* Microphone Input: If speech recognition times out instantly, ensure your primary microphone channel is set correctly in your OS properties, and adjust your microphone for ambient background room noise.
* Active Spotify Session: Spotify commands require a Premium account. Furthermore, the official Spotify client application must already be open and active on your machine or device for playback redirection to process properly.


* Offline Support: This setup relies on web endpoints for cloud processing (Gemini, Speech-to-Text, and API hooks). If you need an offline deployment, you will need to replace the core generation modules with local processing libraries like Ollama or vosk and skip the API initialization chains.



```

```

