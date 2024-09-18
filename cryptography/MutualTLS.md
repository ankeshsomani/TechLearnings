# Mutual TLS
A protocal that uses TLS to provide mutual authentication between client and server, ensuring that both parties are authenticated before establishing a secure connection.

## Practical

### Pre-requisites
1. Certificates - Client Cert, Server Cert, CA
2. Keystores and TrustStores

### Generate server certificate and save it in server truststore
```
keytool -genkeypair -alias server -keyalg RSA -keysize 2048 -keystore server.keystore -validity 365 -storepass password -keypass password -dname "CN=localhost, OU=IT, O=ankesh, L=Pune, C=India"      
Generating 2,048 bit RSA key pair and self-signed certificate (SHA256withRSA) with a validity of 365 days
  for: CN=localhost, OU=IT, O=ankesh, L=Pune, C=India
```
### Generate client certificate and save it in client trustsore
```
keytool -genkeypair -alias client -keyalg RSA -keysize 2048 -keystore client.keystore -validity 365 -storepass password -keypass password -dname "CN=client, OU=IT, O=ankesh, L=Pune, C=India"
Generating 2,048 bit RSA key pair and self-signed certificate (SHA256withRSA) with a validity of 365 days
	for: CN=client, OU=IT, O=ankesh, L=Pune, C=India
```
### Export client cert and server cert from keystore in a file
```
keytool -export -alias server -file server.cer -keystore server.keystore -storepass password 
Certificate stored in file <server.cer>

keytool -export -alias client -file client.cer -keystore client.keystore -storepass password 
Certificate stored in file <client.cer>
```

### Import server certificate in client truststore
```
keytool -import -alias server -file server.cer -keystore client.truststore -storepass password 
Owner: CN=localhost, OU=IT, O=ankesh, L=Pune, C=India
Issuer: CN=localhost, OU=IT, O=ankesh, L=Pune, C=India
Serial number: 15ad1942119a8379
Valid from: Wed Sep 18 22:07:34 IST 2024 until: Thu Sep 18 22:07:34 IST 2025
Certificate fingerprints:
	 SHA1: C2:37:23:4D:79:43:97:D3:59:74:D5:8A:50:DF:CD:0C:64:78:6B:DB
	 SHA256: E0:45:98:AC:59:41:3B:C5:26:10:3B:41:EF:CD:0C:66:FD:7B:AB:28:68:DA:AA:AC:73:77:02:A1:68:04:13:06
Signature algorithm name: SHA256withRSA
Subject Public Key Algorithm: 2048-bit RSA key
Version: 3

Extensions: 

#1: ObjectId: 2.5.29.14 Criticality=false
SubjectKeyIdentifier [
KeyIdentifier [
0000: 45 85 D4 BA ED ED 18 8A   1F 40 2E AA 04 4B 8E 3E  E........@...K.>
0010: F6 52 2D 9A                                        .R-.
]
]

Trust this certificate? [no]:  yes
Certificate was added to keystore
```

### Import client certificate in server truststore
```
keytool -import -alias client -file client.cer -keystore server.truststore -storepass password
Owner: CN=client, OU=IT, O=ankesh, L=Pune, C=India
Issuer: CN=client, OU=IT, O=ankesh, L=Pune, C=India
Serial number: 574debe4910d283d
Valid from: Wed Sep 18 22:11:18 IST 2024 until: Thu Sep 18 22:11:18 IST 2025
Certificate fingerprints:
	 SHA1: 5D:42:E1:31:E4:71:01:F9:B2:B2:88:3B:BA:98:B1:88:D0:E3:DC:0B
	 SHA256: 22:1C:F0:3A:94:7F:5A:A8:55:1E:3C:F5:1A:ED:A5:06:8B:69:C0:AA:C8:3E:D5:D5:BA:4D:5E:4C:9C:DD:31:E2
Signature algorithm name: SHA256withRSA
Subject Public Key Algorithm: 2048-bit RSA key
Version: 3

Extensions: 

#1: ObjectId: 2.5.29.14 Criticality=false
SubjectKeyIdentifier [
KeyIdentifier [
0000: 19 17 91 7D 94 C9 7F D0   D0 3C 99 7C 57 BC 6F BF  .........<..W.o.
0010: 37 B4 D9 59                                        7..Y
]
]

Trust this certificate? [no]:  yes
Certificate was added to keystore
```
### List local files and validate required files are present
```
ls -a
.			client.cer		client.truststore	server.keystore
..			client.keystore		server.cer		server.truststore 
```

### Run below java code to check client and server are able to connect using mutual TLS
```
https://github.com/ankeshsomani/learning-lab/blob/main/src/main/java/com/ankesh/cryptography/MutualTLSTest.java
```
