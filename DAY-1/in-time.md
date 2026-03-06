# Beginner CP — Starter Pack (General Use)

## 1) Problem List (Beginner Friendly Set)

**Codeforces**

1. Watermelon (4A)
2. Way Too Long Words (71A)
3. Team (231A)

**AtCoder (ABS)**
4) Placing Marbles (ABC081A)
5) Product (ABC086A)
6) Some Sums (ABC083B)

**CodeChef**
7) Add Two Numbers (FLOW001)
8) Sum of Digits (FLOW006)
9) Enormous Input Test (INTEST)

---

## 2) এই Problem Set solve করতে যা যা লাগবে (General Checklist)

### A) Core C++ Basics (সবগুলোর জন্য)

* Input/Output: `cin`, `cout`, `\n`
* Data types: `int`, `long long`
* Operators: `+  -  *  /  %`
* Fast I/O (recommended):

  * `ios::sync_with_stdio(false);`
  * `cin.tie(nullptr);`

### B) Condition (if/else)

* Basic: `if (condition) ... else ...`
* Even/Odd: `x % 2 == 0`
* Logical operators:

  * AND: `&&`
  * OR: `||`

### C) Loops + Counting

* `for` loop
* `while` loop
* Testcases pattern: `int t; cin >> t; while(t--) { ... }`
* Counting pattern: `cnt++` when condition true

### D) String Basics

* `string s; cin >> s;`
* length: `s.size()`
* first/last char: `s[0]`, `s.back()`
* character count (যেমন `'1'` কয়টা)

### E) Digit Sum Technique (CP core)

* `sum += n % 10;`
* `n /= 10;`
* প্রতি testcase এ `sum=0` reset

### F) Brute Force + Filter (easy algorithm thinking)

* `for (i=1..N)` loop
* digit sum বের করে `A <= sum <= B` হলে answer এ যোগ

### G) Large Input Counting (INTEST)

* অনেক সংখ্যা পড়া
* divisible check: `x % k == 0`
* শুধু final count print (extra print না)

---

## 3) Problem → Topic Map (Quick)

* **4A Watermelon** → if/else + even/odd + edge case
* **71A Way Too Long Words** → string size + first/last char + testcases
* **231A Team** → loop + counting + condition (>=2)
* **ABC081A Placing Marbles** → string/char count
* **ABC086A Product** → multiplication parity (even/odd)
* **ABC083B Some Sums** → loop 1..N + digit sum + filter + sum
* **FLOW001** → testcases + add two nums
* **FLOW006** → digit sum per testcase
* **INTEST** → fast I/O + count divisible

---

## 4) Recommended Solve Order (Beginner-friendly)

1. FLOW001
2. 4A
3. ABC086A
4. ABC081A
5. 71A
6. 231A
7. FLOW006
8. INTEST
9. ABC083B

