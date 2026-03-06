# C++ CP Recap Notes (Beginner → CP Ready)

## 0) CP Template (সব সময় এইটা দিয়ে শুরু)

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    // code here

    return 0;
}
```

**কেন লাগবে?** দ্রুত input/output (fast I/O), CP-তে কাজে লাগে।

---

## 1) Input / Output (I/O)

### 1.1 Basic input/output

```cpp
int a, b;
cin >> a >> b;
cout << a + b << "\n";
```

### 1.2 এক লাইনে অনেক ইনপুট

```cpp
int a, b, c;
cin >> a >> b >> c;
```

### 1.3 String input

```cpp
string s;
cin >> s;   // স্পেস ছাড়া শব্দ
cout << s << "\n";
```

### 1.4 Full line input (স্পেসসহ)

```cpp
string line;
getline(cin, line); // 注意: আগে cin থাকলে ignore লাগতে পারে
```

**Mini practice**

* দুইটা সংখ্যা নিয়ে sum, product প্রিন্ট করো
* একটা নাম ইনপুট নিয়ে “Hello <name>” প্রিন্ট করো

---

## 2) Data Types (কী টাইপ কবে ব্যবহার করব)

* `int` → সাধারণ সংখ্যা (±2 বিলিয়ন পর্যন্ত)
* `long long` → বড় সংখ্যা (CP-তে safe)
* `double` → দশমিক
* `char` → এক অক্ষর
* `string` → লেখা
* `bool` → true/false

**Example**

```cpp
long long x = 10000000000LL; // বড় সংখ্যা
double pi = 3.14159;
char ch = 'A';
bool ok = true;
```

---

## 3) Operators (চিহ্নগুলো)

### 3.1 Arithmetic

* `+ - * /`
* `%` → remainder (ভাগশেষ)

```cpp
int a=10, b=3;
cout << a/b << "\n"; // 3 (int division)
cout << a%b << "\n"; // 1
```

### 3.2 Comparison (true/false দেয়)

* `==  !=  <  >  <=  >=`

### 3.3 Logical

* AND `&&`
* OR `||`
* NOT `!`

**Mini practice**

* একটা সংখ্যা even নাকি odd বের করো: `n%2==0`
* তিনটা সংখ্যার মধ্যে maximum বের করো

---

## 4) If / Else (Decision Making)

```cpp
int n;
cin >> n;

if (n % 2 == 0) cout << "Even\n";
else cout << "Odd\n";
```

### Common mistake

* `==` (compare) আর `=` (assign) গুলিয়ে ফেলবে না।

**Mini practice**

* n positive/negative/zero চেক করো
* a,b,c → max বের করো

---

## 5) Loops (Repeat)

### 5.1 for loop

```cpp
for (int i = 1; i <= 5; i++) {
    cout << i << " ";
}
cout << "\n";
```

### 5.2 while loop

```cpp
int n;
cin >> n;
while (n > 0) {
    cout << n << "\n";
    n--;
}
```

### 5.3 break / continue

```cpp
for(int i=1;i<=10;i++){
    if(i==5) continue; // 5 skip
    if(i==8) break;    // stop at 8
    cout << i << " ";
}
```

---

## 6) Test Cases Pattern (CP-তে খুব common)

CodeChef/Codeforces এ অনেক problem এ `t` থাকে:

```cpp
int t;
cin >> t;
while (t--) {
    int a, b;
    cin >> a >> b;
    cout << a + b << "\n";
}
```

**Mini practice**

* t টা সংখ্যার digit sum বের করো (FLOW006 টাইপ)

---

## 7) String Basics (71A, 081A ইত্যাদিতে লাগে)

### 7.1 size, index, first/last

```cpp
string s;
cin >> s;

cout << s.size() << "\n";
cout << s[0] << "\n";
cout << s.back() << "\n";
```

### 7.2 count a specific char (ABC081A)

```cpp
string s;
cin >> s;
int cnt = 0;
for(char c : s) if(c == '1') cnt++;
cout << cnt << "\n";
```

### 7.3 71A concept (short/long word formatting)

```cpp
string s;
cin >> s;
if ((int)s.size() > 10) {
    cout << s[0] << (int)s.size()-2 << s.back() << "\n";
} else {
    cout << s << "\n";
}
```

---

## 8) Counting Pattern (231A, INTEST টাইপ)

### “কতগুলো satisfy করে” → counter++

```cpp
int n;
cin >> n;
int cnt = 0;

for(int i=0;i<n;i++){
    int x;
    cin >> x;
    if(x % 2 == 0) cnt++;
}
cout << cnt << "\n";
```

**INTEST idea (divisible count)**

* `if (x % k == 0) cnt++;`

---

## 9) Digit Sum Technique (FLOW006, ABC083B)

### 9.1 digit sum function

```cpp
int digit_sum(int n) {
    int s = 0;
    while(n > 0) {
        s += n % 10;
        n /= 10;
    }
    return s;
}
```

### 9.2 ABC083B style (bruteforce + filter)

```cpp
int N, A, B;
cin >> N >> A >> B;

long long ans = 0;
for(int i=1;i<=N;i++){
    int s = digit_sum(i);
    if(A <= s && s <= B) ans += i;
}
cout << ans << "\n";
```

---

## 10) CP Small Habits (ভালো speed + কম ভুল)

* সবসময় template + fast I/O রাখো
* output শেষে `\n` দাও
* variable নাম meaningful রাখো (`cnt`, `sum`, `ans`)
* submit এর আগে sample input দিয়ে test
* ভুল হলে:

  * input ঠিক পড়ছো তো?
  * loop limit ঠিক তো?
  * counter reset করছো তো? (testcase এ common bug)

---

# Quick Practice Set (এই নোট দেখে করা যায়)

1. Add two numbers (FLOW001 style)
2. Even/Odd (ABC086A/4A style)
3. Count ‘1’ in string (ABC081A)
4. Team counting (231A style)
5. Digit sum (FLOW006)

