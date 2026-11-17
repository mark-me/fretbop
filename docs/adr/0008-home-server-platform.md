# Target platform is the home server

Fretbop runs as a single Docker image with SQLite and audio on a mounted volume, behind the user's own reverse proxy with HTTPS. HTTPS is a hard requirement: browsers only grant microphone access in a secure context.
