# SpeakEasy ISL — Speech-to-Avatar Prototype

SpeakEasy ISL is a Flutter application and Python backend prototype exploring a path from spoken input to Indian Sign Language (ISL) gloss and a visual pose sequence.

## Processing flow

Audio recording → speech transcription (Whisper) → ISL gloss generation → pose/keypoint sequence → Flutter avatar visualization.

## Main components
- **Flutter app:** records audio, sends it to the backend, and displays the response/animated skeleton.
- **FastAPI backend:** exposes `/speech`, `/gloss`, `/pose`, and `/pipeline` endpoints.
- **Model wrappers:** gloss and pose model loaders are under `backend/models/`.
- **Setup guide:** [SETUP.md](SETUP.md) explains dependency installation, model-weight setup, backend URLs, and troubleshooting.

## Run the Flutter app

Install Flutter and the Android SDK, then run from the repository root:

~~~bash
flutter pub get
flutter run
~~~

## Run the backend

~~~bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload --host 0.0.0.0 --port 8000
~~~

Check `http://localhost:8000/health` and follow [SETUP.md](SETUP.md) to prepare the model weights and point the app at the backend.

## Tech stack
Flutter · Dart · FastAPI · Python · Whisper · PyTorch model wrappers · HTTP/audio recording

## Status and limitations
Review the model setup instructions carefully: model weights and architecture-specific loading may need to be configured before real inference works. Treat generated gloss/pose as an accessibility prototype, not a validated substitute for a fluent ISL interpreter.
