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
	- 

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

# Network Security
- Turn Firewalls on
- emergency: set firewall to block incomming and outgoing by default and then start blocking
- Make sure that firewall service is up if issues occur. 
- 