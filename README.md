# FIN657 Course Repository

## Overview

This is a README file for the Github repository for the course 
FIN 657 (Financial Econometrics) at Emory University taught by [William Mann](https://sites.google.com/site/williamgilesmann/).
(At the moment, it is also the landing page for the course on Github Pages, because I haven't yet built out a proper landing page, but that will change sometime soon.)

This repository contains the files used when I teach the course.
It is a collection of slides, Python notebooks, and other materials.
Students are required to be able to run this code locally so they can follow the course concepts and complete their homework assignments.
There are several ways to do this, but this document explains the easiest way, which is to clone the repo locally and set up a Conda environment as specified by the `environment.yml` file included with this repo.

---

To run the code on your own computer, you will need to:

1. Create a Conda environment from `environment.yml`
2. Create a personal `.env` file with your credentials

Follow the steps below in order.

---

## Prerequisites

You must have **Conda** installed. There are several different versions of it. The most common are Miniconda or Anaconda, both of which are fine.

You will also need a terminal:

- macOS / Linux: Terminal
- Windows: Anaconda Prompt or PowerShell

However, you do not need much experience with either Conda or terminal commands. Just follow the steps below.

---

## 1. Download or Clone This Repository

If you know how to use Git:

    git clone https://github.com/wgjm1986/FIN657
    cd FIN657

If you haven't installed or used git before, but want to try, see the [official webpage](https://git-scm.com) for resources to help you get started.

If you don't want to use git, you can download the repository as a ZIP file from the GitHub website and then unzip it.

(In either case, note that I will be adding materials to the repo as the semester progresses. If you did `git clone` then you can always pull the updates with `git pull`. If you are downloading from the GitHub website then you can navigate there to find the new files, or download the whole repo again.)

All remaining commands below should be run **from inside the repository directory**.

---

## 2. Create the Conda Environment

This repository includes an `environment.yml` file that specifies all required packages.

Create the environment by running:

    conda env create -f environment.yml

This will create a Conda environment named:

    FIN657

Once the environment is created, activate it:

    conda activate FIN657

Finally, register this Conda environment with Jupyter so that it appears as a selectable
kernel in notebooks:

    python -m ipykernel install --user --name FIN657 --display-name "FIN657 (conda)"

This step makes it easy to ensure your notebook is using the correct Python environment.
If you skip it, Jupyter may default to the wrong Python environment.
We will discuss in class what this means and why it matters.

---

## 3. Set Up Your Credentials (`.env` file)

This project uses **environment variables** to store credentials such as API keys and usernames.

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

Do not use quotes or spaces in the above. For example if your FRED key is abc123 and your WRDS username is jdoe, then the two lines in your file should be FRED_API_KEY=abc123 and WRDS_USERNAME=jdoe.

The Python code automatically loads variables from `.env` using the `python-dotenv` package.
As long as your `.env` file is present and correctly filled out, you should not need to personalize the code in any way for it to run properly.

**Note:** It is possible to store your WRDS password in .env, but you do not need to and I recommend you don't.
Instead, the wrds library will prompt you for your password the first time you connect,
then will store it in a secure `.pgpass` file on your computer for future logins.
This is better than having you type the password in cleartext into the .env file.

If you are prompted for your WRDS password every time you run the code, 
it usually means the `.pgpass` file was not created correctly.
This is usually easy to troubleshoot and I can help if needed.

---

## 4. Running the Code

### Background

Once you have set up the Conda environment and your credentials file, you can run any Python code and expect it to match my results.
For this class, our code examples are contained in notebook files, which require some explanation if you are not familiar.

Notebooks are files that include both blocks of code, results from that code including figures, and blocks of text discussing the code.
These files are viewed through web browsers like a webpage.
To use them, you first use the `jupyter notebook` command to start a tiny server running on your own computer that can talk to a web browser and tell it what to display.
Once that server is running, you can use a web browser to navigate and open Jupyter files.

### Steps to follow

To open, edit, and run a notebook, do the following:

(1) Open a terminal

(2) Navigate to the repository directory

(3) Activate the environment:

    conda activate FIN657

(4) Launch jupyter: 

    jupyter notebook

(5) Look for the browser window that opens up. If one does not open automatically, find the URL that appears in the output of the above command, and paste it into a browser window.

(6) Navigate to the file that you want and click once to open.

(7) When finished, you can close this file and use the earlier tab to navigate to a different one if desired.

(8) When you are completely done, close all the browser windows that have opened up, go back to the terminal from earlier, kill the notebook server by entering `Ctrl+C`, and exit the terminal window.

---

## A word about Binder

Binder is a free online environment that lets you launch and run code directly from a GitHub repository like this one.
It can be useful for previewing how our notebooks are structured and how the code is meant to work once you are set up locally.

However, Binder should be treated as a public and untrusted environment. 
It does not provide security guarantees appropriate for handling secrets.
So, as a matter of standard security practice, 
**you should never enter confidential information into Binder**,
including usernames, passwords, or API keys (and this may even violate terms of service for the databases we use). 

For this reason, any use of Binder with this repository should be limited to code that does not require downloading protected data. 
Any code that requires credentials should be run locally using a .env file as described above.
This README does not include instructions on using Binder, to avoid encouraging credential use in an environment that is not designed for it.

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

