FROM python:3.12-slim

ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

RUN apt-get update && apt-get install -y \
    git \
    curl \
    ca-certificates \
    nodejs \
    npm \
    && rm -rf /var/lib/apt/lists/*

RUN npm install -g pnpm

RUN pip install --no-cache-dir uv

# Preinstall Playwright system deps and Chromium
RUN uv pip install --system playwright && \
    playwright install-deps chromium && \
    playwright install chromium && \
    uv pip uninstall --system playwright
