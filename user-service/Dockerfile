FROM python:3.10-slim

WORKDIR /app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    PYTHONPATH=/app

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    libpq-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*



COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt



# Copy .env file
COPY .env .

# Copy application code
COPY app/ app/


# Run the applicaiton
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8003"]