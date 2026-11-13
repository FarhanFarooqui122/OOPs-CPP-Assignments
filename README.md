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
| 9 | `Ass09.cpp` | Move semantics | Copy vs. move constructor for a student record transfer |
| 10 | `Ass10.cpp` | Templates | Function template for maximum marks, class template for results |
| 11 | `Ass11.cpp` | STL containers | `Book` records in a `list`, prices in a `vector` |
| 12 | `Ass12.cpp` | Type casting | Menu-driven unit conversion using implicit and explicit casts |

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

## Notes

- There is no `Ass04.cpp` — assignment 4 is the file named `assignment4.cpp`.
- Every program needs a C++11-or-newer compiler; `g++ -std=c++17` and Visual Studio 2019+ build them unchanged.
- Some programs are menu-driven and read from `cin`, so run them in an interactive terminal rather than piping input blindly.
- Programs are independent: there is no shared header, namespace or Makefile between them.
