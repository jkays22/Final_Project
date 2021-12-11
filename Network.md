# Network Forensic Analysis Report

## Time Thieves 

1. What is the domain name of the users' custom site? 
    - Frank-n-Ted.DC.frank-n-ted.com

![time1](https://user-images.githubusercontent.com/88590862/145689311-c5cf919c-7605-4d98-9488-fe5389c7b0b4.PNG)


2. What is the IP address of the Domain Controller (DC) of the AD network?
    - 10.6.12.12
3. What is the name of the malware downloaded to the 10.6.12.203 machine?
   - june11.dll

![time2](https://user-images.githubusercontent.com/88590862/145689325-78157f5a-7866-44e9-8e7d-4db40398fdcc.PNG)


4. Upload the file to [VirusTotal.com]

![malware](https://user-images.githubusercontent.com/88590862/145689341-9a886034-7b8c-4283-b7ab-9d1a5f436e76.PNG)


6. What kind of malware is this classified as?
    - Cross Site Request Forgery (CSRF) 

---

## Vulnerable Windows Machine

1. Find the following information about the infected Windows machine:
    - Host name
        - Rotterdamn-PC
    - IP address
        - 172.16.4.205
    - MAC address
        - LenovoEM_b0:63:a4 (00:59:07:b0:63:a4)
    
    ![infected1](https://user-images.githubusercontent.com/88590862/145689396-67ef7669-fa82-4de9-b60b-c3564ea4fa48.PNG)

    
2. What is the username of the Windows user whose computer is infected? 
    -  matthijs.devries

![infected2](https://user-images.githubusercontent.com/88590862/145689404-fc866447-384f-431e-b5b0-f4a6b5fe6073.PNG)


3. What are the IP addresses used in the actual infection traffic? 
    - 166.62.111.64

![infection3](https://user-images.githubusercontent.com/88590862/145689413-fea468f9-6061-4ba8-a43e-c4b4eb8bfe27.PNG)
![infection4](https://user-images.githubusercontent.com/88590862/145689414-179d2a6e-aec4-4ec7-8684-e6c6816abe5a.PNG)


---

## Illegal Downloads

1. Find the following information about the machine with IP address `10.0.0.201`:
    - MAC address
        - Msi_18:66:c8 (00:16:17:18:66:c8)
    - Windows username
        - elmer.blanco
    - OS version
        - Windows NT 10.0; Win64; x64

![Torrent1](https://user-images.githubusercontent.com/88590862/145689694-800edeb3-1015-4fdb-932b-0186702d0938.PNG)


2. Which torrent file did the user download? 
    - Betty_Boop_Rhythm_on_the_Reservation.avi.torrent

![Torrent_file](https://user-images.githubusercontent.com/88590862/145689459-e554fd2f-8665-425b-8396-b7a2a7520c75.PNG)


