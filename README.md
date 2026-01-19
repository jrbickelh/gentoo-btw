# <img width="48" height="51" alt="image" src="https://github.com/user-attachments/assets/7c2c9d4e-216d-4894-9348-f1094e3e2938" /> Gentoo, BTW 


## 📖 The Journey

This repository documents my expedition into the **Gentoo Operating System**.

Often described as the "Mount Everest" of the Linux world, installing Gentoo is a journey that moves away from convenience and toward total control. While some view the compilation process as a waste of time, I found it to be a deeply rewarding experience that offers an unfiltered look at the traditional roots of Unix-like systems.

## ⚙️ The Rig

This build was compiled specifically for the following hardware, as captured in the "summit" screenshot:

* **OS:** Gentoo Linux (Kernel 5.10.27)
* **CPU:** Intel Core i7-7700 @ 4.2GHz
* **GPU:** NVIDIA GeForce GTX 1060 3GB
* **RAM:** ~16GB (15954MiB)
* **Desktop Environment:** KDE Plasma 5.21.5
* **Terminal:** Konsole / Bash 5.1.8

## 🛠️ Configuration Highlights

The core of this build lies in the `/etc/portage/make.conf`. Below are the key optimization strategies used to tailor the OS to the hardware.

### 1. Architecture Optimization
I used the `march=native` flag to ensure the compiler optimized code specifically for the Intel i7-7700 architecture, rather than a generic processor.

```bash
COMMON_FLAGS="-march=native -O2 -pipe"
CFLAGS="${COMMON_FLAGS}"
CXXFLAGS="${COMMON_FLAGS}"
```

### 2. Parallel Compilation

To maximize the 8 threads available on the CPU, the make options were tuned to allow 8 simultaneous jobs, ensuring the system remained responsive even during heavy compiles.
```bash
MAKEOPTS="-j8 -l8"
EMERGE_DEFAULT_OPTS="--jobs=8 --load-average=8"
```
### 3. Graphics & Driver Isolation

This system was built strictly for a proprietary NVIDIA experience. I explicitly enabled the nvidia flag while disabling conflicting or unnecessary drivers like Intel, Radeon, and VESA to keep the build clean.

```bash

VIDEO_CARDS="nvidia"
USE="nvidia X -intel -radeon -vesa"
```
### 📸 Proof of Life

The header image confirms the successful build:

<img width="549" height="376" alt="image" src="https://github.com/user-attachments/assets/6c3ff632-d815-4614-aa1d-6db8e8169f52" />

### 💭 Reflection

Successfully configuring the kernel and managing dependencies manually provided a level of insight into the Linux ecosystem that standard installers obscure. The complexity was not a barrier, but the path to a deeper understanding of the machine. It is a reminder that the climb is just as important as the view from the top.
