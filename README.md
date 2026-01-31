# VIGENERE-CIPHER

-----
#### Date:31/01/26
#### Reg No:212224230211
#### Name:Priyan V
-----

## EX. NO: 4

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.<br>
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.<br>
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.<br>
STEP-4: The keyword and the plain text is read from the user.<br>
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.<br>
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.<br>
STEP-7: The junction character where these two meet forms the cipher character.<br>
STEP-8: Repeat the above steps to generate the entire cipher text.<br>


## PROGRAM
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void encrypt(char *plaintext, char *key, char *ciphertext) {
    int textLen = strlen(plaintext);
    int keyLen  = strlen(key);

    for (int i = 0, j = 0; i < textLen; i++) {
        char currentChar = plaintext[i];

        if (isalpha(currentChar)) {
            char base = isupper(currentChar) ? 'A' : 'a';
            int keyShift = tolower(key[j % keyLen]) - 'a';

            ciphertext[i] = (currentChar - base + keyShift) % 26 + base;
            j++;
        } else {
            ciphertext[i] = currentChar;
        }
    }

    ciphertext[textLen] = '\0';
}

void decrypt(char *ciphertext, char *key, char *plaintext) {
    int textLen = strlen(ciphertext);
    int keyLen  = strlen(key);

    for (int i = 0, j = 0; i < textLen; i++) {
        char currentChar = ciphertext[i];

        if (isalpha(currentChar)) {
            char base = isupper(currentChar) ? 'A' : 'a';
            int keyShift = tolower(key[j % keyLen]) - 'a';

            plaintext[i] = (currentChar - base - keyShift + 26) % 26 + base;
            j++;
        } else {
            plaintext[i] = currentChar;
        }
    }

    plaintext[textLen] = '\0';
}

int main() {
    char plaintext[1024];
    char key[1024];
    char ciphertext[1024];
    char decrypted[1024];

    printf("Enter plaintext: ");
    fgets(plaintext, sizeof(plaintext), stdin);
    plaintext[strcspn(plaintext, "\n")] = '\0';

    printf("Enter key (alphabetic only): ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = '\0';

    encrypt(plaintext, key, ciphertext);
    printf("Encrypted text: %s\n", ciphertext);

    decrypt(ciphertext, key, decrypted);
    printf("Decrypted text: %s\n", decrypted);

    return 0;
}
```

## OUTPUT
<img width="1486" height="921" alt="image" src="https://github.com/user-attachments/assets/498c087d-758d-40f1-8bc5-e7aca1878a54" />


## RESULT
 The implement of Vigenere Cipher substitution technique using C program is successful.
