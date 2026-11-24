# My First devops lab
## About
A beginner-level project designed to explore DevOps fundamentals through GitHub Actions, Linux commands, and workflow automation.
## Objectives
To establish an automated pipeline that runs few linux commands whenever there's a change made to the GitHub repository.
## Technologies
+ Github
+ Github actions
+ Ubuntu linux
+ YAML
## Usage
### Here's a flow chart describing the process
<img width="1026" height="1678" alt="image" src="https://github.com/user-attachments/assets/20f15440-2390-4407-b903-c4e0e6010c67" />

## Results
+ Successfully triggered workflow on repository pushes.
+ Automatically executed Linux commands using an Ubuntu runner.
+ Retrieved repository files using the checkout action.
+ Displayed system information, date, username, and directory contents.

## Learning outcomes
1. How to use Github.
2. How to use Github actions.
3. How to create a repository, workflow and to use them correcrtly.
4. How to succesfully integrate operating systems in github workflows.
5. How automation concept works.

## Troubleshooting Log: Intentional Failure

### What I did
I deliberately changed `echo` to `ech` in the "Say hello" step of
`.github/workflows/main.yml` to see how a failed pipeline looks like.
<img width="749" height="58" alt="image" src="https://github.com/user-attachments/assets/763e5e9d-feb8-4b39-ab5e-b07e7fb52176" />


### What happened
The workflow run failed with a red X. The "Say hello" step failed,
and the steps after it were skipped.
<img width="702" height="443" alt="Screenshot 2026-11-12 111024" src="https://github.com/user-attachments/assets/55a9aad5-0d17-457a-b709-1e96db690c0a" />

### Root cause
I misspelled the `echo` command. The Linux runner had no command
called `ech`, so it returned exit code 127 ("command not found").

### How I fixed it
I opened the workflow file, corrected `ech` to `echo`, and committed
the change. The pipeline re-ran automatically and passed.
<img width="724" height="60" alt="image" src="https://github.com/user-attachments/assets/5cdee49c-b068-4651-9686-a15db305a180" />


### What I learned
- A red X means one step failed, and later steps are skipped.
- The log shows the failing command and the error message.
- Exit code 127 means "command not found".


# Recently added section:
## Automated testing (CI)
### About
A Python CI pipeline built using GitHub Actions that automatically executes unit tests whenever changes are pushed to the repository. It also supports manual workflow execution.
### Files added:
+ calculator.py (the main python program that is going to be tested)
+ test_calculator.py (the file that contains automated tests for the calculator functions using pytest.)
+ requirements.txt (lists the Python dependencies required to run the project.)
+ .gitignore (prevents unnecessary files and sensitive data from being tracked by Git.)

### How to run it:
1. First: run *pip install -r requirements.txt*
2. Second: run *pytest -v*

### Troubleshooting Log: Intentional faliure
I intentionally introduced an error into the main Python program to simulate a real-world development issue and test the CI pipeline's ability to detect failing tests.

<img width="128" height="52" alt="image" src="https://github.com/user-attachments/assets/336d3894-8a74-45e5-a504-fe4bd3046756" />

### Result:

<img width="334" height="72" alt="image" src="https://github.com/user-attachments/assets/6774ba7f-095e-4803-b607-14dcec68e45b" />

### Root cause:

The pipeline failed because the modified calculator function produced an unexpected result that contradicted the expected output defined in the test.

<img width="770" height="530" alt="image" src="https://github.com/user-attachments/assets/00b52d07-591e-435f-a389-f9f421b17249" />

### How i fixed it:
I examined the GitHub Actions logs to identify the failing test, traced the issue back to the modified function, and corrected the implementation to satisfy the expected test conditions.

<img width="381" height="135" alt="image" src="https://github.com/user-attachments/assets/d5e28874-6716-4bc4-b6be-9211dc5a6cab" />













### Author:
Ahmed Adil
