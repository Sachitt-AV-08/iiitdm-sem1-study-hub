# End-Semester Exam Study Guide — Calculus (`MA1000`)

**Course:** Calculus (`MA1000`) — IIITDM Kancheepuram  
**Time Horizon:** Designed for rapid, high-yield mastery in **< 4 days**  
**Synthesized from:** Lecture notes (`01 Sequences, Series and Power Series` through `05 Partial Derivatives`, `Sequences.pdf`), `Assignment 1 & 2`, `Problem Sets 1–7`, `Tutorial on Module 1 & 3`, `Rolle and Cauchy Theorem Problems`, `Fundamental Theorem of Calculus.pdf`, `Quotient rule proof.pdf`, and Previous Year Papers (`Midsem_21`, `CAL-Midsem_21batch`, `Endsem_21`, `Midsem Dec 2022`, `Endsem Feb 2023`, `MAT104T` Quiz/Midsem).

---

## 1. Exam Blueprint & High-Yield Weightage

Based on the IIITDM Kancheepuram end-semester (`Endsem_21` — 40 marks, `Endsem Feb 2023` — 12 questions) and mid-semester papers, `MA1000` exams consistently test **exact theorem statements, rigorous proofs, counterexamples, and clean step-by-step computations**:

| Module | Topic Area | Typical Exam Questions | Priority |
| :--- | :--- | :--- | :---: |
| **1A** | **Sequences & Convergence** | $\epsilon$-$N$ proofs, Monotone Convergence Theorem (recursive sequences), Squeeze/Special limits, Subsequences & oscillation, Cauchy's 1st & 2nd theorems | High |
| **1B** | **Infinite Series** | $n$-th term divergence ($\sin(1/n)$ vs $\cos(1/n)$), Integral/Comparison/Ratio/Root tests (prime-indexed series), Leibniz alternating error bounds ($|R_n| \le b_{n+1}$), Conditional vs Absolute | High |
| **1C** | **Power & Taylor Series** | Convergence Theorem proof, Radius & Interval of Convergence (with endpoints!), Term-by-term differentiation/integration ($\tan^{-1}x$, $\ln(1+x)$), Maclaurin ($\sqrt{1+x}$, $\sin^2 x$, $1/(1+x^2)$) | High |
| **2** | **1D Limits & Continuity** | $\epsilon$-$\delta$ proofs (linear & quadratic), Removable/Jump/Infinite/Oscillating discontinuities, Dirichlet-type pointwise continuity, IVT root existence | Very High |
| **3** | **Differentiation & MVTs** | Differentiability $\Rightarrow$ Continuity (and counterexamples $x\sin(1/x)$, $x^2\sin(1/x)$), Quotient Rule proof, Rolle's / Lagrange MVT / Cauchy MVT proofs & inequalities, Critical points ($f'=0$ or **DNE**) | Very High |
| **4** | **Riemann Integration & FTC** | $L(P,f) \le L(P^*,f) \le U(P^*,f) \le U(P,f)$, Explicit equal-partition $U(P,f)-L(P,f) < \epsilon$ proof, Limit of Riemann sums, FTC Part 1 & 2 proofs, Leibniz rule | Very High |
| **5** | **Multivariable Calculus** | Open/Closed/Bounded sets in $\mathbb{R}^2$, Two-Path Test & 2D $\epsilon$-$\delta$ limits, Partial derivatives at $(0,0)$, Differentiability vs Continuity, Chain Rule, Directional Derivative & Gradient ($\nabla f$) | Very High |

---

## 2. Module 1: Sequences, Infinite Series & Power Series

### 2.1 Sequences: Core Definitions & Theorems
1. **$\epsilon$-$N$ Definition of Convergence:** A sequence $\{a_n\}$ converges to $L$ ($\lim_{n\to\infty} a_n = L$) if for every $\epsilon > 0$, there exists $N \in \mathbb{N}$ such that for all $n \ge N$, $|a_n - L| < \epsilon$.
   - *Proof Template:* Start with $|a_n - L| < \text{simple upper bound in } n$. Set that bound $< \epsilon$, solve for $n > g(\epsilon)$, and explicitly write *"Choose $N = \lceil g(\epsilon) \rceil + 1$."*
2. **Limit Laws & Squeeze Theorem:** If $a_n \to A$ and $b_n \to B$, then $a_n \pm b_n \to A \pm B$, $a_n b_n \to AB$, and $a_n/b_n \to A/B$ ($B \ne 0$). If $a_n \le c_n \le b_n$ for $n \ge N_0$ and $\lim a_n = \lim b_n = L$, then $\lim c_n = L$.
3. **7 Must-Know Special Limits:**
   - $\lim_{n\to\infty} \frac{\ln n}{n} = 0$
   - $\lim_{n\to\infty} n^{1/n} = 1$
   - $\lim_{n\to\infty} x^{1/n} = 1 \quad (x > 0)$
   - $\lim_{n\to\infty} x^n = 0 \quad (|x| < 1)$
   - $\lim_{n\to\infty} \left(1 + \frac{x}{n}\right)^n = e^x \quad (\text{any } x \in \mathbb{R})$
   - $\lim_{n\to\infty} \frac{x^n}{n!} = 0 \quad (\text{any } x \in \mathbb{R})$
   - $\lim_{n\to\infty} (n!)^{1/n^2} = 1 \quad \text{(Proof via } 1 \le (n!)^{1/n^2} \le (n^n)^{1/n^2} = n^{1/n} \to 1 \text{)}$
4. **Monotone Convergence Theorem (MCT):** Every bounded monotonic sequence converges (increasing + bounded above $\Rightarrow$ converges to $\sup\{a_n\}$; decreasing + bounded below $\Rightarrow$ converges to $\inf\{a_n\}$).
5. **Subsequences & Oscillation (`Sequences.pdf`):**
   - $\{a_n\}$ converges to $L$ $\iff$ **every** subsequence converges to $L$.
   - *How to prove divergence:* Find **two subsequences converging to different limits** (e.g., $a_{2k}$ and $a_{2k+1}$), OR show $\{a_n\}$ is unbounded.
   - **Bolzano-Weierstrass Theorem:** Every bounded sequence has a convergent subsequence.
   - A sequence converges iff it is bounded and has a **unique limit point**.
6. **Cauchy's 1st & 2nd Theorems on Limits (`Sequences.pdf`):**
   - *1st Theorem (Cesàro Mean):* If $a_n \to L$, then $\frac{a_1 + a_2 + \dots + a_n}{n} \to L$. *(Converse is false: $a_n = (-1)^n$ oscillates, yet Cesàro mean $\to 0$).*
   - *2nd Theorem:* If $a_n > 0$ and $\lim \frac{a_{n+1}}{a_n} = L$, then $\lim (a_n)^{1/n} = L$. *(Note: $(a_n)^{1/n}$ can converge even when $a_{n+1}/a_n$ fails to have a limit!)*

### 2.2 Infinite Series: Complete Test Decision Table

First check: **Does $\lim_{n\to\infty} a_n = 0$?** If NOT (or DNE), $\sum a_n$ **diverges immediately** by the **$n$-th Term Test**. *(Trap: $\lim a_n = 0$ does NOT prove convergence — e.g., $\sum 1/n$ diverges!)*

| Test | Applies To | Condition for Convergence | Condition for Divergence | Exam Notes / Traps |
| :--- | :--- | :--- | :--- | :--- |
| **Geometric** | $\sum_{n=0}^\infty a r^n$ | $|r| < 1$; Sum $= \frac{a}{1-r}$ | $|r| \ge 1$ ($a \ne 0$) | Always check the starting index ($n=0$ vs $n=1$)! |
| **Telescoping** | $\sum (b_n - b_{n+1})$ | $\lim_{N\to\infty} S_N$ exists finitely | $\lim_{N\to\infty} S_N$ DNE / $\infty$ | Write $S_N$ explicitly; never cancel terms without keeping tail terms! |
| **$p$-Series** | $\sum_{n=1}^\infty \frac{1}{n^p}$ | $p > 1$ | $p \le 1$ | $p=1$ is Harmonic series (diverges). |
| **Integral Test** | $a_n = f(n) \ge 0$, $f$ continuous, positive, **decreasing** | $\int_N^\infty f(x)\,dx < \infty$ | $\int_N^\infty f(x)\,dx = \infty$ | Verify decreasing ($f'(x) \le 0$). Ideal for $\sum \frac{1}{n(\ln n)^p}$. |
| **Direct Comparison** | $0 \le a_n \le b_n$ | $\sum b_n$ conv $\Rightarrow$ $\sum a_n$ conv | $\sum a_n$ div $\Rightarrow$ $\sum b_n$ div | Direction of inequality matters! |
| **Limit Comparison (LCT)** | $a_n > 0, b_n > 0$ | $\lim \frac{a_n}{b_n} = c \in (0,\infty)$ $\Rightarrow$ both behave alike; if $c=0$ & $\sum b_n$ conv $\Rightarrow \sum a_n$ conv | If $c=\infty$ & $\sum b_n$ div $\Rightarrow \sum a_n$ div | Use $\sin(x) \sim x$, $\tan^{-1}(1/n) \sim 1/n$, rational highest powers. |
| **Ratio Test** | Factorials $n!$, $a^n$ | $L = \lim \left|\frac{a_{n+1}}{a_n}\right| < 1$ (Abs. Conv.) | $L > 1$ or $L = \infty$ | **$L = 1$ is inconclusive** (always inconclusive for algebraic/rational $p$-series). |
| **Root Test** | Powers $(\dots)^n$, piecewise odd/even/prime formulas | $L = \lim_{n\to\infty} |a_n|^{1/n} < 1$ (or $\limsup |a_n|^{1/n} < 1$) | $L > 1$ or $L = \infty$ | Stronger than Ratio Test; solves non-uniform terms like prime vs non-prime! |
| **Alternating Series (Leibniz)** | $\sum (-1)^{n-1} b_n$ ($b_n > 0$) | (1) $b_{n+1} \le b_n$ eventually, AND (2) $\lim b_n = 0$ | If $\lim b_n \ne 0$ ($n$-th term test) | **Error bound:** $|S - S_n| = |R_n| \le b_{n+1}$ (if monotonic from start). |

### 2.3 Absolute vs. Conditional Convergence
- **Absolutely Convergent:** $\sum |a_n|$ converges ($\Rightarrow \sum a_n$ also converges). Safe under arbitrary rearrangement!
- **Conditionally Convergent:** $\sum a_n$ converges, but $\sum |a_n|$ diverges (classic example: $\sum_{n=1}^\infty \frac{(-1)^{n-1}}{n^p}$ for $0 < p \le 1$).

### 2.4 Power Series, Radius of Convergence & Taylor/Maclaurin Series
1. **Convergence Theorem for $\sum_{n=0}^\infty c_n (x - a)^n$:** Exactly three possibilities:
   1. Converges for **all** $x \in \mathbb{R}$ ($R = \infty$).
   2. Converges **only** at $x = a$ ($R = 0$).
   3. There exists $R > 0$ such that the series converges **absolutely** for $|x - a| < R$ and **diverges** for $|x - a| > R$.
   - **CRITICAL:** The endpoints $x = a - R$ and $x = a + R$ MUST always be tested **individually** (Ratio/Root gives $L=1$ at endpoints).
2. **Term-by-Term Differentiation & Integration:** Inside $(a-R, a+R)$, a power series can be differentiated and integrated term by term **with the same radius $R$** *(though endpoint convergence may change — differentiating can lose an endpoint; integrating can gain one!)*.
3. **Standard Maclaurin Expansions (Memorize with Interval!):**
   - $\frac{1}{1 - x} = \sum_{n=0}^\infty x^n \quad (|x| < 1)$
   - $\frac{1}{(1-x)^2} = \sum_{n=1}^\infty n x^{n-1} = \sum_{n=0}^\infty (n+1)x^n \quad (|x| < 1)$
   - $e^x = \sum_{n=0}^\infty \frac{x^n}{n!} \quad (x \in \mathbb{R})$
   - $\sin x = \sum_{n=0}^\infty \frac{(-1)^n x^{2n+1}}{(2n+1)!} \quad (x \in \mathbb{R})$
   - $\cos x = \sum_{n=0}^\infty \frac{(-1)^n x^{2n}}{(2n)!} \quad (x \in \mathbb{R})$
   - $\ln(1 + x) = \sum_{n=1}^\infty \frac{(-1)^{n-1} x^n}{n} \quad (-1 < x \le 1)$
   - $\tan^{-1} x = \sum_{n=0}^\infty \frac{(-1)^n x^{2n+1}}{2n+1} \quad (-1 \le x \le 1)$
   - **Binomial:** $(1+x)^m = 1 + mx + \frac{m(m-1)}{2!}x^2 + \frac{m(m-1)(m-2)}{3!}x^3 + \dots \quad (|x| < 1)$
4. **Taylor's Uniqueness Warning:** $f(x) = e^{-1/x^2}$ ($x \ne 0$), $f(0)=0$ is $C^\infty$ at $0$ with $f^{(n)}(0) = 0$ for ALL $n \ge 0$. Its Maclaurin series is identically $0$, which equals $f(x)$ **only at $x=0$**!

---

## 3. Module 2: Limits & Continuity (Single Variable)

### 3.1 Formal $\epsilon$-$\delta$ Definition & Proof Recipe
$\lim_{x\to c} f(x) = L$ means: $\forall \epsilon > 0,\ \exists \delta > 0$ such that whenever $0 < |x - c| < \delta$, we have $|f(x) - L| < \epsilon$.

**Two-Step $\epsilon$-$\delta$ Exam Recipe (For Quadratic/Nonlinear $f(x)$ like $x^2 \to 4$ as $x \to 2$):**
1. Factor $|f(x) - L| = |x - c|\cdot |g(x)|$. For $x^2 - 4$: $|x-2|\cdot |x+2|$.
2. **Pre-restrict $\delta \le 1$** so $|x - 2| < 1 \Rightarrow 1 < x < 3 \Rightarrow |x + 2| < 5$.
3. Then $|x^2 - 4| < 5|x - 2| < \epsilon$ whenever $|x - 2| < \epsilon/5$.
4. Write: *"Take $\delta = \min\left(1, \frac{\epsilon}{5}\right)$."* Then verify: $0 < |x-2| < \delta \Rightarrow |x+2|<5$ and $|x-2|<\epsilon/5 \Rightarrow |x^2-4| < 5(\epsilon/5) = \epsilon$.

### 3.2 Continuity & Types of Discontinuities
$f$ is continuous at $c$ iff: (1) $f(c)$ exists, (2) $\lim_{x\to c} f(x)$ exists, and (3) $\lim_{x\to c} f(x) = f(c)$.

1. **Removable Discontinuity:** $\lim_{x\to c} f(x)$ exists, but $f(c)$ is undefined or $\ne L$. *(Fixable by Continuous Extension).*
2. **Jump Discontinuity:** One-sided limits exist finitely, but $\lim_{x\to c^-} f(x) \ne \lim_{x\to c^+} f(x)$.
3. **Infinite Discontinuity:** At least one one-sided limit is $\pm \infty$.
4. **Oscillating Discontinuity:** $\sin(1/x)$ as $x \to 0$ (oscillates infinitely without approaching any value).

### 3.3 Pointwise Continuity Trap (Dirichlet Variant) & IVT
- **Classic IIITDM Question (`Assignment 2`, `Midsem Dec 2022`):** $f(x) = x$ if $x \in \mathbb{Q}$, and $f(x) = 0$ if $x \notin \mathbb{Q}$.
  - At $c \ne 0$: sequences $q_n \in \mathbb{Q} \to c$ give $f(q_n) = q_n \to c$, while $r_n \notin \mathbb{Q} \to c$ give $f(r_n) = 0 \to 0 \ne c$ $\Rightarrow$ **Discontinuous everywhere except $0$**.
  - At $c = 0$: $|f(x) - 0| \le |x| \to 0$ as $x \to 0$ $\Rightarrow$ **Continuous ONLY at $x = 0$**!
- **Intermediate Value Theorem (IVT):** If $f$ is continuous on closed $[a,b]$ and $y_0$ lies between $f(a)$ and $f(b)$, there exists $c \in [a,b]$ such that $f(c) = y_0$.
  - *Root Proof Template:* Check $f$ continuous on $[a,b]$, evaluate $f(a)$ and $f(b)$ of opposite signs, invoke IVT $\Rightarrow$ at least one root in $(a,b)$. (Pair with $f'(x) > 0$ or Rolle's theorem for *uniqueness*!)

---

## 4. Module 3: Differentiation & Mean Value Theorems

### 4.1 Differentiability & Counterexamples
- **Definition:** $f'(c) = \lim_{h\to 0} \frac{f(c+h) - f(c)}{h}$ exists **finitely** ($RHD = LHD$).
- **Theorem:** $f$ differentiable at $c \implies f$ continuous at $c$.
  - *Proof:* $f(c+h) - f(c) = \frac{f(c+h)-f(c)}{h} \cdot h \to f'(c) \cdot 0 = 0$.
- **Important Exam Counterexamples:**
  - **Continuous everywhere, not differentiable at $0$:** $f(x) = |x|$ ($RHD = 1 \ne LHD = -1$), or $f(x) = x^{1/3}$ (vertical tangent, limit $= \infty$), or $f(x) = x \sin(1/x)$ ($f(0)=0$: continuous at $0$ by Squeeze, but difference quotient $= \sin(1/h)$ oscillates!).
  - **Differentiable at $0$ (including $f'(0)=0$), derivative NOT continuous at $0$:** $f(x) = x^2 \sin(1/x)$ ($f(0)=0$). Here $\frac{f(h)-0}{h} = h \sin(1/h) \to 0 \Rightarrow f'(0)=0$, while for $x \ne 0$, $f'(x) = 2x\sin(1/x) - \cos(1/x)$ has no limit as $x \to 0$!
- **Darboux's Theorem:** Derivatives obey the Intermediate Value Property (even if $f'$ is not continuous, $f'$ cannot have a jump discontinuity).

### 4.2 Critical Points & Mean Value Theorems
- **Critical Point Trap (`Endsem_21` Q6):** An interior point $c$ of domain $D$ is a **critical point** of $f$ if **$f'(c) = 0$ OR $f'(c)$ does not exist**! Never forget points where $f'$ is undefined (cusps/corners/vertical tangents)!
- **Extreme Value Theorem (EVT):** Continuous $f$ on closed bounded $[a,b]$ attains both absolute maximum and absolute minimum on $[a,b]$ (check critical points in $(a,b)$ AND endpoints $a, b$).
- **Fermat's / First Derivative Theorem:** If $f$ has a local extremum at interior $c$ and $f'(c)$ exists, then $f'(c) = 0$.
- **Rolle's Theorem:** If (1) $f$ continuous on $[a,b]$, (2) $f$ differentiable on $(a,b)$, and (3) $f(a) = f(b)$, then $\exists c \in (a,b)$ with $f'(c) = 0$.
- **Lagrange Mean Value Theorem (LMVT):** If $f$ continuous on $[a,b]$ and differentiable on $(a,b)$, then $\exists c \in (a,b)$ such that
  $$f'(c) = \frac{f(b) - f(a)}{b - a}$$
  *Corollary:* If $f'(x) = 0$ on $(a,b)$, $f$ is constant on $(a,b)$. If $f'(x) = g'(x)$ on $(a,b)$, $f(x) = g(x) + C$.
- **Cauchy Mean Value Theorem (CMVT):** If $f, g$ continuous on $[a,b]$, differentiable on $(a,b)$, and $g'(x) \ne 0$ on $(a,b)$, then $\exists c \in (a,b)$ such that
  $$\frac{f'(c)}{g'(c)} = \frac{f(b) - f(a)}{g(b) - g(a)}$$
  *(Proof trick: Apply Rolle's Theorem to $h(x) = [f(b)-f(a)]g(x) - [g(b)-g(a)]f(x)$!)*

---

## 5. Module 4: Riemann Integration & FTC

### 5.1 Partitions, Darboux Sums & Integrability Criterion
- For bounded $f: [a,b] \to \mathbb{R}$ and partition $P = \{a = x_0 < x_1 < \dots < x_n = b\}$:
  $$m_i = \inf_{x\in[x_{i-1},x_i]} f(x), \quad M_i = \sup_{x\in[x_{i-1},x_i]} f(x), \quad \Delta x_i = x_i - x_{i-1}$$
  $$L(P,f) = \sum_{i=1}^n m_i \Delta x_i, \qquad U(P,f) = \sum_{i=1}^n M_i \Delta x_i$$
- **Refinement Property:** If $P^* \supset P$ is a refinement, then:
  $$L(P,f) \le L(P^*,f) \le U(P^*,f) \le U(P,f)$$
- For any two partitions $P_1, P_2$, taking common refinement $P^* = P_1 \cup P_2$ proves $L(P_1,f) \le U(P_2,f)$. Thus:
  $$\underline{\int_a^b} f(x)\,dx = \sup_P L(P,f) \le \inf_P U(P,f) = \overline{\int_a^b} f(x)\,dx$$
- **Riemann / Darboux Criterion:** $f \in \mathcal{R}[a,b]$ $\iff$ for every $\epsilon > 0$, there exists a partition $P$ such that
  $$U(P,f) - L(P,f) = \sum_{i=1}^n (M_i - m_i)\Delta x_i < \epsilon$$
- **Key Theorems & Counterexamples:**
  - Every **continuous** function on $[a,b]$ is integrable (via uniform continuity on $[a,b]$).
  - Every **monotonic** function on $[a,b]$ is integrable (telescoping $\sum (M_i - m_i)\Delta x_i \le \frac{b-a}{n}|f(b)-f(a)|$).
  - Every bounded function on $[a,b]$ continuous except at **finitely many points** is integrable.
  - **Dirichlet Function ($1$ on $\mathbb{Q}$, $0$ on $\mathbb{R}\setminus\mathbb{Q}$):** On $[a,b]$, every subinterval contains both rationals and irrationals, so $M_i = 1, m_i = 0 \implies U(P,f) = b-a \ne L(P,f) = 0 \implies$ **Not Riemann integrable**!
- **Limit of Riemann Sums Formula:**
  $$\lim_{n\to\infty} \frac{b-a}{n} \sum_{k=1}^n f\!\left(a + k\frac{b-a}{n}\right) = \int_a^b f(x)\,dx \quad \text{and specially on } [0,1]:\quad \lim_{n\to\infty}\frac{1}{n}\sum_{k=1}^n f\!\left(\frac{k}{n}\right) = \int_0^1 f(x)\,dx$$

### 5.2 Fundamental Theorem of Calculus (FTC)
- **FTC Part 1 (Differentiation of Integral):** If $f$ is continuous on $[a,b]$ and $F(x) = \int_a^x f(t)\,dt$, then $F$ is continuous on $[a,b]$, differentiable on $(a,b)$, and $F'(x) = f(x)$.
  - **General Leibniz Chain Form:**
    $$\frac{d}{dx} \int_{g(x)}^{h(x)} f(t)\,dt = f(h(x))\,h'(x) - f(g(x))\,g'(x)$$
- **FTC Part 2 (Evaluation):** If $f$ is continuous on $[a,b]$ and $F$ is any antiderivative of $f$ ($F'(x)=f(x)$), then $\int_a^b f(x)\,dx = F(b) - F(a)$.

---

## 6. Module 5: Multivariable Functions, Limits & Partial Derivatives

### 6.1 Topology of $\mathbb{R}^2$ (Open, Closed & Bounded Sets)
- **$\delta$-Disk:** $N_\delta(x_0, y_0) = \{(x,y) \in \mathbb{R}^2 : (x-x_0)^2 + (y-y_0)^2 < \delta^2\}$.
- **Interior Point:** $\exists$ an open disk centered at $P$ lying **entirely inside** $S$.
- **Boundary Point:** **Every** open disk centered at $P$ contains at least one point inside $S$ AND at least one point outside $S$ ($S^c$). *(Note: a boundary point need NOT belong to $S$!)*
- **Open Set:** Every point in $S$ is an interior point (contains none of its boundary points).
- **Closed Set:** $S$ contains **all** of its boundary points (equivalently, its complement $\mathbb{R}^2 \setminus S$ is open).
- **Bounded vs Unbounded:** Bounded if $S$ lies inside some disk of finite radius centered at $(0,0)$.
- **CRITICAL EXAM TRAP (`Endsem_21` Q9(b)):** Is $S = \{(x,y) \in \mathbb{R}^2 : x^2 + y^2 = 1,\ y > 0\}$ open, closed, or neither?
  - **NOT open:** Every point $(x_0,y_0)$ on the semicircle has points $(x,y)$ arbitrarily close to it with $x^2+y^2 \ne 1$, so NO 2D open disk around it lies inside $S$.
  - **NOT closed:** The boundary points $(1,0)$ and $(-1,0)$ satisfy every open disk intersecting both $S$ and $S^c$, yet $(1,0), (-1,0) \notin S$ because $y=0 \not> 0$!
  - **Conclusion:** $S$ is **neither open nor closed** (though it is bounded)!

### 6.2 Limits & Continuity in $\mathbb{R}^2$
- **To prove limit DNE (Two-Path Test):** Approach $(x_0,y_0)$ along lines $y = mx$, parabolas $y = kx^2$, or curves $x = ky^2$. Different limits along two paths $\implies$ limit DNE!
- **To prove limit EXISTS ($\epsilon$-$\delta$ / Squeeze in $\mathbb{R}^2$):** Use polar/inequalities:
  $$|x| \le \sqrt{x^2+y^2}, \qquad |y| \le \sqrt{x^2+y^2}, \qquad |xy| \le \frac{1}{2}(x^2+y^2)$$

### 6.3 Partial Derivatives, Differentiability, Chain Rule & Gradients
- **Partial Derivatives at $(a,b)$ (ALWAYS use limits for piecewise functions at $(0,0)$!):**
  $$f_x(a,b) = \lim_{h\to 0} \frac{f(a+h,b) - f(a,b)}{h}, \qquad f_y(a,b) = \lim_{k\to 0} \frac{f(a,b+k) - f(a,b)}{k}$$
- **Clairaut's (Mixed Derivative) Theorem:** If $f, f_x, f_y, f_{xy}, f_{yx}$ are defined on an open disk containing $(a,b)$ and are continuous at $(a,b)$, then $f_{xy}(a,b) = f_{yx}(a,b)$.
- **2D Differentiability vs Continuity vs Partial Derivatives:**
  - $f$ **differentiable** at $(a,b)$ $\implies$ $f$ is continuous at $(a,b)$ AND $f_x(a,b), f_y(a,b)$ exist.
  - **Sufficient condition:** If $f_x$ and $f_y$ exist near $(a,b)$ and are **continuous** at $(a,b)$, then $f$ is differentiable at $(a,b)$.
  - **Warning:** Existence of $f_x(0,0)$ and $f_y(0,0)$ alone does NOT imply even continuity! *(Example: $f(x,y) = 1$ if $xy=0$, $0$ otherwise — $f_x(0,0)=f_y(0,0)=0$, NOT continuous at $(0,0)$!)*
- **Directional Derivative & Gradient:**
  $$\nabla f = f_x \hat{\mathbf{i}} + f_y \hat{\mathbf{j}} + f_z \hat{\mathbf{k}}, \qquad D_{\hat{\mathbf{u}}} f(P) = \nabla f(P) \cdot \hat{\mathbf{u}} \quad (\text{MUST normalize } \hat{\mathbf{u}} = \mathbf{v}/\|\mathbf{v}\|!)$$
  - **Max rate of increase:** $\|\nabla f(P)\|$ in direction of $\nabla f(P)$.
  - **Tangent plane to $z = f(x,y)$ at $(x_0,y_0,z_0)$:** $z - z_0 = f_x(x_0,y_0)(x-x_0) + f_y(x_0,y_0)(y-y_0)$.

---

## 7. Previous-Year Papers & Assignment Problems (Fully Solved)

### Part A: Previous-Year Endsem & Midsem Solutions

**Q1 (`Midsem_21`, `CAL-Midsem_21batch`):** Define a convergent sequence using $\epsilon$-$N$, and prove directly from the definition that $\lim_{n\to\infty} \frac{2n+1}{n+3} = 2$.  
**Solution:**
Let $\epsilon > 0$. Consider:
$$\left|\frac{2n+1}{n+3} - 2\right| = \left|\frac{2n+1 - 2n - 6}{n+3}\right| = \frac{5}{n+3}$$
We need $\frac{5}{n+3} < \epsilon \iff n + 3 > \frac{5}{\epsilon} \iff n > \frac{5}{\epsilon} - 3$. Choose $N = \max\left(1, \left\lceil \frac{5}{\epsilon} \right\rceil\right)$. Then for all $n \ge N$, $n+3 > n \ge \frac{5}{\epsilon} \implies \left|\frac{2n+1}{n+3} - 2\right| < \epsilon$. Thus $\lim_{n\to\infty} \frac{2n+1}{n+3} = 2$.

---

**Q2 (`CAL-Midsem_21batch` Q2 & `Endsem_21` style):** Prove that $a_1 = 2,\ a_{n+1} = \frac{1}{2}\left(a_n + \frac{10}{a_n}\right)$ converges and find its limit. *(Similarly `Assignment 1`: $a_{n+1}=\sqrt{6+a_n}$.)*  
**Solution:**
1. Clearly $a_n > 0$ for all $n$ (by induction).
2. **Bounded below:** By AM–GM, for $n \ge 1$,
   $$a_{n+1} = \frac{1}{2}\left(a_n + \frac{10}{a_n}\right) \ge \sqrt{a_n \cdot \frac{10}{a_n}} = \sqrt{10} \implies a_n \ge \sqrt{10} \text{ for all } n \ge 2.$$
   *(Wait: check $a_1 = 2 < \sqrt{10}$, then $a_2 = \frac{1}{2}(2 + 5) = 3.5 > \sqrt{10} \approx 3.162$!)*
3. **Monotonicity (for $n \ge 2$):** Since $a_n \ge \sqrt{10} \implies a_n^2 \ge 10$:
   $$a_{n+1} - a_n = \frac{1}{2}\left(a_n + \frac{10}{a_n}\right) - a_n = \frac{10 - a_n^2}{2a_n} \le 0 \quad (n \ge 2).$$
   Thus $\{a_n\}_{n\ge 2}$ is decreasing and bounded below by $\sqrt{10}$.
4. **Limit:** By MCT, $a_n \to L > 0$. Taking limits in the recurrence: $L = \frac{1}{2}(L + 10/L) \implies L^2 = 10 \implies L = \sqrt{10}$.

---

**Q3 (`CAL-Midsem_21batch` Q5):** Test convergence of $\sum_{n=1}^\infty \sin\!\left(\frac{1}{n}\right)$ and $\sum_{n=1}^\infty \cos\!\left(\frac{1}{n}\right)$.  
**Solution:**
- **For $\sum \cos(1/n)$:** $\lim_{n\to\infty} \cos(1/n) = \cos(0) = 1 \ne 0$. By the **$n$-th Term Test**, it **diverges**.
- **For $\sum \sin(1/n)$:** All terms positive for $n \ge 1$. Compare with $b_n = \frac{1}{n}$ using Limit Comparison Test:
  $$\lim_{n\to\infty} \frac{\sin(1/n)}{1/n} = \lim_{t\to 0^+} \frac{\sin t}{t} = 1 \in (0,\infty).$$
  Since $\sum \frac{1}{n}$ diverges (harmonic series), $\sum \sin(1/n)$ **diverges**.

---

**Q4 (`CAL-Midsem_21batch` Q6):** Test convergence of $\sum_{n=1}^\infty a_n$ where $a_n = \frac{n}{2^n}$ if $n$ is prime, and $a_n = \frac{1}{3^n}$ if $n$ is not prime.  
**Solution:**
Here Ratio Test fails/oscillates wildly, so apply the **Root Test ($\limsup$)**:
- For prime $n$: $a_n^{1/n} = \frac{n^{1/n}}{2} \to \frac{1}{2}$ (as $n^{1/n} \to 1$).
- For non-prime $n$: $a_n^{1/n} = \frac{1}{3}$.
- Thus $\limsup_{n\to\infty} (a_n)^{1/n} = \max\left(\frac{1}{2}, \frac{1}{3}\right) = \frac{1}{2} < 1$.
By the Root Test, $\sum a_n$ **converges**.

---

**Q5 (`Endsem_21` Q1, 4 marks):** Evaluate $\sum_{n=1}^\infty \frac{2n+1}{n^2(n+1)^2}$ OR test convergence of $\sum_{n=1}^\infty \frac{x^n}{n^{10}}$ (`CAL-Midsem_21batch` Q9).  
**Solution:**
1. **Telescoping Sum:** Notice $\frac{2n+1}{n^2(n+1)^2} = \frac{(n+1)^2 - n^2}{n^2(n+1)^2} = \frac{1}{n^2} - \frac{1}{(n+1)^2}$.
   Partial sum $S_N = 1 - \frac{1}{(N+1)^2} \implies \sum_{n=1}^\infty \frac{2n+1}{n^2(n+1)^2} = \lim_{N\to\infty} S_N = \mathbf{1}$.
2. **Power Series $\sum \frac{x^n}{n^{10}}$:** By Ratio Test:
   $$L = \lim_{n\to\infty} \left|\frac{x^{n+1}/(n+1)^{10}}{x^n/n^{10}}\right| = |x| \lim_{n\to\infty} \left(\frac{n}{n+1}\right)^{10} = |x|.$$
   Converges for $|x| < 1$ ($R = 1$). Test endpoints:
   - At $x = 1$: $\sum \frac{1}{n^{10}}$ converges ($p$-series, $p = 10 > 1$).
   - At $x = -1$: $\sum \frac{(-1)^n}{n^{10}}$ converges absolutely ($\sum 1/n^{10}$ converges).
   **Interval of Convergence:** $[-1, 1]$.

---

**Q6 (`Problem Set 3` & `Endsem Feb 2023` style — Alternating Error Bound):** Estimate $\sum_{n=1}^\infty \frac{(-1)^{n+1} n}{10^n}$ to 4 decimal places (error $< 0.5 \times 10^{-4}$), and determine how many terms of $\sum_{n=1}^\infty \frac{(-1)^{n-1}}{n^3}$ are needed for error $< 10^{-4}$.  
**Solution:**
- **First series:** $b_n = \frac{n}{10^n}$ is decreasing for $n \ge 1$ ($b_1=0.1, b_2=0.02, b_3=0.003, b_4=0.0004, b_5=0.00005, b_6=0.000006 < 5\times 10^{-5}$).
  Since $|R_5| \le b_6 = 6 \times 10^{-6} < 5 \times 10^{-5}$, summing the first **5 terms** suffices:
  $$S_5 = 0.1 - 0.02 + 0.003 - 0.0004 + 0.00005 = 0.08265 \approx 0.0827.$$
- **Second series:** Need $|R_n| \le b_{n+1} = \frac{1}{(n+1)^3} < 10^{-4} \iff (n+1)^3 > 10^4 \approx (21.54)^3$.
  So $n + 1 \ge 22 \implies \mathbf{n = 21}$ terms suffice.

---

**Q7 (`Endsem_21` Q4 & `CAL-Midsem_21batch` Q10 — Taylor/Maclaurin Series):**  
(a) Find the Maclaurin series of $f(x) = \sqrt{1+x}$ up to $x^3$ (or general term) and state its radius of convergence.  
(b) Find the power series representation of $\frac{x}{(1-x)^2}$ and $\ln(1+x)$ for $|x| < 1$.  
**Solution:**
- **(a):** $f(0) = 1$, $f'(x) = \frac{1}{2}(1+x)^{-1/2} \Rightarrow f'(0) = \frac{1}{2}$, $f''(0) = -\frac{1}{4}$, $f'''(0) = \frac{3}{8}$:
  $$\sqrt{1+x} = 1 + \frac{1}{2}x - \frac{1}{8}x^2 + \frac{1}{16}x^3 - \dots = 1 + \sum_{n=1}^\infty \frac{\frac{1}{2}(\frac{1}{2}-1)\cdots(\frac{1}{2}-n+1)}{n!} x^n, \quad R = 1.$$
- **(b):** Differentiate $\frac{1}{1-x} = \sum_{n=0}^\infty x^n \ (|x|<1)$ to get $\frac{1}{(1-x)^2} = \sum_{n=1}^\infty n x^{n-1}$. Multiply by $x$:
  $$\frac{x}{(1-x)^2} = \sum_{n=1}^\infty n x^n \quad (|x| < 1).$$
  Integrating $\frac{1}{1+t} = \sum_{n=0}^\infty (-1)^n t^n$ from $0$ to $x$:
  $$\ln(1+x) = \sum_{n=0}^\infty \frac{(-1)^n x^{n+1}}{n+1} = x - \frac{x^2}{2} + \frac{x^3}{3} - \dots \quad (-1 < x \le 1).$$

---

**Q8 (`Endsem_21` Q2 & `Problem Set 4` — $\epsilon$-$\delta$ Limit Proof):** Prove rigorously that $\lim_{x\to 3} (x^2 + x - 2) = 10$ (or $\lim_{x\to 2} x^2 = 4$).  
**Solution:**
Let $\epsilon > 0$. We bound $|(x^2 + x - 2) - 10| = |x^2 + x - 12| = |x - 3||x + 4|$.  
Assume $\delta \le 1$. Then $|x - 3| < 1 \implies 2 < x < 4 \implies 6 < x + 4 < 8 \implies |x + 4| < 8$.  
Thus $|(x^2+x-2) - 10| < 8|x - 3|$.  
Choose $\delta = \min\!\left(1, \frac{\epsilon}{8}\right) > 0$. Then whenever $0 < |x - 3| < \delta$, both $|x+4|<8$ and $|x-3| < \epsilon/8$ hold, so:
$$|(x^2 + x - 2) - 10| = |x - 3||x + 4| < \frac{\epsilon}{8} \cdot 8 = \epsilon.$$

---

**Q9 (`Assignment 2`, `Rolle and Cauchy Theorem Problems` — Differentiability & Continuity):**  
Check continuity and differentiability at $x = 0$ for:  
(a) $f(x) = x\sin(1/x)$ ($x\ne 0$), $0$ ($x=0$)  
(b) $g(x) = x^2\sin(1/x)$ ($x\ne 0$), $0$ ($x=0$)  
**Solution:**
- **(a):** Since $-|x| \le x\sin(1/x) \le |x|$ and $\lim_{x\to 0} \pm|x| = 0$, by Squeeze Theorem $\lim_{x\to 0} f(x) = 0 = f(0) \implies$ **Continuous at $0$**.  
  However, $f'(0) = \lim_{h\to 0} \frac{h\sin(1/h) - 0}{h} = \lim_{h\to 0} \sin(1/h)$ DNE (oscillates in $[-1,1]$) $\implies$ **Not differentiable at $0$**.
- **(b):** Continuous at $0$ similarly. For differentiability:
  $$g'(0) = \lim_{h\to 0} \frac{h^2\sin(1/h) - 0}{h} = \lim_{h\to 0} h\sin(1/h) = 0 \quad (\text{since } |h\sin(1/h)| \le |h| \to 0).$$
  Thus $g$ IS **differentiable at $0$** with $g'(0) = 0$! *(Note: for $x \ne 0$, $g'(x) = 2x\sin(1/x)-\cos(1/x)$, which is discontinuous at $0$!)*

---

**Q10 (`Assignment 2`, `Midsem Dec 2022`, `Endsem Feb 2023` — Mean Value Theorem Inequalities):**  
Prove: (a) $|\sin b - \sin a| \le |b - a|$ for all $a, b \in \mathbb{R}$;  
(b) $\frac{x}{1+x} < \ln(1+x) < x$ for all $x > 0$.  
**Solution:**
- **(a):** If $a = b$, trivial ($0 \le 0$). If $a \ne b$, $f(x) = \sin x$ is continuous on $[a,b]$ and differentiable on $(a,b)$ with $f'(x) = \cos x$. By LMVT, $\exists c$ between $a$ and $b$ such that
  $$\frac{\sin b - \sin a}{b - a} = \cos c \implies |\sin b - \sin a| = |\cos c|\cdot |b - a| \le 1\cdot |b - a| = |b - a|.$$
- **(b):** Let $f(t) = \ln(1+t)$ on $[0, x]$ for $x > 0$. Continuous on $[0,x]$, differentiable on $(0,x)$ with $f'(t) = \frac{1}{1+t}$. By LMVT, $\exists c \in (0, x)$ such that
  $$\frac{\ln(1+x) - \ln(1)}{x - 0} = \frac{1}{1+c}.$$
  Since $0 < c < x$, we have $\frac{1}{1+x} < \frac{1}{1+c} < 1$. Multiplying by $x > 0$:
  $$\frac{x}{1+x} < \ln(1+x) < x.$$

---

**Q11 (`Endsem_21` Q6 — Critical Points & Extrema Trap):**  
Find the critical points and absolute extrema of $g(x) = 3x^{2/3}$ on $[-2, 8]$ (and note why $x=0$ is crucial!).  
**Solution:**
- $g'(x) = 2x^{-1/3} = \frac{2}{x^{1/3}}$.
- $g'(x)$ is never $0$, BUT **$g'(0)$ does NOT exist** (vertical cusp)! Since $x = 0 \in (-2, 8)$ is in the domain of $g$, **$x = 0$ IS a critical point**.
- Evaluate at critical point & endpoints:
  - $g(0) = 0$
  - $g(-2) = 3(4)^{1/3} \approx 4.76$
  - $g(8) = 3(8)^{2/3} = 3(4) = 12$
- **Absolute Minimum:** $0$ at $x = 0$; **Absolute Maximum:** $12$ at $x = 8$. *(Common mistake in `Scan Mar 1, 2021.pdf`: claiming no critical points because $g'(x) \ne 0$ and missing the true minimum at $x=0$!)*

---

**Q12 (`Tutorial on Module 3_RI`, `Endsem_21` Q7, `Endsem Feb 2023` — Riemann Integrability & Sums):**  
(a) Using upper and lower Darboux sums, prove $f(x) = x^2$ is Riemann integrable on $[0, a]$ ($a>0$) and evaluate $\int_0^a x^2\,dx$.  
(b) Evaluate $\lim_{n\to\infty} \left(\frac{1}{n+1} + \frac{1}{n+2} + \dots + \frac{1}{2n}\right)$.  
**Solution:**
- **(a):** Partition $[0,a]$ into $n$ equal subintervals of width $\Delta x = \frac{a}{n}$, with $x_k = \frac{ka}{n}$. Since $f(x)=x^2$ is increasing on $[0,a]$:
  $$m_k = x_{k-1}^2 = \frac{(k-1)^2 a^2}{n^2}, \qquad M_k = x_k^2 = \frac{k^2 a^2}{n^2}.$$
  $$U(P_n, f) - L(P_n, f) = \sum_{k=1}^n (M_k - m_k)\Delta x = \Delta x (M_n - m_1) = \frac{a}{n}(a^2 - 0) = \frac{a^3}{n}.$$
  *(Notice the telescoping shortcut $\sum_{k=1}^n (f(x_k)-f(x_{k-1})) = f(x_n)-f(x_0)$ whenever $f$ is monotone!)*  
  For any $\epsilon > 0$, choose $n > \frac{a^3}{\epsilon} \implies U(P_n,f) - L(P_n,f) < \epsilon \implies f$ is Riemann integrable! Moreover:
  $$U(P_n, f) = \sum_{k=1}^n \frac{k^2 a^2}{n^2} \cdot \frac{a}{n} = \frac{a^3}{n^3} \cdot \frac{n(n+1)(2n+1)}{6} \xrightarrow{n\to\infty} \frac{a^3}{3}.$$
- **(b):** Rewrite as a Riemann sum on $[0,1]$:
  $$\sum_{k=1}^n \frac{1}{n+k} = \frac{1}{n} \sum_{k=1}^n \frac{1}{1 + k/n} \xrightarrow{n\to\infty} \int_0^1 \frac{1}{1+x}\,dx = \Big[\ln(1+x)\Big]_0^1 = \mathbf{\ln 2}.$$

---

**Q13 (`Tutorial on Module 3_RI` & `Midsem` — FTC Differentiation):**  
Find $\frac{dy}{dx}$ for: (a) $y = \int_{\sin x}^{x^2} e^{t^2}\,dt$; (b) Find $f(4)$ if $\int_0^{x^2} f(t)\,dt = x\cos(\pi x)$.  
**Solution:**
- **(a):** By FTC Part 1 + Chain Rule (Leibniz):
  $$\frac{dy}{dx} = e^{(x^2)^2} \cdot (2x) - e^{\sin^2 x} \cdot \cos x = 2x e^{x^4} - \cos x\,e^{\sin^2 x}.$$
- **(b):** Differentiate both sides with respect to $x$:
  $$f(x^2)\cdot (2x) = \cos(\pi x) - \pi x \sin(\pi x).$$
  Set $x = 2$ (so $x^2 = 4$):
  $$4 f(4) = \cos(2\pi) - 2\pi \sin(2\pi) = 1 - 0 = 1 \implies f(4) = \mathbf{\frac{1}{4}}.$$

---

**Q14 (`Endsem_21` Q9, `Practice Problems.jpg`, `Endsem Feb 2023` — 2D Limits, Continuity, Differentiability & Gradient):**  
(a) Check if $\lim_{(x,y)\to(0,0)} \frac{x^2 y}{x^4 + y^2}$ exists.  
(b) Prove $f(x,y) = \frac{xy}{\sqrt{x^2+y^2}}$ ($(x,y)\ne(0,0)$), $f(0,0)=0$ is continuous at $(0,0)$, find $f_x(0,0), f_y(0,0)$, and check differentiability at $(0,0)$.  
(c) Find the directional derivative of $g(x,y,z) = x e^y + y z^2$ at $(1,0,2)$ in the direction of $\mathbf{v} = \langle 2, -1, 2 \rangle$, and its maximum rate of increase.  
**Solution:**
- **(a):** Along $y = mx$: $\frac{m x^3}{x^4 + m^2 x^2} = \frac{mx}{x^2 + m^2} \to 0$. Along **$y = x^2$**: $\frac{x^2 \cdot x^2}{x^4 + x^4} = \frac{1}{2} \ne 0$. By Two-Path Test, limit **DNE**.
- **(b):**
  - *Continuity:* Using $|x| \le \sqrt{x^2+y^2}$ and $|y| \le \sqrt{x^2+y^2}$, $|f(x,y)-0| = \frac{|x||y|}{\sqrt{x^2+y^2}} \le |y| \le \sqrt{x^2+y^2}$. Given $\epsilon > 0$, take $\delta = \epsilon$: $0 < \sqrt{x^2+y^2} < \delta \implies |f(x,y)-0| < \epsilon$. **Continuous at $(0,0)$!**
  - *Partials:* $f_x(0,0) = \lim_{h\to 0}\frac{f(h,0)-0}{h} = 0$, $f_y(0,0) = \lim_{k\to 0}\frac{f(0,k)-0}{k} = 0$.
  - *Differentiability:* Need $\lim_{(h,k)\to(0,0)} \frac{f(h,k) - f(0,0) - h f_x(0,0) - k f_y(0,0)}{\sqrt{h^2+k^2}} = \lim_{(h,k)\to(0,0)} \frac{hk}{h^2+k^2} = 0$.  
    Along $h = k$: $\frac{h^2}{2h^2} = \frac{1}{2} \ne 0$! Thus $f$ is **continuous AND has partial derivatives, yet is NOT differentiable at $(0,0)$!**
- **(c):** $\nabla g = \langle e^y,\ x e^y + z^2,\ 2yz \rangle$. At $(1,0,2)$: $\nabla g(1,0,2) = \langle 1,\ 1 + 4,\ 0 \rangle = \langle 1, 5, 0 \rangle$.  
  Unit vector: $\hat{\mathbf{u}} = \frac{\langle 2,-1,2\rangle}{\sqrt{4+1+4}} = \left\langle \frac{2}{3}, -\frac{1}{3}, \frac{2}{3}\right\rangle$.  
  Directional derivative: $D_{\hat{\mathbf{u}}}g = \nabla g \cdot \hat{\mathbf{u}} = 1(\frac{2}{3}) + 5(-\frac{1}{3}) + 0 = \mathbf{-1}$.  
  Maximum rate of increase $= \|\nabla g(1,0,2)\| = \sqrt{1^2 + 5^2} = \mathbf{\sqrt{26}}$.

---

## 8. Practice Question Bank (With Hints/Answers)

1. **Sequence Limit & Proof (`Sequences.pdf`):** Find $\lim_{n\to\infty} \frac{1}{n}\left(1 + 2^{1/2} + 3^{1/3} + \dots + n^{1/n}\right)$. *(Ans: $1$ by Cauchy's 1st Theorem since $n^{1/n} \to 1$).*
2. **Series Battery (`Assignment 1`):** Test convergence: (a) $\sum_{n=2}^\infty \frac{1}{n (\ln n)^2}$; (b) $\sum_{n=1}^\infty \frac{n!}{n^n}$; (c) $\sum_{n=1}^\infty \frac{\cos(n\pi)}{\sqrt{n}}$; (d) $\sum_{n=1}^\infty \frac{(-1)^n n}{n^2+1}$. *(Ans: (a) Conv. by Integral Test; (b) Conv. by Ratio Test, $L=1/e < 1$; (c) Cond. Conv. by Leibniz + harmonic $p=1/2$; (d) Cond. Conv. by Leibniz + LCT with $1/n$).*
3. **Power Series (`Problem Set 2`):** Find radius and interval of convergence of $\sum_{n=1}^\infty \frac{(3x - 2)^n}{n 5^n}$. *(Ans: $R = 5/3$, center $2/3$, interval $[-1, 7/3)$).*
4. **MVT Exact Zeroes (`Assignment 2`):** Prove $x^5 + 10x + 3 = 0$ has **exactly one** real root. *(Hint: IVT on $[-1, 0]$ for existence + $f'(x) = 5x^4 + 10 > 0$ via Rolle for uniqueness).*
5. **Cauchy MVT (`Rolle & Cauchy`):** Prove $\frac{\sin\alpha - \sin\beta}{\cos\beta - \cos\alpha} = \cot\theta$ for some $\theta \in (\alpha,\beta) \subset (0,\pi/2)$.
6. **Riemann Non-Integrability (`Problem Set 6`):** Define $f(x) = 1$ if $x \in \mathbb{Q}$, $-1$ if $x \notin \mathbb{Q}$ on $[0,1]$. Compute lower and upper Riemann integrals and conclude integrability. *(Ans: $\underline{\int} = -1$, $\overline{\int} = 1$, NOT integrable).*
7. **2D Limit & Partials (`Endsem Feb 2023` style):** Check continuity of $f(x,y) = \frac{x^3}{x^2+y^2}$ ($f(0,0)=0$) at $(0,0)$ and compute $f_x(0,0), f_y(0,0)$. *(Ans: Continuous since $|x^3/(x^2+y^2)| \le |x| \to 0$; $f_x(0,0)=1, f_y(0,0)=0$, NOT differentiable at $(0,0)$).*

---

## 9. Common Exam Mistakes Checklist (Observed from Past Answer Scripts)

- [ ] **Missing `DNE` Critical Points:** Never forget to include points where $f'(c)$ fails to exist when finding critical points / extrema (e.g., $x=0$ for $x^{2/3}$).
- [ ] **Open vs Closed Sets in $\mathbb{R}^2$:** A curve in $\mathbb{R}^2$ (like an arc or circle) is NEVER open in $\mathbb{R}^2$; if endpoints are excluded (like $y>0$), it is NOT closed either!
- [ ] **Two-Path Test Misuse:** Getting $0$ along $y=mx$ for ALL $m$ does **not** prove a 2D limit exists! Always check parabolic/curved paths ($y=kx^2$, $x=ky^2$), and use $\epsilon$-$\delta$ / Squeeze to prove existence.
- [ ] **Confusing $f_{xy}(0,0)$ vs Limit Continuity:** For piecewise 2D functions, compute $f_x(0,0)$ and $f_y(0,0)$ strictly from the **limit definition**, not by differentiating the $x\ne 0$ formula and plugging $(0,0)$.
- [ ] **$n$-th Term Test Fallacy:** $\lim a_n = 0$ is necessary, **never sufficient** for convergence ($\sum 1/n$!).
- [ ] **Power Series Endpoints:** Ratio/Root gives the interior $(a-R, a+R)$ ONLY — always check both endpoints separately!
- [ ] **Riemann Upper/Lower Integrals:** Never assume $L(P,f)=0$ means $\int f = 0$ without checking $U(P,f)$ too!

---

## 10. Quick Last-Hour Formula Sheet

- $\lim_{n\to\infty} n^{1/n} = 1$, $\lim (1+x/n)^n = e^x$, $\lim x^n/n! = 0$
- Geometric sum: $\sum_{n=k}^\infty a r^n = \frac{a r^k}{1-r}$ ($|r|<1$)
- Alternating error bound: $|S - S_n| \le b_{n+1}$
- LMVT: $f(b)-f(a) = f'(c)(b-a)$; Cauchy MVT: $\frac{f(b)-f(a)}{g(b)-g(a)} = \frac{f'(c)}{g'(c)}$
- $\frac{d}{dx}\int_{g(x)}^{h(x)} f(t)\,dt = f(h(x))h'(x) - f(g(x))g'(x)$
- Riemann sum: $\int_a^b f(x)\,dx = \lim_{n\to\infty} \frac{b-a}{n}\sum_{k=1}^n f\!\left(a + \frac{k(b-a)}{n}\right)$
- Gradient & Directional Derivative: $D_{\hat{\mathbf{u}}}f = \nabla f \cdot \frac{\mathbf{v}}{\|\mathbf{v}\|}$
