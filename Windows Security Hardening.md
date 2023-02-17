# Users and groups:
### Tools:
- microsoft management console #mmc - can be used for most windows admin tools  
	- snap ins: file>add snap ins
	- win + r mmc
- local security policy #lsp - windows policy changing and implementation

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
