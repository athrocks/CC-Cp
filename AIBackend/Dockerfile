# AIBackend/Dockerfile

FROM python:3.9-slim

# Set working directory
WORKDIR /app

# Install system dependencies (OpenCV, Torch, etc.)
RUN apt-get update && apt-get install -y \
    build-essential \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender-dev \
    libgl1-mesa-glx \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements and install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Avoid downloading YOLOv5 from scratch every time
RUN pip install --no-cache-dir torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu

# Copy the rest of the code
COPY . .

# Expose Flask port
EXPOSE 8000

# Run the app using gunicorn (production-ready)
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "Detection:app"]
