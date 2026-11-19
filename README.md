# OOPs C++ Assignments

Lab assignments for the Object-Oriented Programming with C++ course. Each file is a standalone program with its own `main()`, written to demonstrate one core OOP concept.

## At a glance

- 12 standalone C++ programs
- C++11 or newer (move semantics and `override` are used)
- No build system or external libraries — a single compiler command per file

## Assignments

| # | File | Topic | Key concepts |
| --- | --- | --- | --- |
| 1 | `Ass01.cpp` | Class basics | `Student` with name, roll number and marks; percentage calculation |
| 2 | `Ass02.cpp` | Constructors | `Employee` with default and parameterized constructors |
| 3 | `Ass03.cpp` | Operator overloading | `Complex` number addition via `operator+` |
| 4 | `assignment4.cpp` | Parameter passing | Swapping two values with references and with pointers |
| 5 | `Ass05.cpp` | Friend classes | `Student` and `Result` sharing private data; static counter |
| 6 | `Ass06.cpp` | Inheritance | `Person` → `Student` / `Teacher`, plus `Exam` over student data |
| 7 | `Ass07.cpp` | Polymorphism | Virtual functions with `override`, function overloading |
| 8 | `Ass08.cpp` | Encapsulation | `BankAccount` with private state and public operations |
| 9 | `Ass09.cpp` | Move semantics | `Student` records handed between objects with `std::move`; no copy or move constructor is written by hand |
| 10 | `Ass10.cpp` | Templates | Function template for maximum marks, class template for results |
| 11 | `Ass11.cpp` | STL containers | `Book` records in a `list`, prices in a `vector` |
| 12 | `Ass12.cpp` | Type casting | Menu-driven unit conversion using implicit and explicit casts |

### Standard headers used

| Headers | Files |
| --- | --- |
| `<iostream>` only | `Ass03.cpp`, `Ass12.cpp`, `assignment4.cpp` |
| `<iostream>`, `<string>` | `Ass01.cpp`, `Ass02.cpp`, `Ass05.cpp`, `Ass06.cpp`, `Ass07.cpp`, `Ass08.cpp`, `Ass10.cpp` |
| `<iostream>`, `<string>`, `<utility>` | `Ass09.cpp` (uses `std::move`) |
| `<iostream>`, `<list>`, `<vector>`, `<string>` | `Ass11.cpp` |

Nothing else is pulled in — no third-party libraries, no shared headers.

### Size at a glance

| File | Lines |
| --- | --- |
| `Ass09.cpp` | 42 |
| `Ass10.cpp` | 49 |
| `assignment4.cpp` | 57 |
| `Ass05.cpp` | 64 |
| `Ass12.cpp` | 71 |
| `Ass02.cpp` | 79 |
| `Ass03.cpp` | 85 |
| `Ass07.cpp` | 92 |
| `Ass08.cpp` | 104 |
| `Ass01.cpp` | 149 |
| `Ass11.cpp` | 154 |
| `Ass06.cpp` | 242 |

## Build and run

Requires a C++ compiler: g++ (MinGW), MSVC or clang.

```bash
g++ -std=c++17 Ass01.cpp -o Ass01
./Ass01
```

On Windows with MSVC:

```powershell
cl /EHsc /std:c++17 Ass01.cpp
.\Ass01.exe
```

### Build every assignment (PowerShell + g++)

```powershell
Get-ChildItem *.cpp | ForEach-Object {
    $exe = [IO.Path]::GetFileNameWithoutExtension($_.Name)
    g++ -std=c++17 $_.FullName -o "$exe.exe"
}
```

Compiled binaries and object files are ignored by git — build artifacts are not committed.

## Running them

| Program | Reads input | Menu loop |
| --- | --- | --- |
| `Ass01.cpp` | yes | yes (1 enter / 2 report / 3 exit) |
| `Ass02.cpp` | yes | no |
| `Ass03.cpp` | yes | yes |
| `assignment4.cpp` | yes | no |
| `Ass05.cpp` | yes | no |
| `Ass06.cpp` | yes | no |
| `Ass07.cpp` | yes | no |
| `Ass08.cpp` | yes | yes |
| `Ass09.cpp` | **no** — runs start to finish | no |
| `Ass10.cpp` | yes | no |
| `Ass11.cpp` | yes | yes |
| `Ass12.cpp` | yes | yes (1–5, 5 = exit) |

The menu programs loop until you pick Exit, and `Ass01.cpp` keeps printing "Invalid choice" forever if
stdin hits EOF — run them in an interactive terminal (or pipe a trailing `exit` choice) rather than
redirecting an empty file into them.

### Compiler flags

`-std=c++17` is enough for every file. Add warnings while reading or modifying one:

```bash
g++ -std=c++17 -Wall -Wextra Ass01.cpp -o Ass01
```

`Ass12.cpp` exits with code **1** on invalid input instead of re-prompting, so scripted runs should check
`$LASTEXITCODE` (PowerShell) or `$?` (bash).

## Error handling

Only `Ass08.cpp` throws exceptions, and every one is deliberate:

| Trigger | Exception |
| --- | --- |
| Constructor called with a negative balance | `invalid_argument("Initial balance cannot be negative.")` |
| Deposit ≤ 0 | `invalid_argument("Deposit amount must be positive.")` |
| Withdrawal ≤ 0 | `invalid_argument("Withdrawal amount must be positive.")` |
| Withdrawal larger than the balance | `runtime_error("Insufficient account balance.")` |
| Non-numeric menu choice or amount | `runtime_error("Invalid menu input.")` / `runtime_error("Invalid amount input.")` |

`main()` catches them and prints the message instead of crashing. The other programs validate input with
plain `if` checks — `Ass12.cpp` is the one that responds to bad input by exiting with code **1**.

## Notes

- There is no `Ass04.cpp` — assignment 4 is the file named `assignment4.cpp`.
- Every program needs a C++11-or-newer compiler; `g++ -std=c++17` and Visual Studio 2019+ build them unchanged.
- Some programs are menu-driven and read from `cin`, so run them in an interactive terminal rather than piping input blindly.
- Programs are independent: there is no shared header, namespace or Makefile between them.

## Quick quiz

One question per program, with the answer — useful before a viva:

| # | Question | Answer |
| --- | --- | --- |
| 1 | Which file turns marks into a percentage? | `Ass01.cpp` — `class Student` holding name, roll number and marks |
| 2 | Where are default and parameterized constructors shown side by side? | `Ass02.cpp` — `Employee` |
| 3 | How is complex-number addition expressed? | `Ass03.cpp` — a member `operator+` that returns a new `Complex` |
| 4 | What differs between the two swap demos? | `assignment4.cpp` — one swaps through `int&`, the other through `int*` and dereferences |
| 5 | Which program reads another class's private data without inheritance? | `Ass05.cpp` — `friend` class `Result` over `Student`, plus a `static` counter |
| 6 | Which program has multiple inheritance? | `Ass06.cpp` — `Result : public Exam, public Sports`, with `Exam : public Student` |
| 7 | Where is runtime polymorphism? | `Ass07.cpp` — a `virtual` function in `Person` overridden with `override` in `Student` / `Teacher` |
| 8 | How does the bank reject a bad withdrawal? | `Ass08.cpp` — `runtime_error` for insufficient funds, `invalid_argument` for non-positive amounts |
| 9 | What does `Ass09.cpp` actually demonstrate? | `std::move` at the call sites; the move constructor used is the compiler-generated one |
| 10 | Function template vs class template? | `Ass10.cpp` — `findMaximum<T>()` for marks, `Student<T>` for the result |
| 11 | Which containers are used? | `Ass11.cpp` — `std::list<Book>` for records, `std::vector<double>` for prices |
| 12 | Which cast styles appear? | `Ass12.cpp` — implicit conversion, `static_cast`, and a C-style explicit cast |
