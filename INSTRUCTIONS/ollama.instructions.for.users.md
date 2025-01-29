# Ollama using Docker.Compose

/binsh

```bash
version: '3.8'
services:
  ollama:
    image: ollama/ollama:latest
    container_name: ollama
    ports:
      - "11434:11434"
    volumes:
      - ./ollama:/root/.ollama
    restart: unless-stopped
    command: serve
```
Create a docker-compose.yml file with above content

```bash
docker-compose up -d
```
Access olama on the exposed port.

## To load Model using olama docker 

- get inside Ollama docker 

```bash
docker exec -it ollama /bin/bash 
```
- pull and load a model 

```bash
ollama pull mistral:instruct 
ollama pull llama3.2:1b

ollama pull deepseek-r1:1.5b

```

- lists all available model

```bash
ollama list
```
- remove a model

```bash
ollama rm deepseek-r1:7b
```
You can use any other method to load load a model.

Clean up your HDD To free up system HDD space, please use the following command. It will delete unnecessary Docker images, volumes, networks, and cached Docker objects:

`docker system prune -a --volumes`