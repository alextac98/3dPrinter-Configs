# 3D Printer Configs

This repo keeps the configs for all my personal 3D printers. The intent is to have the repo stored on each of the devices in a public place (`~/printer-configs`) and then point Klipper to the new location.

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

1. Start with the initial script:

```bash
ansible-playbook -i ansible/hosts.yaml -l Spoiler ansible/install.yaml --tags "global" -K
```

2. Install all required projects. The easiest way to install all the tools is [Kiauh](https://github.com/dw-0/kiauh), which has scripts to install all commonly used systems. For each of the devices, here are the things I installed (in order):

* Spoiler
  * Klipper
  * Moonraker
  * Fluidd
  * Klipper-Screen
  * Crowsnest
* Hazard
  * Klipper
  * Moonraker
  * Fluidd
  * Crowsnest
* Bullet
  * Klipper
  * Moonraker
  * Fluidd

3. Install firmware (jump to Flashing Firmware section)

4. Set up configs by running the klipper-config ansible script:

```bash
ansible-playbook -i ansible/hosts.yaml -l Spoiler ansible/install.yaml --tags "klipper"
ansible-playbook -i ansible/hosts.yaml -l Spoiler ansible/install.yaml --tags "klipper-config" -K
```

> **_NOTE:_** 
>
> It is possible to do all of this with Ansible. However it was getting very complicated to do so since a lot of the startup scripts require interaction. Therefore, I decided to make it easy on me and do the install step manually.

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