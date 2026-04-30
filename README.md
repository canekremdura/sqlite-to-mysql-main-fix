# 🗄️ SQLite to MySQL Converter

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![SQLite](https://img.shields.io/badge/Database-SQLite-003B57.svg)
![MySQL](https://img.shields.io/badge/Database-MySQL-4479A1.svg)

A practical and robust Python script designed to seamlessly migrate or convert your SQLite databases into MySQL-compatible SQL dump files.

## 🌟 Features

*   **Automated Schema Translation:** Intelligently maps SQLite data types (TEXT, INTEGER, REAL, etc.) to their MySQL equivalents (VARCHAR, INT, DECIMAL, etc.).
*   **Data Export:** Generates standard `INSERT INTO` statements compatible with MySQL servers.
*   **Table Generation:** Recreates table structures with appropriate MySQL engines (e.g., InnoDB) and charsets (e.g., utf8mb4).
*   **Easy to Use:** Run it directly via the command line with simple arguments.

## ⚙️ Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/canekremdura/sqlite-to-mysql-main-fix.git
    cd sqlite-to-mysql-main-fix
    ```

2.  **Environment Setup:**
    The script primarily relies on the built-in `sqlite3` Python library. You just need Python installed.
    ```bash
    python --version
    ```

## 🚀 Usage

Execute the script by providing your source SQLite database file. You can optionally specify an output file name.

**Basic Usage:**
```bash
python export.py database.sqlite
```
*This will create a `database.sql` dump file in the same directory.*

**Specifying Output File:**
```bash
python export.py database.sqlite my_mysql_dump.sql
```

**Additional Flags:**
*   `--no-drop`: Prevents adding `DROP TABLE IF EXISTS` statements in the generated SQL file.
    ```bash
    python export.py database.sqlite --no-drop
    ```

## 📥 Importing to MySQL

Once you have generated the `.sql` file, you can easily import it into your MySQL database:

```bash
mysql -u your_username -p your_database_name < my_mysql_dump.sql
```

## 📄 License
Open source and available for modification. See project files for details.
