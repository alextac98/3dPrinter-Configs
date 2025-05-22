# 3D Printer Configs

This repo keeps the configs for all my personal 3D printers.

## Initial Installations


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