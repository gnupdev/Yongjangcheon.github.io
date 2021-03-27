---
title: "Coding-Test"  
excerpt: "주식가격 | Programmers"  
categories:  
- Coding Test

tags:
- [Coding Test]

toc: true  
toc_sticky: true  

date: 2021-03-28  
last_modified_at: 2021-03-28  
---

## 1. 주식가격 (Programmers)  
## 2. 문제정의
### 주식을 매수한 각 지점마다 몇 초 동안 가격이 유지 되었는지를 파악하자.
## 3. 문제분석
배열의 길이 : 주어진 시간  
배열의 값 : 해당 시점에서의 매수 가격

1초 : 1원에 아르고를 매수 -> 이후 4초간 익  
2초 : 2원에 아르고를 매수 -> 이후 3초간 익  
3초 : 3원에 아르고를 매수 -> 이후 1초간 익 ( 1초후 값이 떨어지므로 1초간 값이 유지된 것으로 파악)  
4초 : 2원에 아르고를 매수 -> 이후 1초간 익  
5초 : 3원에 아르고를 매수 -> 이후 0초간 익

입출력 예시  
|Prices|return|
|------|------|
|[1, 2, 3, 2, 3]|[4, 3, 1, 1, 0]|

### 4. 풀이

* Bubble Sort를 이용해서 시점 이후에 떨어지는 구간을 탐색
* 가격이 떨어지면 Break, 떨어지는 시점까지를 유지된 것으로 파악하기에 +1초
* 가격이 떨어지지 않으면 +1초
* 마지막 시점은 반드시 0초

### 5. Source Code
'''c++
#include <string>  
#include <vector>  
using namespace std;

vector<int> solution(vector<int> prices) {
    vector<int> answer(prices.size());
    int temp = 0;
    for(int i=0; i < prices.size() - 1; i++){
        for(int j=i+1; j < prices.size(); j++){
            if(prices[i] <= prices[j]){
                temp++;
            }
            else {
                temp++;
                break;
            }
        }
        answer[i] = temp;
        temp = 0;
    }
    
    return answer;
}

'''


