# EC1000: Electrical Circuits

> From Lecture-1 Course Overview: Assignment 10%, Mid Sem 40%, End Sem 50% (S ≥ 90, A 80–89, B 70–79, C 60–69, D 50–59, U < 50). Always check the passive sign convention, keep dependent sources active when finding R_Th or using Superposition, and verify conservation of power (ΣP = 0).

## Syllabus Topics
- [ ] **Charge, Current, Voltage, Power & Sources** (Lecture 1)
- [ ] **Ohm's Law, KCL, KVL, Dividers & Δ–Y Transforms** (Lecture 2)
- [ ] **Nodal Analysis & Supernode** (Lecture 3(a,B1))
- [ ] **Mesh Analysis & Supermesh** (Lecture 3(a,B2))
- [ ] **Source Transformation & Superposition** (Lecture 4(A,B))
- [ ] **Thevenin, Norton & Maximum Power Transfer** (Lecture 4(B,C))
- [ ] **Capacitors & Inductors (DC Steady-State)** (Lecture 5)
- [ ] **First-Order RC & RL Circuits (Source-Free & Step)** (Lecture 6)
- [ ] **Sinusoids, Phasors & AC Nodal/Mesh Analysis** (Lecture 8–9(a))
- [ ] **AC Theorems, RMS, Complex Power & Max AC Power** (Lecture 9(b)–10)
- [ ] **Transformers: EMF Equation, Turns Ratio & Losses** (Lecture 11)
- [ ] **DC Motors & 3-Phase Induction Motors** (Lecture 12)
- [ ] **Semiconductor Diodes, Zener & Rectifiers** (Lecture 13)

## 1. Basics of Electricity, Power & Conservation of Energy
*Lecture 1*

**Plain Summary:** Voltage is the energy given to each coulomb of charge, while current is how fast that charge flows. Multiplying them gives electrical power, and in any closed circuit total power absorbed equals total power delivered.

- **Current & Charge:** Current is the rate of flow of charge, $i = \frac{dq}{dt}$ (Amperes), where one electron carries $1.6 \times 10^{-19}\text{ C}$.
- **Voltage & EMF:** Potential difference is work done per unit charge, $v = \frac{dw}{dq}$ (Volts = J/C).
- **Power & Energy:** Instantaneous power is $p = vi = \frac{dE}{dt}$ (Watts), and energy billed in kWh is $E = P \times t$.
- **Passive Sign Convention:** If current enters the $+$ terminal of an element, $p = +vi$ is power absorbed; if it enters the $-$ terminal, $p = +vi$ is power supplied.
- **Dependent vs Independent Sources:** Independent sources fix $V$ or $I$ regardless of the rest of the circuit; diamond-shaped dependent sources depend on another circuit variable.

**Worked Example (Lecture-1 Course Overview & Basics of Electricity.pdf (Slide 41)):** Calculate the power absorbed or supplied by each of the 4 elements: a $20\text{ V}$ source ($p_1$, $5\text{ A}$ leaving $+$), a top element ($p_2$, $12\text{ V}$ with $5\text{ A}$ entering $+$), a middle element ($p_3$, $8\text{ V}$ with $6\text{ A}$ entering $+$), and a right dependent current source $0.2I$ ($p_4$, $I=5\text{ A}$, $1\text{ A}$ leaving $+$ at $8\text{ V}$).
1. For the $20\text{ V}$ source, $5\text{ A}$ leaves the $+$ terminal, so it supplies $p_1 = 20 \times 5 = 100\text{ W}$ (or absorbed power $-100\text{ W}$).
1. For element 2, $5\text{ A}$ enters the $+$ terminal of $12\text{ V}$, so it absorbs $p_2 = 12 \times 5 = 60\text{ W}$.
1. For element 3, $6\text{ A}$ enters the $+$ terminal of $8\text{ V}$, so it absorbs $p_3 = 8 \times 6 = 48\text{ W}$.
1. For the dependent source $0.2I = 0.2(5) = 1\text{ A}$, current leaves the $+$ terminal at $8\text{ V}$, so it supplies $p_4 = 1 \times 8 = 8\text{ W}$.
**Answer:** Power supplied $= 100 + 8 = 108\text{ W}$; power absorbed $= 60 + 48 = 108\text{ W}$, verifying $\sum P = 0$.

**Key Formula:** $$i = \frac{dq}{dt}, \quad v = \frac{dw}{dq}, \quad p = vi, \quad \sum P = 0, \quad R = \rho\frac{l}{A}$$

**Common Mistake:** Mixing up absorbed vs supplied power signs: always check whether the current arrow enters the $+$ terminal (absorbs $+vi$) or leaves the $+$ terminal (supplies $+vi$).

---

## 2. Basic Laws, Dividers & Wye-Delta (Y-Δ) Transformations
*Lecture 2(a) & 2(b)*

**Plain Summary:** KCL ensures no charge piles up at a node, while KVL ensures net voltage change around any closed loop is zero. When bridge resistors are neither in series nor parallel, a Δ–Y or Y–Δ swap turns them into simple combinations.

- **Ohm's Law & Power:** For a resistor, $V = IR$ and power dissipated is $P = VI = I^2 R = \frac{V^2}{R}$ (always absorbed).
- **Kirchhoff's Laws:** KCL gives $\sum I_{\text{in}} = \sum I_{\text{out}}$ at any node; KVL gives $\sum v = 0$ around any closed loop.
- **Voltage & Current Division:** Series divider: $V_k = \frac{R_k}{R_1+R_2}V$. Parallel divider: $I_1 = \frac{R_2}{R_1+R_2}I$.
- **Δ to Y Rule:** Each Y resistor is the product of its two adjacent Δ resistors divided by the sum of all three Δ resistors.
- **Y to Δ Rule:** Each Δ resistor is the sum of pairwise products $(R_1R_2 + R_2R_3 + R_3R_1)$ divided by the opposite Y resistor; for balanced networks, $R_Y = R_\Delta / 3$.

**Worked Example (Lecture-2(b) Y and Delta Network.pdf (Slide 6)):** For the $120\text{ V}$ bridge circuit with top-left $12.5\,\Omega$, bottom-left $15\,\Omega$, top-right $10\,\Omega$, bottom-right $20\,\Omega$, center bridge $5\,\Omega$, and a parallel $30\,\Omega$ branch across terminals $a$-$b$, find $R_{ab}$ and source current $i$.
1. Convert the right-side Y ($R_1 = 10\,\Omega$, $R_2 = 20\,\Omega$, $R_3 = 5\,\Omega$) into an equivalent Δ: numerator $= 10(20) + 20(5) + 5(10) = 350$.
1. The Δ resistors are $R_{ab} = 350/5 = 70\,\Omega$, $R_{ac} = 350/20 = 17.5\,\Omega$, and $R_{bc} = 350/10 = 35\,\Omega$.
1. Combine parallel pairs: $12.5 \parallel 17.5 = 7.292\,\Omega$ and $15 \parallel 35 = 10.5\,\Omega$, which add in series to $17.792\,\Omega$.
1. Put $17.792\,\Omega$, $70\,\Omega$, and $30\,\Omega$ in parallel: $\frac{1}{R_{ab}} = \frac{1}{17.792} + \frac{1}{70} + \frac{1}{30} \implies R_{ab} = 9.632\,\Omega$.
**Answer:** $R_{ab} = 9.632\,\Omega$ and $i = \frac{120}{9.632} = 12.458\text{ A}$.

**Key Formula:** $$R_1 = \frac{R_b R_c}{R_a+R_b+R_c}, \quad R_a = \frac{R_1R_2+R_2R_3+R_3R_1}{R_1}, \quad R_Y = \frac{R_\Delta}{3}$$

**Common Mistake:** Using the wrong resistor in the current divider: for two parallel resistors $R_1$ and $R_2$, the current in $R_1$ has $R_2$ (the OTHER resistor) in the numerator, not $R_1$.

---

## 3. Nodal Analysis & Supernode
*Lecture 3(a) & 3(B1)*

**Plain Summary:** Nodal analysis assigns a voltage to every node relative to a $0\text{ V}$ ground and writes KCL at each non-reference node. When a voltage source sits between two non-reference nodes, wrap both nodes in a supernode and pair one KCL equation with a KVL constraint.

- **Reference Node:** Pick a ground node ($0\text{ V}$) and label the remaining $n-1$ node voltages $v_1, v_2, \dots, v_{n-1}$.
- **Branch Current Rule:** Current always flows from higher to lower potential: $i = \frac{v_{\text{higher}} - v_{\text{lower}}}{R}$.
- **Grounded Voltage Source:** If a voltage source connects a node directly to ground, that node voltage is immediately fixed (e.g., $v_1 = 10\text{ V}$).
- **Supernode (Floating Voltage Source):** Enclose any dependent or independent voltage source between two non-reference nodes (plus parallel elements), apply KCL to the whole boundary, and apply KVL inside to get the voltage difference constraint.
- **Dependent Sources:** Express the controlling variable ($i_x$ or $v_x$) in terms of node voltages before solving $G V = I$.

**Worked Example (Lecture-3 (B1) Super Node Analysis.pdf (Slide 4)):** A $2\text{ V}$ source ($-$ on $v_1$, $+$ on $v_2$) and parallel $10\,\Omega$ resistor connect non-reference nodes $v_1$ and $v_2$. Node $v_1$ has a $2\text{ A}$ current source entering and $2\,\Omega$ to ground; node $v_2$ has $4\,\Omega$ to ground and a $7\text{ A}$ source leaving. Find $v_1$ and $v_2$.
1. Nodes $v_1$ and $v_2$ form a supernode around the $2\text{ V}$ source (the parallel $10\,\Omega$ resistor carries only internal current and drops out of the supernode KCL).
1. Apply KCL to the supernode: $2 = \frac{v_1}{2} + \frac{v_2}{4} + 7 \implies 2v_1 + v_2 = -20$.
1. Apply KVL around the supernode loop: $-v_1 - 2 + v_2 = 0 \implies v_2 = v_1 + 2$.
1. Substitute $v_2 = v_1 + 2$: $2v_1 + (v_1 + 2) = -20 \implies 3v_1 = -22$.
**Answer:** $v_1 = -7.333\text{ V}$ and $v_2 = -5.333\text{ V}$.

**Key Formula:** $$\sum i_{\text{out}} = \sum i_{\text{in}}, \quad i = \frac{v_a - v_b}{R}, \quad v_+ - v_- = V_s \text{ (supernode KVL)}$$

**Common Mistake:** Forgetting to include the KVL constraint equation for a supernode, or writing $\frac{v_1 - v_2}{R}$ for a resistor connected in parallel with the supernode voltage source (it cancels inside KCL).

---

## 4. Mesh Analysis & Supermesh
*Lecture 3(a) & 3(B2)*

**Plain Summary:** Mesh analysis assigns a clockwise loop current to every window pane of a planar circuit and writes KVL around each mesh. If a current source sits on a shared edge between two meshes, merge them into a supermesh and pair one KVL loop with a KCL constraint.

- **Mesh Currents vs Branch Currents:** Assign clockwise mesh currents $i_1, i_2, \dots, i_n$; a shared branch carries the difference $i_1 - i_2$.
- **Matrix Form ($R I = V$):** Diagonal terms sum all resistances in mesh $k$; off-diagonal terms equal minus the shared resistance between meshes $j$ and $k$.
- **Outer-Edge Current Source:** If a current source lies in only one mesh, that mesh current is fixed immediately (no KVL needed for that mesh).
- **Supermesh (Shared Current Source):** Exclude the shared current source and any series element with it, write KVL around the combined outer loop, and apply KCL at the branch node to relate the two mesh currents.
- **Solving Linear Systems:** Use Cramer's rule ($i_k = \Delta_k / \Delta$) or Gaussian elimination to solve the simultaneous equations.

**Worked Example (Lecture-3 (B2)- Super Mesh Analysis.pdf (Slide 4)):** Find $i_o$ (flowing right in the $1\,\Omega$ resistor between bottom-left mesh $i_1$ and top mesh $i_3$) in a 3-mesh circuit: mesh 1 ($5\,\Omega$, $1\,\Omega$, shared $45\text{ A}$ upward source with mesh 2), mesh 2 ($4\,\Omega$, $180\text{ V}$ with $+$ top, shared $45\text{ A}$ source), and mesh 3 ($90\text{ V}$ with $+$ left, $2\,\Omega$, $4\,\Omega$, $1\,\Omega$).
1. Meshes 1 and 2 share the $45\text{ A}$ current source, so they form a supermesh. KCL at the bottom node gives $i_2 = i_1 + 45$.
1. Apply KVL to the supermesh (clockwise around meshes 1 and 2): $5(i_1) + 1(i_1 - i_3) + 4(i_2 - i_3) + 180 = 0 \implies 6i_1 + 4i_2 - 5i_3 = -180$.
1. Apply KVL to mesh 3 (clockwise): $90 + 4(i_3 - i_2) + 1(i_3 - i_1) + 2i_3 = 0 \implies -i_1 - 4i_2 + 7i_3 = -90$.
1. Substitute $i_2 = i_1 + 45$: $10i_1 - 5i_3 = -360$ and $-5i_1 + 7i_3 = 90$, giving $i_1 = -46\text{ A}$ and $i_3 = -20\text{ A}$.
**Answer:** $i_o = i_1 - i_3 = -46 - (-20) = -26\text{ A}$.

**Key Formula:** $$\sum v_{\text{loop}} = 0, \quad R\,I = V, \quad i_k = \frac{\Delta_k}{\Delta}$$

**Common Mistake:** Writing KVL directly through a current source (its voltage is unknown!) or getting the sign of a shared branch current $i_1 - i_2$ backwards.

---

## 5. Source Transformation & Superposition Theorem
*Lecture 4(A) & 4(B)*

**Plain Summary:** Source transformation swaps a voltage source in series with $R$ for a current source in parallel with $R$ so resistors can be combined. Superposition finds the response to one independent source at a time (others turned off) and sums the partial voltages or currents.

- **Source Transformation Equivalence:** A voltage source $v_s$ in series with $R$ equals a current source $i_s = v_s/R$ (arrow pointing to the $+$ terminal) in parallel with the same $R$.
- **Linearity Requirement:** Superposition works ONLY for linear responses ($v$ or $i$), NEVER for power ($P = I^2R$ is quadratic).
- **Turning Off Independent Sources:** Set independent voltage sources to $0\text{ V}$ (short circuit) and independent current sources to $0\text{ A}$ (open circuit).
- **Dependent Sources Stay Active:** Never turn off a dependent source during Superposition; keep it in every sub-circuit.
- **Add Algebraically:** Keep the exact same reference polarity or current arrow in every step, then sum all contributions.

**Worked Example (Lecture-4(A) Source Transformation.pdf (Slides 4–5)):** Use source transformation to find $v_o$ across the $8\,\Omega$ resistor in a circuit with a $4\,\Omega$ resistor in parallel with a $3\text{ A}$ downward source on the left, a $2\,\Omega$ series resistor in the top middle, the $8\,\Omega$ shunt resistor in the center, and a $3\,\Omega$ resistor in series with a $12\text{ V}$ source ($+$ top) on the right.
1. Transform the left $3\text{ A}$ (downward) $\parallel 4\,\Omega$ into a $12\text{ V}$ source ($-$ on top, $+$ on bottom) in series with $4\,\Omega$; combine $4 + 2 = 6\,\Omega$.
1. Transform the right $12\text{ V}$ ($+$ top) in series with $3\,\Omega$ into a $4\text{ A}$ (upward) source $\parallel 3\,\Omega$.
1. Transform the left $12\text{ V}$ ($-$ top) in series with $6\,\Omega$ into a $2\text{ A}$ (downward) source $\parallel 6\,\Omega$.
1. Combine parallel sources ($4\text{ A up} - 2\text{ A down} = 2\text{ A up}$) and parallel resistors ($6 \parallel 3 = 2\,\Omega$), then use current division into $8\,\Omega$: $i = \frac{2}{2+8}(2) = 0.4\text{ A}$.
**Answer:** $v_o = 8\,i = 8(0.4) = 3.2\text{ V}$.

**Key Formula:** $$v_s = i_s R, \quad i_s = \frac{v_s}{R}, \quad y = y_1 + y_2 + \dots + y_n \text{ (not } P\text{)}$$

**Common Mistake:** Applying superposition directly to power ($P \neq P_1 + P_2$), or pointing the transformed current arrow toward the $-$ terminal instead of the $+$ terminal.

---

## 6. Thevenin, Norton & Maximum Power Transfer
*Lecture 4(B) & 4(C)*

**Plain Summary:** Any linear two-terminal network shrinks to a single voltage source $V_{Th}$ in series with $R_{Th}$ (Thevenin) or a current source $I_N$ in parallel with $R_N$ (Norton). Maximum power goes to a resistive load when $R_L$ matches $R_{Th}$.

- **Thevenin Equivalent:** $V_{Th} = v_{oc}$ is the open-circuit voltage across terminals $a$-$b$; $R_{Th}$ is the equivalent resistance looking into $a$-$b$ with independent sources turned off.
- **Norton Equivalent:** $I_N = i_{sc}$ is the short-circuit current from $a$ to $b$, $R_N = R_{Th}$, and $V_{Th} = I_N R_{Th}$.
- **When Dependent Sources Exist:** Keep dependent sources ON; find $R_{Th} = V_{oc}/I_{sc}$ or apply a $1\text{ V}$ (or $1\text{ A}$) test source at $a$-$b$ with independent sources zeroed.
- **Maximum Power Transfer (DC):** Variable load $R_L$ absorbs maximum power when $R_L = R_{Th}$.
- **Maximum Power Value:** At $R_L = R_{Th}$, half the voltage drops across $R_L$, giving $P_{\max} = \frac{V_{Th}^2}{4 R_{Th}}$.

**Worked Example (Lecture-4(B) Network Theorems.pdf (Slides 11–12)):** Using Thevenin's equivalent circuit, calculate the current $I_0$ downward through the middle $2\,\Omega$ resistor connected between a $2\text{ V}$–$1\,\Omega$ left branch and a $3\text{ V}$–$3\,\Omega$ right branch.
1. Remove the $2\,\Omega$ load resistor to expose terminals $a$ (top) and $b$ (bottom).
1. Find $V_{Th} = V_{ab}$ by nodal analysis at $a$: $\frac{V_{Th} - 2}{1} + \frac{V_{Th} - 3}{3} = 0 \implies 4V_{Th} = 9 \implies V_{Th} = 2.25\text{ V}$.
1. Turn off the $2\text{ V}$ and $3\text{ V}$ sources (short circuits) to find $R_{Th} = 1\,\Omega \parallel 3\,\Omega = \frac{1 \times 3}{1 + 3} = 0.75\,\Omega$.
1. Reconnect the $2\,\Omega$ load to the Thevenin circuit: $I_0 = \frac{V_{Th}}{R_{Th} + R_L} = \frac{2.25}{0.75 + 2}$.
**Answer:** $V_{Th} = 2.25\text{ V}$, $R_{Th} = 0.75\,\Omega$, and $I_0 = 0.8182\text{ A}$.

**Key Formula:** $$V_{Th} = I_N R_{Th}, \quad R_L = R_{Th} \implies P_{\max} = \frac{V_{Th}^2}{4 R_{Th}}$$

**Common Mistake:** Turning off dependent sources when computing $R_{Th}$ (only independent sources are zeroed), or forgetting that $P_{\max} = V_{Th}^2 / (4 R_{Th})$ only applies when the load is matched to $R_{Th}$.

---

## 7. Capacitors & Inductors (Energy Storage & DC Steady State)
*Lecture 5*

**Plain Summary:** Capacitors store energy in an electric field and oppose sudden voltage jumps; inductors store energy in a magnetic field and oppose sudden current jumps. Under steady DC, a capacitor acts like an open circuit and an inductor acts like a short circuit.

- **Capacitor V–I & Energy:** $q = Cv$, $i_C = C\frac{dv}{dt}$, $v_C = \frac{1}{C}\int i\,dt$, and stored energy $w_C = \frac{1}{2}Cv^2$.
- **Inductor V–I & Energy:** $v_L = L\frac{di}{dt}$, $i_L = \frac{1}{L}\int v\,dt$, and stored energy $w_L = \frac{1}{2}Li^2$.
- **DC Steady State:** When voltages and currents are constant ($\frac{d}{dt} = 0$), a capacitor is an **open circuit** ($i_C = 0$) and an inductor is a **short circuit** ($v_L = 0$).
- **Continuity Laws:** Capacitor voltage $v_C$ cannot change instantaneously; inductor current $i_L$ cannot change instantaneously.
- **Series / Parallel Combinations:** Inductors combine just like resistors; capacitors combine oppositely ($C_{\text{par}} = C_1 + C_2$, $\frac{1}{C_{\text{ser}}} = \frac{1}{C_1} + \frac{1}{C_2}$).

**Worked Example (Lecture-5. Inductors & Capacitors.pdf (Slide 27)):** A $12\text{ V}$ DC source feeds a $1\,\Omega$ series resistor, followed by a shunt branch ($4\,\Omega$ in series with $1\text{ F}$ capacitor) and a right branch ($5\,\Omega$ in series with $2\text{ H}$ inductor). Under DC conditions, find $i$, $v_C$, $i_L$, and stored energies $w_C$ and $w_L$.
1. Replace the $1\text{ F}$ capacitor with an open circuit and the $2\text{ H}$ inductor with a short circuit.
1. Because the capacitor branch is open, all source current flows through the $1\,\Omega$ and $5\,\Omega$ resistors in series: $i = i_L = \frac{12}{1 + 5} = 2\text{ A}$.
1. With zero current in the $4\,\Omega$ resistor, $v_C$ equals the voltage across the $5\,\Omega$ resistor: $v_C = 5i = 5(2) = 10\text{ V}$.
1. Compute energies: $w_C = \frac{1}{2}(1)(10)^2 = 50\text{ J}$ and $w_L = \frac{1}{2}(2)(2)^2 = 4\text{ J}$.
**Answer:** $i = i_L = 2\text{ A}$, $v_C = 10\text{ V}$, $w_C = 50\text{ J}$, $w_L = 4\text{ J}$.

**Key Formula:** $$i_C = C\frac{dv}{dt}, \; w_C = \frac{1}{2}Cv^2 \quad | \quad v_L = L\frac{di}{dt}, \; w_L = \frac{1}{2}Li^2$$

**Common Mistake:** Swapping the DC rules or combination rules: at DC, C is OPEN and L is SHORT; when combining elements, capacitors in series add reciprocally like parallel resistors.

---

## 8. First-Order RC & RL Circuits (Source-Free & Step Response)
*Lecture 6(a) & 6(b)*

**Plain Summary:** Every switching transient in an RC or RL circuit decays exponentially from its initial value $x(0^+)$ to its final DC steady-state value $x(\infty)$ at a rate set by one time constant $\tau$.

- **Source-Free Decay:** With no independent source for $t > 0$, $v(t) = V_0 e^{-t/\tau}$ (RC) and $i(t) = I_0 e^{-t/\tau}$ (RL), falling to $36.8\%$ ($1/e$) at $t = \tau$.
- **Time Constants:** $\tau = R_{Th} C$ for RC circuits and $\tau = \frac{L}{R_{Th}}$ for RL circuits, where $R_{Th}$ is the resistance seen by $C$ or $L$ for $t > 0$.
- **Unit-Step Function:** $u(t) = 0$ for $t < 0$ and $1$ for $t > 0$; used to switch sources on or off cleanly.
- **3-Step Complete Response:** Find (1) $x(0^-) = x(0^+)$ before switching, (2) $x(\infty)$ at DC steady state after switching, and (3) $\tau$ for $t > 0$.
- **Universal Formula:** Plug into $x(t) = x(\infty) + [x(0^+) - x(\infty)]e^{-t/\tau}$ for $t > 0$ (where $x$ is $v_C$ or $i_L$).

**Worked Example (Lecture-6(b). First Order Circuits (R-L & R-C) with Unit Step Function.pdf (Slide 10)):** A $0.5\text{ mF}$ capacitor is connected to a switch that has been at position A ($24\text{ V}$ through a $3\text{ k}\Omega$ series and $5\text{ k}\Omega$ shunt divider) for a long time, and moves to position B ($30\text{ V}$ in series with $4\text{ k}\Omega$) at $t = 0$. Find $v(t)$ for $t > 0$ and $v(1)$.
1. For $t < 0$ (switch at A, capacitor open at DC), voltage division gives $v(0^-) = \frac{5}{5+3}(24) = 15\text{ V}$. By continuity, $v(0^+) = 15\text{ V}$.
1. For $t > 0$ (switch at B), the capacitor sees $R_{Th} = 4\text{ k}\Omega$ and $30\text{ V}$. Thus $\tau = R_{Th} C = (4\times 10^3)(0.5\times 10^{-3}) = 2\text{ s}$.
1. At $t \to \infty$, the capacitor is open again, so $v(\infty) = 30\text{ V}$.
1. Apply the step response formula: $v(t) = 30 + (15 - 30)e^{-t/2} = (30 - 15e^{-0.5t})\text{ V}$, so $v(1) = 30 - 15e^{-0.5} = 20.9\text{ V}$.
**Answer:** $v(t) = (30 - 15e^{-0.5t})\text{ V}$ for $t > 0$; $v(1) = 20.9\text{ V}$.

**Key Formula:** $$\tau_{RC} = R_{Th}C, \quad \tau_{RL} = \frac{L}{R_{Th}}, \quad x(t) = x(\infty) + [x(0^+) - x(\infty)]e^{-t/\tau}$$

**Common Mistake:** Using the $t < 0$ resistor network to calculate $\tau$, or forgetting that $R_{Th}$ for $\tau$ must be computed in the $t > 0$ circuit with independent sources turned off.

---

## 9. Sinusoids, Phasors, Impedance & AC Nodal/Mesh
*Lecture 8 & 9(a)*

**Plain Summary:** Phasors turn differential equations of AC circuits at a fixed frequency $\omega$ into ordinary complex algebra. Once resistors, inductors, and capacitors become impedances $Z$, DC Nodal and Mesh methods work unchanged.

- **Cosine Phasor Convention:** $v(t) = V_m\cos(\omega t + \phi) \iff \mathbf{V} = V_m\angle\phi$; convert $\sin(\theta)$ using $\sin(\theta) = \cos(\theta - 90^\circ)$ and $-\sin(\theta) = \cos(\theta + 90^\circ)$.
- **Element Impedances:** $Z_R = R$, $Z_L = j\omega L$ (current lags $V$ by $90^\circ$), and $Z_C = \frac{1}{j\omega C} = -j\frac{1}{\omega C}$ (current leads $V$ by $90^\circ$).
- **Impedance & Admittance:** $Z = R + jX$ ($\Omega$) and $Y = 1/Z = G + jB$ (S); series and parallel combinations follow resistor rules.
- **AC Analysis Workflow:** (1) Transform sources and $R,L,C$ to the phasor domain at $\omega$, (2) solve via Nodal/Mesh with complex numbers, (3) convert back to $\cos(\omega t + \phi)$.
- **Same-Frequency Rule:** Phasors can only be added or solved together in one circuit when all sources share the exact same $\omega$.

**Worked Example (Lecture-9 (a) Sinusoidal Steady State Analysis (Mesh & Nodal).pdf (Slides 8–9)):** Find $v_o(t)$ across the $1\,\Omega$ resistor using AC nodal analysis: left branch $16\sin(4t)\text{ V}$ in series with $4\,\Omega$ and $\frac{1}{12}\text{ F}$, center parallel $1\,\Omega$ and $2\cos(4t)\text{ A}$ upward, right branch $2\text{ H}$ in series with $6\,\Omega$.
1. With $\omega = 4\text{ rad/s}$, convert to cosine phasors: $2\cos(4t) \to 2\angle 0^\circ\text{ A}$ and $16\sin(4t) = 16\cos(4t - 90^\circ) \to -j16\text{ V}$.
1. Compute reactances: $Z_L = j(4)(2) = j8\,\Omega$ and $Z_C = \frac{1}{j(4)(1/12)} = -j3\,\Omega$.
1. Write KCL at top node $\mathbf{V}_o$: $\frac{-j16 - \mathbf{V}_o}{4 - j3} + 2 = \frac{\mathbf{V}_o}{1} + \frac{\mathbf{V}_o}{6 + j8}$.
1. Solve for $\mathbf{V}_o$: $\mathbf{V}_o = \frac{3.92 - j2.56}{1.22 + j0.04} = 3.835\angle -35.02^\circ\text{ V}$.
**Answer:** $v_o(t) = 3.835\cos(4t - 35.02^\circ)\text{ V}$.

**Key Formula:** $$Z_L = j\omega L, \quad Z_C = \frac{1}{j\omega C} = -\frac{j}{\omega C}, \quad \sin(\omega t) = \cos(\omega t - 90^\circ)$$

**Common Mistake:** Forgetting to convert $\sin(\omega t)$ to $\cos(\omega t - 90^\circ)$ before writing the phasor, or mixing $Z_C = +j\omega C$ instead of $1/(j\omega C)$.

---

## 10. AC Theorems, RMS, Complex Power & Maximum AC Power
*Lecture 9(b) & 10*

**Plain Summary:** Superposition handles mixed frequencies (like DC + AC) by solving each frequency separately and adding in the time domain. Complex power $\mathbf{S} = P + jQ$ tracks both useful average power $P$ (Watts) and reactive exchange $Q$ (VAR).

- **Mixed-Frequency Superposition:** Never add phasors of different $\omega$; solve each source with its own $\omega$ (for DC, $\omega = 0$ so $L$ is short and $C$ is open), then sum in time.
- **RMS Value:** $I_{\text{rms}} = \sqrt{\frac{1}{T}\int_0^T i^2(t)\,dt}$; for a pure sinusoid, $V_{\text{rms}} = V_m/\sqrt{2}$ and $I_{\text{rms}} = I_m/\sqrt{2}$.
- **Complex Power & Power Factor:** $\mathbf{S} = \mathbf{V}_{\text{rms}}\mathbf{I}_{\text{rms}}^* = \frac{1}{2}\mathbf{V}_m\mathbf{I}_m^* = P + jQ$, with $\text{pf} = \cos(\theta_v - \theta_i) = P/|\mathbf{S}|$.
- **Lagging vs Leading PF:** Inductive loads have $\theta_v - \theta_i > 0$ and $Q > 0$ (lagging pf); capacitive loads have $\theta_v - \theta_i < 0$ and $Q < 0$ (leading pf).
- **Maximum Average Power Transfer:** For a general load, set $\mathbf{Z}_L = \mathbf{Z}_{Th}^* = R_{Th} - jX_{Th}$ giving $P_{\max} = \frac{|\mathbf{V}_{Th}|^2}{8 R_{Th}}$ (peak $\mathbf{V}_{Th}$); for a purely real load, $R_L = |\mathbf{Z}_{Th}|$.

**Worked Example (Lecture-10 AC Circuits (AC Power Analysis (Ch. 11).pdf (Example 11.5, Slides 15–16)):** A $10\angle 0^\circ\text{ V}$ (peak) source feeds $4\,\Omega$ series, $(8 - j6)\,\Omega$ shunt, and $j5\,\Omega$ series into load $\mathbf{Z}_L$. Find $\mathbf{Z}_L$ for maximum average power transfer and compute $P_{\max}$.
1. Turn off $10\angle 0^\circ\text{ V}$ (short circuit) to find $\mathbf{Z}_{Th} = j5 + 4 \parallel (8 - j6) = j5 + \frac{4(8 - j6)}{12 - j6} = 2.933 + j4.467\,\Omega$.
1. Find open-circuit voltage by voltage division: $\mathbf{V}_{Th} = \frac{8 - j6}{4 + 8 - j6}(10\angle 0^\circ) = 7.454\angle -10.3^\circ\text{ V}$ (peak).
1. Match the load with the complex conjugate: $\mathbf{Z}_L = \mathbf{Z}_{Th}^* = 2.933 - j4.467\,\Omega$.
1. Compute $P_{\max} = \frac{|\mathbf{V}_{Th}|^2}{8 R_{Th}} = \frac{(7.454)^2}{8(2.933)} = 2.368\text{ W}$.
**Answer:** $\mathbf{Z}_L = 2.933 - j4.467\,\Omega$ and $P_{\max} = 2.368\text{ W}$.

**Key Formula:** $$\mathbf{S} = \mathbf{V}_{\text{rms}}\mathbf{I}_{\text{rms}}^* = P + jQ, \quad P = \frac{1}{2}V_m I_m\cos(\theta_v - \theta_i), \quad P_{\max} = \frac{|\mathbf{V}_{Th}|^2}{8R_{Th}} \text{ (peak } V_{Th}\text{)}$$

**Common Mistake:** Missing the factor of $1/2$ when using peak phasors ($P = \frac{1}{2}V_m I_m\cos\theta$ vs $V_{\text{rms}}I_{\text{rms}}\cos\theta$), or forgetting the conjugate $\mathbf{I}^*$ in $\mathbf{S} = \mathbf{V}\mathbf{I}^*$.

---

## 11. Transformers: EMF Equation, Turns Ratio & Losses
*Lecture 11*

**Plain Summary:** A transformer transfers AC power from primary to secondary through a shared magnetic core without changing frequency, stepping voltage up or down in direct proportion to the turns ratio $N_2/N_1$.

- **Core Principle:** Works by Faraday's law of electromagnetic induction; windings are magnetically coupled and electrically isolated.
- **EMF Equation:** For sinusoidal flux $\Phi = \Phi_m\sin(\omega t)$, the RMS induced EMF is $E = 4.44 f N \Phi_m = 4.44 f N B_m A$.
- **Transformation Ratio ($K$):** $\frac{E_2}{E_1} = \frac{N_2}{N_1} = \frac{I_1}{I_2} = K$ ($K > 1$ step-up, $K < 1$ step-down, $K = 1$ isolation).
- **Losses & Max Efficiency:** Core/iron loss $P_i$ (hysteresis + eddy current, constant with load) and copper loss $P_c$ ($I^2R$); efficiency $\eta = \frac{P_{\text{out}}}{P_{\text{out}} + P_i + P_c}$ is maximum when $P_c = P_i$.
- **Voltage Regulation & VA Rating:** Regulation $\% = \frac{E_{\text{no-load}} - E_{\text{full-load}}}{E_{\text{full-load}}}\times 100\%$; rated in VA ($V_2 I_2$) because heating depends on current regardless of load power factor.

**Worked Example (Lecture-11 Transformers.pdf (Example 3, Slide 13)):** A $25\text{ kVA}$ single-phase transformer has $N_1 = 500$ turns and $N_2 = 50$ turns, connected to a $3000\text{ V}$, $50\text{ Hz}$ supply. Find full-load primary and secondary currents, secondary EMF, and maximum flux $\Phi_m$ in the core.
1. Turns ratio: $K = \frac{N_2}{N_1} = \frac{50}{500} = \frac{1}{10}$.
1. Full-load primary current: $I_1 = \frac{S}{E_1} = \frac{25000}{3000} = 8.33\text{ A}$, and secondary current $I_2 = \frac{I_1}{K} = 10 \times 8.33 = 83.3\text{ A}$.
1. Secondary EMF: $E_2 = K E_1 = \frac{1}{10}(3000) = 300\text{ V}$.
1. From $E_1 = 4.44 f N_1 \Phi_m$: $3000 = 4.44(50)(500)\Phi_m \implies \Phi_m = 27\text{ mWb}$.
**Answer:** $I_1 = 8.33\text{ A}$, $I_2 = 83.3\text{ A}$, $E_2 = 300\text{ V}$, $\Phi_m = 27\text{ mWb}$.

**Key Formula:** $$E_{\text{rms}} = 4.44\,f\,N\,\Phi_m, \quad \frac{E_2}{E_1} = \frac{N_2}{N_1} = \frac{I_1}{I_2}, \quad \eta_{\max} \text{ at } P_{\text{core}} = P_{\text{cu}}$$

**Common Mistake:** Inverting the current ratio: voltage scales with $N_2/N_1$, so current scales inversely ($I_1/I_2 = N_2/N_1$) to conserve $E_1 I_1 = E_2 I_2$.

---

## 12. Electrical Machines: DC Motors & 3-Phase Induction Motors
*Lecture 12*

**Plain Summary:** Electrical machines convert between electrical and mechanical energy using force on a current-carrying wire ($F = IBl$) and induced EMF ($e = vBl$). In a 3-phase induction motor, the rotor must spin slightly slower than the stator's rotating field so slip induces rotor current and torque.

- **DC Motor Force & Back-EMF:** Armature current $i_a$ via commutator and brushes creates fixed torque $T = k i_f i_a$, while spinning induces back-EMF $E = k\omega$.
- **3-Phase Rotating Magnetic Field:** Balanced 3-phase stator currents at frequency $f_e$ with $P$ poles create a field rotating at synchronous speed $n_{\text{sync}} = \frac{120 f_e}{P}$ rpm.
- **Why Slip Must Be Non-Zero:** If $n_m = n_{\text{sync}}$, the rotor sees no relative motion, zero EMF/current is induced, and torque drops to zero.
- **Slip & Rotor Frequency:** Slip $s = \frac{n_{\text{sync}} - n_m}{n_{\text{sync}}}$ ($s=0$ at sync, $s=1$ at standstill), rotor speed $n_m = (1-s)n_{\text{sync}}$, and rotor frequency $f_r = s f_e$.
- **Mechanical Power & Torque:** $P_{\text{out}} = \tau_{\text{load}}\,\omega_m$ with $\omega_m = \frac{2\pi n_m}{60}\text{ rad/s}$ and $1\text{ HP} = 746\text{ W}$.

**Worked Example (Lecture-12 Electrical Machines.pdf (Example 1, Slides 41–42)):** A $208\text{ V}$, $10\text{ HP}$, $4$-pole, $60\text{ Hz}$ Y-connected induction motor runs at a full-load slip of $5\%$. Find synchronous speed, rotor speed, rotor frequency, and shaft torque.
1. Synchronous speed: $n_{\text{sync}} = \frac{120 f_e}{P} = \frac{120(60)}{4} = 1800\text{ rpm}$.
1. Rotor speed: $n_m = (1 - s)n_{\text{sync}} = (1 - 0.05)(1800) = 1710\text{ rpm}$.
1. Rotor frequency: $f_r = s f_e = 0.05 \times 60 = 3\text{ Hz}$.
1. Shaft torque: $\tau_{\text{load}} = \frac{P_{\text{out}}}{\omega_m} = \frac{10 \times 746}{2\pi (1710)/60} = 41.7\text{ N}\cdot\text{m}$.
**Answer:** $n_{\text{sync}} = 1800\text{ rpm}$, $n_m = 1710\text{ rpm}$, $f_r = 3\text{ Hz}$, $\tau_{\text{load}} = 41.7\text{ N}\cdot\text{m}$.

**Key Formula:** $$n_{\text{sync}} = \frac{120 f_e}{P}, \quad s = \frac{n_{\text{sync}} - n_m}{n_{\text{sync}}}, \quad f_r = s f_e, \quad \tau = \frac{P_{\text{out}}}{2\pi n_m / 60}$$

**Common Mistake:** Confusing pole pairs with total poles $P$ in $n_{\text{sync}} = 120 f_e / P$ (3 pole-pairs means $P = 6$), or forgetting to convert rpm to rad/s ($\times 2\pi/60$) and HP to Watts ($\times 746$) when computing torque.

---

## 13. Semiconductor Diodes, Zener & Rectifier Circuits
*Lecture 13*

**Plain Summary:** A p–n junction diode acts like a one-way valve for current: it conducts when forward-biased above its threshold voltage and blocks when reverse-biased, turning AC into pulsating DC in rectifier circuits.

- **Doping & p–n Junction:** n-type has excess electrons (majority), p-type has excess holes (majority); joining them forms a depletion region.
- **Biasing Regions:** Forward bias narrows the depletion layer and conducts once $V_D$ reaches $\approx 0.7\text{ V}$ (Si), $0.3\text{ V}$ (Ge), or $1.2\text{ V}$ (GaAs); reverse bias widens it ($I_D \approx 0$ until breakdown at PIV/PRV).
- **Special-Purpose Diodes:** Zener diodes operate in reverse breakdown to hold a steady reference voltage $V_Z$; Schottky diodes (metal–semiconductor) switch fast with $\approx 0.25\text{ V}$ drop.
- **Half-Wave Rectifier:** Conducts on positive half-cycles only; peak output is $V_{o,\text{peak}} = V_m - V_\gamma$ (1 diode drop).
- **Full-Wave Bridge Rectifier:** Four diodes steer both half-cycles in one direction through $R_L$ (2 diode drops per half-cycle), cutting the capacitor discharge time in half and reducing ripple.

**Worked Example (Lecture-13- Semiconductor Diode.pdf (Slides 18, 24, 26–27)):** A $12\text{ V}$ (RMS), $50\text{ Hz}$ sinusoidal AC source feeds (a) a half-wave rectifier and (b) a full-wave bridge rectifier using Silicon diodes ($V_\gamma = 0.7\text{ V}$). Find the peak output voltage $V_{o,\text{peak}}$ in each case.
1. First convert RMS input to peak input voltage: $V_m = \sqrt{2}\,V_{\text{rms}} = \sqrt{2}(12) = 16.97\text{ V}$.
1. In the half-wave rectifier, current passes through 1 forward-biased Silicon diode on the positive half-cycle.
1. So $V_{o,\text{peak}}(\text{HW}) = V_m - 0.7 = 16.97 - 0.7 = 16.27\text{ V}$.
1. In the full-wave bridge rectifier, current passes through 2 forward-biased diodes in series each half-cycle, so $V_{o,\text{peak}}(\text{FW}) = V_m - 2(0.7) = 16.97 - 1.4 = 15.57\text{ V}$.
**Answer:** Half-wave $V_{o,\text{peak}} = 16.27\text{ V}$; Full-wave bridge $V_{o,\text{peak}} = 15.57\text{ V}$.

**Key Formula:** $$V_K(\text{Si}) \approx 0.7\text{ V}, \; V_K(\text{Ge}) \approx 0.3\text{ V}, \; V_{\text{HW,pk}} = V_m - V_K, \; V_{\text{FW-bridge,pk}} = V_m - 2V_K$$

**Common Mistake:** Subtracting only one $0.7\text{ V}$ drop in a 4-diode bridge rectifier (two diodes always conduct in series), or subtracting $0.7\text{ V}$ from $V_{\text{rms}}$ instead of $V_m = \sqrt{2}V_{\text{rms}}$.

---

## Practice Questions (25)
### Q1. Quiz1_QP.pdf Q1 · Power & Battery (Quiz / Lab)
(a) A $600\text{ W}$ TV runs for $4\text{ h}$ at Rs. $10/\text{kWh}$. How much money is wasted? (b) A $6\text{ V}$ flashlight battery is rated at $0.8\text{ Ah}$ with a $10\text{ h}$ lifetime. Find its current, power, and stored energy in Wh.
- **Hint:** Energy in kWh is $P(\text{kW}) \times t(\text{h})$; battery current is $\text{Ah} / t$.
- **Solution:** (a) $E = 0.6\text{ kW} \times 4\text{ h} = 2.4\text{ kWh} \implies \text{Cost} = 2.4 \times 10 = \text{Rs. } 24$.
(b) $I = \frac{0.8\text{ Ah}}{10\text{ h}} = 0.08\text{ A} = 80\text{ mA}$, $P = V I = 6 \times 0.08 = 0.48\text{ W}$, $E = 0.48\text{ W} \times 10\text{ h} = 4.8\text{ Wh}$.

### Q2. IMG-20190828-WA0001.jpg Q1–Q2 · Energy & Ah (Quiz / Lab)
(a) A $120\text{ W}$ PC runs $4\text{ h/day}$ and a $60\text{ W}$ bulb runs $8\text{ h/day}$ at Rs. $12/\text{kWh}$. Find the yearly bill ($365$ days). (b) A $160\text{ Ah}$ battery supplies $40\text{ h}$: find its max current, and how many days it lasts at $1\text{ mA}$.
- **Hint:** Add daily Wh from both appliances before converting to kWh and multiplying by $365$.
- **Solution:** (a) Daily energy $= 120(4) + 60(8) = 960\text{ Wh} = 0.96\text{ kWh/day}$. Yearly cost $= 0.96 \times 365 \times 12 = \text{Rs. } 4204.80$.
(b) $I = 160/40 = 4\text{ A}$; at $1\text{ mA}$, time $= \frac{160}{0.001} = 160{,}000\text{ h} = 6666.67\text{ days}$.

### Q3. IMG-20191106-WA0003.jpg Q1 · Light Bulbs (Quiz / Lab)
Three light bulbs rated $30\text{ W}$, $40\text{ W}$, and $50\text{ W}$ (each rated for $120\text{ V}$) are connected in (a) series and (b) parallel to a $120\text{ V}$ DC source. Find the power absorbed by each bulb and compare brightness.
- **Hint:** Find each bulb's filament resistance first from $R = V_{\text{rated}}^2 / P_{\text{rated}}$.
- **Solution:** Resistances: $R_{30} = \frac{120^2}{30} = 480\,\Omega$, $R_{40} = 360\,\Omega$, $R_{50} = 288\,\Omega$.
(a) Series: $R_{\text{total}} = 1128\,\Omega$, $I = 120/1128 = 0.1064\text{ A}$. $P = I^2 R \implies P_{30} = 5.43\text{ W}$, $P_{40} = 4.07\text{ W}$, $P_{50} = 3.26\text{ W}$ (the $30\text{ W}$ bulb has highest $R$ so it glows brightest in series).
(b) Parallel: each gets $120\text{ V}$, absorbing its rated $30\text{ W}$, $40\text{ W}$, and $50\text{ W}$ (the $50\text{ W}$ bulb glows brightest).

### Q4. Quiz1_QP.pdf Q2 · Δ–Y Bridge (Quiz / Lab)
A $24\text{ V}$ DC source feeds a bridge network: top-left $20\,\Omega$, top-right $60\,\Omega$, center horizontal $40\,\Omega$, bottom-left $10\,\Omega$, bottom-right $50\,\Omega$, and a $20\,\Omega$ resistor along the bottom wire between the two legs. Find $R_{\text{eq}}$ and source current $I_o$.
- **Hint:** Combine the $10\,\Omega$ and $20\,\Omega$ in series ($30\,\Omega$?) No—look closely: the $20\,\Omega$ bottom resistor connects the bottom of $10\,\Omega$ to the bottom of $50\,\Omega$, so $20+50=70\,\Omega$ is one arm of the lower Δ ($10, 40, 70$)! Convert that Δ to Y (or top Δ $20, 60, 40$ to Y).
- **Solution:** Combine bottom-right $50\,\Omega + 20\,\Omega = 70\,\Omega$. Convert the top Δ ($20\,\Omega, 60\,\Omega, 40\,\Omega$, sum $= 120$) to Y: $R_1 = \frac{20\times 60}{120} = 10\,\Omega$, $R_2 = \frac{20\times 40}{120} = 6.667\,\Omega$, $R_3 = \frac{60\times 40}{120} = 20\,\Omega$.
Now two legs meet in parallel: $(6.667 + 10) \parallel (20 + 70) = 16.667 \parallel 90 = 14.0625\,\Omega$.
Add $R_1$: $R_{\text{eq}} = 10 + 14.0625 = 24.0625\,\Omega$, so $I_o = \frac{24}{24.0625} = 0.9974\text{ A} = 997.4\text{ mA}$.

### Q5. ECE-Midsem_21batch.pdf Q5 · Δ–Y Bridge (Midsem / Endsem)
A $60\text{ V}$ source feeds a bridge network with $50\,\Omega$ (top-left), $150\,\Omega$ (top-right), $100\,\Omega$ (middle horizontal), $25\,\Omega$ (bottom-left), $125\,\Omega$ (bottom-right), and $50\,\Omega$ on the bottom wire. Calculate source current $I_o$.
- **Hint:** Combine $125 + 50 = 175\,\Omega$ on the bottom-right, then convert the upper Δ ($50, 150, 100$) to Y.
- **Solution:** Top Δ ($50, 150, 100$, sum $= 300$) $\to$ Y: $R_1 = \frac{50\times 150}{300} = 25\,\Omega$, $R_2 = \frac{50\times 100}{300} = 16.667\,\Omega$, $R_3 = \frac{150\times 100}{300} = 50\,\Omega$.
Parallel legs: $(16.667 + 25) \parallel (50 + 175) = 41.667 \parallel 225 = 35.15625\,\Omega$.
$R_{\text{eq}} = 25 + 35.15625 = 60.15625\,\Omega$, so $I_o = \frac{60}{60.15625} = 0.9974\text{ A}$.

### Q6. ECE-Midsem_21batch.pdf Q8 · Equivalent Resistance (Midsem / Endsem)
From terminal $a$, a $24\,\Omega$ resistor leads to node $x$. Between $x$ and $b$ are three parallel paths: $27\,\Omega$, $13.5\,\Omega$, and a right ladder where $(30\,\Omega \parallel 7.5\,\Omega)$ in series with $1.5\,\Omega$ is in parallel with $30\,\Omega$, followed by $3\,\Omega$ to $b$. Find $R_{ab}$.
- **Hint:** Reduce from the right-most parallel pair $(30\,\Omega \parallel 7.5\,\Omega)$ inward toward $x$ and $b$.
- **Solution:** Step 1: $30 \parallel 7.5 = 6\,\Omega$. Add $1.5\,\Omega \implies 7.5\,\Omega$.
Step 2: $7.5 \parallel 30 = 6\,\Omega$. Add $3\,\Omega$ to $b \implies 9\,\Omega$.
Step 3: Combine the three paths from $x$ to $b$: $27 \parallel 13.5 = 9\,\Omega$, then $9 \parallel 9 = 4.5\,\Omega$.
Step 4: $R_{ab} = 24 + 4.5 = 28.5\,\Omega$.

### Q7. Quiz1_QP.pdf Q4 · Dependent Nodal (Quiz / Lab)
A $60\text{ V}$ source ($+$ at node A, $-$ grounded) feeds a $4\,\Omega$ top-left resistor carrying $i_o$ right to node $v_1$, and a $10\,\Omega$ middle resistor to node $v_2$. A $2\,\Omega$ resistor connects $v_1$ to $v_2$, an $8\,\Omega$ resistor goes from $v_1$ to ground, and an upward dependent source $3i_o$ connects ground to $v_2$. Find $i_o$ using nodal analysis.
- **Hint:** Express $i_o = \frac{60 - v_1}{4}$ and write KCL at $v_1$ and $v_2$.
- **Solution:** At $v_1$: $\frac{v_1 - 60}{4} + \frac{v_1 - v_2}{2} + \frac{v_1}{8} = 0 \implies 7v_1 - 4v_2 = 120$.
At $v_2$: $\frac{v_2 - 60}{10} + \frac{v_2 - v_1}{2} - 3\left(\frac{60 - v_1}{4}\right) = 0 \implies 5v_1 + 12v_2 = 1020$.
Solving gives $v_1 = 53.077\text{ V}$ and $v_2 = 62.885\text{ V}$, so $i_o = \frac{60 - 53.077}{4} = 1.731\text{ A}$.

### Q8. ECE-Midsem_21batch.pdf Q7 · Nodal & Power (Midsem / Endsem)
In a grounded circuit, a $40\text{ V}$ source ($+$ top) in series with $1\,\Omega$ reaches node $v_1$. Between $v_1$ and node $V_o$ are a $5\text{ A}$ current source (pointing right) in parallel with $2\,\Omega$. From $V_o$, a $5\,\Omega$ resistor goes to ground and an $8\,\Omega$ resistor leads to a $20\text{ V}$ source ($-$ top, $+$ ground). Find $V_o$ and power dissipated in $5\,\Omega$.
- **Hint:** Watch the $20\text{ V}$ polarity: its top terminal is at $-20\text{ V}$ relative to ground.
- **Solution:** At $v_1$: $\frac{v_1 - 40}{1} + 5 + \frac{v_1 - V_o}{2} = 0 \implies 3v_1 - V_o = 70$.
At $V_o$: $\frac{V_o - v_1}{2} - 5 + \frac{V_o}{5} + \frac{V_o - (-20)}{8} = 0 \implies -20v_1 + 33V_o = 100$.
Solving: $V_o = \frac{1700}{79} = 21.52\text{ V}$, and $P_{5\Omega} = \frac{V_o^2}{5} = 92.61\text{ W}$.

### Q9. ECE-Midsem_21batch.pdf Q2 · Supernode (Midsem / Endsem)
With bottom wire grounded, nodes $v_1$, $v_2$, and $V_o$ ($v_3$) are connected as follows: $4\text{ k}\Omega$ from $v_1$ to ground, $6\text{ k}\Omega$ between $v_1$ and $v_2$, $6\text{ mA}$ upward from ground to $v_2$, $6\text{ k}\Omega$ from $v_3$ to ground, a $12\text{ V}$ source ($+$ at $v_1$, $-$ at $v_3$), and a $6\text{ V}$ source ($-$ at $v_2$, $+$ at $v_3$). Find $V_o$.
- **Hint:** Because voltage sources connect $v_1$ to $v_3$ and $v_2$ to $v_3$, all three nodes form one supernode!
- **Solution:** Supernode KCL (in mA and k$\Omega$): $\frac{v_1}{4} - 6 + \frac{v_3}{6} = 0 \implies 3v_1 + 2v_3 = 72$.
KVL constraints: $v_1 - v_3 = 12 \implies v_1 = v_3 + 12$ (and $v_3 - v_2 = 6$).
Substitute $v_1 = v_3 + 12$: $3(v_3 + 12) + 2v_3 = 72 \implies 5v_3 = 36 \implies V_o = v_3 = 7.2\text{ V}$.

### Q10. Solutions_chpater-3 Q3 · Dependent Supernode (Assignment / Tutorial)
Find node voltages $v_1, v_2, v_3$: node $v_1$ has $1\text{ A}$ upward, $4\,\Omega$ to ground, $1\,\Omega$ ($+v_o-$) to $v_3$, and a dependent $4I_o$ source ($-$ at $v_1$, $+$ at $v_2$). Node $v_2$ has $1\,\Omega$ to ground and a $2v_o$ current source entering from $v_3$. Node $v_3$ has $4\,\Omega$ to ground (carrying $I_o$ down) and $2\,\Omega$ in series with $10\text{ V}$ ($+$ at top).
- **Hint:** Write KCL for the $(v_1, v_2)$ supernode, KCL at $v_3$, and use $v_o = v_1 - v_3$, $I_o = v_3/4$.
- **Solution:** Supernode KCL: $\frac{v_1}{4} + v_2 + \frac{v_1 - v_3}{1} = 1 + 2v_o$; with $v_o = v_1 - v_3$, this gives $-3v_1 + 4v_2 + 4v_3 = 4$.
Node $v_3$ KCL: $\frac{v_3 - 10}{2} + \frac{v_3 - v_1}{1} + \frac{v_3}{4} + 2(v_1 - v_3) = 0 \implies 4v_1 - v_3 = 20$.
Supernode KVL: $v_2 - v_1 = 4I_o = v_3 \implies v_1 - v_2 + v_3 = 0$.
Solving: $v_1 = 4.97\text{ V}$, $v_2 = 4.85\text{ V}$, $v_3 = -0.12\text{ V}$.

### Q11. Quiz1_QP.pdf Q3 · Supermesh (Quiz / Lab)
Use mesh analysis to find clockwise mesh currents $i_1, i_2, i_3$: left mesh $i_1$ has an $8\text{ V}$ source ($+$ top), shares a $2\,\Omega$ resistor with top-right mesh $i_3$, and shares a downward $4\text{ A}$ source in series with $1\,\Omega$ with bottom-right mesh $i_2$. Meshes $i_3$ and $i_2$ share $4\,\Omega$, with $2\,\Omega$ on the right of $i_3$ and $8\,\Omega$ on the right of $i_2$.
- **Hint:** Form a supermesh around meshes 1 and 2, exclude the $4\text{ A}$–$1\,\Omega$ branch, and use $i_1 - i_2 = 4$.
- **Solution:** Supermesh (1,2) KVL: $-8 + 2(i_1 - i_3) + 4(i_2 - i_3) + 8i_2 = 0 \implies 2i_1 + 12i_2 - 6i_3 = 8$.
Constraint: $i_1 - i_2 = 4$.
Mesh 3 KVL: $2(i_3 - i_1) + 2i_3 + 4(i_3 - i_2) = 0 \implies -2i_1 - 4i_2 + 8i_3 = 0$.
Solving: $i_1 = 4.632\text{ A}$, $i_2 = 0.632\text{ A}$, $i_3 = 1.474\text{ A}$.

### Q12. Solution set for chapter 4 · Supermesh Q2 (Assignment / Tutorial)
Find current $i$ ($= i_1$ entering the $+$ terminal of a $30\text{ V}$ source) in a 4-mesh window: bottom-left mesh $i_1$ ($30\text{ V}, 2\,\Omega$ top, $3\,\Omega$ right), bottom-right mesh $i_2$ ($3\,\Omega$ left, $6\,\Omega$ top, $1\,\Omega$ right), top-left mesh $i_3$ ($4\,\Omega$ top, $2\,\Omega$ bottom), and top-right mesh $i_4$ ($8\,\Omega$ top, $6\,\Omega$ bottom), with an upward $4\text{ A}$ current source between $i_3$ and $i_4$.
- **Hint:** Meshes 3 and 4 share the $4\text{ A}$ source, giving $i_4 - i_3 = 4$.
- **Solution:** Mesh 1: $5i_1 - 3i_2 - 2i_3 = 30$.
Mesh 2: $-3i_1 + 10i_2 - 6i_4 = 0$.
Supermesh (3,4): $-2i_1 - 6i_2 + 6i_3 + 14i_4 = 0$, with $i_4 = i_3 + 4$.
Solving the linear system yields $i = i_1 = 8.561\text{ A}$.

### Q13. Quiz1_QP.pdf Q5 · Superposition (Quiz / Lab)
Use the superposition theorem to find current $i$ downward in the center $3\,\Omega$ resistor: left branch has $12\text{ V}$ ($+$ top), center top has $4\,\Omega$–node–$4\,\Omega$, right branch has $3\text{ A}$ upward, and an upper bypass branch has $24\text{ V}$ ($+$ left, $-$ right) in series with $8\,\Omega$.
- **Hint:** Find $i_1$ (due to $12\text{ V}$ alone), $i_2$ (due to $24\text{ V}$ alone), and $i_3$ (due to $3\text{ A}$ alone), then add them.
- **Solution:** 1) $12\text{ V}$ alone: nodal equations with $v_L = 12\text{ V}$ give $\frac{v_1-12}{4}+\frac{v_1}{3}+\frac{v_1-v_2}{4}=0$ and $\frac{v_2-v_1}{4}+\frac{v_2-12}{8}=0 \implies v_1 = 4.5\text{ V}, i_1 = 1.5\text{ A}$.
2) $24\text{ V}$ alone: $v_1 = -1.5\text{ V}, i_2 = -0.5\text{ A}$.
3) $3\text{ A}$ alone: $v_1 = 3\text{ V}, i_3 = 1\text{ A}$.
Total $i = 1.5 - 0.5 + 1 = 2\text{ A}$.

### Q14. Quiz1_QP.pdf Q6 & Lec 4(A) PP4 · Source Trans (Quiz / Lab)
Find $v_o$ across the bottom $2\,\Omega$ resistor ($+$ left, $-$ right) using source transformation: top branch has $2\text{ A}$ right $\parallel 9\,\Omega$; left branch $3\text{ A}$ down $\parallel 4\,\Omega$; right branch $6\text{ A}$ down $\parallel 5\,\Omega$; bottom branch has $2\,\Omega$ in series with $30\text{ V}$ ($+$ left, $-$ right).
- **Hint:** Transform each parallel current-source–resistor pair into a series voltage source and apply KVL to the single loop.
- **Solution:** Top: $2\text{ A} \parallel 9\,\Omega \to 18\text{ V}$ ($-$ left, $+$ right) in series with $9\,\Omega$.
Left: $3\text{ A} \parallel 4\,\Omega \to 12\text{ V}$ ($-$ top, $+$ bottom) in series with $4\,\Omega$.
Right: $6\text{ A} \parallel 5\,\Omega \to 30\text{ V}$ ($-$ top, $+$ bottom) in series with $5\,\Omega$.
Clockwise KVL: $-(4+9+5+2)i + 12 - 18 - 30 - 30 = 0 \implies 20i = -66 \implies i = -3.3\text{ A}$, so $v_o = 2i = -6.6\text{ V}$.

### Q15. ECE-Midsem_21batch.pdf Q4 · Max Power (Midsem / Endsem)
Find the value of variable resistor $R$ (connected between nodes $A$ and $B$) for maximum power transfer and that maximum power: $10\text{ V}$ ($+$ top) $\to 3\,\Omega \to A$; $12\,\Omega$ in series with $10\text{ V}$ ($-$ left, $+$ right) also spans $A$ to $B$; and node $B$ connects to ground via $5\,\Omega \parallel 16\text{ A}$ (downward).
- **Hint:** Remove $R$ between $A$ and $B$ and find $R_{Th}$ and $V_{Th} = V_A - V_B$.
- **Solution:** For $R_{Th}$ (zero $10\text{ V}, 10\text{ V}, 16\text{ A}$): $(3+5)\,\Omega$ is in parallel with $12\,\Omega$, so $R_{Th} = 8 \parallel 12 = 4.8\,\Omega$.
For $V_{Th} = V_A - V_B$: Nodal at $A$ gives $\frac{V_A-10}{3} + \frac{V_A - V_B + 10}{12} = 0$, and at $B$ gives $\frac{V_B - 10 - V_A}{12} + \frac{V_B}{5} + 16 = 0 \implies V_A = -10\text{ V}, V_B = -60\text{ V}$, so $V_{Th} = 50\text{ V}$.
Thus $R = 4.8\,\Omega$ and $P_{\max} = \frac{50^2}{4(4.8)} = 130.21\text{ W}$.

### Q16. IMG-20191106-WA0003.jpg Q3 · Thevenin (Quiz / Lab)
Using Thevenin's theorem, find the current through the $4\,\Omega$ load resistor in a loop containing $6\text{ A}$ (upward) in parallel with $16\,\Omega$, a $6\text{ V}$ source ($+$ left, $-$ right) in the top wire, the $4\,\Omega$ load on the right, and a $20\,\Omega$ resistor in the bottom return wire.
- **Hint:** Remove the $4\,\Omega$ resistor and source-transform $6\text{ A} \parallel 16\,\Omega$ into $96\text{ V}$ in series with $16\,\Omega$.
- **Solution:** With $4\,\Omega$ removed, $R_{Th} = 16 + 20 = 36\,\Omega$.
Open-circuit voltage: $6\text{ A} \parallel 16\,\Omega \to 96\text{ V}$ ($+$ top), minus the opposing $6\text{ V}$ drop gives $V_{Th} = 96 - 6 = 90\text{ V}$.
Reconnect $4\,\Omega$: $I_{4\Omega} = \frac{90}{36 + 4} = 2.25\text{ A}$.

### Q17. ECE-Midsem_21batch.pdf Q1 & Q8(a) · C & L (Midsem / Endsem)
(a) A $50\text{ V}$ DC source feeds $10\,\Omega$ to node X; from X, $30\,\Omega$ goes to $(40\,\Omega \parallel C_1)$ ($V_1$) and $20\,\Omega$ goes to $C_2$ ($V_2$). Find $V_1$ and $V_2$ at DC. (b) A $50\text{ mH}$ inductor has $i(t) = 50 e^{-100t}\text{ mA}$. Find $v_L(t)$ and stored energy at $t = 0$.
- **Hint:** (a) Capacitors are open at DC so no current enters $20\,\Omega$. (b) Use $v_L = L\frac{di}{dt}$ and $w_L = \frac{1}{2}Li^2$.
- **Solution:** (a) At DC, $C_1, C_2$ are open: $V_X = 50\frac{30+40}{10+30+40} = 43.75\text{ V} = V_2$ (zero drop across $20\,\Omega$), and $V_1 = 50\frac{40}{80} = 25\text{ V}$.
(b) $v_L(t) = (50\times 10^{-3})(-100 \times 50\times 10^{-3} e^{-100t}) = -0.25 e^{-100t}\text{ V}$; at $t=0$, $w_L(0) = \frac{1}{2}(50\times 10^{-3})(0.05)^2 = 62.5\,\mu\text{J}$.

### Q18. Solution for first order RL & RC circuits.pdf · SF RL Q4 (Assignment / Tutorial)
In a source-free RL circuit with a dependent source, a $10\,\Omega$ resistor (left), $6\text{ H}$ inductor (top, carrying current $i$ right), downward dependent current source $0.5i$ (middle), and $40\,\Omega$ resistor (right) form two loops. If $i(0) = 6\text{ A}$, find $i(t)$ for $t > 0$.
- **Hint:** Replace the $6\text{ H}$ inductor with a $1\text{ V}$ test voltage source to find $R_{Th}$ (do NOT zero the dependent source!).
- **Solution:** With a $1\text{ V}$ test source ($-$ left, $+$ right) driving test current $i$ into $10\,\Omega$: KCL at the middle node gives current in $40\,\Omega$ as $i - 0.5i = 0.5i$.
KVL around outer loop: $10i + 40(0.5i) = 1 \implies 30i = 1 \implies R_{Th} = \frac{1}{i} = 30\,\Omega$.
Time constant: $\tau = \frac{L}{R_{Th}} = \frac{6}{30} = 0.2\text{ s} \implies i(t) = 6e^{-5t}\text{ A}$ for $t > 0$.

### Q19. Lecture-6(b) PP2 & Ch-7 Step RL Q4 · Sequential Switching (Assignment / Tutorial)
A $6\text{ A}$ source $\parallel 15\,\Omega$ connects via switch $S_1$ (closes at $t = 0$) to $10\,\Omega$, $20\,\Omega$, and a $5\text{ H}$ inductor carrying $i(t)$. At $t = 2\text{ s}$, switch $S_2$ closes to short out the $20\,\Omega$ resistor. Find $i(t)$ for all $t$, and evaluate $i(1)$ and $i(3)$.
- **Hint:** Treat $0 < t < 2$ and $t > 2$ as two separate first-order intervals linked by $i(2^+) = i(2^-)$.
- **Solution:** For $t < 0$: $S_1$ is open, so $i(t) = 0$.
For $0 < t < 2$: $R_{Th1} = 15+10+20 = 45\,\Omega$, $\tau_1 = 5/45 = 1/9\text{ s}$, $i(\infty)_1 = \frac{15}{45}(6) = 2\text{ A} \implies i(t) = 2(1 - e^{-9t})\text{ A}$. Thus $i(1) = 1.9998\text{ A}$ and $i(2^-) = 2(1 - e^{-18}) \approx 2\text{ A}$.
For $t > 2$: $20\,\Omega$ is shorted, so $R_{Th2} = 25\,\Omega$, $\tau_2 = 5/25 = 0.2\text{ s}$, $i(\infty)_2 = \frac{15}{25}(6) = 3.6\text{ A}$. Thus $i(t) = 3.6 - 1.6e^{-5(t-2)}\text{ A}$, giving $i(3) = 3.6 - 1.6e^{-5} = 3.589\text{ A}$.

### Q20. ASSIGNMENT2-2 (EC1000).pdf Q1 · AC Nodal (Assignment / Tutorial)
Find phasor current $\mathbf{I}$ (downward in $-j2\,\Omega$) using nodal analysis: left source $20\angle -90^\circ\text{ V}$ in series with $2\,\Omega$ to node 1 ($-j2\,\Omega$ to ground); top branch $5\angle 0^\circ\text{ A}$ (right) in parallel with $j1\,\Omega$ to node 2; node 2 has upward dependent source $2\mathbf{I}$ and $4\,\Omega$ to ground.
- **Hint:** Substitute $\mathbf{I} = \mathbf{V}_1 / (-j2) = j0.5\mathbf{V}_1$ into the nodal equations at nodes 1 and 2.
- **Solution:** Node 1: $\frac{\mathbf{V}_1 - (-j20)}{2} + \frac{\mathbf{V}_1}{-j2} + \frac{\mathbf{V}_1 - \mathbf{V}_2}{j1} + 5 = 0$.
Node 2: $\frac{\mathbf{V}_2 - \mathbf{V}_1}{j1} - 5 - 2\left(\frac{\mathbf{V}_1}{-j2}\right) + \frac{\mathbf{V}_2}{4} = 0$.
Solving gives $\mathbf{V}_1 = 15.81\angle -46.51^\circ\text{ V}$, so $\mathbf{I} = \frac{\mathbf{V}_1}{-j2} = 7.906\angle 43.49^\circ\text{ A}$.

### Q21. Lecture-9(b) Slides 6–7 · Mixed-Freq AC (Assignment / Tutorial)
Find $v_o(t)$ across the $2\,\Omega$ resistor in a simple series circuit with a $0.25\text{ F}$ capacitor and a $2\,\Omega$ resistor driven by $v_s(t) = 6\cos(2t) + 4\sin(4t)\text{ V}$.
- **Hint:** Use superposition! Solve $\omega_1 = 2\text{ rad/s}$ and $\omega_2 = 4\text{ rad/s}$ separately, then add in time.
- **Solution:** 1) At $\omega_1 = 2\text{ rad/s}$: $Z_C = \frac{1}{j(2)(0.25)} = -j2\,\Omega$. $\mathbf{V}_1 = \frac{2}{2 - j2}(6\angle 0^\circ) = 4.243\angle 45^\circ\text{ V} \to 4.243\cos(2t + 45^\circ)\text{ V}$.
2) At $\omega_2 = 4\text{ rad/s}$: $Z_C = \frac{1}{j(4)(0.25)} = -j1\,\Omega$. Taking $4\sin(4t)$ with sine reference gives $\mathbf{V}_2 = \frac{2}{2 - j1}(4) = 3.578\angle 26.56^\circ\text{ V} \to 3.578\sin(4t + 26.56^\circ)\text{ V}$.
Total: $v_o(t) = 4.243\cos(2t + 45^\circ) + 3.578\sin(4t + 26.56^\circ)\text{ V}$.

### Q22. ASSIGNMENT2-2 (EC1000).pdf Q11 · AC Complex Power (Assignment / Tutorial)
An AC source $\mathbf{V}$ (rms) feeds a $20\,\Omega$ line resistor into two parallel branches: $(30\,\Omega \parallel -j10\,\Omega)$ and $(j20 + 60)\,\Omega$. If the $60\,\Omega$ resistor absorbs $240\text{ W}$ (take its current phase as $0^\circ$), find $\mathbf{V}$ and total complex power $\mathbf{S}$.
- **Hint:** Find $I_{60}$ from $P = I^2 R$, get the parallel node voltage $\mathbf{V}_b$, then sum branch currents.
- **Solution:** $I_{60} = \sqrt{240/60} = 2\angle 0^\circ\text{ A rms} \implies \mathbf{V}_b = 2(60 + j20) = 120 + j40\text{ V rms}$.
Branch currents: $\mathbf{I}_{30} = \frac{120+j40}{30} = 4 + j1.333\text{ A}$, $\mathbf{I}_C = \frac{120+j40}{-j10} = -4 + j12\text{ A}$.
Total current: $\mathbf{I} = 2 + (4+j1.333) + (-4+j12) = 2 + j13.333\text{ A rms}$.
Source voltage: $\mathbf{V} = \mathbf{V}_b + 20\mathbf{I} = 160 + j306.67 = 345.90\angle 62.45^\circ\text{ V rms}$.
Total complex power: $\mathbf{S} = \mathbf{V}\mathbf{I}^* = 4408.9 - j1520\text{ VA}$.

### Q23. Assignment_3.pdf Q11 · Parallel AC Loads (Assignment / Tutorial)
A $220\angle 0^\circ\text{ V}$ (rms) source supplies three parallel loads: Load 1 is $12\text{ kW}$ at $0.866\text{ pf leading}$; Load 2 is $16\text{ kW}$ at $0.85\text{ pf lagging}$; Load 3 is $20\text{ kVAR}$ at $0.6\text{ pf lagging}$. Find the source current $\mathbf{I}_o$.
- **Hint:** Compute $S = P + jQ$ for each load (remember $Q < 0$ for leading, $Q > 0$ for lagging), sum $\mathbf{S}_T$, then use $\mathbf{I}_o = (\mathbf{S}_T / \mathbf{V})^*$.
- **Solution:** Load 1: $Q_1 = -12\tan(\cos^{-1} 0.866) = -6.93\text{ kVAR} \implies \mathbf{S}_1 = 12 - j6.93\text{ kVA}$.
Load 2: $Q_2 = +16\tan(\cos^{-1} 0.85) = +9.92\text{ kVAR} \implies \mathbf{S}_2 = 16 + j9.92\text{ kVA}$.
Load 3: $P_3 = \frac{20}{\tan(\cos^{-1} 0.6)} = 15\text{ kW} \implies \mathbf{S}_3 = 15 + j20\text{ kVA}$.
Total: $\mathbf{S}_T = 43 + j22.99\text{ kVA} \implies \mathbf{I}_o = \left(\frac{43000 + j22987}{220\angle 0^\circ}\right)^* = 221.6\angle -28.13^\circ\text{ A rms}$.

### Q24. Lecture-11 Ex 1 & Lecture-12 Ex 2 · Trafo & IM (Midsem / Endsem)
(a) A $250/3000\text{ V}$, $50\text{ Hz}$ single-phase transformer has $B_m = 1.2\text{ Wb/m}^2$ and EMF/turn $= 8\text{ V}$. Find primary/secondary turns and core area. (b) A 3-phase, $50\text{ Hz}$ cage induction motor with 3 pole-pairs runs at $960\text{ rpm}$ at $40\text{ N}\cdot\text{m}$. Find $n_{\text{sync}}$, slip, rotor frequency, and mechanical power.
- **Hint:** Use $E = 4.44 f N B_m A$ for the transformer and $P = 2 \times \text{pole-pairs} = 6$ for the motor.
- **Solution:** (a) $N_1 = 250/8 \approx 32$ turns, $N_2 = 3000/8 = 375$ turns; $A = \frac{3000}{4.44 \times 50 \times 375 \times 1.2} = 0.03\text{ m}^2$.
(b) $P = 6 \implies n_{\text{sync}} = \frac{120(50)}{6} = 1000\text{ rpm}$; $s = \frac{1000 - 960}{1000} = 4\%$; $f_r = 0.04(50) = 2\text{ Hz}$; $P_{\text{out}} = \tau\omega_m = 40 \times \frac{2\pi(960)}{60} = 4.02\text{ kW}$.

### Q25. Lecture-13 Slides 24–27 · Diodes & Rectifiers (Quiz / Lab)
(a) Compare Silicon, Germanium, and Schottky forward voltage drops. (b) A $20\text{ V}$ (RMS) AC source feeds a full-wave Silicon bridge rectifier ($V_K = 0.7\text{ V}$) with a reservoir capacitor. Find the peak output voltage across $R_L$ and explain the capacitor's role.
- **Hint:** Convert $V_{\text{rms}}$ to peak $V_m = \sqrt{2}V_{\text{rms}}$ and remember 2 bridge diodes conduct simultaneously.
- **Solution:** (a) Typical forward conduction drops: Silicon $\approx 0.7\text{ V}$, Germanium $\approx 0.3\text{ V}$, Schottky $\approx 0.25\text{ V}$ (fastest switching).
(b) $V_m = 20\sqrt{2} = 28.28\text{ V}$. Two diodes conduct in series each half-cycle, so $V_{o,\text{peak}} = 28.28 - 2(0.7) = 26.88\text{ V}$. The reservoir capacitor charges to the peak and supplies $R_L$ between peaks to reduce output ripple.
