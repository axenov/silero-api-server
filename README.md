# A simple FastAPI Server to run Silero TTS
Credit goes to the developers of Silero TTS  
[Silero PyTorch Page](https://pytorch.org/hub/snakers4_silero-models_tts/)  
[Silero GitHub Page](https://github.com/snakers4/silero-models)

This is primarily to serve the TTS extension in [SillyTavern](https://github.com/Cohee1207/SillyTavern). The TTS module or server can be used any way you wish.

## Installation
`pip install silero-api-server`

## Starting Server
`python -m silero_api_server` will run on default ip and port (0.0.0.0:8001)

```
usage: silero_api_server [-h] [-o HOST] [-p PORT]

Run Silero within a FastAPI application

options:
  -h, --help            show this help message and exit
  -o HOST, --host HOST
  -p PORT, --port PORT
  -l LANG, --language LANG
  --show-languages
```

On first run of server, two operations occur automatically. These may take a minute or two.
1. The model will be downloaded 
2. Voice samples will be generated. 

## Using v4 Models

This server supports both v3 and v4 Silero TTS models. To use v4 models, specify the model name in the language parameter:

```bash
# Russian v4 model
python -m silero_api_server --language "v4_ru.pt"

# Ukrainian v4 model  
python -m silero_api_server --language "v4_ua.pt"

# Uzbek v4 model
python -m silero_api_server --language "v4_uz.pt"

# Indic v4 model
python -m silero_api_server --language "v4_indic.pt"

# Cyrillic v4 model
python -m silero_api_server --language "v4_cyrillic.pt"
```

# API Docs
API Docs can be accessed from [http://localhost:8001/docs](http://localhost:8001/docs)

# Voice Samples
Samples are served statically by the web server at `/samples/{speaker}.wav` or callable from the API from `/tts/sample?speaker={speaker}` endpoint.

# Selecting Language
Use command-line options or download and set the desired language using `POST /tts/language` with payload `{"id":"languageId"}`  
List of language ids are available via `GET /tts/language`
