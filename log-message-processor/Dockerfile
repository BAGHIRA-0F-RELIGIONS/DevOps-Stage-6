FROM python:3.11-slim
ENV DEBIAN_FRONTEND=noninteractive
WORKDIR /app
# Copy requirements first for better layer caching
COPY requirements.txt /app/requirements.txt
# Install OS-level build dependencies needed to compile wheels
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      build-essential \
      gcc \
      libssl-dev \
      libffi-dev \
      libpq-dev \
      python3-dev \
      curl \
      git \
      ca-certificates \
 && rm -rf /var/lib/apt/lists/*
# Upgrade pip and install requirements
RUN python -m pip install --upgrade pip setuptools wheel \
 && pip install --no-cache-dir -r /app/requirements.txt
# Copy the rest of the app
COPY . /app
CMD ["python","main.py"]





