> [!NOTE]
> This guide is under construction. Please contribute with fork this repo and pull request if you can.

> [!CAUTION]
> If **you** build **KernelSU Next version >3**:
> 1. **You must use syscall hooks v1.7** **or use kprobes hook** (check a32_k+e_defconfig).
> 2. ****You** must use ReZygisk CI builds** and **use Metamoudule** (list metamodule below)

> [!TIP]
> **Metamodule list**:
> 1. [**OverlayFS**](https://github.com/KernelSU-Modules-Repo/meta-overlayfs)
> 2. [**Mountify**](https://github.com/backslashxx/mountify)
> 3. [**Magic Mount**](https://github.com/KernelSU-Modules-Repo/meta-mm)
> 4. [**Magic Mount RS**](https://github.com/Tools-cx-app/meta-magic_mount/)
> 5. [**Hybird Mound**](https://github.com/YuzakiKokuban/meta-hybrid_mount)
> 
> **ReZygisk CI builds you can get on [Actions tab](https://github.com/PerformanC/ReZygisk/actions) in the [repository](https://github.com/PerformanC/ReZygisk/)**

### How to build Moonlight kernel

- **Step 1: Clone this repository.**
```
git clone --depth=1 https://github.com/Moonlight-kernel
```

+ **Step 1.1: (Optional) Configure extra version name of kernel.**
> [!TIP]
> **Explain kernel version.**
> 
> 1. **4 = VERSION:** The version of the kernel.
> 
> 2. **14 = PATCHLEVEL:** The major revision of the kernel.
> 
> 3. **356 = SUBLEVEL:** The minor revision of the kernel.
> 
> 4. **-moonlight@nongki = EXTRAVERSION:** Custom extra version (like 4.14.356-**moonlight@nongki**)

> [!CAUTION]
> **Do not edit VERSION, PATCHLEVEL or SUBLEVEL because it will cause error or compatibility.**

1. Open MAKEFILE on root folder in text editor.
2. Edit line **EXTRAVERION** = -moonlight@nongki to anything you want for it.
3. Save file

- **Step 2: Clone clang (example: zyc clang 14)**
```
git clone https://github.com/EmanuelCN/zyc_clang-14
```

> [!TIP]
> If you clone another clang, please go change directory in build script.

- **Optional: Add KernelSU variant.**
> [!TIP]
> All of KernelSU variant setup script please go to [```guide/KernelSUSetup.md```](https://github.com/m0onl1ghtt/Moonlight-kernel/blob/main/guide/KernelSUSetup.md)

1. Run script (If you want to be sure, please run the script twice.)

- **Step 3: Customize the build script.**
1. Open build_kernel.sh in root folder
```
# KernelSU
- If you use Kprobes hook for your kernel, please edit defconfig to a32_k+e_defconfig.
- If you use manual hook for your kernel. please edit defconfig to a32_manual_ksu_defconfig.
# Non-KernelSU
- Please edit defconfig to a32_noksu_defconfig.
```

- **Step 4: Build.**
```
bash build_kernel.sh
```
