FROM python:3.11-slim

RUN apt-get update && \
    apt-get install -y git make gcc libffi-dev libusb-1.0-0-dev libjpeg-dev build-essential && \
    rm -rf /var/lib/apt/lists/*

# Clone Klipper
RUN git clone https://github.com/Klipper3d/klipper.git /klipper

WORKDIR /klipper

# Install python dependencies
RUN pip install -r scripts/klippy-requirements.txt

# Expose klippy socket
VOLUME ["/tmp/klippy_uds"]

# Entrypoint for simulation
CMD ["python3", "klippy/klippy.py", "out/klipper.elf", "-i", "/configs/printer.cfg", "-l", "/tmp/klippy.log", "-a", "/tmp/klippy_uds/klippy.sock"]