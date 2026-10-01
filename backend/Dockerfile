FROM python:3.11-slim

# Evita que o Python grave arquivos .pyc no disco
ENV PYTHONDONTWRITEBYTECODE=1
# Evita buffering nas saídas stdout e stderr (logs em tempo real)
ENV PYTHONUNBUFFERED=1

WORKDIR /app

# Instalar dependências de compilação mínimas
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Copiar requirements.txt e instalar dependências do Python
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copiar todo o código-fonte do backend
COPY . .

# Expõe a porta padrão configurada no run.py
EXPOSE 8180

# Comando para inicializar a API FastAPI
CMD ["python", "run.py"]
