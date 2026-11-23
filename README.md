# Kayo Bot

A DEPI team coursework chatbot with a Flask interface, a TensorFlow Seq2Seq LSTM response model, and Groq-powered Arabic/English translation around the response pipeline.

## Contribution and credits

Mohamed Ayman curated, merged and cleaned Arabic/English technical Q&A data covering web development, machine learning and deep learning. The model and interface were team work, not his independent implementation.

Credits preserved from the supplied project README:
- Abdelrhman Tarek: data preprocessing and Seq2Seq LSTM model development.
- Hussein Adel: Groq integration and user interface.
- Mohamed Ayman Mohamed: data collection and preparation.
- Mohamed Ayman Mahmoud: Azure deployment.

The supplied README points to the original team repository, `Abdelrhman-T/ChatBot`. This copy preserves the team attribution. No new software license has been added on behalf of the contributors.

## Status

Source snapshot, not a hosted demo. The required trained model and processed dataset are intentionally not committed. A clean-machine end-to-end run is not verified. The old Azure deployment is not represented as live. The team-reported BLEU result is not reproduced by this repository, so it is not used as a benchmark here.

## Local setup

Use Python 3.10, matching the supplied project setup:

```bash
python -m venv .venv
# Activate .venv using your operating system's activation command.
pip install -r requirements.txt
python -m spacy download en_core_web_sm
```

Obtain the matching artifacts described in `models/README.md`, then set environment variables in your shell:

```bash
export GROQ_API_KEY='your_own_key'
export GROQ_MODEL='a_model_available_in_your_account'
python app.py
```

Open the local URL printed by Flask. On Windows, use the corresponding PowerShell environment-variable syntax. `.env.example` documents names only; the app does not automatically load `.env` files. Groq requests may incur charges under your own provider account.

## Routes

- `/`: landing page.
- `/chatbot_new`: technical Q&A interface.
- `/chatbot_groq`: alternate interface supplied with the original UI.
- `/en_answer`: direct Seq2Seq response endpoint.
- `/ar_answer`: translation, Seq2Seq response, translation back to Arabic.

## Limits and cleanup

The app is a local educational prototype. It rebuilds the tokenizer at startup and depends on fixed model layer indices. Conversation histories are process-global, not isolated per user, so do not expose this server to the internet or use it for private conversations without further work. The pretrained model architecture limits input lengths.

Portfolio cleanup removed a hardcoded Groq key, made the provider model selectable through `GROQ_MODEL`, made artifact paths relative to the app file, added the missing spaCy dependency, and disabled Flask debug mode. No claim of a retrained or improved model is made. Original slides/reports, notebook outputs, datasets and weights are not included.
