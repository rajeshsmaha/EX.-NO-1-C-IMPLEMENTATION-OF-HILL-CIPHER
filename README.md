# EX.-NO-1-C-IMPLEMENTATION-OF-HILL-CIPHER

## AIM:
To write a C program to implement the hill cipher substitution techniques.

## ALGORITHM:

STEP-1: Read the plain text and key from the user.

STEP-2: Split the plain text into groups of length three.

STEP-3: Arrange the keyword in a 3*3 matrix.

STEP-4: Multiply the two matrices to obtain the cipher text of length three.

STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM: 
```
  #include <stdio.h>
  #include <string.h>
  #include <ctype.h>
  
  #define SIZE 3
  
  void hillEncrypt(char message[], int key[SIZE][SIZE]) {
      int i, j, k;
      int msgVector[SIZE];     
      int cipherVector[SIZE]; 
      int messageLen = strlen(message);
  
      printf("Cipher Text: ");
  
      for (i = 0; i < messageLen; i += SIZE) {
        
          for (j = 0; j < SIZE; j++) {
              if (i + j < messageLen)
                  msgVector[j] = toupper(message[i + j]) - 'A';
              else
                  msgVector[j] = 'X' - 'A';  
          }
  
       
          for (j = 0; j < SIZE; j++) {
              cipherVector[j] = 0;
              for (k = 0; k < SIZE; k++) {
                  cipherVector[j] += key[j][k] * msgVector[k];
              }
              cipherVector[j] %= 26;
          }
  
          for (j = 0; j < SIZE; j++) {
              printf("%c", cipherVector[j] + 'A');
          }
      }
      printf("\n");
  }
  
  int main() {
      char message[100];
      int key[SIZE][SIZE]; 
      int i, j;
  
      scanf("%s", message);
      
      printf("Enter the message : %s\n",message);
  
      printf("Enter the 3x3 key matrix (row by row):\n");
      for (i = 0; i < SIZE; i++) {
          for (j = 0; j < SIZE; j++) {
              scanf("%d", &key[i][j]);
              printf("%d ",key[i][j]);
          }
          printf("\n");
      }
  
  
      hillEncrypt(message, key);
  
      return 0;
  }
```
## OUTPUT:
<img width="623" height="267" alt="image" src="https://github.com/user-attachments/assets/3b05d9f5-5841-4e17-a15b-653d70b37b49" />

## RESULT:
  Thus the hill cipher substitution technique had been implemented successfully.
