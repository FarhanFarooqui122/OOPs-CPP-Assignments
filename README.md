# OOPs C++ Assignments

Lab assignments for the Object-Oriented Programming with C++ course.
Every file is a standalone program with its own `main()` — compile and run one at a time.

## Assignments

| File | Topic |
| --- | --- |
| `Ass01.cpp` | Class basics — `Student` with name, roll number and marks, percentage calculation |
| `Ass02.cpp` | Constructors — `Employee` with default and parameterized constructors |
| `Ass03.cpp` | Operator overloading — `Complex` number addition via `operator+` |
| `assignment4.cpp` | Parameter passing — swapping two values using references and pointers |
| `Ass05.cpp` | Friend classes — `Student` and `Result` sharing private data |
| `Ass06.cpp` | Inheritance — `Person` → `Student` / `Teacher`, plus `Exam` over student data |
| `Ass07.cpp` | Polymorphism — virtual functions with `override`, function overloading |
| `Ass08.cpp` | Encapsulation — `BankAccount` with private state and public operations |
| `Ass09.cpp` | Move semantics — copy vs. move constructor for a student record transfer |
| `Ass10.cpp` | Templates — function template for maximum marks, class template for results |
| `Ass11.cpp` | STL containers — `Book` records stored in `list` with prices in `vector` |
| `Ass12.cpp` | Type casting — menu-driven unit conversion using implicit and explicit casts |

## Build and run

Requires a C++ compiler (g++ / MSVC / clang).

```bash
g++ Ass01.cpp -o Ass01
./Ass01
```

On Windows with MSVC:

```powershell
cl Ass01.cpp
Ass01.exe
```

Compiled binaries and object files are ignored by git — build artifacts are not committed.
