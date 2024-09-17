# Certificates
It is a digital document that proves the identity of a entity and binds that identity with a public key. It is a critical part of PKI infrastructure enabling secure, authenticated communication through encryption and digital signatures.
## Key roles of a certificate
1. Trust :- Certificates are issues by CA (certificate authorities) and they verify the identity of the entity requesting certificate, ensuring that the public key actually belongs to the entity( Individual, org, website, etc).
2. Authentication :- Certificate authenticates the identity of an entity(website, person) in online transactions and give confidence that interaction is made with intended entity.
3. Secure communication :- Certificates consist of public keys which are used to initiate secure communication. Encryption keys are exchanged via asymmetric encryption ( encrypted using public keys and decrypted using private keys). This encryption keys are then further used for further communication which is secured via symmetric encryption.
4. Non-repudiation :- Certificate owner can not deny having send a digitally signed document or message.
## What does certificate contains
1. Subject :- The entity that certificate represents.
2. Public key :- Public key of the entity/subject.This is used to verify identity of entity/subject or encrypt data for subject and send.
3. Issuer:- CA that issued certificate.
4. Validity period
5. Digital Signature:- Certificate is digitally signed by CA using its private key.The Signature ensures certificate's authenticity and integrity.
6. Serial number :- A unique no assigned by CA to each certificate for identification.
7. Signature Algorithm :- The algorithm used by CA to digitally sign the certificate. Ex/- RSA with SHA-256(sha256WithRSAEncryption)
## Types of certificates
1. SSL/TLS Certificates:- Used to secure communication between client and server in HTTPS.It verifies the authenticity of website and enables secure communication between client and server by encrypting data in transit.
2. Code signing Certificates:-Used by software developers to sign software packages.It assures software came from a trusted source and was not tampered.
3. Email certificates:- used to sign and encrypt emails, ensuring secure email communication and verifying the identity of sender.
4. Client Certificates :- used to authenticate users to servers.

 ## How does a certificate look like
 ### X.509
 An X.509 certificate is a certificate which is very commonly used and adopts widely accepted international X.509 Public key infrastructure (PKI) standard to verify that public key belongs to the user. It can be represented in various formats such as PEM, DFR and PFX.
1. .PEM format :- PEM (privacy-enhanced mail) Base64 encoded format between -----BEGIN CERTIFICATE----- and -----END CERTIFICATE----- 
2. .DER format :- DER (Distinguished Encoding Rules) is a binary format that is not human-readable. used for binary encoded certificate.
3. .PFX/P12 format :- A binary format that can inlcude both the certificate and the private key, usually protected by a password. Used for exporting and importing certificates and private key.
```
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number: 1234567890 (0x499602d2)
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: CN=Example CA, O=Example Org, C=US
        Validity
            Not Before: Sep 17 00:00:00 2023 GMT
            Not After : Sep 17 00:00:00 2024 GMT
        Subject: CN=www.example.com, O=Example Org, C=US
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
            Public-Key: (2048 bit)
                Modulus: 00:d3:bc:15:2a:c7...
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            X509v3 Subject Alternative Name:
                DNS:www.example.com, DNS:example.com
        Signature Algorithm: sha256WithRSAEncryption
            42:33:ac:12:ef:fa...

```
#### Tools used for viewing certificates
openssl
```
openssl x509 -in certificate.pem -text -noout
```
keytool
```
keytool -list -v -keystore keystore.jks
```
