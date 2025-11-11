#include <stdio.h>
#include <string.h>
#include <stdbool.h>

void railFenceEncrypt(char text[], int key, char result[]) {
    int len = strlen(text);
    char rail[key][len];
    memset(rail, '\n', sizeof(rail));

    bool dir_down = false;
    int row = 0, col = 0;

    for (int i = 0; i < len; i++) {
        if (text[i] == '\n') continue; // skip newline from fgets
        if (row == 0 || row == key - 1)
            dir_down = !dir_down;
        rail[row][col++] = text[i];
        row += dir_down ? 1 : -1;
    }

    printf("\nRail Fence Zigzag Pattern:\n");
    for (int i = 0; i < key; i++) {
        for (int j = 0; j < col; j++) {
            if (rail[i][j] == '\n')
                printf("  ");
            else
                printf("%c ", rail[i][j]);
        }
        printf("\n");
    }

    int idx = 0;
    for (int i = 0; i < key; i++)
        for (int j = 0; j < col; j++)
            if (rail[i][j] != '\n')
                result[idx++] = rail[i][j];
    result[idx] = '\0';
}

int main() {
    char text[200];
    int key;
    char cipher[200];

    printf("Enter the plaintext (you can type a full sentence):\n");
    fgets(text, sizeof(text), stdin); // reads full line with spaces

    printf("Enter the key: ");
    scanf("%d", &key);

    railFenceEncrypt(text, key, cipher);

    printf("\nCiphertext: %s\n", cipher);

    return 0;
}


#include <stdio.h>
#include <string.h>

void columnarEncrypt(char text[], int key[], int keySize, char result[]) {
    int len = strlen(text);
    int numRows = (len + keySize - 1) / keySize;
    char grid[numRows][keySize];
    int k = 0;

    // Fill grid with text and pad with 'X'
    for (int i = 0; i < numRows; i++) {
        for (int j = 0; j < keySize; j++) {
            if (k < len)
                grid[i][j] = text[k++];
            else
                grid[i][j] = 'X';
        }
    }

    // Display grid (allocation pattern)
    printf("\nColumnar Transposition Grid:\n");
    for (int i = 0; i < numRows; i++) {
        for (int j = 0; j < keySize; j++) {
            printf("%c ", grid[i][j]);
        }
        printf("\n");
    }

    // Read columns by key order
    int idx = 0;
    for (int col = 1; col <= keySize; col++) {
        for (int j = 0; j < keySize; j++) {
            if (key[j] == col) {
                for (int i = 0; i < numRows; i++) {
                    result[idx++] = grid[i][j];
                }
            }
        }
    }
    result[idx] = '\0';
}

int main() {
    char text[] = "HELLOWORLD";
    int key[] = {4, 3, 1, 2, 5}; // permutation key
    char cipher[100];

    printf("Plaintext: %s\n", text);

    columnarEncrypt(text, key, 5, cipher);

    printf("\nCiphertext: %s\n", cipher);

    return 0;
}