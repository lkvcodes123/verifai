# VerifAI

**HackSB 2025 winner — Varied Prizes**

A Python desktop prototype that turns video audio into a transcript and uses AI to analyze its claims. Built as a team hackathon project.

[View the project and award on Devpost](https://devpost.com/software/tick-tock-check) · [HackSB 2025](https://hacksb.devpost.com/)

## How it works

1. Enter a YouTube or TikTok video URL in the Tkinter interface.
2. Download the video with yt-dlp.
3. Extract its audio with MoviePy.
4. Transcribe the audio using SpeechRecognition's Google service.
5. Send the transcript to OpenAI's GPT-4o model and display the analysis.

The interface includes progress indicators and a scrollable transcript/results panel. Text-to-speech support is present in the source but is not enabled in the processing flow.

## Team

As credited on the Devpost submission:

- [Lakshan Kaushik Vinooth](https://devpost.com/lakshanvinooth)
- [Wasim Vorvoi](https://devpost.com/wasimvorvoi)
- [Abdurrahman Aly](https://devpost.com/aaly0177)
- [Devi kanumilli](https://devpost.com/devxko)

## Setup

Use a Python environment with Tkinter available. Python 3.10 or 3.11 is a reasonable starting point for this legacy prototype. FFmpeg is required for media processing; video-site support also depends on yt-dlp and the site's current restrictions.

```sh
python -m venv .venv
```

Activate the environment:

```sh
# macOS / Linux
source .venv/bin/activate

# Windows PowerShell
.venv\Scripts\Activate.ps1
```

Install dependencies:

```sh
python -m pip install -r requirements.txt
```

Set `OPENAI_API_KEY` in your environment before starting the app. Use your own key; do not put it in source files or commit it to GitHub.

```sh
# macOS / Linux
export OPENAI_API_KEY='YOUR_API_KEY'

# Windows PowerShell
$env:OPENAI_API_KEY = 'YOUR_API_KEY'
```

Launch from the project directory:

```sh
python gui.py
```

The code retains the hackathon-era OpenAI and MoviePy interfaces, so `requirements.txt` limits those packages to their compatible major versions. API access, network connectivity, and any applicable usage charges are required. The app does not load `.env` files automatically.

## Prototype limitations

- This version asks an AI model to assess the transcript. It does **not** perform live web search, retrieve supporting sources, or guarantee factual accuracy.
- Speech recognition and AI analysis send audio/transcript data to external services.
- Long videos and network calls can make the desktop interface unresponsive. Short clips are the intended starting point.
- The app uses fixed `video.mp4` and `audio.wav` files in its working directory, so run it in its own folder and avoid simultaneous instances.
- Downloading depends on platform availability and restrictions. Transcription or API failures can prevent a complete result.

## Repository preparation

The supplied hackathon source is preserved with small publishing changes: the embedded API key was replaced with an environment variable, a missing-key message was added, and the progress text was corrected to avoid claiming web search. No live transcription, paid API call, or end-to-end desktop run was performed during import. The Python source passed a syntax check.

Future work: source-backed verification, more robust error handling, background processing, and a web interface.
