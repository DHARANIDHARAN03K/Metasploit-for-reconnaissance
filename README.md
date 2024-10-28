# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
Find out the ip address of the attackers system

## OUTPUT:

![Screenshot 2024-10-28 153752](https://github.com/user-attachments/assets/b71c63ba-c362-4767-8443-c7f383d3f539)

Invoke msfconsole:

![Screenshot 2024-10-28 155854](https://github.com/user-attachments/assets/62e3d8e5-ab1e-4881-9588-49203e54feeb)
![Screenshot 2024-10-28 155905](https://github.com/user-attachments/assets/9bb974f5-c698-4206-991b-4d4ca90fe7e5)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![Screenshot 2024-10-28 151001](https://github.com/user-attachments/assets/69f828c0-73ba-41de-a47f-750306038a0a)

## Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:
![Screenshot 2024-10-28 151826](https://github.com/user-attachments/assets/efac0f4f-5bbe-4c9d-9490-13cfb74c7b59)

step4:

use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24

## OUTPUT:

![image](https://github.com/user-attachments/assets/4d1baf54-3b9d-4e54-836f-7dfeb5571259)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:
![Screenshot 2024-10-28 155912](https://github.com/user-attachments/assets/09794528-aec8-4d3f-9b9c-963f042029ff)

Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,

## OUTPUT:

![Screenshot 2024-10-28 152219](https://github.com/user-attachments/assets/c8bf022f-ad0b-45cd-ab64-0b1d92b65eba)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION

Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![image](https://github.com/user-attachments/assets/2613dfc2-2456-4d64-92da-2562260f6bcc)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql

![Screenshot 2024-10-28 152406](https://github.com/user-attachments/assets/1d5f172e-7bfd-49dc-8bfd-8d236d9f33b4)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version

![Screenshot 2024-10-28 152456](https://github.com/user-attachments/assets/32851115-c50c-4adf-b7e5-87e784ec59a9)

Use the set rhosts command to set the parameter and run the module, as follows:

![Screenshot 2024-10-28 152556](https://github.com/user-attachments/assets/5695003b-de06-4dfd-892d-ae11844422e7)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![Screenshot 2024-10-28 152740](https://github.com/user-attachments/assets/fc8b5b61-858e-462c-b2b3-bc320ab514e9)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true

![Screenshot 2024-10-28 153252](https://github.com/user-attachments/assets/6409547a-a51e-440b-a58d-5546860245a3)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
