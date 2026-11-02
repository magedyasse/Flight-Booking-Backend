# --- Stage 1: Build -----
FROM python:3.12-slim

# Install uv from PyPI so the build does not depend on GHCR authentication.
# RUN pip install --no-cache-dir uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

COPY . /app

WORKDIR /app

RUN uv sync --frozen --no-cache --no-dev

EXPOSE 80

CMD ["/app/.venv/bin/fastapi", "run", "main.py", "--port", "80", "--host", "0.0.0.0"]
    