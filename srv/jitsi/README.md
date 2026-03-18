# Notes
Jitis will use STUN to discover its own address, then share that IP address with the clients. Setup Outbound NAT so that the outbound network connection from the Jitsi VM uses the same IP address as the one JVB is listening on, otherwise it will not work.
