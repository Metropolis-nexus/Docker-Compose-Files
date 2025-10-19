## Jitsi Setup

- After the initial setup, uncomment all commented options for prosody.
- Set the correct ownership.
- Add turn server into `prosody/config/conf.d/jitsi-meet.cfg.lua` with [mod_external_services](https://prosody.im/doc/modules/mod_external_services). There is an example in this repo. Do NOT use mod_turn_external - it does not work.
- Run `docker compose down` and then `docker compose up -d`.
