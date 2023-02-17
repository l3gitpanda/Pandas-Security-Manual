# Users and groups:
### Tools:
- **Microsoft Management Console** #mmc - can be used for most windows admin tools  
	- snap ins: file>add snap ins
	- win + r mmc
- **Local Security Policy** #lsp - windows policy changing and implementation
- **Process Explorer** #procexp - more detailed task manager 
	- https://download.sysinternals.com/files/ProcessExplorer.zip
- **Revo Uninstaller** #revo - powerful uninstaller used for logging and removing traces
	- https://download.revouninstaller.com/download/RevoUninstaller_Portable.zip
- **Network Miner** - (not needed mostly for just network logging see #netstat for other methods)
	- https://www.netresec.com/?download=NetworkMiner
- Windows Services #winser - for managing windows services
- Malwarebytes #malbyte - free antivirus
- Bitdefender #bitdef - free antivirus

### Update Passwords: #mmc > local users and groups
- Max enforce password history
- Min password age: 15 days
- max password age: 45
- DISABLE REVERSIBLE ENCRYPTIONNNNNNN

### Lower Attack Surface #mmc: 

- Manage User Roles 
	- #mmc > computer management > local users and groups > Users >  {User} properties > Member of
		- Everyone should be either admin or user **nothing else unless told otherwise**

- Secure User Properties
	- #mmc > computer management > local users and groups 

- Remove unnecessary accounts  
	- #mmc > computer management > local users and groups > users
		- let user change passwords
		- let passwords expire
		- disable before delete (just in case)

- Secure Default Accounts (User/Admin Accounts)
	- #mmc > computer management > local users and groups > users
		- change/set passwords
		- change usernames
		- configure properties
		- disable

- Account lockout threshold
	- #lsp > Account Policies > Account Lockout Policy > Account lockout threshold 
		- 30 5 30?
		- maybe if we set strong passwords it would waste red team time if they try to brute force without lockout threshold?? just a weird thought lol\


# Application Security

- Remove unneeded software 
	- use #revo to uninstall
- Update Windows
- Update applications 
	- winget upgrade --all
- Make sure important services are on 
- Remove/shutdown unnecessary services
- Disable Telnet
	- replace with ssh if needed
- Remove Windows Gadget Platform
	- Nothing full trust
- Check startup applications
Things to watch out for: 
- Applications appearing an reappearing 
- Applications changing names
- Check cpu times
- install applications needed using ninite
- use dism and sfc /scannow
# Network Security
- Turn Firewalls on
- emergency: set firewall to block incomming and outgoing by default and then start blocking
- Make sure that firewall service is up if issues occur. 



# Infection types:

- **Appender Infection** – The virus is at the end of the program, eventually executing when the end of the file is executed
- **Swiss cheese Infection** – This is when the virus is injected into various places of the program. Anytime a specific item is executed (and it is infected), it will execute the viruses code.
- **Split Infection** – The virus is split into various parts and proceeds to be stored in various areas, when executed, the virus will switch to different places, executing the code.

# Command Line Tips:
- General:
	- **>** outputs to something
	- **findstr** = grep
	- **tasklist** = task info
	- you can echo variables to easily see them
	- **hostname** = find hostname
- **Networking**:
	-  **netsh advfirewall reset** to reset firewall to default
		- usage of turning on firewall: netsh advfirewall set currentprofile state on
	- **ipconfig /all** to show all interfaces info
	- **ipconfig /flushdns** to flush dns
		- Useful if dns cache is poisoned or changed
	- **nslookup** for dns info
	- **net sessions** to view local computer connections (DISCONNECT ANYTHING NOT AUTHORIZED)
		- net session \\computername /del to delete a session
	- 
	- **netstat** used to view network statistics
		- **netstat** (seconds) to have the netstat auto update
			- eg netstat 5
			- eg with flags: netstat –ano –p tcp 5
		- Flags:
			- **-a** displays all tcp connections with tcp and udp ports open
			- **-n** displays active tcp connections but the port numbers and addresses are expresse with numbers
			- **-o** displays the active tcp connection while also displaying the PID
			- **-p** displays the protocol
				- eg netstat -p tcp for tcp connections
			- use all 3 together with -ano
- **User Management**:
	- **net user** to manage users on machine
		- to add user: net user username password /add
		- to disable (not delete) a user net username /active:yes
	- **net localgroup** to view all groups in system
		- net localgroup administrators will show all users with administrator group
	- **net share** to manage network storage shares
		- net share sharename /del to delete shares.  
	- **net accounts**
		- Usage: net accounts /minpwlen:8 /maxpwage:90 /minpwage:15 /uniquepw:24
	- **net use** connect to any share using ip, name of the share and user/password of system trying to access. 
		- usage: net use C: \\192.168.0.1\C$
			- C$ is share trying to access