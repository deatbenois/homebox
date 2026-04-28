# Homebox

> A fork of [sysadminsmedia/homebox](https://github.com/sysadminsmedia/homebox) — a home inventory and organization system.

[![Go Version](https://img.shields.io/badge/go-1.21+-blue.svg)](https://golang.org)
[![License](https://img.shields.io/badge/license-AGPL--3.0-green.svg)](LICENSE)

## Overview

Homebox is a self-hosted home inventory and organization system built for the home user. It allows you to track your belongings, manage warranties, and organize your household items with ease.

## Features

- 📦 Track and organize household items
- 🏷️ Label and categorize with custom fields
- 📸 Attach photos and documents to items
- 🔧 Warranty and maintenance tracking
- 🔍 Full-text search across all items
- 👥 Multi-user support with shared households
- 📊 Reports and statistics
- 🌐 REST API with OpenAPI documentation

## Quick Start

### Docker

```bash
docker run -d \
  --name homebox \
  -p 7745:7745 \
  -v homebox-data:/data \
  ghcr.io/your-org/homebox:latest
```

### Docker Compose

```yaml
services:
  homebox:
    image: ghcr.io/your-org/homebox:latest
    container_name: homebox
    restart: unless-stopped
    ports:
      - "7745:7745"
    volumes:
      - homebox-data:/data
    environment:
      - HBOX_LOG_LEVEL=info
      - HBOX_LOG_FORMAT=text

volumes:
  homebox-data:
```

## Development

### Prerequisites

- [Go 1.21+](https://golang.org/dl/)
- [Node.js 18+](https://nodejs.org/)
- [Task](https://taskfile.dev/) (optional, for task runner)

### Getting Started

```bash
# Clone the repository
git clone https://github.com/your-org/homebox.git
cd homebox

# Install backend dependencies
go mod download

# Install frontend dependencies
cd frontend && npm install && cd ..

# Start development server
go run ./backend/app/api/main.go
```

### Dev Container

This project includes a [Dev Container](.devcontainer/) configuration for VS Code and GitHub Codespaces. Open the project in VS Code and select **Reopen in Container** to get a fully configured development environment.

## Configuration

Homebox is configured via environment variables:

| Variable | Default | Description |
|---|---|---|
| `HBOX_LOG_LEVEL` | `info` | Log level (`debug`, `info`, `warn`, `error`) |
| `HBOX_LOG_FORMAT` | `text` | Log format (`text`, `json`) |
| `HBOX_WEB_PORT` | `7745` | HTTP port to listen on |
| `HBOX_WEB_HOST` | `` | Host address to bind to |
| `HBOX_STORAGE_DATA` | `./data` | Path to data directory |
| `HBOX_MAILER_HOST` | `` | SMTP host for email notifications |

## Contributing

Contributions are welcome! Please read the [contributing guidelines](.github/AGENTS.md) before submitting a pull request.

1. Fork the repository
2. Create a feature branch (`git checkout -b feat/my-feature`)
3. Commit your changes (`git commit -m 'feat: add my feature'`)
4. Push to the branch (`git push origin feat/my-feature`)
5. Open a Pull Request

## License

This project is licensed under the AGPL-3.0 License — see the [LICENSE](LICENSE) file for details.
