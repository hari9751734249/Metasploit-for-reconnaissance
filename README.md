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
<img width="454" height="319" alt="Screenshot 2026-11-26 123230" src="https://github.com/user-attachments/assets/ddae29b4-d0f3-41af-a78a-95c0263aa6cb" />



Invoke msfconsole:
## OUTPUT:
<img width="424" height="362" alt="Screenshot 2026-11-26 123300" src="https://github.com/user-attachments/assets/9eb62c4f-cc20-4e57-b26a-c14b8a5eec1c" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="458" height="367" alt="Screenshot 2026-11-26 123419" src="https://github.com/user-attachments/assets/691325e0-1d00-42b1-802c-d7e303b846e2" />


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="619" height="539" alt="Screenshot 2026-11-27 095256" src="https://github.com/user-attachments/assets/e3c002b2-73f9-4a04-9a1e-73a6a5c8b7bf" />




Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="551" height="457" alt="image" src="https://github.com/user-attachments/assets/91279112-1172-41fd-895c-d21061597127" />




Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="849" height="486" alt="image" src="https://github.com/user-attachments/assets/17dbf253-2b7e-4f89-befc-1be4d2d31c1d" />




The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:
<img width="617" height="485" alt="image" src="https://github.com/user-attachments/assets/bce0b3bb-603b-4fd8-b1a6-34f9ff79eb74" />





## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="1061" height="230" alt="image" src="https://github.com/user-attachments/assets/e761c93c-f766-4403-b1c5-6f0d2b35b91f" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="1675" height="681" alt="image" src="https://github.com/user-attachments/assets/621e0113-70ed-47a2-8ff3-55a452a876c8" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="1447" height="399" alt="image" src="https://github.com/user-attachments/assets/f0fa5752-b56f-4857-afe1-150abb4e0eb6" />




Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
<img width="947" height="245" alt="image" src="https://github.com/user-attachments/assets/9e8236c8-6da3-4d26-a919-e8422f58e513" />



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:
<img width="1659" height="834" alt="image" src="https://github.com/user-attachments/assets/b91022ae-d191-42a4-acfe-adc18034eee7" />




set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img width="1668" height="811" alt="image" src="https://github.com/user-attachments/assets/e95c2ea0-1d59-42b4-848f-85740b71a83f" />






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
