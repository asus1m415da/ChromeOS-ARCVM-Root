# Rooting ChromeOS ARCVM-based Android subsystem (Android 11+)

Scripts to enable **root access** in the ChromeOS Android subsystem (ARCVM only, not ARC++), using **KernelSU‑Next**.  
These scripts download and install a prebuilt ARCVM kernel from the official KernelSU‑Next GitHub Releases.

---

## ⚙️ Requirements
- ChromeOS **Developer Mode** must be enabled.  
  See [Chromebrew prerequisites](https://github.com/chromebrew/chromebrew?tab=readme-ov-file#prerequisites) for instructions.
- Only supported on **ARCVM** (Android 11+).  
- You need to install the **KernelSU‑Next Android app** manually after rooting (APK not included in this repo).

---

## 🚀 Usage

### Root
This will:
- Download the prebuilt ARCVM kernel with KernelSU‑Next.
- Verify its SHA256 checksum.
- Backup your original kernel (`vmlinux.orig`).
- Replace the running kernel with the patched one.
- Prompt you to reboot.

Run:

```shell
curl -Ls https://raw.githubusercontent.com/asus1m415da/ChromeOS-ARCVM-Root/main/root.sh | sudo bash -eu
```

After reboot, open the **KernelSU‑Next app** inside Android to validate root access.

---

### Unroot
This will:
- Restore the original kernel from backup.
- Remove the patched kernel and symlink.
- Prompt you to reboot.

Run:

```shell
curl -Ls https://raw.githubusercontent.com/asus1m415da/ChromeOS-ARCVM-Root/main/unroot.sh | sudo bash -eu
```

After reboot, ARCVM will run with the stock kernel (no root).

---

## 📌 Notes
- If some Android apps fail to detect root, try installing the KernelSU module under `root_fix_module/`.
- Backup is stored at `/mnt/stateful_partition/arcvm_root/vmlinux.orig`.  
  You can restore it manually if needed.
- Always reboot after running either script for changes to take effect.
- To update to a newer KernelSU‑Next release, edit `root.sh` with the correct version/tag and SHA256 hash.

---

## ⚠️ Disclaimer
Rooting may break system integrity or void warranties. Use at your own risk.  
This project is community‑maintained and not affiliated with Google or FydeOS.
```

