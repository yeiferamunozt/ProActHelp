## Encrypted to free cloud sharing service
  
Upload file encrypted to free.keep.sh
> Note: Use a secure password

```bash
openssl aes-256-cbc -pbkdf2 -in <any.file> | curl -T - https://free.keep.sh/secrets.enc
```

Output
> Note: Copy the link to download the file

```
enter aes-256-cbc encryption password:
Verifying - enter aes-256-cbc encryption password:
https://free.keep.sh/8dWV2y9YzzOw5XiT/secrets.enc
```
## Download encrypted from free cloud sharing service in development  

Download and decrypted from free.keep.sh
> Note: Use the link generated and the password used to encrypt the file

```bash
curl -LO https://free.keep.sh/8dWV2y9YzzOw5XiT/secrets.enc
openssl aes-256-cbc -pbkdf2 -d -in secrets.enc -out <outpu.file>
```