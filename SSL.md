#### create a ssl private key and csr 
      openssl req \
             -newkey rsa:2048 -nodes -keyout domain.key \
             -out domain.csr\
      -subj "/C=US/ST=New York/L=Brooklyn/O=Example Brooklyn Company/CN=localhost"


#### create a ssl certificate which contains the private key
      openssl x509 \
             -signkey domain.key \
             -in domain.csr \
             -req -days 365 -out domain.crt


#### Sign the text file with created private key
    openssl dgst -sha256 -sign <private-key> -out sign.sha256 <file>

<private-key> private key create in above step 
<file> file you want to sign
sign.sha256 is binary digital signature generated from file


#### Then you can encrypt the signature 

#### To verify the signature you need a public key
 
#### To get the public key from certificate file

    openssl x509 -pubkey -noout -in domain.cert > pubkey.pem
    openssl dgst -sha256 -verify pubkey.pem -signature sign.sha256 <file>
