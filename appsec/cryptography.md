# cryptography

## поточные

генератор случайных чисел

стойкий шифр == длина ключа должна быть равной длине шифрованного сообщения



## блочные

блок текста фиксированной длинны преращается в шифрованный блок такой же длинны

размер блока 128 bit

размер ключа 128-512

`DES`, `AES` -> блочные шифры

многораундовые

`AES` намного быстрее

## encrypt

`offline message exchange`:

1. encrypt a message by symmetric key (session key)
2. calculate hash from encrypted message 
3. encrypt the hash by sender's private key
4. encrypt symmetric key (session key) by recipient's public key

## HMAC

`sendor`

1. we have calculated the `session key` -> do not use it straight-forward
2. calculate 2 keys from the `session key` that was calculated earlier whis the function
    `encryption key` - Ke
    `verification key` - Kv
3. encrypt a message by the encryption key == E`ke`(M)
4. add HMAC by the verification key == HMAC`kv`(E`ke`(M)) (hash func)

`recipient`

1. check the HMAC`kv`(E`ke`(M))
2. decrypt the message

### PKI

1. confidentiality -> encryption
2. integrity -> digital sign
3. authentication

1. generate privkey and pubkey
2. generate CSR -> add pubkey and personal information -> submit this CSR to the CA
3. CA checks the received CSR (verification sender)
4. CA sings the CSR by a private key and issues the certificate

signature algorithm == Hash func == md5, sha-1, sha-2

### HTTPS

1. authentication
2. integrity
3. encryption


