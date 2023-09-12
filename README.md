#include <stdio.h>

int main() {
    int range_start, range_end;
    
    printf("Enter the range (start and end): ");
    scanf("%d %d", &range_start, &range_end);
    
    if (range_start < 1 || range_end < 1 || range_start >= range_end) {
        printf("Invalid range. Please enter positive integers with a valid range.\n");
        return 1;
    }
    
    printf("Amicable number pairs within the range %d to %d:\n", range_start, range_end);
    
    for (int num1 = range_start; num1 <= range_end; num1++) {
        int sum1 = 1;
        
        // Calculate the sum of proper divisors for num1
        for (int i = 2; i * i <= num1; i++) {
            if (num1 % i == 0) {
                sum1 += i;
                if (i != (num1 / i)) {
                    sum1 += (num1 / i);
                }
            }
        }
        
        if (sum1 > num1 && sum1 <= range_end) {
            int sum2 = 1;
    
            for (int i = 2; i * i <= sum1; i++) {
                if (sum1 % i == 0) {
                    sum2 += i;
                    if (i != (sum1 / i)) {
                        sum2 += (sum1 / i);
                    }
                }
            }
            
            if (sum2 == num1 && num1 != sum1) {
                printf("(%d, %d)\n", num1, sum1);
            }
        }
    }
    
    return 0;
}
