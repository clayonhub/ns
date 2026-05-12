# Comprehensive Cryptography and Network Security Answers

# 1. Explain RSA Algorithm in Detail with Example

## Introduction
RSA is an asymmetric key cryptography algorithm developed by Rivest, Shamir and Adleman in 1977. It is one of the most widely used public key cryptographic systems for secure data transmission, digital signatures and secure key exchange.

RSA uses two different keys:
1. Public Key – used for encryption
2. Private Key – used for decryption

The security of RSA is based on the mathematical difficulty of factoring very large prime numbers.

---

# Working Principle of RSA

RSA consists of three major phases:
1. Key Generation
2. Encryption
3. Decryption

---

# Step 1: RSA Key Generation

## Step 1: Choose Two Prime Numbers
Select two large prime numbers:

p = 17
q = 11

---

## Step 2: Compute n

n = p × q

n = 17 × 11 = 187

The modulus n is used in both public and private keys.

---

## Step 3: Compute Euler’s Totient Function

ϕ(n) = (p − 1)(q − 1)

ϕ(n) = (17 − 1)(11 − 1)

ϕ(n) = 16 × 10 = 160

---

## Step 4: Choose Public Key Exponent e

Choose e such that:

1 < e < ϕ(n)

and

GCD(e, ϕ(n)) = 1

Choose:

e = 7

Check:

GCD(7,160) = 1

Therefore valid.

---

## Step 5: Compute Private Key d

Compute d such that:

(d × e) mod ϕ(n) = 1

(d × 7) mod 160 = 1

Solving:

d = 23

Because:

23 × 7 = 161

161 mod 160 = 1

---

# RSA Keys

## Public Key
(e, n)

(7, 187)

## Private Key
(d, n)

(23, 187)

---

# Step 2: RSA Encryption

Suppose plaintext message:

M = 88

Encryption formula:

C = M^e mod n

Substitute values:

C = 88^7 mod 187

After modular exponentiation:

C = 11

Ciphertext = 11

---

# Step 3: RSA Decryption

Decryption formula:

M = C^d mod n

M = 11^23 mod 187

After modular exponentiation:

M = 88

Original message recovered successfully.

---

# RSA Algorithm Flow

1. Select prime numbers p and q
2. Calculate n = p × q
3. Calculate ϕ(n)
4. Choose public exponent e
5. Calculate private exponent d
6. Generate public and private keys
7. Encrypt using public key
8. Decrypt using private key

---

# RSA Block Diagram

Plaintext → Encryption using Public Key → Ciphertext → Decryption using Private Key → Plaintext

---

# Mathematical Foundation of RSA

RSA relies on:
1. Modular arithmetic
2. Euler’s theorem
3. Prime factorization difficulty

Euler theorem:

M^ϕ(n) ≡ 1 mod n

This property enables correct decryption.

---

# Advantages of RSA

1. Provides secure communication
2. Supports digital signatures
3. Enables authentication
4. Provides non-repudiation
5. Secure key exchange possible
6. Public key can be openly distributed
7. No need to share private key
8. Widely standardized

---

# Disadvantages of RSA

1. Slower than symmetric encryption
2. Requires large key sizes
3. Computationally expensive
4. Vulnerable if small keys are used
5. Quantum computing may break RSA in future

---

# Applications of RSA

1. HTTPS and TLS
2. Secure email systems
3. Digital signatures
4. VPN security
5. Banking applications
6. Secure file transfer
7. Software signing
8. Blockchain systems

---

# 2. Draw and Explain How DES Algorithm Works in Detail

# Introduction to DES

DES (Data Encryption Standard) is a symmetric block cipher developed by IBM and adopted by NIST.

Characteristics:

1. Block size = 64 bits
2. Key size = 56 bits
3. Total rounds = 16
4. Uses Feistel structure

---

# DES Overall Structure

Plaintext (64 bits)
↓
Initial Permutation (IP)
↓
16 Feistel Rounds
↓
Swap
↓
Final Permutation (FP)
↓
Ciphertext

---

# Detailed Working of DES

# Step 1: Initial Permutation (IP)

The 64-bit plaintext undergoes bit rearrangement using IP table.

Purpose:
1. Spread input bits
2. Improve diffusion

After permutation:

Divide into:

L0 = Left 32 bits
R0 = Right 32 bits

---

# Step 2: 16 Feistel Rounds

For each round i:

Li = Ri−1

Ri = Li−1 XOR F(Ri−1, Ki)

Where:

Ki = round key
F = DES round function

---

# DES Round Function F

The function F consists of:

1. Expansion Permutation
2. XOR with round key
3. S-box substitution
4. P-box permutation

---

## 1. Expansion Permutation

32-bit R input expanded to 48 bits.

Purpose:
1. Match 48-bit key
2. Increase confusion

---

## 2. XOR with Round Key

Expanded data XORed with 48-bit subkey.

Output = 48 bits.

---

## 3. S-Box Substitution

48 bits divided into:

8 groups × 6 bits

Each group enters S-box.

Each S-box converts:

6 bits → 4 bits

Total output:

32 bits

Purpose:
1. Non-linearity
2. Security against attacks

---

## 4. P-Box Permutation

32-bit output permuted.

Purpose:
1. Bit diffusion
2. Better randomness

---

# Step 3: Swap Operation

After 16 rounds:

L16 and R16 are swapped.

---

# Step 4: Final Permutation

Inverse initial permutation applied.

Output:

64-bit ciphertext.

---

# DES Key Generation

Input key = 64 bits

Actual usable key = 56 bits

8 parity bits removed.

Process:

1. Permuted Choice 1
2. Split into two halves
3. Left circular shifts
4. Permuted Choice 2
5. Generate 16 round keys

Each round key = 48 bits.

---

# DES Encryption Example (Conceptual)

Plaintext:

HELLO123

Key:

SECURITY

Steps:
1. Convert to binary
2. Initial permutation
3. 16 Feistel rounds
4. Final permutation
5. Ciphertext generated

---

# DES Decryption

DES decryption uses same structure.

Only difference:

Round keys used in reverse order.

K16 → K1

---

# Advantages of DES

1. Simple implementation
2. Fast in hardware
3. Historical importance
4. Strong confusion and diffusion

---

# Disadvantages of DES

1. Small key size
2. Vulnerable to brute force
3. Obsolete today
4. Weak against modern attacks

---

# Applications of DES

1. Legacy banking systems
2. Smart cards
3. Old communication systems
4. Historical cryptographic systems

---

# 3. Explain Any Two Classical Ciphers with Example

# A. Playfair Cipher

## Introduction

Playfair cipher is a digraph substitution cipher.

Invented by Charles Wheatstone.

Encrypts two letters together instead of one.

---

# Steps in Playfair Cipher

## Step 1: Create 5×5 Matrix

Keyword: MONARCHY

Matrix:

M O N A R
C H Y B D
E F G I K
L P Q S T
U V W X Z

I and J treated as same.

---

## Step 2: Prepare Plaintext

Message:

HELLO

Split into digraphs:

HE LX LO

Insert X if repeated letters occur.

---

## Step 3: Encryption Rules

### Rule 1: Same Row
Replace with right letter.

### Rule 2: Same Column
Replace with below letter.

### Rule 3: Rectangle Rule
Replace with opposite corner letters.

---

# Example Encryption

HE:
H → row2 col2
E → row3 col1

Rectangle substitution:

C F

Similarly:

LX → SU
LO → PM

Ciphertext:

CFSUPM

---

# Advantages

1. Better than Caesar cipher
2. Hides single-letter frequencies
3. Uses digraph encryption

---

# Disadvantages

1. Vulnerable to frequency analysis
2. Difficult for long messages
3. Not secure today

---

# B. Vigenère Cipher

## Introduction

Vigenère cipher is a polyalphabetic substitution cipher.

Uses repeated keyword.

More secure than Caesar cipher.

---

# Encryption Formula

Ci = (Pi + Ki) mod 26

Where:
Pi = plaintext letter
Ki = key letter
Ci = ciphertext letter

---

# Example

Plaintext:

ATTACKATDAWN

Keyword:

LEMONLEMONLE

---

# Encryption Table

| Plaintext | A | T | T | A | C | K | A | T | D | A | W | N |
|-----------|---|---|---|---|---|---|---|---|---|---|---|---|
| Key       | L | E | M | O | N | L | E | M | O | N | L | E |
| Cipher    | L | X | F | O | P | V | E | F | R | N | H | R |

Ciphertext:

LXFOPVEFRNHR

---

# Decryption Formula

Pi = (Ci − Ki) mod 26

---

# Advantages

1. Stronger than monoalphabetic cipher
2. Reduces frequency attack effectiveness
3. Simple implementation

---

# Disadvantages

1. Vulnerable if keyword repeats
2. Kasiski attack possible
3. Not secure for modern systems

---

# 4. Compare Symmetric and Asymmetric Key Cryptography

| Parameter | Symmetric Key Cryptography | Asymmetric Key Cryptography |
|---|---|---|
| Keys Used | Single shared key | Public and private keys |
| Speed | Fast | Slow |
| Complexity | Less complex | More complex |
| Key Distribution | Difficult | Easier |
| Security | Good for bulk data | Better for authentication |
| Encryption Time | Low | High |
| Decryption Time | Low | High |
| Scalability | Difficult for many users | Better scalability |
| Examples | AES, DES | RSA, ECC |
| Resource Usage | Low | High |
| Key Size | Smaller | Larger |
| Main Usage | Data encryption | Key exchange and signatures |
| Confidentiality | Yes | Yes |
| Authentication | Limited | Strong |
| Non-repudiation | No | Yes |
| Communication Type | Secure channel needed | Public channel possible |

---

# 5. Compare Security Techniques for CIA, Authentication and Non-Repudiation

| Technique | Confidentiality | Integrity | Authentication | Non-Repudiation |
|---|---|---|---|---|
| Classical Encryption | Moderate | Weak | No | No |
| Symmetric Encryption | Strong | Moderate | Weak | No |
| Asymmetric Encryption | Strong | Moderate | Strong | Yes |
| Hashing Technique | No | Strong | No | No |
| MAC Technique | No | Strong | Strong | No |
| Digital Signature | No | Strong | Strong | Strong |

---

# Explanation

## Classical Encryption
Provides secrecy using substitution/transposition.
Weak against modern attacks.

## Symmetric Encryption
Uses same key.
Good confidentiality.
Limited authentication.

## Asymmetric Encryption
Uses public/private keys.
Supports signatures and authentication.

## Hashing
Ensures integrity.
No encryption.

## MAC
Combines secret key and hash.
Provides integrity and authentication.

## Digital Signature
Provides integrity, authentication and non-repudiation.

---

# 6. Draw and Explain Digital Signature System

# Digital Signature Block Diagram

Message
↓
Hash Function
↓
Message Digest
↓
Encrypt Digest using Sender Private Key
↓
Digital Signature
↓
Transmit Message + Signature
↓
Receiver decrypts signature using Sender Public Key
↓
Generate hash of received message
↓
Compare digests
↓
Verified / Rejected

---

# Working of Digital Signature

## Step 1
Sender creates message.

## Step 2
Hash function generates digest.

## Step 3
Digest encrypted using sender private key.

## Step 4
Signature sent with message.

## Step 5
Receiver decrypts signature using sender public key.

## Step 6
Receiver computes new digest.

## Step 7
Digests compared.

If equal:
1. Integrity maintained
2. Sender authenticated
3. Non-repudiation achieved

---

# Applications

1. E-commerce
2. Secure email
3. Banking
4. Software signing
5. Legal documents

---

# 7. End-to-End Email Communication with Hashing, Digital Signature and Digital Envelope

# Block Diagram

Sender Side:

Message
↓
Hash Function
↓
Message Digest
↓
Encrypt digest using sender private key
↓
Digital Signature
↓
Generate Session Key
↓
Encrypt message using session key
↓
Encrypt session key using receiver public key
↓
Digital Envelope
↓
Transmission

Receiver Side:

Receive encrypted message + encrypted session key
↓
Decrypt session key using receiver private key
↓
Decrypt message using session key
↓
Decrypt digital signature using sender public key
↓
Generate hash of received message
↓
Compare digests
↓
Authentication and Integrity verified

---

# Explanation

## Hashing
Ensures integrity.

## Digital Signature
Ensures authentication and non-repudiation.

## Digital Envelope
Ensures confidentiality.

---

# 8. What is Hash Function? Explain Working and Applications of SHA-2

# Definition

Hash function converts variable length input into fixed length output.

Output called:
1. Hash value
2. Message digest

Example:
SHA-256 generates 256-bit hash.

---

# Properties of Hash Function

1. One-way function
2. Fixed length output
3. Fast computation
4. Collision resistant
5. Avalanche effect
6. Deterministic

---

# Working of Hash Function

1. Input message divided into blocks
2. Padding added
3. Initial hash values assigned
4. Compression rounds performed
5. Final digest generated

---

# SHA-2 Family

1. SHA-224
2. SHA-256
3. SHA-384
4. SHA-512

---

# Applications of SHA-2

1. Password protection
2. Blockchain
3. Digital signatures
4. SSL/TLS certificates
5. File integrity verification
6. Secure email
7. Banking systems
8. Software verification
9. VPN authentication
10. Data integrity checking

---

# 9. Explain TLS and S/MIME used in Email Security. Compare PGP vs S/MIME

# TLS (Transport Layer Security)

TLS provides secure communication over network.

Functions:
1. Encryption
2. Authentication
3. Integrity

Used in:
1. HTTPS
2. Email servers
3. VPNs

---

# TLS Working

1. Client sends hello
2. Server sends certificate
3. Key exchange occurs
4. Session key generated
5. Encrypted communication starts

---

# S/MIME

Secure/Multipurpose Internet Mail Extensions.

Provides:
1. Email encryption
2. Digital signatures
3. Authentication
4. Integrity

Uses:
1. RSA
2. X.509 certificates

---

# PGP vs S/MIME

| Parameter | PGP | S/MIME |
|---|---|---|
| Full Form | Pretty Good Privacy | Secure MIME |
| Certificate System | Web of trust | CA based |
| Usage | Personal email | Enterprise email |
| Trust Model | Decentralized | Centralized |
| Complexity | Moderate | Easier in organizations |
| Standardization | Less formal | Standardized |
| Key Management | User controlled | Certificate authority |
| Scalability | Lower | Higher |

---

# 10. Short Notes

# A. Transport and Tunnel Mode in IPSec

## Transport Mode

Only payload encrypted.

IP header remains visible.

Used for:
1. Host-to-host communication

Advantages:
1. Lower overhead
2. Faster

Disadvantages:
1. Less secure than tunnel mode

---

## Tunnel Mode

Entire IP packet encrypted.

New IP header added.

Used in:
1. VPNs
2. Gateway-to-gateway communication

Advantages:
1. Better security
2. Hides original IP

Disadvantages:
1. More overhead

---

# B. S/MIME for Email Security

Features:
1. Email encryption
2. Digital signature
3. Authentication
4. Integrity
5. Non-repudiation

Uses public key cryptography and certificates.

---

# C. TLS with Example

Suppose user accesses banking website.

Steps:
1. Browser requests secure connection
2. Server sends certificate
3. Browser verifies certificate
4. Session key established
5. Data encrypted

HTTPS lock symbol indicates TLS active.

---

# 11. Explain CIA, Authentication and Non-Repudiation

# Confidentiality

Ensures only authorized users access data.

Methods:
1. Encryption
2. Access control

---

# Integrity

Ensures data not modified.

Methods:
1. Hashing
2. Checksums
3. Digital signatures

---

# Availability

Ensures systems available when needed.

Methods:
1. Backup
2. Redundancy
3. Fault tolerance

---

# Authentication

Verifies user identity.

Methods:
1. Passwords
2. Biometrics
3. OTP
4. Certificates

---

# Non-Repudiation

Sender cannot deny performing action.

Achieved using:
1. Digital signatures
2. Certificates

---

# 12. Explain Interruption, Interception, Modification and Fabrication Attack

# Interruption Attack

Targets availability.

Example:
Server crash or DoS attack.

Affects:
Availability.

---

# Interception Attack

Unauthorized access to data.

Example:
Packet sniffing.

Affects:
Confidentiality.

---

# Modification Attack

Unauthorized data alteration.

Example:
Man-in-the-middle attack.

Affects:
Integrity.

---

# Fabrication Attack

Fake data insertion.

Example:
Fake email or spoofing.

Affects:
Authentication and non-repudiation.

---

# Correlation Table

| Attack | Affected Security Property |
|---|---|
| Interruption | Availability |
| Interception | Confidentiality |
| Modification | Integrity |
| Fabrication | Authentication, Non-Repudiation |

---

# 13. Compare Classical vs Modern Cryptography

| Parameter | Classical Cryptography | Modern Cryptography |
|---|---|---|
| Technique | Manual methods | Mathematical algorithms |
| Security | Weak | Strong |
| Keys | Simple | Complex |
| Speed | Slow | Fast |
| Automation | No | Yes |
| Attacks | Easy to break | Hard to break |
| Examples | Caesar cipher | AES, RSA |
| Key Size | Small | Large |
| Computation | Minimal | High |
| Authentication | Weak | Strong |

---

# 14. What is DoS and DDoS Attack? Mitigation Techniques

# DoS Attack

Denial of Service attack floods target with traffic.

Goal:
Make service unavailable.

---

# DDoS Attack

Distributed DoS uses multiple compromised systems.

Harder to stop.

---

# Types

1. SYN flood
2. UDP flood
3. ICMP flood
4. HTTP flood

---

# Mitigation

1. Firewalls
2. Rate limiting
3. IDS/IPS
4. Load balancing
5. CDN usage
6. Traffic filtering
7. Anti-DDoS services
8. Blackhole routing

---

# 15. Steganography for Image Data

# Definition

Steganography hides secret data inside image.

---

# Block Diagram

Secret Message
↓
Embedding Algorithm
↓
Cover Image
↓
Stego Image
↓
Transmission
↓
Extraction Algorithm
↓
Recovered Message

---

# Working

Least Significant Bit (LSB) commonly used.

Pixel bits modified slightly.

Human eye cannot detect changes.

---

# Applications

1. Secret communication
2. Digital watermarking
3. Military communication
4. Copyright protection

---

# 16. Compare Steganography vs Cryptography

| Parameter | Steganography | Cryptography |
|---|---|---|
| Goal | Hide existence of data | Hide meaning of data |
| Visibility | Secret hidden | Ciphertext visible |
| Detection | Difficult | Easy to detect |
| Security Basis | Concealment | Encryption |
| Data Form | Hidden in media | Converted to ciphertext |
| Example | Hidden image text | AES encryption |
| Failure Impact | Hidden message exposed | Ciphertext exposed |
| Combination | Can combine with crypto | Often combined with stego |

---

# 17. Applications of Hash Functions

# A. Password Storage Protection

Passwords stored as hashes.

During login:
1. Entered password hashed
2. Compared with stored hash

Even database leak does not reveal password directly.

Salting improves security.

---

# B. Data Integrity Check

Hash generated before transmission.

Receiver recalculates hash.

If hashes match:
Data unchanged.

Used in:
1. Software downloads
2. File transfer
3. Digital signatures

---

# 18. Different Types of Cookies

1. Session Cookies
2. Persistent Cookies
3. Secure Cookies
4. HttpOnly Cookies
5. Third-party Cookies
6. Zombie Cookies
7. SameSite Cookies

---

# Session Cookies
Temporary cookies deleted after browser close.

# Persistent Cookies
Remain for defined period.

# Secure Cookies
Transferred only over HTTPS.

# HttpOnly Cookies
Cannot be accessed by JavaScript.

# Third-party Cookies
Created by external domains.

# Zombie Cookies
Recreated after deletion.

# SameSite Cookies
Prevent CSRF attacks.

---

# 19. Advantages and Drawbacks of Cookies

# Advantages

1. Session management
2. Personalization
3. Faster browsing
4. Shopping cart storage
5. User tracking

---

# Drawbacks

1. Privacy concerns
2. Tracking users
3. Session hijacking risk
4. Security vulnerabilities
5. Storage limitations

---

# 20. Session Hijacking Using Cookies

# Definition

Attacker steals session cookie.

Then impersonates user.

---

# Methods

1. XSS attack
2. Packet sniffing
3. Malware
4. Session fixation

---

# Prevention

1. HTTPS
2. Secure cookies
3. HttpOnly cookies
4. Short session timeout
5. Multi-factor authentication

---

# 21. Firewalls

# A. Packet Filtering Firewall

Filters packets using:
1. IP address
2. Port number
3. Protocol

Works at network layer.

Advantages:
1. Fast
2. Simple

Disadvantages:
1. Limited inspection

---

# B. Application Layer Firewall

Operates at application layer.

Inspects application data.

Advantages:
1. High security
2. Deep packet inspection

Disadvantages:
1. Slower

---

# C. Circuit Level Gateway Firewall

Monitors TCP handshakes.

Creates secure sessions.

Advantages:
1. Hides internal network

Disadvantages:
1. No payload inspection

---

# 22. Compare Firewall vs Antivirus

| Parameter | Firewall | Antivirus |
|---|---|---|
| Purpose | Block unauthorized access | Detect malware |
| Working | Filters traffic | Scans files/programs |
| Protection Type | Network protection | System protection |
| Attack Prevention | External attacks | Malware attacks |
| Layer | Network layer | Host layer |
| Example Threat | Intrusion | Virus |
| Operation | Real-time traffic monitoring | Signature scanning |
| Scope | Network | Device |

---

# 23. Compare IDS and IPS

| Parameter | IDS | IPS |
|---|---|---|
| Full Form | Intrusion Detection System | Intrusion Prevention System |
| Function | Detect attacks | Detect and block attacks |
| Placement | Passive | Inline |
| Response | Alert only | Automatic prevention |
| Traffic Handling | Monitors | Controls |
| Risk | Less disruption | Possible false blocking |
| Action | Logging | Blocking |
| Security Level | Moderate | Higher |

---

# 24. Explain AH and ESP in IPSec

# AH (Authentication Header)

Provides:
1. Authentication
2. Integrity
3. Anti-replay protection

Does not provide encryption.

---

# ESP (Encapsulating Security Payload)

Provides:
1. Confidentiality
2. Authentication
3. Integrity

Encrypts payload.

More commonly used.

---

# Comparison

| Feature | AH | ESP |
|---|---|---|
| Encryption | No | Yes |
| Integrity | Yes | Yes |
| Authentication | Yes | Yes |
| Confidentiality | No | Yes |
| NAT Compatibility | Poor | Better |

---

# 25. WEP and WPA Security Techniques

# WEP (Wired Equivalent Privacy)

Older Wi-Fi security protocol.

Uses:
1. RC4 encryption
2. 40-bit or 104-bit keys

Weaknesses:
1. Weak IV
2. Easily cracked

---

# WPA (Wi-Fi Protected Access)

Improved version.

Uses:
1. TKIP
2. MIC
3. Dynamic keys

---

# WPA2

Uses AES encryption.

More secure.

---

# WPA3

Latest version.

Provides:
1. Stronger authentication
2. Better encryption
3. Forward secrecy

---

# 26. Wireless Components Used for Wi-Fi and Bluetooth

# Wi-Fi Components

1. Access Point
2. Wireless Router
3. Wireless NIC
4. Antenna
5. Repeater
6. Wireless Controller

---

# Bluetooth Components

1. Bluetooth Adapter
2. Bluetooth Radio
3. Piconet
4. Master Device
5. Slave Device
6. Bluetooth Antenna

---

# 27. ISM Band Frequencies, Bluetooth Standards and Wi-Fi Standards

# ISM Bands

| Band | Frequency |
|---|---|
| 900 MHz | 902–928 MHz |
| 2.4 GHz | 2.4–2.4835 GHz |
| 5.8 GHz | 5.725–5.875 GHz |

---

# Bluetooth Standards

| Version | Features |
|---|---|
| Bluetooth 1.x | Basic connectivity |
| Bluetooth 2.x | Enhanced data rate |
| Bluetooth 3.x | Higher speed |
| Bluetooth 4.x | BLE support |
| Bluetooth 5.x | Long range and higher speed |

---

# Wi-Fi Standards

| Standard | Frequency | Speed |
|---|---|---|
| 802.11a | 5 GHz | 54 Mbps |
| 802.11b | 2.4 GHz | 11 Mbps |
| 802.11g | 2.4 GHz | 54 Mbps |
| 802.11n | 2.4/5 GHz | 600 Mbps |
| 802.11ac | 5 GHz | Gbps range |
| 802.11ax (Wi-Fi 6) | 2.4/5 GHz | Higher efficiency |

---

# 28. Practical Program – Caesar Cipher Encryption and Decryption

# Algorithm

1. Read plaintext
2. Read key
3. Convert letters using shift
4. Generate ciphertext
5. Reverse shift for decryption

---

# C++ Program

```cpp
#include <iostream>
using namespace std;

string encrypt(string text, int key){
    for(int i=0;i<text.length();i++){
        if(isupper(text[i]))
            text[i] = ((text[i]-'A'+key)%26)+'A';
        else if(islower(text[i]))
            text[i] = ((text[i]-'a'+key)%26)+'a';
    }
    return text;
}

string decrypt(string text, int key){
    return encrypt(text, 26-key);
}

int main(){
    string text;
    int key;

    cout << "Enter text: ";
    getline(cin,text);

    cout << "Enter key: ";
    cin >> key;

    string cipher = encrypt(text,key);
    cout << "Encrypted: " << cipher << endl;

    cout << "Decrypted: " << decrypt(cipher,key);

    return 0;
}
```

---

# Sample Output

Enter text: HELLO
Enter key: 3
Encrypted: KHOOR
Decrypted: HELLO

---

# 29. Practical Program – Transposition Cipher

# C++ Program

```cpp
#include <iostream>
using namespace std;

int main(){
    string text;
    cout << "Enter plaintext: ";
    cin >> text;

    string cipher="";

    for(int i=0;i<text.length();i+=2)
        cipher += text[i];

    for(int i=1;i<text.length();i+=2)
        cipher += text[i];

    cout << "Ciphertext: " << cipher;

    return 0;
}
```

---

# 30. Practical Program – Password Checking

# Objective

Check:
1. Default passwords
2. Weak passwords
3. Plaintext storage risk

---

# C++ Program

```cpp
#include <iostream>
using namespace std;

int main(){
    string password;

    cout << "Enter password: ";
    cin >> password;

    if(password == "admin" || password == "1234")
        cout << "Weak/Default Password";
    else
        cout << "Strong Password";

    return 0;
}
```

---

# 31. Simulate Diffie-Hellman Key Exchange

# Steps

1. Public values chosen:
   - Prime p
   - Primitive root g

2. User A selects private key a
3. User B selects private key b
4. Public keys exchanged
5. Shared secret generated

---

# Example

p = 23
g = 5

A private key = 6
B private key = 15

A public key:
5^6 mod 23 = 8

B public key:
5^15 mod 23 = 19

Shared secret:
19^6 mod 23 = 2

8^15 mod 23 = 2

Shared key = 2

---

# Advantages

1. Secure key exchange
2. No prior secret required
3. Used in TLS and VPNs

---

# 32. Simulate Vernam Cipher

# Definition

Vernam cipher uses XOR operation.

If key truly random and equal length:
Called One-Time Pad.

---

# Example

Plaintext:
HELLO

Key:
XMCKL

Encryption:
XOR each character.

Decryption:
Apply XOR again.

---

# Advantages

1. Very secure
2. Simple implementation

---

# Disadvantages

1. Key management difficult
2. Key must be random
3. Key must never repeat

---

# 33. Key Applications for Message Encryption

# Message

PLEASE TRANSFER ONE MILLION DOLLARS TO MY SWISS BANK ACCOUNT SIX TWO TWO FOUR

---

# Caesar Cipher with Key = 3

P → S
L → O
E → H

Encrypted message generated using +3 shift.

---

# Caesar Cipher with Key = 5

P → U
L → Q

Encrypted using +5 shift.

---

# Vigenère Cipher with Key = MEGABUCK

Keyword repeated.

Plaintext letters shifted according to keyword letters.

Produces polyalphabetic ciphertext.

---

# Security Observation

1. Caesar cipher weak
2. Vigenère stronger
3. OTP strongest among classical methods

---

# 34. Compare Firewall vs Antivirus vs IDS vs IPS

| Feature | Firewall | Antivirus | IDS | IPS |
|---|---|---|---|---|
| Main Goal | Filter traffic | Detect malware | Detect attacks | Prevent attacks |
| Placement | Network boundary | Host system | Monitoring point | Inline network |
| Blocking | Yes | Yes | No | Yes |
| Detection | Rules | Signatures | Patterns | Patterns + blocking |
| Scope | Network | Files/programs | Intrusion | Intrusion prevention |
| Performance Impact | Moderate | Moderate | Low | Higher |
| Real-time Action | Yes | Yes | Alerts only | Automatic response |

---

# Conclusion

Cryptography and network security together form the foundation of modern secure communication systems. Classical cryptography introduced the concepts of substitution and transposition, while modern cryptography uses advanced mathematical algorithms like RSA, AES and SHA to provide confidentiality, integrity, authentication and non-repudiation. Technologies such as TLS, IPSec, digital signatures, hashing, firewalls and IDS/IPS systems are essential for protecting modern computer networks, wireless systems, emails, banking systems and internet communication from various cyber attacks.

