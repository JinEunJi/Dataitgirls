# Palindrome과 홀,짝 정렬

#### C

문제 : 문자열을 받아 문자열이 palindrome인지 판별하라(True/False)

 - 입력: 임의의 길이의 str
 - 출력: bool. 문자열이 palindrome인지의 여부
 - **palindrome: 180도 뒤집었을 때 원 문자열과 같아지는 문자열.** 예) 기러기, racecar 등
 - 정의상 빈 문자열('')도 palindrome이라고 할 수 있음.• 데이터 가공하기

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

bool palindrome(char* s) {

	int j = strlen(s);
	for (int i = 0; i < strlen(s) / 2; i++) {
		if (s[i] != s[j-1]) {
			printf("X\n");
			return false;
		}
		j--;
	}
	printf("O\n");
	return true;
}
int main()
{
	char *s1 = malloc(sizeof(char) * 100);    
	printf("문자열을 입력하세요: ");
	scanf("%s", s1);      
	palindrome(s1);
	free(s1);   
	return 0;
}
```



문제 : 정수가 마구잡이로 들어있는 리스트를 오름차순 정렬하되, **홀수가 짝수보다 무조건 앞서게 정렬하라**

 - 입력: 정수 많이 있는 list. 길이는 1,000,000 이하
 - 출력: 정렬된 리스트. 단 홀수가 짝수보다 무조건 앞서야 함.
 - 예) [7, 2, 3, 5, 4, 1]    ->    [1, 3, 5, 7, 2, 4]

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main()
{
	int list[6];
	int size = sizeof(list) / sizeof(list[0]);
	int i,j,k,even=0;
	
	for (i = 0; i < size; i++)
		scanf("%d", &list[i]);

	for (i = 0; i < size; i++)
		if (list[i] % 2 == 0)
			even++;

	for (i = 0; i < size; i++) {
		for (j = 1; j < size-i; j++) {
			if (list[j-1]%2==0) {
				k = list[j-1];
				list[j-1] = list[j];
				list[j] = k;
			}
		}
	}

	for (i = 0; i < size-even; i++) {
		for (j = 1; j < size-even-i; j++) {
			if (list[j] < list[j - 1]) {
				k = list[j];
				list[j] = list[j - 1];
				list[j - 1] = k;
			}
		}
	}

	for (i = 0; i < even; i++) {
		for (j = size-even + 1; j < size - i; j++) {
			if (list[j] < list[j - 1]) {
				k = list[j];
				list[j] = list[j - 1];
				list[j - 1] = k;
			}
		}
	}

	for (int z = 0; z < size; z++)
		printf("%d ", list[z]);
	return 0;
}
```

