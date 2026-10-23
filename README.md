# Smart Expense Tracker 💸

A desktop personal-finance application built with **Java 17, Swing, SQLite, and Maven**. Add income and expenses, search transactions, review totals, edit/delete entries, and export filtered data to CSV.

## Features

- Add, edit, and delete transactions
- Record income and expenses with dates, categories, descriptions, and amounts
- Summary cards for total income, expenses, and balance
- Search descriptions/categories and filter by transaction type
- Persistent local SQLite database
- Export the currently filtered transactions to CSV
- Input validation and confirmation before deletion

## Tech stack

- Java 17+
- Java Swing
- SQLite via Xerial SQLite JDBC
- Maven

## Requirements

Install a JDK 17 or newer and Maven. Check your setup:

```bash
java -version
mvn -version
```

## Run the application

Clone the repository, then run these commands from the project directory:

```bash
mvn clean package
mvn exec:java -Dexec.mainClass="dev.portfolio.expensetracker.ExpenseTrackerApp"
```


The application creates `expense-tracker.db` in the working directory on first launch. Keep this file private if it contains personal financial data; it is intentionally excluded from Git.

## How to use

1. Enter a date using `YYYY-MM-DD`.
2. Select `EXPENSE` or `INCOME` and choose a category.
3. Enter a description and positive amount, then click **Save transaction**.
4. Select a row to load it into the form for editing or deletion.
5. Use search and type filters to narrow the table.
6. Click **Export CSV** to save the visible filtered results.

## Project structure

```text
smart-expense-tracker/
├── pom.xml
├── README.md
├── .gitignore
└── src/
    └── main/java/dev/portfolio/expensetracker/
        ├── ExpenseTrackerApp.java
        ├── Database.java
        ├── Transaction.java
        ├── TransactionDAO.java
        └── CsvExporter.java
```

## Database design

The `transactions` table stores:

| Column | Description |
|---|---|
| `id` | Auto-incrementing primary key |
| `transaction_date` | Transaction date (`YYYY-MM-DD`) |
| `type` | `INCOME` or `EXPENSE` |
| `category` | User-selected category |
| `description` | Short transaction note |
| `amount` | Positive amount |

Prepared SQL statements are used for database operations.

## Ideas for future improvements

- Monthly budgets and alerts
- Charts for category-wise spending
- Monthly reports
- Unit and integration tests
- Optional recurring transactions
- Packaging as a native desktop installer

## Contributing

Issues and pull requests are welcome. For substantial changes, open an issue first to discuss the proposal.

## License

This project is available under the MIT License. See [LICENSE](LICENSE).
