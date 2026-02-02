# HILL CIPHER

## EX. NO: 3 

## AIM:

To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B = 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To decrypt the message, each block is multiplied by the inverse of the m trix used for encryption. The matrix used for encryption is the cipher key, and it shold be chosen randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. 

STEP-2: Split the plain text into groups of length three. 

STEP-3: Arrange the keyword in a 3*3 matrix.

STEP-4: Multiply the two matrices to obtain the cipher text of length three.

STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 

```
import numpy as np

keymat = np.array([
    [1, 2, 1],
    [2, 3, 2],
    [2, 2, 1]
])
# Inverse key matrix (mod 26)
invkeymat = np.array([
    [-1, 0, 1],
    [2, -1, 0],
    [-2, 2, -1]
])

key = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
def char_to_num(c):
    return ord(c) - 65

def num_to_char(n):
    return key[n % 26]

def encode(a, b, c):
    pos = np.array([char_to_num(a), char_to_num(b), char_to_num(c)])
    result = pos @ keymat
    return "".join(num_to_char(x) for x in result)

def decode(a, b, c):
    pos = np.array([char_to_num(a), char_to_num(b), char_to_num(c)])
    result = pos @ invkeymat
    return "".join(num_to_char(x) for x in result)

def hill_cipher():
    msg = "SecurityLaboratory"
    print("Simulation of Hill Cipher")
    print("Input message :", msg)

    msg = msg.upper()
    # Padding with X
    n = len(msg) % 3
    if n != 0:
        msg += "X" * (3 - n)
    print("Padded message :", msg)
    enc = ""
    for i in range(0, len(msg), 3):
        enc += encode(msg[i], msg[i+1], msg[i+2])
    print("Encoded message :", enc)
    dec = ""
    for i in range(0, len(enc), 3):
        dec += decode(enc[i], enc[i+1], enc[i+2])
    print("Decoded message :", dec)
hill_cipher()

```

## OUTPUT

<img width="617" height="244" alt="image" src="https://github.com/user-attachments/assets/8ff01f3d-2b74-4abf-a65d-8bb2a9539d71" />

## RESULT

Thus the program to implement Hill Cipher is done successfully.
