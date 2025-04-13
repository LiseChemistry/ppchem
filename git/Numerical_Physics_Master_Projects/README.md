# 📚 **Numerical Physics – Master Projects**
)
[![Python](https://img.shields.io/badge/code-Python-yellow?style=flat-square&logo=python)](https://www.python.org/)
[![C](https://img.shields.io/badge/code-C-blue?style=flat-square&logo=c)](https://en.wikipedia.org/wiki/C_(programming_language))
[![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)

🔹 **Project I: Monte Carlo Simulation of Phase Transitions in 2D Lennard-Jones Systems**
&nbsp;&nbsp;&nbsp;&nbsp;• Initial Configuration Setup
&nbsp;&nbsp;&nbsp;&nbsp;• Monte Carlo Simulation
&nbsp;&nbsp;&nbsp;&nbsp;• Heating Simulation
&nbsp;&nbsp;&nbsp;&nbsp;• Cooling Simulation
&nbsp;&nbsp;&nbsp;&nbsp;• Isotherms and Pressure Measurement
&nbsp;&nbsp;&nbsp;&nbsp;• Phase Transition Characterization

🔹 **Project II: Random Number Generators**
&nbsp;&nbsp;&nbsp;&nbsp;• Linear Congruential Generator Definition

🔹 **Project III: Molecular Dynamics Simulation**
&nbsp;&nbsp;&nbsp;&nbsp;• Performing **energy conservation checks**
&nbsp;&nbsp;&nbsp;&nbsp;• Generating **physical properties plots** (temperature, pressure, energy)
&nbsp;&nbsp;&nbsp;&nbsp;• Analysis of **melting behavior** starting from an ordered structure

> 🧠 Developed using **C** for high-performance numerical tasks and **Python** for data fitting and visualization.

---

## 🧮 Project I: Monte Carlo Simulation of Phase Transitions in 2D Lennard-Jones Systems

### 🔍 Overview

To illustrate phase transitions in a 2D Lennard-Jones system using the **Metropolis Monte Carlo algorithm**. While 3D phase diagrams provide a reference, 2D systems exhibit subtleties that are still under scientific debate. However, for qualitative analysis, our approach remains insightful and effective.

### Monte Carlo Simulation

- Implement the **Metropolis Monte Carlo algorithm**.
- Generate random displacements of particles.
- Accept or reject each move using the **Metropolis acceptance criterion**.

One **Monte Carlo step**  = **N attempted moves**, meaning each particle tries to move once on average. This definition provides a consistent unit of simulation time.

💡 *Tip:* A simple visualization of the particle configurations can be very helpful for interpreting results.

### ⚙️  Initial Configuration Setup

Create a 2D **perfectly ordered crystal** consisting of 100 particles arranged on a **square lattice**, ensuring it fits within the simulation box with **periodic boundary conditions**.

Generate 2 initial configurations:

- `L = 45`
- `L = 9`

### 🔥  Heating Simulation

- **Equilibrate** the configuration with `L = 10` at a low temperature (`kT = 0.01`).
- Gradually **increase the temperature** up to `kT = 10`.
- Analysis of the system's behavior.
- Comparing these results with those from a sample using `L = 40`.

### ❄️  Cooling Simulation

- Performing of the **reverse experiment**: gradually **decrease** the temperature.
- Analysis of the structural changes during cooling.

### 📈  Isotherms and Pressure Measurement

- Measuring the **pressure** using the **virial method**. 
- Plot of an **isotherm**: pressure \( P \) as a function of volume \( V \) at a **fixed temperature** (`kT = const`).

### 🌐  Phase Transition Characterization

- At `kT = 0.05`, conducting of the simulations to plot the **average energy per particle** as a function of **density** over the range \([0, 1.3]\).
- Conclusion about the **phase transition**.

### 🛠️ Tools:

- `Python` / `C`
- Scientific libraries: `NumPy`, `Matplotlib`.
- Visualization tools:`VMD`, `Avito`.

### 🧠 Learning Outcomes

- Master the Metropolis Monte Carlo method
- Understand phase transitions in low-dimensional systems
- Visualize and interpret simulation data
- Explore thermodynamic quantities like energy, pressure, and density

---

## 🎲 Project II: Random Number Generators

### 🔍 Overview

This project aims to study the behavior, limitations, and statistical properties of **pseudo-random numbers** generated using a **Linear Congruential Generator (LC-RNG)**. By analyzing its period, correlation, and autocorrelation, we explore the reliability of such generators and propose methods for improvement.

### 🔢 Linear Congruential Generator Definition

The LC-RNG generates a sequence of numbers using the formula:

\[
x_{n+1} = (k x_n + l) \mod m, \quad r_n = \frac{x_n}{m}
\]

Where:
- \(k\), \(l\), \(m\): positive integers (parameters)
- \(x_0\): initial seed
- \(x_n\): integer values
- \(r_n\): normalized values in [0, 1)

### 1️⃣ Period Calculation

Implement an algorithm that computes the **period** of the sequence \({x_n}\), i.e., the number of steps before the sequence repeats.

#### 🔧 Test Cases:
- **P1**: `k = 899`, `l = 0`, `m = 32768`, `\(x_0\) = 12`
- **P2**: `k = 16807`, `l = 0`, `m = 6075`, `\(x_0\) = 12`
- **P3**: `k = 7^5`, `l = 0`, `m = 2^31 − 1`, `x_0 = 12`  

#### 🎯 Tasks:
- Determine the exact period length for each case.
- Investigate how **small changes in parameters** (e.g., \(k\) or \(m\)) affect the period.
- Conclusions on the quality of each parameter set.

### 2️⃣ Correlation Visualization

Write a program to generate a large number \(N\) of values using the LC-RNG. Then, create a **scatter plot**:

\[
(x_n, x_{n+1})
\]

#### 🎯 Tasks:
- Generate \(N\) values.
- Plot \(x_{n+1}\) vs \(x_n\) for different parameter sets (P1, P2, P3.)
- Results:
  - **patterns** vs **clusters**?
  - What do these patterns suggest about **randomness**?
- Explore the effect of **slightly modifying** the parameters.

### 3️⃣ Autocorrelation Function

Quantify correlation using the **autocorrelation function**.

#### 🔍 Definitions:

- Temporal Mean:
  \[
  \bar{x}(t) = \frac{1}{T} \sum_{t=1}^{T} x_t
  \]

- Correlation between two variables x and y:
  \[
  R_{xy} = \frac{1}{T} \sum_{t=1}^{T} x_t y_t
  \]

- Autocorrelation function:
  \[
  R_x(\tau) = \frac{1}{T} \sum_{t=1}^{T} x_t x_{t+\tau}
  \]

- Normalized Autocorrelation:
  \[
  C_x(\tau) = \frac{R_{\delta x}(\tau)}{R_{\delta x}(0)} = \frac{\sum_i (x_i - \bar{x})(x_{i+\tau} - \bar{x})}{\sum_i (x_i - \bar{x})^2}
  \]

  Where \(\delta x(t) = x(t) - \bar{x}\) and \(\tau\) is a time shift.

#### 🎯 Tasks:
- Compute \(C(\tau)\) for various lags \(\tau\)
- Test sequences:
  - Constant: \(1, 1, 1, 1, ...\)
  - Alternating: \(1, 2, 1, 2, ...\)
  - Random: \(+1, -1\)
- Results:
  - What value does \(C(\tau)\) take for perfectly correlated sequences?
  - What value for random ones?

### 4️⃣ Improved Generator

Improve the quality of LC-RNG output by **combining two weak generators**.

#### 💡 Method:
- LC-RNG #1 to generate a list of \(M_1\) values
- LC-RNG #2 to randomly **select an index** from that list
- Selected value as the random output
- Replacement of used value with a new one from LC-RNG #1

#### 🎯 Tasks:
- Implement both generators with poor parameters
- Evaluate whether this **combined method** increases:
  - Period
  - Decorrelation
  - Statistical randomness

### 📈 Final Results:
✔️ Plot: \(x_{n+1}\) vs \(x_n\)
✔️ Plot: Autocorrelation \(C(\tau)\)
✔️ Table: Periods for each parameter set

---
## 🧪 Project III: Molecular Dynamics Simulation

### 🔍 Overview

This project involves implementing a **Molecular Dynamics (MD)** simulation to study the behavior of particles interacting via a **Lennard-Jones potential**. The goal is to simulate atomic-scale material behavior under various conditions, and to validate the stability and physical relevance of the results.-

### ⚙️ Physical Model and Numerical Method

#### 🧊 System Description
- **Number of particles (N)**: Predefined and modifiable
- **Simulation box**: 2D square domain of size \( L \times L \)
- **Boundary conditions**: Periodic boundaries with **minimum image convention**

#### 🧲 Interactions
- **Lennard-Jones potential** (in reduced units):

  \[
  u(r) = 4 \left( \frac{1}{r^{12}} - \frac{1}{r^6} \right)
  \]

- **Interaction cutoff**: \( R_c = 2.5\sigma \)
  - Beyond this distance, inter-particle interactions are neglected for efficiency

#### ⏱️ Time Integration
- Numerical scheme: **Velocity-Verlet algorithm**
  - Chosen for its time-reversibility and energy conservation properties

### 📊 Final Results

#### 1️⃣ Code Validation and Justification
- Vverified code for the **correctness of the simulation**
- **Plot of energy conservation** over time for several integration time steps (Δt)
- Comparing the results with analytical values or simplified test cases

#### 2️⃣ Melting a Crystal: Qualitative Simulation
- Starting from a **regular lattice configuration** (e.g., simple cubic or square)
- System is allowed to evolve toward a **liquid state**
- Report of the **equilibrium temperature** achieved

#### 3️⃣ Graphical Analysis
- 🟠 **Kinetic Temperature**: Indicates thermal motion
- 🔵 **Potential Energy**: Shows interactions and phase changes
- 🟣 **Pressure**: Use the virial expression adapted for 2D Lennard-Jones

> Using these plots to discuss the stability of the system and identify transitions.

#### 4️⃣ Code File
- Submit a **well-commented source file** in `.c`
- Including:
  - A section to initialize the system
  - A function/subroutine for force calculations
  - The integration loop using Velocity-Verlet
  - Output of physical quantities

---

### License

The package is licensed under the MIT License.
