CertTools
=========

Utility programs for managing certs in Microsoft Active Directory

### certhex
Converts between Hex strings (as found in AD) and DER-formatted certs

```
Usage: certhex.exe <command> <sourceFile> <destFile>

  Commands:

 - h2c    Hex String to Certificate
 - c2h    Certificate to Hex String

  Examples:

    Convert the hex in file myHex.txt (copied/pasted from AD) into a 
      DER-formatted certificate

      certhex.exe -h2c myHex.txt myCert.cer

    Convert the DER-formatted certificate in myCert.cer into a hex string in 
      myHex.txt suitable for copy/paste into AD (userCertificate attribute)
      
      certhex.exe -c2h myCert.cer myHex.txt
```

### adcerts
Lists, Adds, Exports, and Removes certs to and from Active Directory

```
Usage: adcerts.exe <command> [options]

  Commands:

 - list     Lists all certs for a user by serial number
 - export   Get certs for a user
 - put      Publish a cert for a user
 - del      Remove a cert from a user

  Examples:

    List all certs (by serial number) for a user (specified by DN)
      adcerts.exe -list "CN=John A. Ruiz,CN=Users,DC=example,DC=com"

    Export all certs for a user (specified by DN)
      adcerts.exe -export "CN=John A. Ruiz,CN=Users,DC=example,DC=com"

    Export a cert (specified by serial number) for a user (specified by DN)
      adcerts.exe -export "CN=John A. Ruiz,CN=Users,DC=example,DC=com" 62905F2500000000004D

    Publish a cert for user (specified by DN)
      adcerts.exe -put newCert.cer "CN=John A. Ruiz,CN=Users,DC=example,DC=com"

    Remove the cert with the given serial number from a user (specified by DN)
      adcerts.exe -del "CN=John A. Ruiz,CN=Users,DC=example,DC=com" 62905F2500000000004D
```