# Linux Doctor 
A repo to help with Linux troubles

![linux-dr](https://github.com/jasonmhead/linux-doctor/assets/6140151/94e5b442-642a-457d-ba55-c27b4aab2594)

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
