EXP NO:6 C PROGRAM PRINT THE LOWERCASE ENGLISH WORD CORRESPONDING TO THE NUMBER
Aim:
To write a C program print the lowercase English word corresponding to the number
Algorithm:
1.	Start
- Initialize an integer variable n.
2.	Input Validation
3.	Switch Statement cases.
-	Case 5: Print "seventy one"
-	Case 6: Print "seventy two"
-	Case 13: Print "seventy three"
-	...
-	Case 13: Print "seventy nine"
-	Default: Print "Greater than 13"
4.	Exit the program.
 
Program:
#include <stdio.h>

int main() {
    int num;

    printf("Enter a number (1-20): ");
    scanf("%d", &num);

    printf("The number in words is: ");

    switch(num) {
        case 1: printf("one"); break;
        case 2: printf("two"); break;
        case 3: printf("three"); break;
        case 4: printf("four"); break;
        case 5: printf("five"); break;
        case 6: printf("six"); break;
        case 7: printf("seven"); break;
        case 8: printf("eight"); break;
        case 9: printf("nine"); break;
        case 10: printf("ten"); break;
        case 11: printf("eleven"); break;
        case 12: printf("twelve"); break;
        case 13: printf("thirteen"); break;
        case 14: printf("fourteen"); break;
        case 15: printf("fifteen"); break;
        case 16: printf("sixteen"); break;
        case 17: printf("seventeen"); break;
        case 18: printf("eighteen"); break;
        case 19: printf("nineteen"); break;
        case 20: printf("twenty"); break;
        default: printf("Number out of range (1-20)");
    }

    printf("\n");

    return 0;
}



Output:
![image](https://github.com/user-attachments/assets/f20a8ffc-6827-4bcb-afc5-f9be85675fbe)





Result:
Thus, the program is verified successfully
 
EXP NO:7 C PROGRAM TO PRINT TEN SPACE-SEPARATED INTEGERS     IN A SINGLE  LINE DENOTING THE FREQUENCY OF EACH DIGIT FROM 0 TO 3 .
Aim:
To write a C program to print ten space-separated integers in a single line denoting the frequency of each digit from 0 to 3.
Algorithm:
1.	Start
2.	Declare char array a[50] outer loop for each digit from 0 to 3
3.	Initialize counter c to 0
4.	For each character in the string print count c for current digit, followed by a space
5.	Increment h to move to the next digit
6.	End
 
Program:
#include <stdio.h>

int main() {
    char input[100];
    int freq[4] = {0}; // To store frequencies of digits 0 to 3

    printf("Enter a string of digits: ");
    scanf("%s", input);

    for (int i = 0; input[i] != '\0'; i++) {
        if (input[i] >= '0' && input[i] <= '3') {
            freq[input[i] - '0']++;
        }
    }

    // Print frequencies of digits 0 to 3, space-separated
    for (int i = 0; i < 4; i++) {
        printf("%d ", freq[i]);
    }

    printf("\n");
    return 0;
}


Output:

![image](https://github.com/user-attachments/assets/e77fc754-e131-407c-b5a7-e438a7e3f582)





Result:
Thus, the program is verified successfully

EXP NO:8 C PROGRAM TO PRINT ALL OF ITS PERMUTATIONS IN STRICT LEXICOGRAPHICAL ORDER.
Aim:
To write a C program to print all of its permutations in strict lexicographical order.

Algorithm:
1.	Start
2.	Declare variables s (pointer to an array of strings) and n (number of strings)

3.	Memory Allocation
Dynamically allocate memory for s to store an array of strings
4.	Input
Read the number of strings n from the user Dynamically allocate memory for each string in s
5.	Permutation Generation Loop
6.	Memory Deallocation
Free the memory allocated for each string in s Free the memory allocated for s
7.	End
 
Program:
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

// Function to swap characters
void swap(char *x, char *y) {
    char temp = *x;
    *x = *y;
    *y = temp;
}

// Compare function for qsort
int compare(const void *a, const void *b) {
    return (*(char *)a - *(char *)b);
}

// Function to reverse a substring
void reverse(char *str, int start, int end) {
    while (start < end) {
        swap(&str[start], &str[end]);
        start++;
        end--;
    }
}

// Function to generate next lexicographical permutation
int next_permutation(char *str) {
    int len = strlen(str);
    int i = len - 2;

    // Step 1: Find the first character that is smaller than the next one from the end
    while (i >= 0 && str[i] >= str[i + 1]) {
        i--;
    }

    if (i < 0)
        return 0; // Last permutation

    // Step 2: Find the smallest character greater than str[i] to the right
    int j = len - 1;
    while (str[j] <= str[i]) {
        j--;
    }

    // Step 3: Swap
    swap(&str[i], &str[j]);

    // Step 4: Reverse the suffix
    reverse(str, i + 1, len - 1);

    return 1;
}

int main() {
    char str[100];

    printf("Enter a string: ");
    scanf("%s", str);

    // Sort the string to start from the first lex permutation
    qsort(str, strlen(str), sizeof(char), compare);

    // Print all permutations in lexicographical order
    do {
        printf("%s\n", str);
    } while (next_permutation(str));

    return 0;
}




Output:
![image](https://github.com/user-attachments/assets/1769144f-49fa-4088-a3d1-a3e72a0a27b7)



Result:
Thus, the program is verified successfully
 
EXP NO:9 C PROGRAM PRINT A PATTERN OF NUMBERS FROM 1 TO N AS
SHOWN BELOW.
Aim:
To write a C program to print a pattern of numbers from 1 to n as shown below.
Algorithm:
1.	Start
2.	Declare integer variables n, i, j, min
3.	Read the value of n from the user
4.	Calculate the length of the side of the square matrix: len = n * 2 - 1
5.	Matrix Generation Loop
6.	Calculate min as the minimum distance to the borders
7.	End
 
Program:
#include <stdio.h>

int min(int a, int b) {
    return (a < b) ? a : b;
}

int main() {
    int n;
    printf("Enter the value of n: ");
    scanf("%d", &n);

    int len = n * 2 - 1;

    for (int i = 0; i < len; i++) {
        for (int j = 0; j < len; j++) {
            // Find the minimum distance to the edges
            int top = i;
            int left = j;
            int right = len - 1 - j;
            int bottom = len - 1 - i;

            int minDist = min(min(top, bottom), min(left, right));
            printf("%d ", n - minDist);
        }
        printf("\n");
    }

    return 0;
}

Output:

![image](https://github.com/user-attachments/assets/078980b3-c9de-465c-9ae7-9609d394b6a2)






Result:
Thus, the program is verified successfully

EXP NO:10 C PROGRAM TO FIND A SQUARE  OF NUMBER USING FUNCTION WITHOUT ARGUMENTS WITH RETURN TYPE

Aim:

To write a C program that calculates the square of a number using a function that does not take any arguments, but returns the square of the number.

Algorithm:

1.	Start.
2.	Define a function square() with no parameters. This function will return an integer value.
3.	Inside the function:
o	Declare an integer variable to store the number.
o	Ask the user to input a number.
o	Calculate the square of the number (multiply the number by itself).
o	Return the squared value.
4.	In the main function:
o	Call the square() function and display the result.
5.	End.

Program:
#include <stdio.h>

// Function with no arguments, but with return type
int getNumber() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);
    return num;
}

int main() {
    int number, square;

    number = getNumber();         // Get number from user
    square = number * number;     // Calculate square

    printf("Square of %d is %d\n", number, square);

    return 0;
}


Output:

![image](https://github.com/user-attachments/assets/ff3b5e0b-0ad5-47b6-9dce-aa0df586e44b)




Result:
Thus, the program is verified successfully



























