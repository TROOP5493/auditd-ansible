This project automates the installation configs, and verifaction on an Ubuntu 24.x system. Auditd is very critical for Linux security that records system level events. This project ensures consistent configuration across systems, version controlled and documented audit rules, automated provisioning using ansible pull from GitHub.

System Requirments- Ubuntu 24.04 LTS or later, Ansible3 2.14, and network access to GitHub

Repository Structure- The main playbook, an auditd role, config templates

How to use- Run ansible-pull with your GitHUub repo URL to auto configure auditd on the VM

Audit Rules- Monitor changes to /etc/passwd and entire /var/log/ directory.

                +-----------------------+
                |       GitHub Repo     |
                |  (Playbook & Rules)   |
                +-----------+-----------+
                            |
                            |  ansible-pull (HTTPS)
                            v
                +-----------------------+
                |     Ubuntu 24.x VM    |
                |  Runs ansible-pull to |
                |  install/configure    |
                |        auditd          |
                +-----------+-----------+
                            |
                            |  Applies audit rules:
                            |  - /etc/passwd changes
                            |  - /var/log/ changes
                            v
                +-----------------------+
                |        auditd         |
                |  Logs system events   |
                +-----------+-----------+
                            |
                            |  Log queries (ausearch, aureport)
                            v
                +-----------------------+
                |   Administrator User  |
                |  Verifies audit logs  |
                +-----------------------+
Verification Steps- Verify auditd by checking loaded rules and searching logs withj auditctl and ausearch

Troubleshooting tips- Common issues are bad syntax, network errors, or missing dependencies.




