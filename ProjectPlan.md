# Project: 225g Antweight Shuffler "Cool Name"

## 1. Goals
* **Goal:** Building a first version of a Combat Robot for the ROFLS-League until October 2026, followed by iterative improvements based on fight performance.
* **Category:** Antweight Shuffler. Max. Weight: 225g (150g base weight + 50% Shuffler bonus).

## 2. Technical Specifications (Target State)
### Mechanics & Chassis
* **Drive Mechanism:** Mechanical Shuffling/Walking Linkage (e.g., Klann or Jansen mechanism) driven by DC motors to qualify for the 50% weight bonus.
* **Weapon System:** Active Vertical Spinner, mounted at a 45° angle. Focused on a fixed, non-modular setup to keep the project's complexity manageable.
* **Planned Materials:** Nylon (PA) for high-impact structural components (hydrated), TPU for armor/shock absorption, and potentially Carbon Fiber for the main chassis stiffening.
* **Manufacturing:** In-house FDM printing via Bambu Lab P1S, external manufacturing services (PCBWay/JLCPCB) if custom metal parts or PCBs are required.
* **Input Mapping:** Linear Arcade Drive (Single-stick XY-mixing for intuitive movement without non-linear curve manipulation).
* **Stability Assist (Optional):** Toggleable Gyro-assisted heading hold via RC auxiliary switch to compensate for weapon-induced gyroscopic precession.

### Electronics & Software
* **Microcontroller:** Seed Studio XIAO (Esp32 Chip)
* **Protocol / Radio:** ExpressLRS (ELRS) via RadioMaster Pocket. Receiver unit TBD (Focus on serial CRSF protocol output).
* **Programming Language:** C 

## 3. Regulatory Requirements (ROFLS Compliance)
* **Failsafe:** Automatic shutdown of drive and weapon systems upon signal loss in less than 10 seconds (Target: < 2 seconds for advanced safety).
* **Weapon Stop:** Autonomous deceleration of the weapon spinning mass to a complete stop in less than 30 seconds after spin-down command.
* **Electrical Safety:** Highly visible Power-LED indicator. Mechanical switch or switch-mechanism allowed for the Antweight class.
* **Mechanical Safety:** Dedicated physical locking pin (Weapon Lock) for the 45° spinner outside the arena.

## 4. Modular Dev-Plan (Proof of Concepts)
* [x] **PoC 1: Mechanical Linkage Kinematics** (Testing a single leg mechanism for smooth operation, low friction, and grip).
* [x] **PoC 2: ELRS Signal Decoding, Failsafe Logic & Arcade Mixing** (C implementation of non-blocking serial reading, linear XY-mixing, and basic input validation on a breadboard).
* [ ] **PoC 3: Brushless Weapon Control & Active Brake** (Implementing the 30s stop rule safely via software/ESC).
* [ ] **PoC 4: Enclosed Power & Electronics Integration** (Power management, voltage regulation, and wiring harness footprint).
* [ ] **PoC 5: Integration Prototype v1** (Full chassis printed in cheap PLA to verify weight distribution and center of mass).

## 5. Documentation
The whole Project gets Documented with a structured CSV work journal and semantic summaries of the individual parts. This serves as a direct preparation for the IPA (final apprenticeship exam) and acts as a potential showcase project for future job applications.
