#include <stdio.h>
#include <string.h>
unsigned long long factorial(int n) {
    if (n == 0 || n == 1) return 1;
    unsigned long long result = 1;
    for (int i = 2; i <= n; i++) {
        result *= i;
    }
    return result;
}
int main() {
    char word[15];
    scanf("%s", word);
    int length = strlen(word);
    int counts[26] = {0};
    for (int i = 0; i < length; i++) {
        counts[word[i] - 'A']++;
    }
    unsigned long long total_permutations = factorial(length);
    for (int i = 0; i < 26; i++) {
        if (counts[i] > 1) {
            total_permutations /= factorial(counts[i]);
        }
    }
    printf("%llu\n", total_permutations);
    return 0;
}
