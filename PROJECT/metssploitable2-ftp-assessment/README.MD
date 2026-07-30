# Metasploitsble2 FTP Security Assessment

## Target

- Target: Metasploitable2
- IP Address: 192.168.56.101
- Assessment Type: Local Vulnerability Assessment
- Environment: VirtualBox lab

## FINDINGS: Anonymous FTP Access 

# Description

The ftp service on port 21 allows anonymous users to log in without a normal user account.

### Discovery 

Nmap identified the FTP service and confirmed that anonymous FTP login is allowed.

### Verification 

Manual FTP authentication was performed using the 'anonymous' username.
the server returned:
'230 Login successful.'
the remote working directory was also confirmed as:
'/'

### Security impact 
Anonymous FTP access can expose files or directories to unauthorized user if sensitive information is stored in the FTP-accessible location.

### Risk
Medium

### Recommendation
Disable anonymous FTP access unless it is explicitly required. If anonymous access is necessary,restrict the accessible directory and permissions, and ensure that sensitive files cannot be accessed.

### Evidence 

- Nmap identified anonymous FTP access 
- Manual login using 'anonymous' succeeded.
- FTP server returned '230 Login successful'.
- Remote directory confirmed as '/'.

## Conclusion
The assessment confirmed that anonymous FTP access is enabled on the metasploitable2 host. This configuration can create an information-disclosure risk and should be disabled or properly restricted in a production environment.
