ARG BASE_IMAGE=python:3.8-slim-buster
FROM $BASE_IMAGE

# system update & package install
RUN apt-get -y update && \
    apt-get install -y --no-install-recommends \
    build-essential \
    openssl libssl-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Add Tini
ENV TINI_VERSION v0.19.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini
RUN chmod +x /tini
ENTRYPOINT ["/tini", "--"]

WORKDIR /app
COPY app/pyproject.toml ./pyproject.toml
RUN python3 -m pip install --upgrade pip && \
    python3 -m pip install poetry && \
    poetry config virtualenvs.create false && \
    poetry install && \
    rm -rf ~/.cache/pip/* && \
    rm -rf ~/.cache/pypoetry/*
EXPOSE 3001

# Execute
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "3001", "--reload"]