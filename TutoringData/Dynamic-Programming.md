## :star: Dynamic Programming

### 중복되는 연산을 줄이자.

최적의 해를 구하기에 시간이 매우 많이 필요하거나 메모리 공간이 매우 많이 필요한 문제 등이 컴퓨터로도 해결하기 어려운 문제이다. 컴퓨터는 연산 속도에 한계가 잇고, 메모리 공간을 사용할 수 있는 데이터의 개수도 한정적이라는 점이 많은 제약을 발생시킨다. 그래서 우리는 **연산 속도와 메모리 공간을 최대한으로 활용할 수 있는 효율적인 알고리즘**을 작성해야 한다.

다만, 어떤 문제는 메모리 공간을 약간 더 사용하면 연산 속도를 비약적으로 증가시킬 수 있는 방법이 있다. 대표적인 방법이 `다이나믹 프로그래밍`기법으로 동적 계회법이라고 표현하기도 한다.

다이나믹 프로그래밍은 코드를 통해 설명하겠다. 대표적인 예시로는 피보나치 수열이 있다. 피보나치 수열은 이전 두 항의 합을 현재의 항으로 설정하는 특징이 있는 수열이다. 수열은 `배열`이나 `리스트`로 표현할 수 있다.

```
def fibo(x):
    if x == 1 or x == 2:
        return 1
    return fibo(x - 1) + fibo(x - 2)


print(fibo(4))
```

위에 코드는 피보나치 수열의 소스코드이다. 하지만, 소스코드를 이렇게 작성하면 심각한 문제가 생길 수 있다. 바로 f(n) 함수에서 n이 커지면 커질수록 수행 시간이 기하급수적으로 늘어나기 때문이다. 이 소스코드의 시간복잡도는, 엄밀히 말하면 피보나치 수열의 정확한 시간복잡도는 O(2<sup>N</sup>)의 지수 시간이 소요된다고 표현한다.

이처럼 피보나치 수열의 점화식을 재귀 함수를 사용해 만들 수는 있지만, 단순히 매번 계산하도록 하면 문제를 효율적으로 해결할 수 없다. 이러한 문제는 다이나믹 프로그래밍을 사용하면 효율적으로 해결할 수 있다. 다만 항상 다이나믹 프로그래밍을 사용할 수는 없으며, 다음 조건을 만족할 때 사용할 수 있다.

- 큰 문제를 작은 문제로 나눌 수 있다.
- 작은 문제에서 구한 정답은 그것을 포함하는 큰 문제에서도 동일하다.

피보나치 수열은 이러한 조건을 만족하는 대표 문제이다. 이 문제를 `메모이제이션` 기법을 사용해서 해결할 수 있다. 메모이제이션 기법은 다이나믹 프로그래밍을 구현하는 방법 중 한 종류로, **한 번 구한 결과를 메모리 공간에 메모해두고 같은 식을 다시 호출하면 메모한 결과를 그대로 가져오는 기법**을 의미한다. 메모이제이션은 값을 저장하는 방법이므로 `캐싱`이라고도 한다.

```
def fibo(x):
    if x == 1 or x == 2:
        return 1
    if array[x] != 0:
        return array[x]
    array[x] = fibo(x - 1) + fibo(x - 2)
    return array[x]


array = [0] * 100
print(fibo(99))
```

정리를 하자면, 다이나믹 프로그래밍이란 큰 문제를 작게 나누고, 같은 문제라면 한 번씩만 풀어 문제를 효율적으로 해결하는 알고리즘 기법이다. 하지만 위의 코드처럼 재귀함수를 이용하여 코드를 작성하면 `오버헤드`가 발생할 수 있다. 따라서 재귀 함수 대신에 `반복문`을 사용하여 오버헤드를 줄일 수 있다. 일반적으로 반복문을 이용한 다이나믹 프로그래밍이 더 성능이 좋기 때문이다.

```
array = [0] * 100

array[1] = 1
array[2] = 1
n = 99

for i in range(3, n + 1):
    array[i] = array[i - 1] + array[i - 2]
print(array[n])
```

이처럼 재귀 함수를 이용하여 다이나믹 프로그래밍 소스코드를 작성하는 방법을, 큰 문제를 해결하기 위해 작은 문제를 호출한다고 하여 `탑다운 방식`이라고 말한다. 반면에 단순히 반복문을 이용하여 소스코드를 작성하는 경우 작은 문제부터 차근차근 답을 도출한다고 하여 `보텀업 방식`이라고 말한다. 완전 탐색 알고리즘으로 접근했을 때 시간이 매우 오래걸리면 다이나믹 프로그래밍을 적용할 수 있는지 해결하고자 하는 부분 문제들의 중복 여부를 확인해보자.