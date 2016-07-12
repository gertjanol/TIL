# SSH

## Forwarding

How to forward a port on local host, to a machine inside a network using a jumphost?
 * in `/etc/hosts`: `127.0.0.1 myhost.com`
 * in `/etc/sudoers` (or file in `sudoers.d/`): `Defaults env_keep="SSH_AUTH_SOCK"`
   * this makes sure your ssh-agent connection is usable when forwarding privileged ports using sudo, later on.
 * `sudo ssh -L 443:localhost:443 -o ProxyCommand="ssh <user>@<jumphost> nc %h %p 2> /dev/null" <user>@<targethost>`
