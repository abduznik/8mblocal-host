# 8mblocal-host

A local-first, browser-based video compressor designed for speed and privacy. This project hosts a static interface that utilizes FFmpeg.wasm to perform video compression entirely within the user's browser memory.

## Features

- Local Execution: Compression runs on your device's CPU/GPU via WebAssembly.
- Privacy: No video data ever leaves your network.
- Target Size Presets: Optimized for 8MB (Discord), 25MB, and 50MB targets.
- Lazy Optimization: Prioritizes speed with 'ultrafast' presets.
- Live Preview: Watch your compressed video before downloading.

## Quick Start

### Docker Compose

Create a `compose.yaml` file:

```yaml
services:
  8mblocal:
    image: ghcr.io/abduznik/8mblocal-host:master
    container_name: 8mblocal
    ports:
      - "8080:80"
    restart: unless-stopped
```

Run the container:

```bash
docker compose up -d
```

### Manual Run

```bash
docker run -d \
  --name 8mblocal \
  -p 8080:80 \
  ghcr.io/abduznik/8mblocal-host:master
```

## Configuration

The application is served by Nginx and requires specific MIME types for WebAssembly. Ensure `nginx.conf` is correctly mapped to handle `.wasm` files.

## License

MIT License - Copyright (c) 2026 Abduznik
