#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int checkPrime(int n)
{
    int i, m = n / 2;
    for (i = 2; i <= m; i++)
    {
        if (n % i == 0)
        {
            return 0;
        }
    }
    return 1;
}
int findGcd(int a, int b)
{
    int i, gcd;
    for (i = 1; i <= a && i <= b; i++)
    {
        if (a % i == 0 && b % i == 0)
        {
            gcd = i;
        }
    }
    return gcd;
}
int powMod(int a, int b, int n)
{
    long long int x = 1, y = a;
    while (b > 0)
    {
        if (b % 2 == 1)
            x = (x * y) % n;
        y = (y * y) % n;
        b = b / 2;
    }
    return x % n;
}
int main()
{
    int p, q;
    int n, phin;
    int data, cipher, decipher;
    while (1)
    {
        printf("Enter two prime numbers: ");
        scanf("%d %d", &p, &q);
        if(!(checkPrime(p))&&(checkPrime(q))){
            printf("Both are not prime\n");
        }
        else if (!checkPrime(p))
        {
            printf("p is not prime number\n");
        }
        else if (!checkPrime(q))
        {
            printf("q is not prime number\n");
        }
        else
        {
            break;
        }
    }
    printf("p:%d and q:%d \n",p,q);
    n = p * q;
    phin = (p - 1) * (q - 1);
    int e = 0;
    for (e = 5; e <= 100; e++)
    {
        if (findGcd(phin, e) == 1)
        {
            break;
        }
    }
    int d = 0;
    for (d = e + 1; d <= 100; d++)
    {
        if ((d * e) % phin == 1)
        {
            break;
        }
    }
    printf("value of e: %d\nvalue of d: %d\n", e, d);
    printf("Enter the data to be encrypted: ");
    scanf("%d", &data);
    cipher = powMod(data, e, n);
    printf("Encryption: %d\n", cipher);
    decipher = powMod(cipher, d, n);
    printf("Decryption: %d\n", decipher);
    return 0;
}
