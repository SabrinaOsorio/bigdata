# Usamos la base de Python 3.12 oficial compatible con codespaces
FROM mcr.microsoft.com/devcontainers/python:3.12

# Evitar prompts de usuario durante la instalación
ENV DEBIAN_FRONTEND=noninteractive

# Instalar Java 17 (Recomendado para Spark 3.5+) y utilidades
RUN apt-get update && apt-get install -y \
    default-jre \
    wget \
    curl \
    git-lfs \
    && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# Instalar uv para gestión ultra-rápida
RUN pip install uv

# Configurar el espacio de trabajo
WORKDIR /workspaces/${localWorkspaceFolderBasename}

# Instalaremos las dependencias desde el pyproject.toml
# Esto hace que el contenedor se sincronice con tu archivo de configuración
COPY pyproject.toml uv.lock* ./
RUN uv pip install --system -r pyproject.toml