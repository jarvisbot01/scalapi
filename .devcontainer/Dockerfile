ARG VARIANT=3-slim-bookworm
FROM python:${VARIANT}

ARG DEBIAN_FRONTEND=noninteractive
ARG TZ=America/Bogota

ENV TZ ${TZ}
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

RUN apt-get update -qq && apt-get upgrade -qq --no-install-recommends --no-install-suggests -yy && \
    apt-get install -qq --no-install-recommends --no-install-suggests -yy curl \
    ca-certificates \
    gnupg \
    build-essential \
    libssl-dev \
    libffi-dev \
    libpq-dev \
    python3-dev \
    gcc && \
    mkdir -p /etc/apt/keyrings && \
    curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg && \
    echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_22.x nodistro main" > /etc/apt/sources.list.d/nodesource.list && \
    apt-get update && \
    apt-get install nodejs -qq --no-install-recommends --no-install-suggests -yy && \
    npm i npm@latest -g && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install --upgrade pip --no-cache-dir && \
    python3 -m pip install --no-cache-dir setuptools wheel
