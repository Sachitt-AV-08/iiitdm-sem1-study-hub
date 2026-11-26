# CS1000: C Programming

> In CS1000 (Problem Solving and Programming), questions focus on tracing short C programs step by step, spotting compile-time errors (invalid identifiers, non-constant `switch` labels, missing `;` or `{}`), and writing clean logic without forbidden library functions when specified (`PSP Quiz 2.pdf`, `QP.pdf`).

## Syllabus Topics
- [ ] **C Basics, Compilation & Number Systems** (FOUNDATION)
- [ ] **Operators, Precedence & Short-Circuiting** (MUST KNOW)
- [ ] **Conditionals: if-else & switch-case** (MUST KNOW)
- [ ] **Loops & Jump Statements** (MUST KNOW)
- [ ] **Functions, Parameter Passing & Recursion** (HIGH YIELD)
- [ ] **Scope Rules & Storage Classes** (HIGH YIELD)
- [ ] **1D & 2D Arrays and Pointers** (MUST KNOW)
- [ ] **Strings & Character Arrays** (MUST KNOW)
- [ ] **Structures & Unions** (HIGH YIELD)
- [ ] **File I/O & Preprocessor Directives** (CORE)

## 1. C Basics, Compilation Phases & Number Systems
*BASICS-1.pptx, Quiz _19.jpg & Practice - 2.pptx*

**Plain Summary:** A C program turns human-readable source text into machine instructions in four steps: edit, compile, link, and execute. Every variable has a fixed byte size and type, and negative integers are stored in 2's complement form.

- **Computer & Algorithms (`BASICS-1.pptx`):** CPU contains Memory, Control Unit, and ALU; RAM is volatile while ROM is non-volatile. Algorithms use Sequence, Selection, and Iteration and must be finite and definite.
- **6 C Tokens (`BASICS-1.pptx`):** Keywords (32 lowercase reserved words like `int`, `static`, `return`), Identifiers, Constants (decimal, octal leading `0`, hex leading `0x`, `'a'`, `"str"`), Strings, Special Symbols (`{}`, `()`, `[]`, `;`, `,`, `.`), and Operators.
- **I/O Statements (`BASICS-1.pptx`):** `#include <stdio.h>` provides `printf()` and `scanf()`. `scanf("%d", &a)` requires the address operator `&` so input is stored at `a`'s memory location.
- **2's Complement (`Practice - 2.pptx`, `Quiz _19.jpg`):** Invert all bits and add `1` to negate a number. With `n` bits in 2's complement, the range is `-2^(n-1)` to `2^(n-1) - 1` (for 8 bits: `-128` to `+127`).

| Concept | Details from CS1000 Slides | Example / Specifier |
| --- | --- | --- |
| Program Phases | Edit (`.c`) -> Compile (`.obj`/`.o`) -> Link libraries -> Execute (`.exe`) | `stdio.h`, `math.h` |
| Identifier Rules | Start with letter or `_`; only letters, digits, `_`; no spaces or keywords; case-sensitive | Valid: `int_t`; Invalid: `group one`, `Price$` |
| `char` (1 byte) | Signed: `-128` to `127`; Unsigned: `0` to `255` | `%c`, `char gender = 'F';` |
| `int` (2 or 4 bytes) | Signed integer (2B: `-32,768..32,767`; 4B: `-2,147,483,648..2,147,483,647`) | `%d` or `%i` |
| `float` / `double` | `float` 4 bytes (6 dec places); `double` 8 bytes (14 dec places) | `%f` / `%lf` |

**Worked Example (Previous Years Quiz _19.jpg Q7(c) & IMG-20190828-WA0002.jpg Q8):** Trace signed 8-bit `char` overflow in C and explain why `Main()` fails to link.
```c
#include <stdio.h>
int main(void)
{
    char c = 125;
    c = c + 3;
    printf("%d", c);
    return 0;
}
```
1. `char` is 1 byte (8 bits), signed range `-128` to `127` (`BASICS-1.pptx` Slide 47).
1. In binary, `125` is `0111 1101`. Adding `3` gives `1000 0000` (`128` unsigned).
1. With a leading sign bit `1` in 8-bit 2's complement, `1000 0000` represents `-128`.
1. In `Quiz _19` / `WA0002` Q8 (`int Main()`), C is case-sensitive: the linker looks for `main` and reports an undefined reference to `main`.
**Answer:** Output: `-128` (for `c = 125 + 3` in signed 8-bit `char`); `Main()` causes a linker error because `main` is missing.

**Key Formula:** `scanf("%d", &var);` | `n`-bit 2's complement range: `-2^(n-1)` to `2^(n-1) - 1` | `printf()` returns number of characters printed

**Common Mistake:** Forgetting `&` in `scanf("%d", a)` passes a garbage value instead of `a`'s address, and writing `Main()` instead of `main()` fails linking because C is case-sensitive.

---

## 2. Operators, Precedence & Short-Circuiting
*operators.pptx, Practice - 1.pptx & Midsem Dec 2022*

**Plain Summary:** C evaluates expressions by operator precedence first and associativity second, not blindly left to right. Logical `&&` and `||` stop early (short-circuit) as soon as the left side already decides the truth value.

- **Integer Division & Modulo (`BASICS-1.pptx`):** Dividing two `int` values truncates the fraction (`9 / 4 == 2`, `2 / 3 == 0`), while `%` gives the remainder (`9 % 4 == 1`).
- **Pre vs Post `++`/`--` (`BASICS-1.pptx`, `operators.pptx`):** `++a` increments first then uses the new value; `a++` uses the old value first then increments.
- **Short-Circuit `&&` and `||` (`Practice - 1.pptx`):** In `A || B`, if `A` is non-zero (true), `B` is NOT evaluated. In `A && B`, if `A` is `0` (false), `B` is NOT evaluated.
- **Bitwise vs Logical (`operators.pptx`, `Assignment 1`):** Logical `!x` turns non-zero to `0` and `0` to `1`. Bitwise `~x` flips every bit (`~0 == -1`, `~1 == -2`, both non-zero/true in `if`).
- **`sizeof` Is Compile-Time (`Practice - 1.pptx` Slide 11):** `sizeof(i++)` returns the byte size of `i`'s type without evaluating `i++`, so `i` does not change.

| Category | Operators (High to Low) | Associativity |
| --- | --- | --- |
| Postfix & Unary | `() [] -> . ++ --`  then  `+ - ! ~ ++ -- (type) * & sizeof` | Postfix L->R; Unary R->L |
| Arithmetic & Shift | `* / %`  then  `+ -`  then  `<< >>` | Left to right |
| Relational & Equality | `< <= > >=`  then  `== !=` (return `1` or `0`) | Left to right |
| Bitwise | `&` (AND)  then  `^` (XOR)  then  `|` (OR) | Left to right |
| Logical & Ternary | `&&`  then  `||`  then  `?:` | `&&`, `||` L->R; `?:` R->L |
| Assignment & Comma | `= += -= *= /= %= >>= <<= &= ^= |=`  then  `,` | Assign R->L; Comma L->R |

**Worked Example (Practice - 1.pptx Slide 5 & Slide 23):** Find the exact output of this short-circuit and precedence program.
```c
#include <stdio.h>
int main(void)
{
    int a = 1, b = 1;
    int c = a || --b;
    int d = a-- && --b;
    printf("a = %d, b = %d, c = %d, d = %d", a, b, c, d);
    return 0;
}
```
1. Line 5 (`a || --b`): `a` is `1` (true), so `||` short-circuits; `--b` is skipped (`b` stays `1`), and `c = 1`.
1. Line 6 (`a-- && --b`): `a--` uses `1` (true) and sets `a = 0`. Since the left side was true, `--b` MUST run: `b` becomes `0`.
1. `1 && 0` evaluates to `0`, so `d = 0`.
**Answer:** Output: `a = 0, b = 0, c = 1, d = 0`.

**Key Formula:** `cond ? expr1 : expr2` | `&&` has higher precedence than `||` | `+ -` have higher precedence than `<< >>`

**Common Mistake:** Never modify the same variable twice without a sequence point (e.g. `b = a++ + a++;`), and watch chained comparisons like `a == b == 0`: `==` goes left-to-right, so `(3 == 2) == 0` evaluates to `0 == 0`, which is `1`!

---

## 3. Conditionals: if-else & switch-case
*conditional statements.ppt, PSP Quiz 2.pdf & Midsem Dec 2022*

**Plain Summary:** An `if` treats `0` as false and ANY non-zero value (even `-1` or `printf()`'s character count) as true. A `switch` jumps directly to the matching integer constant `case` label and keeps falling down until it hits `break;`.

- **`if` / `else if` Ladder (`conditional statements.ppt`):** Conditions are tested top to bottom; only the first true branch executes. Without `{ }`, `if` controls only the single next statement.
- **Non-Zero Means True (`Practice - 2.pptx`, `Assignment 1`):** `if (-1)` and `if (printf("hello"))` (returns `5`) are both TRUE; `if (0)` is FALSE.
- **`switch` Expression & Labels (`conditional statements.ppt` S13):** `switch(expr)` requires an integer or `char` expression. Every `case` label MUST be a unique integer constant expression (e.g. `case 'a':` or `case 1+2:`).
- **Fall-Through & `default` Placement (`conditional statements.ppt` S13-14):** Omitting `break;` lets execution fall into the next `case` (or `default`). `default` can appear anywhere inside `switch` and runs only if no `case` matches (or via fall-through).

**Worked Example (Midsem Dec 2022 Part B Q1 (QP.pdf p. 2)):** Find the output of this `switch` program with character constant arithmetic.
```c
#include <stdio.h>
int main(void)
{
    int ch = ('a' + 'b' * 'c') % 2;
    switch (ch)
    {
        case 'a':
        case 'b':
            printf("\nYou entered b");
        case 'A':
            printf("\nYou entered in A");
        case ('b' * 'c' + 'a') % 2:
            printf("\nYou are performing arithmetic operation.");
    }
    printf("\nYou are outside the switch");
    return 0;
}
```
1. `'a'` is `97`, `'b'` is `98`, `'c'` is `99`. Since `97 + 98*99 = 9799` is odd, `ch = 9799 % 2 = 1`.
1. `('b' * 'c' + 'a') % 2` is a valid integer constant expression equal to `1` (`case 1:`), so there is NO compile error.
1. `switch(ch)` jumps to that last `case`, prints the arithmetic message, exits `switch`, and prints the outside line.
**Answer:** Output:
`You are performing arithmetic operation.`
`You are outside the switch`

**Key Formula:** `switch(int_or_char) { case CONST: ... break; default: ... }` | Any non-zero value is true in `if`

**Common Mistake:** A stray semicolon `if (a == 5);` ends the `if` immediately! If an `else` follows `{ ... }`, the compiler rejects it (`'else' without a previous 'if'`), as tested in `Midsem Dec 2022 Part A Q4`. Also `case i:` (variable), `case 1.5:` (float), and duplicate `case 3:` + `case 7-4:` (`PSP Quiz 2.pdf` A-Q2) are compile errors.

---

## 4. Loops & Jump Statements
*conditional statements.ppt, Practice - 3.pptx & PSP Quiz 2.pdf*

**Plain Summary:** `while` and `for` test the condition before running the body (entry-controlled), so they may run zero times. `do-while` runs the body first and checks the condition at the bottom (exit-controlled), so it always runs at least once.

- **`for` Loop Mechanics (`conditional statements.ppt` S21):** Must have exactly two semicolons. Multiple `init` or `update` expressions can be comma-separated, and any of the three parts may be omitted (`for (; i; i >>= 1)`).
- **`break` in Nested Loops (`conditional statements.ppt` S24, `Assignment 1`):** `break;` terminates only the innermost enclosing loop or `switch`, NOT outer loops.
- **`continue` (`conditional statements.ppt` S27-29):** Skips remaining statements in the current iteration and moves to the next iteration (in `for`, it still runs the `update` step).
- **`goto label;` (`conditional statements.ppt` S30):** Jumps to `label:` inside the same function.

| Construct | Type | When Condition Runs | Jump Behavior |
| --- | --- | --- | --- |
| `while (cond)` | Entry-controlled | Before every iteration | `break` exits loop; `continue` re-checks `cond` |
| `do { ... } while (cond);` | Exit-controlled | After every iteration (runs `>= 1` time) | Ends with `;`; `continue` jumps to `while (cond)` |
| `for (init; cond; upd)` | Entry-controlled | `init` once -> `cond` -> body -> `upd` | `continue` runs `upd` then re-checks `cond` |
| `break;` / `continue;` | Jump | Inside loop or `switch` | `break` exits innermost loop/`switch` only |

**Worked Example (Endsem Feb 2023 Section B Q1 (QP.pdf p. 6)):** Trace this nested `while` loop with `break`.
```c
#include <stdio.h>
int main(void)
{
    int x = 4, y = 4;
    while (y)
    {
        y--;
        while (x) {
            if (x != y) {
                printf("\n%d %d", x, y);
                x--;
            } else
                break;
        }
        x++;
    }
    return 0;
}
```
1. `y=4`: `y--` makes `y=3`. Inner `while(x)`: `x=4 != 3` prints `4 3` (`x=3`), then `3 == 3` hits `break;`. Outer `x++` sets `x=4`.
1. `y=3`: `y--` makes `y=2`. Inner prints `4 2`, `3 2`, then breaks at `x=2`; `x++` sets `x=3`.
1. `y=2`: `y--` makes `y=1`. Inner prints `3 1`, `2 1`, then breaks at `x=1`; `x++` sets `x=2`.
1. `y=1`: `y--` makes `y=0`. Inner prints `2 0`, `1 0`, reaches `x=0` (exits inner loop); `x++` sets `x=1`. Outer `while(0)` stops.
**Answer:** Output lines: `4 3`, `4 2`, `3 2`, `3 1`, `2 1`, `2 0`, `1 0`.

**Key Formula:** `for (init; cond; update)` | `do { ... } while (cond);` (semicolon required) | `while (c--)` tests `c` BEFORE decrementing

**Common Mistake:** Writing `for (i = 0; i < 10; i + 3)` (`Practice - 3.pptx` S14) does NOT update `i` (`i + 3` discards the result; you need `i += 3`), causing an infinite loop! Also `for (x = 0; 0;)` (`PSP Quiz 2.pdf` A-Q5) still executes `x = 0` before seeing condition `0` is false.

---

## 5. Functions, Parameter Passing & Recursion
*functions.ppt & Endsem Feb 2023*

**Plain Summary:** Functions split code into reusable blocks using three steps: declare (prototype), call, and define. Passing normal variables copies values (call by value), while passing `&var` addresses to pointers `*p` lets the function modify the caller's variables (call by reference).

- **Function Anatomy (`functions.ppt` S5-15):** Prototype (`int max(int, int);`) tells the compiler return type and parameter types before `main()`. Actual parameters are passed in the call; formal parameters receive them in the definition.
- **4 Forms (`functions.ppt` S13-15):** Functions can have any combination of return value (`void` vs type) and parameters (none vs list). `return expr;` exits the function immediately.
- **Recursion Rules (`functions.ppt` S23-27, `Endsem` A-Q6):** A recursive function calls itself and needs a **base case** (to stop) and a **recursive case** (reducing the problem). Recursive calls unwind in **Last-In, First-Out (LIFO)** order.
- **Passing 1D Arrays (`functions.ppt` S28):** Pass the array name `sum(a)` with parameter `int a[10]`, `int a[]`, or `int *b`.

| Method | What Is Passed | Formal Parameter | Effect on Caller Variables |
| --- | --- | --- | --- |
| Call by Value | Copy of value: `swap(a, b)` | `void swap(int x, int y)` | Caller variables stay unchanged |
| Call by Reference | Memory address: `swap(&a, &b)` | `void swap(int *x, int *y)` | Changes through `*x`, `*y` modify caller variables |

**Worked Example (Endsem Feb 2023 Section B Q4 (QP.pdf p. 7)):** Trace call-by-reference (`*i`) mixed with call-by-value (`j`).
```c
#include <stdio.h>
int cal(int *i, int j)
{
    *i = (*i) * (*i);
    j = j * j;
    return (2 * j);
}
int main(void)
{
    int i = 5, j = 2, t = 5;
    t = cal(&i, j);
    j = j + t * 3;
    i = i - t + 7;
    printf("\n%d,%d", i, j);
    return 0;
}
```
1. `cal(&i, j)` receives the address of `main`'s `i` (`*i` is `5`) and a copy of `j` (`2`).
1. `*i = 5 * 5 = 25` modifies `main`'s `i` directly to `25`. Local `j` becomes `4`, and `cal` returns `2 * 4 = 8` into `t`.
1. `main`'s `j` was NOT modified by `cal`, so `j` is still `2`: `j = 2 + 8 * 3 = 26`.
1. `i = 25 - 8 + 7 = 24`.
**Answer:** Output: `24,26`.

**Key Formula:** `return_type fn(param_types);` | Base case + Recursive case (LIFO stack) | `sqrt()` needs `<math.h>`

**Common Mistake:** In recursive factorial (`functions.ppt` S26-27), writing `if (n == 0 || n == 1) return n;` returns `0` for `0!`! Always make the base case `if (n == 0) return 1;`.

---

## 6. Scope Rules & Storage Classes
*scope.pptx, functions.ppt & Endsem Feb 2023*

**Plain Summary:** Scope decides where a variable name can be seen, while lifetime decides how long its memory stays alive. A `static` local variable is hidden inside its function/block, yet keeps its value across every call for the entire program.

- **Global vs Local Scope (`scope.pptx` S4-7):** Variables declared outside all functions have global (file) scope and are visible everywhere below. Variables inside `{ }` have block scope; an inner `{ int y = 40; }` shadows an outer `y` without changing it.
- **`static` Persistence (`scope.pptx` S8-9, `functions.ppt` S40-42):** Initialized only ONCE (`static int i = 1;`). When the function returns, `static` keeps its updated value for the next call, and cannot be accessed by name from `main()` (`Endsem` A-Q5).
- **`extern` Keyword (`functions.ppt` S36-39):** Tells the compiler a global variable is defined elsewhere (outside the function/file).

| Storage Class | Default Value | Scope | Lifetime | Storage Location |
| --- | --- | --- | --- | --- |
| `auto` (default local) | Garbage | Local to block `{ }` | Until block exits | RAM (stack) |
| `extern` (global) | `0` | Global (file scope) | Entire program | RAM (global/data) |
| `static` (local) | `0` | Local to block `{ }` | Entire program (init once) | RAM (data segment) |
| `register` | Garbage | Local to block `{ }` | Until block exits | CPU register (hint) |

**Worked Example (Endsem Feb 2023 Section A Q4 & Q8 (QP.pdf p. 5-6)):** Trace `static` inside recursion (`f(1)`) and global vs local shadowing.
```c
#include <stdio.h>
int f(int n)
{
    static int i = 1;
    if (n >= 5)
        return n;
    n = n + i;
    i++;
    return f(n);
}
int main(void) { printf("%d", f(1)); return 0; }
```
1. Call `f(1)`: `i` is initialized once to `1`. `1 >= 5` is false, so `n = 1 + 1 = 2`, `i` becomes `2`, calls `f(2)`.
1. Call `f(2)`: `i` is NOT re-initialized (still `2`). `n = 2 + 2 = 4`, `i` becomes `3`, calls `f(4)`.
1. Call `f(4)`: `i` is `3`. `n = 4 + 3 = 7`, `i` becomes `4`, calls `f(7)`.
1. Call `f(7)`: `7 >= 5` is true, returns `7` all the way back.
**Answer:** Output: `7` (and `i` persists as `4` in memory after `f` finishes, though `main` cannot access `i`).

**Key Formula:** `static type var = val;` (init once, default `0`, program lifetime) | Inner `{ int x; }` shadows outer `x`

**Common Mistake:** Re-declaring `int i = 100;` inside a `while (i--)` block (`Practice - 3.pptx` S21) creates a brand-new `auto` variable that shadows the loop's `i`, so `i--` inside the block never changes the loop counter!

---

## 7. 1D & 2D Arrays and Pointers
*arrays.ppt, PSP Quiz 2.pdf & Endsem Feb 2023*

**Plain Summary:** An array stores elements of the same type side by side in contiguous memory, indexed from `0` to `size - 1`. A pointer holds a variable's memory address (`&x`), and incrementing an `int *` pointer jumps by one `int` element (`sizeof(int)` bytes).

- **1D Array Declaration & Init (`arrays.ppt` S4-10):** `int a[4] = {10, 20, 30, 40};` or `int a[] = {1, 2, 4, 8, 16};`. Dynamic input uses a `for` loop with `scanf("%d", &a[i]);`.
- **2D Arrays & Matrices (`arrays.ppt` S12-21):** `int a[3][4];` stores 3 rows x 4 columns (`a[i][j]`). Matrix multiplication of `r1 x c1` and `r2 x c2` requires `c1 == r2`, and `c[i][j] = 0;` must be reset before the inner `k` loop.
- **Pointers & Dereferencing (`BASICS-1.pptx` S71, `Endsem` A-Q9/Q10):** `&x` gives address of `x`; `*p` accesses the value at address `p`. Arithmetic like `p + 1` or `q - p` works on pointers, but dividing a pointer (`r++ / 2`) is invalid.
- **Array-Pointer Link (`Endsem` B-Q9):** `arr` decays to `&arr[0]`, so `*(arr + i)` accesses `arr[i]`.

**Worked Example (PSP Quiz 2.pdf Part B Q4 & Endsem Feb 2023 Sec A Q10):** Trace array pre/post indexing and pointer post-increment.
```c
#include <stdio.h>
int main(void)
{
    int x[5] = {6, 2, 12, 18, 20};
    int p, r;
    p = --x[1];
    r = x[p++];
    printf("%d, %d", p, r);
    return 0;
}
```
1. `x` starts as `{6, 2, 12, 18, 20}` (`x[1]` is `2`).
1. `p = --x[1];` decrements `x[1]` first (`2` -> `1`), then assigns `p = 1`.
1. `r = x[p++];` uses current `p` (`1`) to read `x[1]` (which is now `1`!) into `r = 1`, then increments `p` to `2`.
**Answer:** Output: `2, 1`.

**Key Formula:** `type arr[N];` (indices `0` to `N-1`) | `*(arr + i) == arr[i]` | `*z++` means `*(z++)` (advances pointer `z`, NOT `*z`)

**Common Mistake:** In `*z++;` (`Endsem` A-Q10), postfix `++` has higher precedence than unary `*`, so it increments the **pointer** `z`, NOT the value `*z`! Use `(*z)++;` to increment the pointed value.

---

## 8. Strings & Character Arrays
*strings.ppt, PSP Quiz 2.pdf & Endsem Feb 2023*

**Plain Summary:** In C, a string is simply a 1D `char` array ending with the null character `'\0'`. Every `%s` print and `<string.h>` function stops only when it hits `'\0'` — if `'\0'` is missing, it keeps reading into adjacent memory.

- **Declaration & Null Terminator (`strings.ppt` S2-3, `Quiz 2` A-Q4):** `char a[] = "Hello";` automatically inserts `'\0'` (size 6 bytes). `char a[] = {'H','e','l','l','o','\0'};` needs `'\0'` explicitly.
- **String I/O (`strings.ppt` S4-5):** `scanf("%s", a)` needs no `&` (array name is an address) and stops at whitespace; `puts(a)` and `fgets(a, n, stdin)` handle full lines.
- **`strlen` vs `sizeof` (`strings.ppt` S7):** For `char str[20] = "vaishnavtej";`, `strlen(str)` is `11`, whereas `sizeof(str)` is `20`.
- **Case-Sensitive ASCII (`strings.ppt` S16, `Endsem`):** `'A'` is `65`, `'a'` is `97`, `'0'` is `48`. So `strcmp("Geetham", "geetham")` returns negative (not `0`).

| `<string.h>` Function | Purpose | Key Detail / Return Value |
| --- | --- | --- |
| `strlen(s)` | Length of string | Counts chars before `'\0'` (unlike `sizeof(s)` which gives total array bytes) |
| `strcpy(dest, src)` | Copy string | Copies `src` including `'\0'` into `dest` |
| `strcat(s1, s2)` / `strncat(s1, s2, n)` | Concatenate strings | Appends `s2` (or first `n` chars) onto end of `s1` + `'\0'` |
| `strcmp(s1, s2)` | Compare strings (case-sensitive) | Returns `0` if equal, `< 0` if `s1 < s2`, `> 0` if `s1 > s2` |
| `strlwr` / `strupr` / `strrev` | Lower / Upper / Reverse | Shown in `strings.ppt` (compiler-specific extensions) |

**Worked Example (PSP Quiz 2.pdf Part B Q3 & Endsem Feb 2023 Sec B Q8):** Explain what happens when a 2D `char` array leaves no room for `'\0'`.
```c
#include <stdio.h>
int main(void)
{
    char arr[4][3] = {"hi", "how", "are", "u"};
    printf("%s", arr[2]);
    return 0;
}
```
1. Each row of `arr[4][3]` holds only `3` characters.
1. `arr[0]` is `{'h','i','\0'}` and `arr[3]` is `{'u','\0','\0'}` (valid strings).
1. `arr[1]` (`"how"`) and `arr[2]` (`"are"`) use all 3 slots (`{'a','r','e'}`), leaving NO room for `'\0'`.
1. `printf("%s", arr[2])` prints `are` and keeps reading right into `arr[3]` until `'\0'`, printing `areu`.
**Answer:** Output: `areu` (because `arr[2]` has size `3` and lacks a `'\0'` terminator, so `%s` overflows into `arr[3]`).

**Key Formula:** `char s[N]` holds at most `N - 1` chars + `'\0'` | `strcmp(a, b) == 0` for equality

**Common Mistake:** Never compare strings with `s1 == s2` (that compares memory addresses, not text — use `strcmp(s1, s2) == 0`), and always allocate `+1` byte for `'\0'`.

---

## 9. Structures & Unions
*STRUCTURES.ppt & Endsem Feb 2023*

**Plain Summary:** A `struct` packs variables of different types together into one record, giving every member its own memory. A `union` overlays all its members in the exact same memory space, so only one member can hold a value at a time.

- **Declaration Syntax (`STRUCTURES.ppt` S4-8):** Always end `struct student { int rno; char name[20]; float cgpa; };` with `;`. You cannot initialize members inside the `struct` definition because no memory is allocated until variables are created.
- **Init, Copy & Access (`STRUCTURES.ppt` S9-11, `Endsem` B-Q6):** Initialize with `{56, "Sohel", 8.2}`. Struct assignment (`p3 = p2;`) copies all members into a separate struct. Access via `.` on variables or `->` on pointers (`p2->x`).
- **Arrays, Nesting & Functions (`STRUCTURES.ppt` S14-24):** Arrays of structs (`emp[3]`) store multiple records; nested structs access inner members with `st.add.city`; pass `&s` to a function (`struct books *p`) to modify or avoid copying.
- **Unions (`STRUCTURES.ppt` S26-29):** Useful for saving memory when fields are mutually exclusive (`sizeof(union Data)` equals `20` when `char str[20]` is the largest member).

| Feature | `struct` | `union` |
| --- | --- | --- |
| Memory Layout | Each member gets separate memory | All members share the same memory location |
| Size (`sizeof`) | Sum of members (plus compiler padding) | Size of largest member (`20` for `int`, `float`, `char[20]`) |
| Active Members | All members can store values simultaneously | Only one member holds a valid value at a time |
| Member Access | `var.member` (dot) or `ptr->member` (arrow) | `var.member` or `ptr->member` |

**Worked Example (Endsem Feb 2023 Section B Q6 & Q10 (QP.pdf p. 7-8)):** Trace struct copying (`p3 = p2`) and verify each member's independent values.
```c
#include <stdio.h>
struct product_details {
    char productName[10];
    float price;
};
int main(void)
{
    struct product_details p1 = {"Pen", 30.0};
    struct product_details p2 = {"paper", 120.0};
    struct product_details p3 = p2;
    p3.productName[0] = 'P';
    p2.price = p3.price / 4;
    printf("%s, %f\n", p1.productName, p1.price);
    printf("%s, %f\n", p2.productName, p2.price);
    if (p3.price > p2.price)
        printf("%s, %f\n", p3.productName, p3.price);
    return 0;
}
```
1. `p3 = p2;` makes an independent copy of `p2` (`"paper"`, `120.0`).
1. `p3.productName[0] = 'P';` changes `p3` to `"Paper"`; `p2.productName` remains `"paper"`.
1. `p2.price = 120.0 / 4 = 30.0;` updates `p2` only; `p3.price` stays `120.0`.
1. `p3.price > p2.price` (`120.0 > 30.0`) is true, so all three `printf` lines run.
**Answer:** Output:
`Pen, 30.000000`
`paper, 30.000000`
`Paper, 120.000000`

**Key Formula:** `struct tag { ... };` (needs `;`) | `ptr->field` is `(*ptr).field` | `sizeof(union)` `>=` largest member

**Common Mistake:** Forgetting the semicolon `;` after the closing brace of a `struct`/`union`, or trying to initialize a field inside the type template (`struct s { int x = 0; };` causes a compile error).

---

## 10. File I/O & Preprocessor Directives
*FILES.ppt (Unit 6)*

**Plain Summary:** Variables in RAM vanish when a program exits; files save data permanently on disk via a `FILE *` pointer opened by `fopen()` and closed by `fclose()`. Before compilation even begins, `#` preprocessor directives paste headers and expand `#define` macros.

- **4 File Steps (`FILES.ppt` S6-20):** Declare `FILE *fp;`, open with `fopen("name.txt", "mode")` and check `if (fp == NULL)`, read/write, then call `fclose(fp);`.
- **Text I/O Functions (`FILES.ppt` S12-19, S26-29):** Formatted: `fprintf(fp, ...)` / `fscanf(fp, ...)`; Character: `fgetc(fp)` (returns `EOF` at end) / `fputc(ch, fp)`; String: `fgets(buf, n, fp)` / `fputs(str, fp)`.
- **Random Access (`FILES.ppt` S21-25):** `fseek(fp, offset, origin)` moves the file cursor (`0`=`SEEK_SET` start, `1`=`SEEK_CUR` current, `2`=`SEEK_END` end). `ftell(fp)` returns current byte position; `rewind(fp)` resets to start.
- **Preprocessor Directives (`FILES.ppt` S30-42):** Start with `#` and NEVER end with `;`. Includes `#include`, `#define PI 3.1415`, `#define AREA(l,b) ((l)*(b))`, `#ifdef`/`#else`/`#endif`, and `#undef`.

| `fopen` Mode | Purpose | If File Exists | If File Missing |
| --- | --- | --- | --- |
| `"r"` | Read text | Opens from start | Returns `NULL` |
| `"w"` | Write text | Erases (overwrites) contents | Creates new file |
| `"a"` | Append text | Writes at end of file | Creates new file |
| `"r+"` | Read & write | Opens without erasing | Returns `NULL` |
| `"w+"` | Read & write | Erases contents | Creates new file |
| `"a+"` | Read & append | Reads anywhere, appends at end | Creates new file |

**Worked Example (FILES.ppt Slide 26 & Slide 28):** Read and copy every character from `in.txt` to `out.txt` using `fgetc` and `fputc`.
```c
#include <stdio.h>
#include <stdlib.h>
int main(void)
{
    FILE *fp1, *fp2;
    int ch;
    fp1 = fopen("in.txt", "r");
    fp2 = fopen("out.txt", "w");
    if (fp1 == NULL || fp2 == NULL) {
        printf("Error opening file\n");
        exit(1);
    }
    while ((ch = fgetc(fp1)) != EOF) {
        fputc(ch, fp2);
    }
    fclose(fp1);
    fclose(fp2);
    return 0;
}
```
1. Open source with `"r"` and destination with `"w"`, checking for `NULL` before reading or writing.
1. `fgetc(fp1)` reads one character at a time (stored in `int` so `EOF` `-1` is distinct from valid bytes) until `EOF`.
1. `fputc(ch, fp2)` writes each character to `out.txt`.
1. `fclose(fp1); fclose(fp2);` flushes buffered output to disk and releases file handles.
**Answer:** Safely copies `in.txt` into `out.txt` character by character and closes both files.

**Key Formula:** `FILE *fp = fopen(name, mode);` | `fseek(fp, offset, SEEK_SET|SEEK_CUR|SEEK_END);` | No `;` after `#define`

**Common Mistake:** Always check `if (fp == NULL)` after `fopen(..., "r")`, never put `;` after `#define PI 3.14`, and wrap macro arguments in parentheses (`#define AREA(l,b) ((l)*(b))` so `AREA(1+2, 3)` doesn't turn into `1+2*3`!).

---

## Practice Questions (25)
### Q1. Easy (Quiz / Lab)
[Source: `Quiz _19.jpg` Q5 & `BASICS-1.pptx` S25-29]
Discuss the phases of building and running a C source file named `p1.c`, and name the file extensions generated at each phase.
- **Hint:** Recall the 4 phases from `BASICS-1.pptx`: Editing, Compilation, Linking, Execution.
- **Solution:** 1. **Editing (`.c`):** Source code is written in high-level C and saved as `p1.c`.
2. **Compilation (`.obj` / `.o`):** Compiler checks syntax and translates error-free source into low-level object code (`p1.obj` / `p1.o`).
3. **Linking:** Linker attaches object code with required system/library functions (e.g., `printf` from `<stdio.h>`, `sqrt` from `<math.h>`).
4. **Execution (`.exe`):** Produces the executable `p1.exe` and loads it into memory to run.

### Q2. Easy (Midsem / Endsem)
[Source: `IMG-20190828-WA0002.jpg` Q6 & `QP.pdf` Midsem Dec 2022 A-Q3]
Classify each C identifier/declaration as **valid** or **invalid**, and give the reason:
(a) `int_t`  (b) `group one`  (c) `Price$`  (d) `(area)`  (e) `int 1_35;`  (f) `float _income;`  (g) `int a!;`  (h) `char name123;`  (i) `int num-data;`
- **Hint:** Identifiers may only contain letters, digits, and `_`, cannot start with a digit, and cannot use spaces or special symbols.
- **Solution:** **Valid:** (a) `int_t` (not a keyword, uses letters and `_`), (f) `_income` (may start with `_`), (h) `name123` (digits allowed after first char).
**Invalid:** (b) `group one` (space not allowed), (c) `Price$` (`$` invalid in standard identifiers), (d) `(area)` (parentheses not allowed), (e) `1_35` (starts with digit `1`), (g) `a!` (`!` not allowed), (i) `num-data` (hyphen `-` parsed as minus).

### Q3. Medium (Assignment / Tutorial)
[Source: `Practice - 2.pptx` S2, S8, S14]
1. Write `-28` in 16-bit 2's complement form.
2. Find the decimal value of the 6-bit 2's complement binary number `111010`.
3. What is the smallest integer representable in 8-bit 2's complement form?
- **Hint:** To negate in 2's complement, invert all bits and add `1`. For `111010`, the MSB is `1` (negative).
- **Solution:** 1. `+28` in 16-bit binary is `0000 0000 0001 1100`. Invert bits: `1111 1111 1110 0011`. Add `1`: **`1111 1111 1110 0100`** (`0xFFE4`).
2. MSB is `1` (negative). Invert `111010` -> `000101`, add `1` -> `000110` (`6`), so the value is **`-6`**.
3. In `n`-bit 2's complement, smallest integer is `-2^(n-1)`. For `n = 8`: **`-128`** (`1000 0000`).

### Q4. Medium (Quiz / Lab)
[Source: `Quiz _19.jpg` Q7(c)]
What is the output of the following C code (assuming 8-bit signed `char`)?
```c
void main()
{
    char c = 125;
    c = c + 3;
    printf("%d", c);
}
```
- **Hint:** Signed `char` ranges from `-128` to `+127` (`BASICS-1.pptx` Slide 47).
- **Solution:** `125 + 3 = 128`, which in 8-bit binary is `1000 0000`. In 8-bit signed 2's complement, `1000 0000` wraps past `+127` to **`-128`**.

### Q5. Medium (Midsem / Endsem)
[Source: `QP.pdf` Midsem Dec 2022 Part A Q4]
What is the output/error of this program?
```c
#include <stdio.h>
void main() {
    int a = 5;
    if (a == 5);
    {
        printf("Value of a is %d.\n", 5);
        printf("Successfully executed if statement.\n");
    }
    else;
    printf("Successfully completed else statement.");
}
```
- **Hint:** Look closely at the semicolon `;` right after `if (a == 5)`.
- **Solution:** **Compilation Error** (`'else' without a previous 'if'`). The `;` after `if (a == 5)` terminates the `if` statement immediately, making the `{ ... }` block a standalone compound statement, so `else;` has no matching `if`.

### Q6. Medium (Midsem / Endsem)
[Source: `QP.pdf` Midsem Dec 2022 Part B Q2]
Find the values of `w, x, y, z`:
```c
void main()
{
    int i = 10, j = -4, k = 0, w, x, y, z;
    w = i || j || k;
    x = i && j && !k;
    y = i || j && k;
    z = i + 2 * j - 2 && j + 4 || k;
    printf("\nw = %d x = %d y = %d z = %d", w, x, y, z);
}
```
- **Hint:** Precedence: arithmetic (`*`, `+`, `-`) before `!`, before `&&`, before `||`.
- **Solution:** - `w = 10 || -4 || 0` -> **`1`**.
- `x = 10 && -4 && !0` -> `10 && -4 && 1` -> **`1`**.
- `y = i || (j && k)` (`&&` binds tighter than `||`) -> `10 || 0` -> **`1`**.
- `z`: `i + 2*j - 2 = 10 - 8 - 2 = 0`; `0 && (j+4)` short-circuits to `0`; `0 || 0` -> **`0`**.
Output: `w = 1 x = 1 y = 1 z = 0`.

### Q7. Hard (Midsem / Endsem)
[Source: `QP.pdf` Midsem Dec 2022 Part B Q3]
Find `w, x, y, z` step by step:
```c
void main()
{
    int m = 4, n = 2, p = 2, w, x, y, z;
    w = m * n / 4 - 6 / 2 + 2 / 3 * 6 / p;
    x = m < n / p - 4 / 2 + 2 * 3 - 6 > !p;
    y = m * p % 2 + 4 - m * 2 / 2;
    z = m++ + --p + ++n;
    printf("\nw = %d x = %d y = %d z = %d", w, x, y, z);
}
```
- **Hint:** `* / %` are left-to-right; `2 / 3 == 0` in integer division; `<` and `>` share precedence left-to-right.
- **Solution:** - `w = (4*2)/4 - 3 + ((2/3)*6)/2 = 2 - 3 + 0 = -1`.
- `x`: `!p` is `0`; `n/p - 4/2 + 2*3 - 6 = 1 - 2 + 6 - 6 = -1`. Left-to-right `<` and `>`: `(4 < -1) > 0` -> `0 > 0` -> `0`.
- `y = (4*2)%2 + 4 - (4*2)/2 = 0 + 4 - 4 = 0`.
- `z = 4 + 1 + 3 = 8` (distinct variables `m`, `p`, `n`).
Output: `w = -1 x = 0 y = 0 z = 8`.

### Q8. Medium (Assignment / Tutorial)
[Source: `Practice - 1.pptx` Slide 6, Slide 11 & Slide 14]
Predict the output of these three snippets:
(a) `printf("%d", 1 << 2 + 3 << 4);`
(b) `int i = 12; int j = sizeof(i++); printf("%d %d", i, j);` (assume `sizeof(int) == 4`)
(c) `printf("%d", printf("jagadeesh"));`
- **Hint:** `+` has higher precedence than `<<`; `sizeof` does not evaluate its operand; `printf` returns characters printed.
- **Solution:** (a) `+` runs before `<<`: `(1 << 5) << 4 = 32 << 4 =` **`512`**.
(b) `sizeof(i++)` only checks type size at compile time without running `i++`, so output is **`12 4`**.
(c) Inner `printf` prints `jagadeesh` (9 chars) and returns `9`, so outer `printf` prints **`jagadeesh9`**.

### Q9. Hard (Assignment / Tutorial)
[Source: `Practice - 1.pptx` Slide 23]
Predict the output:
```c
#include <stdio.h>
int main()
{
    int i = -1, j = -1, k = 0, l = 2, m;
    m = i++ && j++ && k++ || l++;
    printf("%d %d %d %d %d", i, j, k, l, m);
    return 0;
}
```
- **Hint:** `&&` binds tighter than `||`: parse as `(i++ && j++ && k++) || l++`.
- **Solution:** - `i++` is `-1` (true), `i` becomes `0`.
- `j++` is `-1` (true), `j` becomes `0`.
- `k++` is `0` (false!), `k` becomes `1`. The left `&&` group is now `0`.
- Since `0 || l++` must evaluate the right side, `l++` gives `2` (true), `l` becomes `3`, and `m = 1`.
Output: **`0 0 1 3 1`**.

### Q10. Easy (Midsem / Endsem)
[Source: `QP.pdf` Endsem Feb 2023 Section A Q3]
Find the output:
```c
void main()
{
    int a = 15, b = 27, k, m;
    k = a ^ 32;
    m = a & b;
    printf("\nk = %d, m = %d", k, m);
}
```
- **Hint:** Write `15`, `27`, and `32` in 6-bit binary: `15 = 001111`, `27 = 011011`, `32 = 100000`.
- **Solution:** - `k = 001111 ^ 100000 = 101111_2 = 32 + 15 =` **`47`**.
- `m = 001111 & 011011 = 001011_2 = 8 + 2 + 1 =` **`11`**.
Output: `k = 47, m = 11`.

### Q11. Medium (Assignment / Tutorial)
[Source: `Assignment 1.docx` (`Assignment_1_1.png` & `Assignment_1_2.png`)]
What do these two bitwise-NOT programs print?
(a) `int x = 10, y = 11; if (~(x ^ y)) printf("equal"); else printf("not equal");`
(b) `int a = -1, b = ~0; if (b == a) printf("equal"); else printf("unequal");`
- **Hint:** `~` flips every bit (bitwise complement), unlike `!` (logical NOT).
- **Solution:** (a) `10 ^ 11 = 1`. Bitwise `~1` is `-2`, which is **non-zero** (true in `if`!), so it prints **`equal`** even though `10 != 11`! (To test equality with XOR, you need `!(x ^ y)`.)
(b) In 2's complement, flipping all `0` bits in `0` gives all `1` bits, which equals `-1`. Thus `b == a` is true and it prints **`equal`**.

### Q12. Medium (Quiz / Lab)
[Source: `PSP Quiz 2.pdf` Part A Q2 & `Practice - 3.pptx` Slides 7-8]
Find the output or error in each `switch` snippet:
(a) `int c = 3; switch(c) { case 3: case 5: case (7-4): printf("It is something"); break; case c=1: printf("It is one"); break; }`
(b) `#define N 1.5` with `case N + 5:` and `case N * 4:`
- **Hint:** `case` labels in C must be unique integer constant expressions.
- **Solution:** (a) **Compile-time errors:** (1) `case (7-4):` equals `case 3:`, creating a **duplicate case value**; (2) `case c=1:` is an assignment (not a constant expression).
(b) **Compile-time error:** `N` is `1.5` (`double`), so `N + 5` and `N * 4` do not reduce to integer constants (`Practice - 3.pptx` Slide 9).

### Q13. Medium (Assignment / Tutorial)
[Source: `Practice - 3.pptx` Slide 12]
Predict the output:
```c
#include <stdio.h>
int main() {
    int i = 0;
    for (i = 0; i < 20; i++) {
        switch (i) {
            case 0: i += 5;
            case 1: i += 2;
            case 5: i += 5;
            default: i += 4; break;
        }
        printf("%d  ", i);
    }
    return 0;
}
```
- **Hint:** Notice `case 0`, `case 1`, and `case 5` have NO `break;` statements — they fall straight through into `default`!
- **Solution:** - Start `i = 0`: enters `case 0` (`+5` -> `5`), falls through `case 1` (`+2` -> `7`), `case 5` (`+5` -> `12`), `default` (`+4` -> `16`), hits `break;`. Prints **`16  `**, then `i++` makes `i = 17`.
- `i = 17` (`< 20`): enters `default` (`+4` -> `21`), hits `break;`. Prints **`21  `**, then `i++` makes `i = 22` and loop ends.
Output: **`16  21  `**.

### Q14. Medium (Quiz / Lab)
[Source: `PSP Quiz 2.pdf` Part A Q1 & Q3]
Find the output of both loops:
(a)
```c
int c = 6;
while (c--) {
    printf("%d\t", c);
}
```
(b)
```c
int k = 1;
do {
    printf("%d ", k);
    k = k + 1;
} while (k % 2 == 0 && k <= 8);
```
- **Hint:** In (a), `c--` checks `c` before subtracting `1`. In (b), `do-while` runs the body once before checking the condition.
- **Solution:** (a) `while(c--)` checks `6, 5, 4, 3, 2, 1` (all true) and decrements inside before `printf`, then stops when `c` is `0`: **`5  4  3  2  1  0`**.
(b) Iter 1: prints `1`, `k` becomes `2` (`2%2==0 && 2<=8` is true). Iter 2: prints `2`, `k` becomes `3` (`3%2==0` is false -> stops). Output: **`1 2`**.

### Q15. Medium (Quiz / Lab)
[Source: `PSP Quiz 2.pdf` Part B Q2]
Trace the output carefully:
```c
#include <stdio.h>
void main()
{
    int i = 6;
    for (i = i / 3; i < 3; i--)
    {
        if (i == 0)
            break;
        while (i <= 4)
        {
            printf("%d", i);
            i++;
            break;
        }
        i++;
    }
}
```
- **Hint:** Follow `i` through `while`, `break`, the outer `i++`, and the `for` update `i--`.
- **Solution:** 1. `i = 6 / 3 = 2`. `2 < 3` is true, `i != 0`.
2. Enters `while (i <= 4)`: prints **`2`**, `i++` makes `i = 3`, `break` exits `while`.
3. After `while`, `i++` makes `i = 4`.
4. `for` update `i--` makes `i = 3`.
5. Condition `i < 3` (`3 < 3`) is FALSE, so `for` exits.
Output: **`2`**.

### Q16. Hard (Midsem / Endsem)
[Source: `QP.pdf` Endsem Feb 2023 Section B Q3]
What does this recursive program print?
```c
void func(int n, int sum)
{
    int k = 0, j = 0;
    if (n == 0)
        return;
    k = n % 10;
    j = n / 10;
    sum = sum + k;
    func(j, sum);
    printf("%d,", k);
}
int main()
{
    int a = 2048, sum = 0;
    func(a, sum);
    printf("%d", sum);
}
```
- **Hint:** `printf("%d,", k)` is AFTER the recursive call (LIFO unwind), and `sum` is passed by value.
- **Solution:** Calls push digits `8`, `4`, `0`, `2` onto the stack until `n == 0`. Unwinding in LIFO order prints `2,0,4,8,`. Because `sum` in `main` was passed by value, it stays `0` and prints `0`.
Output: **`2,0,4,8,0`**.

### Q17. Medium (Midsem / Endsem)
[Source: `QP.pdf` Endsem Feb 2023 Section B Q7]
What is the output?
```c
void f1(int a, int b) {
    int c; c = a; a = b; b = c;
}
void f2(int *a, int *b) {
    int c; c = *a; *a = *b; *b = c;
}
int main() {
    int a = 4, b = 5, c = 6;
    f1(a, b);
    f2(&b, &c);
    printf("%d", c - a - b);
    return 0;
}
```
- **Hint:** `f1` uses call by value (no effect on `main`); `f2` uses call by reference (swaps `b` and `c`).
- **Solution:** `f1(a, b)` swaps local copies only (`a = 4, b = 5` unchanged). `f2(&b, &c)` swaps `b` and `c` via pointers, so `b = 6, c = 5`. Then `c - a - b = 5 - 4 - 6 =` **`-5`**.

### Q18. Medium (Midsem / Endsem)
[Source: `QP.pdf` Endsem Feb 2023 Section A Q8]
What is the output?
```c
#include <stdio.h>
int i = 10;
void check() {
    printf("%d ", i++);
}
void main() {
    int i = 20;
    printf("%d ", i);
    check();
    printf("%d", ++i);
}
```
- **Hint:** `main` has its own local `i = 20` which shadows the global `i = 10`, while `check()` sees only global `i`.
- **Solution:** 1. Inside `main`, local `i` (`20`) shadows global `i`, so first `printf` prints `20`.
2. `check()` cannot see `main`'s local `i`; it prints global `i` (`10`) and increments global `i` to `11`.
3. Back in `main`, `++i` increments local `i` from `20` to `21` and prints `21`.
Output: **`20 10 21`**.

### Q19. Medium (Midsem / Endsem)
[Source: `QP.pdf` Endsem Feb 2023 Section A Q9 & Q10]
1. Given `int *p, *q, *r, x=5, y=6, z, a[10]={1,2}; p=&x; q=&y; r=a;`, which expression is **incorrect**?
   (a) `(*p) * (*q)`  (b) `z = (r++ / 2)`  (c) `q - p`  (d) `*p + 5`
2. If `int x = 20, y = 21, *z;` are at contiguous addresses `5000, 5004, 5008` (4-byte `int`), what does `z = &x; *z++; x++;` print for `&x, &y, &z` and `x, y, *z`?
- **Hint:** You cannot divide a pointer by an integer. Also `*z++` parses as `*(z++)`.
- **Solution:** 1. **`(b) z = (r++ / 2)`** is invalid: pointer division by `2` is illegal in C.
2. `*z++` advances pointer `z` from `5000` (`&x`) to `5004` (`&y`), while `x++` sets `x = 21`. Addresses stay `5000, 5004, 5008`, and values are `x = 21, y = 21, *z = 21` (**`5000, 5004, 5008, 21, 21, 21`**).

### Q20. Medium (Midsem / Endsem)
[Source: `QP.pdf` Endsem Feb 2023 Section B Q9]
What is the output?
```c
void func(int *arr1, int *arr2, int size) {
    int i;
    for (i = 0; i < size; i++) {
        *(arr2 + i) = ++(*(arr1 + i));
    }
}
void main() {
    int arr1[10] = {2, 2, 3, 3, 3, 4, 4, 4, 4, 5};
    int arr2[10];
    func(arr1, arr2, 10);
    for (int i = 0; i < 10; i++)
        printf("%d\n", *(arr2 + i));
}
```
- **Hint:** `++(*(arr1 + i))` pre-increments each element of `arr1` and assigns the incremented value to `arr2[i]`.
- **Solution:** Every element of `arr1` is incremented by `1` before being copied to `arr2`, so `arr2` contains **`3, 3, 4, 4, 4, 5, 5, 5, 5, 6`** (each printed on its own line).

### Q21. Easy (Quiz / Lab)
[Source: `PSP Quiz 2.pdf` Part A Q4]
Given `char str[] = {'g', 'l', 'o', 'b', 'e'};`, which option added after initialization converts it into a valid C string?
A. `str[5] = '0';`
B. `str[5] = '\0';`
C. `str[] = {'g','l','o','b','e','\0'};`
D. All the above
- **Hint:** A C string ends with the null character `'\0'` (ASCII 0, not `'0'`).
- **Solution:** **B (`str[5] = '\0';`)** is the intended quiz answer because `'\0'` (not `'0'`, which is ASCII 48) marks the end of a C string, and `str[] = {...}` is invalid syntax after initialization. (In practice, `str` should be declared with size at least `6`, e.g. `char str[6]`, before writing `str[5]`.)

### Q22. Medium (Midsem / Endsem)
[Source: `QP.pdf` Endsem Feb 2023 Section B Q8]
What is the output?
```c
#include <stdio.h>
#include <string.h>
void main()
{
    char str1[20] = "aabba", str2[10];
    strcpy(str2, str1);
    printf("%s\n", str2);
    str1[3] = 'd';
    if (strcmp(str1, str2) > 0)
        printf("Success %s\n", str1);
    else
        printf("Failure %s\n", str2);
}
```
- **Hint:** `str1[3]` is the 4th character (`'b'`), replaced by `'d'`.
- **Solution:** `strcpy(str2, str1)` copies `"aabba"` into `str2` and prints `aabba`. Setting `str1[3] = 'd'` changes `str1` to `"aabda"`. Comparing `"aabda"` vs `"aabba"`: `'d'` (ASCII 100) `>` `'b'` (ASCII 98), so `strcmp` returns a positive value.
Output:
`aabba`
`Success aabda`

### Q23. Hard (Quiz / Lab)
[Source: `PSP Quiz 2.pdf` Part C Q1]
Write a C program (without `<string.h>` functions and using at most one extra 1D array) to separate a string into even-ASCII characters first, followed by odd-ASCII characters.
Sample: `abcde` -> `bdace`, `klmn` -> `lnkm`.
- **Hint:** Make two passes over the input string `s`: first copy characters with `s[i] % 2 == 0` into `res`, then copy `s[i] % 2 != 0`, and finish with `'\0'`.
- **Solution:** ```c
#include <stdio.h>
int main(void) {
    char s[100], res[100];
    int i, j = 0;
    scanf("%s", s);
    for (i = 0; s[i] != '\0'; i++)
        if (s[i] % 2 == 0) res[j++] = s[i];
    for (i = 0; s[i] != '\0'; i++)
        if (s[i] % 2 != 0) res[j++] = s[i];
    res[j] = '\0';
    printf("%s", res);
    return 0;
}
```

### Q24. Medium (Midsem / Endsem)
[Source: `QP.pdf` Endsem Feb 2023 Section B Q10]
What is the output?
```c
#include <stdio.h>
struct node {
    int id, val;
} *nptr;
void detail(struct node *nptr, int n) {
    for (int i = 0; i < n; i++) {
        if (nptr->val % 2 == 0)
            printf("%d %d\n", nptr->id, nptr->val);
        else
            printf("%d %d\n", nptr->id, nptr->val * 2);
        nptr++;
    }
}
int main() {
    int n = 5;
    struct node List[] = {{1, 37}, {2, 16}, {3, 84}, {4, 71}, {5, 48}};
    nptr = &List[0];
    detail(nptr, n);
    return 0;
}
```
- **Hint:** Even `val` prints as-is; odd `val` prints `val * 2`. `nptr++` moves to the next `struct node`.
- **Solution:** - `{1, 37}` (odd) -> `1 74`
- `{2, 16}` (even) -> `2 16`
- `{3, 84}` (even) -> `3 84`
- `{4, 71}` (odd) -> `4 142`
- `{5, 48}` (even) -> `5 48`

### Q25. Easy (Assignment / Tutorial)
[Source: `STRUCTURES.ppt` Slide 29 & `FILES.ppt` Slides 8-11, 22-25]
1. Given `union Data { int i; float f; char str[20]; };`, what does `sizeof(union Data)` return and why does it differ from a `struct`?
2. What happens when you call `fopen("data.txt", "r")` vs `fopen("data.txt", "w")` on a missing file vs an existing file? What does `fseek(fp, -5, 2)` do?
- **Hint:** A `union` shares one memory block sized to its largest member. `2` in `fseek` means `SEEK_END`.
- **Solution:** 1. `sizeof(union Data)` is **`20`** bytes (the size of its largest member `char str[20]`), because all `union` members share the same memory location; a `struct` allocates separate space for every member.
2. `"r"` returns **`NULL`** if `data.txt` is missing and reads from the start if it exists; `"w"` creates a new file if missing and **erases** existing contents if it exists. `fseek(fp, -5, 2)` (`SEEK_END`) moves the file pointer 5 bytes backward from the end of the file.
