# PH1000: Electromagnetics

> Assessment split from lect_2.pdf: Quiz 1 (15 marks), Quiz 2 (15 marks), 2 Assignments (2 x 10 = 20 marks), and End Semester (50 marks). Full marks depend on converting curvilinear vectors to Cartesian before adding at different points, including coordinate scale factors in $dl$, $dS$, and $d\tau$, and tracking minus signs in $\mathbf{E} = -\nabla V$, $\rho_b = -\nabla\cdot\mathbf{P}$, and $\mathcal{E} = -d\Phi/dt$.

## Syllabus Topics
- [ ] **Vectors, Dot/Cross Products & Vector Fields** (lect_2)
- [ ] **Cylindrical & Spherical Coordinate Transforms** (lect_3-6)
- [ ] **Differential Elements, Integrals & Del Calculus** (lect_6-10)
- [ ] **Divergence Theorem & Stokes' Theorem** (lect_10-13)
- [ ] **Coulomb's Law, Charge Distributions & Gauss's Law** (lect_14-16)
- [ ] **Electrostatic Potential, Work, Energy & Dipoles** (lect_15-17)
- [ ] **Conductors, Dielectrics, Polarization & Bound Charges** (lect_17-19)
- [ ] **Capacitors, Boundary Conditions & Laplace's Equation** (lect_19-23)
- [ ] **Lorentz Force, Currents, Biot-Savart & Ampere's Law** (lect_24-26)
- [ ] **Vector Potential A, Magnetization M & Auxiliary Field H** (lect_27-32)
- [ ] **Faraday's Law, Inductance & Displacement Current** (lect_31-35)
- [ ] **Maxwell's Equations, Poynting Theorem & EM Waves** (lect_35-37)

## 1. Vectors, Dot/Cross Products & Vector Fields
*lect_2.pdf*

**Plain Summary:** A vector field assigns a magnitude and direction to every point in space. Dot products measure alignment (projection), while cross and scalar triple products measure perpendicular area and 3D volume.

- **Cartesian basis:** Unit vectors $\hat{\mathbf{x}}, \hat{\mathbf{y}}, \hat{\mathbf{z}}$ are fixed everywhere, mutually orthogonal ($\hat{\mathbf{x}}\cdot\hat{\mathbf{y}}=0$), and right-handed ($\hat{\mathbf{x}}\times\hat{\mathbf{y}}=\hat{\mathbf{z}}$).
- **Dot product trap:** $\mathbf{P}\cdot\mathbf{Q} = \mathbf{P}\cdot\mathbf{M}$ only implies $\mathbf{P}\cdot(\mathbf{Q}-\mathbf{M})=0$, so either $\mathbf{Q}=\mathbf{M}$, $\mathbf{P}=\mathbf{0}$, or $\mathbf{P}\perp(\mathbf{Q}-\mathbf{M})$.
- **Cross & triple products:** $|\mathbf{A}\times\mathbf{B}| = AB\sin\theta$ gives the area of a parallelogram; $|\mathbf{A}\cdot(\mathbf{B}\times\mathbf{C})|$ gives the volume of the parallelepiped formed by $\mathbf{A}, \mathbf{B}, \mathbf{C}$.
- **Scalar vs vector fields:** Temperature $T(x,y,z)$ is a scalar field; $\mathbf{F}(x,y) = P\hat{\mathbf{i}} + Q\hat{\mathbf{j}}$ assigns a vector at each point $(x,y)$.

**Worked Example (lect_2.pdf Problem 1 & Problem 3):** Given $\mathbf{A} = 3\mathbf{a}_x + 2\mathbf{a}_y - \mathbf{a}_z$ and $\mathbf{B} = \mathbf{a}_x - 3\mathbf{a}_y + 2\mathbf{a}_z$, find $\mathbf{C} = 2\mathbf{A} - 3\mathbf{B}$, its unit vector $\mathbf{a}_c$, and the angle $\theta_z$ it makes with the $z$-axis.
1. Compute $\mathbf{C} = 2(3\mathbf{a}_x + 2\mathbf{a}_y - \mathbf{a}_z) - 3(\mathbf{a}_x - 3\mathbf{a}_y + 2\mathbf{a}_z) = 3\mathbf{a}_x + 13\mathbf{a}_y - 8\mathbf{a}_z$.
1. Find the magnitude: $C = \sqrt{3^2 + 13^2 + (-8)^2} = \sqrt{9 + 169 + 64} = \sqrt{242} \approx 15.556$.
1. Normalize to get the unit vector: $\mathbf{a}_c = \mathbf{C}/C \approx 0.193\mathbf{a}_x + 0.836\mathbf{a}_y - 0.514\mathbf{a}_z$.
1. Use the $z$-component for the angle: $\theta_z = \cos^{-1}(C_z / C) = \cos^{-1}(-8 / 15.556) \approx 120.95^\circ$.
**Answer:** $\mathbf{C} = 3\mathbf{a}_x + 13\mathbf{a}_y - 8\mathbf{a}_z$, $\mathbf{a}_c \approx 0.193\mathbf{a}_x + 0.836\mathbf{a}_y - 0.514\mathbf{a}_z$, $\theta_z \approx 120.95^\circ$.

**Key Formula:** $$\mathbf{A}\cdot\mathbf{B} = AB\cos\theta, \quad \hat{\mathbf{n}} = \frac{\hat{\mathbf{a}}\times\hat{\mathbf{b}}}{\sin\theta}, \quad V = \mathbf{A}\cdot(\mathbf{B}\times\mathbf{C}) = \det\begin{bmatrix}A_x & A_y & A_z\\ B_x & B_y & B_z\\ C_x & C_y & C_z\end{bmatrix}$$

**Common Mistake:** Never cancel $\mathbf{P}$ in $\mathbf{P}\cdot\mathbf{Q} = \mathbf{P}\cdot\mathbf{M}$ to conclude $\mathbf{Q}=\mathbf{M}$; $\mathbf{P}$ may simply be perpendicular to $\mathbf{Q}-\mathbf{M}$.

---

## 2. Cylindrical & Spherical Coordinate Transforms
*lect_3.pdf - lect_6.pdf*

**Plain Summary:** Cylindrical $(\rho, \phi, z)$ and spherical $(r, \theta, \phi)$ coordinates match circular or spherical symmetry, but their unit vectors rotate as you move from one point to another.

- **Cylindrical transform:** $A_x = A_\rho\cos\phi - A_\phi\sin\phi$, $A_y = A_\rho\sin\phi + A_\phi\cos\phi$, $A_z = A_z$. Inverse: $A_\rho = A_x\cos\phi + A_y\sin\phi$, $A_\phi = -A_x\sin\phi + A_y\cos\phi$.
- **Spherical transform:** $\hat{\mathbf{r}} = \sin\theta\cos\phi\,\hat{\mathbf{x}} + \sin\theta\sin\phi\,\hat{\mathbf{y}} + \cos\theta\,\hat{\mathbf{z}}$, $\hat{\boldsymbol{\theta}} = \cos\theta\cos\phi\,\hat{\mathbf{x}} + \cos\theta\sin\phi\,\hat{\mathbf{y}} - \sin\theta\,\hat{\mathbf{z}}$, $\hat{\boldsymbol{\phi}} = -\sin\phi\,\hat{\mathbf{x}} + \cos\phi\,\hat{\mathbf{y}}$.
- **Position vector:** In cylindrical coordinates $\mathbf{r} = \rho\hat{\boldsymbol{\rho}} + z\hat{\mathbf{z}}$ (note $A_\phi = 0$); in spherical coordinates $\mathbf{r} = r\hat{\mathbf{r}}$.
- **Common-point rule:** Vectors at the *same* point $P$ can be added, dotted, or crossed directly in cylindrical or spherical components; vectors at *different* points must first be converted to Cartesian.

| System | Coordinates & Ranges | Relation to Cartesian $(x,y,z)$ | Right-Handed Basis |
| --- | --- | --- | --- |
| Cylindrical | $\rho \ge 0,\; 0 \le \phi < 2\pi,\; z \in \mathbb{R}$ | $x=\rho\cos\phi,\; y=\rho\sin\phi,\; z=z$ | $\hat{\boldsymbol{\rho}}\times\hat{\boldsymbol{\phi}}=\hat{\mathbf{z}}$ |
| Spherical | $r \ge 0,\; 0 \le \theta \le \pi,\; 0 \le \phi < 2\pi$ | $x=r\sin\theta\cos\phi,\; y=r\sin\theta\sin\phi,\; z=r\cos\theta$ | $\hat{\mathbf{r}}\times\hat{\boldsymbol{\theta}}=\hat{\boldsymbol{\phi}}$ |

**Worked Example (lect_5.pdf Problem 3 (corrected from slide annotation)):** If $\mathbf{A} = 3\mathbf{a}_\rho + 2\mathbf{a}_\phi + 5\mathbf{a}_z$ at $P(3, \pi/6, 5)$ and $\mathbf{B} = -2\mathbf{a}_\rho + 3\mathbf{a}_\phi - \mathbf{a}_z$ at $Q(4, \pi/3, 3)$, find $\mathbf{C} = \mathbf{A} - \mathbf{B}$ at $S(2, \pi/4, 4)$.
1. Convert $\mathbf{A}$ at $\phi = 30^\circ$ to Cartesian: $A_x = 3\cos 30^\circ - 2\sin 30^\circ = 1.598$, $A_y = 3\sin 30^\circ + 2\cos 30^\circ = 3.232$, $A_z = 5$.
1. Convert $\mathbf{B}$ at $\phi = 60^\circ$ to Cartesian: $B_x = -2\cos 60^\circ - 3\sin 60^\circ = -3.598$, $B_y = -2\sin 60^\circ + 3\cos 60^\circ = -0.232$, $B_z = -1$.
1. Subtract in Cartesian (note lect_5.pdf flags the screenshot's $\mathbf{C}=-2\mathbf{a}_x+3\mathbf{a}_y+4\mathbf{a}_z$ as incorrect): $\mathbf{C} = \mathbf{A}-\mathbf{B} = 5.196\mathbf{a}_x + 3.464\mathbf{a}_y + 6\mathbf{a}_z$.
1. Transform $\mathbf{C}$ to cylindrical components at $S$ ($\phi = 45^\circ$): $C_\rho = 5.196\cos 45^\circ + 3.464\sin 45^\circ = 6.124$, $C_\phi = -5.196\sin 45^\circ + 3.464\cos 45^\circ = -1.225$, $C_z = 6$.
**Answer:** $\mathbf{C} = 6.124\mathbf{a}_\rho - 1.225\mathbf{a}_\phi + 6\mathbf{a}_z$ (Cartesian: $5.196\mathbf{a}_x + 3.464\mathbf{a}_y + 6\mathbf{a}_z$).

**Key Formula:** $$\begin{bmatrix}A_x\\A_y\\A_z\end{bmatrix} = \begin{bmatrix}\cos\phi & -\sin\phi & 0\\ \sin\phi & \cos\phi & 0\\ 0 & 0 & 1\end{bmatrix}\begin{bmatrix}A_\rho\\A_\phi\\A_z\end{bmatrix}, \quad \begin{bmatrix}A_r\\A_\theta\\A_\phi\end{bmatrix} = \begin{bmatrix}\sin\theta\cos\phi & \sin\theta\sin\phi & \cos\theta\\ \cos\theta\cos\phi & \cos\theta\sin\phi & -\sin\theta\\ -\sin\phi & \cos\phi & 0\end{bmatrix}\begin{bmatrix}A_x\\A_y\\A_z\end{bmatrix}$$

**Common Mistake:** Do NOT add or subtract cylindrical/spherical vectors defined at different points directly, and do NOT pull $\hat{\mathbf{r}}$ or $\hat{\boldsymbol{\rho}}$ outside an integral—convert to Cartesian first (lect_8.pdf Problem-2).

---

## 3. Differential Elements, Integrals & Del Calculus
*lect_6.pdf - lect_10.pdf*

**Plain Summary:** Differential length, surface, and volume elements track how far a step moves in curved coordinates. The del operator $\nabla$ produces the steepest-ascent vector (gradient), outward flux density (divergence), and local swirl (curl).

- **Gradient $\nabla T$:** Vector pointing in the direction of maximum increase of scalar $T(x,y,z)$, with $dT = \nabla T\cdot d\mathbf{l}$. A unit normal to surface $f(x,y,z)=c$ is $\hat{\mathbf{n}} = \nabla f / |\nabla f|$ (lect_10.pdf).
- **Fundamental theorem for gradients:** $\int_{\mathbf{a}}^{\mathbf{b}} (\nabla T)\cdot d\mathbf{l} = T(\mathbf{b}) - T(\mathbf{a})$ is path-independent, and $\oint (\nabla T)\cdot d\mathbf{l} = 0$.
- **Divergence $\nabla\cdot\mathbf{v}$:** A scalar measuring outward flux per unit volume (source if $>0$, sink if $<0$, solenoidal if $=0$).
- **Curl $\nabla\times\mathbf{v}$:** A vector measuring circulation per unit area; $\nabla\times\mathbf{v} = \mathbf{0}$ everywhere defines an irrotational (conservative) field.

| Coordinate | Displacement $d\mathbf{l}$ | Surface Elements $d\mathbf{s}$ | Volume $d\tau$ |
| --- | --- | --- | --- |
| Cartesian | $dx\hat{\mathbf{x}} + dy\hat{\mathbf{y}} + dz\hat{\mathbf{z}}$ | $dy\,dz\hat{\mathbf{x}},\; dx\,dz\hat{\mathbf{y}},\; dx\,dy\hat{\mathbf{z}}$ | $dx\,dy\,dz$ |
| Cylindrical | $d\rho\hat{\boldsymbol{\rho}} + \rho\,d\phi\hat{\boldsymbol{\phi}} + dz\hat{\mathbf{z}}$ | $\rho\,d\phi\,dz\hat{\boldsymbol{\rho}},\; d\rho\,dz\hat{\boldsymbol{\phi}},\; \rho\,d\rho\,d\phi\hat{\mathbf{z}}$ | $\rho\,d\rho\,d\phi\,dz$ |
| Spherical | $dr\hat{\mathbf{r}} + r\,d\theta\hat{\boldsymbol{\theta}} + r\sin\theta\,d\phi\hat{\boldsymbol{\phi}}$ | $r^2\sin\theta\,d\theta\,d\phi\hat{\mathbf{r}},\; r\sin\theta\,dr\,d\phi\hat{\boldsymbol{\theta}},\; r\,dr\,d\theta\hat{\boldsymbol{\phi}}$ | $r^2\sin\theta\,dr\,d\theta\,d\phi$ |

**Worked Example (lect_8.pdf Problem-3 (Example 2.16)):** The electron density inside a sphere of radius $2\text{ m}$ is $n_e = (1000/r)\cos(\phi/4)\text{ electrons/m}^3$. Find the total charge enclosed ($e = -1.6\times 10^{-19}\text{ C}$).
1. Use the spherical volume element $dv = r^2\sin\theta\,dr\,d\theta\,d\phi$ over $r\in[0,2]$, $\theta\in[0,\pi]$, $\phi\in[0,2\pi]$.
1. Integrate: $N = \int_0^2 \frac{1000}{r} r^2\,dr \int_0^\pi \sin\theta\,d\theta \int_0^{2\pi} \cos(\phi/4)\,d\phi$.
1. Evaluate each factor: $\int_0^2 1000r\,dr = 2000$, $\int_0^\pi \sin\theta\,d\theta = 2$, $\int_0^{2\pi}\cos(\phi/4)\,d\phi = [4\sin(\phi/4)]_0^{2\pi} = 4$.
1. Multiply: $N = 2000 \times 2 \times 4 = 16000$ electrons, so $Q = 16000 \times (-1.6\times 10^{-19}) = -2.56\times 10^{-15}\text{ C}$.
**Answer:** $N = 16000$ electrons; $Q = -2.56\times 10^{-15}\text{ C}$.

**Key Formula:** $$\nabla T = \frac{\partial T}{\partial x}\hat{\mathbf{x}} + \frac{\partial T}{\partial y}\hat{\mathbf{y}} + \frac{\partial T}{\partial z}\hat{\mathbf{z}}, \quad \nabla\cdot\mathbf{v} = \frac{\partial v_x}{\partial x} + \frac{\partial v_y}{\partial y} + \frac{\partial v_z}{\partial z}, \quad \nabla\times\mathbf{v} = \begin{vmatrix}\hat{\mathbf{x}} & \hat{\mathbf{y}} & \hat{\mathbf{z}}\\ \partial_x & \partial_y & \partial_z\\ v_x & v_y & v_z\end{vmatrix}$$

**Common Mistake:** Omitting $\rho$ in cylindrical $d\tau = \rho\,d\rho\,d\phi\,dz$ or $r^2\sin\theta$ in spherical $d\tau = r^2\sin\theta\,dr\,d\theta\,d\phi$ ruins every integral.

---

## 4. Divergence Theorem & Stokes' Theorem
*lect_10.pdf - lect_12_13.pdf*

**Plain Summary:** The divergence theorem trades a 3D volume integral of $\nabla\cdot\mathbf{v}$ for a closed 2D surface flux, while Stokes' theorem trades a 2D surface flux of $\nabla\times\mathbf{v}$ for a closed 1D boundary loop integral.

- **Divergence (Gauss's) theorem:** $\int_\mathcal{V} (\nabla\cdot\mathbf{v})\,d\tau = \oint_\mathcal{S} \mathbf{v}\cdot d\mathbf{a}$, where $d\mathbf{a}$ points outward from the closed surface $\mathcal{S}$.
- **Stokes' theorem:** $\int_\mathcal{S} (\nabla\times\mathbf{v})\cdot d\mathbf{a} = \oint_\mathcal{P} \mathbf{v}\cdot d\mathbf{l}$, with $d\mathbf{a}$ and the perimeter direction $d\mathbf{l}$ linked by the right-hand rule.
- **Curvilinear divergence:** In cylindrical, $\nabla\cdot\mathbf{F} = \frac{1}{\rho}\partial_\rho(\rho F_\rho) + \frac{1}{\rho}\partial_\phi F_\phi + \partial_z F_z$; in spherical, $\nabla\cdot\mathbf{F} = \frac{1}{r^2}\partial_r(r^2 F_r) + \frac{1}{r\sin\theta}\partial_\theta(\sin\theta F_\theta) + \frac{1}{r\sin\theta}\partial_\phi F_\phi$.
- **Rotational vs irrotational:** If $\oint \mathbf{v}\cdot d\mathbf{l} \ne 0$ around a closed loop, $\nabla\times\mathbf{v} \ne \mathbf{0}$ (rotational); if $\nabla\times\mathbf{v} = \mathbf{0}$, the field is conservative.

**Worked Example (lect_12_13.pdf Problem 4):** Verify Stokes' theorem for $\mathbf{F} = -2xy^2\hat{\mathbf{x}}$ on the square in the $xy$-plane with vertices $P(1,1)$, $Q(2,1)$, $R(2,2)$, $S(1,2)$ traversed counterclockwise.
1. Compute the curl: $\nabla\times\mathbf{F} = -\frac{\partial(-2xy^2)}{\partial y}\hat{\mathbf{z}} = 4xy\hat{\mathbf{z}}$.
1. Evaluate the surface integral over $x\in[1,2],\; y\in[1,2]$ with $d\mathbf{S} = dx\,dy\hat{\mathbf{z}}$: $\int_1^2\int_1^2 4xy\,dx\,dy = 4\left[\frac{x^2}{2}\right]_1^2\left[\frac{y^2}{2}\right]_1^2 = 4(3/2)(3/2) = 9$.
1. Evaluate the closed line integral $\oint \mathbf{F}\cdot d\mathbf{l} = -\int 2xy^2\,dx$: along $QR$ and $SP$, $dx=0$ so both contribute $0$.
1. Along $PQ$ ($y=1$, $x:1\to 2$): $-\int_1^2 2x(1)^2\,dx = -3$. Along $RS$ ($y=2$, $x:2\to 1$): $-\int_2^1 2x(4)\,dx = +12$. Total: $-3 + 0 + 12 + 0 = 9$.
**Answer:** Both $\int_\mathcal{S}(\nabla\times\mathbf{F})\cdot d\mathbf{S}$ and $\oint\mathbf{F}\cdot d\mathbf{l}$ equal $9$.

**Key Formula:** $$\int_{\mathcal{V}} (\nabla\cdot\mathbf{v})\,d\tau = \oint_{\mathcal{S}} \mathbf{v}\cdot d\mathbf{a}, \qquad \int_{\mathcal{S}} (\nabla\times\mathbf{v})\cdot d\mathbf{a} = \oint_{\mathcal{P}} \mathbf{v}\cdot d\mathbf{l}$$

**Common Mistake:** In Divergence theorem face-by-face checks (lect_10.pdf Problem-3), remember opposite faces have opposite outward normals ($+\hat{\mathbf{y}}$ at $y=1$ vs $-\hat{\mathbf{y}}$ at $y=0$) and different coordinate values.

---

## 5. Coulomb's Law, Charge Distributions & Gauss's Law
*lect_14.pdf - lect_16.pdf, Assignment-1*

**Plain Summary:** Electric field is force per unit test charge. When charge distributions have spherical, cylindrical, or planar symmetry, Gauss's law gives $\mathbf{E}$ immediately from the enclosed charge $Q_{\text{enc}}$.

- **Coulomb & superposition:** $\mathbf{E}(\mathbf{r}) = \frac{1}{4\pi\epsilon_0}\sum_i \frac{q_i}{\mathscr{r}_i^2}\hat{\boldsymbol{\mathscr{r}}}_i$, where $\boldsymbol{\mathscr{r}}_i = \mathbf{r} - \mathbf{r}'_i$ points from source to field point.
- **Continuous sources:** Replace $dq$ with $\lambda\,dl'$ (line), $\sigma\,da'$ (surface), or $\rho\,d\tau'$ (volume) and integrate over the primed source coordinates.
- **Gauss's law (integral & differential):** $\oint \mathbf{E}\cdot d\mathbf{a} = Q_{\text{enc}}/\epsilon_0$ and $\nabla\cdot\mathbf{E} = \rho/\epsilon_0$. Outside any spherically symmetric charge $Q$, $\mathbf{E}$ is identical to a point charge $Q$ at the center.
- **Infinite plane sheet:** Using a Gaussian pillbox straddling a plane of uniform surface charge $\sigma$, flux leaves both sides ($2A|\mathbf{E}| = \sigma A/\epsilon_0$), giving $E = \sigma/(2\epsilon_0)$ away from the sheet (lect_19.pdf).

**Worked Example (Assignment-1.pdf Q1):** Find the electric field a distance $z$ above the center of a flat circular disk of radius $R$ carrying uniform surface charge $\sigma$. Check the limits $R\to\infty$ and $z\gg R$.
1. Break the disk into concentric rings of radius $r'$ and width $dr'$, carrying charge $dq = \sigma(2\pi r'\,dr')$.
1. By symmetry, horizontal field components cancel; each ring contributes $dE_z = \frac{1}{4\pi\epsilon_0}\frac{dq\,\cos\alpha}{r'^2+z^2} = \frac{\sigma}{2\epsilon_0}\frac{z\,r'\,dr'}{(r'^2+z^2)^{3/2}}$.
1. Integrate from $r'=0$ to $R$: $E_z = \frac{\sigma z}{2\epsilon_0}\left[-\frac{1}{\sqrt{r'^2+z^2}}\right]_0^R = \frac{\sigma}{2\epsilon_0}\left(1 - \frac{z}{\sqrt{R^2+z^2}}\right)$ (for $z>0$).
1. Limits: as $R\to\infty$, $z/\sqrt{R^2+z^2}\to 0$ so $E_z \to \frac{\sigma}{2\epsilon_0}$ (infinite sheet). For $z\gg R$, $\frac{z}{\sqrt{R^2+z^2}} = (1+R^2/z^2)^{-1/2} \approx 1 - \frac{R^2}{2z^2}$, giving $E_z \approx \frac{\sigma\pi R^2}{4\pi\epsilon_0 z^2} = \frac{Q}{4\pi\epsilon_0 z^2}$ (point charge).
**Answer:** $\mathbf{E} = \frac{\sigma}{2\epsilon_0}\left(1 - \frac{z}{\sqrt{R^2+z^2}}\right)\hat{\mathbf{z}}$ ($z>0$); limits $\frac{\sigma}{2\epsilon_0}$ ($R\to\infty$) and $\frac{Q}{4\pi\epsilon_0 z^2}$ ($z\gg R$).

**Key Formula:** $$\mathbf{E}(\mathbf{r}) = \frac{1}{4\pi\epsilon_0}\int \frac{\hat{\boldsymbol{\mathscr{r}}}}{\mathscr{r}^2}\,dq, \qquad \oint_{\mathcal{S}} \mathbf{E}\cdot d\mathbf{a} = \frac{Q_{\text{enc}}}{\epsilon_0}, \qquad \nabla\cdot\mathbf{E} = \frac{\rho}{\epsilon_0}$$

**Common Mistake:** Always draw $\boldsymbol{\mathscr{r}} = \mathbf{r} - \mathbf{r}'$ from the *source* charge to the *field* point, and do not forget the factor of $2$ in $E = \sigma/(2\epsilon_0)$ for a single infinite plane.

---

## 6. Electrostatic Potential, Work, Energy & Dipoles
*lect_15.pdf - lect_17.pdf, Assignment-1*

**Plain Summary:** Because an electrostatic field has zero curl, it can be derived from a single scalar potential $V$. Storing charges costs work against their mutual repulsion, and this energy resides in the electric field.

- **Conservative $\mathbf{E}$ & potential:** $\nabla\times\mathbf{E} = \mathbf{0}$ lets us write $\mathbf{E} = -\nabla V$ and $V(\mathbf{b}) - V(\mathbf{a}) = -\int_{\mathbf{a}}^{\mathbf{b}} \mathbf{E}\cdot d\mathbf{l}$.
- **Poisson & Laplace:** Combining $\nabla\cdot\mathbf{E} = \rho/\epsilon_0$ with $\mathbf{E} = -\nabla V$ gives $\nabla^2 V = -\rho/\epsilon_0$ (Poisson), or $\nabla^2 V = 0$ where $\rho=0$ (Laplace).
- **Electrostatic energy:** $W = \frac{1}{2}\sum q_i V_i = \frac{1}{2}\int \rho V\,d\tau = \frac{\epsilon_0}{2}\int_{\text{all space}} E^2\,d\tau$. Energy is quadratic in $\mathbf{E}$, so **it does NOT obey superposition** ($W_{\text{tot}} = W_1 + W_2 + \epsilon_0\int \mathbf{E}_1\cdot\mathbf{E}_2\,d\tau$, lect_17.pdf).
- **Electric dipole ($r\gg d$):** $\mathbf{p} = q\mathbf{d}$ (from $-q$ to $+q$), $V = \frac{\mathbf{p}\cdot\hat{\mathbf{r}}}{4\pi\epsilon_0 r^2}$, and $\mathbf{E} = \frac{3(\mathbf{p}\cdot\mathbf{r})\mathbf{r} - r^2\mathbf{p}}{4\pi\epsilon_0 r^5} = \frac{p}{4\pi\epsilon_0 r^3}(2\cos\theta\,\mathbf{a}_r + \sin\theta\,\mathbf{a}_\theta)$.

**Worked Example (Assignment-1.pdf Q2):** Consider a sphere of radius $R$ containing a charge $Q$ uniformly distributed throughout its volume. Calculate the work done to assemble these charges.
1. With uniform density $\rho = \frac{Q}{\frac{4}{3}\pi R^3}$, Gauss's law gives $\mathbf{E}(r) = \frac{Qr}{4\pi\epsilon_0 R^3}\hat{\mathbf{r}}$ for $r < R$ and $\mathbf{E}(r) = \frac{Q}{4\pi\epsilon_0 r^2}\hat{\mathbf{r}}$ for $r > R$.
1. Integrate the field energy density $w_e = \frac{\epsilon_0}{2}E^2$ over all space ($d\tau = 4\pi r^2\,dr$).
1. Inside ($0 < r < R$): $W_{\text{in}} = \frac{\epsilon_0}{2}\int_0^R \left(\frac{Qr}{4\pi\epsilon_0 R^3}\right)^2 4\pi r^2\,dr = \frac{Q^2}{8\pi\epsilon_0 R^6}\int_0^R r^4\,dr = \frac{Q^2}{40\pi\epsilon_0 R}$.
1. Outside ($r > R$): $W_{\text{out}} = \frac{\epsilon_0}{2}\int_R^\infty \left(\frac{Q}{4\pi\epsilon_0 r^2}\right)^2 4\pi r^2\,dr = \frac{Q^2}{8\pi\epsilon_0 R}$. Total: $W = \frac{Q^2}{40\pi\epsilon_0 R} + \frac{Q^2}{8\pi\epsilon_0 R} = \frac{3Q^2}{20\pi\epsilon_0 R}$.
**Answer:** $W = \frac{3Q^2}{20\pi\epsilon_0 R}$ (contrast with $\frac{Q^2}{8\pi\epsilon_0 R}$ for a hollow spherical shell in lect_17.pdf).

**Key Formula:** $$\mathbf{E} = -\nabla V, \quad \nabla^2 V = -\frac{\rho}{\epsilon_0}, \quad W = \frac{\epsilon_0}{2}\int_{\text{all space}} E^2\,d\tau, \quad V_{\text{dip}} = \frac{\mathbf{p}\cdot\hat{\mathbf{r}}}{4\pi\epsilon_0 r^2}$$

**Common Mistake:** Never add electrostatic energies directly ($W_{\text{tot}} \ne W_1 + W_2$); always find the total $\mathbf{E} = \mathbf{E}_1 + \mathbf{E}_2$ first, and remember the minus sign in $\mathbf{E} = -\nabla V$.

---

## 7. Conductors, Dielectrics, Polarization & Bound Charges
*lect_17.pdf - lect_19.pdf, Assignment-1*

**Plain Summary:** Free charges in a conductor move until the interior field vanishes, whereas bound charges in a dielectric only shift slightly inside atoms, creating polarization $\mathbf{P}$ and effective bound charges $\rho_b$ and $\sigma_b$.

- **Conductors in equilibrium:** $\mathbf{E}=\mathbf{0}$ and $\rho=0$ inside; any net charge sits on the surface; the conductor is an equipotential; $\mathbf{E}$ just outside is normal to the surface.
- **Cavities (lect_18.pdf):** Placing $+q$ inside a hollow cavity induces $-q$ on the cavity's inner wall (so $\oint \mathbf{E}\cdot d\mathbf{a}=0$ in the metal) and $+q$ on the outer surface of an isolated neutral conductor.
- **Polarization & bound charges:** Polarization $\mathbf{P}$ is dipole moment per unit volume (for a single atom $\mathbf{p} = \alpha\mathbf{E}$; torque on a dipole $\mathbf{N} = \mathbf{p}\times\mathbf{E}$). A polarized object produces the same field as volume bound charge $\rho_b = -\nabla\cdot\mathbf{P}$ and surface bound charge $\sigma_b = \mathbf{P}\cdot\hat{\mathbf{n}}$.
- **Electric displacement $\mathbf{D}$:** $\mathbf{D} = \epsilon_0\mathbf{E} + \mathbf{P}$ obeys $\nabla\cdot\mathbf{D} = \rho_f$ and $\oint \mathbf{D}\cdot d\mathbf{a} = Q_{f,\text{enc}}$. For linear media, $\mathbf{P} = \epsilon_0\chi_e\mathbf{E}$ and $\mathbf{D} = \epsilon_0(1+\chi_e)\mathbf{E} = \epsilon_0\epsilon_r\mathbf{E} = \epsilon\mathbf{E}$.

**Worked Example (Assignment-1.pdf Q4):** A sphere of radius $R$ carries a polarization $\mathbf{P}(\mathbf{r}) = k\mathbf{r}$, where $k$ is a constant and $\mathbf{r}$ is the vector from the center. Calculate the bound charges and find the electric field inside and outside the sphere.
1. Volume bound charge: in Cartesian $\mathbf{P} = k(x\hat{\mathbf{x}} + y\hat{\mathbf{y}} + z\hat{\mathbf{z}})$, so $\rho_b = -\nabla\cdot\mathbf{P} = -(k + k + k) = -3k$.
1. Surface bound charge at $r=R$ (outward normal $\hat{\mathbf{n}} = \hat{\mathbf{r}}$): $\sigma_b = \mathbf{P}(R)\cdot\hat{\mathbf{r}} = kR$.
1. Inside ($r < R$): enclosed bound charge is $Q_{b,\text{enc}} = (-3k)\left(\frac{4}{3}\pi r^3\right) = -4\pi k r^3$. Gauss's law gives $E(4\pi r^2) = \frac{-4\pi k r^3}{\epsilon_0} \implies \mathbf{E}_{\text{in}} = -\frac{k\mathbf{r}}{\epsilon_0} = -\frac{\mathbf{P}}{\epsilon_0}$.
1. Outside ($r > R$): total bound charge is $Q_{\text{tot}} = (-3k)\left(\frac{4}{3}\pi R^3\right) + (kR)(4\pi R^2) = 0$, so $\mathbf{E}_{\text{out}} = \mathbf{0}$ (equivalently $\rho_f = 0 \implies \mathbf{D} = \mathbf{0}$ everywhere).
**Answer:** $\rho_b = -3k$, $\sigma_b = kR$; $\mathbf{E}_{\text{in}} = -\frac{k\mathbf{r}}{\epsilon_0}$, $\mathbf{E}_{\text{out}} = \mathbf{0}$.

**Key Formula:** $$\rho_b = -\nabla\cdot\mathbf{P}, \quad \sigma_b = \mathbf{P}\cdot\hat{\mathbf{n}}, \quad \mathbf{D} = \epsilon_0\mathbf{E} + \mathbf{P} = \epsilon\mathbf{E}, \quad \nabla\cdot\mathbf{D} = \rho_f, \quad \epsilon_r = 1 + \chi_e$$

**Common Mistake:** Do NOT drop the minus sign in $\rho_b = -\nabla\cdot\mathbf{P}$, and remember $\nabla\cdot\mathbf{P}$ in spherical coordinates is $\frac{1}{r^2}\frac{\partial(r^2 P_r)}{\partial r}$, NOT $\frac{\partial P_r}{\partial r}$.

---

## 8. Capacitors, Boundary Conditions & Laplace's Equation
*lect_19.pdf - lect_23.pdf, Assignment-1*

**Plain Summary:** At any interface, tangential $\mathbf{E}$ is continuous while normal $\mathbf{D}$ jumps by the free surface charge $\rho_s$. Solving $\nabla^2 V = 0$ with plate potentials gives $V$, $\mathbf{E}$, and capacitance $C = Q/V_0$.

- **Dielectric-dielectric boundary (lect_20-21):** Using a loop and pillbox at an interface with normal $\mathbf{a}_n$ (from medium 2 to 1), $\mathbf{E}_{t1} = \mathbf{E}_{t2}$ and $D_{n1} - D_{n2} = \rho_s$ (so $\epsilon_1 E_{n1} = \epsilon_2 E_{n2}$ when $\rho_s=0$).
- **Conductor-dielectric boundary (lect_21.pdf):** Inside a conductor $\mathbf{D}_2 = \mathbf{0}$, so $E_{t1} = 0$ and $D_{n1} = \epsilon_1 E_{n1} = \rho_s$.
- **Energy in dielectrics & capacitors:** $w_e = \frac{1}{2}\mathbf{D}\cdot\mathbf{E} = \frac{1}{2}\epsilon E^2 = \frac{D^2}{2\epsilon}$ and $W = \frac{1}{2}CV^2 = \frac{Q^2}{2C}$.
- **Split-dielectric sphere (lect_22.pdf):** Two hemispherical dielectrics $\epsilon_1, \epsilon_2$ between $r=a$ and $r=b$ share the same $V$ and have tangential $E_{r1}=E_{r2}$, so they act in parallel: $C = 2\pi(\epsilon_1+\epsilon_2)\frac{ab}{b-a} = C_1 + C_2$.

| Capacitor Geometry | Potential $V$ (from $\nabla^2 V = 0$) | Capacitance |
| --- | --- | --- |
| Parallel plates (area $A$, gap $d$) | $V(z) = \frac{z}{d}V_0$ | $C = \frac{\epsilon A}{d}$ |
| Coaxial cylinders (radii $a < b$) | $V(\rho) = V_0\frac{\ln(\rho/b)}{\ln(a/b)}$ | $C/L = \frac{2\pi\epsilon}{\ln(b/a)}$ |
| Concentric spheres (radii $a < b$) | $V(r) = V_0\frac{1/r - 1/b}{1/a - 1/b}$ | $C = \frac{4\pi\epsilon ab}{b-a}$ (isolated: $4\pi\epsilon a$) |

**Worked Example (lect_21.pdf Problem-1):** The plane $z=0$ marks the boundary between free space ($z<0$, medium 2) and a dielectric with $\epsilon_r = 40$ ($z>0$, medium 1). If $\mathbf{E}_2 = 13\mathbf{a}_x + 40\mathbf{a}_y + 50\mathbf{a}_z\text{ V/m}$ next to the interface, find $\mathbf{E}_1$ on the other side.
1. The normal unit vector to $z=0$ is $\mathbf{a}_n = \mathbf{a}_z$, so $x$ and $y$ are tangential components.
1. Tangential $\mathbf{E}$ is continuous: $E_{x1} = E_{x2} = 13\text{ V/m}$ and $E_{y1} = E_{y2} = 40\text{ V/m}$.
1. With no free surface charge ($\rho_s = 0$), normal $\mathbf{D}$ is continuous: $\epsilon_1 E_{z1} = \epsilon_2 E_{z2}$.
1. Substitute $\epsilon_2 = \epsilon_0$ and $\epsilon_1 = 40\epsilon_0$: $E_{z1} = \frac{50}{40} = 1.25\text{ V/m}$.
**Answer:** $\mathbf{E}_1 = 13\mathbf{a}_x + 40\mathbf{a}_y + 1.25\mathbf{a}_z\text{ V/m}$.

**Key Formula:** $$\mathbf{E}_{t1} = \mathbf{E}_{t2}, \quad D_{n1} - D_{n2} = \rho_s, \quad w_e = \frac{1}{2}\epsilon E^2 = \frac{1}{2}\mathbf{D}\cdot\mathbf{E}, \quad C = \frac{\epsilon A}{d}$$

**Common Mistake:** At a dielectric interface with $\rho_s = 0$, it is $D_n = \epsilon E_n$ (NOT $E_n$) that is continuous, whereas $E_t$ (NOT $D_t$) is continuous.

---

## 9. Lorentz Force, Currents, Biot-Savart & Ampere's Law
*lect_24.pdf - lect_26.pdf*

**Plain Summary:** Moving charges feel a magnetic force perpendicular to their velocity, so magnetic forces bend paths without doing work. Steady currents generate curled magnetic fields governed by Biot-Savart and Ampere's law.

- **Lorentz force & zero work:** $\mathbf{F} = Q[\mathbf{E} + (\mathbf{v}\times\mathbf{B})]$ ($1\text{ T} = 10^4\text{ Gauss}$). Since $dW = Q(\mathbf{v}\times\mathbf{B})\cdot\mathbf{v}\,dt = 0$, magnetic forces never change a particle's speed; in uniform $\mathbf{B}\perp\mathbf{v}$, radius $R = mv/(qB)$.
- **Currents & continuity:** Line $I = \lambda v$, volume $\mathbf{J} = \rho\mathbf{v}$, magnetic force $\mathbf{F}_{\text{mag}} = \int I(d\mathbf{l}\times\mathbf{B})$. Charge conservation gives $\nabla\cdot\mathbf{J} = -\partial\rho/\partial t$, which reduces to $\nabla\cdot\mathbf{J} = 0$ for steady currents.
- **Biot-Savart law:** $\mathbf{B}(\mathbf{r}) = \frac{\mu_0 I}{4\pi}\int \frac{d\mathbf{l}'\times\hat{\boldsymbol{\mathscr{r}}}}{\mathscr{r}^2}$. For a straight segment at perpendicular distance $s$, $B = \frac{\mu_0 I}{4\pi s}(\sin\theta_2 - \sin\theta_1)$; infinite wire $B = \frac{\mu_0 I}{2\pi s}$ (parallel wires attract with force/length $f = \frac{\mu_0 I_1 I_2}{2\pi d}$).
- **Loop, dipole & Ampere:** On a loop's axis $B(z) = \frac{\mu_0 I R^2}{2(R^2+z^2)^{3/2}}$; dipole moment $\mathbf{m} = I\pi R^2\mathbf{a}_z$ (torque $\mathbf{m}\times\mathbf{B}$). Globally $\nabla\cdot\mathbf{B} = 0$ ($\oint\mathbf{B}\cdot d\mathbf{s}=0$) and $\oint\mathbf{B}\cdot d\mathbf{l} = \mu_0 I_{\text{enc}}$ ($\nabla\times\mathbf{B} = \mu_0\mathbf{J}$).

**Worked Example (lect_26.pdf Problem-3):** Find the net magnetic force on a square loop of side $a$ carrying steady current $I$, placed coplanar at distance $s$ from an infinite straight wire carrying steady current $I$ in the same sense on the near side.
1. The two sides of length $a$ perpendicular to the infinite wire experience equal and opposite forces, so they cancel.
1. Near side (distance $s$, parallel currents): attractive force $F_1 = \left(\frac{\mu_0 I}{2\pi s}\right) I a = \frac{\mu_0 I^2 a}{2\pi s}$ toward the wire.
1. Far side (distance $s+a$, antiparallel currents): repulsive force $F_2 = \frac{\mu_0 I^2 a}{2\pi(s+a)}$ away from the wire.
1. Since $1/s > 1/(s+a)$, net force is toward the wire: $F = F_1 - F_2 = \frac{\mu_0 I^2 a}{2\pi}\left(\frac{1}{s} - \frac{1}{s+a}\right) = \frac{\mu_0 I^2 a^2}{2\pi s(s+a)}$.
**Answer:** $F = \frac{\mu_0 I^2 a^2}{2\pi s(s+a)}$ directed toward the infinite wire (attractive).

**Key Formula:** $$\mathbf{F} = Q(\mathbf{E} + \mathbf{v}\times\mathbf{B}), \quad B_{\text{seg}} = \frac{\mu_0 I}{4\pi s}(\sin\theta_2 - \sin\theta_1), \quad \oint \mathbf{B}\cdot d\mathbf{l} = \mu_0 I_{\text{enc}}, \quad \nabla\cdot\mathbf{B} = 0$$

**Common Mistake:** Wait before concluding $\nabla\times\mathbf{H}=\mathbf{0}$ for an infinite thin wire (Assignment-2 Q1(ii)): $H_\phi = I/(2\pi s)$ has zero curl for $s>0$, but at $s=0$ the current is singular ($\mathbf{J} = I\,\delta(x)\delta(y)\hat{\mathbf{z}}$), matching Stokes' theorem $\oint\mathbf{H}\cdot d\mathbf{l} = I$.

---

## 10. Vector Potential A, Magnetization M & Auxiliary Field H
*lect_27.pdf - lect_32.pdf, Assignment-2*

**Plain Summary:** Because $\nabla\cdot\mathbf{B}=0$, magnetic fields derive from a vector potential $\mathbf{A}$ ($\mathbf{B}=\nabla\times\mathbf{A}$). Magnetized matter acts like bound currents $\mathbf{J}_b$ and $\mathbf{K}_b$, while $\mathbf{H}$ responds solely to free currents.

- **Vector potential $\mathbf{A}$:** $\mathbf{B} = \nabla\times\mathbf{A}$ and magnetic flux $\Phi = \int_S \mathbf{B}\cdot d\mathbf{s} = \oint_C \mathbf{A}\cdot d\mathbf{l}$. In the Coulomb gauge $\nabla\cdot\mathbf{A} = 0$, $\nabla^2\mathbf{A} = -\mu_0\mathbf{J}$ so $\mathbf{A}(\mathbf{r}) = \frac{\mu_0}{4\pi}\int \frac{\mathbf{J}(\mathbf{r}')}{\mathscr{r}}\,d\tau'$.
- **Magnetization $\mathbf{M}$ & bound currents:** $\mathbf{M}$ is magnetic dipole moment per unit volume ($\mathbf{m}/V$). A magnetized object produces the field of volume bound current $\mathbf{J}_b = \nabla\times\mathbf{M}$ and surface bound current $\mathbf{K}_b = \mathbf{M}\times\hat{\mathbf{n}}$.
- **Auxiliary field $\mathbf{H}$:** $\mathbf{H} \equiv \frac{1}{\mu_0}\mathbf{B} - \mathbf{M}$ (so $\mathbf{B} = \mu_0(\mathbf{H}+\mathbf{M})$) satisfies $\nabla\times\mathbf{H} = \mathbf{J}_f$ and $\oint\mathbf{H}\cdot d\mathbf{l} = I_{f,\text{enc}}$.
- **Linear media & boundary conditions:** $\mathbf{M} = \chi_m\mathbf{H}$ ($\chi_m>0$ paramagnet, $\chi_m<0$ diamagnet) and $\mathbf{B} = \mu\mathbf{H}$ with $\mu = \mu_0(1+\chi_m)$. At an interface with surface current $\mathbf{K}$: $B_\perp^{\text{above}} = B_\perp^{\text{below}}$ and $B_\parallel^{\text{above}} - B_\parallel^{\text{below}} = \mu_0 K$ (lect_32.pdf).

**Worked Example (Assignment-2.pdf Q2(a) & Q2(b)):** Find the magnetic vector potential $\mathbf{A}$ at distance $r$ outside an infinite straight wire carrying steady current $I$, verify $\nabla\cdot\mathbf{A}=0$ and $\nabla\times\mathbf{A}=\mathbf{B}$, and find $\mathbf{A}$ inside the wire (radius $R$, uniform current).
1. Outside ($r > R$): $\mathbf{B} = \frac{\mu_0 I}{2\pi r}\hat{\boldsymbol{\phi}}$. Since $\mathbf{J} = J\hat{\mathbf{z}}$, take $\mathbf{A} = A_z(r)\hat{\mathbf{z}}$; then $\nabla\times\mathbf{A} = -\frac{dA_z}{dr}\hat{\boldsymbol{\phi}} = \frac{\mu_0 I}{2\pi r}\hat{\boldsymbol{\phi}}$.
1. Integrate with reference $r_0$ (or $r_0=R$): $A_z(r) = -\frac{\mu_0 I}{2\pi}\ln\left(\frac{r}{r_0}\right)$, so $\mathbf{A}_{\text{out}} = -\frac{\mu_0 I}{2\pi}\ln\left(\frac{r}{R}\right)\hat{\mathbf{z}}$ (matching $A_z(R)=0$).
1. Check divergence & curl: $\nabla\cdot\mathbf{A} = \frac{\partial A_z}{\partial z} = 0$ (since $A_z$ depends only on $r$), and $\nabla\times\mathbf{A} = -\frac{\partial A_z}{\partial r}\hat{\boldsymbol{\phi}} = \frac{\mu_0 I}{2\pi r}\hat{\boldsymbol{\phi}} = \mathbf{B}$.
1. Inside ($r < R$): $\mathbf{B} = \frac{\mu_0 I r}{2\pi R^2}\hat{\boldsymbol{\phi}}$, so $-\frac{dA_z}{dr} = \frac{\mu_0 I r}{2\pi R^2} \implies \mathbf{A}_{\text{in}} = \frac{\mu_0 I}{4\pi R^2}(R^2 - r^2)\hat{\mathbf{z}}$ (continuous at $r=R$).
**Answer:** $\mathbf{A}_{\text{out}} = -\frac{\mu_0 I}{2\pi}\ln(r/R)\hat{\mathbf{z}}$; $\mathbf{A}_{\text{in}} = \frac{\mu_0 I}{4\pi R^2}(R^2 - r^2)\hat{\mathbf{z}}$ (up to an additive constant), with $\nabla\cdot\mathbf{A}=0$ and $\nabla\times\mathbf{A}=\mathbf{B}$.

**Key Formula:** $$\mathbf{B} = \nabla\times\mathbf{A}, \quad \mathbf{J}_b = \nabla\times\mathbf{M}, \quad \mathbf{K}_b = \mathbf{M}\times\hat{\mathbf{n}}, \quad \mathbf{H} = \frac{\mathbf{B}}{\mu_0} - \mathbf{M}, \quad \oint\mathbf{H}\cdot d\mathbf{l} = I_{f,\text{enc}}$$

**Common Mistake:** Do NOT set $\mathbf{H}=\mathbf{0}$ everywhere just because $I_{f,\text{enc}}=0$ without checking symmetry, and remember $\mathbf{K}_b = \mathbf{M}\times\hat{\mathbf{n}}$ uses the *outward* unit normal $\hat{\mathbf{n}}$ from the magnetized material.

---

## 11. Faraday's Law, Inductance & Displacement Current
*lect_31.pdf - lect_35.pdf, Assignment-2*

**Plain Summary:** Changing magnetic flux induces an electric field (Faraday's law), while changing electric flux acts as Maxwell's displacement current to generate a magnetic field even across an open capacitor gap.

- **Faraday's & Lenz's law:** $\mathcal{E} = \oint \mathbf{E}\cdot d\mathbf{l} = -\frac{d\Phi}{dt}$ ($-N\frac{d\Phi}{dt}$ for $N$ turns), or $\nabla\times\mathbf{E} = -\frac{\partial\mathbf{B}}{\partial t}$ (non-conservative!). Induced current creates $\mathbf{B}_{\text{in}}$ opposing the change in $\Phi_{\text{ext}}$.
- **Motional EMF (lect_32-33):** Moving a conductor at velocity $\mathbf{u}$ in $\mathbf{B}$ creates $\mathbf{E}_m = \mathbf{u}\times\mathbf{B}$ and $e = \int_c (\mathbf{u}\times\mathbf{B})\cdot d\mathbf{l}_c$ (reduces to $BLu$ for a straight bar, or $\frac{1}{2}B\omega L^2$ for a pivoted rotating rod).
- **Inductance & magnetic energy (lect_35):** Self-inductance $L = \frac{N\Phi}{I}$ (solenoid: $L = \frac{\mu_0 N^2\pi r^2}{l}$, per unit length $L/l = \mu_0\pi n^2 b^2$); mutual EMF $\mathcal{E}_2 = -M\frac{dI_1}{dt}$. Energy $W = \frac{1}{2}LI^2 = \frac{1}{2\mu_0}\int B^2\,d\tau$.
- **Displacement current (lect_34):** Because $\nabla\cdot(\nabla\times\mathbf{H}) = 0$ would fail when $\partial\rho_v/\partial t \ne 0$, Maxwell added $\mathbf{J}_d = \frac{\partial\mathbf{D}}{\partial t} = \epsilon_0\epsilon_r\frac{\partial\mathbf{E}}{\partial t}$, giving $\nabla\times\mathbf{H} = \mathbf{J}_c + \frac{\partial\mathbf{D}}{\partial t}$ with $\mathbf{J}_c = \sigma\mathbf{E}$.

**Worked Example (Assignment-2.pdf Q5 (also lect_31.pdf Problem-1)):** A fat wire of radius $a$ carries a constant current $I$ uniformly distributed over its cross section. A narrow gap of width $w\ll a$ forms a parallel-plate capacitor. Find $\mathbf{B}$ inside the gap at distance $s < a$ from the axis.
1. In the gap there is no conduction current ($\mathbf{J}=\mathbf{0}$), but charge accumulates on the faces at rate $dQ/dt = I$, giving uniform surface charge density $\sigma(t) = Q(t)/(\pi a^2)$.
1. Neglecting fringing ($w\ll a$), the electric field in the gap is $E(t) = \frac{\sigma(t)}{\epsilon_0} = \frac{Q(t)}{\pi a^2\epsilon_0}$, so the displacement current density is $J_d = \epsilon_0\frac{\partial E}{\partial t} = \frac{1}{\pi a^2}\frac{dQ}{dt} = \frac{I}{\pi a^2}$.
1. Apply Ampere-Maxwell law to a circular loop of radius $s < a$ in the gap: $\oint\mathbf{B}\cdot d\mathbf{l} = \mu_0 I_{d,\text{enc}}$.
1. Since $I_{d,\text{enc}} = J_d (\pi s^2) = I\frac{s^2}{a^2}$, we get $B(2\pi s) = \mu_0 I\frac{s^2}{a^2} \implies \mathbf{B} = \frac{\mu_0 I s}{2\pi a^2}\hat{\boldsymbol{\phi}}$ (for $s=1\text{ cm}, a=2\text{ cm}, I=10\text{ A}$, $B = 5\times 10^{-5}\text{ T}$).
**Answer:** $\mathbf{B}(s) = \frac{\mu_0 I s}{2\pi a^2}\hat{\boldsymbol{\phi}}$ inside the gap for $s < a$.

**Key Formula:** $$\mathcal{E} = -\frac{d\Phi}{dt}, \quad \nabla\times\mathbf{E} = -\frac{\partial\mathbf{B}}{\partial t}, \quad \nabla\times\mathbf{H} = \mathbf{J}_c + \frac{\partial\mathbf{D}}{\partial t}, \quad L = \frac{\mu_0 N^2\pi r^2}{l}, \quad W_m = \frac{1}{2}LI^2$$

**Common Mistake:** Inside a capacitor gap there is zero conduction current ($\mathbf{J}_c=\mathbf{0}$); the magnetic field there comes entirely from Maxwell's displacement current $\mathbf{J}_d = \partial\mathbf{D}/\partial t$.

---

## 12. Maxwell's Equations, Poynting Theorem & EM Waves
*lect_35.pdf - lect_37.pdf, PH1001*

**Plain Summary:** Coupling Faraday's law with Ampere-Maxwell's displacement current creates self-sustaining transverse electromagnetic waves traveling at $v = 1/\sqrt{\mu\epsilon}$, carrying energy flux $\mathbf{S} = \mathbf{E}\times\mathbf{H}$.

- **Poynting theorem (lect_36-37):** $\mathbf{S} = \mathbf{E}\times\mathbf{H}$ ($\text{W/m}^2$) is instantaneous power density flowing out per unit area; $\oint \mathbf{S}\cdot d\mathbf{s} + \int \mathbf{J}\cdot\mathbf{E}\,dv = -\frac{d}{dt}\int (w_m + w_e)\,dv$ with $w_e = \frac{1}{2}\epsilon E^2$ and $w_m = \frac{1}{2}\mu H^2$.
- **Plane EM waves in vacuum (lect_37):** $\nabla^2\mathbf{E} = \mu_0\epsilon_0\partial_t^2\mathbf{E}$ gives $c = 1/\sqrt{\mu_0\epsilon_0} = 3.00\times 10^8\text{ m/s}$. For $\mathbf{E} = E_0\cos(\mathbf{k}\cdot\mathbf{r}-\omega t+\delta)\hat{\mathbf{n}}$ ($\hat{\mathbf{n}}\cdot\hat{\mathbf{k}}=0$), $\mathbf{B} = \frac{1}{c}E_0\cos(\mathbf{k}\cdot\mathbf{r}-\omega t+\delta)(\hat{\mathbf{k}}\times\hat{\mathbf{n}})$ and $E/H = \sqrt{\mu_0/\epsilon_0}$.
- **EM waves in linear matter (lect_37):** Speed drops to $v = 1/\sqrt{\epsilon\mu} = c/n$ with refractive index $n = \sqrt{\epsilon\mu/(\epsilon_0\mu_0)} \cong \sqrt{\epsilon_r}$. With no free charges/currents, $\epsilon_1 E_1^\perp = \epsilon_2 E_2^\perp$, $B_1^\perp = B_2^\perp$, $\mathbf{E}_1^\parallel = \mathbf{E}_2^\parallel$, and $\frac{1}{\mu_1}\mathbf{B}_1^\parallel = \frac{1}{\mu_2}\mathbf{B}_2^\parallel$.
- **PH1001 Optical Fiber Lab:** Attenuation $\alpha$ and bending losses in optical fibers are measured using $950\text{ nm}$ (SFH 450V) and $660\text{ nm}$ (SFH 756V) LEDs across different fiber lengths and bend radii.

| Law | Vacuum (Differential) | Matter (Differential) | Integral Form (Matter) |
| --- | --- | --- | --- |
| Gauss (E) | $\nabla\cdot\mathbf{E} = \rho/\epsilon_0$ | $\nabla\cdot\mathbf{D} = \rho_f$ | $\oint_\mathcal{S}\mathbf{D}\cdot d\mathbf{a} = Q_{f,\text{enc}}$ |
| Gauss (B) | $\nabla\cdot\mathbf{B} = 0$ | $\nabla\cdot\mathbf{B} = 0$ | $\oint_\mathcal{S}\mathbf{B}\cdot d\mathbf{a} = 0$ |
| Faraday | $\nabla\times\mathbf{E} = -\partial_t\mathbf{B}$ | $\nabla\times\mathbf{E} = -\partial_t\mathbf{B}$ | $\oint_\mathcal{P}\mathbf{E}\cdot d\mathbf{l} = -\frac{d}{dt}\int_\mathcal{S}\mathbf{B}\cdot d\mathbf{a}$ |
| Ampere-Maxwell | $\nabla\times\mathbf{B} = \mu_0\mathbf{J} + \mu_0\epsilon_0\partial_t\mathbf{E}$ | $\nabla\times\mathbf{H} = \mathbf{J}_f + \partial_t\mathbf{D}$ | $\oint_\mathcal{P}\mathbf{H}\cdot d\mathbf{l} = I_{f,\text{enc}} + \frac{d}{dt}\int_\mathcal{S}\mathbf{D}\cdot d\mathbf{a}$ |

**Worked Example (lect_36.pdf Problem-3 & Solution-2):** In a lossless dielectric, $\mathbf{E} = E\cos(\omega t - kz)\mathbf{a}_x\text{ V/m}$. Determine (a) the magnetic field intensity $\mathbf{H}$, (b) the direction of power flow, and (c) the time-averaged power density.
1. Apply Faraday's law: $\frac{\partial\mathbf{B}}{\partial t} = -\nabla\times\mathbf{E} = -\frac{\partial E_x}{\partial z}\mathbf{a}_y = -Ek\sin(\omega t - kz)\mathbf{a}_y$.
1. Integrate with respect to $t$: $B_y = \frac{Ek}{\omega}\cos(\omega t - kz)\text{ T}$, so $\mathbf{H} = \frac{\mathbf{B}}{\mu} = \frac{Ek}{\omega\mu}\cos(\omega t - kz)\mathbf{a}_y\text{ A/m}$.
1. Compute the Poynting vector: $\mathbf{S} = \mathbf{E}\times\mathbf{H} = \frac{k}{\omega\mu}E^2\cos^2(\omega t - kz)(\mathbf{a}_x\times\mathbf{a}_y) = \frac{k}{\omega\mu}E^2\cos^2(\omega t - kz)\mathbf{a}_z\text{ W/m}^2$ (power flows along $+\mathbf{a}_z$).
1. Time-average over one period $T$ using $\langle\cos^2(\omega t - kz)\rangle = 1/2$: $\langle S_z\rangle = \frac{k}{2\omega\mu}E^2\text{ W/m}^2$.
**Answer:** (a) $\mathbf{H} = \frac{Ek}{\omega\mu}\cos(\omega t - kz)\mathbf{a}_y\text{ A/m}$; (b) $+z$ direction; (c) $\langle S_z\rangle = \frac{kE^2}{2\omega\mu}\text{ W/m}^2$.

**Key Formula:** $$\mathbf{S} = \mathbf{E}\times\mathbf{H}, \quad c = \frac{1}{\sqrt{\mu_0\epsilon_0}}, \quad \frac{E_0}{B_0} = c, \quad \frac{E}{H} = \sqrt{\frac{\mu_0}{\epsilon_0}}, \quad v = \frac{1}{\sqrt{\epsilon\mu}} = \frac{c}{n}, \quad n \cong \sqrt{\epsilon_r}$$

**Common Mistake:** In $\mathbf{E} = E_0\sin(\omega t - ky)\hat{\mathbf{z}}$ (lect_37.pdf), propagation is along $+\hat{\mathbf{y}}$; always use $\hat{\mathbf{k}}\times\hat{\mathbf{n}}$ (here $\hat{\mathbf{y}}\times\hat{\mathbf{z}} = +\hat{\mathbf{x}}$) for the direction of $\mathbf{B}$ so that $\mathbf{E}\times\mathbf{B}$ points along $+\hat{\mathbf{k}}$.

---

## Practice Questions (22)
### Q1. lect_2.pdf Problem 3 (Assignment / Tutorial)
Calculate the volume of a parallelepiped formed by $\mathbf{A} = 2\mathbf{a}_x + \mathbf{a}_y - 2\mathbf{a}_z$, $\mathbf{B} = -\mathbf{a}_x + 3\mathbf{a}_y + 5\mathbf{a}_z$, and $\mathbf{C} = 5\mathbf{a}_x - 2\mathbf{a}_y - 2\mathbf{a}_z$.
- **Hint:** Evaluate the scalar triple product $\mathbf{A}\cdot(\mathbf{B}\times\mathbf{C})$ as a $3\times 3$ determinant.
- **Solution:** $V = \det\begin{bmatrix}2 & 1 & -2\\ -1 & 3 & 5\\ 5 & -2 & -2\end{bmatrix} = 2(-6+10) - 1(2-25) - 2(2-15) = 8 + 23 + 26 = 57$.

### Q2. lect_5.pdf Problem 2 (Assignment / Tutorial)
Express the vector $\mathbf{A} = \frac{k}{\rho^2}\mathbf{a}_\rho + 5\sin(2\phi)\mathbf{a}_z$ in the rectangular (Cartesian) coordinate system.
- **Hint:** Use $A_x = A_\rho\cos\phi - A_\phi\sin\phi$, $A_y = A_\rho\sin\phi + A_\phi\cos\phi$, and $\cos\phi = x/\rho$, $\sin\phi = y/\rho$, $\rho = \sqrt{x^2+y^2}$.
- **Solution:** Here $A_\rho = k/\rho^2$, $A_\phi = 0$, $A_z = 5\sin(2\phi) = 10\sin\phi\cos\phi$. Thus $A_x = \frac{k\cos\phi}{\rho^2} = \frac{kx}{(x^2+y^2)^{3/2}}$, $A_y = \frac{k\sin\phi}{\rho^2} = \frac{ky}{(x^2+y^2)^{3/2}}$, and $A_z = \frac{10xy}{x^2+y^2}$.

### Q3. lect_7.pdf Example 1.7 (Assignment / Tutorial)
Calculate the surface integral of $\mathbf{v} = 2xz\hat{\mathbf{x}} + (x+2)\hat{\mathbf{y}} + y(z^2-3)\hat{\mathbf{z}}$ over five sides (excluding the bottom $z=0$) of the cubical box of side $2$ in the first octant ($0\le x,y,z\le 2$), with outward/upward positive.
- **Hint:** Integrate separately over (i) $x=2$, (ii) $x=0$, (iii) $y=2$, (iv) $y=0$, and (v) $z=2$ with outward $d\mathbf{a}$.
- **Solution:** (i) $x=2$: $\int_0^2\int_0^2 4z\,dy\,dz = 16$. (ii) $x=0$: $0$. (iii) $y=2$: $\int_0^2\int_0^2 (x+2)\,dx\,dz = 12$. (iv) $y=0$: $-\int_0^2\int_0^2 (x+2)\,dx\,dz = -12$. (v) $z=2$: $\int_0^2\int_0^2 y(4-3)\,dx\,dy = 4$. Total flux $= 16 + 0 + 12 - 12 + 4 = 20$.

### Q4. lect_10.pdf Slide 5-6 (Quiz / Lab)
Find a unit vector normal to the surface $x^3 + y^3 + 3xyz = 3$ at the point $(1, 2, -1)$.
- **Hint:** Let $f(x,y,z) = x^3 + y^3 + 3xyz - 3$ and compute $\hat{\mathbf{n}} = \nabla f / |\nabla f|$ at $(1,2,-1)$.
- **Solution:** $\nabla f = (3x^2+3yz)\hat{\mathbf{x}} + (3y^2+3xz)\hat{\mathbf{y}} + 3xy\hat{\mathbf{z}}$. At $(1,2,-1)$: $\nabla f = (3-6)\hat{\mathbf{x}} + (12-3)\hat{\mathbf{y}} + 6\hat{\mathbf{z}} = -3\hat{\mathbf{x}} + 9\hat{\mathbf{y}} + 6\hat{\mathbf{z}}$. Magnitude $|\nabla f| = \sqrt{9+81+36} = \sqrt{126} = 3\sqrt{14}$, so $\hat{\mathbf{n}} = \frac{-\hat{\mathbf{x}} + 3\hat{\mathbf{y}} + 2\hat{\mathbf{z}}}{\sqrt{14}}$.

### Q5. lect_12_13.pdf Problem 3 (Assignment / Tutorial)
Calculate the total outward flux of $\mathbf{v} = \rho z\hat{\mathbf{z}}$ for a solid cylinder bounded by $z=0$, $z=2$, and radius $\rho = 2$ (and verify with the divergence theorem).
- **Hint:** The curved wall has $d\mathbf{s}_1 = \rho\,d\phi\,dz\hat{\boldsymbol{\rho}}$ perpendicular to $\mathbf{v}$, and the bottom cap has $z=0$.
- **Solution:** Curved wall flux $= 0$; bottom cap ($z=0$) flux $= 0$; top cap ($z=2$, $d\mathbf{s}_2 = \rho\,d\rho\,d\phi\hat{\mathbf{z}}$) gives $\int_0^2\int_0^{2\pi} 2\rho^2\,d\rho\,d\phi = \frac{2}{3}(8)(2\pi) = \frac{32\pi}{3}$. By divergence theorem: $\nabla\cdot\mathbf{v} = \rho$, so $\int_0^2\int_0^{2\pi}\int_0^2 \rho(\rho\,d\rho\,d\phi\,dz) = \frac{8}{3}(2\pi)(2) = \frac{32\pi}{3}$.

### Q6. lect_14.pdf Problem-1 & Problem-2 (Assignment / Tutorial)
(a) Three equal charges of $200\text{ nC}$ are placed in free space at $(0,0,0)$, $(2,0,0)$, and $(0,2,0)$. Find the total force on a $500\text{ nC}$ charge at $(2,2,0)$. (b) Point charges $20\text{ nC}$ and $-20\text{ nC}$ are at $(1,0,0)$ and $(0,1,0)$. Find $\mathbf{E}$ at $(0,0,1)$.
- **Hint:** Compute $\mathbf{R}_i = \mathbf{r} - \mathbf{r}_i$ for each source charge and sum $\frac{q_i}{4\pi\epsilon_0 R_i^3}\mathbf{R}_i$.
- **Solution:** (a) $\mathbf{F}_1 = 225\mathbf{a}_y\,\mu\text{N}$ from $(2,0,0)$, $\mathbf{F}_2 = 225\mathbf{a}_x\,\mu\text{N}$ from $(0,2,0)$, and $\mathbf{F}_3 = \frac{9\times 10^9(200\times 10^{-9})(500\times 10^{-9})}{(2\sqrt{2})^3}(2\mathbf{a}_x+2\mathbf{a}_y) \approx 79.55(\mathbf{a}_x+\mathbf{a}_y)\,\mu\text{N}$. Total $\mathbf{F}_t \approx 304.55(\mathbf{a}_x+\mathbf{a}_y)\,\mu\text{N}$. (b) $\mathbf{R}_1 = -\mathbf{a}_x+\mathbf{a}_z$, $\mathbf{R}_2 = -\mathbf{a}_y+\mathbf{a}_z$ ($R_1=R_2=\sqrt{2}$), so $\mathbf{E} = \frac{9\times 10^9(20\times 10^{-9})}{2^{3/2}}[(-\mathbf{a}_x+\mathbf{a}_z)-(-\mathbf{a}_y+\mathbf{a}_z)] \approx 63.64(-\mathbf{a}_x+\mathbf{a}_y)\text{ V/m}$.

### Q7. Assignment-1 Q1 (Assignment / Tutorial)
Find the electric field a distance $z$ above the center of a flat circular disk of radius $R$ carrying a uniform surface charge $\sigma$. What does the formula give as $R\to\infty$ and for $z\gg R$?
- **Hint:** Integrate rings of charge $dq = \sigma(2\pi r'\,dr')$ from $0$ to $R$.
- **Solution:** $\mathbf{E} = \frac{\sigma}{2\epsilon_0}\left(1 - \frac{z}{\sqrt{R^2+z^2}}\right)\hat{\mathbf{z}}$ for $z>0$. As $R\to\infty$, $\mathbf{E} \to \frac{\sigma}{2\epsilon_0}\hat{\mathbf{z}}$ (infinite sheet). For $z\gg R$, $\frac{z}{\sqrt{R^2+z^2}} \approx 1 - \frac{R^2}{2z^2}$, giving $\mathbf{E} \approx \frac{\sigma\pi R^2}{4\pi\epsilon_0 z^2}\hat{\mathbf{z}} = \frac{Q}{4\pi\epsilon_0 z^2}\hat{\mathbf{z}}$.

### Q8. Assignment-1 Q2 (Assignment / Tutorial)
A sphere of radius $R$ contains a total charge $Q$ uniformly distributed throughout its volume. Calculate the work done to assemble these charges.
- **Hint:** Compute $W = \frac{\epsilon_0}{2}\int_{\text{all space}} E^2\,d\tau$ by splitting $0<r<R$ and $r>R$ (or integrate $dW = V(r)\,dq$ shell by shell).
- **Solution:** $E(r) = \frac{Qr}{4\pi\epsilon_0 R^3}$ ($r<R$) and $\frac{Q}{4\pi\epsilon_0 r^2}$ ($r>R$). Integrating $\frac{\epsilon_0}{2}E^2(4\pi r^2\,dr)$ gives $W_{\text{in}} = \frac{Q^2}{40\pi\epsilon_0 R}$ and $W_{\text{out}} = \frac{Q^2}{8\pi\epsilon_0 R}$, so $W = \frac{3Q^2}{20\pi\epsilon_0 R}$.

### Q9. Assignment-1 Q3 & lect_18.pdf (Assignment / Tutorial)
Charge is uniformly distributed with density $\rho_v$ within a sphere of radius $a$. An isolated uncharged conducting spherical shell with inner radius $b$ and outer radius $c$ ($a<b<c$) is placed concentrically. Determine $\mathbf{E}$ in all four regions and the induced surface charge densities at $r=b$ and $r=c$.
- **Hint:** Apply Gauss's law to concentric spherical surfaces in regions I ($r<a$), II ($a\le r<b$), III ($b\le r\le c$), and IV ($r>c$).
- **Solution:** I ($r<a$): $\mathbf{E} = \frac{\rho_v r}{3\epsilon_0}\mathbf{a}_r$. II ($a\le r<b$): $\mathbf{E} = \frac{\rho_v a^3}{3\epsilon_0 r^2}\mathbf{a}_r$. III ($b\le r\le c$, inside conductor): $\mathbf{E} = \mathbf{0}$, so inner wall carries $Q_b = -\frac{4}{3}\pi a^3\rho_v \implies \rho_{sb} = -\frac{a^3}{3b^2}\rho_v$. IV ($r>c$): outer wall carries $+\frac{4}{3}\pi a^3\rho_v \implies \rho_{sc} = \frac{a^3}{3c^2}\rho_v$, and $\mathbf{E} = \frac{\rho_v a^3}{3\epsilon_0 r^2}\mathbf{a}_r$.

### Q10. Assignment-1 Q4 (Assignment / Tutorial)
A sphere of radius $R$ carries polarization $\mathbf{P}(\mathbf{r}) = k\mathbf{r}$, where $k$ is a constant and $\mathbf{r}$ is from the center. Calculate $\rho_b$, $\sigma_b$, and the electric field inside and outside the sphere.
- **Hint:** Use $\rho_b = -\nabla\cdot\mathbf{P}$, $\sigma_b = \mathbf{P}\cdot\hat{\mathbf{r}}$, and Gauss's law.
- **Solution:** $\rho_b = -\nabla\cdot(k\mathbf{r}) = -3k$; $\sigma_b = kR$ at $r=R$. Inside ($r<R$), $Q_{b,\text{enc}} = -4\pi k r^3 \implies \mathbf{E}_{\text{in}} = -\frac{k\mathbf{r}}{\epsilon_0}$. Outside ($r>R$), total bound charge is $0$, so $\mathbf{E}_{\text{out}} = \mathbf{0}$.

### Q11. Assignment-1 Q5 (Assignment / Tutorial)
Find the volume bound charge density $\rho_b$, surface bound charge density $\sigma_b$, and total bound charge of a dielectric cube of side $a = 2\text{ units}$, centered at the origin, carrying polarization $\mathbf{P} = 6\mathbf{r}$.
- **Hint:** Write $\mathbf{P} = 6(x\hat{\mathbf{x}} + y\hat{\mathbf{y}} + z\hat{\mathbf{z}})$ and evaluate $\mathbf{P}\cdot\hat{\mathbf{n}}$ on each face $x=\pm 1, y=\pm 1, z=\pm 1$.
- **Solution:** $\rho_b = -\nabla\cdot(6\mathbf{r}) = -18$, so total volume bound charge is $Q_{bv} = -18\times 2^3 = -144$. On each of the 6 faces (e.g. $x=+1$ with $\hat{\mathbf{n}}=\hat{\mathbf{x}}$, or $x=-1$ with $\hat{\mathbf{n}}=-\hat{\mathbf{x}}$), $\sigma_b = \mathbf{P}\cdot\hat{\mathbf{n}} = 6$, so total surface bound charge is $Q_{bs} = 6\times (6\times 2^2) = +144$. Net bound charge $Q_{bv} + Q_{bs} = 0$.

### Q12. Assignment-1 Q6 & lect_22.pdf (Assignment / Tutorial)
Find the relative permittivity $\epsilon_r$ of the dielectric in a parallel-plate capacitor if: (a) $A = 0.12\text{ m}^2$, $d = 80\,\mu\text{m}$, $V_0 = 12\text{ V}$, $W = 1\,\mu\text{J}$; (b) $w_e = 100\text{ J/m}^3$, $V_0 = 200\text{ V}$, $d = 45\,\mu\text{m}$; (c) $E = 200\text{ kV/m}$, $\sigma = 20\,\mu\text{C/m}^2$.
- **Hint:** Use (a) $W = \frac{\epsilon_0\epsilon_r A}{2d}V_0^2$, (b) $w_e = \frac{1}{2}\epsilon_0\epsilon_r(V_0/d)^2$, and (c) $D = \epsilon_0\epsilon_r E = \sigma$ ($\epsilon_0 = 8.854\times 10^{-12}\text{ F/m}$).
- **Solution:** (a) $\epsilon_r = \frac{2Wd}{\epsilon_0 A V_0^2} = \frac{2(10^{-6})(80\times 10^{-6})}{8.854\times 10^{-12}(0.12)(144)} \approx 1.046$. (b) $\epsilon_r = \frac{2 w_e d^2}{\epsilon_0 V_0^2} = \frac{2(100)(45\times 10^{-6})^2}{8.854\times 10^{-12}(200)^2} \approx 1.144$. (c) $\epsilon_r = \frac{\sigma}{\epsilon_0 E} = \frac{20\times 10^{-6}}{8.854\times 10^{-12}(2\times 10^5)} \approx 11.294$.

### Q13. lect_17.pdf Problem-2 & lect_22.pdf D3.3 (Quiz / Lab)
(a) An electron and a proton separated by $10^{-11}\text{ m}$ lie along the $z$-axis symmetrically about $z=0$ ($\mathbf{p}$ along $+\mathbf{a}_z$). Find $V$ at $P(3, 4, 12)$. (b) Given $\mathbf{D} = 0.3 r^2 \mathbf{a}_r\text{ nC/m}^2$ in free space, find the total charge within sphere $r=3\text{ m}$.
- **Hint:** (a) $r = \sqrt{3^2+4^2+12^2} = 13\text{ m}$ and $V = \frac{\mathbf{p}\cdot\mathbf{r}}{4\pi\epsilon_0 r^3}$. (b) By Gauss's law for $\mathbf{D}$, $Q_{\text{enc}} = \oint \mathbf{D}\cdot d\mathbf{s} = 4\pi r^2 D_r$.
- **Solution:** (a) $p = 1.6\times 10^{-19}\times 10^{-11} = 1.6\times 10^{-30}\text{ C}\cdot\text{m}$, so $V = \frac{9\times 10^9(1.6\times 10^{-30})(12)}{13^3} \approx 7.865\times 10^{-23}\text{ V}$. (b) At $r=3\text{ m}$, $Q_{\text{enc}} = 4\pi(3)^2 [0.3(3)^2]\text{ nC} = 97.2\pi\text{ nC} \approx 305.4\text{ nC}$.

### Q14. lect_21.pdf Problem-2 (Coaxial Laplace) (Assignment / Tutorial)
The inner conductor of radius $a$ of a coaxial cable is at potential $V_0$ while the outer conductor of radius $b$ is grounded ($V=0$). Using Laplace's equation, find $V(\rho)$, $\mathbf{E}$, and the capacitance per unit length.
- **Hint:** Solve $\frac{1}{\rho}\frac{d}{d\rho}\left(\rho\frac{dV}{d\rho}\right) = 0$ with $V(a)=V_0$ and $V(b)=0$.
- **Solution:** $V(\rho) = c\ln\rho + d$; applying $V(b)=0$ and $V(a)=V_0$ gives $V(\rho) = V_0\frac{\ln(\rho/b)}{\ln(a/b)}$. Then $\mathbf{E} = -\nabla V = \frac{V_0}{\rho\ln(b/a)}\mathbf{a}_\rho$, $\rho_s(a) = \frac{\epsilon V_0}{a\ln(b/a)}$, $Q/L = 2\pi a\rho_s = \frac{2\pi\epsilon V_0}{\ln(b/a)}$, and $C/L = \frac{2\pi\epsilon}{\ln(b/a)}$.

### Q15. Assignment-2 Q1(i) & Q1(ii) (Assignment / Tutorial)
(i) A charged particle enters $\mathbf{E} = E\hat{\mathbf{z}}$ and $\mathbf{B} = B\hat{\mathbf{x}}$ at the origin with initial velocity $\mathbf{v}_0 = \frac{E}{\sqrt{2}B}(\hat{\mathbf{y}}+\hat{\mathbf{z}})$. Describe its velocity evolution. (ii) For a straight wire, $H_\phi = I/(2\pi s)$ gives $\nabla\times\mathbf{H}=\mathbf{0}$ for $s>0$, yet Ampere's law says $\nabla\times\mathbf{H}=\mathbf{J}$. Resolve this contradiction.
- **Hint:** (i) Split $\mathbf{v}$ into drift $\mathbf{v}_d = (E/B)\hat{\mathbf{y}}$ plus circular gyration in the $yz$-plane. (ii) Check what happens at $s=0$ (and inside a finite-radius wire).
- **Solution:** (i) $\mathbf{F}/m = \frac{q}{m}[E\hat{\mathbf{z}} + (v_z B\hat{\mathbf{y}} - v_y B\hat{\mathbf{z}})]$. Writing $v_y = \frac{E}{B} + u_y$, $v_z = u_z$ removes the constant $E$, leaving cycloidal motion: drift $\frac{E}{B}\hat{\mathbf{y}}$ superposed with gyration at $\omega_c = qB/m$ and amplitude $u_0 = \frac{E}{B}\sqrt{2-\sqrt{2}}$ (stays in the $yz$-plane with $v_x(t)=0$). (ii) $H_\phi = I/(2\pi s)$ holds only outside the wire ($s>0$, where $\mathbf{J}=\mathbf{0}$); at $s=0$ the current is concentrated in a 2D Dirac delta $\mathbf{J} = I\delta(x)\delta(y)\hat{\mathbf{z}}$ (or $J=I/(\pi R^2)$ inside radius $R$), so $\int(\nabla\times\mathbf{H})\cdot d\mathbf{s} = \oint\mathbf{H}\cdot d\mathbf{l} = I$.

### Q16. lect_26.pdf Problem-1 & lect_27.pdf Problem-4 (Quiz / Lab)
(a) Find the magnetic field at the center of a square loop carrying steady current $I$, if $R$ is the distance from the center to each side. (b) Which vector potential $\mathbf{A}$ produces $\mathbf{B}$ along $-\hat{\mathbf{x}}$: $\frac{z}{2}\hat{\mathbf{y}}$, $z\hat{\mathbf{x}}+x\hat{\mathbf{z}}$, $x\hat{\mathbf{x}}+y\hat{\mathbf{y}}$, or $-x\hat{\mathbf{x}}-y\hat{\mathbf{y}}-z\hat{\mathbf{z}}$?
- **Hint:** (a) Use $B = \frac{\mu_0 I}{4\pi s}(\sin\theta_2 - \sin\theta_1)$ with $\theta_1=-45^\circ$, $\theta_2=+45^\circ$ for each of the 4 sides. (b) Compute $\nabla\times\mathbf{A}$.
- **Solution:** (a) Each side gives $B_{\text{side}} = \frac{\mu_0 I}{4\pi R}(2\cdot\frac{\sqrt{2}}{2}) = \frac{\sqrt{2}\mu_0 I}{4\pi R}$, so 4 sides give $B_{\text{tot}} = \frac{\sqrt{2}\mu_0 I}{\pi R}$ perpendicular to the loop. (b) For $\mathbf{A} = \frac{z}{2}\hat{\mathbf{y}}$, $\nabla\times\mathbf{A} = -\frac{\partial(z/2)}{\partial z}\hat{\mathbf{x}} = -\frac{1}{2}\hat{\mathbf{x}}$ (along $-\hat{\mathbf{x}}$); the other three choices all have $\nabla\times\mathbf{A}=\mathbf{0}$.

### Q17. Assignment-2 Q3 & Q4 (Assignment / Tutorial)
A coaxial cable of inner radius $a$ and outer radius $b$ is separated by linear insulating material of magnetic susceptibility $\chi_m$. Current $I$ flows down the inner tube ($+\hat{\mathbf{z}}$) and returns along the outer tube ($-\hat{\mathbf{z}}$). Find $\mathbf{H}$, $\mathbf{B}$, $\mathbf{M}$, $\mathbf{J}_b$, and $\mathbf{K}_b$ for $a < s < b$, and verify that free + bound currents give $\mathbf{B}$.
- **Hint:** Use $\oint\mathbf{H}\cdot d\mathbf{l} = I_{f,\text{enc}}$ first, then $\mathbf{M}=\chi_m\mathbf{H}$, $\mathbf{J}_b=\nabla\times\mathbf{M}$, $\mathbf{K}_b=\mathbf{M}\times\hat{\mathbf{n}}$.
- **Solution:** For $a<s<b$: $\mathbf{H} = \frac{I}{2\pi s}\hat{\boldsymbol{\phi}}$, $\mathbf{M} = \frac{\chi_m I}{2\pi s}\hat{\boldsymbol{\phi}}$, and $\mathbf{B} = \mu_0(1+\chi_m)\frac{I}{2\pi s}\hat{\boldsymbol{\phi}}$. Since $s M_\phi$ is constant, $\mathbf{J}_b = \nabla\times\mathbf{M} = \mathbf{0}$. At $s=a$ ($\hat{\mathbf{n}}=-\hat{\mathbf{s}}$), $\mathbf{K}_b(a) = \frac{\chi_m I}{2\pi a}\hat{\mathbf{z}}$ (total $I_b(a) = \chi_m I$); at $s=b$ ($\hat{\mathbf{n}}=+\hat{\mathbf{s}}$), $\mathbf{K}_b(b) = -\frac{\chi_m I}{2\pi b}\hat{\mathbf{z}}$. Total enclosed current for $a<s<b$ is $I_f + I_b(a) = (1+\chi_m)I$, reproducing $\mathbf{B} = \mu_0(1+\chi_m)\frac{I}{2\pi s}\hat{\boldsymbol{\phi}}$.

### Q18. lect_30.pdf Problem-3 & lect_31.pdf Problem-3 (Assignment / Tutorial)
(a) Within a bar, $B = 0.63\text{ T}$ at $H = 5\times 10^5\text{ A/m}$. Find $\mu$, $\chi_m$, and type of magnetism. (b) A $0.25\text{ m}$, $400$-turn coil carrying $15\text{ A}$ contains a chromium bar ($\chi_m = 3.13\times 10^{-4}$). Compute $B$ and $M$ inside chromium.
- **Hint:** Use $H = NI/l$, $\mu = \mu_0(1+\chi_m)$, $B = \mu H$, and $M = \chi_m H$.
- **Solution:** (a) $\mu = \frac{0.63}{5\times 10^5} = 1.26\times 10^{-6}\text{ H/m}$, $\chi_m = \frac{\mu}{\mu_0}-1 = \frac{1.26\times 10^{-6}}{4\pi\times 10^{-7}} - 1 \approx 0.00268$ (positive and small $\implies$ paramagnetic). (b) $H = \frac{400\times 15}{0.25} = 24000\text{ A/m}$, $M = 3.13\times 10^{-4}\times 24000 = 7.512\text{ A/m}$, $B = 4\pi\times 10^{-7}(1.000313)(24000) \approx 0.03017\text{ T}$.

### Q19. lect_31.pdf Problem-4 (Assignment / Tutorial)
An infinitely long cylinder of radius $b$ carries only magnetization $\mathbf{M} = b r \hat{\mathbf{z}}$ (no free current, where $r$ is the cylindrical radial coordinate). Calculate $\mathbf{H}$, $\mathbf{J}_b$, $\mathbf{K}_b$, $\mathbf{B}_{\text{in}}$, and $\mathbf{B}_{\text{out}}$.
- **Hint:** With no free current and axial symmetry, $\mathbf{H}=\mathbf{0}$, so $\mathbf{B} = \mu_0(\mathbf{H}+\mathbf{M})$.
- **Solution:** $\mathbf{H} = \mathbf{0}$ everywhere (since $\mathbf{J}_f = \mathbf{0}$ and $\mathbf{K}_b$ is azimuthal like a solenoid). Volume bound current: $\mathbf{J}_b = \nabla\times(br\hat{\mathbf{z}}) = -b\hat{\boldsymbol{\phi}}$. Surface bound current at $r=b$ ($\hat{\mathbf{n}}=\hat{\mathbf{r}}$): $\mathbf{K}_b = \mathbf{M}(b)\times\hat{\mathbf{r}} = b^2\hat{\boldsymbol{\phi}}$. Inside ($r<b$): $\mathbf{B}_{\text{in}} = \mu_0\mathbf{M} = \mu_0 b r\hat{\mathbf{z}}$; outside ($r>b$): $\mathbf{B}_{\text{out}} = \mathbf{0}$.

### Q20. lect_32.pdf Problem-1 & lect_34.pdf Problem-1 (Assignment / Tutorial)
(a) A copper strip of length $L$ pivoted at one end rotates at angular velocity $\omega$ in a uniform magnetic field $\mathbf{B} = B\hat{\mathbf{z}}$. Find the induced motional emf between its ends. (b) A material with $\sigma = 0.11\text{ S/m}$ and $\epsilon_r = 1.2$ is in $\mathbf{E} = \cos(0.1t)\text{ V/m}$. At $t = 5\text{ s}$, find $J_c$ and $J_D$.
- **Hint:** (a) $\mathbf{u} = \rho\omega\mathbf{a}_\phi$, integrate $\mathbf{E}_m\cdot d\mathbf{l} = (\mathbf{u}\times\mathbf{B})\cdot d\mathbf{l}$ from $0$ to $L$. (b) Use $J_c = \sigma E$ and $J_D = \epsilon_0\epsilon_r \partial E/\partial t$ (radians).
- **Solution:** (a) $\mathbf{u}\times\mathbf{B} = \rho\omega B\mathbf{a}_\rho$, so $e_{ba} = \int_0^L \rho\omega B\,d\rho = \frac{1}{2}B\omega L^2$. (b) At $t=5\text{ s}$ ($0.1t = 0.5\text{ rad}$): $J_c = 0.11\cos(0.5) \approx 0.0965\text{ A/m}^2$; $J_D = 8.854\times 10^{-12}(1.2)(-0.1\sin(0.5)) \approx -5.09\times 10^{-13}\text{ A/m}^2$.

### Q21. lect_35.pdf Problem-3 & Problem-1 (Quiz / Lab)
(a) Two solenoids have turns in ratio $1:1$, lengths in ratio $2:1$, and radii in ratio $3:2$. Find the ratio of their self-inductances. (b) A very long solenoid of radius $20\text{ cm}$ has $200\text{ turns/m}$. Find its inductance per unit length.
- **Hint:** Use $L = \frac{\mu_0 N^2 \pi r^2}{l}$ and $L/l = \mu_0\pi n^2 b^2$.
- **Solution:** (a) $L_1/L_2 = (N_1/N_2)^2 (r_1/r_2)^2 (l_2/l_1) = 1^2 \times (3/2)^2 \times (1/2) = 9/8$ ($9:8$). (b) $L/l = (4\pi\times 10^{-7})\pi(200)^2(0.2)^2 \approx 6.32\text{ mH/m}$.

### Q22. lect_37.pdf Slide 22 & PH1001 Optical Fiber Lab (Quiz / Lab)
(a) For a vacuum EM wave $\mathbf{E} = E_0\sin(\omega t - ky)\hat{\mathbf{z}}$, find $\mathbf{B}$ and relate $B_0$ to $E_0$. (b) If Earth receives $10\text{ cal}/(\text{m}^2\cdot\text{s})$ ($41.84\text{ W/m}^2$) from the Sun, find the peak $E_0$ and $B_0$ amplitudes. (c) In the PH1001 Optical Fiber Lab, which two LED wavelengths are used to measure attenuation $\alpha$ and bending losses?
- **Hint:** (a) Wave propagates along $+\hat{\mathbf{y}}$, so $\hat{\mathbf{B}} = \hat{\mathbf{k}}\times\hat{\mathbf{E}}$. (b) Average intensity $\langle S\rangle = \frac{1}{2}c\epsilon_0 E_0^2$.
- **Solution:** (a) $\hat{\mathbf{k}}\times\hat{\mathbf{E}} = \hat{\mathbf{y}}\times\hat{\mathbf{z}} = \hat{\mathbf{x}}$, so $\mathbf{B} = \frac{E_0}{c}\sin(\omega t - ky)\hat{\mathbf{x}}$ with $B_0 = E_0/c$. (b) $E_0 = \sqrt{\frac{2\langle S\rangle}{c\epsilon_0}} = \sqrt{\frac{2(41.84)}{(3\times 10^8)(8.854\times 10^{-12})}} \approx 177.5\text{ V/m}$, and $B_0 = E_0/c \approx 5.92\times 10^{-7}\text{ T}$. (c) IR LED SFH 450V ($950\text{ nm}$) and red LED SFH 756V ($660\text{ nm}$).
