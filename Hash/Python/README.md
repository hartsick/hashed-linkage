# CPL Hashed Linkage Toolkit - Hashing (Python)

This directory contains the Python code for running hashing a hashing algorithim against a CSV, outputting a CSV with PII hashed for research puposse.

This README focuses only on technical usage for the Python hashing script. For an overview including hashing concepts and possible configurations, see the [project README](https://github.com/californiapolicylab/hashed-linkage/blob/main/README.md).

## Requirements
- python 3
- python package installer (e.g. pip)
- a CSV with data to be hashed

## Usage
- Clone this repository
- Navigate to this directory (in repository root directory `cd Hash/Python`)
- Install dependencies
    - With pip: `pip install -r requirements.txt`
- Update `Hash/Python/hashing_config.ini` with any necessary configuration
    - Config you must supply:
        - `salt`: the secret that will be used to hash PII. Do not commit this updated value.
    - Config you will likely need to review and update:
        - `input`: the path to the input CSV
        - `output`: the desired path to the output CSV
        - `Max DOB year`: last acceptable DOB year; years later than this will be flagged as bad DOBs
        - values under `[Column names]`: the columns to be hashed as PII. Note: any additions or deletions from this list will require a corresponding change in the implementation code
- Verify the input CSV is at the `input` path provided in `hashing_config.ini`
- Run the script: `python hashing_base_linkagetoolkit.py`
    - Optionally, pass a custom hashing config by passing the path to the file as an argument (e.g. ` or `python hashing_base_linkagetoolkit.py <path/to/hashing_config.ini>`)
- On success, a CSV with PII hashed will be saved locally