<img width="2560" height="1396" alt="Onizuka_logo" src="https://github.com/user-attachments/assets/13b90daf-eff0-4ce6-b7e4-1b15c2334a7e" />

<div align="center">

# 👹 ONIZUKA KERNEL V1.1
### The Ultimate Cloud Gaming Kernel for Xiaomi Pad 5 (Nabu)
### *Optimized for Stock HyperOS (Android 13)*

[![Version](https://img.shields.io/badge/Version-V1.1-red?style=for-the-badge)](https://github.com/tonystyle13)
[![Device](https://img.shields.io/badge/Device-Xiaomi_Pad_5-orange?style=for-the-badge)](https://github.com/tonystyle13)
[![License](https://img.shields.io/badge/License-GPLv2-blue?style=for-the-badge)](LICENSE)

> **"A controller without vibration is heresy."**
</div>

---

## ⚠️ COMPATIBILITY & REQUIREMENTS
**READ THIS BEFORE FLASHING:**

1.  **ROM Compatibility:**
    * **✅ Verified Target:** This kernel was built and tested specifically on **Stock Xiaomi HyperOS OS1.0.6.0.TKXEUXM (EEA/EU)**.
    * **❓ Other HyperOS Versions:** It **should** work on other HyperOS builds (Global, CN, or Custom HyperOS Ports).
    * **❌ AOSP / LineageOS / DerpFest:** Not supported. Flashing this on AOSP ROMs will likely cause a **Bootloop**.

2.  **ROOT REQUIRED:** You **MUST** have **Magisk** installed.
    * *Why?* The core optimization scripts (Memory Guard, CPU Tuning, Joyose Killer) are injected into `/data/adb/service.d/`. **Without Magisk, these scripts will NOT run.**

---

## 📖 The Story Behind
As a dad, the living room TV is often hijacked by the kids. Gaming on the couch became my escape.
I own a **Lenovo Legion Go**, which is an absolute beast. However, I often prefer the **bigger 11-inch WQHD+ screen** of the Xiaomi Pad 5 for better immersion and visual comfort. Why Onizuka? I just like the character, nothing more.

**The Quest for Zero Latency:**
After testing dozens of AOSP ROMs, I found that decoding latency for high-bitrate cloud gaming was always higher than on Stock ROMs. I returned to the official **OS1.0.6.0.TKXEUXM** and the difference was night and day:
* **BetterXCloud:** Latency dropped to **4-5ms**.
* **Artemis (Moonlight Fork):** Latency dropped to **5-7ms** even at **Native 2560x1600 @ 120 FPS**.

**The Problem:**
While fast, the Stock ROM had a critical flaw: the **Bluetooth Controller vs. Touchscreen conflict**. Streaming at high resolution while using a controller with rumble would overload the system memory allocation, causing the touchscreen to freeze or the tablet to violently reboot (Kernel Panic) during heavy action scenes like shooting in Call of Duty.

After testing numerous kernels and going through several build iterations, I finally achieved the perfect stability build 
ready to be shared with people who have the same problem as me, **Onizuka Kernel V1 is the survivor.** It keeps the incredible low latency of the Stock ROM while implementing "Ironclad" stability fixes to prevent crashes under heavy load.

---

## 🎮 Universal Controller & Rumble Support
My philosophy is simple: **No Rumble = No Play.**
This kernel **adds missing drivers** and **activates specific kernel flags** (Force Feedback, Memless, UHID) to ensure native rumble support for:

* **Xbox** (One, Series X/S)
* **PlayStation** (DualShock 4, DualSense)
* **Nintendo** (Switch Pro Controller)
* **3rd Party:** GameSir G8+, BSP D9, BSP D10

---

## ⚡ Key Features & Optimizations

### 1. 🛡️ Anti-Crash Memory Guard (V1.1 Update)
Fixed reboots during heavy gameplay (Audio + Rumble + Network) caused by memory fragmentation.
* **FIX:** Reserved **256MB of physical RAM** exclusively for critical Kernel tasks (`min_free_kbytes`).
* **FIX:** **64-bit Binder IPC Enabled:** Unlocked the memory addressing limit which caused "No Address Space" errors.
* **FIX:** Hard-patched the source to set Binder Buffer to **4MB (Sweet Spot)** and optimized Threads to **64** for maximum stability.
* **Result:** No more reboots or freeze when shooting in Call of Duty.

### 2. 🖥️ Winlator & PC Emulation Ready
Standard Xiaomi kernels lock the memory mapping limit, causing PC emulators to crash.
* **FIX:** Hard-coded `max_map_count` to **524,288** (Steam Deck standard) directly in the source code.
* **Result:** Native support for **Winlator and Mobox** without "Permission Denied" errors.

### 3. 🔋 CPU Sweet Spot & Adreno Boost
Optimized for sustained performance without thermal throttling.
* **CPU Tuning:** Prime Core (7) locked to **Performance Mode** (2.01GHz) for instant processing.
* **GPU Adreno:** Enabled **"No Nap"** mode to prevent the GPU from sleeping between frames, ensuring maximum smoothness.
* **SchedTune:** Global Boost set to **10** for foreground tasks.

### 4. 🚀 System Optimizations & Joyose Killer
* **Joyose Removed:** Disables the service that throttles performance.
* **I/O Read-Ahead:** Boosted to **2048KB** for fast asset loading.
* **TCP BBR:** Enabled congestion control for stable high-bitrate streaming.
* **120Hz Locked:** Ensures maximum smoothness.

---

## 🧪 Tested Configurations
Validated on **Xiaomi Pad 5 (Nabu)** with:
* **Artemis** (2560x1600 / 120 FPS / 150Mbps)
* **BetterXCloud** (Xbox Cloud Gaming)
* **Winlator / Mobox** (PC Emulation)

---

## 📥 Installation
1.  **Backup your current Boot image** in TWRP (Critical).
2.  Flash `Onizuka_Kernel_V1.1_Stable.zip`.
3.  Reboot.
4.  *Wait 25 seconds after boot for the Magisk script to apply settings.*
---
This is the stable release. I might release other versions if I encounter bugs that need fixing in the long term.
---

## 🏆 Credits & Special Thanks
This project stands on the shoulders of giants:

* **Xiaomi:** For the kernel source code.
* **osm0sis:** For the AnyKernel3 flashable zip template.
* **The Linux Kernel Team:** For the upstream patches (BBR, Schedutil) and driver support.
* **AI Assistance:** For help with log analysis and debugging the memory allocation crashes.

---

## 📸 Proofs & Benchmarks
<p align="center">
  <img src="https://github.com/user-attachments/assets/1cd7cd3a-9bd1-4117-9903-269828bb44a1" width="45%" />
  <img src="https://github.com/user-attachments/assets/9cefe5a1-cc57-4aef-9347-ef14f47e4545" width="45%" />
</p>

<div align="center">
<i>"Built for low latency. Built for rumble. Built for Gaming."</i>
</div>
