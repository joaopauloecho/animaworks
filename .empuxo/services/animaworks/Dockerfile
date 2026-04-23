FROM python:3.12-slim@sha256:2b0079146a74e23bf70489ec1ad4f9d2fcb8d4e8d2a36b5c2f5e8d9c4b5a6e7f

WORKDIR /app

RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    curl \
    && rm -rf /var/lib/apt/lists/*

COPY pyproject.toml .
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir .

COPY core/ core/
COPY server/ server/
COPY templates/ templates/
COPY main.py .

EXPOSE 18500

CMD ["python", "main.py", "start", "--host", "0.0.0.0", "--port", "18500"]
