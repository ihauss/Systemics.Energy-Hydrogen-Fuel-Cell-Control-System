# 🚛 Hydrogen Fuel Cell Control System — Le Mans World Record

[![C](https://img.shields.io/badge/C-Embedded-blue)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Microchip](https://img.shields.io/badge/Microchip-MCU-red)](https://www.microchip.com/)
[![CAN](https://img.shields.io/badge/CAN-Bus-green)](https://en.wikipedia.org/wiki/CAN_bus)
[![I2C](https://img.shields.io/badge/I2C-Communication-yellow)](https://en.wikipedia.org/wiki/I2C)
[![Record](https://img.shields.io/badge/Record-World_Record-gold)](https://www.youtube.com/watch?v=N4Ja7tXK798)

> **Embedded C software that stabilised a hydrogen fuel cell stack – enabling a hydrogen‑powered tuk‑tuk to achieve a world record of 800+ km in 24 hours at Le Mans.**

🎥 **Official Company Vlog:** [Watch the Le Mans record attempt](https://www.youtube.com/watch?v=N4Ja7tXK798)

---

## 🔧 The Challenge

A hydrogen fuel cell stack requires **precise, real‑time regulation** of multiple interdependent parameters to operate safely and efficiently:

- **Temperature** – too low kills efficiency; too high becomes dangerous
- **Hydrogen leaks** – H₂ is odourless and invisible, so a leak can go unnoticed until it's too late
- **Voltage stability** – output must remain within tight bounds
- **Oxygen‑hydrogen mix** – the stack uses ambient air for both cooling *and* oxygen supply; that balance is critical

> ⚠️ On a small, resource‑constrained embedded system (Microchip MCU), there is no room for heavy OS abstractions or ML models – just fast, deterministic C code talking directly to sensors and actuators via CAN bus and I2C.

---

## 🎯 My Contribution

I joined the project as an **embedded systems developer**, taking ownership of the hydrogen stack control module in two distinct phases.

### Phase 1 – Codebase Rehabilitation

The existing codebase was functional but undocumented, unversioned, and inconsistent in style – a silent risk for any safety‑critical system.

**What I did:**
- Wrote **complete documentation** (module descriptions, function behaviours, expected I/O ranges)
- Added **inline comments** for non‑obvious logic and hardware interactions
- Introduced **Git version control** to track changes and enable collaboration
- Standardised the code to meet **professional embedded coding standards** (naming, error handling, static analysis readiness)

> 📌 *This phase was about turning a fragile prototype into a maintainable, auditable codebase – essential before any further development could happen safely.*

### Phase 2 – System Rescaling for a Smaller Stack

The hydrogen and electronics engineers needed to **scale down the technology** for a smaller stack (different thermal mass, flow rates, and voltage curves). I worked directly alongside them to adapt the control logic:

- Re‑tuned **temperature regulation loops** for the smaller stack's faster thermal dynamics
- Adjusted **voltage stabilisation parameters** to maintain output quality under varying load
- Validated **leak detection thresholds** and fail‑safe responses
- Updated **air flow management** (since the same air serves both cooling and oxygen supply)

**The result:** a stable, production‑ready embedded system that doubled the vehicle's usable energy capacity while maintaining safety margins.

---

## 🛠️ Tech Stack

| Layer               | Technologies                                                              |
|---------------------|---------------------------------------------------------------------------|
| **Microcontroller** | Microchip MCU (embedded C)                                                |
| **Communication**   | CAN bus, I2C                                                              |
| **Low‑level I/O**   | PWM, GPIO, ADC (sensor reading), timer interrupts                         |
| **Development**     | Git, embedded C toolchain (Microchip IDE / compiler)                      |
| **Target vehicle**  | Hydrogen‑powered tuk‑tuk (light mobility platform)                        |

> 💡 *No RTOS – bare‑metal C with careful interrupt prioritisation for deterministic timing.*

---

## 🧠 How It Works – Control Overview

```
[Hydrogen Stack]
      │
      ├─ Temperature sensor ──→ PWM fan control ──→ [Cooling]
      ├─ Voltage sensor    ──→ load balancing  ──→ [Stable output]
      ├─ H₂ leak sensor    ──→ emergency stop  ──→ [Safety]
      ├─ O₂ sensor (ambient air) ──→ flow regulation ──→ [Mix control]
      └─ CAN/I2C bus ──→ communication with vehicle main control unit
```

The embedded C code runs on a **Microchip MCU**, reading all sensors via ADC or digital interfaces, applying regulation logic, and driving actuators (fans, valves, PWM signals) in real time – all within strict timing constraints.

---

## 📊 Key Results

| Metric                              | Achievement                                                    |
|-------------------------------------|----------------------------------------------------------------|
| **Distance covered**                | **> 800 km** (some sources report 900 km on a single charge)  |
| **Duration**                        | 24 hours non‑stop driving                                      |
| **Hydrogen used**                   | Just 2 kg of H₂ for the entire run          |
| **Platform**                        | Light hydrogen‑powered tuk‑tuk (ambient air cooling + oxygen)  |
| **My contribution**                 | Codebase documentation, Git introduction, coding standards, then system rescaling for a smaller stack |
| **Impact**                          | ✅ Stable, safe hydrogen operation<br>✅ Doubled usable energy capacity<br>✅ **World record** at the 2024 24 Hours of Le Mans |

---

## 🚀 What I Learned

- **Rapid adaptation to unfamiliar domains.** I joined with zero hydrogen or fuel cell experience – within weeks I was discussing thermal dynamics and voltage curves with the hardware engineers and implementing the fixes in C.
- **Documentation is not optional.** The undocumented codebase was a major risk; after adding docs and Git, the team could safely evolve the system.
- **Embedded C is unforgiving but powerful.** No garbage collector, no safety net – just deterministic, bit‑level control. It forced me to think about *every* cycle and *every* byte.
- **Hardware‑software co‑design is different.** When you rescale a physical system (smaller stack), you must re‑tune the software alongside hardware changes – not just recompile.
- **Safety‑critical thinking.** Leak detection and fail‑safe responses become second nature when the fuel is invisible and odourless.

---

## 📸 Gallery

| Media                                                              | Description |
|--------------------------------------------------------------------|-------------|
| 🎥 [Official company vlog (YouTube)](https://www.youtube.com/watch?v=N4Ja7tXK798) | The Le Mans record attempt – including the hydrogen tuk‑tuk in action |
| 🖼️ *(Coming soon)*                                                | System architecture diagram (CAN / I2C / PWM layout) |
| 🖼️ *(Coming soon)*                                                | Photo of the Microchip MCU board with sensor connections |

---

## 📄 License & Status

- **Project status:** ✅ Successfully completed – world record achieved at the 2024 24 Hours of Le Mans
- **Technology:** Deployed in Systemics Energy's hydrogen light‑mobility platform
- **Contact:** [ismael.hauss@gmail.com](mailto:ismael.hauss@gmail.com) – open to discussing embedded systems, fuel cell control, or safety‑critical software roles

---

> *From zero hydrogen experience to a world record – all in C, all on bare metal.*
