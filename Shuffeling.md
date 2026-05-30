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

### Iteration 3: Tolerance Profiling & Kinematic Deadlocks (v3.0)
* **Approach:** Manufactured a physical test rig using PLA to analyze structural tolerances and multi-axis alignment (Gear -> Cam -> Frame Axis -> Secondary Gear).
* **Results & Vulnerabilities:**
  * **Tolerance Limits:** Testing revealed that a 0.2 mm clearance caused immediate binding, while 0.4 mm introduced excessive mechanical backlash. The optimal tolerance for the Bambu Lab P1S printer was benchmarked at exactly 0.3 mm.
  * **Mechanical Complexity:** The fragmented multi-part axis setup required high assembly effort and introduced potential axial failure points under combat loads.
  * **Kinematic Deadlock:** Discovered that the auxiliary leg alignment axis must be strictly synchronized via gearing. While a slot guidance approach could have been used to alter the X/Y axis movement distribution, it was rejected due to invertibility requirements. When flipped upside down, the robot will rest on its weapon protector, tilting its chassis. In this inverted state, the Y-axis movement effectively translates into crucial X-axis forward propulsion, proving highly beneficial for drivability.

### Iteration 4: Monolithic Design for Manufacturing - DFM (v3.1)
* **Approach:** Complete overhaul focused on radical parts-reduction and structural simplification using the *Spur Gear FeatureScript* in OnShape.
* **Key Modifications:**
  * **Part Reduction:** Merged functions into monolithic prints, reducing the core drive assembly to just 8 robust components (Frame, main gears, shuffling leg, and two eccentric wheels).
  * **Integrated Component Geometry:** The spur gear, eccentric cam pin (8 mm stroke), and the rotation shaft were fused into a single 3D-printable component to eliminate loose fasteners.
  * **Print Optimization:** Designed geometries to print completely support-less. Slicing parameters adjusted to a minimum of 4 perimeters (wall lines) and 10% infill to maximize printing speed during the prototyping phase.
  * **Calculated Dynamics:** Operating at approx. 1400 RPM on a 2S LiPo configuration with an 8 mm eccentric stroke results in a theoretical velocity of $\approx 0.37 \text{ m/s}$ ($1.34 \text{ km/h}$). This delivers an optimized balance between drivability, mechanical high-torque control, and minimized chassis vibration.
* **Current Status:** Prototype v3.1 is currently slicing/printing. Next step: physical assembly and hand-testing the 0.3 mm tolerance fitments under simulated motor loads.

### Iteration 5: Physical Load Testing & Weight Benchmarking (v3.2)
* **Approach:** Assembled the printed v3.2 components and conducted manual stress-testing to simulate real-world combat loads and structural compression.
* **Results & Critical Vulnerabilities:**
  * **Structural Deflection:** While the mechanism rotated flawlessly when loose, applying realistic chassis pressure caused the outer walls to deflect inward, causing immediate gear binding and binding of the eccentric cams. 
  * **Weight Penalty:** A single drive module weighed in at 53g (excluding the motor). With a total weight limit of 225g for the entire robot, this iteration is drastically overweight.
  * **Traction Issues:** Low-load testing indicated that the hard PLA feet lack sufficient mechanical grip on smooth arena floors at high stamp rates.
* **Engineering Solutions & Action Plan:**
  * **Parallelism:** Integrate M2 aluminum standoffs/spacers in the CAD model to mechanically lock the housing walls in a perfectly parallel orientation, eliminating deflection.
  * **Mass Reduction:** Redesign the geometry for v4.0 with a target of 30% size reduction, minimizing wall thickness and removing non-critical structural mass.
