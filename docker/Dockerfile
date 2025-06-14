FROM python:3.13-slim

ARG POETRY_VERSION=2.1

RUN pip install "poetry==${POETRY_VERSION}"

# gcc can be required to install some dependencies
RUN apt-get update && \
    apt-get install -y gcc && \
    rm -rf /var/lib/apt/lists/*

ENV POETRY_NO_INTERACTION=1 \
    POETRY_VIRTUALENVS_IN_PROJECT=0 \
    POETRY_VIRTUALENVS_CREATE=1 \
    POETRY_CACHE_DIR=/tmp/poetry_cache

WORKDIR /app
EXPOSE 8501

ENTRYPOINT bash -c "poetry install --only main && poetry run streamlit run src/run.py"
