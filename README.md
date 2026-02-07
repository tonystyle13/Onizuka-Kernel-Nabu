<img width="2816" height="1536" alt="Onizuka_logo" src="https://github.com/user-attachments/assets/08842cbe-9813-48f2-802d-d88cdf87fe27" />
<div align="center">

# 👹 ONIZUKA KERNEL V1
### The Ultimate Cloud Gaming Kernel for Xiaomi Pad 5 (Nabu)
### *Optimized for Stock HyperOS (Android 13)*

[![Version](https://img.shields.io/badge/Version-V1.0-red?style=for-the-badge)](https://github.com/tonystyle13)
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
After testing dozens of AOSP ROMs, I found that decoding latency for high-bitrate cloud gaming was always higher than on Stock ROMs. I returned to the official **OS1.0.6.0.TKXEUXM** and the performance difference was night and day:
* **BetterXCloud:** Latency dropped to **4-5ms**.
* **Artemis (Moonlight Fork):** Latency dropped to **5-7ms** even at **Native 2560x1600 @ 120 FPS**.

**The Problem:**
While fast, the Stock ROM had a critical flaw: the **Bluetooth Controller vs. Touchscreen conflict**. Streaming at high resolution while using a controller with rumble would overload the system memory allocation, causing the touchscreen to freeze or the tablet to violently reboot (Kernel Panic) during heavy action scenes like shooting in Call of Duty.

**Onizuka Kernel V1 is the survivor.** It keeps the incredible low latency of the Stock ROM while implementing "Ironclad" stability fixes to prevent crashes under heavy load.

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

### 1. 🛡️ Anti-Crash Memory Guard 
Fixed reboots during heavy gameplay (Audio + Rumble + Network) caused by memory fragmentation.
* **FIX:** Reserved **128MB of physical RAM** exclusively for critical Kernel tasks (`min_free_kbytes`).
* **FIX:** Hard-patched the source to increase Binder Buffer to **4MB** and increased Threads to **128**.
* **Result:** No more reboots when shooting in Call of Duty.

### 2. 🖥️ Winlator & PC Emulation Ready
Standard Xiaomi kernels lock the memory mapping limit, causing PC emulators to crash.
* **FIX:** Hard-coded `max_map_count` to **524,288** (Steam Deck standard) directly in the source code.
* **Result:** Native support for **Winlator and Mobox** without "Permission Denied" errors.

### 3. 🔋 Voltage Stability (Schedutil)
The "Performance" governor was too aggressive on some units, causing power and battery collapse.
* **Optimized:** Switched to a custom-tuned **Schedutil** (0.5ms reaction time).
* **Benefit:** Maximum responsiveness while preventing sudden shutdowns.

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
2.  Flash `Onizuka_Kernel_V1.zip`.
3.  Reboot.
4.  *Wait 25 seconds after boot for the Magisk script to apply settings.*
---
This is the first release, i might release other versions if I encounter bugs that need fixing in the long term.
---

## 🏆 Credits & Special Thanks
This project stands on the shoulders of giants:

* **Xiaomi:** For the kernel source code.
* **osm0sis:** For the AnyKernel3 flashable zip template.
* **The Linux Kernel Team:** For the upstream patches (BBR, Schedutil) and driver support.
* **Gemini Pro** For help with log analysis and debugging the memory allocation crashes.

---
<div align="center">
<i>"Built for low latency. Built for rumble. Built for Gaming."</i>
</div>
