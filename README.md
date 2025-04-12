# password-generator-c

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Function to generate a random password
void generatePassword(int length) {
    char password[length + 1];  // +1 for null terminator

    // Possible characters for the password
    char chars[] = "abcdefghijklmnopqrstuvwxyz"
                   "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
                   "0123456789"
                   "!@#$%^&*()-_=+<>?";

    int charSetLength = sizeof(chars) - 1;

    // Seed the random number generator
    srand(time(0));

    for (int i = 0; i < length; i++) {
        int index = rand() % charSetLength;
        password[i] = chars[index];
    }

    password[length] = '\0';  // Null-terminate the string

    printf("Generated Password: %s\n", password);
}

int main() {
    int length;

    printf("Enter the desired password length: ");
    scanf("%d", &length);

    if (length <= 0) {
        printf("Please enter a valid length greater than 0.\n");
        return 1;
    }

    generatePassword(length);

    return 0;
}
