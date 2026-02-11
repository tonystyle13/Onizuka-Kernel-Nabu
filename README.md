<img width="2560" height="1396" alt="Onizuka_logo" src="https://github.com/user-attachments/assets/13b90daf-eff0-4ce6-b7e4-1b15c2334a7e" />

<div align="center">

# 👹 ONIZUKA KERNEL V1.2
### The Ultimate Cloud Gaming Kernel for Xiaomi Pad 5 (Nabu)
### *Optimized for Stock HyperOS (Android 13)*

[![Version](https://img.shields.io/badge/Version-V1.2-red?style=for-the-badge)](https://github.com/tonystyle13)
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
    * *Why?* The core optimization scripts (GPU Boost, CPU Tuning, Joyose Killer) are injected into `/data/adb/service.d/`. **Without Magisk, these scripts will NOT run.**

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

After testing numerous kernels and going through several build iterations, I finally achieved the perfect stability build.
**Onizuka Kernel V1.2** is the evolution. It moves away from heavy memory hacks and solves the root cause (Input Driver Fixes) while keeping the incredible low latency of the Stock ROM.

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

### 1. 🛡️ Smart Stability & Input Fix (V1.2 Update)
Replaced the old memory hacks with surgical driver fixes.
* **FIX:** **Tactile Rescued:** Removed the "0/0/0" EV_SYN filter in `input.c` that was causing the touchscreen to freeze during heavy gaming.
* **FIX:** **Null Pointer Guard:** Added strict checks (`!dev`) in Input and HID drivers to prevent Kernel Panics if a device disconnects.
* **FIX:** **Clean Binder:** Now using 32-bit Binder with 4MB buffer injected via Command Line (AnyKernel) instead of hard-patching source. Safer and cleaner.

### 2. 🎮 Rumble Throttle & Protection
Cloud Gaming can sometimes spam vibration data, choking the tablet.
* **FIX:** Implemented a **Smart Throttle** in `ff-memless`. It limits vibration updates to every 4ms, which is invisible to the user but saves the CPU from crashing.
* **FIX:** Added **Clamps** (Limiters) for Sony, Xbox, and Nintendo controllers to prevent motors from requesting unsafe power levels.

### 3. 🔋 CPU Sweet Spot & Adreno Boost
Optimized for sustained performance without thermal throttling.
* **CPU Tuning:** L3 Cache minimum frequency boosted to **1612MHz** via script for snappier asset loading.
* **GPU Adreno:** Enabled **"No Nap"** mode via script to prevent the GPU from sleeping between frames, ensuring maximum smoothness.
* **SchedTune:** Global Boost set to **10** for foreground tasks.

### 4. 🚀 System Optimizations & Joyose Killer
* **Joyose Removed:** Disables the service that throttles performance.
* **I/O Read-Ahead:** Boosted to **2048KB** for fast asset loading.
* **TCP BBR + Busy Poll:** Enabled congestion control and network busy polling for lower latency in streaming.
* **120Hz Locked:** Script enforces min/peak refresh rate to 120Hz after boot.

---

## 🧪 Tested Configurations
Validated on **Xiaomi Pad 5 (Nabu)** with:
* **Artemis** (2560x1600 / 120 FPS / 150Mbps)
* **BetterXCloud** (Xbox Cloud Gaming)
* **Winlator / Mobox** (PC Emulation)

---

## 📥 Installation
1.  **Backup your current Boot image** in TWRP (Critical).
2.  Flash `Onizuka_Kernel_V1.2.zip`.
3.  Reboot.
4.  *Wait 60 seconds after boot for the Magisk script to apply settings.*
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
