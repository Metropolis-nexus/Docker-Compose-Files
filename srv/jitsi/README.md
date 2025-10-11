## Jitsi Setup

- During the initial setup, comment out `-/srv/jitsi/prosody-config-override:/etc/cont-init.d/10-config:Z` in `compose.yml`
- Once the services have been brought up and configuration files files have been generated, uncomment it.
- Add turn server into `prosody/config/conf.d/jitsi-meet.cfg.lua` with [mod_external_services](https://prosody.im/doc/modules/mod_external_services). There is an example in this repo. Do NOT use mod_turn_external - it does not work.
- Run `docker compose down` and then `docker compose up -d`.
