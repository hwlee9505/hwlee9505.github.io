---
layout: default
title: CodeUp 1930
parent: Algorithm
nav_order: 13
---

# CodeUp 1930 SuperSum(재귀 함수), 완벽 해결 X
{: .no_toc }

---

## 문제 설명

SuperSum 함수는 다음과 같이 정의된다.  
SuperSum(0,n)=n (n은  모든 양의 정수)  
SuperSum(k,n)=SuperSum(k−1,1)+SuperSum(k−1,2)+...+SuperSum(k−1,n)  
k와 n이 여러개 주어진다. SuperSum의 값을 각각 출력하시오.  

## 입력

k(1<=k<=14)와 n(1<=n<=14)이 입력된다. 입력의 끝은 EOF(End Of File) 이다.  
입력 처리 방법)  
while( scanf("%d %d", &k, &n) != EOF )  
	printf("%d\n", SuperSum(k, n));  

## 출력

SuperSum(k,n)의 값을 각 행에 하나씩 출력한다.  

### 입력 예시

1 3  
2 3  
4 10  
10 10  

### 출력 예시

6  
10  
2002  
167960  


## 도움말

ACM-ICPC타입의 입출력방식입니다.  
입력의 개수가 몇 개인지 모릅니다. (많겠죠..?)  
재귀함수 SuperSum(k, n)를 정의하는 문제이며, 메모이제이션(Memoization) 기법을 활용하면 시간을 단축시킬 수 있습니다.  

## 해결 코드1
```yaml
#import java.io.BufferedReader;
#import java.io.InputStreamReader;
#import java.io.IOException;
#
#public class Main {
#
#    public static void main(String[] args) throws IOException {
#        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
#
#        while(true){
#            String readLine = br.readLine();
#            if(readLine == null){
#                break;
#            }
#
#            String[] temp = readLine.split("\\s");
#
#            System.out.println(superSum(Integer.parseInt(temp[0]), Integer.parseInt(temp[1])));
#        }
#    }
#
#    public static int superSum(int k, int n) {
#        int i,sum=0;
#        if (k == 0) {
#            return n;
#        }
#        else {
#            while (n != 0) {
#                sum += superSum(k - 1, n);
#                --n;
#            }
#            return sum;
#        }
#    }
#}
```