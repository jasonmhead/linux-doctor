# Linux Doctor 
A repo to help with Linux troubles

![linux-dr](https://github.com/jasonmhead/linux-doctor/assets/6140151/94e5b442-642a-457d-ba55-c27b4aab2594)

---
## General Problem Solving Philosophy
There can be many ways to do a thing, so if you keep hitting walls when trying a solution, it could be time to head another direction.

For example, for file sharing / general data transfer:
- cd to the file dir and serve your file with a Python simple server on port 80 `sudo python3 -m http.server 80`
  -- port 80 may need opened
- you could use `wget [file url]` to retrieve a file
- you could use ssh to securely transfer a file `scp /path/to/local/file username@remote_host:/path/to/remote/directory`
- (use sftp to transfer files)[https://www.techrepublic.com/article/how-to-set-up-an-sftp-server-on-linux/]
  -- make sure sftp is running and serve files 
  -- `sftp username@remote_server`
  -- download a file `get remote_file_path`
  -- upload a file: `put local_file_path`
  -- download a directory: `get -r remote_directory_path`
  -- upload a directory: `put -r local_directory_path`

So for any given problem, if one takes too long to solve then a work-around could be in order, evaluating complexity of potentual solutions.

---
## Linux inside Windows

Running Linux on "bare metal" without a inbetween will give you the best resource usage and advantages, but there is a way other than using a VM to run Linux on windows **WSL**

_"WSL (Windows Subsystem for Linux) is a compatibility layer in Windows 10 and later that allows you to run a Linux distribution alongside your Windows operating system._

_WSL works by translating Linux system calls into Windows system calls, providing a seamless integration of Linux and Windows functionality for developers and power users."_

WSL Docs (https://learn.microsoft.com/en-us/windows/wsl/install)

WSL Ubuntu (https://ubuntu.com/wsl)

---

## Getting in system help
- use `man your-command` to get the manual
- try putting --help on the end of your command, the man page should list if there is a help option (or switch)

## The Kitchen Sink - Cheatsheets and Broadly Focused Resources
![linux-kitchen-sink](https://github.com/jasonmhead/linux-doctor/assets/6140151/f5b9873a-7e90-45d7-b96b-3077c60abe15)

- Comprehensive Linux Cheatsheet [gto76/linux-cheatsheet](https://github.com/gto76/linux-cheatsheet) 
- Ultimate list of Linux bash commands, cheatsheet and resources https://github.com/trinib/Linux-Bash-Commands 
- List of Linux commands https://github.com/sudheerj/Linux-cheat-sheet 
- Handy commands for Linux https://github.com/crhuber/linux-cheatsheet 

## More focused problem solving
![Linux-scalpel](https://github.com/jasonmhead/linux-doctor/assets/6140151/7388380d-08a5-48cc-8a97-bc3738252a90)

### Permissions - permissions getting in your way? `sudo` is your friend for appending to commands to do everything while maintaining system security, but here is a way to make it easier to not have to type in the password every time.
#### add your user to the  sudoers file to give your user root permissions - be aware that a user with this level of permissions that is compromised is a extra security risk
- in the terminal window type `whoami` to get your user name
- next `sudo visudo` to safely access the sudoers file
- add `yourusername ALL=(ALL) NOPASSWD: ALL` to the file - replacing yourusername with what you got from `whoami`
- save the file
- close the terminal window, open a new one and `sudo ls` to test

### File locked? - here's some help, but becareful what you stop to not loose data or cause an issue
 locked file in Linux and then freeing it:

Find PID of Locking Process:
- Use `lsof | grep [filename]` to identify the process and its PID.

Terminate Process:
- Standard kill: `kill [PID]`
- If not effective, `force kill: kill -9 [PID]`

Check if File is Unlocked:
Recheck with `lsof`.

### Versioning and Dependancy issues
- for Python use Conda [https://docs.conda.io/projects/conda/en/stable/user-guide/install/download.html#anaconda-or-miniconda] 
or venv (python focused - cannot manage non-Python packages.) [https://docs.python.org/3/library/venv.html]
- if using apt, always update apt before doing a program install or update `sudo apt update`
- some setups may have a Docker container, but that has it's own setup so perhaps best to avoid unless as a last resort
- alternative to using Docker (Podman)[https://podman.io/]
