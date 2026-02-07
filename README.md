# Project: Linux for Data Engineering (Lab 1)

## Objective
This project simulates a real-world scenario where you, as a Data Engineer, must set up a staging environment. You will demonstrate proficiency in **Linux File Systems, Permissions, Process Management, and Bash Scripting.**

##  Project Setup (Do this first!)
1.  **GitHub:** Log in to your GitHub account.
2.  **Create Repo:** Create a new public repository named `linux-data-engineering-lab`.
3.  **Clone:** Clone this repository to your local machine (using WSL, Ubuntu, or Git Bash).
4.  **Documentation:** Add this `README.md` file to your repository so visitors know what the project is about.
5.  **Evidence:** As you complete the tasks below, you will need to take screenshots of your terminal commands and output. You will upload these screenshots to this repository.

---

##  The Scenario: DataCorp Staging Setup
You have just joined **DataCorp** as a Junior Data Engineer. Your team is preparing to deploy a new data ingestion pipeline. Before the deployment can happen, the team lead has tasked you with preparing the Linux staging server.

You must demonstrate your ability to navigate the file system, secure data directories, manage processes, and write basic automation scripts to ensure the server is ready for the ETL jobs.

---

## Task Instructions

### Part 1: File System Navigation & Structure
**Goal:** Create the directory structure required for the data pipeline.

1.  Navigate to your repository directory in your terminal.
2.  Create a directory named `datacorp_pipeline`.
3.  Inside `datacorp_pipeline`, create three sub-directories:
    * `source_data`
    * `processed_data`
    * `logs`
4.  Create an empty file named `pipeline.conf` inside the `datacorp_pipeline` directory.
5.  List the contents of the `datacorp_pipeline` directory to verify the structure.

### Part 2: File Permissions & Ownership
**Goal:** Secure the sensitive source data.

1.  Navigate into the `datacorp_pipeline` directory.
2.  Change the permissions of the `source_data` directory so that **only the owner** has Read, Write, and Execute permissions. No one else (Group or Others) should have any access.
3.  Verify the permission change by listing the directory details in "long format".

### Part 3: Environment Variables
**Goal:** Set up environment configurations for the pipeline.

1.  Create a temporary environment variable named `ETL_STAGE` and set its value to `staging`.
2.  Print the value of `ETL_STAGE` to the terminal to verify it is set.

### Part 4: Process Management
**Goal:** Manage a "stuck" background process.

1.  Start a "dummy" process that sleeps for 500 seconds in the background. (Hint: Use the `sleep` command combined with an operator to push it to the background).
2.  Find the **Process ID (PID)** of this sleep command using a process listing tool.
3.  Kill the process using its PID.
4.  Verify the process is gone.

### Part 5: Package Management
*(Skip this step if using Git Bash on Windows)*
**Goal:** Ensure the server has necessary monitoring tools.

1.  Update your system's package repository lists.
2.  Install a command-line system monitor tool called `htop`.
3.  Run `htop` to verify it is installed, then quit the application.

### Part 6: System Monitoring & I/O Redirection
**Goal:** Check server capacity and save the report.

1.  Run a command that displays the **disk space usage** of your system in a "human-readable" format.
2.  Instead of printing this to the screen, redirect the output to a file named `disk_report.txt` inside your `logs` directory.
3.  Use a command to display the contents of `logs/disk_report.txt` to the terminal to verify it worked.

### Part 7: Shell Scripting Basics
**Goal:** Automate the daily cleanup routine.

1.  Create a new file named `daily_maintenance.sh` inside the `datacorp_pipeline` directory.
2.  Add a "Shebang" line at the top to specify this is a bash script.
3.  The script should do the following two things sequentially:
    * Print the message: *"Starting daily maintenance on [Date]..."* (You can use the `date` command dynamically or just hardcode a string for now).
    * List the files currently inside the `source_data` directory.
4.  Make the script executable.
5.  Run the script.

---

## Submission Requirements

To complete this project, your GitHub repository must contain:

1.  **The Directory Structure:** The folders and files you created in Part 1.
2.  **The Script:** The `daily_maintenance.sh` file you wrote in Part 7.
3.  **The Proof:** A folder named `screenshots` containing images of your terminal for each Part (1-7), OR a single PDF document named `Lab_Report.pdf` with all screenshots compiled.

**Final Step:** Submit the URL to your GitHub repository.
