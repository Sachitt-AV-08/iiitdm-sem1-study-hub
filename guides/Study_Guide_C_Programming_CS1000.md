# End-Semester Exam Study Guide — Problem Solving & Programming (`CS1000`)

**Course:** Problem Solving and Programming (`CS1000`) — C Programming (IIITDM Kancheepuram)  
**Time Horizon:** Built for **< 4-day** exam readiness  
**Synthesized from:** Lecture decks (`BASICS-1`, `operators`, `conditional statements`, `functions`, `scope`, `arrays`, `strings`, `STRUCTURES`, `FILES`), `Practice - 1/2/3`, `C questions`, `C questions on NS`, `Assignment 1` (all 12 code images + sets 1–4), `Questions for Lab`, `Switch&If_else`, `COM105T Quiz 1`, `PSP Quiz 2 (Oct 2023)`, `CS1000 Midsem Dec 2022`, and `CS1000 Endsem Feb 2023` (60 marks).

---

## 1. Exam Pattern & Priority Breakdown

In `CS1000` exams (`Midsem` 30 marks, `Endsem` 60 marks), roughly **50% of marks** come from short-answer code-tracing / output / compile-error traps (MCQs & 2-mark questions), and **50% of marks** come from writing clean, bug-free C programs (**Section C**, often banning `<string.h>` functions!).

| Topic | Favorite IIITDM Exam Questions | Priority |
| :--- | :--- | :---: |
| **Number Systems & Bits** | Radix puzzles `(123)_5 = (X8)_Y`, Octal$\leftrightarrow$Hex via 3/4-bit binary, $n$-bit 2's complement ranges/overflow, bit shifting ($8\times P$, `a ^ 32`, `~0 == -1`), signed `char` wraparound | High |
| **Compilation & Tokens** | 4 stages (Edit/Preprocess $\to$ Compile $\to$ Assemble $\to$ Link $\to$ Execute), `Main()` linker error, valid C identifiers, `#define` macro & `#undef` traps | High |
| **Operators & Evaluation** | Precedence (`+` before `<<` before `<` before `&` before `&&`), `&&`/`\|\|` short-circuiting, `sizeof(expr)` NOT evaluating side-effects, `printf`/`scanf` return values, `(1,2,3)` comma operator | Very High |
| **Control Flow & `switch`** | **Semicolon trap (`if(a==5);`)**, `if(a=0)` assignment trap, missing `break` fallthrough, non-constant `case a:`, duplicate case value (`case 3:` + `case 7-4:`), `while(c--)` vs `for` trace | Very High |
| **Functions, Recursion & Scope** | Pass-by-value vs Pass-by-reference (`swap`), LIFO recursive stack order, **printing before vs after recursive call**, `static` local persistence, global vs local shadowing, `register`/`extern` | Very High |
| **Arrays, Pointers & Strings** | `arr[i]` $\equiv$ `*(arr+i)`, `*z++` vs `(*z)++`, `q - p` vs invalid `r/2`, 2D char array missing `'\0'` (`char arr[4][3]`), manual string partition/reverse without `<string.h>` | Very High |
| **Structures, Unions & Files** | `struct` pass-by-value vs `struct *` with `->`, struct assignment `p3 = p2`, `union` max member size, `fopen` modes (`r,w,a,r+,w+,a+`), `fprintf/fscanf/fgetc/fgets`, `fseek/ftell/rewind` | Very High |

---

## 2. Rapid Revision Core Notes

### 2.1 Number Systems & Signed Representation
- **Radix Equation Technique:** Convert both sides to base 10! Enforce **digit $<$ base** constraint (e.g., if `8` appears in `(X8)_Y`, then $Y \ge 9$ and $1 \le X < Y$).
- **2's Complement (Width $n$ bits):**
  - Range: $\mathbf{-2^{n-1}}$ to $\mathbf{+(2^{n-1} - 1)}$. (8-bit: $-128$ to $+127$; 16-bit: $-32768$ to $+32767$).
  - Sign-magnitude 8-bit `-9`: MSB `1`, magnitude `0001001` $\to$ `10001001`.
  - 2's complement of $-N$: invert all bits of $+N$ (1's comp) and add $1$. (Shortcut: copy bits from right up to first `1`, flip all bits to the left!).
  - **Signed `char` wraparound (`COM105T`, `C questions`):** `char val = 125; val = val + 3;` $\to 128$ overflows $+127$ into **$-128$**! `~0` is `-1` (all `1` bits!).
  - **Bitwise Arithmetic Shortcuts:** Left shift $k$ bits (`x << k`) $\approx \times 2^k$ (so `8 * P` = arithmetic/logical left shift by 3 bits, keeping 16-bit width!). Right shift by 1 (`>> 1`) divides by 2 (signed negative right shift `(-2)>>1` = `-1` on arithmetic-shift compilers).

### 2.2 C Compilation Pipeline & Preprocessor (`BASICS-1`, `FILES.ppt`)
1. **Preprocessing:** Expands `#include`, `#define` macros (pure text substitution — watch missing parentheses in `#define SQ(x) x*x` $\to$ pass `1+2` gives `1+2*1+2 = 5`!), handles `#ifdef`/`#else`/`#endif`, `#undef`. Directives end with newline, NEVER `;`.
2. **Compilation:** Syntax/semantic checks $\to$ generates assembly / `.obj` object code. *(Catches syntax errors, undeclared variables, non-constant `case` labels, duplicate `case`, dividing pointer by `2`.)*
3. **Linking:** Combines `.obj` files with library code (`stdio.h`, `math.h`). *(Catches missing `main()` — e.g., `Main()` case sensitivity error!)*
4. **Execution:** OS loads `.exe` into memory; runtime/logical errors appear here.

### 2.3 Operator Precedence & Tricky Side Effects (Top 6 Traps)
1. **Precedence Ladder (High $\to$ Low):**
   `()` `[]` `->` `.` **>** Unary `++` `--` `!` `~` `sizeof` `(type)` `&` `*` **>** `* / %` **>** `+ -` **>** `<< >>` **>** `< <= > >=` **>** `== !=` **>** `&` **>** `^` **>** `|` **>** `&&` **>** `||` **>** `?:` **>** `=` `+=` **>** `,`
   - Example: `1 << 2 + 3 << 4` evaluates `+` FIRST: `(1 << 5) << 4` $= 32 \times 16 = \mathbf{512}$!
2. **Short-Circuiting (`&&`, `||`):**
   - `A || B`: if `A` is non-zero (true), `B` is **NEVER evaluated**!
   - `A && B`: if `A` is `0` (false), `B` is **NEVER evaluated**!
3. **`sizeof()` is Compile-Time:** `int j = sizeof(i++);` does **NOT** increment `i`! (`printf` inside `sizeof(printf("hi"))` prints NOTHING and returns `4`, size of `int` return type!). Also `sizeof('a')` in C is **`4`** (character constant has type `int`), whereas `sizeof(2.5)` is **`8`** (`double`)!
4. **R-value Increment Error:** `(10++)` or `(++i)++` or `#define c 7; (++c)` $\implies$ **Compilation Error** (cannot modify a constant/r-value).
5. **Return values of `printf()` & `scanf()`:**
   - `printf("hello")` returns number of **characters printed** ($5$).
   - `scanf("%d %d", &a, &b)` returns number of **items successfully read** ($2$).
6. **Comma Operator vs Declaration:** `int i = 1, 2, 3;` is a **compile error** (comma is separator in declaration); `int i = (1, 2, 3);` evaluates left-to-right and assigns **`3`**!

### 2.4 Control Flow, Loops & `switch` Rules
- **Dangling `if` Semicolon (`if(a==5);`):** Ends the `if` immediately with an empty statement! Any `else` immediately afterward causes **Compile Error: `'else' without a previous 'if'`** (`Midsem 2022` Q4). No `else` afterward means the next `{...}` block executes unconditionally!
- **`switch(expr)` Mandatory Rules (`Quiz 2`, `Midsem 2022`):**
  1. `expr` MUST be **integer/character** (never `float`/`double`/`string`).
  2. Every `case` label MUST be a **constant integer expression** (`case 1+2:` ok; `case a:` or `case c=1:` or `case N*4:` with float `N` $\to$ **Compile Error**).
  3. All `case` values MUST be **unique** (`case 3:` and `case (7-4):` together $\to$ **Compile Error: duplicate case**!).
  4. Without `break;`, execution **falls through** all subsequent cases (including `default:` if `default` sits before cases!).
- **`for(init; cond; update)` Order:** `init` runs **once** $\to$ `cond` checked (if 0, exit; note `init` ALREADY changed the variable!) $\to$ body $\to$ `update` (`continue;` jumps straight to `update`, NOT skipping it!).
- **`do { ... } while(cond);`:** Body always executes **at least once**, even if `cond` starts false!

### 2.5 Functions, Recursion & Storage Classes
- **Call by Value vs Call by Reference:** Passing `x` sends a copy (caller unchanged); passing `&x` allows modifying caller's variable via `*px`. Arrays decay to pointers (`sum(a)` passes `&a[0]`, modifying original array!).
- **Recursion:** Needs Base Case + Recursive Case; uses **LIFO** call stack. Pay close attention to whether `printf()` is **before** (prints top-down) or **after** (prints bottom-up during unwinding) the recursive call (`Endsem 2023` Sec B Q3!).
- **4 Storage Classes (`scope.pptx`, `functions.ppt`):**

| Class | Keyword | Storage | Default Initial Value | Scope | Lifetime |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Automatic** | `auto` (default) | RAM (Stack) | Garbage | Block / Local | Till block ends |
| **External** | `extern` | RAM (Data) | `0` | Global (whole program) | Entire program |
| **Static** | `static` | RAM (Data) | **`0`** | Block / File | **Entire program** (retains value across calls!) |
| **Register** | `register` | CPU Register | Garbage | Block / Local | Till block ends (cannot use `&`!) |

### 2.6 Pointers, Strings, Structures & Files
- **Pointer Arithmetic (assume `sizeof(int) = 4`):**
  - `p + 1` adds `1 * sizeof(*p)` bytes.
  - `*p++` $\equiv$ `*(p++)`: dereferences current address, then advances pointer `p`!
  - `(*p)++` or `++(*p)`: increments the **value** pointed to!
  - `q - p` gives number of elements between two pointers of the same type; `p + q` or `p / 2` is **ILLEGAL**!
- **Strings (`strings.ppt`):**
  - Terminated by `'\0'` (ASCII `0`). `'0'` is ASCII `48`, `'A'` is `65`, `'a'` is `97`.
  - `scanf("%s", s)` stops at whitespace! Never write `&s` for a char array name.
  - `strlen(s)` returns length excluding `'\0'`; `sizeof(s)` returns total allocated array bytes!
  - `strcmp(s1, s2)` returns `0` if equal, `< 0` if `s1 < s2`, `> 0` if `s1 > s2` (case-sensitive: `'G' (71) < 'g' (103)`!).
- **Structures vs Unions (`STRUCTURES.ppt`):**
  - **Cannot initialize members inside `struct` definition** (no memory yet!). Don't forget final `;` after `}`.
  - Dot `s.member` for struct variable; Arrow `ptr->member` (same as `(*ptr).member`) for struct pointer. `p3 = p2;` performs member-wise copy!
  - `union` shares one memory block across all members: `sizeof(union)` = size of **largest member** (20 bytes in `union { int i; float f; char str[20]; }`).
- **Files (`FILES.ppt`):**
  - Pointer: `FILE *fp;` $\to$ `fp = fopen("name.txt", "mode");` (check `fp == NULL`!). Always `fclose(fp);`.
  - **Modes:** `"r"` (read existing; `NULL` if missing), `"w"` (create/overwrite; **destroys** existing contents), `"a"` (append at end; creates if missing), `"r+"` (read+write existing), `"w+"` (create/truncate + read/write), `"a+"` (read + append).
  - Text I/O: `fprintf(fp, "%d", x)`, `fscanf(fp, "%d", &x)`, `fgetc(fp)` (returns `EOF` at end), `fputc(ch, fp)`, `fgets(buf, n, fp)`, `fputs(str, fp)`.
  - Random access: `fseek(fp, offset, origin)` (`0`=`SEEK_SET`, `1`=`SEEK_CUR`, `2`=`SEEK_END`), `ftell(fp)`, `rewind(fp)`.

---

## 3. Traced Previous-Year Exam Questions (Complete Set)

### 3.1 `CS1000` Endsem Feb 2023 + Midsem Dec 2022 + Quiz 2 Tricky Traces

1. **`Endsem 2023` Sec A Q2 (Double Trap in `switch`):**
   ```c
   int a = 3, b = 4, c, d; c = b - a; d = a || b;
   switch(c) {
       case 1 || 2 && 15%5: printf("Grade S\n"); break;
       case !(10%3*5%5) && -10: printf("Grade A\n"); break;
   }
   ```
   - `c = 1`. Case 1: `15%5=0`, `2&&0=0`, `1||0 = 1`. Case 2: `10%3=1`, `1*5=5`, `5%5=0`, `!0=1`, `1&&-10 = 1`.
   - **Result:** **Compilation Error — Duplicate case value `1`**! *(Similarly `Quiz 2` Q2 had `case 3:` and `case (7-4):` $\to$ duplicate case error!)*

2. **`Endsem 2023` Sec A Q4 (`static` inside Recursion):**
   ```c
   int f(int n) { static int i = 1; if(n>=5) return n; n=n+i; i++; return f(n); }
   ```
   - Trace `f(1)`: Call 1 (`n=1, i=1` $\to n=2, i=2$) $\to$ Call 2 (`n=2, i=2` $\to n=4, i=3$) $\to$ Call 3 (`n=4, i=3` $\to n=7, i=4$) $\to$ Call 4 (`n=7 \ge 5` returns **`7`**).

3. **`Endsem 2023` Sec A Q8 (Global vs Local Shadowing):**
   `global i=10;` in `main`: local `int i=20; printf("%d", i); check(); printf("%d", ++i);` where `check()` prints `i++` (global).
   - Output: **`20 10 21`** (`check()` sees global `10` because local `i` in `main` is out of scope!).

4. **`Endsem 2023` Sec A Q10 (Pointer Increment Precedence):**
   `int x=20, y=21, *z;` (contiguous addresses `5000, 5004, 5008`): `z = &x; *z++; x++;`
   - Precedence: `++` binds to `z` BEFORE `*`! So `*z++` evaluates `*(z++)`: advances **`z`** from `5000` to `5004` (`&y`), leaving `x` at `20`! Then `x++` makes `x = 21`.
   - Prints addresses `5000, 5004, 5008`, then values `x=21, y=21, *z=21` (`(c)`).

5. **`Endsem 2023` Sec B Q3 (Recursion Order + Pass-by-Value Trap):**
   ```c
   void func(int n, int sum) { if(n==0) return; k=n%10; j=n/10; sum=sum+k; func(j, sum); printf("%d,", k); }
   ```
   - Called with `func(2048, 0)`: pushes `k=8`, `k=4`, `k=0`, `k=2`, then pops & prints **`2,0,4,8,`**. In `main()`, `sum` was passed by value so remains `0` $\implies$ **`2,0,4,8,0` (`(c)`)**.

6. **`Endsem 2023` Sec B Q4 (Pointer Parameter + Same-Name Shadow):**
   ```c
   int cal(int *i, int j) { *i = *i * *i; j = j * j; return (2*j); }
   // main: int i=5, j=2, t=5; t = cal(&i, j); j = j + t*3; i = i - t + 7;
   ```
   - `cal(&i, 2)`: `*i = 25` (`main`'s `i=25`), local `j = 4` (doesn't change `main`'s `j=2`!), returns `t = 8`.
   - Back in `main`: `j = 2 + 8*3 = 26`; `i = 25 - 8 + 7 = 24`. Output: **`24,26`**.

7. **`Endsem 2023` Sec B Q6 (`struct` Copy vs Separate Char Array):**
   `p3 = p2;` copies `{"paper", 120.0}` into `p3`. Changing `p3.productName[0] = 'P'` makes `p3.productName` `"Paper"` (independent copy, `p2` stays `"paper"`!). `p2.price = 120.0 / 4 = 30.0`. Both `p1, p2, p3` have `p3.price > p2.price` true! Prints: `Pen, 30.000000`, `paper, 30.000000`, `Paper, 120.000000`.

8. **`Endsem 2023` Sec B Q7 (`f1` vs `f2` Swap):**
   `f1(a,b)` is pass-by-value (no effect on `a=4, b=5`). `f2(&b, &c)` passes pointers: `*a` (`b=5`) and `*b` (`c=6`) are swapped so `b=6, c=5`. `printf("%d", c-a-b)` $= 5 - 4 - 6 = \mathbf{-5}$!

9. **`Endsem 2023` Sec B Q9 (`*arr2++` Pointer Increment Trap):**
   - Look at printed line `*arr2++ = ++(*(arr1 + i));` vs `arr2[i]`: With `arr2` as a pointer parameter, `*arr2++` stores into `arr2[i]` AND increments `arr2` by 1 element each iteration, while `++(*(arr1+i))` increments `arr1[i]` in place (`{2,2,3,3,3,4,4,4,4,5}` $\to$ `{3,3,4,4,4,5,5,5,5,6}`). `main` prints **`3 3 4 4 4 5 5 5 5 6`** (one per line).

10. **`Endsem 2023` Sec B Q10 (Struct Pointer Traversal):**
    `List[] = {{1,37}, {2,16}, {3,84}, {4,71}, {5,48}};` Even `val` prints `val`, odd `val` prints `val*2`:
    Output: `1 74`, `2 16`, `3 84`, `4 142`, `5 48`.

11. **`Quiz 2` Oct 2023 Traps:**
    - `c = 6; while(c--) printf("%d\t", c);` $\to$ Prints **`5 4 3 2 1 0`** (`c--` tests 6,5,4,3,2,1 as true, printing decremented value!).
    - `for(x=0; 0;) printf("success");` $\to$ `x=0` runs ONCE, then condition `0` is false $\to$ Loop does NOT run, **`x` becomes `0`**.
    - `char arr[4][3] = {"hi", "how", "are", "u"}; printf("%s", arr[2]);` $\to$ `"how"` and `"are"` fill all 3 chars with **NO room for `'\0'`**, so `arr[2]` runs directly into `arr[3]` (`"u\0"`) and prints **`areu`** (adjacent row overrun)!
    - `int x[5]={6,2,12,18,20}; p = --x[1]; r = x[p++]; printf("%d,%d",p,r);` $\to$ `--x[1]` sets `x[1]=1, p=1`. Then `x[p++]` reads `x[1]` (`1`) and increments `p` to `2` $\to$ Prints **`2,1`**.

12. **`COM105T` Quiz 1 & `Assignment 1` Code Image Traps:**
    - **`char c = 125; c = c + 3;`** $\to$ Overflows signed 8-bit char ($127$) $\to$ **`-128`**!
    - **`if (~(x ^ y))`** (`x=10, y=11`) $\to$ `10^11 = 1`, `~1 = -2` (bitwise NOT, NOT logical `!`!). Since `-2 != 0`, `if` is **TRUE** and prints `" x is equal to y "`!
    - **`int i=1024; for(; i; i>>=1) printf("program");`** $\to$ $1024, 512, 256, 128, 64, 32, 16, 8, 4, 2, 1$ $\to$ prints **`11` times**!
    - **`printf("%d", printf("AA") || printf("BB"));`** $\to$ Prints `AA` (returns `2`), short-circuits `||` (never prints `BB`), returns `1` $\to$ **`AA1`**!

### 3.2 Base & 2's Complement Exam Problems Solved (`COM105T`, `Assignment 1`, `Midsem`)
1. **`(123)_5 = (X8)_Y`:** $(123)_5 = 1(25)+2(5)+3 = 38$. Since digit `8` is in base $Y$, $Y \ge 9$, and $X \cdot Y + 8 = 38 \implies X \cdot Y = 30$. Possible pairs $(X, Y)$ with $1 \le X < Y$ and $Y \ge 9$: **`(3, 10)`**, **`(2, 15)`**, **`(1, 30)`**!
2. **`2B5.EF`$_{16}$ $\to$ Octal (`COM105T`):** Hex $\to$ 4-bit binary: `0010 1011 0101 . 1110 1111`. Regroup in 3-bit groups from decimal point: `001 010 110 101 . 111 011 110` $\to$ **`(1265.736)_8`**!
3. **`16`-bit signed $P = (\text{F87B})_{16}$, find $8 \times P$:** Note MSB is `F` (`1111`), so $P$ is negative! Subtract from `10000_16` = `0785_16` $= -(7\times 256 + 8\times 16 + 5) = -1925_{10}$ (check via shift left 3 bits: `(F87B)_16 << 3` = `(C3D8)_16`! Verify: `-1925 * 8 = -15400`; `65536 - 15400 = 50136 = C3D8_16`!). Wait: `0xF87B = 1111 1000 0111 1011`, shift left 3 dropping top 3 `1`s: `1100 0011 1101 1000` $= \mathbf{(C3D8)_{16}}$ (`-15400_10`)! No overflow because `-15400` fits in $[-32768, 32767]$!

---

## 4. Exam-Ready Full C Programs (Section C Coding Solutions)

### Program 1: Three-Digit Armstrong Number (`Midsem Dec 2022` Part C Q1)
```c
#include <stdio.h>
int main() {
    int n, orig, d, sum = 0;
    printf("Enter a 3-digit integer: ");
    scanf("%d", &n);
    orig = n;
    while (n > 0) {
        d = n % 10;
        sum += d * d * d;
        n /= 10;
    }
    if (sum == orig)
        printf("%d is an Armstrong number\n", orig);
    else
        printf("%d is not an Armstrong number\n", orig);
    return 0;
}
```

### Program 2: Segregate Even-ASCII and Odd-ASCII Characters Without `<string.h>` (`Quiz 2` Part C Q1 & `Endsem 2023` Sec C Q1)
*(In `Quiz 2`: even ASCII first, odd ASCII second, using at most 1 extra 1D array.)*
```c
#include <stdio.h>
int main() {
    char s[200], out[200];
    int i = 0, k = 0;
    printf("Enter the string\n");
    scanf("%s", s);
    // First pass: even ASCII characters
    for (i = 0; s[i] != '\0'; i++) {
        if (s[i] % 2 == 0) out[k++] = s[i];
    }
    // Second pass: odd ASCII characters
    for (i = 0; s[i] != '\0'; i++) {
        if (s[i] % 2 != 0) out[k++] = s[i];
    }
    out[k] = '\0';
    printf("%s\n", out);
    return 0;
}
```
*(For `Endsem 2023` Sec C Q1: swap the condition to odd ASCII first, even ASCII second! And for partition relative to character `ch`: 3 passes — `base[i] > ch`, then `base[i] == ch`, then `base[i] < ch`.)*

### Program 3: Pointer-Based Odd-Making Array Update (`Endsem 2023` Sec C Q2)
```c
#include <stdio.h>
void Find(int *p, int n) {
    // Pass 1: traverse using pointer *(p+i); check preceding element parity
    for (int i = 1; i < n; i++) {
        if (*(p + i) % 2 == 0 && *(p + i - 1) % 2 == 0)
            *(p + i) = *(p + i) - 1;
    }
    // Pass 2: traverse updated array with same pointer
    for (int i = 0; i < n; i++)
        printf("%d ", *(p + i));
}
int main() {
    int n, a[100];
    scanf("%d", &n);
    for (int i = 0; i < n; i++) scanf("%d", &a[i]);
    Find(a, n);
    return 0;
}
```
> [!TIP]
> **Exam Ambiguity Note (`Endsem 2023` Sec C Q2):** Notice the paper's sample `1 2 6 4 -> 1 1 5 4` matches subtracting `1` from even elements followed by an even element (`*(p+i+1)%2 == 0`), whereas strict left-to-right checking `*(p+i-1)%2 == 0` gives `1 2 5 4`. Use single-pointer indexing (`*(p+i)`) cleanly and state your neighbor check in a 1-line comment for full credit.

### Program 4: Binary String Addition & Hex/Dec Struct Conversion (`Endsem 2023` Sec C Q3)
```c
#include <stdio.h>
#include <string.h>
struct BinCalc {
    char str1[65], str2[65], str3[65];
    int dec;
    char hexd[20];
};
struct BinCalc add(struct BinCalc b) {
    int i = strlen(b.str1) - 1, j = strlen(b.str2) - 1;
    int maxl = (i > j ? i : j) + 1, carry = 0, k = maxl - 1;
    char tmp[66];
    tmp[maxl] = '\0';
    while (k >= 0) {
        int s = carry + (i >= 0 ? b.str1[i--] - '0' : 0) + (j >= 0 ? b.str2[j--] - '0' : 0);
        tmp[k--] = (s % 2) + '0';
        carry = s / 2;
    }
    if (carry) { b.str3[0] = '1'; strcpy(b.str3 + 1, tmp); }
    else strcpy(b.str3, tmp);
    return b;
}
void convert(struct BinCalc *b) {
    int dec = 0;
    for (int i = 0; b->str3[i] != '\0'; i++)
        dec = dec * 2 + (b->str3[i] - '0');
    b->dec = dec;
    sprintf(b->hexd, "%X", dec); // or manual %16 loop with "0123456789ABCDEF"
}
int main() {
    struct BinCalc x;
    scanf("%s %s", x.str1, x.str2);
    x = add(x);
    convert(&x);
    printf("%s\n%d (deci)\n%s (hexadecimal)\n", x.str3, x.dec, x.hexd);
    return 0;
}
```

### Program 5: Factors of a Number (`Endsem 2023` Sec C Q4) & Prime Function (`Lab`)
```c
#include <stdio.h>
int main() {
    int n;
    scanf("%d", &n);
    for (int i = 1; i <= n; i++)
        if (n % i == 0) printf("%d ", i);
    return 0;
}
```

### Program 6: Copy Text File & Count Characters (`FILES.ppt` Template)
```c
#include <stdio.h>
#include <stdlib.h>
int main() {
    FILE *fp1 = fopen("in.txt", "r"), *fp2 = fopen("out.txt", "w");
    if (fp1 == NULL || fp2 == NULL) { printf("Error!\n"); exit(1); }
    int ch;
    while ((ch = fgetc(fp1)) != EOF) fputc(ch, fp2);
    fclose(fp1); fclose(fp2);
    return 0;
}
```

---

## 5. Common Exam Mistakes Checklist

- [ ] **Using `=` instead of `==` inside `if` / `while`:** `if(a=0)` assigns `0` and ALWAYS evaluates false!
- [ ] **Trailing `;` on `if` or `for`:** `if(a==5);` or `for(i=0;i<5;i++);` detaches the body!
- [ ] **Forgetting `'\0'` when building strings manually:** Always set `out[k] = '\0';` after character loops!
- [ ] **Using `str1 == str2` to compare strings:** That compares memory addresses! Always use `strcmp(str1, str2) == 0` or a manual char loop.
- [ ] **Passing value instead of address to `scanf`:** `scanf("%d", &n);` needs `&`, while `scanf("%s", str);` does NOT (`str` is already an address).
- [ ] **Modifying pointers vs values:** `*p++` moves the pointer; `(*p)++` increments the value!
- [ ] **Modifying `void` vs `int` / function prototypes:** Returning a value from a `void` function or forgetting prototype before `main()` when return type isn't `int`.
- [ ] **`fgetc` type:** Store `fgetc(fp)` in an `int` (not `char`) when comparing `!= EOF`, and open `"r"` only on existing files (`fp == NULL` guard!).
