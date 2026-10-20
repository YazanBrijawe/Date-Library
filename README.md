
# 📅 Date Library – clsDate (C++)

A complete Date class built from scratch in C++ using Object-Oriented Programming. It handles everything you need when working with dates: creating, validating, comparing, adding/subtracting days, weeks, months and years, printing calendars, and calculating business days and vacation return dates. Everything lives in a single header file (`clsDate.h`), so it's easy to drop into any project.

---

🚨 **Note : Feel free to fork, modify, or use this as a learning resource!** 🛠️

---

## ✨ Features

- **🏗️ Multiple Constructors**

  * 📆 Default → today's system date
  * 🔤 From a string (`"dd/mm/yyyy"`)
  * 🔢 From day, month, year
  * #️⃣ From the day's order in the year (e.g. day 60 of 2024)

- **✅ Validation & Info**

  * ✔️ Check if a date is valid (including leap years)
  * 🗓️ Leap year check
  * 📏 Number of days / hours / minutes / seconds in a month or a year
  * 📛 Day name and month short name (`Tue`, `Oct`)
  * 🔚 Last day in month / end of week / weekend checks

- **➕➖ Date Arithmetic**

  * Increase or decrease by: day, X days, week, X weeks, month, X months, year, X years, decade, X decades, century, millennium
  * 🧠 Smart month handling (`31/1/2024 + 1 month = 29/2/2024`)
  * 📐 Difference in days between two dates (with optional end-day include)
  * 🎂 Calculate age in days

- **⚖️ Comparison**

  * Before / Equal / After checks
  * `CompareDates()` returns an enum: `Before = -1`, `Equal = 0`, `After = 1`

- **🗓️ Calendar Printing**

  * Print a full month calendar
  * Print a full year calendar

- **💼 Business Days & Vacations**

  * Weekend = Friday & Saturday
  * Count business days between two dates
  * Calculate vacation return date (skipping weekends)
  * Days until end of week / month / year

- **🧩 Clean Design**

  * Every function has a `static` version (takes a date) and a member version (works on the object through `*this`)
  * Properties via `__declspec(property)` → use `Date.Day` like a normal variable while getters/setters run behind it

---

## 🛠️ How to Compile & Run

1. Put `clsDate.h` and `clsString.h` in the same folder as your `main.cpp`.
2. Compile:
   - **Visual Studio (MSVC):** works out of the box with `__declspec(property)` (replace `<bits/stdc++.h>` with the standard headers you need).
   - **Clang:**
```bash
     clang++ -std=c++17 -fms-extensions main.cpp -o DateApp
```
3. Run:
```bash
   ./DateApp
```

> ⚠️ `g++` doesn't support `__declspec(property)`, so use MSVC or Clang with `-fms-extensions`.

---

## 💻 Example Usage

```cpp
#include "clsDate.h"

int main()
{
    clsDate Date1("31/1/2024");
    clsDate Date2(20, 10, 2026);

    Date1.Print();                         // 31/1/2024
    cout << Date2.DayShortName() << endl;  // Tue

    Date1.IncreaseDateByOneMonth();
    Date1.Print();                         // 29/2/2024 (leap year)

    cout << clsDate::GetDifferenceInDays(clsDate(1, 1, 2026), Date2) << endl;   // 292
    cout << clsDate::CalculateBusinessDays(clsDate(1, 10, 2026), Date2) << endl; // 13

    clsDate::CalculateVacationReturnDate(clsDate(1, 10, 2026), 5).Print();      // 8/10/2026

    clsDate::PrintMonthCalendar(10, 2026);
    return 0;
}
```

**Calendar output:**

```
  _______________Oct_______________

  Sun  Mon  Tue  Wed  Thu  Fri  Sat
                        1    2    3
    4    5    6    7    8    9   10
   11   12   13   14   15   16   17
   18   19   20   21   22   23   24
   25   26   27   28   29   30   31
  _________________________________
```

---

## 📁 Project Structure

```
├── clsDate.h      # The Date class
├── clsString.h    # String helper (used for Split in the string constructor)
└── README.md
```
