# Penetration-Testing-Project

<h1>Project Overview</h1>  

- Pre-test
- Testing (Mapping and Scanning) the target environment and conduct a vulnerability scan
- Testing (Exploitation) by gaining access through a vulnerability identified by the vulnerability scan
- Analysis and Reporting

Purpose of this project:  

- Build and deploy an attack OS                       
- Configure and deploy a victim host
- Conduct a vulnerability scan
- Research a hardware or software vulnerability
- Discuss how the vulnerability can be exploited
- Exploit the vulnerability
- Evaluate the risk posed by the vulnerability
- Provide compensating control to mitigate the vulnerability


<h2> Pre-Test </h2>

For this project, a local lab was setup which gave me access to the environment as needed. Oracle VM Virtual box was utilized to deploy Kali Linux as the host environment and utilized Metasploitable 2 as the vulnerable target. 

![image](https://github.com/user-attachments/assets/d56aef15-cf7d-43cf-a0d8-5cbe086e3458)

<h2> Testing </h2>

IP address of the local host and the vulnerable target was idenified using the ifconfig command. NMap identified the target system through network discovery and confirmed using netdiscover. NMap discovered ports 21/tcp service ftp, 22/tcp service ssh, 23/tcp service telnet, 25/tcp service smtp, 53/tcp service domain, 80/tcp service http. Nessus obtained a list of vulnerabilities that included 5 critical vulnerabilities.  

![image](https://github.com/user-attachments/assets/e7ffca1f-58e5-48de-a9f1-821ef944f5d8)
![image](https://github.com/user-attachments/assets/801c7413-3d59-4e00-acd0-a8557ee47ae5)
![image](https://github.com/user-attachments/assets/c4807bf0-f936-472b-8b4e-794ceb75b7cc)
![image](https://github.com/user-attachments/assets/98df7b9c-6214-40bc-87d9-3abbe5f75d7d)
![image](https://github.com/user-attachments/assets/b3b11817-9bf1-4988-bed9-9bf784bc700c)

<h3> Exploitation </h3>

RHOST was set to the target IP address and the RPORT was set as port 21 which is the vulnerable FTP server port. The target was then exploited and connected to the target machine. 

![image](https://github.com/user-attachments/assets/23546f0a-ccda-4157-901c-c2ea6d0c3d57)
![image](https://github.com/user-attachments/assets/8e2957a1-4e37-46a3-8eb9-cb8d613e1b8f)
![image](https://github.com/user-attachments/assets/44dbc6bc-74ee-4917-91d4-45a2a99379c4)

<h4> Vulnerability Research </h4>

VSFTPD is the Very Secure FTP Daemon which Nessus defined as a backdoor vulnerability in which an unauthorized user has the ability to gain access and implant backdoor software to re-enter whenever they like. VSFTPD 2.3.4 has a CVSS v2 score of 10 and CVSS v3 score of 9.8. A critical concern with this vulnerability is the possibility of remote code execution which means the attacker could run a malicious code on the server. 

Testing Details

id command - shows root

![image](https://github.com/user-attachments/assets/aa75ca05-416d-40d2-af96-9cbc812dc2e3)

hostname command

![image](https://github.com/user-attachments/assets/e19e3b8d-54f9-43c5-a013-8de244b21db2)

whoami command

![image](https://github.com/user-attachments/assets/490ec641-2849-48a8-926b-cdf9ef7e0058)

ifConfig command

![image](https://github.com/user-attachments/assets/ff30c94c-3082-4cf8-9d2f-72fcf3c7d23a)

<h5> Risk Assessment </h5>

If an attacker were to be successful in using VSFTPD 2.3.4 backdoor attack, it could lead to a compromise of the system which the threat agent would be able to execute remote code execution leading to a complete system compromise. The attacker would have complete access to steal sensitive data, or corrupt information to a government or organization. 

<h6> Mitigation </h6>

A thorough review and testing of a system's security measures can help identify any potentially malicious activities which can lead to the detection of backdoor attacks already in progress. Hardening of your system will help mitigate against backdoor attacks as well as removing unused or unnecessary applications, software updates, turning off unnecessary features, and implementing strong access controls. Utilization of an IDS would help indicate suspicious activity which would help shorten the time in which a threat agent would have access. 
