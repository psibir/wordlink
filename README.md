# wordlink

![wordlink logo](/logo.png)

A tool that searches for a given term in multiple files within a directory and returns links to the matched occurrences within their sentence context. It provides two output options: an HTML file with clickable links or a console display using a formatted table.
The `__main__.py` file is located in the `/wordlink/` directory.

## Prerequisites

- Python 3.x
- `argparse` library
- `fuzzysearch` library
- `prettytable` library

## Installation

1. Clone the repository or download the script file.
2. Install the required libraries by running the following command:

   ```bash
   pip install wordlink
   ```

See [INSTALL](INSTALL) for instructions to clone from GitHub.

## Usage

Run the script using the following command:

```bash
python3 wordlink <search_term> <search_directory> [-o OUTPUT_FILE]
```

- `<search_term>`: The term to search for within the text files.
- `<search_directory>`: The directory to search for text files.
- `-o OUTPUT_FILE` or `--output_file OUTPUT_FILE`: (Optional) Specify the output file name to save the results as an HTML file. If not provided, the results will be displayed in the console using a formatted table.

**Examples:**

Search for the term "example" in the current directory and display the results in the console:

   ```bash
   python3 wordlink example .
   ```

Search for the term "example" in the directory "documents" and save the results as an HTML file named "output.html":

   ```bash
   python3 wordlink example documents -o output.html
   ```

See the `/examples/readme.md` for instructions on running a demo of the wordlink module.

## Output

The tool generates two types of output depending on the presence of the output file option:

1. **HTML Output File:** If an output file is specified using the `-o` or `--output_file` option, the tool generates an HTML file with clickable links. Each link represents a matched occurrence in a specific file and line. The output file contains a table with columns for the file name, line number, and corresponding text.

2. **Console Display:** If no output file is provided, the tool displays the results in the console using a formatted table. The console output includes columns for the file name, line number, and corresponding text.

## Tests

The tool includes a test suite to ensure its functionality. The `main_test.py` file contains the unit tests. Here's a description of what each test case in `main_test.py` is testing:

- `test_find_word_locations`: This test verifies that the `find_word_locations` method correctly identifies the locations of the given search term within a test file.
- `test_generate_links_output_file`: This test checks if the `generate_links` method generates the expected output file in HTML format when an output file name is provided.
- `test_generate_links_console`: This test validates that the `generate_links` method produces the expected console output when no output file name is provided.

To run the tests, navigate to the `/tests/` directory and execute the following command:

```bash
python3 main_test.py
```

## Limitations

- The tool searches for the specified term within all text files (`.txt`) in the given directory and its subdirectories. It does not support searching within other file formats.
- The maximum Levenshtein distance for finding near matches is set to 1. This can be adjusted by modifying the `max_l_dist` parameter in the `find_near_matches` function call within the `find_word_locations` method.

## License

This code is provided under the [MIT License](LICENSE). Feel free to modify and use it according to your needs.
