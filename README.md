# nithinsai02-setup-and-use-a-firewall-windows-linux-


Objective:Configure and test basic firewall rules to allow or block traffic using UFW (Ubuntu) and Windows Firewall.

---

##  Repository Contents
- README.md — Documentation of everything done  
- setup-ufw.sh — Bash script to install & configure UFW  
- windows-firewall-steps.md — Windows GUI and PowerShell instructions  
- screenshots/ — Firewall rule screenshots (see list below)  
- test-outputs/ — Terminal or PowerShell output logs (optional)

---

 Ubuntu (UFW) — Commands Used
1) Install & Enable UFW
sudo apt update
sudo apt install -y ufw
sudo ufw enable
sudo ufw status verbose

2️) Allow SSH (Port 22)
(Important to avoid locking yourself out)

sudo ufw allow 22/tcp

3️) List Current Rules

sudo ufw status numbered

4️) Block Port 23 (Telnet)

sudo ufw deny 23/tcp

5️) Test the Block Rule
Using netcat:


nc -v -z localhost 23
Expected result: connection refused or failed.


6️)Remove the Test Block Rule
Find rule number: 


sudo ufw status numbered
Delete the rule:
sudo ufw delete <rule-number>

7️) Restore to Original State (Optional)

sudo ufw disable
 


Windows Firewall — Summary of Steps
Testing in PowerShell
1. Press **Win + R** → type `wf.msc`
2. Go to **Inbound Rules**
3. Click **New Rule…**
4. Select **Port**
5. Choose **TCP**
6. Enter port **23**
7. Action → **Block the connection**
8. Apply to: Domain, Private, Public
9. Name → `Block-Telnet-Port23`


 

 

