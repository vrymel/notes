# openssl

#### Encrypt file

    openssl aes-256-cbc -salt -in <filename> -out <output filename>

#### Decrypt file

    openssl aes-256-cbc -d -in <filename to decrypt> -out <decrypted filename output>