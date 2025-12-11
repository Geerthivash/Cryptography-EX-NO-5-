# Ex-5 Rail-Fence-Program
```
GEERTHIVASH J.D. - 212223060067
```

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>

int main() {
    char text[200], rails[10][200] = {0};
    int key, row = 0, dir = 1, i;

    printf("Enter text: ");
    scanf("%[^\n]", text);

    printf("Enter rails (key): ");
    scanf("%d", &key);

    for (i = 0; text[i] != '\0'; i++) {
        int len = strlen(rails[row]);
        rails[row][len] = text[i];
        rails[row][len+1] = '\0';

        if (row == 0) dir = 1;
        else if (row == key-1) dir = -1;
        row += dir;
    }

    printf("Cipher: ");
    for (i = 0; i < key; i++)
        printf("%s", rails[i]);
    printf("\n");

    return 0;
}


```
# OUTPUT
<img width="637" height="276" alt="image" src="https://github.com/user-attachments/assets/740aa782-3717-42a0-ae9c-a9558a54ec7e" />

# RESULT
Thus the implementation of Rail fence programhad been executed successfully.
