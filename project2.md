[Back to Portfolio](./)

Project 2 Ubuntu CIS Benchmark Compliance Checker
===============

-   **Class:** CSCI 301
-   **Grade:** 100 (A)
-   **Language(s):** BASH (scripting language)
-   **Source Code Repository:** [features/mastering-markdown](https://guides.github.com/features/mastering-markdown/)  
    (Please [email me](mailto:bjcooper2@csustudent.net?subject=GitHub%20Access) to request access.)

## Project description

This project is a **Bash-based compliance checker** that automates the verification of critical security configurations on **Ubuntu Linux systems**, following five selected controls from the **CIS Ubuntu Benchmark**. The script evaluates whether key security rules are properly configured and outputs clear results showing if the system is compliant or not compliant. This helps system administrators quickly identify and remediate vulnerabilities without manually reviewing multiple configuration files.

**The script checks for:**

1. **nodev option on /tmp**  
   Ensures that no executable files can run from /tmp, reducing exposure to malicious temporary files.

2. **Permissions on /etc/passwd**  
   Confirms that the file permissions are correctly set to 644, protecting user account information from unauthorized modification.

3. **Password expiration policy**  
   Checks that the password maximum age (PASS_MAX_DAYS) in /etc/login.defs is **365 days or less**, enforcing regular password changes.

4. **SSH root login restriction**  
   Verifies that direct SSH root login is disabled (PermitRootLogin no) to minimize remote access risks.

5. **Firewall (UFW) activation**  
   Validates that the **UFW** firewall is active and monitoring network traffic.

The project demonstrates how automation and scripting can be used to ensure consistent application of security standards across systems, translating the **CIS Ubuntu Benchmark** into practical enforcement.  
It was developed and tested on an Ubuntu virtual machine using standard Linux utilities such as grep, awk, stat, and  ufw.

## How to Run the Program

** Prerequistes**

- Operating System: Ubuntu or a Debian-based Linux distribution  
- Shell: Bash  
- Tools required: grep, awk, tat, ufw, and mount must be available on the system

**Execution Steps**

1. Download or copy the script to your system as compliance_checker.sh
2. Give the script execute permission:
   
```bash
chmod +x compliance_checker.sh
```
3. Run the script:
```bash
./compiance_checker.sh
```
4. The script will check each rule sequentially and output the compliance status directly in the terminal ( Example Output below)

    1. Checking if nodev is set on /tmp:
       Compliant

    2. Checking permissions on /etc/passwd:
       Compliant

    3. Checking password max age <= 365 days:
       Not compliant, current value: 99999

    4. Checking SSH root login is disabled:
       Compliant

    5. Checking if UFW firewall is enabled:
       Compliant

  Each section provides a straightforward compliance result, making it suitable for both manual audits and automated monitoring workflows. 
   
If the programming language does not require compilation, the update the heading to be “How to run the program.” If your application is deployed on a remote service, including instructions on how to deploy it.

**Program Functionality**(How it works):
   
   User Tasks:
    - Simply execute the script, no user input is required.
    - Review the compliance results in the terminal output.
   
   Program Functionality:
    - Uses Linux command-line tools to query configuration files and system states.
    - Compares the results against five CIS Ubuntu Benchmark rules.
    - Prints “Compliant” or “Not compliant” messages for each rule.
    - Highlights any noncompliance for quick remediation.

  **How it Works**:

| **Rule**                  | **Command(s) Used**                               | **Purpose**                                             |
| ------------------------- | ------------------------------------------------- | ------------------------------------------------------- |
| /tmp nodev                |  mount,   grep                                    | Verifies that  /tmp  is mounted with the  nodev  option |
| /etc/passwd permissions   |  stat -c %a /etc/passwd`                          | Checks that permissions are set to  644                 |
| Password age policy       |  grep  and  awk  on  /etc/login.defs              | Reads and validates  PASS_MAX_DAYS  ≤ 365               |
| SSH root login            |  grep '^PermitRootLogin no' /etc/ssh/sshd_config` | Ensures root login via SSH is disabled                  |
| UFW firewall status       |  ufw status`                                      | Checks whether the firewall is active                   |


Each rule is wrapped in simple if/else logic to produce clear, actionable output.
The modular structure also allows future expansion—for example, adding checks for password complexity or audit logging.
    
## UI Design

- Lightweight & native: Uses only built-in Linux commands.
- Readable output: Prints simple compliance results for each control.
- Extensible: Additional checks can easily be added for other CIS Benchmark rules.

Lorem ipsum dolor sit amet (see Fig 1), consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat (see Fig 2). Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum (see Fig 3).

![screenshot](images/dummy_thumbnail.jpg)  
Fig 1. The launch screen

![screenshot](images/dummy_thumbnail.jpg)  
Fig 2. Example output after input is processed.

![screenshot](images/dummy_thumbnail.jpg)  
Fig 3. Feedback when an error occurs.

## 3. Additional Considerations

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. 

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

[Back to Portfolio](./)
