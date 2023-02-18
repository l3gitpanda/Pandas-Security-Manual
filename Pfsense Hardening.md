## Restricting Admin Access 
- Restrict ips of who can access management aswell as admin account
- give strong passwords to admin account
- Change username for admin if possible 
- USE MFAAAAAAAAAAA

## Encrypt all traffic
- use https for management aswell as anything else that allows it
- setup certificates................ gotta figure this out maybe
- enable aes-ni cpu base acceleration

## Restrict internal network access
- strict rules for ip addresses in the internal network
- only things that need rules should get them

## Update Everything

## Backups
Not sure if this will be necessary but we also have boot environments.

1.  Keep the pfSense box and all the services running on it up-to-date with the latest security patches and updates. Regularly check for new security advisories and apply patches as soon as possible.
    
2.  Disable or block all unnecessary services, ports, and protocols that are not required for the functionality of the system. This minimizes the attack surface and reduces the risk of a successful attack.
    
3.  Use strong passwords for all user accounts and enforce the use of strong passwords for all services, especially for any services that can be accessed from the internet.
    
4.  Use multi-factor authentication (MFA) for all remote access to the system, such as SSH or VPN. MFA adds an extra layer of security by requiring an additional authentication factor in addition to the password, such as a time-based one-time password (TOTP) or a smart card.
    
5.  Enable and configure firewall rules to control the inbound and outbound traffic to and from the system. Use the principle of least privilege, meaning only allow necessary traffic to pass through the firewall.
    
6.  Monitor the system logs and set up alerts for any suspicious activities, such as failed login attempts, unusual traffic patterns, or changes to the system configuration.
    
7.  Regularly backup the system and the data on it to ensure the ability to quickly recover from any security incidents or hardware failures.
    
8.  Conduct regular security audits and vulnerability assessments to identify and mitigate any potential weaknesses in the system.