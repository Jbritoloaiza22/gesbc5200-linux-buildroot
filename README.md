# GESBC-5200 Linux Buildroot Docker Environment

Repository:
https://github.com/Jbritoloaiza22/gesbc5200-linux-buildroot.git

This project provides a Docker-based Buildroot environment to build an embedded Linux system for the SAMA5D2 platform.

---

## 1. Clone repository with submodules

git clone --recurse-submodules https://github.com/Jbritoloaiza22/gesbc5200-linux-buildroot.git
cd gesbc5200-linux-buildroot

If already cloned:

git submodule update --init --recursive

---

## 2. Build Docker image

sudo docker build -t buildroot-arm-env -f docker/Dockerfile .

---

## 3. Run Docker container

sudo docker run -it --rm \
  -v ~/Documents/gesbc5200-linux-buildroot:/workspace/project \
  buildroot-arm-env

---

## 4. Enter Buildroot directory (inside container)

cd /workspace/project/buildroot/buildroot-mchp

---

## 5. Load default configuration

BR2_EXTERNAL=../buildroot-external-microchip make atmel_sama5d2_xplained_mmc_defconfig

---

## 6. Build full system

BR2_EXTERNAL=../buildroot-external-microchip make

---

## 7. Output images

output/images/