# National Institute of Technology,Silchar
## Mini Project-1
### Data Structures
### Course Code:CS 201

#### "C program for Large Fibonacci Number"




      #include <stdio.h>
      #include <string.h>

        int char_int(const char *s, int in)
     {
    if (in < strlen(s))
        return s[strlen(s) - in - 1] - 48;
    return 0;
     }
     char out[1000000] = "0";
     char a[100000] = "0";
     char b[100000] = "1";
   
     int main()
    {
    int n;
    printf("enter n: \n");
    scanf("%d", &n);
    if (n == 0)
        printf("%s", a);
    else if (n == 1)
        printf("%s", b);
      else
    {
        for (int j = 2; j <= n; j++)
        {
            int i, la = strlen(a), lb = strlen(b), x, sum, carry = 0;
            x = la > lb ? la : lb;
            for (i = 0; i < x; i++)
            {
                int a_c = char_int(a, i);
                int b_c = char_int(b, i);
                sum = a_c + b_c + carry;
                carry = 0;
                if (sum > 9)
                {
                    carry = 1;
                    sum = sum - 10;
                }
                out[i] = sum + 48;
             }
              if (carry)
                  out[i++] = carry + 48;

            for (i = 0; i < strlen(out) / 2; i++)
            {
                char t = out[i];
                out[i] = out[strlen(out) - i - 1];
                out[strlen(out) - i - 1] = t;
            }
            for (int i = 0; b[i] != '\0'; i++)
                a[i] = b[i];
            for (int i = 0; out[i] != '\0'; i++)
                b[i] = out[i];
        }
    }
    printf("Fibonacci number \n");
    printf("%s", out);
}
