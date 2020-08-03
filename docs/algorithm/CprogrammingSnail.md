---
layout: default
title: C programming snail
parent: Algorithm
nav_order: 19
---

# 윤성우의 열혈 C 프로그래밍 (달팽이 그리기)
{: .no_toc }

---

## 문제 설명

달팽이 배열을 만들어서 이를 출력하는 프로그램을 작성하고자 한다.  
여기서 말하는 달팽이 배열은 다음과 같다.  
 
![](/assets/images/algorithm/snail.png)
 
위 그림에서 4X4의 달팽이 배열과 5X5의 달팽이 배열을 보여주고 있다.  
이 내용을 참조하여 프로그램의 사용자로부터 하나의 숫자 n을 입력 받아서 nXn의 길이에 해당하는 달팽이 배열을 출력해주는 프로그램을 작성해보자.  

## 입력

5

## 출력

1|2|3|4|5
16|17|18|19|6
15|24|25|20|7
14|23|22|21|8
13|12|11|10|9

## 해결 코드
```markdown
#include<stdio.h>

void PrintAll(int (*ptr)[100], int n) {

    int i, j;

    for (i = 0; i < n; i++) {
        for (j = 0; j < n; j++) {
            printf("%3d ", ptr[i][j]);
        }
        printf("\n");
    }
    printf("\n");
}

int main(void) {

    int arr[100][100];
    int x = 0;
    int y = -1;
    int value = 0;

    int sw = -1;    //  스위치 변수  -1 일때 밑, 왼쪽
    //            +1 일때 위 , 오른쪽
    int i, j, n;

    for (i = 0; i < n; i++) {
        for (j = 0; j < n; j++) {
            arr[i][j] = 0;
        }
    }

    printf("숫자를 입력하세요 : ");
    scanf("%d", &n);


    for (i = 0; i < n; i++) {
        value++;
        y++;
        arr[x][y] = value;
    }

    
    // 여기서 헤메었던 로직
    
    for (i = n - 1; i > 0; i--) {       //  4, 4, 3, 3, 2, 2, 1, 1

        for(j=0; j<i; j++){
            if(sw == -1){
                x++;
            }
            else{
                x--;
            }
            value++;
            arr[x][y] = value;
        }


        for(j = 0; j < i ; j++){
            if(sw == -1){
                y--;
            }else{
                y++;
            }
            value++;
            arr[x][y] = value;
        }

        sw *= -1;

    }
    
    PrintAll(arr, n);


    return 0;
}
```