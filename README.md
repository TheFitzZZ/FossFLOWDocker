# FossFLOW Docker Images

This repository automatically builds Docker images from the [stan-smith/FossFLOW](https://github.com/stan-smith/FossFLOW) repository and publishes them to Docker Hub.

## Setup Instructions

To get this working, you'll need to:

### 1. Create a Docker Hub Access Token

1. Go to [Docker Hub](https://hub.docker.com/) and log in
2. Go to Account Settings → Security → Access Tokens
3. Create a new access token with "Read, Write, Delete" permissions
4. Copy the token (you won't see it again)

### 2. Add GitHub Secrets

1. Go to your GitHub repository settings
2. Navigate to "Secrets and variables" → "Actions"
3. Add a new repository secret:
   - Name: `DOCKER_HUB_TOKEN`
   - Value: [paste the Docker Hub access token you created]

### 3. Trigger the Workflow

The workflow will automatically run when:
- You push to the main branch
- Daily at 2 AM UTC
- You manually trigger it from the Actions tab

## Available Tags

- `latest` - Latest build from main branch
- `YYYY-MM-DD` - Daily builds
- `upstream-{short-sha}` - Builds tagged with upstream commit
- `main-{sha}` - Builds from main branch with full commit SHA

## Usage

### Quick Start

```bash
# Run the latest version
docker run -d -p 3000:3000 fitzzz/fossflow:latest
```

Open your browser to [http://localhost:3000](http://localhost:3000)

### Docker Compose

```yaml
version: '3.8'
services:
  fossflow:
    image: fitzzz/fossflow:latest
    ports:
      - "3000:3000"
    restart: unless-stopped
```

### Advanced Usage

```bash
# Run with custom port
docker run -d -p 8080:3000 fitzzz/fossflow:latest

# Run specific version
docker run -d -p 3000:3000 fitzzz/fossflow:upstream-abc1234
```

## About FossFLOW

FossFLOW is a powerful, open-source Progressive Web App (PWA) for creating beautiful isometric diagrams. Built with React and the Isoflow library, it runs entirely in your browser with offline support.

### Features

- 🎨 **Isometric Diagramming** - Create stunning 3D-style technical diagrams
- 💾 **Auto-Save** - Your work is automatically saved every 5 seconds
- 📱 **PWA Support** - Install as a native app on Mac and Linux
- 🔒 **Privacy-First** - All data stored locally in your browser
- 📤 **Import/Export** - Share diagrams as JSON files
- 🎯 **Session Storage** - Quick save without dialogs
- 🌐 **Offline Support** - Work without internet connection

## Automated Builds

This repository:

- ✅ Automatically builds when upstream changes are detected
- ✅ Builds daily to ensure latest dependencies
- ✅ Supports both AMD64 and ARM64 architectures
- ✅ Uses GitHub Actions for CI/CD
- ✅ Provides multiple tagging strategies

## Development & Contributing

This is purely a Docker packaging repository. For development and contributions to FossFLOW itself, please visit the [upstream repository](https://github.com/stan-smith/FossFLOW).

## License

FossFLOW is released under the Unlicense license. See the [upstream repository](https://github.com/stan-smith/FossFLOW) for license details.

## Support

For issues related to FossFLOW functionality, please open issues in the [upstream repository](https://github.com/stan-smith/FossFLOW/issues).

For Docker-specific issues with these images, please open issues in this repository.