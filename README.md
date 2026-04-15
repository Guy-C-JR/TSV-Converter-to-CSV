[README.md](https://github.com/user-attachments/files/26746373/README.md)
# TSV Converter to CSV/.md

Python script that converts TSV or CSV files into:

- CSV (recommended for Codex / AI / database reference work)
- TXT (plain text with tab-separated values)
- MD (Markdown table output)

This converter is built for very large files because it streams the input row by row instead of loading the full file into memory.

It does **not** guarantee unlimited file size.

It is still limited by:

- available disk space
- filesystem limits
- total processing time
- your machine's stability while the job is running

## Files in this folder

- `tsv_to_csv_or_txt.py` - the converter
- `run_converter.bat` - double-click launcher for Windows watch mode
- `README.md` - this guide
- `Processing` - place TSV or CSV files here for watched conversion
- `Output_CSV` - converted CSV files land here
- `Output_TXT` - converted TXT files land here
- `Output_MD` - converted Markdown files land here

## Main workflow

1. Double-click `run_converter.bat`.
2. Keep the watcher window open.
3. Choose the auto-convert target in the watcher window: CSV, Text, or Markdown.
4. Drop one or more TSV or CSV files into `Processing`.
5. The watcher queues all stable files and processes them automatically.
6. A progress window appears during each conversion.
7. The converted file is written into `Output_CSV`, `Output_TXT`, or `Output_MD`.

The original source file stays in `Processing` as your source reference.

## Folder paths

- Main folder:


- Processing folder:


- CSV output:


- TXT output:


- MD output:


## Fastest way to run it

Use one of these:

- Double-click `run_converter.bat`
- Or run the watcher manually from Command Prompt or PowerShell

```bat
cd /d "C:\Users\
python tsv_to_csv_or_txt.py --watch
```

If `python` is not recognized:

```bat
cd /d "C:\
py tsv_to_csv_or_txt.py --watch
```

## Recommended workflow for Codex / AI

1. Convert the TSV to CSV.
2. Store the CSV in your project folder.
3. Point Codex or your analysis workflow at the CSV.
4. Keep the original TSV as the source reference.

## Direct single-file command-line usage

Change into the folder:

```bat
cd /d "C:\Users\
```

Convert a specific TSV or CSV directly to CSV:

```bat
python tsv_to_csv_or_txt.py --input "C:\path\to\your_file.tsv" --format csv
```

You can also use the positional form:

```bat
python tsv_to_csv_or_txt.py "C:\path\to\your_file.tsv" --format csv
```

Convert to TXT instead:

```bat
python tsv_to_csv_or_txt.py --input "C:\path\to\your_file.tsv" --format txt
```

Convert TSV or CSV to Markdown:

```bat
python tsv_to_csv_or_txt.py --input "C:\path\to\your_file.tsv" --format md
python tsv_to_csv_or_txt.py --input "C:\path\to\your_file.csv" --format md
```

Use console prompts for a one-off conversion:

```bat
python tsv_to_csv_or_txt.py --prompt
```

## Overwrite an existing output file

```bat
python tsv_to_csv_or_txt.py --input "C:\path\to\your_file.tsv" --format csv --overwrite
```

## Encoding help

The script tries to detect BOM-based encodings automatically and otherwise defaults to `utf-8-sig`.

If you get an encoding error, try:

```bat
python tsv_to_csv_or_txt.py --input "C:\path\to\file.tsv" --format csv --encoding latin-1
```

If the file came from Excel or another Windows export, `utf-16` may also work:

```bat
python tsv_to_csv_or_txt.py --input "C:\path\to\file.tsv" --format csv --encoding utf-16
```

## Output details

- CSV output is written as UTF-8.
- TXT output is written as UTF-8.
- MD output is written as UTF-8 as a Markdown table.
- TXT keeps the data as tab-separated plain text.
- Watch mode shows a GUI progress bar based on the file being read.
- Watch mode queues all stable files in `Processing` and runs them sequentially using the selected output format.
- Direct command-line mode prints progress every 5,000 rows by default.
- Watch mode overwrites the matching output file if you reconvert the same source file to the same output format.

You can change the progress interval:

```bat
python tsv_to_csv_or_txt.py --input "C:\path\to\file.tsv" --format csv --progress-every 50000
```

Disable progress messages:

```bat
python tsv_to_csv_or_txt.py --input "C:\path\to\file.tsv" --format csv --progress-every 0
```

## Default recommendation

Use:

```bat
python tsv_to_csv_or_txt.py --watch
```
