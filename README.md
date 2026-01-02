# FIN657 Course Repository

This repository contains Python code and notebooks used in **FIN 657**.

To run the code on your own computer, you will need to:

1. Create a Conda environment from `environment.yml`
2. Create a personal `.env` file with your credentials

Follow the steps below in order. Do **not** skip steps.

---

## Prerequisites

You must have **Conda** installed. Either of the following is fine:

- **Miniconda** (recommended): https://docs.conda.io/en/latest/miniconda.html
- **Anaconda**

You will also need a terminal:

- macOS / Linux: Terminal
- Windows: Anaconda Prompt or PowerShell

You do **not** need prior experience with Conda.

---

## 1. Download or Clone This Repository

If you know how to use Git:

    git clone https://github.com/wgjm1986/FIN657
    cd FIN657

Otherwise, download the repository as a ZIP file from GitHub and unzip it.

All remaining commands should be run **from inside the repository directory**.

---

## 2. Create the Conda Environment

This repository includes an `environment.yml` file that specifies all required packages.

Create the environment by running:

    conda env create -f environment.yml

This will create a Conda environment named:

    FIN657

Once the environment is created, activate it:

    conda activate FIN657

To confirm that the environment is active:

    python --version

Finally, register this Conda environment with Jupyter so that it appears as a selectable
kernel in notebooks:

    python -m ipykernel install --user --name FIN657 --display-name "FIN657 (conda)"

This step makes it easy to ensure your notebook is using the correct Python environment.
If you skip it, Jupyter may default to the wrong Python environment.
We will discuss in class what this means and why it matters.

---

## 3. Set Up Your Credentials (`.env` file)

This project uses **environment variables** to store credentials such as API keys and usernames.
These should **not** be hardcoded into the code.

### Step 3.1: Create your `.env` file

You will see a file called:

    .env.example

Make a copy of this file and rename it to:

    .env

macOS / Linux:

    cp .env.example .env

Windows (PowerShell):

    copy .env.example .env

---

### Step 3.2: Edit `.env`

Open `.env` in a text editor and replace the placeholder values with your own information.

The file looks like this:

    FRED_API_KEY=YOUR_FRED_API_KEY
    WRDS_USERNAME=YOUR_WRDS_USERNAME

Replace:

- `YOUR_FRED_API_KEY` with your personal FRED API key
- `YOUR_WRDS_USERNAME` with your WRDS username

Important rules:

- Do **not** use quotes
- Do **not** add spaces around `=`
- Do **not** share your `.env` file

Each student’s `.env` file will be different.

The Python code automatically loads variables from `.env` using the `python-dotenv` package.

As long as your `.env` file is present and correctly filled out, you do not need to do anything else.

**Note:** It is possible to store your WRDS password in .env, but you do not need to and I recommend you don't.
Instead, the wrds library will prompt you for your password the first time you connect,
then will store it in a secure .pgpass file on your computer for future logins.
This is better than having you type the password in cleartext into the .env file.

If you are prompted for your WRDS password every time you run the code, 
it usually means the `.pgpass` file was not created correctly.
This is usually easy to troubleshoot and I can help if needed.

---

## 4. Running the Code

All our examples are notebooks, which are files that have blocks of code along with text discussion.
They are viewed through web browsers like a webpage.
To open, edit, and run one of these files, do the following:

(1) Open a terminal

(2) Navigate to the repository directory

(3) Activate the environment:

    conda activate FIN323

(4) Launch jupyter: 

    jupyter notebook

(5) Look for the browser window that opens up. If one does not open automatically, find the URL that appears in the output of the above command, and paste it into a browser window.

(6) Navigate to the file that you want and click once to open!

(7) When finished, you can close this file and use the earlier tab to navigate to a different one if desired.

(8) When you are completely done, close all the browser windows that have opened up, go back to the terminal from earlier, kill the notebook server by entering `Ctrl+C`, and exit the terminal window.

---

## Common Problems

### Conda environment already exists

If you see an error saying the environment already exists, remove it and recreate it:

    conda env remove -n FIN657
    conda env create -f environment.yml

---

### Credentials not found or authentication errors

Check the following:

- `.env` exists (not `.env.example`)
- Variable names match exactly
- You restarted Python or Jupyter after editing `.env`

---

## What You Should NOT Do

- Do not commit your `.env` file to GitHub
- Do not hardcode API keys or usernames into notebooks
- Do not rename environment variables unless you also update the code

---

## Getting Help

When asking for help, include:

- The **exact error message**
- The step you were on
- Your operating system (Windows / macOS / Linux)

This will make it much easier to diagnose the issue.

---

## Licensing

This repository contains instructional materials and a small amount of
supporting software code.

- **Instructional materials**, including Jupyter notebooks (`.ipynb`),
  written explanations, examples, and course content, are licensed under
  the Creative Commons Attribution–NonCommercial 4.0 International License.
- **Standalone software code files** (e.g. `.py` scripts intended for reuse
  outside the instructional context) are licensed under the MIT License.

See `LICENSE` and `LICENSE-CODE` for details.

