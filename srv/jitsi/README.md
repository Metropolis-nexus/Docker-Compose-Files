## Jitsi Setup

- Generate configs using upstream's `docker-compose.yml` with the environment files in this repository.
- Run `docker compose down`.
- Add turn server into `prosody/config/conf.d/jitsi-meet.cfg.lua` with [mod_external_services](https://prosody.im/doc/modules/mod_external_services). There is an example in this repo. Do NOT use mod_turn_external - it does not work.
- Switch to the `compose.yml` in this repository.
- Set permissions for directories according to the content of `compose.yml`.
- Run `docker compose up -d`.