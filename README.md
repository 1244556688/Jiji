# Justin OS - Debian 12 Live ISO Build System

This repository provides the configuration and automation files required to build a customized Debian 12 (bookworm) live ISO bootable image called **Justin OS**.

It includes a customized premium Windows 11 and modern Linux inspired Plymouth boot animation sequence (**"justinos" theme**).

---

## 🚀 How to Build

The easiest way to build the ISO is using the integrated **GitHub Actions** CI/CD runner.

1. Create a new repository on GitHub (e.g., `justin-os`).
2. Push the files in this project directory directly to your repository:
   ```bash
   git init
   git add .
   git commit -m "feat: initial Justin OS build system"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/justin-os.git
   git push -u origin main
   ```
3. Go to the **Actions** tab of your GitHub repository.
4. Select the **"Build Justin OS Live ISO"** workflow and click **"Run workflow"** (or let it run automatically on push).
5. Once completed, download the bootable `justin-os-live-amd64.iso` artifact from the build logs.

---

## 🛠️ Testing Locally

You can test the resulting ISO image in a virtual machine using **QEMU**:

```bash
# Run ISO inside QEMU with Plymouth boot splash visible
qemu-system-x86_64 -m 2G -enable-kvm -cdrom justin-os-live-amd64.iso -vga virtio
```

To test it on a physical USB drive, write it using `dd`:
```bash
# WARNING: Ensure /dev/sdX is the correct USB drive!
sudo dd if=justin-os-live-amd64.iso of=/dev/sdX bs=4M status=progress oflag=sync
```

---

## 🎨 Theme Details
The custom Plymouth theme features:
- A pure black ambient background.
- A glowing white monochrome logo centered in the screen.
- A 5-dot circular loading animation that matches modern workstation operating system boots.
- Location: `/usr/share/plymouth/themes/justinos/`
