# **Project Title: The 'EtlBox' Container Challenge**

**Prerequisites:**

1. **Docker Desktop** installed and running (using WSL2 backend is recommended).
2. **Git Bash** installed.
3. **GitHub Account**.

### **Phase 0: The Specific Setup (Crucial Step)**

*We need to start the Linux server and connect your Windows file system to it.*

1. Create a folder on your Windows machine (e.g., `Documents/etl_assignment`).
2. Right-click that folder and select **"Git Bash Here"**.
3. **The Magic Command:** Run this exact command to handle the Windows-to-Linux path conversion and terminal interactivity:
```bash
winpty docker run -it -v "/$(pwd)":/app ubuntu:latest

```


* **Why `winpty`?** Without this, the Linux terminal will freeze inside Git Bash.
* **Why quotes around `pwd`?** This helps Docker translate the Git Bash path path correctly to the Windows path format.


4. Once the prompt changes to `root@<random_id>:/#`, you are inside the Linux container.
5. Type `cd /app` and hit enter. You are now inside your mounted folder.

---

### **Phase 1: Environment Provisioning**

*The container is a blank slate. You need to build your toolbox.*

1. **Update & Install:**
* Run `apt-get update`.
* Install the missing essentials: `nano` (text editor) and `procps` (for process monitoring).
* *Command:* `apt-get install -y nano procps`




2. **Directory Structure:**
* Inside `/app`, create: `raw_data`, `processed_data`, `scripts`.


3. **Permissions:**
* Create `/app/scripts/secret_config.conf`.
* **Task:** Use `chmod` to set permissions to `600`.



---

### **Phase 2: The "CRLF" Trap (Scripting)**

*Use the tools inside the container to avoid Windows formatting issues.*

**⚠️ VERY IMPORTANT WARNING FOR WINDOWS USERS:**
If you write your shell scripts using Notepad or VS Code on Windows, they will save with **Windows Line Endings (CRLF)**. When you try to run these in Linux, they will fail with confusing errors like `^M: bad interpreter`.

**The Requirement:** You must write your scripts **using `nano` inside the container terminal** to ensure they are saved in Linux format (LF).

1. **Write `ingest.sh`:**
* Type `nano scripts/ingest.sh`.
* Write a script that:
* Accepts a filename argument (e.g., `$1`).
* Checks if `raw_data` exists.
* Creates a file inside `raw_data`.


* Save and exit (`Ctrl+X`, then `Y`, then `Enter`).
* Make it executable: `chmod +x scripts/ingest.sh`.


2. **Write `dashboard.sh`:**
* Create this script using `nano`.
* It should run an infinite loop (`while true`) printing a message every few seconds.
* Make it executable.



---

### **Phase 3: Dependencies & Variables**

1. **Environment Variables:**
* Set `BASE_ETL_PATH=/app`.
* Append this to the bash configuration file: `echo 'export BASE_ETL_PATH=/app' >> ~/.bashrc`.
* Refresh the source: `source ~/.bashrc`.


2. **Package Management:**
* Install `jq` and `htop` (or `top` if htop fails in minimal containers).



---

### **Phase 4: Process Management**

1. Run the dashboard script in the background: `./scripts/dashboard.sh &`
2. Use `ps aux` to find its Process ID (PID).
3. **Task:** Kill the process using the `kill` command.
4. **Log Proof:** Save the output of your process list to a file: `ps aux > process_log.txt`.

---

## **Submission Instructions (GitHub)**

Because you used the Volume Mount (`-v`), all the files you created inside the container (using `nano`) are actually sitting in your Windows folder right now!

1. Open VS Code or File Explorer in your Windows `etl_assignment` folder. You will see the scripts there.
2. **Verify Line Endings:** In VS Code, look at the bottom right corner of the window when you open `ingest.sh`. It should say **"LF"**, not "CRLF".
3. **Push to GitHub:**
* Initialize the repo: `git init`
* Add files: `git add .`
* Commit: `git commit -m "feat: initial etl setup"`
* Push to your new public repository.

