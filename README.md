# Language Validator for X/Twitter Datasets

This script automatically detects the language of social media posts stored in a CSV file and validates whether they are written in Portuguese.

The validation process uses the FastText language identification model (`lid.176.bin`) developed by Facebook Research.

## Features

- Reads CSV files generated after data collection and processing.
- Detects the language of each post using FastText.
- Marks Portuguese posts as `VALID`.
- Marks non-Portuguese posts as `INVALID`.
- Exports a new validated CSV file.

## Requirements

- Python 3.12+
- pandas
- fasttext
- FastText language model (`lid.176.bin`)

Install dependencies:

```bash
pip install pandas
pip install fasttext
```

## Input

The input CSV must contain a column named:

```text
post_description
```

which stores the text content of each collected post.

## Output

The script creates a new CSV file containing the validation results in the column:

```text
post_validation_status
```

Possible values:

| Value | Meaning |
|---------|----------|
| VALID | Portuguese post (`pt`) |
| INVALID | Non-Portuguese post |

## Usage

Run:

```bash
python verificar_idioma.py
```

The script will ask for:

```text
Input CSV path:
Output CSV path:
```

Example:

```text
Input CSV path:
/data/x_2026-05-25_2026-05-31_before.csv

Output CSV path:
/data/x_2026-05-25_2026-05-31.csv
```

## Workflow

1. Load the FastText language identification model.
2. Read the input CSV.
3. Detect the language of each post.
4. Assign validation status:
   - `VALID` for Portuguese (`pt`)
   - `INVALID` for all other languages.
5. Export the validated CSV.

## License

This project uses the FastText language identification model provided by Facebook Research.

FastText:
https://fasttext.cc/

Language Identification Model:
https://fasttext.cc/docs/en/language-identification.html
