# 3D Printer Configs

This repo keeps the configs for all my personal 3D printers.

## Repo Setup Instructions

When making this repo for the first time on a new device, there's a few setup steps you'll need to do:

```shell
# Set up python environment
python -m venv .venv
source .venv/bin/activate

# Install Ansible
pip install ansible
```

## New Device Setup Instructions

```shell
# Install general requirements
ansible-playbook -i ansible/hosts.yaml -l Spoiler ansible/install.yaml --tags "global" -K

# Install Klipper
ansible-playbook -i ansible/hosts.yaml -l Spoiler ansible/install.yaml --tags "klipper" -K

# Install Moonraker

# Install Fluidd

# Install Klipper-Screen

# Install Crowsnest


```


## Flashing Firmware

## Development Instructions

Docker can be used to validate configurations before they are pushed to the representative printer. To do so, follow the instructions below:

```bash
# Build docker image
docker compose build

# Run docker container for testing
docker compose up
```

Logs will live in `tmp/klippy.log`.

## References and Links
* https://www.klipper3d.org/Installation.html
* https://github.com/dw-0/kiauh