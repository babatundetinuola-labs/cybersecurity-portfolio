#metasploitable2 - mysql security Assessment

A hands-on cybersecurity lab where i investigated an intentionally vulnerable Metasploitable2 system,identified an exposed MYSQL service,researched a related vulnerability,and assessed weak password storage.      

#Objective
 To assess the security of an intentionally vulnerable metasploitable2 system by identifying exposed services,investigating the mysql service, and assesing the security of password storage within the DNWA application.

 ## Lab environment 
 -Attacker machine: Kali Linux
 -Target machine: Metasploitable2
 -Target IP: 192.168.56.101
 -Application tested: DVWA
 -Network: Isolated VirtualBox lab

 ## Tool Used
 -Nmap - network/service discovery
 -MYSQL - database investigation
 -John the Ripper - password-hash auditing
 -NIST National Vulnerability Database (NVD) - vulnerability research

 ## Methodology
1. Scanned the metasploitable2 host with Nmap to identify exposed services.
2. Performed service and version detection to identify software running on exposed ports.
3. Identified MYSQL 5.0.51a running on port 3306.
4. Researched the identified MYSQL version using the NIST National Vulnerability Database.
5. investigated the DVWA database and its 'users' table
6. identified MDS password hashes stored in the database.
7. used John the Ripper in the authorized lab environment to demonstrate recovery of a weak password hash.
      
## Findings 

### Finding 1 - MYSQL service Exposed

Nmap identified MYSQL 5.0.51a running on port 3306.

### finding 2 - weak passwoard Hashing 

The DVWA 'users' table stored password values as 32-character MD5 HASHES.

Testing confirmed that the hashe:

'5f4dcc3baa765d61d8327deb882cf99'

corresponds to the weak password 'password'.

John the Ripper successfully recovered the password from the md5 hash in the authorized lab environment.

### Security impact

Weak password hashing can allow attackers who obtain password hashes to recover weak passwords, potentially leading to unauthorized account access.

### Recommendation

Use a modern password-hashing algorithm designed for password storage,such as Argon2id,bcrypt, or scrypt, with unique salts for each password. Enforce strong passwotrd policies and protect the database from unauthorized access.
