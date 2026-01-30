# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int mod26(int x) {
    int r = x % 26;
    if (r < 0) r += 26;
    return r;
}

int main() {
    char plain[100];
    int key[3][3];
    int i, j, k;

    printf("Enter plaintext (only letters): ");
    scanf("%s", plain);

    int len = strlen(plain);

    // convert to uppercase
    for (i = 0; i < len; i++) {
        plain[i] = toupper(plain[i]);
    }

    // padding with X if needed
    while (len % 3 != 0) {
        plain[len] = 'X';
        len++;
    }
    plain[len] = '\0';

    printf("Enter 3x3 key matrix (row-wise):\n");
    for (i = 0; i < 3; i++) {
        for (j = 0; j < 3; j++) {
            scanf("%d", &key[i][j]);
            key[i][j] = mod26(key[i][j]);
        }
    }

    char cipher[100];
    int p[3], c[3];
    int index = 0;

    // process each block of 3 letters
    for (i = 0; i < len; i += 3) {

        // convert letters to numbers
        for (j = 0; j < 3; j++) {
            p[j] = plain[i + j] - 'A';
        }

        // matrix multiplication key * p
        for (j = 0; j < 3; j++) {
            c[j] = 0;
            for (k = 0; k < 3; k++) {
                c[j] += key[j][k] * p[k];
            }
            c[j] = mod26(c[j]);
        }

        // convert numbers back to letters
        for (j = 0; j < 3; j++) {
            cipher[index++] = c[j] + 'A';
        }
    }

    cipher[index] = '\0';

    printf("Cipher text: %s\n", cipher);

    return 0;
}
```

## OUTPUT
<img width="849" height="354" alt="image" src="https://github.com/user-attachments/assets/15d27714-bdc2-49a5-a91f-0ad1450138e6" />

## RESULT
The program is executed successfully


