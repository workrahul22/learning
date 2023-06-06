# Improving the security of RSA with OAEP

## In cryptography, Optimal Asymmetric Encryption Padding is a padding schema often used together with RSA encryption, standarized in PKCS#1 v2

# How RSA works?

## Lets initially decide the keys

- Choose two different large random prime numbers p and q => let say p=2 q=7 (Note: we are choosing a small number for the sake of explaining)
- Calculate n=pq (n = 14), n is the modulus for the public key and the private keys.
- Calculate the coprime count of n, this can be calculated by multiplying (p-1)(q-1) => x = 6
- Choose e where e satisfied below 2 conditions
    - 1 < e < x => (1 < e < 6)
    - coprime with n and x => (coprime with 14 and 6, only the value 5 satisfies the required condition)
    - so the Encryption pair is : (11, 14)
- Now lets calculate the decryption pair, choose d where d.e(mod(x)) = 1, In my case i should choose 5.d(mod(6))=1, I can choose 5, 11, 17 etc. I choose 11 here. So the decryption pair is (11, 14)

## Lets encrypt the plain text with RSA now

### Lets use the plain text value B

### Encryption (5, 14)
### To encrypt, we need to take B^e(mod(x)) => 25(mod)