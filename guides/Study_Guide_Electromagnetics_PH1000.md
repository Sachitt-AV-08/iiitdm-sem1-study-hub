# End-Semester Exam Study Guide — Engineering Electromagnetics (`PH1000`)

**Course:** Engineering Electromagnetics (`PH1000`) — IIITDM Kancheepuram (Dr. Debolina Misra)  
**Textbooks Used in Slides:** David J. Griffiths (*Introduction to Electrodynamics*) & Bhag Singh Guru (*Electromagnetic Field Theory Fundamentals*)  
**Time Horizon:** Built for **< 4-day** exam readiness

> [!WARNING]
> **Misfiled Assignments Alert:** `EM_Assignment 1` and `EM_Assignment 3` in your folder belong to *PHY108T — Engineering Mechanics* (statics/trusses/centroids/MOI), **NOT** Engineering Electromagnetics (`PH1000`). Only `Assignment-1.pdf` (Electrostatics) and `Assignment-2` (Magnetostatics & Displacement Current) are for `PH1000`!

---

## 1. Formula & Vector Calculus Cheat Sheet

### 1.1 Coordinate Systems & Differential Elements (`lect_6`, `lect_7`)

| System | Variables | Point Conversion to Cartesian | Differential Length $d\mathbf{l}$ | Differential Volume $d\tau$ |
| :--- | :--- | :--- | :--- | :--- |
| **Cartesian** | $(x, y, z)$ | $(x, y, z)$ | $dx\,\hat{\mathbf{x}} + dy\,\hat{\mathbf{y}} + dz\,\hat{\mathbf{z}}$ | $dx\,dy\,dz$ |
| **Cylindrical** | $(\rho, \phi, z)$ | $x = \rho\cos\phi,\ y = \rho\sin\phi,\ z = z$ | $d\rho\,\hat{\boldsymbol{\rho}} + \rho\,d\phi\,\hat{\boldsymbol{\phi}} + dz\,\hat{\mathbf{z}}$ | $\rho\,d\rho\,d\phi\,dz$ |
| **Spherical** | $(r, \theta, \phi)$ | $x = r\sin\theta\cos\phi,\ y = r\sin\theta\sin\phi,\ z = r\cos\theta$ | $dr\,\hat{\mathbf{r}} + r\,d\theta\,\hat{\boldsymbol{\theta}} + r\sin\theta\,d\phi\,\hat{\boldsymbol{\phi}}$ | $r^2\sin\theta\,dr\,d\theta\,d\phi$ |

- **Surface Elements $d\mathbf{S}$:**
  - Cylindrical curved wall ($\rho = R$): $R\,d\phi\,dz\,\hat{\boldsymbol{\rho}}$; flat caps ($z = \text{const}$): $\pm \rho\,d\rho\,d\phi\,\hat{\mathbf{z}}$.
  - Spherical shell ($r = R$): $R^2\sin\theta\,d\theta\,d\phi\,\hat{\mathbf{r}}$.
- **Cylindrical $\leftrightarrow$ Spherical Point Conversion:**
  $$\rho = r\sin\theta, \quad z = r\cos\theta, \quad \phi = \phi; \qquad r = \sqrt{\rho^2+z^2},\quad \theta = \tan^{-1}(\rho/z).$$
- **Vector Transformation Exam Trap:** Basis vectors $(\hat{\mathbf{r}},\hat{\boldsymbol{\theta}},\hat{\boldsymbol{\phi}})$ depend on position! **Never** add two vectors defined at different points directly in spherical/cylindrical form — convert both to Cartesian first!
  - Spherical $(A_r, A_\theta, A_\phi) \to$ Cylindrical $(A_\rho, A_\phi, A_z)$:
    $$A_\rho = A_r\sin\theta + A_\theta\cos\theta, \qquad A_\phi = A_\phi, \qquad A_z = A_r\cos\theta - A_\theta\sin\theta.$$

### 1.2 Del Operator & Fundamental Theorems (`lect_8`–`lect_13`)
- **Gradient:** $\nabla T = \frac{\partial T}{\partial x}\hat{\mathbf{x}} + \frac{\partial T}{\partial y}\hat{\mathbf{y}} + \frac{\partial T}{\partial z}\hat{\mathbf{z}}$. Points in the direction of **maximum increase**; unit normal to surface $f(x,y,z)=c$ is $\hat{\mathbf{n}} = \frac{\nabla f}{|\nabla f|}$.
- **Divergence & Curl (Cartesian & Curvilinear):**
  - Cylindrical Div: $\nabla\cdot\mathbf{F} = \frac{1}{\rho}\frac{\partial(\rho F_\rho)}{\partial\rho} + \frac{1}{\rho}\frac{\partial F_\phi}{\partial\phi} + \frac{\partial F_z}{\partial z}$.
  - Spherical Div: $\nabla\cdot\mathbf{F} = \frac{1}{r^2}\frac{\partial(r^2 F_r)}{\partial r} + \frac{1}{r\sin\theta}\frac{\partial(\sin\theta F_\theta)}{\partial\theta} + \frac{1}{r\sin\theta}\frac{\partial F_\phi}{\partial\phi}$.
  - $\nabla\cdot\mathbf{F} > 0$ (source), $< 0$ (sink), $= 0$ (**solenoidal**). $\nabla\times\mathbf{F} = \mathbf{0}$ (**irrotational / conservative**).
  - Vector identities: $\nabla\times(\nabla T) = \mathbf{0}$, $\nabla\cdot(\nabla\times\mathbf{v}) = 0$.
- **Three Fundamental Theorems:**
  1. **Gradient Theorem:** $\int_{\mathbf{a}}^{\mathbf{b}} (\nabla T)\cdot d\mathbf{l} = T(\mathbf{b}) - T(\mathbf{a})$ *(path independent)*.
  2. **Divergence (Gauss's) Theorem:** $\int_{\mathcal{V}} (\nabla\cdot\mathbf{v})\,d\tau = \oint_{\mathcal{S}} \mathbf{v}\cdot d\mathbf{a}$.
  3. **Stokes' Theorem:** $\int_{\mathcal{S}} (\nabla\times\mathbf{v})\cdot d\mathbf{a} = \oint_{\mathcal{P}} \mathbf{v}\cdot d\mathbf{l}$.

---

## 2. Electrostatics & Dielectrics (`lect_14`–`lect_23`)

### 2.1 Core Laws & Potentials
- **Coulomb & Electric Field ($\epsilon_0 = 8.854\times 10^{-12}\text{ C}^2/(\text{N}\cdot\text{m}^2)$, $\frac{1}{4\pi\epsilon_0} \approx 9\times 10^9$):**
  $$\mathbf{E}(\mathbf{r}) = \frac{1}{4\pi\epsilon_0}\int \frac{dq}{\mathfrak{r}^2}\hat{\boldsymbol{\mathfrak{r}}}, \qquad \boldsymbol{\mathfrak{r}} = \mathbf{r} - \mathbf{r}' \quad (\text{separation vector from source } \mathbf{r}' \text{ to field } \mathbf{r})$$
  - Useful standard results: Infinite plane sheet $E = \frac{\sigma}{2\epsilon_0}$; Charged ring on axis $E_z = \frac{\lambda a z}{2\epsilon_0(a^2+z^2)^{3/2}}$; Disk of radius $R$: $E_z = \frac{\sigma}{2\epsilon_0}\left(1 - \frac{z}{\sqrt{z^2+R^2}}\right)$.
- **Gauss's Law:** $\oint_{\mathcal{S}}\mathbf{E}\cdot d\mathbf{a} = \frac{Q_{\text{enc}}}{\epsilon_0}$ and $\nabla\cdot\mathbf{E} = \frac{\rho}{\epsilon_0}$.
- **Electrostatic Potential ($V$):** $\nabla\times\mathbf{E}=\mathbf{0} \implies \mathbf{E} = -\nabla V$, $\ V(\mathbf{b}) - V(\mathbf{a}) = -\int_{\mathbf{a}}^{\mathbf{b}} \mathbf{E}\cdot d\mathbf{l}$.
  - **Poisson's & Laplace's Equations:** $\nabla^2 V = -\frac{\rho}{\epsilon}$; in charge-free regions ($\rho = 0$): **$\nabla^2 V = 0$** (parallel-plate $V(z) = \frac{z}{d}V_0$, coaxial $V(\rho) = V_0\frac{\ln(\rho/b)}{\ln(a/b)}$).
- **Electrostatic Energy:**
  $$W = \frac{1}{2}\sum_{i=1}^n q_i V(\mathbf{r}_i) = \frac{1}{2}\int \rho V\,d\tau = \frac{1}{2}\int \mathbf{D}\cdot\mathbf{E}\,d\tau = \frac{\epsilon}{2}\int E^2\,d\tau$$
  - Energy does **NOT** obey superposition ($W_{\text{tot}} = W_1 + W_2 + \epsilon_0\int\mathbf{E}_1\cdot\mathbf{E}_2\,d\tau$).
- **Electric Dipole ($\mathbf{p} = q\mathbf{d}$, from $-q$ to $+q$):**
  $$V(\mathbf{r}) = \frac{\mathbf{p}\cdot\hat{\mathbf{r}}}{4\pi\epsilon_0 r^2} = \frac{p\cos\theta}{4\pi\epsilon_0 r^2}, \qquad \mathbf{E}(\mathbf{r}) = \frac{p}{4\pi\epsilon_0 r^3}(2\cos\theta\,\hat{\mathbf{r}} + \sin\theta\,\hat{\boldsymbol{\theta}}) = \frac{3(\mathbf{p}\cdot\mathbf{r})\mathbf{r} - r^2\mathbf{p}}{4\pi\epsilon_0 r^5}$$
  - Torque on dipole in uniform $\mathbf{E}$: $\mathbf{N} = \mathbf{p}\times\mathbf{E}$.

### 2.2 Conductors, Dielectrics & Boundary Conditions
- **5 Golden Rules of Conductors in Electrostatic Equilibrium:**
  1. $\mathbf{E} = \mathbf{0}$ inside conductor.
  2. $\rho = 0$ inside conductor.
  3. Any net charge resides strictly on the **surface**.
  4. Entire conductor is an **equipotential**.
  5. Just outside conductor, $\mathbf{E}$ is perpendicular to surface ($\mathbf{E} = \frac{\sigma}{\epsilon_0}\hat{\mathbf{n}}$).
  - *Cavity rule:* Charge $q$ inside cavity induces $-q$ on inner cavity wall and leaves $+q$ on outer conductor surface.
- **Polarization $\mathbf{P}$ (Dipole Moment per Unit Volume):**
  $$\rho_b = -\nabla\cdot\mathbf{P}, \qquad \sigma_b = \mathbf{P}\cdot\hat{\mathbf{n}} \quad (\hat{\mathbf{n}} \text{ outward normal})$$
  - *Sanity check:* Total bound charge of an isolated polarized object MUST be zero: $\int \rho_b\,d\tau + \oint \sigma_b\,da = 0$!
- **Electric Displacement $\mathbf{D}$ & Linear Dielectrics:**
  $$\mathbf{D} \equiv \epsilon_0\mathbf{E} + \mathbf{P}, \qquad \nabla\cdot\mathbf{D} = \rho_f, \qquad \oint_{\mathcal{S}}\mathbf{D}\cdot d\mathbf{a} = Q_{f,\text{enc}}$$
  - Linear isotropic medium: $\mathbf{P} = \epsilon_0\chi_e\mathbf{E}$, $\mathbf{D} = \epsilon_0(1+\chi_e)\mathbf{E} = \epsilon_0\epsilon_r\mathbf{E} = \epsilon\mathbf{E}$.
- **Electrostatic Boundary Conditions (1 above, 2 below, $\hat{\mathbf{a}}_n$ points $2 \to 1$):**
  $$D_{1\perp} - D_{2\perp} = \rho_s \ (\sigma_f) \implies \epsilon_1 E_{1\perp} - \epsilon_2 E_{2\perp} = \rho_s, \qquad \mathbf{E}_{1\parallel} = \mathbf{E}_{2\parallel}$$
  *(Dielectric-dielectric with no free surface charge: $D_{1\perp} = D_{2\perp}$ and $E_{1\parallel} = E_{2\parallel}$!)*
- **Standard Capacitances ($C = Q/V$):**
  - Parallel plate: $C = \frac{\epsilon A}{d}$; Spherical concentric ($a < b$): $C = \frac{4\pi\epsilon ab}{b-a}$ (isolated sphere $C = 4\pi\epsilon a$); Coaxial ($a < b$): $\frac{C}{L} = \frac{2\pi\epsilon}{\ln(b/a)}$; Split-dielectric spherical shell (`lect_22` Prob 3): $C = C_1 + C_2 = 2\pi(\epsilon_1+\epsilon_2)\frac{ab}{b-a}$ (parallel combination!).

---

## 3. Magnetostatics & Magnetic Materials (`lect_24`–`lect_31`)

### 3.1 Lorentz Force, Currents & Continuity
- **Lorentz Force Law:** $\mathbf{F} = q(\mathbf{E} + \mathbf{v}\times\mathbf{B})$. Magnetic work $dW_{\text{mag}} = q(\mathbf{v}\times\mathbf{B})\cdot\mathbf{v}\,dt = 0$ (**magnetic fields do NO work**!).
- **Circular motion ($v\perp B$):** $qvB = \frac{mv^2}{R} \implies R = \frac{mv}{qB}$. **Crossed $\mathbf{E}\perp\mathbf{B}$:** $\mathbf{F}=0 \implies v = E/B$.
- **Currents:** $I = \lambda v$ (line), $\mathbf{K} = \sigma\mathbf{v}$ (surface current density), $\mathbf{J} = \rho\mathbf{v}$ (volume current density); $\mathbf{F}_{\text{mag}} = I\int d\mathbf{l}\times\mathbf{B}$.
- **Continuity Equation:** $\nabla\cdot\mathbf{J} = -\frac{\partial\rho}{\partial t}$. In magnetostatics (steady currents): $\nabla\cdot\mathbf{J} = 0$.

### 3.2 Biot-Savart, Ampere's Law & Vector Potential $\mathbf{A}$
- **Biot-Savart Law ($\mu_0 = 4\pi\times 10^{-7}\text{ N/A}^2$):** $\mathbf{B}(\mathbf{r}) = \frac{\mu_0 I}{4\pi}\int \frac{d\mathbf{l}'\times\hat{\boldsymbol{\mathfrak{r}}}}{\mathfrak{r}^2}$.
  - Straight segment: $B = \frac{\mu_0 I}{4\pi s}(\sin\theta_2 - \sin\theta_1)$; Infinite wire: $B = \frac{\mu_0 I}{2\pi s}$.
  - Force/length between parallel wires: $f = \frac{\mu_0 I_1 I_2}{2\pi d}$ (parallel **attract**, antiparallel **repel**).
  - Circular loop ($z$ on axis): $B(z) = \frac{\mu_0 I}{2}\frac{R^2}{(R^2+z^2)^{3/2}}$; Magnetic dipole $\mathbf{m} = N I A\,\hat{\mathbf{n}}$, torque $\mathbf{N} = \mathbf{m}\times\mathbf{B}$.
- **Ampère's Law:** $\oint\mathbf{B}\cdot d\mathbf{l} = \mu_0 I_{\text{enc}} \iff \nabla\times\mathbf{B} = \mu_0\mathbf{J}$ *(steady currents only!)*. Always $\nabla\cdot\mathbf{B} = 0$ (no magnetic monopoles).
  - Solenoid ($n$ turns/m): $B_{\text{in}} = \mu_0 n I$, $B_{\text{out}} = 0$.
- **Magnetic Vector Potential $\mathbf{A}$:** $\mathbf{B} = \nabla\times\mathbf{A}$, Coulomb gauge $\nabla\cdot\mathbf{A} = 0 \implies \nabla^2\mathbf{A} = -\mu_0\mathbf{J}$, $\Phi = \int_S\mathbf{B}\cdot d\mathbf{a} = \oint_C \mathbf{A}\cdot d\mathbf{l}$.

### 3.3 Magnetization $\mathbf{M}$, Auxiliary Field $\mathbf{H}$ & Bound Currents
- **Bound Currents:**
  $$\mathbf{J}_b = \nabla\times\mathbf{M}, \qquad \mathbf{K}_b = \mathbf{M}\times\hat{\mathbf{n}}$$
- **Total Current & $\mathbf{H}$:** $\mathbf{J} = \mathbf{J}_f + \mathbf{J}_b$, $\mathbf{H} \equiv \frac{1}{\mu_0}\mathbf{B} - \mathbf{M}$ (so $\mathbf{B} = \mu_0(\mathbf{H} + \mathbf{M})$):
  $$\nabla\times\mathbf{H} = \mathbf{J}_f \iff \oint \mathbf{H}\cdot d\mathbf{l} = I_{f,\text{enc}}$$
- **Linear Magnetic Media:** $\mathbf{M} = \chi_m\mathbf{H}$, $\mu = \mu_0(1+\chi_m) = \mu_0\mu_r$, $\mathbf{B} = \mu\mathbf{H}$ ($\chi_m < 0$ diamagnet, $\chi_m > 0$ mild paramagnet, $\mu_r \gg 1$ ferromagnet).
- **Magnetic Boundary Conditions:**
  $$B_{1\perp} = B_{2\perp}, \qquad \mathbf{H}_{1\parallel} - \mathbf{H}_{2\parallel} = \mathbf{K}_f \times \hat{\mathbf{n}} \quad (\text{or } B_{1\parallel} - B_{2\parallel} = \mu_0 K \text{ in vacuum})$$

---

## 4. Electrodynamics, Maxwell's Equations & EM Waves (`lect_32`–`lect_37`)

- **Faraday's Law & Lenz's Law:**
  $$\mathcal{E} = \oint \mathbf{E}\cdot d\mathbf{l} = -\frac{d\Phi}{dt}, \qquad \nabla\times\mathbf{E} = -\frac{\partial\mathbf{B}}{\partial t}$$
  - *Motional EMF:* $\mathcal{E} = \int (\mathbf{u}\times\mathbf{B})\cdot d\mathbf{l}$ (straight rod $e = BLu$, pivoted rod $e = \frac{1}{2}B\omega L^2$).
  - *Lenz Polarity Rule (`lect_36`):* Find $\mathbf{B}_{\text{in}}$ opposing the **change** in external flux $\Phi_{\text{ext}}$; use right-hand thumb along $\mathbf{B}_{\text{in}}$ to get induced current direction (which goes from `-` to `+` *inside* the source/loop to establish terminal polarity!).
- **Maxwell's Displacement Current & General Ampère's Law:**
  - Why $\nabla\times\mathbf{H} = \mathbf{J}$ fails when $\partial\rho/\partial t \ne 0$: $\nabla\cdot(\nabla\times\mathbf{H}) = 0$, whereas $\nabla\cdot\mathbf{J} = -\partial\rho/\partial t \ne 0$!
  - Fix: $\mathbf{J}_d = \frac{\partial\mathbf{D}}{\partial t} = \epsilon\frac{\partial\mathbf{E}}{\partial t}$ ($\mathbf{J}_c = \sigma\mathbf{E}$ is conduction current).
- **Complete Maxwell's Equations:**
  - **Free Space ($\epsilon_0, \mu_0$):**
    1. $\nabla\cdot\mathbf{E} = \frac{\rho}{\epsilon_0}$
    2. $\nabla\cdot\mathbf{B} = 0$
    3. $\nabla\times\mathbf{E} = -\frac{\partial\mathbf{B}}{\partial t}$
    4. $\nabla\times\mathbf{B} = \mu_0\mathbf{J} + \mu_0\epsilon_0\frac{\partial\mathbf{E}}{\partial t}$
  - **In Matter (Macroscopic):**
    1. $\nabla\cdot\mathbf{D} = \rho_f$
    2. $\nabla\cdot\mathbf{B} = 0$
    3. $\nabla\times\mathbf{E} = -\frac{\partial\mathbf{B}}{\partial t}$
    4. $\nabla\times\mathbf{H} = \mathbf{J}_f + \frac{\partial\mathbf{D}}{\partial t}$
- **Inductance & Magnetic Energy:** $N\Phi = L i$, $\mathcal{E} = -L\frac{di}{dt}$, Solenoid $L = \frac{\mu_0 N^2 \pi r^2}{l}$, $W_m = \frac{1}{2}LI^2 = \frac{1}{2\mu_0}\int B^2\,d\tau$.
- **Poynting Vector & Theorem (`lect_36`, `lect_37`):**
  $$\mathbf{S} = \mathbf{E}\times\mathbf{H} = \frac{1}{\mu_0}(\mathbf{E}\times\mathbf{B})\ [\text{W/m}^2], \qquad u = \frac{1}{2}\left(\epsilon_0 E^2 + \frac{1}{\mu_0}B^2\right)$$
  $$\frac{dW_{\text{mech}}}{dt} = -\frac{d}{dt}\int_{\mathcal{V}} u\,d\tau - \oint_{\mathcal{S}} \mathbf{S}\cdot d\mathbf{a} \quad \left(\text{or } \oint\mathbf{S}\cdot d\mathbf{a} + \int \mathbf{J}\cdot\mathbf{E}\,d\tau = -\frac{d}{dt}\int (w_m+w_e)\,d\tau\right)$$
- **EM Waves (`lect_37`):**
  - 1D Wave Equation: $\frac{\partial^2\psi}{\partial z^2} = \frac{1}{v^2}\frac{\partial^2\psi}{\partial t^2}$, $\psi(z,t) = f(z - vt)$ moves in $+z$.
  - Vacuum speed $c = \frac{1}{\sqrt{\mu_0\epsilon_0}} = 3\times 10^8\text{ m/s}$; in linear matter $v = \frac{1}{\sqrt{\mu\epsilon}} = \frac{c}{n}$, $n = \sqrt{\frac{\mu\epsilon}{\mu_0\epsilon_0}} \approx \sqrt{\epsilon_r}$.
  - Plane wave relations ($\hat{\mathbf{k}}$ propagation, $\hat{\mathbf{n}}$ polarization, $\hat{\mathbf{n}}\cdot\hat{\mathbf{k}}=0$):
    $$\mathbf{B}(\mathbf{r},t) = \frac{1}{v}E_0\cos(\mathbf{k}\cdot\mathbf{r} - \omega t + \delta)(\hat{\mathbf{k}}\times\hat{\mathbf{n}}), \qquad \frac{E}{H} = \sqrt{\frac{\mu_0}{\epsilon_0}} \approx 377\,\Omega, \qquad B_0 = \frac{E_0}{c}$$
  - Average intensity (Irradiance): $I = \langle S \rangle = \frac{1}{2}\epsilon_0 c E_0^2 = \frac{E_0 B_0}{2\mu_0}$.

---

## 5. Worked Past Exam & Assignment Solutions

### Part A: `PH1000` Midsem Exam (Dec 19, 2022) — All 8 Questions

**Q1 (`Midsem 2022`, 2m):** Given $\vec{u} = 10\hat{r} + 30\hat{\theta} - 10\hat{\phi}$ and $\vec{v} = -3\hat{r} - 10\hat{\theta} + 20\hat{\phi}$ at the same point $P$, find vector projection of $\vec{u}$ onto $\vec{v}$.  
**Solution:**
$$\vec{u}\cdot\vec{v} = 10(-3) + 30(-10) + (-10)(20) = -30 - 300 - 200 = -530$$
$$\|\vec{v}\|^2 = (-3)^2 + (-10)^2 + 20^2 = 9 + 100 + 400 = 509$$
$$\text{proj}_{\vec{v}}\vec{u} = \frac{\vec{u}\cdot\vec{v}}{\|\vec{v}\|^2}\vec{v} = -\frac{530}{509}(-3\hat{r} - 10\hat{\theta} + 20\hat{\phi}) \approx \mathbf{3.124\hat{r} + 10.413\hat{\theta} - 20.825\hat{\phi}}.$$

---

**Q2 (`Midsem 2022`, 4m — Vector Addition Trap):** $\vec{A} = 12\hat{r} + 5\hat{\theta} + \pi\hat{\phi}$ at $P(2,\pi,\pi/2)$, $\vec{B} = 2\hat{r} + 0.5\pi\hat{\theta}$ at $Q(5,\pi/2,\pi/2)$. Find $\vec{C} = \vec{A} + \vec{B}$.  
**Solution:**
Recall Cartesian transformation from spherical:
$$F_x = F_r\sin\theta\cos\phi + F_\theta\cos\theta\cos\phi - F_\phi\sin\phi$$
$$F_y = F_r\sin\theta\sin\phi + F_\theta\cos\theta\sin\phi + F_\phi\cos\phi, \qquad F_z = F_r\cos\theta - F_\theta\sin\theta$$
- **At $P(\theta=\pi, \phi=\pi/2)$:** $\sin\pi=0, \cos\pi=-1, \sin(\pi/2)=1, \cos(\pi/2)=0$:
  - $A_x = 0 + 0 - \pi(1) = -\pi$
  - $A_y = 0 + 5(-1)(1) + 0 = -5$
  - $A_z = 12(-1) - 0 = -12 \implies \vec{A} = -\pi\hat{x} - 5\hat{y} - 12\hat{z}$.
- **At $Q(\theta=\pi/2, \phi=\pi/2)$:** $\sin(\pi/2)=1, \cos(\pi/2)=0$:
  - $B_x = 0$, $B_y = 2(1)(1) = 2$, $B_z = -0.5\pi(1) = -0.5\pi \implies \vec{B} = 2\hat{y} - 0.5\pi\hat{z}$.
- **Sum:** $\vec{C} = \vec{A} + \vec{B} = \mathbf{-\pi\hat{x} - 3\hat{y} - (12 + 0.5\pi)\hat{z}}$.

---

**Q4 (`Midsem 2022`, 4m):** Express $P(r=8,\theta=\pi/6,\phi=\pi/3)$ and $\mathbf{A} = 2\hat{r} + \sqrt{3}\hat{\theta} - 2\hat{\phi}$ in cylindrical coordinates.  
**Solution:**
- Coordinates: $\rho = 8\sin(\pi/6) = \mathbf{4},\ \phi = \mathbf{\pi/3},\ z = 8\cos(\pi/6) = \mathbf{4\sqrt{3}}$.
- Vector components: $A_\rho = 2(\frac{1}{2}) + \sqrt{3}(\frac{\sqrt{3}}{2}) = 2.5$, $A_\phi = -2$, $A_z = 2(\frac{\sqrt{3}}{2}) - \sqrt{3}(\frac{1}{2}) = \frac{\sqrt{3}}{2}$.
  $$\mathbf{A} = \mathbf{2.5\hat{\rho} - 2\hat{\phi} + \frac{\sqrt{3}}{2}\hat{z}}.$$

---

**Q5 (`Midsem 2022`, 4m):** $T(x,y,z) = \frac{x^3}{4\sqrt{3}} + e^{-z} y^2$. Find rate of change at cylindrical $P(8, \pi/6, 6)$ toward origin.  
**Solution:**
- At $P$: $x = 8\cos(\pi/6) = 4\sqrt{3}$, $y = 8\sin(\pi/6) = 4$, $z = 6$.
- $\nabla T = \frac{3x^2}{4\sqrt{3}}\hat{x} + 2y e^{-z}\hat{y} - e^{-z}y^2\hat{z}$.
- At $P$: $x^2 = 48 \implies \frac{\partial T}{\partial x} = \frac{3(48)}{4\sqrt{3}} = \frac{36}{\sqrt{3}} = 12\sqrt{3}$; $\frac{\partial T}{\partial y} = 8 e^{-6}$; $\frac{\partial T}{\partial z} = -16 e^{-6}$.
- Direction from $P$ to origin: $\mathbf{d} = -P = \langle -4\sqrt{3}, -4, -6 \rangle$, $\|\mathbf{d}\| = \sqrt{48+16+36} = 10 \implies \hat{\mathbf{u}} = \langle -0.4\sqrt{3}, -0.4, -0.6 \rangle$.
- Directional derivative $= \nabla T\cdot\hat{\mathbf{u}} = (12\sqrt{3})(-0.4\sqrt{3}) + (8e^{-6})(-0.4) + (-16e^{-6})(-0.6) = -14.4 + 6.4 e^{-6} \approx \mathbf{-14.384}$.

---

**Q7 & Q8 (`Midsem 2022`, 6m + 6m):**  
- **Q7 (Divergence Theorem):** $\mathbf{v} = xy\hat{x} + 2yz\hat{y} + 3zx\hat{z}$ on box $[0,2]\times[0,2]\times[0,1]$:
  - Volume: $\nabla\cdot\mathbf{v} = y + 2z + 3x \implies \int_0^2\int_0^2\int_0^1 (3x+y+2z)\,dz\,dy\,dx = \mathbf{20}$.
  - Surface: $x=2$ gives $\int_0^2\int_0^1 2y\,dz\,dy = 4$; $y=2$ gives $\int_0^2\int_0^1 4z\,dz\,dx = 4$; $z=1$ gives $\int_0^2\int_0^2 3x\,dy\,dx = 12$; faces $x=0,y=0,z=0$ give $0 \implies 4+4+12 = \mathbf{20}$!
- **Q8 (Stokes' Theorem):** $\mathbf{F} = x^2 y\hat{x} + 2xy^2\hat{y}$ around unit square $[0,1]\times[0,1]$:
  - Curl: $\nabla\times\mathbf{F} = (2y^2 - x^2)\hat{z} \implies \int_0^1\int_0^1 (2y^2-x^2)\,dx\,dy = \frac{2}{3} - \frac{1}{3} = \mathbf{\frac{1}{3}}$.
  - Circulation: $0$ (bottom $y=0$) $+ \int_0^1 2y^2\,dy$ (right $x=1$) $+ \int_1^0 x^2\,dx$ (top $y=1$) $+ 0$ (left $x=0$) $= \frac{2}{3} - \frac{1}{3} = \mathbf{\frac{1}{3}}$!

---

### Part B: Key Assignment & Lecture Exam Problems

**P1 (`Assignment-1` Q4 — Polarized Sphere Bound Charges & Field):**  
A sphere of radius $R$ has $\mathbf{P}(\mathbf{r}) = k\mathbf{r}$. Find $\rho_b, \sigma_b$, and $\mathbf{E}$ inside and outside.  
**Solution:**
- $\rho_b = -\nabla\cdot(k\mathbf{r}) = -k\left(\frac{\partial x}{\partial x}+\frac{\partial y}{\partial y}+\frac{\partial z}{\partial z}\right) = \mathbf{-3k}$.
- $\sigma_b = \mathbf{P}(R)\cdot\hat{\mathbf{r}} = k R\,\hat{\mathbf{r}}\cdot\hat{\mathbf{r}} = \mathbf{kR}$.
- Notice total bound charge $= (-3k)\left(\frac{4}{3}\pi R^3\right) + (kR)(4\pi R^2) = 0$. Since $\rho_f = 0$, $\mathbf{D} = \mathbf{0}$ everywhere (symmetric)!
- Inside ($r < R$): $0 = \epsilon_0\mathbf{E} + \mathbf{P} \implies \mathbf{E}_{\text{in}} = -\frac{\mathbf{P}}{\epsilon_0} = \mathbf{-\frac{k\mathbf{r}}{\epsilon_0}}$. Outside ($r > R$): $\mathbf{P}=\mathbf{0} \implies \mathbf{E}_{\text{out}} = \mathbf{0}$.

---

**P2 (`Assignment-1` Q6 — Permittivity from Capacitor Data):**  
Find $\epsilon_r$ if: (a) $A=0.12\text{ m}^2, d=80\,\mu\text{m}, V_0=12\text{ V}, W=1\,\mu\text{J}$; (b) $u=100\text{ J/m}^3, V_0=200\text{ V}, d=45\,\mu\text{m}$; (c) $E=200\text{ kV/m}, \sigma=20\,\mu\text{C/m}^2$.  
**Solution:**
- **(a):** $W = \frac{1}{2}\frac{\epsilon_0\epsilon_r A}{d}V_0^2 \implies 10^{-6} = \frac{1}{2}\frac{8.854\times 10^{-12}\epsilon_r(0.12)}{80\times 10^{-6}}(144) \implies \epsilon_r \approx \mathbf{1.046}$.
- **(b):** $E = \frac{V_0}{d} = \frac{200}{45\times 10^{-6}} = 4.444\times 10^6\text{ V/m}$; $u = \frac{1}{2}\epsilon_0\epsilon_r E^2 \implies 100 = \frac{1}{2}(8.854\times 10^{-12})\epsilon_r(1.975\times 10^{13}) \implies \epsilon_r \approx \mathbf{1.143}$.
- **(c):** On conductor plate $D = \sigma = \epsilon_0\epsilon_r E \implies \epsilon_r = \frac{20\times 10^{-6}}{8.854\times 10^{-12} \times 2\times 10^5} \approx \mathbf{11.29}$.

---

**P3 (`Assignment-2` Q4 & `lect_31` — Magnetized Cylinder $\mathbf{M} = b r \hat{\mathbf{z}}$ & Coax with $\chi_m$):**  
An infinite cylinder of radius $R$ carries $\mathbf{M} = b s\,\hat{\mathbf{z}}$ ($s$ cylindrical radius) with no free current. Find $\mathbf{H}, \mathbf{J}_b, \mathbf{K}_b, \mathbf{B}_{\text{in}}, \mathbf{B}_{\text{out}}$.  
**Solution:**
- Cylindrical Curl: $\mathbf{J}_b = \nabla\times\mathbf{M} = -\frac{\partial M_z}{\partial s}\hat{\boldsymbol{\phi}} = \mathbf{-b\hat{\boldsymbol{\phi}}}$.
- Surface current: $\mathbf{K}_b = \mathbf{M}\times\hat{\mathbf{s}} = (b R\hat{\mathbf{z}})\times\hat{\mathbf{s}} = \mathbf{+b R\hat{\boldsymbol{\phi}}}$.
- No free current ($I_{f,\text{enc}}=0$): $\oint\mathbf{H}\cdot d\mathbf{l} = 0 \implies \mathbf{H} = \mathbf{0}$ everywhere!
- Inside ($s < R$): $\mathbf{B}_{\text{in}} = \mu_0(\mathbf{H}+\mathbf{M}) = \mathbf{\mu_0 b s\,\hat{\mathbf{z}}}$. Outside ($s > R$): $\mathbf{M}=\mathbf{0} \implies \mathbf{B}_{\text{out}} = \mathbf{0}$.

---

**P4 (`Assignment-2` Q5 & `lect_31` Prob 1 — Fat Wire Capacitor Gap):**  
A wire of radius $R = 2\text{ cm}$ carries steady current $I = 10\text{ A}$ uniformly across its cross-section. A narrow gap forms a parallel-plate capacitor. Find $B$ in the gap at $r = 1\text{ cm}$ from the axis.  
**Solution:**
Inside the gap, conduction current $I_{\text{enc}} = 0$, while changing $\mathbf{E}$ produces displacement current $\mathbf{J}_d = \epsilon_0 \frac{\partial\mathbf{E}}{\partial t}$ uniformly over radius $R$, whose total displacement current equals $I = 10\text{ A}$!  
Through a circular Amperian loop of radius $r = 1\text{ cm} < R$:
$$I_{d,\text{enc}} = I\frac{\pi r^2}{\pi R^2} = I\frac{r^2}{R^2}$$
By Ampère-Maxwell Law:
$$B(2\pi r) = \mu_0 I_{d,\text{enc}} = \mu_0 I\frac{r^2}{R^2} \implies B = \frac{\mu_0 I r}{2\pi R^2} = \frac{4\pi\times 10^{-7}\times 10 \times 0.01}{2\pi (0.02)^2} = \mathbf{5\times 10^{-5}\text{ T}\ (50\,\mu\text{T})}.$$

---

**P5 (`lect_34` Prob 1 & `lect_36` Prob 3 — Displacement Current & Poynting Vector):**  
(a) Material has $\sigma = 0.11\text{ S/m}, \epsilon_r = 1.2$, $\mathbf{E} = \cos(0.1t)\,\text{V/m}$. At $t = 5\text{ s}$, find $J_c$ and $J_d$.  
(b) In a lossless dielectric, $\mathbf{E} = E\cos(\omega t - kz)\hat{\mathbf{a}}_x$. Find $\mathbf{H}$, Poynting vector $\mathbf{S}$, and average power density $\langle S_z \rangle$.  
**Solution:**
- **(a):** At $t = 5\text{ s}$, $0.1t = 0.5\text{ rad}$:
  $$J_c = \sigma E = 0.11\cos(0.5) \approx \mathbf{0.0965\text{ A/m}^2}$$
  $$J_d = \epsilon_0\epsilon_r \frac{\partial E}{\partial t} = (8.854\times 10^{-12})(1.2)(-0.1\sin(0.5)) \approx \mathbf{-5.09\times 10^{-13}\text{ A/m}^2}$$
- **(b):** From $\frac{\partial\mathbf{B}}{\partial t} = -\nabla\times\mathbf{E} = -\frac{\partial E_x}{\partial z}\hat{\mathbf{a}}_y = -Ek\sin(\omega t - kz)\hat{\mathbf{a}}_y$:
  Integrating in $t$ and dividing by $\mu$: $\mathbf{H} = \frac{Ek}{\omega\mu}\cos(\omega t - kz)\hat{\mathbf{a}}_y$.
  Poynting vector: $\mathbf{S} = \mathbf{E}\times\mathbf{H} = \frac{k E^2}{\omega\mu}\cos^2(\omega t - kz)\hat{\mathbf{a}}_z\text{ W/m}^2$ ($+\hat{\mathbf{a}}_z$ direction).  
  Time average ($\langle \cos^2\rangle = 1/2$): $\langle S_z \rangle = \mathbf{\frac{k E^2}{2\omega\mu}\text{ W/m}^2}$.

---

**P6 (`lect_37` Slide 22 — Solar Irradiance & EM Wave Fields):**  
Planet receives $10\text{ cal}/(\text{m}^2\cdot\text{s})$ from the Sun ($1\text{ cal} = 4.184\text{ J}$). Find amplitudes $E_0$ and $B_0$.  
**Solution:**
Intensity $\langle S \rangle = 10 \times 4.184 = 41.84\text{ W/m}^2 = \frac{1}{2}\epsilon_0 c E_0^2$:
$$E_0 = \sqrt{\frac{2 \times 41.84}{(8.854\times 10^{-12})(3\times 10^8)}} = \sqrt{3.150\times 10^4} \approx \mathbf{177.5\text{ V/m}}, \qquad B_0 = \frac{E_0}{c} \approx \mathbf{5.92\times 10^{-7}\text{ T}}.$$

---

## 6. Common Mistakes Checklist

- [ ] **Adding vectors at DIFFERENT points in curvilinear coordinates:** Always convert to Cartesian $(\hat{\mathbf{x}},\hat{\mathbf{y}},\hat{\mathbf{z}})$ before adding (`Midsem 2022` Q2!).
- [ ] **Wrong $\hat{\mathbf{r}}$ vs $\boldsymbol{\mathfrak{r}}$ direction:** Separation vector ALWAYS points **from source charge/current ($\mathbf{r}'$) TO field point ($\mathbf{r}$)**: $\boldsymbol{\mathfrak{r}} = \mathbf{r} - \mathbf{r}'$.
- [ ] **Confusing $\sigma_b$ & $\rho_b$ signs:** $\rho_b = -\nabla\cdot\mathbf{P}$ (has a minus sign!), $\sigma_b = +\mathbf{P}\cdot\hat{\mathbf{n}}$ (no minus sign!). In magnetostatics, $\mathbf{J}_b = +\nabla\times\mathbf{M}$ and $\mathbf{K}_b = +\mathbf{M}\times\hat{\mathbf{n}}$ (note order!).
- [ ] **Electric vs Magnetic Boundary Conditions:** For electrostatics, **$E_\parallel$ is continuous** and **$D_\perp$ jumps by $\rho_f$**. For magnetostatics, **$B_\perp$ is continuous** and **$H_\parallel$ jumps by $\mathbf{K}_f\times\hat{\mathbf{n}}$**.
- [ ] **Factor of $1/2$ in Average Power Density:** $\langle S \rangle = \frac{1}{2}\text{Re}(\mathbf{E}\times\mathbf{H}^*) = \frac{1}{2}\epsilon_0 c E_0^2$, NOT $\epsilon_0 c E_0^2$!
- [ ] **Crossed $\sin$ vs $\cos$ Phase in EM Waves:** Make sure $\frac{\partial\mathbf{B}}{\partial t} = -\nabla\times\mathbf{E}$ matches the wave direction ($+\hat{\mathbf{k}}$ vs $-\hat{\mathbf{k}}$): $\hat{\mathbf{E}} \times \hat{\mathbf{B}}$ ALWAYS points along **direction of propagation**.
