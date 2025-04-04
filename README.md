# llm

Docker compose 

```
services:
  ollama:
    volumes:
      - /home/nicolas/docker/llm/ollama:/root/.ollama
    container_name: ollama
    pull_policy: always
    tty: true
    restart: unless-stopped
    image: ollama/ollama:${OLLAMA_DOCKER_TAG-latest}
    ports:
      - 11434:11434

  wyoming-whisper:
    container_name: wyoming-whisper
    image: rhasspy/wyoming-whisper
    ports:
      - "10300:10300"
    volumes:
      - /home/nicolas/docker/llm/whisperdata:/data 
    command: >
      --model base-int8 --language fr
    tty: true 

  wyoming-piper:
    container_name: wyoming-piper
    image: rhasspy/wyoming-piper
    ports:
      - "10200:10200"
    volumes:
      - ~/piperdata:/data
    command: >
      --voice fr_FR-tom-medium
    tty: true 

```
