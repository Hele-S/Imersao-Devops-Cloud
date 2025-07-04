# 1. Usar uma imagem base oficial do Python.
# python:3.10-slim é uma boa escolha por ser leve.
FROM python:3.10-slim

# 2. Definir o diretório de trabalho no contêiner para /app.
WORKDIR /app

# 3. Copiar o arquivo de dependências para o diretório de trabalho.
# Isso é feito primeiro para aproveitar o cache de camadas do Docker.
COPY requirements.txt requirements.txt

# 4. Instalar as dependências do projeto.
# --no-cache-dir reduz o tamanho da imagem.
RUN pip install --no-cache-dir -r requirements.txt

# 5. Copiar o restante do código da aplicação para o diretório de trabalho.
COPY . .

# 6. Expor a porta 8000 para que a aplicação possa ser acessada de fora do contêiner.
EXPOSE 8000

# 7. Comando para executar a aplicação com Uvicorn.
# O host 0.0.0.0 é necessário para que o servidor seja acessível externamente.
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]