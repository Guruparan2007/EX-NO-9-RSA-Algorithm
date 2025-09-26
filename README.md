# EX-NO-9-RSA-Algorithm

## AIM:
To Implement RSA Encryption Algorithm in Cryptography

## Algorithm:


Step 1: Design of RSA Algorithm  
The RSA algorithm is based on the mathematical difficulty of factoring the product of two large prime numbers. It involves generating a public and private key pair, where the public key is used for encryption, and the private key is used for decryption.

Step 2: Implementation in Python or C 
This algorithm can be implemented in languages like Python or C by performing large integer calculations for key generation, encryption, and decryption, utilizing libraries for modular arithmetic if necessary.

Step 3: Algorithm Description  
1. Key Generation:
   - Select two large prime numbers \( p \) and \( q \).
   - Calculate \( n = p \times q \), which will be used as the modulus.
   - Compute the totient \( \phi(n) = (p - 1)(q - 1) \).
   - Choose a public exponent \( e \) such that \( e \) is coprime with \( \phi(n) \).
   - Compute the private key \( d \), which is the modular inverse of \( e \) mod \( \phi(n) \).

2. Encryption:
   - Convert the plaintext message \( M \) into a numerical form \( m \) (such that \( 0 \le m < n \)).
   - Compute the ciphertext \( c \) using the formula: \( c = m^e \mod n \).

3. Decryption:
   - Use the private key \( d \) to recover \( m \) from \( c \) using: \( m = c^d \mod n \).
   - Convert \( m \) back into the original message \( M \).

Step 4: Mathematical Representation  
- Encryption: \( E(m) = m^e \mod n \)
- Decryption: \( D(c) = c^d \mod n \)

Step 5: **Security Foundation  
The security of RSA relies on the difficulty of factoring large numbers; thus, choosing sufficiently large prime numbers for \( p \) and \( q \) is crucial for security.

## Program:

```
#include <stdio.h> 
long long mod_pow(long long base,long long exp,long long mod){ 
long long res=1; 
base%=mod; 
while(exp>0){ 
if(exp&1) res=(res*base)%mod; 
exp>>=1; 
base=(base*base)%mod; 
} 
return res; 
} 
long long mod_inv(long long a,long long m){ 
for(long long x=1;x<m;x++) 
if((a*x)%m==1) return x; 
return -1; 
} 
int main(){ 
long long p=61,q=53,n=p*q,phi=(p-1)*(q-1); 
long long e=17,d=mod_inv(e,phi); 
long long msg; 
printf("Enter a number to encrypt (m<n): "); 
scanf("%lld",&msg); 
long long c=mod_pow(msg,e,n); 
long long m=mod_pow(c,d,n); 
printf("Public key: (n=%lld,e=%lld)\n",n,e); 
printf("Private key: (n=%lld,d=%lld)\n",n,d); 
printf("Ciphertext: %lld\n",c); 
printf("Decrypted: %lld\n",m); 
return 0; 
}
```


## Output:
<img width="475" height="298" alt="image" src="https://github.com/user-attachments/assets/27b92743-ab16-4b8b-85ab-d01c3fe1b814" />



## Result:
 The program is executed successfully.
