# Jitsi Setup

To set this up, you need to:
- Comment out container hardening for the `web` and `prosody` containers in `compose.yml`
- Run `docker compose up -d` to generate configuration files
- Run `chown -R 300005:300005 ./web ./certs ./transcripts` and `chown -R 300006:300006 ./prosody` to adjust permissions
- Uncomment the container hardening in `compose.yml`
- Run `docker compose up -d` to recreate the `web` and `prosody` containers

## Outbound NAT
Jitis will use STUN to discover its own address, then share that IP address with the clients. Setup Outbound NAT so that the outbound network connection from the Jitsi VM uses the same IP address as the one JVB is listening on, otherwise it will not work.
