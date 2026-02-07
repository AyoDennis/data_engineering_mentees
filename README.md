# Project: DataCorp Staging Environment Setup

## Scenario
You have just joined **DataCorp** as a Junior Data Engineer. Your team is preparing to deploy a new data ingestion pipeline. Before the deployment can happen, the team lead has tasked you with preparing the Linux staging server.

You must demonstrate your ability to navigate the file system, secure data directories, manage processes, and write basic automation scripts to ensure the server is ready for the ETL jobs.

##  Prerequisites
* **Environment:** You must complete this project in a Linux-based environment.
    * **Mac/Linux Users:** Use your standard terminal.
    * **Windows Users:** It is highly recommended to use **WSL (Ubuntu)** or a **Docker container** running Ubuntu.
    * *Note for Git Bash users:* Most commands will work, but Package Management tasks may not apply.
* **Tools:** A command-line text editor (like `nano` or `vim`).

---

##  Project Instructions

### Part 1: File System Navigation & Structure
**Goal:** Create the directory structure required for the data pipeline.

1.  Navigate to your home directory.
2.  Create a parent directory named `datacorp_pipeline`.
3.  Inside `datacorp_pipeline`, create three sub-directories:
    * `source_data`
    * `processed_data`
    * `logs`
4.  Create an empty file named `pipeline.conf` inside the `datacorp_pipeline` directory.
5.  List the contents of the `datacorp_pipeline` directory to verify the structure (ensure you can see hidden files if any).

### Part 2: File Permissions & Ownership
**Goal:** Secure the sensitive source data.

1.  Navigate into the `datacorp_pipeline` directory.
2.  Change the permissions of the `source_data` directory so that **only the owner** has Read, Write, and Execute permissions. No one else (Group or Others) should have any access.
3.  Verify the permission change by listing the directory details in "long format".

### Part 3: Environment Variables
**Goal:** Set up environment configurations for the pipeline.

1.  Create a temporary environment variable named `ETL_STAGE` and set its value to `staging`.
2.  Print the value of `ETL_STAGE` to the terminal to verify it is set.
3.  *Bonus:* How would you make this variable persist if you closed the terminal? (You do not need to implement this, just add a comment in your submission about which file you would edit).

### Part 4: Process Management
**Goal:** Manage a "stuck" background process.

1.  Start a "dummy" process that sleeps for 500 seconds in the background. (Hint: Use the `sleep` command combined with an operator to push it to the background).
2.  Find the **Process ID (PID)** of this sleep command using a process listing tool.
3.  Kill the process using its PID.
4.  Verify the process is gone.

### Part 5: Package Management
*(Skip this step if using Git Bash)*
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

You must submit a **Single PDF** containing screenshots of your terminal.

1.  **Screenshot 1 (Setup):** Showing the creation of folders and the directory listing (Part 1).
2.  **Screenshot 2 (Permissions):** Showing the `ls -l` output of the locked-down folder (Part 2).
3.  **Screenshot 3 (Env Vars):** Showing the echo output of your variable (Part 3).
4.  **Screenshot 4 (Processes):** Showing the command to kill the sleep process (Part 4).
5.  **Screenshot 5 (Scripting):** Showing the content of your script (using `cat`) and the output of running the script (Part 7).

**Note:** Please name your repository `linux-data-engineering-lab` and upload this README there along with your PDF submission.
