FROM python:3.10-slim

WORKDIR /python-docker

COPY requirements.txt requirements.txt
RUN apt-get update && apt-get install git -y
RUN pip3 install -r requirements.txt
RUN pip3 install "git+https://github.com/openai/whisper.git" 
RUN apt-get update && apt-get install -y ffmpeg
RUN apt-get install -y nvidia-container-toolkit


# Add a volume for the Whisper models
VOLUME ["/root/.cache/whisper"]


# Set environment variable
ENV PATH="/app:${PATH}"

COPY . .

EXPOSE 8000

CMD ["uvicorn", "fastapi_app:app", "--host", "0.0.0.0", "--port", "8000"]
