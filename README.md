# 🏋️ AI Gym Trainer

A real-time AI-powered gym trainer that uses computer vision to track your exercise form and provides live voice coaching — built with Streamlit, MediaPipe, and Groq's LLM.

## Features

- **Real-time pose detection** using MediaPipe's Pose Landmarker
- **Live rep and set counting** with automatic form analysis
- **AI voice coaching** powered by Groq (LLaMA 3.3) and Google Text-to-Speech
- **Multiple exercises supported:**
  - Squats
  - Push-ups
  - Biceps Curls (Dumbbell)
  - Shoulder Press
  - Lunges
- **Workout history tracking** with a local SQLite database
- **Simple username-based login** — no account creation needed

## Tech Stack

- **Frontend/App:** Streamlit + streamlit-webrtc
- **Computer Vision:** MediaPipe (Pose Landmarker)
- **AI Coaching:** Groq API (LLaMA 3.3 70B)
- **Text-to-Speech:** gTTS (Google Text-to-Speech)
- **Database:** SQLite
- **Package Management:** uv

## Getting Started

### Prerequisites
- Python 3.12+
- A [Groq API key](https://console.groq.com/keys) (free)

### Installation

1. Clone the repository
```bash
   git clone https://github.com/Git-Amann/ai-gym-trainer.git
   cd ai-gym-trainer
```

2. Create a virtual environment and install dependencies
```bash
   uv venv --python 3.12
   .venv\Scripts\activate
   uv pip install -r requirements.txt
```

3. Download the pose detection model
```bash
   Invoke-WebRequest -Uri "https://storage.googleapis.com/mediapipe-models/pose_landmarker/pose_landmarker_full/float16/latest/pose_landmarker_full.task" -OutFile "ml_models\pose_landmarker_full.task"
```

4. Set up your environment variables
   Create a `.env` file in the root directory:
GROQ_API_KEY=your_groq_api_key_here

5. Run the app
```bash
   uv run streamlit run main.py
```

## Project Structure
AI Gym Trainer/
├── core/               # Base exercise logic
├── detectors/          # Exercise-specific detection logic
├── ml_models/          # Pose landmarker model
├── services/
│   ├── auth/           # Login wall
│   ├── coaching/       # LLM + TTS + voice pipeline
│   ├── config/         # Workout configuration
│   ├── persistence/    # Database operations
│   ├── state/          # Session state defaults
│   ├── tracking/       # Metrics tracking
│   ├── ui/             # Styling and font loading
│   └── vision/         # Video processing
├── static/              # CSS and font assets
├── main.py              # App entry point
└── requirements.txt

## How It Works

1. Enter a username to start a session
2. Choose your exercise, set count, and reps per set
3. Click **Start Workout** to activate your camera
4. The app tracks your pose in real-time and counts reps automatically
5. AI coach provides voice feedback on form issues and milestones
6. View your workout history anytime in the app

## License

This project is for educational purposes.
