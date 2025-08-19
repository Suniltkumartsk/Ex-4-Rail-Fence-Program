# Ex-5 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

# STEP-1: 
Read the Plain text.
# STEP-2: 
Arrange the plain text in row columnar matrix format.
# STEP-3: 
Now read the keyword depending on the number of columns of the plain text.
# STEP-4: 
Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
# STEP-5: 
Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
# NAME: SUNIL KUMAR T
# REG: 212223240164

#include <stdio.h>
#include <string.h>

int main() {
    char str[1000];
    int rails;

    printf("Enter a Secret Message:\n");
    fgets(str, sizeof(str), stdin);

    // remove newline char from fgets
    str[strcspn(str, "\n")] = '\0';

    int len = strlen(str);

    printf("Enter number of rails:\n");
    scanf("%d", &rails);

    if (rails <= 1 || rails >= len) {
        printf("Rails must be between 2 and message length-1.\n");
        return 1;
    }

    char rail[rails][len]; // store zig-zag
    int i, j;

    // initialize with '\n' (acts like blank space)
    for (i = 0; i < rails; i++)
        for (j = 0; j < len; j++)
            rail[i][j] = '\n';

    // zig-zag pattern
    int row = 0;  
    int dir_down = 0;  

    for (j = 0; j < len; j++) {
        rail[row][j] = str[j];

        // switch direction at top or bottom
        if (row == 0)
            dir_down = 1;
        else if (row == rails - 1)
            dir_down = 0;

        row += dir_down ? 1 : -1;
    }

    // print encrypted message
    printf("Encrypted Message: ");
    for (i = 0; i < rails; i++)
        for (j = 0; j < len; j++)
            if (rail[i][j] != '\n')
                printf("%c", rail[i][j]);
    printf("\n");

    return 0;
}
```



# OUTPUT

<img width="811" height="311" alt="image" src="https://github.com/user-attachments/assets/b9f9f556-bf80-45d0-8b47-97326d0e4d81" />

# RESULT
The program is executed successfully
