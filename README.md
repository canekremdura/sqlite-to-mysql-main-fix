# SQLite to MySQL Converter

Python-based tool to convert SQLite databases to MySQL compatible SQL dump files.

## Features

- ✅ Convert SQLite databases to MySQL SQL dumps
- ✅ Export both table structures and data
- ✅ Automatic data type conversion
- ✅ UTF-8 character encoding support
- ✅ Graceful handling of interrupted operations
- ✅ Engine and charset configuration

## Fixed Issues

### 1. VARCHAR Length Issue
**Problem:** SQLite `varchar` fields can be defined without length, but MySQL requires length specification.

**Solution:** Automatically adds default length `varchar(255)` to all varchar fields.

### 2. Numeric Data Type Compatibility
**Problem:** SQLite `numeric` types cause incompatibility issues in MySQL.

**Solution:** Converts `numeric` types to `decimal(10,2)` format.

## Installation

```bash
# Clone the repository
git clone https://github.com/canekremdura/sqlite-to-mysql-main-fix.git
cd sqlite-to-mysql-main-fix
```

No additional dependencies required! Uses Python standard library.

## Usage

```bash
# Basic usage
python export.py database.sqlite

# With output file
python export.py database.sqlite output.sql
```

### Example

```bash
python export.py veritabani.sqlite cikti.sql
```

## Output

The converter generates a MySQL-compatible SQL file with:
- Table creation statements with proper data types
- INSERT statements for all data
- UTF-8 charset configuration
- InnoDB engine specification

## Data Type Mappings

| SQLite | MySQL |
|--------|-------|
| `varchar` | `varchar(255)` |
| `numeric` | `decimal(10,2)` |
| `char` | `char(1)` |
| `int` | `int` |
| `integer` | `int` |
| `real` | `decimal(10,3)` |
| `blob` | `blob` |
| `text` | `text` |

## Requirements

- Python 3.x
- SQLite database file

## License

MIT License

## Credits

**Original Developer:** Majid Alavizadeh  
**Fixes and Improvements:** Can Ekrem Dura

## Author

**Can Ekrem Dura**

[GitHub Profile](https://github.com/canekremdura)

---

*Check out my other projects:*
- [csv-to-json-cli](https://github.com/canekremdura/csv-to-json-cli) - CSV to JSON converter
- [Mackolik-Bot](https://github.com/canekremdura/Mackolik-Bot) - Football match data scraper
- [wp-custom-variation-swatches](https://github.com/canekremdura/wp-custom-variation-swatches) - WooCommerce swatches
