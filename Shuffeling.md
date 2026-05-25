# Drive Mechanism: Shuffling Linkage 

## 1. Concept & Inspiration
For this combat robot, the core goal is to utilize the 50% weight bonus by implementing a mechanical shuffling mechanism 
instead of traditional wheels. After researching various walking linkages on YouTube, the focus shifted to designing a custom, high-efficiency locomotion system.

## 2. Design Iterations & Prototyping

### Iteration 1: Digital Simulation (Discontinued)
* **Approach:** Attempted to model and simulate a multi-link walking mechanism using complex assembly mate connectors directly in OnShape.
* **Result:** Discontinued after a few days. The cyclic dependencies of the mates led to an assembly deadlock, making the CAD file unmanageable.
* **Key Learning:** Simulating closed-loop kinematic chains in standard CAD mates requires is above my competence. Physical prototyping will be faster than digital debugging for me.

### Iteration 2: Cam-Driven Shuffling Mechanism
* **Approach:** Designed a simplified mechanism from scratch. Instead of complex leg joints, this version uses a constant-rotation DC motor paired with an off-center circular cam (eccentric drive).
* **Functionality:** The eccentric cam translates the continuous rotation of the motor into an alternating, elliptical lifting and stepping motion to provide constant floor contact and drive traction.
* **Testing:** Manufactured via FDM printing using PLA for immediate physical verification of the kinematic clearance and friction.
