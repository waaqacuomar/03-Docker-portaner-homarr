# Docker Hosts Managed with Portainer + Homarr Dashboard

Two Ubuntu VMs running Docker, managed through Portainer, with Homarr as the front page for the whole lab.

## Hosts
- Main Docker VM: 8 containers (Portainer, Homarr, AdGuard Home, Prometheus, Grafana, node-exporter, cAdvisor, pve-exporter), most as Compose stacks
- Second Docker VM: Portainer with a single app container

## Homarr dashboard
- Live Proxmox widget: nodes, VMs, LXCs and storage
- Pi-hole stats and blocking controls, OPNsense CPU and interface traffic
- Docker container list with CPU and memory per container
- Links to every service in the lab

## What I can do
- Install Docker and Portainer on a fresh Ubuntu VM
- Pull, run, stop and delete containers and images
- Write compose files and manage stacks (up, ps, logs, down)
- Fix a broken Docker apt repository and Docker contexts

## Homarr + OPNsense fix
- Homarr couldn't connect to OPNsense: TLS hostname mismatch, because the certificate didn't include the IP
- Added an `extra_hosts` entry in Homarr's compose file so the container reaches OPNsense by the name on its certificate
- Recreated the container without losing data, since settings live in a mounted volume

## Screenshots
![Portainer on both hosts](images/portainer.png)
![Homarr](images/homarr.png)
