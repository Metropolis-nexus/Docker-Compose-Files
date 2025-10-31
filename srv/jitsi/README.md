## Jitsi Setup

To set this up, you need to:
- Comment out container hardening for the `web` and `prosody` containers in `compose.yml`
- Run `docker compose up -d` to generate configuration files
- Run `chown -R 300005:300005 ./web ./certs ./transcripts` and `chown -R 300006:300006 ./prosody` to adjust permissions
- Uncomment the container hardening in `compose.yml`
- Run `docker compose up -d` to recreate the `web` and `prosody` containers 