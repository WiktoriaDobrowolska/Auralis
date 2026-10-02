# Auralis

A Windows desktop app for tracking calories and macros, built with C#/.NET, WPF and SQLite.

Auralis helps one person keep a daily food and activity log, see their calorie balance against a personal goal, and review weekly statistics. It can also estimate daily calorie and macro targets from the user's own data.

> **Status:** in development. This is a university project for the course *Programowanie w Środowisku Windows* (2026/2027).

## Features

- **Product database:** foods with calories, protein, fat and carbs per 100 g. Products already used in the history are archived instead of deleted.
- **Meal log:** record meals by date, meal type (breakfast, lunch, dinner, snack), product and weight. Nutrition values are stored with each entry, so editing a product later does not change past days.
- **Activity log:** record activities with duration and calories burned.
- **Daily balance:** calories eaten minus calories burned, with progress towards calorie and macro goals and a warning when the limit is exceeded.
- **Goals with history:** each day is evaluated against the goal that applied on that day. Changing the goal never rewrites the past.
- **Target calculator:** estimates BMR (Mifflin-St Jeor), TDEE and macro targets from sex, age, height, weight, activity level and goal (lose, maintain, gain). The result is a proposal the user can accept or adjust. It is an estimate, not medical advice.
- **Weekly report:** totals and daily averages, days on / above / below target, best and worst day, most frequent products, calories by meal type, macro split and charts.

## Tech stack

| Area | Technology |
|---|---|
| Language / platform | C#, .NET |
| UI | WPF |
| Data access | EF Core |
| Storage | SQLite |
| Tests | xUnit |

## Solution structure

```
Auralis/
├── src/
│   ├── Auralis.Core/    # domain model, business rules, calculator, statistics
│   ├── Auralis.Data/    # EF Core, SQLite, repositories
│   └── Auralis.App/     # WPF user interface
└── tests/
    └── Auralis.Tests/   # unit tests for rules and calculations
```

The UI depends on Core and Data. Core knows nothing about the database or the UI, so business rules can be tested in isolation.

## Getting started

Requirements: Windows and the .NET SDK (the version used by the solution).

```bash
git clone https://github.com/<your-username>/Auralis.git
cd Auralis
dotnet build
dotnet test
dotnet run --project src/Auralis.App
```

The SQLite database file is created locally and is not stored in the repository.

## Out of scope

Accounts and login, multiple profiles, barcode scanning, external food databases, cloud sync, wearable integrations, weight tracking over time, and micronutrients (fiber, sugar, salt, vitamins).

## Authors

- Name Surname (@github-username)
- Name Surname (@github-username)
