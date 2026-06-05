# ⚙️ Mechanical Counter — Fusion 360
A 3D-modeled mechanical counter that replicates the classic odometer-style digit wheel mechanism, designed entirely in **Autodesk Fusion 360**.

## 🎯 Project Description

This project is a **3-digit mechanical counter** (units, tens, hundreds) capable of counting from **000 to 999**, operated manually by pushing a lever up or down to increment or decrement the displayed value.

The design is inspired by pre-digital mechanical counters found in tape decks, car odometers, and utility meters — devices that performed reliable decimal counting with nothing but precisely shaped wooden or plastic parts. No electronics. No software. Just geometry in motion.

Every component was modeled from scratch in **Fusion 360**, carefully replicating the two core mechanical principles that make this kind of counter work:

- A **ratchet mechanism** that translates a lever push into exactly one digit of rotation
- A **carry gear mechanism** that automatically propagates a carry from units → tens → hundreds whenever a digit rolls over from 9 to 0

The result is a satisfying, fully mechanical counting device where every click of the lever is a small lesson in mechanical engineering.


## 📋 Parts & Components

### 🏗️ Enclosure

| Part (Fusion 360) | Technical Name | Thickness | Role |
|---|---|---|---|
| `side` | Side panel (×2) | 10mm | Left and right walls — hold all axles and the entire mechanism; include holes for M2 assembly screws |
| `top` | Top cover | 10mm | Roof panel with **3 rectangular windows** through which the digits are visible |
| `bottom` | Base | 10mm | Bottom plate — provides structural rigidity; includes M2 screw holes for assembly |
| `support1` | Inner support (left) | 10mm | Interior plate with cutouts — aligns and supports both the digit cylinder axle and the gear axles |
| `support2` | Inner support (right) | 10mm | Second interior plate — mirrors support1; also provides mounting points for the lever increment mechanism |

---

### 🔢 Digit Wheels

| Part (Fusion 360) | Technical Name | Role |
|---|---|---|
| `cylinder` | Digit rotor | Large cylinder on which digits **0–9** are displayed — rotates 1/10 of a full turn per increment, showing one new digit in the window |
---

### 🖐️ Increment / Decrement Mechanism (Ratchet)

| Part (Fusion 360) | Technical Name | Role |
|---|---|---|
| `gear5` | Ratchet wheel | **10 teeth** — mounted on the units rotor axle; receives impulse from the yoke and advances exactly **1 tooth = 1 digit** per lever action |
| `copy` | Ratchet yoke | Horseshoe-shaped arc that **wraps around `gear5`** on both sides — one end advances the wheel on increment, the other on decrement; the small hole is its pivot point |
| `handle2` | Advance lever | Long bar with a notch at one end and pivot hole at the other — **the lever the user pushes** up or down to increment or decrement |
| `handle3` | Detent lever | Similar bar to `handle2` — keeps the yoke centered at rest and provides a **click-stop** for each digit position; prevents the rotor from drifting freely |
| `handle4` | Cam lever | **Z-shaped** piece with pivot hole at top and active arm at bottom — connects lever motion to the yoke, converting the push into a precise 1-tooth advance |
| `rubber` | Return spring | Elastic band or flexible strip — pulls all levers back to the neutral center position after each action; maintains system tension |

---

### ⚙️ Carry Mechanism (Digit Transfer)

| Part (Fusion 360) | Technical Name | Teeth / Shape | Role |
|---|---|---|---|
| `gear1` | Advance gear | **21 teeth** | Large gear fixed to the rotor — receives the carry impulse and rotates the digit cylinder by exactly 1/10 of a turn |
| `gear2` | Carry trigger | **2 active teeth** (rest removed) | Mounted on the rotor — when passing from 9→0, its 2 teeth catch `gear4` and trigger the carry |
| `gear3` | Carry disk | Solid disc with **one notch** | Sits beside `gear4` — **locks** it for 9 out of 10 increments; the notch only aligns once per full rotor rotation, allowing the carry to pass through |
| `gear4` | Carry gear | **8 teeth** alternating: 4×short (5mm) + 4×tall (15mm) | The heart of the carry mechanism — short teeth ride on the flat face of `gear3` and **lock** rotation; tall teeth pass through the notch and **transmit** the carry to `gear1` of the next digit |

> **How `gear4` works in detail:**
>
> `gear4` has 8 alternating teeth — one short (5mm), one tall (15mm), repeated 4 times around the wheel.  
> Sitting right next to it is `gear3`: a solid disc with a single notch cut into its edge.
>
> **LOCKED state (9 out of every 10 increments):**  
> The 4 short teeth (5mm) of `gear4` press against the flat face of `gear3`.  
> The disc physically blocks them — `gear4` cannot rotate.  
> The digit stays in place.
>
> **FREE state (at the 9→0 transition):**  
> `gear2` (the 2-tooth trigger on the units rotor) strikes `gear4` and nudges it slightly.  
> At that exact moment, the notch in `gear3` aligns with one of the tall teeth (15mm) of `gear4`.  
> The tall tooth passes through the notch — `gear4` rotates freely and engages `gear1` (21 teeth) of the tens rotor.  
> `gear1` is fixed to the tens cylinder — it carries it along for 1/10 of a rotation.  
> The tens digit advances by 1.

Comparison of `gear2` & `gear3` with `gear4`:
<img width="809" height="498" alt="img1" src="https://github.com/user-attachments/assets/8daa0f50-8228-42a3-9c42-5fc4cf987590" />

Comparison of `gear1` with `gear4`:
<img width="802" height="448" alt="img2" src="https://github.com/user-attachments/assets/520bf392-2fc4-4077-8fe3-56c025fafc97" />

### 🔩 Axles & Structural Rods

> ⚠️ `stick1` and `stick2` were modeled in Fusion 360 — but in real life **1mm metal rods** will be used in the physical assembly instead.

| Part (Fusion 360) | Technical Name | Role |
|---|---|---|
| `stick1` | Main axle | Primary rod running through all supports — carries the digit rotors and gears |
| `stick2` | Secondary rod | Secondary guide rod — pivot or rail for the lever mechanism |

---

### 🔧 Additional Notes on Parts

| Part (Fusion 360) | Note |
|---|---|
| `part 5` | Spacer washer — designed specifically to **keep the increment/decrement mechanism properly spaced and aligned** on the axle; prevents the ratchet components from shifting laterally during use |
| `rubber` | Return spring — designed to pull the levers back to the neutral position after each action; **will not be used in the physical build** — a real elastic band will be used instead |

> ⚠️ **Threading / screw holes** were **not implemented** in the 3D models — real M2 screws and hardware will be used for final assembly.


## ⚙️ Gear Parameters & Calculations
For those who want to use Fusion 360's built-in **Spur Gear** generator instead of modeling the gears manually, the parameters for both gears are attached below.

| Parameter | `gear4` (8T) | `gear1` (21T) |
|---|---|---|
| Standard | Metric | Metric |
| Pressure Angle | 20° | 20° |
| Module | 4.35 | 4.35 |
| Number of Teeth | 8 | 21 |
| Backlash | 0.13 mm | 0.13 mm |
| Root Fillet Radius | 1 mm | 1 mm |
| Gear Thickness | 10 mm | 5 mm |
| Hole Diameter | 3 mm | 3 mm |

## 📐 Center Distance

The exact **center-to-center distance** between `gear1` (21T) and `gear4` (8T) is **63.075 mm**.

Calculated using:


### ⚙️ Gear Parameters & Calculations

For those who want to use Fusion 360's built-in **Spur Gear** generator instead of modeling the gears manually, the parameters for both gears are attached below — configured for **21 teeth** (`gear1`) and **8 teeth** (`gear4`) respectively.

<-- attach your gear screenshots here -->

### Center Distance Calculation

To avoid having to recalculate, here is the exact **center-to-center distance** between `gear1` (21T) and `gear4` (8T): 

---

### 🔗 Joint Angles (Motion Simulation)

When setting up **Revolute Joints** in Fusion 360 to simulate gear rotation, use the following values — no need to calculate them yourself:

| Gear | Rotation |
|---|---|
| `gear1` — 21 teeth | 360° |
| `gear4` — 8 teeth | 147.142° |

## 📚 Resources & Credits

- **Primary Mechanical Reference & Inspiration:** Matthias Wandel — [Building a Mechanical Counter](https://woodgears.ca/counter/index.html)
- **Video Reference 1:** [Mechanical Counter Build](https://www.youtube.com/watch?v=rjWfIiaOFR4) — woodgears.ca
- **Video Reference 2:** [Counter Overview](https://www.youtube.com/watch?v=lwt8QujQv5s) — woodgears.ca
- **Video Reference 3:** [3D Printed Mechanical Counter](https://www.youtube.com/watch?v=L6YOfVzRH7Q)
