# MA1000: Calculus

> MA1000 evaluation is 30 Marks Mid Term, 30 Marks Assignments, and 40 Marks End Semester, covering 5 lecture modules supported by Problem Sets 1–7 and Tutorials.

## Syllabus Topics
- [ ] **Real Sequences, Range Set & epsilon-N Convergence** (Module 1)
- [ ] **Sandwich Theorem, Monotone Convergence & Cauchy Limits** (Module 1)
- [ ] **Infinite Series, Geometric/Telescoping & Integral Test** (Module 1)
- [ ] **Comparison, Ratio, Root & Alternating Series Tests** (Module 1)
- [ ] **Power Series, Radius of Convergence & Taylor/Maclaurin** (Module 1)
- [ ] **1D Limits (epsilon-delta), Limit Laws & One-Sided Limits** (Module 2)
- [ ] **Continuity, Discontinuity Types, Extensions & IVT** (Module 2)
- [ ] **Differentiability, Rules, Linearization & Extrema** (Module 3)
- [ ] **Rolle's Theorem, Lagrange MVT & Cauchy MVT** (Module 3)
- [ ] **Riemann Partitions, Upper/Lower Sums & Integrability** (Module 4)
- [ ] **Integral Properties & Fundamental Theorem of Calculus** (Module 4)
- [ ] **R^2 Regions, Two-Path Limits, Partial Derivatives & Gradient** (Module 5)

## 1. Real Sequences, Range Set & epsilon-N Proofs
*Module 1 • 01_Sequences & Sequences.pdf*

**Plain Summary:** A real sequence $a : \mathbb{Z}^+ \to \mathbb{R}$ is an ordered list $a_1, a_2, a_3, \dots$. It converges to $L$ if, for any tolerance $\epsilon > 0$, all terms from some index $N$ onward stay strictly within distance $\epsilon$ of $L$.

- **$\epsilon$-$N$ Convergence:** $\lim_{n\to\infty} a_n = L$ means for every $\epsilon > 0$, there exists an integer $N$ such that $|a_n - L| < \epsilon$ for all $n \ge N$.
- **Divergence to $\pm\infty$:** $a_n \to \infty$ means for every number $M$, there exists $N$ such that $a_n > M$ for all $n \ge N$ (e.g. $\{\sqrt{n}\} \to \infty$, and $\{1/n^p\} \to \infty$ for $p < 0$).
- **Uniqueness & Boundedness:** Every convergent sequence has a unique limit and is bounded. The **Range Set** ignores order and duplicates (e.g. $\{(-1)^{n+1}\}$ has range $\{1, -1\}$).
- **Behavior of $\{r^n\}$:** Converges to $0$ if $|r| < 1$; converges to $1$ if $r = 1$; diverges to $+\infty$ if $r > 1$; oscillates finitely if $r = -1$; oscillates infinitely if $r < -1$.

**Worked Example (01_Sequences & Sequences.pdf Slide 19):** Prove using the $\epsilon$-$N$ definition that $\lim_{n\to\infty} \frac{3 + 2\sqrt{n}}{\sqrt{n}} = 2$.
1. **Step 1:** Simplify the error $|a_n - L|$: $\left|\frac{3 + 2\sqrt{n}}{\sqrt{n}} - 2\right| = \left|\frac{3}{\sqrt{n}}\right| = \frac{3}{\sqrt{n}}$.
1. **Step 2:** Solve $\frac{3}{\sqrt{n}} < \epsilon$ for $n$: $\sqrt{n} > \frac{3}{\epsilon} \iff n > \frac{9}{\epsilon^2}$.
1. **Step 3:** Choose any positive integer $N > \frac{9}{\epsilon^2}$ (e.g. $N = \lfloor 9/\epsilon^2 \rfloor + 1$). Then for all $n \ge N$, $|a_n - 2| < \epsilon$.
**Answer:** $\lim_{n\to\infty} \frac{3+2\sqrt{n}}{\sqrt{n}} = 2$ with $N > 9/\epsilon^2$.

**Key Formula:** $$|a_n - L| < \epsilon \quad (\forall n \ge N) \qquad\Big|\qquad \lim_{n\to\infty} r^n = 0 \iff |r| < 1$$

**Common Mistake:** Having a single limit point does not guarantee convergence: the sequence $\{1, 2, 1, 4, 1, 6, \dots\}$ has $1$ as its only limit point, yet it diverges because it is unbounded (`Sequences.pdf` Slide 25).

---

## 2. Limit Laws, Sandwich Theorem & Monotone Convergence
*Module 1 • 01_Sequences & Quotient rule proof*

**Plain Summary:** When finding a sequence limit directly with $\epsilon$-$N$ is messy, we combine known limits using algebra laws, trap the sequence between two simpler bounds, or check if it is monotonic and bounded.

- **Algebra & Quotient Lemma:** If $a_n \to a$ and $b_n \to b \ne 0$, then $|b_n| \ge |b|/2$ for large $n$, giving $a_n/b_n \to a/b$ (along with sum, difference, and product rules).
- **Sandwich & Continuous Function Theorems:** If $a_n \le b_n \le c_n$ eventually and $a_n, c_n \to L$, then $b_n \to L$. If $a_n \to L$ and $f$ is continuous at $L$, then $f(a_n) \to f(L)$.
- **Special Slide Limits:** For $p > 0$ and $\alpha \in \mathbb{R}$: $\frac{1}{n^p} \to 0$, $p^{1/n} \to 1$, $n^{1/n} \to 1$, $\frac{n^\alpha}{(1+p)^n} \to 0$, $\frac{x^n}{n!} \to 0$, and $\left(1 + \frac{x}{n}\right)^n \to e^x$.
- **Monotone & Cauchy Criteria:** A monotonically increasing sequence bounded above converges to its least upper bound (and decreasing bounded below to its greatest lower bound). A real sequence converges iff it is a **Cauchy sequence** ($|a_n - a_m| < \epsilon$ for $n,m \ge N$).

**Worked Example (Midsem Jan 2021 Q2 & Problem Set 1 Q7):** Prove that the sequence $a_1 = 10$, $a_{n+1} = \frac{1}{2}\left(a_n + \frac{10}{a_n}\right)$ ($n \ge 1$) converges, and find its limit.
1. **Step 1 (Bounded below):** By AM-GM (since $a_n > 0$), $a_{n+1} = \frac{1}{2}\left(a_n + \frac{10}{a_n}\right) \ge \sqrt{a_n \cdot \frac{10}{a_n}} = \sqrt{10}$ for all $n \ge 1$ (and $a_1 = 10 > \sqrt{10}$).
1. **Step 2 (Monotonically decreasing):** $a_{n+1} - a_n = \frac{10 - a_n^2}{2a_n} \le 0$ because $a_n^2 \ge 10$ for all $n \ge 1$. So $a_{n+1} \le a_n$.
1. **Step 3 (Take limit):** By the Monotone Convergence Theorem, $a_n \to L$. Taking limits in the recurrence gives $L = \frac{1}{2}\left(L + \frac{10}{L}\right) \implies L^2 = 10$. Since $a_n > 0$, $L = \sqrt{10}$.
**Answer:** Converges to $\sqrt{10}$.

**Key Formula:** $$a_n \le b_n \le c_n \implies \lim b_n = L \qquad\Big|\qquad \lim_{n\to\infty} n^{1/n} = 1, \quad \lim_{n\to\infty}\left(1+\frac{x}{n}\right)^n = e^x$$

**Common Mistake:** Always check BOTH boundedness and monotonicity before taking $L = f(L)$ on a recursive sequence; assuming the limit exists without proving convergence first is invalid. Also note a slide typo in `01_Sequences` Slide 23: $\lim_{n\to\infty}(1 - 1/n) = 1 - 0 = 1$ (printed as $0$).

---

## 3. Subsequences & Cauchy's First and Second Theorems
*Module 1 • 01_Sequences & Sequences.pdf*

**Plain Summary:** Every subsequence of a convergent sequence shares the same limit, and Cauchy's two theorems let us evaluate tricky arithmetic-mean and $n$-th root limits quickly.

- **Subsequences & Bolzano-Weierstrass:** If $a_n \to L$, every subsequence $a_{n_k} \to L$ (so if two subsequences have different limits, $a_n$ diverges). Conversely, if $a_{2m} \to L$ and $a_{2m+1} \to L$, then $a_n \to L$. Every bounded sequence has a convergent subsequence.
- **Cauchy's 1st Theorem:** If $\lim_{n\to\infty} a_n = L$, then the arithmetic mean sequence also converges to $L$: $\lim_{n\to\infty} \frac{a_1 + a_2 + \dots + a_n}{n} = L$.
- **Cauchy's 2nd Theorem:** If $a_n > 0$ for all $n$ and $\lim_{n\to\infty} \frac{a_{n+1}}{a_n}$ exists, then $\lim_{n\to\infty} (a_n)^{1/n} = \lim_{n\to\infty} \frac{a_{n+1}}{a_n}$.
- **Ratio Criterion for Sequences:** If $\lim_{n\to\infty} \left|\frac{a_{n+1}}{a_n}\right| = L$ with $L < 1$, then $a_n \to 0$; if $L > 1$, then $|a_n| \to \infty$.

**Worked Example (Sequences.pdf Slide 34):** Use Cauchy's 2nd Theorem to find $\lim_{n\to\infty} (a_n)^{1/n}$ where $a_n = \frac{(3n)!}{(n!)^3}$.
1. **Step 1:** All terms $a_n > 0$. Compute the ratio $\frac{a_{n+1}}{a_n} = \frac{(3n+3)!}{((n+1)!)^3} \cdot \frac{(n!)^3}{(3n)!}$.
1. **Step 2:** Cancel factorials: $\frac{a_{n+1}}{a_n} = \frac{(3n+3)(3n+2)(3n+1)}{(n+1)^3} = \frac{3(3+2/n)(3+1/n)}{(1+1/n)^2}$ (after dividing numerator and denominator by $n^3$, or using $(3n+3)/(n+1)=3$).
1. **Step 3:** Take the limit: $\lim_{n\to\infty} \frac{a_{n+1}}{a_n} = \frac{3 \cdot 3 \cdot 3}{1^3} = 27$. By Cauchy's 2nd Theorem, $\lim_{n\to\infty} (a_n)^{1/n} = 27$.
**Answer:** $27$

**Key Formula:** $$\lim_{n\to\infty}\frac{a_1+\dots+a_n}{n} = \lim_{n\to\infty} a_n \qquad\Big|\qquad \lim_{n\to\infty} a_n^{1/n} = \lim_{n\to\infty}\frac{a_{n+1}}{a_n} \ (a_n>0)$$

**Common Mistake:** In `Sequences.pdf` Slide 33, Example (ii) misprints $\lim_{n\to\infty}\frac{1}{n}(1+\frac{1}{2}+\dots+\frac{1}{n}) = 1$ even though $a_n = 1/n \to 0$; the true limit is $0$. Also on Slide 32, $\sum_{k=1}^n \frac{1}{\sqrt{n^2+k}} \to 1$ is proved by the Sandwich Theorem, not Cauchy's 1st Theorem.

---

## 4. Infinite Series, Geometric Series & Integral Test
*Module 1 • 01_Sequences & PS 2–3*

**Plain Summary:** An infinite series $\sum_{n=1}^\infty a_n$ converges to $L$ if its partial sums $s_n = a_1 + \dots + a_n$ approach a finite limit $L$.

- **Geometric Series:** $\sum_{n=1}^\infty a r^{n-1} = \frac{a}{1-r}$ when $|r| < 1$, and diverges when $|r| \ge 1$ ($a \ne 0$).
- **Telescoping & Algebraic Combination:** Break terms into partial fractions so adjacent terms cancel (e.g. $\frac{1}{n(n+1)} = \frac{1}{n} - \frac{1}{n+1}$). Convergent series can be added or scaled term by term.
- **$n$-th Term Test for Divergence:** If $\sum a_n$ converges, then $a_n \to 0$. Thus if $\lim_{n\to\infty} a_n \ne 0$ or does not exist, $\sum a_n$ diverges.
- **Integral Test & $p$-Series:** For positive, continuous, decreasing $f(x)$ with $a_n = f(n)$ for $x \ge N$, $\sum_{n=N}^\infty a_n$ and $\int_N^\infty f(x)\,dx$ both converge or both diverge. Hence the **$p$-series** $\sum \frac{1}{n^p}$ converges iff $p > 1$ (harmonic series $p=1$ diverges).

**Worked Example (01_Sequences (Geometric Series Example)):** Find the sum of the series $\sum_{n=1}^\infty \frac{3^{n-1} - 1}{6^{n-1}}$.
1. **Step 1:** Split the fraction into two geometric terms: $\frac{3^{n-1} - 1}{6^{n-1}} = \frac{1}{2^{n-1}} - \frac{1}{6^{n-1}}$.
1. **Step 2:** Both $\sum_{n=1}^\infty \left(\frac{1}{2}\right)^{n-1}$ ($r=1/2$) and $\sum_{n=1}^\infty \left(\frac{1}{6}\right)^{n-1}$ ($r=1/6$) converge since $|r| < 1$.
1. **Step 3:** Sum each geometric series using $\frac{a}{1-r}$: $\frac{1}{1 - 1/2} - \frac{1}{1 - 1/6} = 2 - \frac{6}{5} = \frac{4}{5}$.
**Answer:** $\frac{4}{5}$

**Key Formula:** $$\sum_{n=1}^{\infty} a r^{n-1} = \frac{a}{1-r}\ (|r|<1) \qquad\Big|\qquad \sum_{n=1}^{\infty} \frac{1}{n^p} \text{ converges} \iff p > 1$$

**Common Mistake:** The converse of the $n$-th Term Test is FALSE: $a_n \to 0$ does NOT prove convergence (the harmonic series $\sum 1/n$ has $1/n \to 0$ yet diverges). Also, adding or deleting finitely many terms does not change convergence, though it changes the sum.

---

## 5. Comparison, Limit Comparison, Ratio & Root Tests
*Module 1 • 01_Sequences & PS 2–3*

**Plain Summary:** To test a positive-term series $\sum a_n$, compare it against a known $p$-series or geometric series, or check the limiting ratio $a_{n+1}/a_n$ or $n$-th root $a_n^{1/n}$.

- **Direct Comparison ($a_n \ge 0$):** If $a_n \le c_n$ eventually and $\sum c_n$ converges, then $\sum a_n$ converges. If $a_n \ge d_n$ eventually and $\sum d_n$ diverges, then $\sum a_n$ diverges.
- **Limit Comparison Test ($a_n, b_n > 0$):** Let $L = \lim_{n\to\infty} \frac{a_n}{b_n}$. If $0 < L < \infty$, both converge or both diverge. If $L=0$ and $\sum b_n$ converges, $\sum a_n$ converges. If $L=\infty$ and $\sum b_n$ diverges, $\sum a_n$ diverges.
- **Ratio Test ($a_n > 0$):** Let $\rho = \lim_{n\to\infty} \frac{a_{n+1}}{a_n}$. Converges if $\rho < 1$, diverges if $\rho > 1$ (or $\infty$), inconclusive if $\rho = 1$.
- **Root Test ($a_n \ge 0$):** Let $\rho = \lim_{n\to\infty} a_n^{1/n}$. Converges if $\rho < 1$, diverges if $\rho > 1$ (or $\infty$), inconclusive if $\rho = 1$.

**Worked Example (01_Sequences & Midsem Jan 2021 Q5):** Test the convergence of $\sum a_n$ where $a_n = \frac{n}{2^n}$ if $n$ is prime, and $a_n = \frac{1}{2^n}$ otherwise.
1. **Step 1:** Since $a_n > 0$ and the formula alternates unpredictably between primes and composites, apply the Root Test.
1. **Step 2:** Compute $a_n^{1/n}$: it equals $\frac{n^{1/n}}{2}$ when $n$ is prime, and $\frac{1}{2}$ otherwise. For all $n \ge 1$, $\frac{1}{2} \le a_n^{1/n} \le \frac{n^{1/n}}{2}$.
1. **Step 3:** Since $n^{1/n} \to 1$, by the Sandwich Theorem $\lim_{n\to\infty} a_n^{1/n} = \frac{1}{2} < 1$. By the Root Test, $\sum a_n$ converges.
**Answer:** Converges by the Root Test ($\rho = 1/2 < 1$).

**Key Formula:** $$\rho = \lim_{n\to\infty}\frac{a_{n+1}}{a_n} \quad \text{or} \quad \lim_{n\to\infty} a_n^{1/n} : \quad \rho < 1 \implies \text{conv},\ \rho > 1 \implies \text{div}$$

**Common Mistake:** When $\rho = 1$ in the Ratio or Root Test, the test is inconclusive — do NOT stop there! For example, $\sum \frac{4^n (n!)^2}{(2n)!}$ gives $\rho = 1$, yet $\frac{a_{n+1}}{a_n} = \frac{2n+2}{2n+1} > 1$, so $a_n \not\to 0$ and the series diverges. Also note slide typo in `01_Sequences`: the divergent Root Test example (b) is $\sum 2^n/n^2$, not $\sum n^2/2^n$.

---

## 6. Alternating Series, Absolute & Conditional Convergence
*Module 1 • 01_Sequences & PS 3–4*

**Plain Summary:** When terms alternate in sign, cancellation helps the series converge even when its absolute values do not — separating absolute convergence from conditional convergence.

- **Alternating Series Test (Leibniz):** $\sum_{n=1}^\infty (-1)^{n+1} u_n$ converges if (1) $u_n > 0$, (2) $u_n \ge u_{n+1}$ for all $n \ge N$, and (3) $\lim_{n\to\infty} u_n = 0$.
- **Absolute Convergence:** $\sum a_n$ converges **absolutely** if $\sum |a_n|$ converges. Every absolutely convergent series converges (proof uses $0 \le a_n + |a_n| \le 2|a_n|$).
- **Conditional Convergence:** A series that converges, while $\sum |a_n|$ diverges, converges **conditionally** (e.g. the alternating harmonic series $\sum \frac{(-1)^{n+1}}{n}$).
- **Alternating $p$-Series:** $\sum_{n=1}^\infty \frac{(-1)^n}{n^p}$ converges absolutely for $p > 1$, converges conditionally for $0 < p \le 1$, and diverges for $p \le 0$.

**Worked Example (01_Sequences & Problem Set 3 Q17):** Test whether $\sum_{n=1}^\infty \frac{\sin n}{n^2}$ converges.
1. **Step 1:** The terms $\frac{\sin n}{n^2}$ change sign irregularly, so check absolute convergence by considering $\sum_{n=1}^\infty \left|\frac{\sin n}{n^2}\right|$.
1. **Step 2:** Since $|\sin n| \le 1$ for all $n$, we have $0 \le \left|\frac{\sin n}{n^2}\right| \le \frac{1}{n^2}$.
1. **Step 3:** $\sum_{n=1}^\infty \frac{1}{n^2}$ is a convergent $p$-series ($p = 2 > 1$). By the Comparison Test, $\sum \left|\frac{\sin n}{n^2}\right|$ converges, so $\sum \frac{\sin n}{n^2}$ converges absolutely and hence converges.
**Answer:** Converges absolutely (hence converges).

**Key Formula:** $$\sum |a_n| \text{ converges} \implies \sum a_n \text{ converges} \qquad\Big|\qquad \sum_{n=1}^\infty \frac{(-1)^{n+1}}{n^p}:\ \text{cond. for } 0<p\le 1$$

**Common Mistake:** Do not apply the Alternating Series Test without checking that $u_n$ is eventually non-increasing AND $u_n \to 0$. Also remember: if $\sum a_n$ diverges, then $\sum |a_n|$ must diverge (`Midsem Jan 2021 Q6`).

---

## 7. Power Series, Radius & Interval of Convergence
*Module 1 • 01_Sequences & PS 4 Set A*

**Plain Summary:** A power series $\sum c_n(x-a)^n$ acts like an infinite polynomial centered at $a$; it converges on an interval centered at $a$ whose half-width is the radius of convergence $R$.

- **Convergence Theorem:** If $\sum a_n x^n$ converges at $x = c \ne 0$, it converges absolutely for all $|x| < |c|$; if it diverges at $x = d$, it diverges for all $|x| > |d|$.
- **Radius of Convergence $R$:** Either $R = 0$ (converges only at $x = a$), $R = \infty$ (converges for all $x$), or $R > 0$ (converges absolutely for $|x-a| < R$ and diverges for $|x-a| > R$). Using the Ratio Test, $R = \lim_{n\to\infty} \left|\frac{a_n}{a_{n+1}}\right|$ when the limit exists.
- **Endpoint Testing:** Ratio/Root tests give no answer at $|x-a| = R$. Always substitute $x = a - R$ and $x = a + R$ separately and test the resulting numerical series.
- **Calculus on Power Series:** Inside $(a-R, a+R)$, a power series can be differentiated and integrated term by term (with the same radius $R$), and two absolutely convergent series can be multiplied via the Cauchy product $c_n = \sum_{k=0}^n a_k b_{n-k}$.

**Worked Example (01_Sequences & Assignment 1 Q15(a)):** Find the radius and interval of convergence of $\sum_{n=1}^\infty \frac{(x-1)^n}{n^3 3^n}$.
1. **Step 1 (Radius $R$):** Here $a_n = \frac{1}{n^3 3^n}$. Compute $R = \lim_{n\to\infty} \left|\frac{a_n}{a_{n+1}}\right| = \lim_{n\to\infty} \frac{(n+1)^3 3^{n+1}}{n^3 3^n} = 3$.
1. **Step 2 (Open interval):** The series converges absolutely for $|x - 1| < 3$, i.e. $-2 < x < 4$, and diverges for $|x - 1| > 3$.
1. **Step 3 (Test endpoints):** At $x = 4$: $\sum_{n=1}^\infty \frac{3^n}{n^3 3^n} = \sum \frac{1}{n^3}$, which converges ($p=3>1$). At $x = -2$: $\sum_{n=1}^\infty \frac{(-3)^n}{n^3 3^n} = \sum \frac{(-1)^n}{n^3}$, which converges absolutely.
**Answer:** Radius $R = 3$; Interval of convergence $[-2, 4]$ (converges absolutely on $[-2, 4]$).

**Key Formula:** $$R = \lim_{n\to\infty}\left|\frac{a_n}{a_{n+1}}\right| \qquad\Big|\qquad \int \left(\sum_{n=0}^\infty c_n(x-a)^n\right)dx = C + \sum_{n=0}^\infty c_n \frac{(x-a)^{n+1}}{n+1}$$

**Common Mistake:** Never forget to test both endpoints $x = a \pm R$! For $\sum_{n=1}^\infty (-1)^{n-1} \frac{x^n}{n}$, $R=1$, $x=1$ converges (alternating harmonic) while $x=-1$ diverges (negative harmonic), giving $(-1, 1]$. Also note a slide typo in `01_Sequences` (`tan^-1 x` example): differentiating $x - x^3/3 + x^5/5 - \dots$ gives $1 - x^2 + x^4 - x^6 + \dots$ (even powers, not $x^3$).

---

## 8. Taylor Series & Standard Maclaurin Expansions
*Module 1 • 01_Sequences & Assignment 1*

**Plain Summary:** If $f$ equals a power series around $a$, its coefficients are uniquely forced by its derivatives at $a$: $c_n = \frac{f^{(n)}(a)}{n!}$.

- **Taylor & Maclaurin Formula:** Taylor series of $f$ at $x = a$ is $\sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n$. Setting $a = 0$ gives the **Maclaurin series** $\sum_{n=0}^\infty \frac{f^{(n)}(0)}{n!} x^n$.
- **Geometric-Derived Series ($|x|<1$):** $\frac{1}{1-x} = \sum_{n=0}^\infty x^n$, $\ln(1+x) = \sum_{n=1}^\infty (-1)^{n-1}\frac{x^n}{n}$ (converges on $(-1,1]$), and $\tan^{-1}x = \sum_{n=0}^\infty (-1)^n\frac{x^{2n+1}}{2n+1}$ (on $[-1,1]$).
- **Entire Expansions ($R = \infty$):** $e^x = \sum_{n=0}^\infty \frac{x^n}{n!}$, $\sin x = \sum_{n=0}^\infty (-1)^n\frac{x^{2n+1}}{(2n+1)!}$, $\cos x = \sum_{n=0}^\infty (-1)^n\frac{x^{2n}}{(2n)!}$ for all $x \in \mathbb{R}$.
- **Substitution & Identities:** Build new series quickly from known ones (e.g. $\sin^2 x = \frac{1 - \cos 2x}{2}$, or $1/x$ expanded about $a = 2$ via geometric ratio $-(x-2)/2$).

**Worked Example (Midsem Jan 2021 Q9 & Assignment 1 Q20):** Find the Taylor (Maclaurin) series generated by $f(x) = \sin^2 x$ at $x = 0$ and its interval of convergence.
1. **Step 1:** Use the identity $\sin^2 x = \frac{1 - \cos(2x)}{2}$.
1. **Step 2:** Substitute $2x$ into $\cos u = \sum_{n=0}^\infty (-1)^n \frac{u^{2n}}{(2n)!}$ (valid for all $u \in \mathbb{R}$): $\cos(2x) = 1 - \frac{(2x)^2}{2!} + \frac{(2x)^4}{4!} - \dots = 1 + \sum_{n=1}^\infty (-1)^n \frac{2^{2n} x^{2n}}{(2n)!}$.
1. **Step 3:** Subtract from $1$ and divide by $2$: $\sin^2 x = \sum_{n=1}^\infty (-1)^{n-1} \frac{2^{2n-1} x^{2n}}{(2n)!} = x^2 - \frac{x^4}{3} + \frac{2x^6}{45} - \dots$, converging for all $x \in (-\infty, \infty)$.
**Answer:** $\sum_{n=1}^\infty (-1)^{n-1} \frac{2^{2n-1} x^{2n}}{(2n)!}$ on $(-\infty, \infty)$.

**Key Formula:** $$f(x) \sim \sum_{n=0}^{\infty} \frac{f^{(n)}(a)}{n!}(x-a)^n \qquad\Big|\qquad \frac{1}{1-x} = \sum_{n=0}^{\infty} x^n \ (|x|<1)$$

**Common Mistake:** A Taylor series can converge everywhere and still NOT equal $f(x)$! In `01_Sequences`, $f(x) = e^{-1/x^2}$ ($x \ne 0$), $f(0) = 0$ has $f^{(n)}(0) = 0$ for all $n$, so its Maclaurin series is identically $0$, which equals $f(x)$ only at $x = 0$.

---

## 9. 1D Limits, epsilon-delta Definition & One-Sided Limits
*Module 2 • 02_Limit and Continuity*

**Plain Summary:** The limit $\lim_{x\to x_0} f(x) = L$ captures what $f(x)$ approaches as $x$ gets arbitrarily close to $x_0$ from both sides — regardless of whether $f(x_0)$ is defined.

- **$\epsilon$-$\delta$ Definition:** $\lim_{x\to x_0} f(x) = L$ iff for every $\epsilon > 0$, there exists $\delta > 0$ such that $0 < |x - x_0| < \delta \implies |f(x) - L| < \epsilon$.
- **Limit Laws & Rational Functions:** Sum, difference, product, constant multiple, and quotient limits (when denominator limit $\ne 0$) follow directly. Polynomials satisfy $\lim_{x\to c} P(x) = P(c)$.
- **One-Sided Limits:** $\lim_{x\to c} f(x) = L$ iff both $\lim_{x\to c^-} f(x) = L$ and $\lim_{x\to c^+} f(x) = L$ (e.g. $x/|x|$ has LHL $-1$ and RHL $+1$ at $0$, so the two-sided limit does not exist).
- **Sandwich Theorem:** If $g(x) \le f(x) \le h(x)$ near $c$ (except possibly at $c$) and $\lim_{x\to c} g(x) = \lim_{x\to c} h(x) = L$, then $\lim_{x\to c} f(x) = L$ (used to prove $\lim_{\theta\to 0}\sin\theta = 0$ and $\lim_{\theta\to 0}\frac{\sin\theta}{\theta} = 1$).

**Worked Example (Endsem March 2021 Q3):** Prove using the $\epsilon$-$\delta$ definition that $\lim_{x\to 3} (x^2 + 2x) = 15$.
1. **Step 1:** Factor $|f(x) - L|$: $|(x^2 + 2x) - 15| = |x - 3|\,|x + 5|$.
1. **Step 2:** Control $|x + 5|$ by assuming $|x - 3| < 1$: then $2 < x < 4$, so $7 < x + 5 < 9$, which gives $|x + 5| < 9$.
1. **Step 3:** Then $|(x^2 + 2x) - 15| < 9|x - 3| < \epsilon$ whenever $|x - 3| < \frac{\epsilon}{9}$. Set $\delta = \min\left(1, \frac{\epsilon}{9}\right)$; then $0 < |x - 3| < \delta \implies |f(x) - 15| < \epsilon$.
**Answer:** Take $\delta = \min(1, \epsilon/9)$.

**Key Formula:** $$0 < |x - x_0| < \delta \implies |f(x) - L| < \epsilon \qquad\Big|\qquad \lim_{\theta\to 0} \frac{\sin\theta}{\theta} = 1$$

**Common Mistake:** In $\epsilon$-$\delta$ proofs for quadratics/rationals, you cannot leave $x$ inside $\delta$ (like $\delta = \epsilon/|x+5|$). Always bound the extra factor on a fixed neighborhood such as $|x - x_0| < 1$ and take $\delta = \min(1, \dots)$.

---

## 10. Continuity, Discontinuity Types & Intermediate Value Theorem
*Module 2 • 02_Limit and Continuity*

**Plain Summary:** A function is continuous at an interior point $c$ if there is no break, jump, hole, or wild oscillation there: the limit exists and matches $f(c)$.

- **Continuity Definition:** $f$ is continuous at interior point $c$ iff $\lim_{x\to c} f(x) = f(c)$ (equivalently, $\forall \epsilon > 0,\ \exists \delta > 0$ such that $|x-c| < \delta \implies |f(x)-f(c)| < \epsilon$). At endpoints $a,b$, use right/left limits.
- **4 Types of Discontinuity:** **Removable** (limit exists, $\ne f(c)$ or $f(c)$ undefined); **Jump** (LHL $\ne$ RHL, e.g. unit step $U(x)$ or $\lfloor x\rfloor$); **Infinite** (one-sided limit is $\pm\infty$, e.g. $1/x^2$); **Oscillating** (e.g. $\sin(1/x)$ at $0$).
- **Continuous Extension & Composites:** If $\lim_{x\to c} f(x) = L$ exists, setting $F(c) = L$ gives a continuous extension (e.g. $\frac{\sin x}{x}$ extended by $1$ at $0$). Composites $g \circ f$ of continuous functions are continuous.
- **Intermediate Value Theorem (IVT):** If $f$ is continuous on $[a,b]$, it takes every value $y_0$ between $f(a)$ and $f(b)$ at some $c \in [a,b]$ — guaranteeing roots when $f(a)$ and $f(b)$ have opposite signs.

**Worked Example (Assignment 2 Q10 & Problem Set 4 Set C Q1(b)):** Find $a$ and $b$ so that $f(x) = \begin{cases} ax + 2b, & x \le 0 \\ x^2 + 3a - b, & 0 < x \le 2 \\ 3x - 5, & x > 2 \end{cases}$ is continuous everywhere.
1. **Step 1:** Each piece is a polynomial, so $f$ is already continuous on $(-\infty, 0)$, $(0, 2)$, and $(2, \infty)$. We only need continuity at $x = 0$ and $x = 2$.
1. **Step 2 (At $x = 0$):** $\lim_{x\to 0^-} f(x) = f(0) = 2b$, and $\lim_{x\to 0^+} f(x) = 3a - b$. Setting them equal gives $2b = 3a - b \implies 3a = 3b \implies a = b$.
1. **Step 3 (At $x = 2$):** $\lim_{x\to 2^-} f(x) = f(2) = 4 + 3a - b$, and $\lim_{x\to 2^+} f(x) = 3(2) - 5 = 1$. Setting $4 + 3a - b = 1$ gives $3a - b = -3$. With $a = b$, $2a = -3 \implies a = b = -\frac{3}{2}$.
**Answer:** $a = -\frac{3}{2},\quad b = -\frac{3}{2}$.

**Key Formula:** $$\lim_{x\to c} f(x) = f(c) \qquad\Big|\qquad f \text{ continuous on } [a,b] \implies f([a,b]) \text{ hits every } y_0 \text{ between } f(a), f(b)$$

**Common Mistake:** IVT requires continuity on a CLOSED interval $[a,b]$; a jump or removable hole inside $[a,b]$ can skip intermediate values.

---

## 11. Differentiability, Derivative Rules, Linearization & Extrema
*Module 3 • 03_Differentiation & PS 5*

**Plain Summary:** The derivative $f'(x)$ is the limit of secant slopes at $x$, measuring both the tangent slope and the instantaneous rate of change.

- **Derivative & One-Sided Derivatives:** $f'(x) = \lim_{h\to 0} \frac{f(x+h)-f(x)}{h} = \lim_{z\to x}\frac{f(z)-f(x)}{z-x}$. A derivative exists at $x_0$ iff left-hand and right-hand derivatives exist and are equal.
- **Differentiable $\implies$ Continuous (Converse False):** Differentiability at $c$ forces continuity at $c$. However, $f(x)=|x|$ and $f(x)=x\sin(1/x)$ ($f(0)=0$) are continuous at $0$ yet not differentiable at $0$.
- **Core Rules & Linearization:** Power, Product, Quotient, Chain, and Implicit rules apply where defined. The tangent line gives the standard linear approximation $L(x) = f(a) + f'(a)(x-a)$ and differential $dy = f'(x)\,dx$.
- **Extreme Value Theorem & Critical Points:** A continuous function on a closed interval $[a,b]$ attains an absolute max and min. Check $f$ at all **critical points** (interior points where $f'(c)=0$ or $f'(c)$ is undefined) AND at the endpoints $a, b$.

**Worked Example (03_Differentiation (Linearization) & Problem Set 5 Q7):** Find the linearization $L(x)$ of $f(x) = \sqrt{9 + x^2}$ at $a = -4$.
1. **Step 1:** Evaluate $f(-4) = \sqrt{9 + (-4)^2} = \sqrt{25} = 5$.
1. **Step 2:** Differentiate using the Chain Rule: $f'(x) = \frac{2x}{2\sqrt{9+x^2}} = \frac{x}{\sqrt{9+x^2}}$, so $f'(-4) = \frac{-4}{5}$.
1. **Step 3:** Write $L(x) = f(-4) + f'(-4)(x - (-4)) = 5 - \frac{4}{5}(x + 4) = -\frac{4}{5}x + \frac{9}{5}$.
**Answer:** $L(x) = 5 - \frac{4}{5}(x + 4) = -\frac{4}{5}x + \frac{9}{5}$.

**Key Formula:** $$f'(x) = \lim_{h\to 0}\frac{f(x+h)-f(x)}{h} \qquad\Big|\qquad L(x) = f(a) + f'(a)(x-a)$$

**Common Mistake:** Critical points include BOTH where $f'(c)=0$ AND where $f'(c)$ does NOT exist (like $x=0$ for $3x^{2/3}$), and $f'(c)=0$ alone does not guarantee an extremum (e.g. $y=x^3$ at $x=0$). Also note a slide typo in `03_Differentiation`: $y=x^4-2x^2+2$ has horizontal tangent at $(-1, 1)$, not $(-1, 2)$.

---

## 12. Rolle's Theorem, Lagrange MVT & Cauchy MVT
*Module 3 • 03_Differentiation & Rolle/Cauchy PDF*

**Plain Summary:** If a smooth curve starts and ends at the same height, it must have a flat tangent somewhere in between (Rolle); tilting that picture gives the Mean Value Theorems connecting secant slopes to instantaneous derivatives.

- **First Derivative (Fermat) Theorem:** If $f$ has a local extremum at an interior point $c$ and $f'(c)$ exists, then $f'(c) = 0$.
- **Rolle's Theorem:** If $f$ is continuous on $[a,b]$, differentiable on $(a,b)$, and $f(a)=f(b)$, then $\exists c \in (a,b)$ with $f'(c) = 0$. Used to show uniqueness of roots (between two roots of $f$, $f'$ has a root).
- **Lagrange Mean Value Theorem (LMVT):** If $f$ is continuous on $[a,b]$ and differentiable on $(a,b)$, then $\exists c \in (a,b)$ with $f'(c) = \frac{f(b)-f(a)}{b-a}$. Corollaries: $f' \equiv 0$ on $(a,b) \implies f$ is constant; $f' \equiv g' \implies f - g$ is constant.
- **Cauchy Mean Value Theorem:** If $f,g$ are continuous on $[a,b]$, differentiable on $(a,b)$, and $g'(x) \ne 0$ on $(a,b)$ (with $g(b) \ne g(a)$), then $\exists c \in (a,b)$ with $\frac{f'(c)}{g'(c)} = \frac{f(b)-f(a)}{g(b)-g(a)}$.

**Worked Example (03_Differentiation (Rolle + IVT Example)):** Show that the equation $x^3 + 3x + 1 = 0$ has exactly one real solution.
1. **Step 1 (Existence via IVT):** Let $f(x) = x^3 + 3x + 1$, which is continuous everywhere. Since $f(-1) = -3 < 0$ and $f(0) = 1 > 0$, by IVT there is at least one real root in $(-1, 0)$.
1. **Step 2 (Uniqueness via Rolle):** Suppose there were two distinct real roots $a < b$ with $f(a) = f(b) = 0$. Since $f$ is a polynomial, it satisfies Rolle's hypotheses on $[a, b]$.
1. **Step 3 (Contradiction):** By Rolle's Theorem, $\exists c \in (a, b)$ with $f'(c) = 0$. But $f'(x) = 3x^2 + 3 \ge 3 > 0$ for all $x$, impossible. Thus there is exactly one real root.
**Answer:** Exactly one real root (exists by IVT, unique by Rolle's Theorem).

**Key Formula:** $$f'(c) = \frac{f(b)-f(a)}{b-a} \qquad\Big|\qquad \frac{f'(c)}{g'(c)} = \frac{f(b)-f(a)}{g(b)-g(a)}$$

**Common Mistake:** Always verify continuity on the CLOSED interval $[a,b]$ and differentiability on the OPEN interval $(a,b)$ before applying Rolle's Theorem or LMVT — e.g. $f(x) = |x|$ on $[-1, 1]$ has $f(-1) = f(1) = 1$ yet $f'(c) \ne 0$ because differentiability fails at $x = 0$.

---

## 13. Riemann Partitions, Darboux Sums & Integrability
*Module 4 • 04_Riemann Integration & PS 6*

**Plain Summary:** We trap the area under a bounded curve $f$ on $[a,b]$ between inner rectangles (lower sum $L$) and outer rectangles (upper sum $U$); $f$ is Riemann integrable when the gap $U - L$ can be made smaller than any $\epsilon > 0$.

- **Upper & Lower Sums:** For partition $P = \{x_0, \dots, x_n\}$ of $[a,b]$, let $M_i = \sup_{[x_{i-1},x_i]} f$ and $m_i = \inf_{[x_{i-1},x_i]} f$. Then $L(P,f) = \sum m_i \Delta x_i \le U(P,f) = \sum M_i \Delta x_i$.
- **Refinement & Bounds:** Adding points ($P_1 \subseteq P_2$) raises $L$ and lowers $U$: $L(P_1,f) \le L(P_2,f) \le U(P_2,f) \le U(P_1,f)$. For any two partitions $P_1, P_2$, $L(P_1,f) \le U(P_2,f)$, so $\underline{\int}_a^b f \le \overline{\int}_a^b f$.
- **Integrability Criterion:** A bounded $f$ is Riemann integrable ($\underline{\int} f = \overline{\int} f$) iff for every $\epsilon > 0$, there exists a partition $P$ with $U(P,f) - L(P,f) < \epsilon$. Every continuous function (and bounded function with finitely many discontinuities) on $[a,b]$ is integrable.
- **Riemann Sums:** For $c_i \in [x_{i-1}, x_i]$, $L(P,f) \le S_P = \sum f(c_i)\Delta x_i \le U(P,f)$. For continuous $f$ on equal subintervals $h = \frac{b-a}{n}$, $\lim_{n\to\infty} S_{P_n} = \int_a^b f(x)\,dx$.

**Worked Example (04_Riemann Integration Slide 57–58):** Evaluate $\int_0^1 (x + x^2)\,dx$ as the limit of right-endpoint Riemann sums.
1. **Step 1:** Divide $[0,1]$ into $n$ equal subintervals of width $\Delta x_i = \frac{1}{n}$, with right endpoints $c_i = \frac{i}{n}$ ($i = 1, \dots, n$).
1. **Step 2:** Form the Riemann sum: $S_{P_n} = \sum_{i=1}^n \left(\frac{i}{n} + \frac{i^2}{n^2}\right)\frac{1}{n} = \frac{1}{n^2}\sum_{i=1}^n i + \frac{1}{n^3}\sum_{i=1}^n i^2$.
1. **Step 3:** Substitute $\sum i = \frac{n(n+1)}{2}$ and $\sum i^2 = \frac{n(n+1)(2n+1)}{6}$: $S_{P_n} = \frac{1}{2}\left(1+\frac{1}{n}\right) + \frac{1}{6}\left(1+\frac{1}{n}\right)\left(2+\frac{1}{n}\right) \xrightarrow{n\to\infty} \frac{1}{2} + \frac{2}{6} = \frac{5}{6}$.
**Answer:** $\frac{5}{6}$

**Key Formula:** $$L(P,f) \le S_P \le U(P,f) \qquad\Big|\qquad f \in \mathcal{R}[a,b] \iff \forall\epsilon > 0,\ \exists P:\ U(P,f) - L(P,f) < \epsilon$$

**Common Mistake:** Boundedness does NOT guarantee Riemann integrability: for Dirichlet's function ($1$ on rationals, $0$ on irrationals) on $[0,1]$, $U(P,f) = 1$ and $L(P,f) = 0$ for every partition $P$, so $\overline{\int}_0^1 f = 1 \ne 0 = \underline{\int}_0^1 f$.

---

## 14. Integral Properties & Fundamental Theorem of Calculus
*Module 4 • 04_Riemann & FTC.pdf*

**Plain Summary:** The Fundamental Theorem of Calculus links derivatives and integrals as inverse operations: integrating a continuous function gives an antiderivative, and any antiderivative evaluates definite integrals directly.

- **Core Properties:** $\int_a^b f = -\int_b^a f$, $\int_a^a f = 0$, linearity, additivity $\int_a^b f + \int_b^c f = \int_a^c f$, Max-Min bound $m(b-a) \le \int_a^b f \le M(b-a)$, and domination ($f \ge g \implies \int f \ge \int g$).
- **FTC (Evaluation Form):** If $f$ is Riemann integrable on $[a,b]$ and $F$ is differentiable on $[a,b]$ with $F' = f$, then $\int_a^b f(x)\,dx = F(b) - F(a)$ (proved by telescoping $F(x_i)-F(x_{i-1}) = f(t_i)\Delta x_i$ via MVT).
- **FTC (Derivative of Integral Form):** If $f$ is Riemann integrable on $[a,b]$, $F(x) = \int_a^x f(t)\,dt$ is continuous on $[a,b]$. If $f$ is continuous on $[a,b]$, then $F$ is differentiable and $F'(x) = f(x)$.
- **Chain Rule with Variable Limits:** $\frac{d}{dx}\int_{u(x)}^{v(x)} f(t)\,dt = f(v(x))v'(x) - f(u(x))u'(x)$ when $f$ is continuous and $u, v$ are differentiable.

**Worked Example (Problem Set 6 (Tutorial on Module 3 RI) Q6(ii) & Q7):** Compute (a) $F'(x)$ for $F(x) = \int_{-x^4}^{\sqrt{x}} \frac{t^2}{1+t^4}\,dt$ ($x > 0$); (b) $G''(x)$ for $G(x) = x\int_2^x \cos(t^3)\,dt$.
1. **Step 1 (Part a):** Split at $0$ and apply FTC + Chain Rule: $F'(x) = \frac{(\sqrt{x})^2}{1+(\sqrt{x})^4}\cdot \frac{d}{dx}(\sqrt{x}) - \frac{(-x^4)^2}{1+(-x^4)^4}\cdot \frac{d}{dx}(-x^4)$.
1. **Step 2 (Part a simplify):** $F'(x) = \frac{x}{1+x^2}\cdot\frac{1}{2\sqrt{x}} - \frac{x^8}{1+x^{16}}(-4x^3) = \frac{\sqrt{x}}{2(1+x^2)} + \frac{4x^{11}}{1+x^{16}}$.
1. **Step 3 (Part b):** By the Product Rule and FTC, $G'(x) = \int_2^x \cos(t^3)\,dt + x\cos(x^3)$. Differentiating again gives $G''(x) = \cos(x^3) + \cos(x^3) - 3x^3\sin(x^3) = 2\cos(x^3) - 3x^3\sin(x^3)$.
**Answer:** (a) $\frac{\sqrt{x}}{2(1+x^2)} + \frac{4x^{11}}{1+x^{16}}$; (b) $2\cos(x^3) - 3x^3\sin(x^3)$.

**Key Formula:** $$\int_a^b f(x)\,dx = F(b) - F(a) \qquad\Big|\qquad \frac{d}{dx}\int_a^x f(t)\,dt = f(x)$$

**Common Mistake:** Do not pull the variable $x$ outside an integral blindly before differentiating unless it is independent of $t$ (as in $x\int_2^x \cos(t^3)\,dt$, where you MUST use the Product Rule!), and never forget the chain-rule factor $v'(x)$ or minus sign on the lower limit $u'(x)$.

---

## 15. R^2 Regions, Limits, Partial Derivatives & Gradient
*Module 5 • 05_Partial Derivatives & Practice Problems*

**Plain Summary:** In two variables, $(x,y)$ can approach $(x_0, y_0)$ along infinitely many curves, not just left and right; partial derivatives slice along the $x$ and $y$ axes, and the gradient vector points in the steepest uphill direction.

- **Regions in $\mathbb{R}^2$:** A set is **open** if every point has a disk inside the set (e.g. $x^2+y^2 < 1$), and **closed** if it contains all its boundary points (e.g. $x^2+y^2 \le 1$). Bounded sets lie inside some finite disk.
- **$\epsilon$-$\delta$ Limits & Two-Path Test:** $\lim_{(x,y)\to(x_0,y_0)} f(x,y) = L$ means $0 < \sqrt{(x-x_0)^2+(y-y_0)^2} < \delta \implies |f(x,y)-L| < \epsilon$. If two paths to $(x_0,y_0)$ (like $y=mx$ or $y=kx^2$) give different limits, the limit does not exist.
- **Partial Derivatives:** $\frac{\partial f}{\partial x}(x_0,y_0) = \lim_{h\to 0}\frac{f(x_0+h,y_0)-f(x_0,y_0)}{h}$ (hold $y$ constant), and $\frac{\partial f}{\partial y}(x_0,y_0) = \lim_{h\to 0}\frac{f(x_0,y_0+h)-f(x_0,y_0)}{h}$ (hold $x$ constant).
- **Directional Derivative & Gradient (`Practice Problems.jpg` Q17–18):** For a differentiable function $f(x,y)$, the directional derivative along unit vector $\mathbf{u}$ is $D_{\mathbf{u}} f(P_0) = (\nabla f \cdot \mathbf{u})_{P_0}$, and $f$ increases most rapidly at $P_0$ in the direction of $\nabla f(P_0) = (f_x, f_y)$.

**Worked Example (05_Partial Derivatives & Practice Problems.jpg Q18):** (a) Find $\frac{\partial f}{\partial x}$ and $\frac{\partial f}{\partial y}$ at $(4,-5)$ for $f(x,y) = x^2+3xy+y-1$. (b) Find the direction of most rapid increase of $g(x,y) = \frac{x^2}{2} + \frac{y^2}{2}$ at $(1,1)$.
1. **Step 1 (Part a):** Hold $y$ constant: $\frac{\partial f}{\partial x} = 2x + 3y$, so at $(4,-5)$ it is $2(4) + 3(-5) = -7$.
1. **Step 2 (Part a):** Hold $x$ constant: $\frac{\partial f}{\partial y} = 3x + 1$, so at $(4,-5)$ it is $3(4) + 1 = 13$.
1. **Step 3 (Part b):** Compute $\nabla g(x,y) = \left(\frac{\partial g}{\partial x}, \frac{\partial g}{\partial y}\right) = (x, y)$. At $(1,1)$, $\nabla g(1,1) = (1, 1)$, so the unit direction of fastest increase is $\frac{(1,1)}{\sqrt{2}} = \left(\frac{1}{\sqrt{2}}, \frac{1}{\sqrt{2}}\right)$.
**Answer:** (a) $f_x(4,-5) = -7,\ f_y(4,-5) = 13$; (b) direction $(1,1)$ (unit vector $\frac{1}{\sqrt{2}}(1,1)$).

**Key Formula:** $$0 < \sqrt{(x-x_0)^2+(y-y_0)^2} < \delta \implies |f(x,y)-L| < \epsilon \qquad\Big|\qquad D_{\mathbf{u}}f = \nabla f \cdot \mathbf{u}$$

**Common Mistake:** Checking only straight lines $y = mx$ is NOT enough to prove a 2D limit exists! For $f(x,y) = \frac{2x^2y}{x^4+y^2}$, every line $y=mx$ gives limit $0$ at $(0,0)$, yet along the parabola $y = kx^2$ the limit is $\frac{2k}{1+k^2}$, so the limit does not exist.

---

## Practice Questions (26)
### Q1. Midsem Jan 2021 Q1 (Midsem / Endsem)
Calculate $\lim_{n\to\infty}(\sqrt{n^2+n} - n)$ and justify your answer using the $\epsilon$-$N$ definition of convergence.
- **Hint:** Rationalize the numerator by multiplying by $\frac{\sqrt{n^2+n}+n}{\sqrt{n^2+n}+n}$, then bound the error $|a_n - 1/2|$ from above.
- **Solution:** Multiply numerator and denominator by $\sqrt{n^2+n}+n$:
$$a_n = \frac{n}{\sqrt{n^2+n}+n} = \frac{1}{\sqrt{1+1/n}+1} \to \frac{1}{2}.$$
For the $\epsilon$-$N$ proof:
$$\left|a_n - \frac{1}{2}\right| = \left|\frac{n}{\sqrt{n^2+n}+n} - \frac{1}{2}\right| = \frac{\sqrt{n^2+n}-n}{2(\sqrt{n^2+n}+n)} = \frac{1}{2\left(\sqrt{1+1/n}+1\right)^2 \cdot n} < \frac{1}{8n}.$$
Given $\epsilon > 0$, choose $N = \lfloor 1/(8\epsilon) \rfloor + 1$; then for all $n \ge N$, $|a_n - 1/2| < 1/(8n) < \epsilon$.

### Q2. Midsem Jan 2021 Q3 (Midsem / Endsem)
Test the convergence of the sequence $\{a_n\}$ where $a_1 = 2$ and $a_{n+1} = \frac{2+a_n}{a_n+1}$ for $n \ge 1$, and find its limit.
- **Hint:** Notice $a_{n+1} = 1 + \frac{1}{a_n+1}$, and compute $a_{n+1} - \sqrt{2}$ in terms of $a_n - \sqrt{2}$ (or compare odd/even subsequences).
- **Solution:** 1) Positivity & bounds: $a_1 = 2 > 0$, so $a_n > 0$ for all $n$, and $1 < a_{n+1} = 1 + \frac{1}{a_n+1} < 2$.
2) Contraction toward $\sqrt{2}$: 
$$|a_{n+1} - \sqrt{2}| = \left|\frac{2+a_n}{a_n+1} - \sqrt{2}\right| = \frac{|(1-\sqrt{2})a_n + (2-\sqrt{2})|}{a_n+1} = \frac{(\sqrt{2}-1)|a_n - \sqrt{2}|}{a_n+1}.$$
Since $a_n > 1$, $\frac{\sqrt{2}-1}{a_n+1} < \frac{\sqrt{2}-1}{2} < \frac{1}{2}$. Thus $|a_{n+1} - \sqrt{2}| \le \left(\frac{1}{2}\right)^n |a_1 - \sqrt{2}| \to 0$.
Hence $\{a_n\}$ converges to $\sqrt{2}$.

### Q3. Quiz 1 (Aug 2019) Q5 (Quiz / Lab)
Prove or disprove that the sequence $a_1 = 1$, $a_n = \sqrt{1 + 2a_{n-1}}$ ($n \ge 2$) is convergent. If it converges, find its limit.
- **Hint:** Check $a_1 < a_2$ and use induction to show $a_n$ is increasing and bounded above by $3$.
- **Solution:** 1) Bounded above by $3$: $a_1 = 1 < 3$. If $a_{n-1} < 3$, then $a_n = \sqrt{1 + 2a_{n-1}} < \sqrt{1 + 6} = \sqrt{7} < 3$.
2) Increasing: $a_n^2 - a_{n-1}^2 = 1 + 2a_{n-1} - a_{n-1}^2$ — even simpler, compare $a_1 = 1 < a_2 = \sqrt{3}$, and if $a_n > a_{n-1}$ then $1 + 2a_n > 1 + 2a_{n-1} \implies a_{n+1} > a_n$.
3) By the Monotone Convergence Theorem, $a_n \to L$. Then $L = \sqrt{1 + 2L} \implies L^2 - 2L - 1 = 0 \implies L = 1 \pm \sqrt{2}$. Since $a_n \ge 1$, the limit is $1 + \sqrt{2}$.

### Q4. Problem Set 1 Q3(b) / Assignment 1 Q1 (Assignment / Tutorial)
Find the limit of the sequence $a_n = \left(1 + \frac{3}{4n}\right)^{\frac{8n}{3}}$.
- **Hint:** Rewrite the exponent in terms of $\frac{4n}{3}$, or take $\ln a_n$ and use L'Hôpital's rule.
- **Solution:** Rewrite $a_n = \left[\left(1 + \frac{3}{4n}\right)^{\frac{4n}{3}}\right]^2$.
Using $\lim_{m\to\infty}\left(1 + \frac{1}{m}\right)^m = e$ (with $m = \frac{4n}{3} \to \infty$), the inner expression converges to $e$.
By continuity of $x \mapsto x^2$, $\lim_{n\to\infty} a_n = e^2$.

### Q5. Assignment 1 Q5 & Problem Set 1 Q10 (Assignment / Tutorial)
Find $\lim_{n\to\infty} a_n$ for (a) $a_n = \frac{1}{n^2+1} + \frac{1}{n^2+2} + \dots + \frac{1}{n^2+n}$ and (b) $b_n = \frac{1}{(n+1)^2} + \frac{1}{(n+2)^2} + \dots + \frac{1}{(2n)^2}$.
- **Hint:** Bound all $n$ terms between $n \cdot (\text{smallest term})$ and $n \cdot (\text{largest term})$ and apply the Sandwich Theorem.
- **Solution:** (a) $\frac{n}{n^2+n} \le a_n \le \frac{n}{n^2+1}$. Both $\frac{n}{n^2+n} \to 0$ and $\frac{n}{n^2+1} \to 0$, so by the Sandwich Theorem $a_n \to 0$.
(b) $\frac{n}{(2n)^2} \le b_n \le \frac{n}{(n+1)^2}$, i.e. $\frac{1}{4n} \le b_n \le \frac{n}{(n+1)^2}$. Both bounds converge to $0$, so $b_n \to 0$.

### Q6. Midsem (MAT104T) Q1.3 (Quiz / Lab)
A ball is dropped from a height of $1\text{ m}$ and bounces back to half of its height every time. What total distance does it travel before coming to rest?
- **Hint:** Add the initial $1\text{ m}$ drop to twice the infinite sum of rebound heights $\frac{1}{2} + \frac{1}{4} + \frac{1}{8} + \dots$.
- **Solution:** The ball falls $1\text{ m}$, then bounces up $\frac{1}{2}\text{ m}$ and falls $\frac{1}{2}\text{ m}$, bounces up $\frac{1}{4}\text{ m}$ and falls $\frac{1}{4}\text{ m}$, etc.:
$$D = 1 + 2\left(\frac{1}{2} + \frac{1}{4} + \frac{1}{8} + \dots\right) = 1 + 2\cdot \frac{1/2}{1 - 1/2} = 1 + 2(1) = 3\text{ m}.$$

### Q7. Midsem Jan 2021 Q4 (Midsem / Endsem)
Discuss the convergence of $\sum_{n=2}^\infty \frac{1}{(\ln n)^p}$, where $p$ is a real constant.
- **Hint:** Split into $p \le 0$ (use the $n$-th Term Test) and $p > 0$ (compare $(\ln n)^p$ with $n$ as $n \to \infty$).
- **Solution:** Case 1 ($p \le 0$): $(\ln n)^{-p} \not\to 0$ as $n \to \infty$, so the series diverges by the $n$-th Term Test.
Case 2 ($p > 0$): By L'Hôpital's rule, $\lim_{n\to\infty} \frac{(\ln n)^p}{n} = 0$, so $(\ln n)^p < n$ for all sufficiently large $n$. Thus $\frac{1}{(\ln n)^p} > \frac{1}{n}$ eventually. Since $\sum \frac{1}{n}$ diverges, the series diverges by the Comparison Test.
Hence the series diverges for every $p \in \mathbb{R}$.

### Q8. Midsem Jan 2021 Q7 (Midsem / Endsem)
Test the convergence of $\sum_{n=1}^\infty (-1)^{n+1}\frac{(n+1)(n+2)}{2^n}$ and find its sum if it converges.
- **Hint:** Test absolute convergence with the Ratio Test. To find the sum, differentiate $\sum_{n=0}^\infty x^{n+2} = \frac{x^2}{1-x}$ or $\sum_{n=0}^\infty x^n = \frac{1}{1-x}$ twice.
- **Solution:** 1) Absolute convergence: $\left|\frac{a_{n+1}}{a_n}\right| = \frac{(n+2)(n+3)}{2^{n+1}} \cdot \frac{2^n}{(n+1)(n+2)} = \frac{n+3}{2(n+1)} \to \frac{1}{2} < 1$. So the series converges absolutely (hence converges).
2) Exact sum: For $|x| < 1$, differentiating $\frac{1}{1-x} = \sum_{n=0}^\infty x^n$ twice gives
$$\frac{2}{(1-x)^3} = \sum_{n=0}^\infty (n+1)(n+2)x^n = 2 + \sum_{n=1}^\infty (n+1)(n+2)x^n.$$
Setting $x = -\frac{1}{2}$ yields $\sum_{n=1}^\infty (-1)^n \frac{(n+1)(n+2)}{2^n} = \frac{2}{(3/2)^3} - 2 = \frac{16}{27} - 2 = -\frac{38}{27}$.
Multiplying by $-1$ gives $\sum_{n=1}^\infty (-1)^{n+1}\frac{(n+1)(n+2)}{2^n} = \frac{38}{27}$.

### Q9. Problem Set 2 Q1 / Assignment 1 Q11 (Assignment / Tutorial)
For what values of $r$ does the series $1 + 2r + r^2 + 2r^3 + r^4 + 2r^5 + \dots$ converge? Find its sum when it converges.
- **Hint:** Split into even powers ($1 + r^2 + r^4 + \dots$) and odd powers ($2r + 2r^3 + 2r^5 + \dots$), and check $|r| \ge 1$ with the $n$-th Term Test.
- **Solution:** If $|r| \ge 1$, the general term does not converge to $0$, so the series diverges by the $n$-th Term Test.
If $|r| < 1$, both geometric subseries $\sum_{k=0}^\infty r^{2k} = \frac{1}{1-r^2}$ and $\sum_{k=0}^\infty 2r^{2k+1} = \frac{2r}{1-r^2}$ converge. Adding them gives:
$$S = \frac{1 + 2r}{1 - r^2} \quad (|r| < 1).$$

### Q10. Problem Set 3 Q4–5 (Assignment / Tutorial)
Compute the exact sums: (a) $\sum_{n=0}^\infty \left(\frac{4}{(-3)^n} - \frac{3}{3^n}\right)$ and (b) $\sum_{n=0}^\infty \left(\frac{3}{2^n} + \frac{4}{5^n}\right)$.
- **Hint:** Each term splits into two convergent geometric series starting at $n=0$ with $|r| < 1$.
- **Solution:** (a) $\sum_{n=0}^\infty 4\left(-\frac{1}{3}\right)^n - \sum_{n=0}^\infty 3\left(\frac{1}{3}\right)^n = \frac{4}{1 - (-1/3)} - \frac{3}{1 - 1/3} = 3 - \frac{9}{2} = -\frac{3}{2}$.
(b) $\sum_{n=0}^\infty 3\left(\frac{1}{2}\right)^n + \sum_{n=0}^\infty 4\left(\frac{1}{5}\right)^n = \frac{3}{1 - 1/2} + \frac{4}{1 - 1/5} = 6 + 5 = 11$.

### Q11. Assignment 1 Q7 & Q10 (Assignment / Tutorial)
(a) Find $b$ such that $1 + e^b + e^{2b} + e^{3b} + \dots = 9$. (b) Show that $\sum_{n=1}^\infty \frac{1}{n^p}\cos\left(\frac{1}{n}\right)$ converges for $p > 1$ and diverges for $0 < p \le 1$.
- **Hint:** For (a), use geometric sum $\frac{1}{1-e^b} = 9$ with $e^b < 1$. For (b), apply the Limit Comparison Test with $b_n = 1/n^p$.
- **Solution:** (a) For convergence we need $e^b < 1$. Then $\frac{1}{1 - e^b} = 9 \implies 1 - e^b = \frac{1}{9} \implies e^b = \frac{8}{9} < 1$, so $b = \ln\left(\frac{8}{9}\right)$.
(b) Take $a_n = \frac{1}{n^p}\cos(1/n) > 0$ (since $0 < 1/n \le 1 < \pi/2$) and $b_n = \frac{1}{n^p}$. Since $\lim_{n\to\infty} \frac{a_n}{b_n} = \lim_{n\to\infty} \cos(1/n) = 1 > 0$, by the Limit Comparison Test $\sum a_n$ converges iff $\sum \frac{1}{n^p}$ converges, i.e. converges for $p > 1$ and diverges for $0 < p \le 1$.

### Q12. Endsem March 2021 Q2 (Midsem / Endsem)
Find the interval of convergence and, within it, the sum as a function of $x$: (a) $\sum_{n=0}^\infty \frac{(x-1)^{2n}}{4^n}$ and (b) $\sum_{n=0}^\infty (\ln x)^n$.
- **Hint:** Both are geometric series $\sum r^n$ which converge iff $|r| < 1$ to $\frac{1}{1-r}$.
- **Solution:** (a) Geometric series with ratio $r = \frac{(x-1)^2}{4}$. Converges iff $\left|\frac{(x-1)^2}{4}\right| < 1 \iff |x-1| < 2 \iff x \in (-1, 3)$. On $(-1, 3)$, the sum is $\frac{1}{1 - (x-1)^2/4} = \frac{4}{4 - (x-1)^2}$.
(b) Geometric series with ratio $r = \ln x$ ($x > 0$). Converges iff $|\ln x| < 1 \iff -1 < \ln x < 1 \iff x \in (e^{-1}, e)$. On $(1/e, e)$, the sum is $\frac{1}{1 - \ln x}$.

### Q13. Assignment 1 Q15(b)–(c) (Assignment / Tutorial)
Find the radius and interval of convergence of (a) $\sum_{n=1}^\infty (-1)^n \frac{x^{n+1}}{\sqrt{n+3}}$ and (b) $\sum_{n=1}^\infty \left(\frac{n}{n+1}\right)^{n^2} x^n$.
- **Hint:** Use the Ratio Test on (a) and test $x = \pm 1$; use the Root Test on (b) with $\lim (1 + 1/n)^{-n} = e^{-1}$.
- **Solution:** (a) $\left|\frac{u_{n+1}}{u_n}\right| = |x|\sqrt{\frac{n+3}{n+4}} \to |x|$, so $R = 1$. At $x = 1$: $\sum (-1)^n/\sqrt{n+3}$ converges conditionally (Alternating Series Test, while $\sum 1/\sqrt{n+3}$ diverges). At $x = -1$: $\sum (-1)^{2n+1}/\sqrt{n+3} = -\sum 1/\sqrt{n+3}$ diverges (limit comparison with $1/n^{1/2}$). Interval: $(-1, 1]$.
(b) By Root Test, $|u_n|^{1/n} = \left(\frac{n}{n+1}\right)^n |x| = \frac{|x|}{(1+1/n)^n} \to \frac{|x|}{e}$. Converges for $|x| < e$, so $R = e$. At $x = \pm e$, $|u_n| = \frac{e^n}{(1+1/n)^{n^2}} \not\to 0$ (in fact $\ln |u_n| = n - n^2\ln(1+1/n) \to 1/2$, so $|u_n| \to e^{1/2} \ne 0$). Thus it diverges at both endpoints; interval is $(-e, e)$.

### Q14. Assignment 1 Q16 & Problem Set 4 Set A Q3 (Assignment / Tutorial)
(a) Find the Taylor series of $f(x) = \cos\left(2x + \frac{\pi}{2}\right)$ about $x = \frac{\pi}{4}$. (b) Find the power series expansion of $g(x) = \frac{x}{1+2x+x^2}$ about $x=0$ and its radius of convergence.
- **Hint:** For (a), write $2x + \frac{\pi}{2} = \pi + 2\left(x - \frac{\pi}{4}\right)$. For (b), note $1+2x+x^2 = (1+x)^2$ and differentiate $\frac{1}{1+x}$.
- **Solution:** (a) $\cos\left(\pi + 2(x - \frac{\pi}{4})\right) = -\cos\left(2(x - \frac{\pi}{4})\right) = \sum_{n=0}^\infty (-1)^{n+1} \frac{2^{2n}}{(2n)!}\left(x - \frac{\pi}{4}\right)^{2n}$ ($R = \infty$).
(b) Since $\frac{1}{1+x} = \sum_{n=0}^\infty (-1)^n x^n$ for $|x| < 1$, differentiating gives $-\frac{1}{(1+x)^2} = \sum_{n=1}^\infty (-1)^n n x^{n-1}$. Multiplying by $-x$ gives $\frac{x}{(1+x)^2} = \sum_{n=1}^\infty (-1)^{n-1} n x^n = x - 2x^2 + 3x^3 - 4x^4 + \dots$, with $R = 1$.

### Q15. Assignment 2 Q9(a)–(c) (Assignment / Tutorial)
Evaluate: (a) $\lim_{y\to 0}\frac{\sin 3y \cot 5y}{y \cot 4y}$, (b) $\lim_{x\to 0} 6x^2 \cot x \csc 2x$, and (c) $\lim_{t\to 0}\sin\left(\frac{\pi}{2}\cos(\tan t)\right)$.
- **Hint:** Rewrite $\cot u = \frac{\cos u}{\sin u}$ and $\csc u = \frac{1}{\sin u}$, then group $\frac{\sin(ku)}{ku} \to 1$.
- **Solution:** (a) Rewrite as $\frac{\sin 3y}{y} \cdot \frac{\cos 5y}{\sin 5y} \cdot \frac{\sin 4y}{\cos 4y} = \frac{12}{5} \cdot \frac{\sin 3y}{3y} \cdot \frac{4y}{\sin 4y} \cdot \frac{5y}{\sin 5y} \cdot \frac{\cos 5y}{\cos 4y} \to \frac{12}{5}(1)(1)(1)(1) = \frac{12}{5}$.
(b) $6x^2 \frac{\cos x}{\sin x} \cdot \frac{1}{\sin 2x} = 3\cos x \cdot \frac{x}{\sin x} \cdot \frac{2x}{\sin 2x} \to 3(1)(1)(1) = 3$.
(c) Since $\tan t$, $\cos u$, and $\sin v$ are continuous, plug in $t=0$: $\tan 0 = 0 \implies \cos 0 = 1 \implies \sin(\pi/2) = 1$.

### Q16. Assignment 2 Q14 & Problem Set 4 Set B Q2(iv) (Assignment / Tutorial)
(a) Evaluate $\lim_{x\to 0} \frac{1 - 2\cos x + \cos 2x}{x^2}$. (b) Find $a, b, c$ such that $\lim_{x\to 0} \frac{x(a + b\cos x) + c\sin x}{x^5} = \frac{1}{60}$.
- **Hint:** Expand $\cos x$ and $\sin x$ in Maclaurin series around $x = 0$ and match powers of $x$ in the numerator.
- **Solution:** (a) Using $\cos x = 1 - \frac{x^2}{2} + O(x^4)$ and $\cos 2x = 1 - 2x^2 + O(x^4)$:
$$\frac{1 - 2(1 - x^2/2) + (1 - 2x^2) + O(x^4)}{x^2} = \frac{-x^2 + O(x^4)}{x^2} \to -1.$$
(b) Expand numerator up to $x^5$: $x(a + b(1 - \frac{x^2}{2} + \frac{x^4}{24})) + c(x - \frac{x^3}{6} + \frac{x^5}{120}) + O(x^7) = (a+b+c)x - (\frac{b}{2}+\frac{c}{6})x^3 + (\frac{b}{24}+\frac{c}{120})x^5 + O(x^7)$.
For the limit to equal $1/60$, the $x$ and $x^3$ coefficients must be $0$ and the $x^5$ coefficient must be $1/60$:
$$a+b+c = 0,\quad \frac{b}{2}+\frac{c}{6} = 0 \implies c = -3b,\quad \frac{b}{24} - \frac{3b}{120} = \frac{1}{60} \implies \frac{b}{60} = \frac{1}{60} \implies b = 1,\ c = -3,\ a = 2.$$

### Q17. Assignment 2 Q2 & Problem Set 4 Set C Q1(a) (Assignment / Tutorial)
Let $f: [0,1] \to \mathbb{R}$ be $f(x) = x$ if $x$ is rational, and $1 - x$ if $x$ is irrational. Show that $f$ is continuous at $x = \frac{1}{2}$ and discontinuous at every other point in $[0,1]$.
- **Hint:** Check $|f(x) - 1/2| = |x - 1/2|$ near $1/2$. At $c \ne 1/2$, approach $c$ via sequences of rationals and irrationals.
- **Solution:** At $x = \frac{1}{2}$: $f(1/2) = 1/2$. For any $x \in [0,1]$, $|f(x) - 1/2|$ is either $|x - 1/2|$ (rational) or $|(1-x) - 1/2| = |x - 1/2|$ (irrational). Thus $|f(x) - 1/2| = |x - 1/2| \to 0$ as $x \to 1/2$, so $f$ is continuous at $1/2$.
At $c \ne 1/2$: take rationals $r_n \to c$ and irrationals $s_n \to c$. Then $f(r_n) = r_n \to c$, whereas $f(s_n) = 1 - s_n \to 1 - c \ne c$. Hence $\lim_{x\to c} f(x)$ does not exist and $f$ is discontinuous at $c$.

### Q18. Endsem March 2021 Q6 (Midsem / Endsem)
Find the absolute maximum and minimum values of $f(x) = 3x^{2/3}$ on the closed interval $[-27, 8]$.
- **Hint:** Check critical points where $f'(x) = 0$ OR $f'(x)$ is undefined, plus both endpoints $-27$ and $8$.
- **Solution:** $f$ is continuous on $[-27, 8]$. For $x \ne 0$, $f'(x) = 2x^{-1/3} \ne 0$; at $x = 0$, $f'(0)$ does not exist, so $x = 0$ is the sole critical point.
Evaluate $f$ at critical point and endpoints:
$f(0) = 0$, $f(-27) = 3(-27)^{2/3} = 3(9) = 27$, $f(8) = 3(8)^{2/3} = 3(4) = 12$.
Absolute maximum is $27$ (at $x = -27$) and absolute minimum is $0$ (at $x = 0$).

### Q19. Problem Set 5 Q5 & Q6 (Assignment / Tutorial)
(a) Show that $(2,4)$ lies on $x^3 + y^3 - 9xy = 0$ and find the tangent and normal lines at $(2,4)$. (b) For $f(x) = x^m \sin(1/x)$ ($x \ne 0$), $f(0)=0$, find values of $m$ for which $f$ is differentiable at $0$ and for which $f'$ is continuous at $0$.
- **Hint:** Use implicit differentiation on (a). For (b), compute $\lim_{h\to 0} h^{m-1}\sin(1/h)$ and compare with $\lim_{x\to 0} f'(x)$.
- **Solution:** (a) Check: $2^3 + 4^3 - 9(2)(4) = 8 + 64 - 72 = 0$. Implicit differentiation gives $3x^2 + 3y^2 y' - 9y - 9xy' = 0 \implies y' = \frac{9y - 3x^2}{3y^2 - 9x}$. At $(2,4)$, $y' = \frac{36 - 12}{48 - 18} = \frac{24}{30} = \frac{4}{5}$. Tangent: $y - 4 = \frac{4}{5}(x - 2)$. Normal (slope $-5/4$): $y - 4 = -\frac{5}{4}(x - 2)$.
(b) $f'(0) = \lim_{h\to 0} h^{m-1}\sin(1/h)$ exists (and equals $0$) iff $m > 1$. For $x \ne 0$, $f'(x) = mx^{m-1}\sin(1/x) - x^{m-2}\cos(1/x)$; $\lim_{x\to 0} f'(x) = 0 = f'(0)$ iff $m > 2$.

### Q20. Rolle and Cauchy Problems Q1 & Problem Set 5 Q10(d) (Assignment / Tutorial)
(a) Rolle's Theorem holds for $f(x) = x^3 + bx^2 + cx$ on $[1, 2]$ at $x = \frac{4}{3}$; find $b$ and $c$. (b) If $c$ is the Rolle's point for $g(x) = \ln\left(\frac{x^2 + \alpha}{7x}\right)$ on $[3, 4]$, find $c$.
- **Hint:** Set $f(1) = f(2)$ and $f'(4/3) = 0$ in (a). In (b), set $g(3) = g(4)$ to find $\alpha$, then solve $g'(c) = 0$ in $(3,4)$.
- **Solution:** (a) $f(1) = f(2) \implies 1 + b + c = 8 + 4b + 2c \implies 3b + c = -7$. Also $f'(4/3) = 0 \implies 3\left(\frac{16}{9}\right) + \frac{8}{3}b + c = 0 \implies 8b + 3c = -16$. Solving gives $b = -5,\ c = 8$.
(b) $g(3) = g(4) \implies \frac{9+\alpha}{21} = \frac{16+\alpha}{28} \implies 4(9+\alpha) = 3(16+\alpha) \implies \alpha = 12$. Now $g'(x) = \frac{2x}{x^2+12} - \frac{1}{x} = \frac{x^2 - 12}{x(x^2+12)} = 0 \implies c = \sqrt{12} = 2\sqrt{3} \in (3,4)$.

### Q21. Rolle & Cauchy Q3 / Assignment 2 Q7 & Q12 (Assignment / Tutorial)
(a) Prove that between any two real roots of $e^x \sin x = 1$ there is at least one real root of $e^x \cos x + 1 = 0$. (b) Prove using LMVT that $\frac{x}{1+x} < \ln(1+x) < x$ for all $x > 0$.
- **Hint:** For (a), rewrite $e^x\sin x = 1$ as $\sin x - e^{-x} = 0$ and apply Rolle's Theorem. For (b), apply LMVT to $\ln(1+t)$ on $[0, x]$.
- **Solution:** (a) Notice $e^x\sin x = 1 \iff \sin x - e^{-x} = 0$. Let $h(x) = \sin x - e^{-x}$; then $h'(x) = \cos x + e^{-x} = e^{-x}(e^x\cos x + 1)$. If $a < b$ are two roots of $e^x\sin x = 1$, then $h(a) = h(b) = 0$. By Rolle's Theorem on $[a,b]$, $\exists c \in (a,b)$ with $h'(c) = 0$, so $e^c\cos c + 1 = 0$. (Note: `Rolle and Cauchy` Slide 7 wrote $f(x)=e^x\sin x - 1$ whose derivative is $e^x(\sin x + \cos x)$, whereas $e^{-x}(\sin x - e^{-x})$ matches `Assignment 2 Q7`.)
(b) Apply LMVT to $f(t) = \ln(1+t)$ on $[0, x]$ ($x > 0$): $\exists c \in (0, x)$ with $\frac{\ln(1+x) - 0}{x - 0} = \frac{1}{1+c}$. Since $0 < c < x$, $\frac{1}{1+x} < \frac{1}{1+c} < 1$, giving $\frac{x}{1+x} < \ln(1+x) < x$.

### Q22. Endsem March 2021 Q5 (Midsem / Endsem)
State and prove Cauchy's Mean Value Theorem: if $f, g$ are continuous on $[a,b]$ with $g(a) \ne g(b)$, differentiable on $(a,b)$, and $g'(x) \ne 0$ on $(a,b)$, show $\exists c \in (a,b)$ with $\frac{f'(c)}{g'(c)} = \frac{f(b)-f(a)}{g(b)-g(a)}$.
- **Hint:** Apply Rolle's Theorem to the auxiliary function $h(x) = (f(x) - f(a)) - \frac{f(b)-f(a)}{g(b)-g(a)}(g(x) - g(a))$.
- **Solution:** Define $h(x) = f(x) - f(a) - \frac{f(b)-f(a)}{g(b)-g(a)}(g(x) - g(a))$.
Since $f, g$ are continuous on $[a,b]$ and differentiable on $(a,b)$, so is $h$. Also $h(a) = 0$ and $h(b) = (f(b)-f(a)) - (f(b)-f(a)) = 0$.
By Rolle's Theorem, $\exists c \in (a,b)$ such that $h'(c) = 0$, i.e.
$$f'(c) - \frac{f(b)-f(a)}{g(b)-g(a)} g'(c) = 0 \implies \frac{f'(c)}{g'(c)} = \frac{f(b)-f(a)}{g(b)-g(a)} \quad (g'(c) \ne 0).$$

### Q23. Endsem March 2021 Q8 (Midsem / Endsem)
Consider $f(x) = x^2$ on $[1, 3]$. Find a sequence of partitions $P_n$ of $[1, 3]$ such that $\lim_{n\to\infty} L(P_n, f) = \lim_{n\to\infty} U(P_n, f)$, prove $f$ is Riemann integrable, and evaluate $\int_1^3 x^2\,dx$.
- **Hint:** Use uniform partition $x_i = 1 + \frac{2i}{n}$ ($\Delta x_i = 2/n$), note $x^2$ is increasing on $[1,3]$, and sum $\sum i$ and $\sum i^2$.
- **Solution:** Let $P_n = \{x_0, x_1, \dots, x_n\}$ with $x_i = 1 + \frac{2i}{n}$ and $\Delta x_i = \frac{2}{n}$. Since $x^2$ is increasing on $[1,3]$, $m_i = x_{i-1}^2$ and $M_i = x_i^2$.
$$U(P_n, f) = \frac{2}{n}\sum_{i=1}^n \left(1 + \frac{2i}{n}\right)^2 = \frac{2}{n}\sum_{i=1}^n \left(1 + \frac{4i}{n} + \frac{4i^2}{n^2}\right) = 2 + 4\left(1 + \frac{1}{n}\right) + \frac{4}{3}\left(1 + \frac{1}{n}\right)\left(2 + \frac{1}{n}\right) \to 2 + 4 + \frac{8}{3} = \frac{26}{3}.$$
Similarly, $U(P_n, f) - L(P_n, f) = \frac{2}{n}(3^2 - 1^2) = \frac{16}{n} \to 0$, so $L(P_n, f) \to \frac{26}{3}$ as well. Given $\epsilon > 0$, choosing $n > 16/\epsilon$ gives $U(P_n, f) - L(P_n, f) < \epsilon$, proving $f$ is Riemann integrable and $\int_1^3 x^2\,dx = \frac{26}{3}$.

### Q24. Problem Set 6 (Tutorial RI) Q1 & Q8 (Assignment / Tutorial)
(a) Compute $L(P,f)$ and $U(P,f)$ for $f(x)=x^2$ on $[0,1]$ with $P = \{0, \frac{1}{4}, \frac{2}{4}, \frac{3}{4}, 1\}$. (b) An object moves with velocity $v(t) = (t-1)^2\text{ ft/s}$ on $[0,3]$; find its average velocity.
- **Hint:** On $[0,1]$, $x^2$ is increasing so $m_i = x_{i-1}^2$ and $M_i = x_i^2$. Average velocity on $[a,b]$ is $\frac{1}{b-a}\int_a^b v(t)\,dt$.
- **Solution:** (a) Here $\Delta x_i = \frac{1}{4}$ for all $i$.
$L(P,f) = \frac{1}{4}\left(0^2 + \left(\frac{1}{4}\right)^2 + \left(\frac{2}{4}\right)^2 + \left(\frac{3}{4}\right)^2\right) = \frac{1}{4}\cdot\frac{0+1+4+9}{16} = \frac{14}{64} = \frac{7}{32}$.
$U(P,f) = \frac{1}{4}\left(\left(\frac{1}{4}\right)^2 + \left(\frac{2}{4}\right)^2 + \left(\frac{3}{4}\right)^2 + 1^2\right) = \frac{1}{4}\cdot\frac{1+4+9+16}{16} = \frac{30}{64} = \frac{15}{32}$.
(b) $v_{\text{avg}} = \frac{1}{3-0}\int_0^3 (t-1)^2\,dt = \frac{1}{3}\left[\frac{(t-1)^3}{3}\right]_0^3 = \frac{1}{9}(8 - (-1)) = 1\text{ ft/s}$.

### Q25. Endsem March 2021 Q9 & Q10 (Midsem / Endsem)
(a) In the $xy$-plane, determine whether $A = \{(x,y) \mid x^2+y^2=1,\ y \ge 0\}$ is closed and whether $B = \{(x,y) \mid x^2+y^2=1,\ y > 0\}$ is open. (b) Prove that $f(x,y) = \frac{xy}{\sqrt{x^2+y^2}}$ for $(x,y)\ne(0,0)$, $f(0,0)=0$, is continuous everywhere.
- **Hint:** For (a), check if every point of $B$ has a 2D open disk inside $B$. For (b), bound $|xy|$ by $x^2+y^2$ or $|x|\sqrt{x^2+y^2}$ for the $\epsilon$-$\delta$ proof at $(0,0)$.
- **Solution:** (a) $A$ contains all its boundary points (every point of $A$ is its own boundary point, and the circle arc with endpoints $(\pm 1, 0)$ includes its limit points), so $A$ is closed. $B$ is NOT open because any 2D disk centered at a point on the unit circle contains points with $x^2+y^2 \ne 1$ outside $B$.
(b) Away from $(0,0)$, $f$ is a quotient of continuous functions with $\sqrt{x^2+y^2} \ne 0$, hence continuous. At $(0,0)$: since $|y| \le \sqrt{x^2+y^2}$ and $|x| \le \sqrt{x^2+y^2}$,
$$|f(x,y) - 0| = \frac{|x||y|}{\sqrt{x^2+y^2}} \le |x| \le \sqrt{x^2+y^2}.$$
Given $\epsilon > 0$, choose $\delta = \epsilon$; then $0 < \sqrt{x^2+y^2} < \delta \implies |f(x,y) - 0| < \epsilon$. Thus $f$ is continuous at $(0,0)$ as well.

### Q26. Practice Problems.jpg Q16 & Q18 (Assignment / Tutorial)
(a) Prove or disprove: $f(x,y) = \sqrt{x^2+y^2}$ is differentiable everywhere. (b) Show that a differentiable $f(x,y)$ increases most rapidly at $P_0$ in the direction of $\nabla f(P_0)$, and find that direction for $g(x,y) = \frac{x^2}{2} + \frac{y^2}{2}$ at $(1,1)$.
- **Hint:** For (a), check whether $f_x(0,0)$ exists along $y=0$: $f(h,0) = |h|$. For (b), write $D_{\mathbf{u}}f = \nabla f \cdot \mathbf{u} = |\nabla f|\cos\theta$.
- **Solution:** (a) False — $f$ is NOT differentiable at $(0,0)$. Along $y=0$, $\frac{f(h,0)-f(0,0)}{h} = \frac{|h|}{h}$, whose limit as $h\to 0$ does not exist ($+1$ from right, $-1$ from left). Thus $f_x(0,0)$ does not exist, so $f$ is not differentiable at $(0,0)$.
(b) $D_{\mathbf{u}} f(P_0) = \nabla f(P_0) \cdot \mathbf{u} = |\nabla f(P_0)|\,|\mathbf{u}|\cos\theta = |\nabla f(P_0)|\cos\theta$, which is maximized when $\cos\theta = 1$ ($\theta = 0$), i.e. when $\mathbf{u}$ points in the direction of $\nabla f(P_0)$. For $g(x,y) = \frac{x^2}{2} + \frac{y^2}{2}$, $\nabla g(1,1) = (1, 1)$, so the unit direction is $\left(\frac{1}{\sqrt{2}}, \frac{1}{\sqrt{2}}\right)$.
