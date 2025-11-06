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
#include <ctype.h>

int main() {
    char text[200];
    int rails;

    printf("Enter the plain text: ");
    fgets(text, sizeof(text), stdin);
    text[strcspn(text, "\n")] = '\0'; 

    char clean[200];
    int k = 0;
    for (int i = 0; text[i]; i++) {
        if (isalpha((unsigned char)text[i])) {
            clean[k++] = toupper((unsigned char)text[i]);
        }
    }
    clean[k] = '\0';

    printf("Enter number of rails: ");
    scanf("%d", &rails);

    int len = strlen(clean);
    char rail[rails][len];

    for (int i = 0; i < rails; i++)
        for (int j = 0; j < len; j++)
            rail[i][j] = '\n';

    int row = 0;
    int dir_down = 0; 

    for (int i = 0; i < len; i++) {
        rail[row][i] = clean[i];
        if (row == 0 || row == rails - 1)
            dir_down = !dir_down;
        row += dir_down ? 1 : -1;
    }

    printf("\nCipher text: ");
    for (int i = 0; i < rails; i++) {
        for (int j = 0; j < len; j++) {
            if (rail[i][j] != '\n')
                printf("%c", rail[i][j]);
        }
    }

    printf("\n");
    return 0;
}

```
# OUTPUT
<img width="637" height="276" alt="image" src="https://github.com/user-attachments/assets/740aa782-3717-42a0-ae9c-a9558a54ec7e" />

# RESULT
Thus the implementation of Rail fence programhad been executed successfully.
