#include<stdio.h>
#include<stdlib.h>
#include<string.h>

int main() 
{
    char s[50],c[50];
    int i,p;
    int key;
    printf("enter the text to be ciphered\n");
    scanf("%[^\n]s",s);
    printf("enter the key value\n");
    scanf("%d",&key);
    p = strlen(s);
    for(i = 0 ;i< p ;i++)
    {
        if(s[i] >= 'a' && s[i] <= 'z')
        {
            c[i] = 'a' + (s[i] - 'a' + key)%26;
        }
        else if(s[i] >= 'A' && s[i] <= 'Z')
        {
            c[i] = 'A' + (s[i] - 'A' + key)%26;
        }
        else if(s[i] >= '0' && s[i] <= '9')
        {
            c[i] = '0' + (s[i] - '0' + key)%26;
        }
    }
    printf("%s",c);
}