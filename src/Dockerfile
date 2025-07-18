FROM python:3.11-slim

# Set working directory
WORKDIR /app

# Copy source code into the container
COPY . /app

# Install dependencies
RUN pip install --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt

# Expose app port
EXPOSE 8000

# Launch FastAPI + custom streamlit/app logic in parallel
CMD ["bash", "-c", "uvicorn --app-dir web fast_api_runner:api_app --port 8000 --workers 2 & python3 web/main.py agents/data_agent local & wait"]
