# Docker help:
- No matching manifest for windows/amd64 in the manifest list entries:
> 1. Right click Docker icon in the Windows System Tray
> 2. Go to Settings
> 3. Daemon
> 4. Advanced
> 5. Set the "experimental": true
> 6. Restart Docker

- Create docker network:
> Error response from daemon: could not find plugin bridge in v1 plugin registry: plugin not found

docker network create --driver nat network-name
