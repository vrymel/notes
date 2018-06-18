# openssl

#### Encrypt file

    openssl aes-256-cbc -salt -in <filename> -out <output filename>

[Source](http://tombuntu.com/index.php/2007/12/12/simple-file-encryption-with-openssl/)

#### Decrypt file

    openssl aes-256-cbc -d -in <filename to decrypt> -out <decrypted filename output>

[Source](http://tombuntu.com/index.php/2007/12/12/simple-file-encryption-with-openssl/)