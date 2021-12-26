# Home Infra
Personal home server powered by Docker and fairly distro-agnostic as a result. Serving various self-hosted services 24/7/365 -- uptime is only guaranteed up to one 9 :-)

**OS: Arch Linux**

**Services:**
- Recursive DNS + Sinkhole 
- HTTP Server + Reverse DNS
- Dynamic DNS Client
- Personal "cloud"
- Media Server(s)
- Automated Media Downloading
- Minecraft Server

## Configuration

> NOTE: to be more thoroughly documented on the next installation with new hardware.

Install base OS (LTS kernel preferred), with a static IP. Additionally, install the following packages:

```
samba mergerfs smartmontools docker docker-compose rsync wireguard-tools sshguard
```
***mergerFS is only accessible in the AUR.***

Configure drives to mount as a mergerfs pool on `/mnt/pool`.

Set environment variables in `.env` file, as shown in `.env.example`.

If a conflict on port 53 occurs, disable the `systemd-resolved` service, so adguard can serve on the appropriate port.

Application data will be stored in the directory specified in `$APP`, and media/miscellaneous files stored in `$POOL` (i.e. the data pool).

Create a docker network named `bridge-net`

## Future Considerations
- Stable host OS (CentOS/OpenSUSE) or type-1 hypervisor
- Rootless containers via Podman
- Move from monolithic compose file to more isolated compose files
- MergerFS -> ZFS pool
