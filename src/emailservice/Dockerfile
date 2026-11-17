FROM python:3.12-slim

WORKDIR /app

# Инсталираме системни зависимости, ако са нужни за компилация на пакети
RUN apt-get update && apt-get install -y --no-install-recommends \
    libgomp1 \
    && rm -rf /var/lib/apt/lists/*

# Копираме и инсталираме Python зависимостите
COPY requirements.txt ./
RUn pip install --no-cache-dir -r requirements.txt

# Копираме целия код на услугата
COPY . .

EXPOSE 8080

ENTRYPOINT ["python", "email_server.py"]