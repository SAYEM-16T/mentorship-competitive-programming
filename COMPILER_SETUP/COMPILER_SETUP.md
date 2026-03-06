# Windows CP Setup (VS Code + MSYS2 + GNU++17) — Teacher Documentation

## 0) Quick Decision

✅ **Student যদি 64-bit Windows ব্যবহার করে (সবচেয়ে কম ঝামেলা):**
➡️ **MSYS2 UCRT64 + mingw-w64-ucrt-x86_64-toolchain**

⚠️ **Student যদি সত্যিই 32-bit Windows হয়:**
➡️ **MSYS2 MINGW32 + mingw-w64-i686-toolchain**
(কিন্তু 2026 এ 32-bit Windows খুব rare; CP-এর জন্য 64-bit strongly recommend)

---

## 1) What we are installing

* **VS Code**: editor
* **MSYS2**: package manager + GCC environment
* **G++ (GNU++17)**: compiler
* **VS Code Tasks/Launch**: extension ছাড়াই 1-key build/run

---

# Part A — Install VS Code

## A1) Download & Install

1. Google এ সার্চ: **Visual Studio Code download**
2. Windows version ডাউনলোড করে ইনস্টল

✅ ইনস্টল করার সময় এগুলো tick দিন:

* **Add to PATH**
* **Open with Code** (context menu)

---

# Part B — Install MSYS2

## B1) Download & Install

1. সার্চ: **MSYS2 download** (msys2.org থেকে)
2. Install শেষ হলে Start Menu এ MSYS2 দেখাবে

---

# Part C — Install Compiler (64-bit recommended)

## C1) Open correct MSYS2 shell

Start Menu থেকে খুলুন:

### ✅ For 64-bit student (Recommended)

* **MSYS2 UCRT64**

### ✅ For 32-bit student

* **MSYS2 MINGW32**

---

## C2) Update MSYS2 (সব shell-এ একই নিয়ম)

প্রথমবার চালান:

```bash
pacman -Syu
```

শেষ হলে shell বন্ধ করে **same shell আবার খুলুন** (UCRT64 বা MINGW32)।

---

## C3) Install Toolchain (Compiler)

### ✅ 64-bit (UCRT64) — Best choice

```bash
pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain
```

### ✅ 32-bit (MINGW32)

```bash
pacman -S --needed base-devel mingw-w64-i686-toolchain
```

---

## C4) Verify compiler works (MSYS2 shell এর ভিতরে)

```bash
g++ --version
```

Version দেখালে OK ✅

---

# Part D — PATH Setup (Windows CMD/VS Code থেকে compiler চালাতে)

## D1) Add to Windows PATH

### ✅ 64-bit (UCRT64)

Add this:

* `C:\msys64\ucrt64\bin`

### ✅ 32-bit (MINGW32)

Add this:

* `C:\msys64\mingw32\bin`

## D2) How to add PATH

1. Start → “Environment Variables”
2. **Edit the system environment variables** → **Environment Variables…**
3. “Path” (User বা System) → Edit → New → path paste → OK
4. সব terminal + VS Code বন্ধ করে আবার খুলুন

## D3) Verify in CMD (important)

CMD খুলে:

```bat
g++ --version
```

✅ এখানে version দেখালে PATH perfect.

> **Note:** PowerShell কখনো কখনো পুরোনো PATH ধরে রাখে—সেক্ষেত্রে VS Code সম্পূর্ণ restart (Task Manager থেকে Code.exe end task) দিলে ঠিক হয়।

---

# Part E — VS Code Project Workflow (No extension needed)

## E1) Open Folder properly

1. একটা folder বানান: `C:\test-cp`
2. VS Code → **File → Open Folder…** → `C:\test-cp`

## E2) Create `main.cpp`

`main.cpp`:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int a, b;
    cin >> a >> b;
    cout << a + b << "\n";
    return 0;
}
```

---

# Part F — 1-key Build + Run (F5) without extensions

## F1) Create folder `.vscode`

Path: `C:\test-cp\.vscode\`

## F2) Create `tasks.json` (Build)

`C:\test-cp\.vscode\tasks.json`

### ✅ 64-bit (UCRT64) tasks.json

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "build active cpp (msys2)",
      "type": "process",
      "command": "C:\\msys64\\ucrt64\\bin\\g++.exe",
      "args": [
        "-std=gnu++17",
        "-O2",
        "-pipe",
        "-Wall",
        "-Wextra",
        "${file}",
        "-o",
        "${fileDirname}\\a.exe"
      ],
      "problemMatcher": ["$gcc"],
      "group": { "kind": "build", "isDefault": true }
    }
  ]
}
```

### ✅ 32-bit (MINGW32) tasks.json

শুধু `command` লাইনে path বদলান:

```json
"command": "C:\\msys64\\mingw32\\bin\\g++.exe"
```

---

## F3) Create `launch.json` (F5 = Build + Run)

`C:\test-cp\.vscode\launch.json`

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Run a.exe (build first)",
      "type": "cppvsdbg",
      "request": "launch",
      "program": "${fileDirname}\\a.exe",
      "cwd": "${fileDirname}",
      "console": "integratedTerminal",
      "preLaunchTask": "build active cpp (msys2)"
    }
  ]
}
```

✅ এখন:

* **Ctrl+Shift+B** = Build
* **F5** = Build + Run
* **Ctrl+F5** = Run without debugging (fast)

---

# Part G — IntelliSense (লাল দাগ) Fix (optional but recommended)

VS Code → `Ctrl+Shift+P` → **C/C++: Edit Configurations (UI)**

### ✅ 64-bit compiler path

`C:\msys64\ucrt64\bin\g++.exe`

### ✅ 32-bit compiler path

`C:\msys64\mingw32\bin\g++.exe`

আর সেট করুন:

* IntelliSense mode: `windows-gcc-x64` (64-bit) / `windows-gcc-x86` (if available)
* C++ standard: `gnu++17`

তারপর:
`Ctrl+Shift+P` → **C/C++: Reset IntelliSense Database** → Reload Window

> (শুধু CP submit করার জন্য এটা বাধ্যতামূলক নয়—compile ঠিক থাকলেই চলে)

---

# Part H — Common Issues & Fix (Teacher Cheat Sheet)

## 1) PowerShell-এ `g++ not recognized` কিন্তু CMD-তে কাজ করে

✅ Fix:

* VS Code পুরো বন্ধ করুন (Task Manager → Code.exe End Task)
* আবার খুলুন
* অথবা tasks.json এ full path থাকলে F5 দিয়ে compile ঠিকই হবে

## 2) `bits/stdc++.h` error দেখাচ্ছে

* 90% IntelliSense config issue
  ✅ Fix: compilerPath ঠিক করুন (Part G)

## 3) Build ok কিন্তু run এ instantly close

✅ Fix:

* VS Code integrated terminal use করুন (launch.json এ আছে)
* input থাকলে terminal এ input দিন

## 4) Student accidentally wrong shell used

* 64-bit student সবসময় **UCRT64**
* 32-bit student হলে **MINGW32**

---

# Part I — Teacher “Final Checklist” (Setup Done?)

স্টুডেন্টকে এই ৫টা verify করান:

1. CMD এ `g++ --version` কাজ করে ✅
2. VS Code → Open Folder দিয়ে প্রজেক্ট খুলেছে ✅
3. `.vscode/tasks.json` আছে ✅
4. `.vscode/launch.json` আছে ✅
5. `main.cpp` ওপেন রেখে **F5** চাপলে run হয় ✅
