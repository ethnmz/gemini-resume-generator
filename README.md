# Gemini Resume Generator

An AI-powered resume generator that uses Google's Gemini AI to optimize your resume for specific job descriptions. The tool takes your base resume in LaTeX format and tailors it to match job requirements while maintaining professional formatting.

## Features

- Uses Google Gemini AI (gemini-2.5-flash model) to optimize resume content
- Accepts resume input in LaTeX format for precise formatting control
- Tailors bullet points and content to match specific job descriptions
- Automatically generates PDF output using pdflatex
- Simple command-line interface
- Maintains 2-page maximum resume length

## Prerequisites

- Python 3.7+
- LaTeX distribution (MiKTeX on Windows, MacTeX on macOS, TeX Live on Linux)
- Google Gemini API key

## Installation

1. Clone this repository:
```bash
git clone https://github.com/ethnmz/gemini-resume-generator.git
cd gemini-resume-generator
```

2. Install required Python packages:
```bash
pip install -r requirements.txt
```

3. Install LaTeX:
   - **macOS**: Install MacTeX from https://www.tug.org/mactex/
   - **Windows**: Install MiKTeX from https://miktex.org/
   - **Linux**: `sudo apt-get install texlive-full` (Ubuntu/Debian)

## Configuration

1. Get a Google Gemini API key from [Google AI Studio](https://makersuite.google.com/app/apikey)

2. Update the API key in `resume.py`:
```python
API_KEY = "YOUR_API_KEY_HERE"
```

 **Security Note**: Never commit your API key to version control. Consider using environment variables:
```python
import os
API_KEY = os.getenv("GEMINI_API_KEY")
```

3. Create a `ResumeText` file containing your base resume in LaTeX format (without document class or preamble, just the content)

## Usage

1. Run the script:
```bash
python resume.py
```

2. When prompted, paste the job description you're applying for

3. Type `END` on a new line when finished

4. The script will generate:
   - `resume.tex` - LaTeX source file
   - `resume.pdf` - Final PDF resume

## Project Structure

```
gemini-resume-generator/
├── resume.py           # Main script
├── ResumeText         # Your base resume content (LaTeX format)
├── requirements.txt   # Python dependencies
├── README.md          # This file
├── .gitignore        # Git ignore rules
├── resume.tex        # Generated LaTeX (output)
└── resume.pdf        # Generated PDF (output)
```

## Configuration Options

You can customize the following in `resume.py`:

- `MODEL_NAME`: Change the Gemini model (default: "gemini-2.5-flash")
- `RESUME_TEXT_FILE`: Path to your base resume file
- `OUTPUT_TEX`: Output LaTeX file name
- `OUTPUT_PDF`: Output PDF file name

## How It Works

1. Reads your base resume from the `ResumeText` file
2. Accepts a job description via command line
3. Sends both to Gemini AI with instructions to optimize the resume
4. Generates clean LaTeX code following strict formatting rules
5. Compiles the LaTeX to PDF using pdflatex

## LaTeX Rules

The generator follows these strict rules for clean, ATS-friendly formatting:

- Uses standard LaTeX (article class)
- No custom commands or macros
- Simple sections and itemize environments
- US Letter paper size
- 0.75-inch margins
- Professional, minimal styling



## Acknowledgments

- Powered by [Google Gemini AI](https://deepmind.google/technologies/gemini/)
- LaTeX for professional document formatting
