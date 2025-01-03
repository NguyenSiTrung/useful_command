
# Useful Linux Terminal Commands for AI Engineers in NLP and NMT

This document summarizes useful Linux terminal commands for an AI engineer working in NLP and NMT.

## **I. File & Directory Navigation & Management**

These are fundamental for navigating your project, handling datasets, and managing model files.

| Command                  | Description                                                                                                                                 | Example                                      |
| :----------------------- | :------------------------------------------------------------------------------------------------------------------------------------------ | :------------------------------------------- |
| `pwd`                  | Print Working Directory - shows your current location in the file system.                                                                      | `pwd`                                       |
| `ls`                   | List directory contents.                                                                                                                      | `ls`, `ls -l`, `ls -lh`, `ls -la`      |
| `cd`                   | Change directory.                                                                                                                             | `cd my_project`, `cd ..`, `cd /`          |
| `mkdir`                | Make directory - creates a new directory.                                                                                                     | `mkdir data`, `mkdir models`                 |
| `rm`                   | Remove files or directories (use with caution!). `-r` for recursive (directories), `-f` for force (no warnings).                               | `rm old_file.txt`, `rm -rf temp_dir`    |
| `cp`                   | Copy files or directories. `-r` for recursive (directories).                                                                                   | `cp source.txt dest.txt`, `cp -r data backup` |
| `mv`                   | Move or rename files or directories.                                                                                                        | `mv old_name.txt new_name.txt`, `mv file.txt my_dir/` |
| `touch`                | Create an empty file or update the timestamp of an existing one.                                                                              | `touch new_file.txt`                       |
| `find`                 | Search for files and directories based on various criteria (name, type, size, etc.).                                                            | `find . -name "*.txt"`                    |
| `locate`               | Quickly find files by name (uses a database, which needs to be updated, usually with `sudo updatedb`).                                          | `locate my_data.csv`                       |
| `du`                   | Display disk usage. `-h` for human-readable output. `-s` for a summary of a directory.                                                             | `du -sh my_dir`                          |
| `df`                   | Display disk free space. `-h` for human-readable output.                                                                                       | `df -h`                                     |
| `tar`                 | Create or extract compressed archives (`.tar`, `.tar.gz`, `.tgz`).                                                                            | `tar -czvf archive.tar.gz my_dir`, `tar -xzvf archive.tar.gz` |
| `gzip`, `gunzip`       | Compress or decompress a single file using gzip compression (`.gz`).                                                                          | `gzip my_file.txt`, `gunzip my_file.txt.gz` |
| `zip`, `unzip`       | Compress or decompress files using zip compression (`.zip`).                                                                                    | `zip my_archive.zip file1.txt file2.txt`, `unzip my_archive.zip` |

## **II. Text Processing & Data Wrangling**

Essential for preparing and analyzing text data, crucial in NLP/NMT.

| Command                  | Description                                                                                                       | Example                                                                                |
| :----------------------- | :---------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------- |
| `cat`                  | Concatenate and display file contents.                                                                              | `cat file1.txt`, `cat file1.txt file2.txt > combined.txt`                      |
| `head`                 | Display the first few lines of a file (default 10). `-n` to specify the number of lines.                        | `head -n 5 data.txt`                                                              |
| `tail`                 | Display the last few lines of a file (default 10). `-n` to specify the number of lines, `-f` to follow a file.   | `tail -n 20 log.txt`, `tail -f log.txt`                                         |
| `less`                 | View file contents one screen at a time (useful for large files).                                                  | `less large_file.txt`                                                             |
| `grep`                 | Search for patterns in files. `-i` for case-insensitive, `-r` for recursive, `-n` for line numbers, `-v` for invert match. | `grep "error" log.txt`, `grep -i "word" data.txt`, `grep -r "pattern" my_dir`   |
| `sed`                  | Stream editor - perform text transformations. Used for substitutions, deletions, insertions.                        | `sed 's/old_word/new_word/g' file.txt`                                            |
| `awk`                  | Powerful text processing language. Used for pattern scanning and processing, data extraction, and reporting.      | `awk '{print $1}' file.txt` (print the first column), `awk -F',' '{print $2}' data.csv` |
| `wc`                   | Word, line, character, and byte count. `-l` for lines, `-w` for words, `-c` for bytes, `-m` for characters.        | `wc -l data.txt`                                                                   |
| `sort`                 | Sort lines of text. `-n` for numerical sort, `-r` for reverse, `-k` to specify a key column.                       | `sort data.txt`, `sort -n numbers.txt`, `sort -k2 file.txt`                        |
| `uniq`                 | Filter out repeated adjacent lines. `-c` to count occurrences. Often used with `sort`.                               | `sort data.txt \| uniq`, `sort data.txt \| uniq -c`                                  |
| `cut`                  | Extract sections from each line of a file. `-f` to select fields, `-d` to specify delimiter.                    | `cut -f 1,3 -d ',' data.csv`                                                        |
| `paste`                | Merge lines of files side-by-side. `-d` to specify delimiter.                                                     | `paste file1.txt file2.txt`                                                         |
| `tr`                   | Translate or delete characters.                                                                                    | `tr 'a-z' 'A-Z' < file.txt` (convert to uppercase)                               |

## **III. Process Management**

For monitoring and managing training processes, especially long-running deep learning jobs.

| Command                  | Description                                                                                                        | Example                                            |
| :----------------------- | :----------------------------------------------------------------------------------------------------------------- | :------------------------------------------------- |
| `ps`                   | Display currently running processes. `ps aux` or `ps -ef` for a detailed view.                                       | `ps aux`                                           |
| `top`, `htop`          | Display and update sorted information about processes and system resource usage (like CPU, memory). `htop` is more interactive. | `top`, `htop`                                    |
| `kill`                 | Send a signal to a process (usually to terminate it). Use `ps` or `top` to find the process ID (PID). Default signal is `SIGTERM` (15), `SIGKILL` (9) is forceful. | `kill 1234` (terminate PID 1234), `kill -9 1234` |
| `killall`             | Kill processes by name.                                                                                             | `killall python`                                   |
| `nohup`                | Run a command immune to hangups, with output to a non-tty. Useful for running long jobs in the background.       | `nohup python train.py &`                         |
| `&`                    | Run a command in the background.                                                                                   | `python train.py &`                               |
| `jobs`                 | List background jobs.                                                                                              | `jobs`                                             |
| `fg`                   | Bring a background job to the foreground.                                                                           | `fg %1` (bring job number 1 to the foreground)   |
| `bg`                   | Put a suspended job into the background.                                                                            | `bg %1`                                            |
| `Ctrl+Z`               | Suspend a running process (pause it).                                                                             | (Press `Ctrl+Z` while a process is running)        |

## **IV. System & Hardware Information**

Useful for checking available resources (GPU, CPU, memory) before and during training.

| Command                  | Description                                                                                                                               | Example                                         |
| :----------------------- | :---------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------- |
| `nvidia-smi`           | NVIDIA System Management Interface - provides monitoring and management capabilities for NVIDIA GPUs.                                        | `nvidia-smi`                                    |
| `lscpu`                | Display information about the CPU architecture.                                                                                             | `lscpu`                                         |
| `free`                 | Display amount of free and used memory in the system. `-h` for human-readable output.                                                         | `free -h`                                        |
| `uname`                | Print system information. `-a` for all information.                                                                                          | `uname -a`                                      |
| `uptime`               | Tell how long the system has been running, load averages.                                                                                     | `uptime`                                        |

## **V. Networking**

These are helpful for transferring data to/from remote servers, downloading datasets, or interacting with remote machines.

| Command                  | Description                                                                                                                          | Example                                                    |
| :----------------------- | :----------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------- |
| `ping`                 | Test network connectivity to a host.                                                                                                 | `ping google.com`                                       |
| `ssh`                  | Secure Shell - connect to a remote server securely.                                                                                    | `ssh user@remote_server`                               |
| `scp`                  | Secure Copy - copy files between hosts on a network securely (uses SSH).                                                               | `scp file.txt user@remote_server:/path/to/destination`  |
| `rsync`                | Fast, versatile, remote (and local) file-copying tool. Excellent for syncing directories and backups, often preferred over `scp`.        | `rsync -avz source_dir/ user@remote_server:/dest_dir/` |
| `wget`                 | Retrieve files from the web (HTTP, HTTPS, FTP).                                                                                       | `wget https://example.com/dataset.zip`                  |
| `curl`                 | Transfer data with URLs. More powerful than `wget`, can interact with APIs, etc.                                                         | `curl https://example.com/api/data`                      |
| `ifconfig` / `ip`      | Display or configure network interfaces. `ifconfig` is older, `ip` is more modern and feature-rich.                                  | `ifconfig`, `ip addr`                                  |

## **VI. Package Management**

Essential for installing and managing the software libraries you need (e.g., PyTorch, TensorFlow, Transformers).

*   **`apt` (Debian/Ubuntu):**
    *   `sudo apt update`: Update the list of available packages.
    *   `sudo apt upgrade`: Upgrade installed packages.
    *   `sudo apt install <package_name>`: Install a package.
    *   `sudo apt remove <package_name>`: Remove a package.
    *   `sudo apt search <keyword>`: Search for packages.
*   **`yum` (Red Hat/Fedora/CentOS):**
    *   `sudo yum update`: Update the list of available packages and upgrade installed packages.
    *   `sudo yum install <package_name>`: Install a package.
    *   `sudo yum remove <package_name>`: Remove a package.
    *   `sudo yum search <keyword>`: Search for packages.
*   **`pip` (Python Package Installer):**
    *   `pip install <package_name>`: Install a Python package.
    *   `pip install -U <package_name>`: Upgrade a Python package.
    *   `pip uninstall <package_name>`: Uninstall a Python package.
    *   `pip list`: List installed Python packages.
    *   `pip show <package_name>`: Show information about an installed package.
    *   `pip freeze > requirements.txt`: Create a requirements file for your project.
    *   `pip install -r requirements.txt`: Install packages from a requirements file.
*   **`conda` (Anaconda/Miniconda):**
    *   `conda create -n <env_name> python=<version>`: Create a new environment.
    *   `conda activate <env_name>`: Activate an environment.
    *   `conda install <package_name>`: Install a package in the current environment.
    *   `conda update <package_name>`: Update a package.
    *   `conda remove <package_name>`: Remove a package.
    *   `conda list`: List installed packages in the current environment.
    *   `conda env list`: List all available environments.
    *   `conda env export > environment.yml`: Export an environment to a YAML file.
    *   `conda env create -f environment.yml`: Create an environment from a YAML file.

## **VII. Other Useful Commands**

| Command                  | Description                                                                                     | Example                                                      |
| :----------------------- | :---------------------------------------------------------------------------------------------- | :----------------------------------------------------------- |
| `history`              | Display command history. `!<number>` to execute a command from history.                           | `history`, `!123`                                           |
| `man`                  | Display the manual page for a command.                                                           | `man ls`                                                     |
| `which`                | Show the full path of a command.                                                                | `which python`                                               |
| `alias`                | Create a shortcut for a command.                                                                 | `alias ll='ls -lh'`                                         |
| `date`                 | Display or set the system date and time.                                                          | `date`                                                       |
| `cal`                  | Display a calendar.                                                                              | `cal`                                                        |
| `clear` or `Ctrl+L`    | Clear the terminal screen.                                                                      | `clear`                                                      |
| `exit`                 | Exit the current shell session.                                                                  | `exit`                                                       |
| `sudo`                 | Execute a command with superuser (root) privileges.                                              | `sudo apt update`                                            |
| `chmod`                | Change file permissions.                                                                         | `chmod +x script.sh` (make a script executable)              |
| `chown`                | Change file owner and group.                                                                     | `sudo chown user:group file.txt`                             |
| `ln`                   | Create links (hard links or symbolic links). `-s` for symbolic link.                           | `ln -s target_file link_name` (create a symbolic link)     |
| `diff`                 | Compare files line by line. `-u` for unified diff (easier to read), `-y` for side-by-side diff. | `diff file1.txt file2.txt`, `diff -u old.txt new.txt`       |
| `comm`                 | Compare two sorted files line by line.                                                            | `comm file1.txt file2.txt`                                   |
| `time`                 | Measure the execution time of a command.                                                        | `time python my_script.py`                                  |
| `screen`, `tmux`       | Terminal multiplexers - allow you to manage multiple terminal sessions from a single window.   | `screen`, `tmux` (start a new session)                      |
| `watch`                | Execute a program periodically, showing output fullscreen. Useful for monitoring.               | `watch -n 1 nvidia-smi` (monitor GPU usage every second)   |

## **VIII. Advanced Text Processing & Data Wrangling**

These commands help you perform more complex operations on text files, preparing them for model training or analysis.

Command                                      | Description                                                                                                                                                                                                                    | Example                                                                                                                                                                                                     |
| :------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `sed` (more advanced usage)                | **Substitute with capture groups:** `sed 's/\(pattern1\)\(pattern2\)/\2\1/g' file.txt` (swap the order of captured patterns)<br>**In-place editing:** `sed -i 's/old/new/g' file.txt` (modify the file directly) <br> **Multiple operations:**  `sed -e 's/this/that/g' -e '/pattern/d' file.txt` (chain multiple sed commands).<br> **Range-based operations:** `sed '10,20s/old/new/g' file.txt` (substitute only on lines 10-20) | `sed 's/\([A-Z]\)\([a-z]\)/\2\1/g' names.txt` (convert CamelCase to camelCase), `sed -i 's/typo/correction/g' data.txt`,  `sed -e 's/  / /g' -e '/^$/d' text.txt` (remove extra spaces and empty lines) |
| `awk` (more advanced usage)               | **Conditional logic:** `awk '{if ($1 > 10) print $0}' file.txt` (print lines where the first field is greater than 10) <br> **Built-in functions:** `awk '{print toupper($0)}' file.txt` (convert to uppercase) <br> **Arrays:** `awk '{count[$1]++} END {for (word in count) print word, count[word]}' file.txt` (count word frequencies) | `awk '{if ($3 == "error") print "Error on line " NR ": " $0}' log.txt`, `awk '{print length($0)}' file.txt` (print the length of each line), `awk '{lines[$0]++} END {for (l in lines) print l}' file.txt` (remove duplicate lines)             |
| `join`                                     | Join lines of two files based on a common field. Files should typically be sorted on the join field.                                                                                                                       | `join -1 1 -2 2 file1.txt file2.txt` (join on the first field of file1 and the second field of file2)                                                                                                   |
| `split`                                    | Split a file into multiple smaller files. Useful for dividing large datasets.                                                                                                                                              | `split -l 1000 data.txt data_part_` (split `data.txt` into files with 1000 lines each, named `data_part_aa`, `data_part_ab`, etc.)                                                                 |
| `csplit`                                   | Split a file into multiple files based on context lines or patterns.                                                                                                                                                     | `csplit data.txt /CHAPTER/ {*}` (split `data.txt` into files at each line containing "CHAPTER")                                                                                                        |
| `shuf`                                     | Randomize the order of lines in a file. Useful for shuffling datasets before training.                                                                                                                                 | `shuf data.txt > shuffled_data.txt`                                                                                                                                                                 |
| `nl`                                       | Number lines of a file. Useful for adding line numbers for easier reference.                                                                                                                                               | `nl data.txt > numbered_data.txt`                                                                                                                                                                   |
| `pr`                                       | Paginate or columnate files for printing. It can also be used to add headers and footers to a file, which can be useful for preparing text data for certain types of analysis or processing.                            | `pr -t -n data.txt`                                                                                                                                                                                 |
| `fmt`                                       | Reformat paragraph text to fit within a specified width.                                                                                                                                                                   | `fmt -w 60 long_lines.txt` (wrap lines to a maximum width of 60 characters)                                                                                                                        |
| `expand`, `unexpand`                        | `expand` converts tabs to spaces, while `unexpand` does the opposite. Useful for standardizing whitespace.                                                                                                                       | `expand -t 4 file.txt` (convert tabs to 4 spaces), `unexpand -a file.txt` (convert spaces to tabs)                                                                                                     |
| `paste` (parallel processing example)    | Combine corresponding lines of two files, which is essential for creating parallel corpora. For example, to create a tab-separated parallel corpus from two files (`source.txt` and `target.txt`):                            | `paste source.txt target.txt > parallel_corpus.tsv`  
