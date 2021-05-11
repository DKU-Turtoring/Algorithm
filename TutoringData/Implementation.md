## :star: Implementation

### 아이디어를 코드로 바꾸는 구현

- 코딩테스트에서 `구현`이란 **머릿속에 있는 알고리즘을 소스코드로 바꾸는 과정**이다. 어떤 문제를 풀든 간에 소스코드를 작성하는 과정은 필수 이므로 구현 문제 유형은 모든 범위의 코딩테스트 문제 유형을 포함하는 개념이다.

```
Problem -> Thinking -> Solution
```

- 흔히 문제 해결 분야에서 구현 유형의 문제는 **풀이를 떠올리는 것은 쉽지만 소스코드로 옮기기 어려운 문제**를 의미한다.

- `완전 탐색`은 **모든 경우의 수를 주저 없이 다 계산하는 해결 방법**을 의미하고, `시뮬레이션`은 **문제에서 제시한 알고리즘을 한 단계씩 차례대로 직접 수행**해야 하는 문제 유형을 의미한다.

- 코딩테스트 수준에서는 메모리 사용량 제한보다 더 적은 크기의 메모리를 사용해야 한다는 점 정도만 기억하자.

```
데이터 개수 : 1,000 -> 메모리 사용량 : 약 4KB
데이터 개수 : 1,000,000 -> 메모리 사용량 : 약 4MB
데이터 개수 : 10,000,000 -> 메모리 사용량 : 약 40MB
```

### 구현 문제에 접근하는 방법

- 보통 구현 유형의 문제는 사소한 입력 조건 등을 문제에서 명시해주며 문제의 길이가 꽤 긴 편이다. 

- 보통 구현 유형의 문제는 문자열 처리가 많이 나온다. 문자열 처리의 경우 `Java`나 `C`, `C++`에서는 다소 어려운 편이다. 하지만 파이썬의 강점은 문자열 처리를 정수형 처리와 동일하게 처리할 수 있다는 강력한 강점이 있다.

#### ❗️ python vs pypy

<img width="112" alt="image" src="https://user-images.githubusercontent.com/78870076/117231579-72213280-ae5a-11eb-8c17-4bdf946b2f47.png">

### 💡 상하좌우

```
여행가 A는 N x N 크기의 정사각형 공간 위에 서 있다. 이 공간은 1 x 1 크기의 정사각형으로 나누어져 있다.
가장 왼쪽 위 좌표는 (1, 1)이며, 가장 오른쪽 아래 좌표는 (N, N)에 해당한다.
여행가 A는 상, 하, 좌, 우 방향으로 이동할 수 있으며, 시작 좌표는 항상 (1, 1)이다.
우리 앞에는 여행가 A가 이동할 계획이 적힌 계획서가 놓여 있다.
계획서에는 하나의 줄에 띄어쓰기를 기준으로 하여 L, R, U, D 중 하나의 문자가 반복적으로 적혀있다.
각 문자의 의미는 다음과 같다.
    - L : 왼쪽으로 한 칸 이동
    - R : 오른쪽으로 한 칸 이동
    - U : 위로 한 칸 이동
    - D : 아래로 한 칸 이동
이때 여행가 A가 N x N 크기의 정사각형 공간을 벗어나는 움직임은 무시된다.
예를 들어 (1, 1)의 위치에서 L 혹은 U를 만나면 무시된다.

계획서가 주어졌을 때 여행가 A가 최종적으로 도착할 지점의 좌표를 출력하는 프로그램을 작성하시오. 
```

#### 입력 조건

```
- 첫째 줄에 공간의 크기를 나타내는 N이 주어진다.
- 둘째 줄에 여행가 A가 이동할 계획서 내용이 주어진다.
```

#### 입력 예시

```
5
R R R U D D
```

#### 출력 예시
```
3 4
```

### 💡 시각

```
정수 N이 입력되면 00시 00분 00초부터 N시 59분 59초까지의 모든 시각 중에서 3이 하나라도 포함되는 모든 경우의 수를 구하는 
프로그램을 작성하시오. 예를 들어 1을 입력했을 때 다음은 3이 하나라도 포함되어 있으므로 세어야 하는 시각이다.

- 00시 00분 03초
- 00시 13분 30초

반면에 다음은 3이 하나도 포함되어 있지 않으므로 세면 안 되는 시각이다.

- 00시 02분 55초
- 01시 27분 45초
```

#### 입력 조건

```
첫째 줄에 정수 N이 입력된다.
```


#### 입력 예시

```
5
```

#### 출력 예시

```
11475
```

### 💡 왕실의 나이트

```
행복 왕국의 왕실 정원은 체스판과 같은 8 x 8 좌표 평면이다. 왕실 정원의 특정한 한 칸에 나이트가 서 있다. 나이트는 매우 
충성스러운 신하로서 매일 무술을 연마한다.
나이트는 말을 타고 있기 때문에 이동을 할 때는 L자 형태로만 이동할 수 있으며 정원 밖으로는 나갈 수 없다. 나이트는 특정한 
위치에서 다음과 같은 2가지 경우로 이동할 수 있다.

    1. 수평으로 두 칸 이동한 뒤에 수직으로 한 칸 이동하기
    2. 수직으로 두 칸 이동한 뒤에 수평으로 한 칸 이동하기

이처럼 8 x 8 좌표 평면상에서 나이트의 위치가 주어졌을 때 나이트가 이동할 수 있는 경우의 수를 출력하는 프로그램을 작성하시오.
이때 왕실의 정원에서 행 위치를 표현할 때는 1부터 8로 표현하며, 열 위치를 표현할 때는 a부터 h로 표현한다.
```

#### 입력 조건

```
- 첫째 줄에 8 x 8 좌표 표면상에서 현재 나이트가 위치한 곳의 좌표를 나타내는 두 문자로 구성된 문자열이 입력된다. 입력 문자는
a1처럼 열과 행으로 이뤄진다.
```


#### 입력 예시

```
a1
```

#### 출력 예시

```
2
```

### 💡 게임 개발

```
현민이는 게임 캐릭터가 맵 안에서 움직이는 시스템을 개발 중이다.
캐릭터가 있는 장소는 1 x 1 크기의 정사각형으로 이뤄진 N x M 크기의 직사각형으로, 각각의 칸은 육지 또는 바다이다.
캐릭터는 동서남북 중 한 곳을 바라본다.
맵의 각 칸은 (A, B)로 나타낼 수 있고, A는 북쪽으로부터 떨어진 칸의 개수, B는 서쪽으로부터 떨어진 칸의 개수이다.
캐릭터는 상하좌우로 움직일 수 있고, 바다로 되어 있는 공간에는 갈 수 없다.
캐릭터의 움직임을 설정하기 위해 정해 놓은 매뉴얼은 이러하다.
    1. 현재 위치에서 현재 방향을 기준으로 왼쪽 방향 (반시계 방향으로 90도 회전한 방향)부터 차례대로 갈 곳을 정한다.
    2. 캐릭터의 바로 왼쪽 방향에 아직 가보지 않은 칸이 존재한다면, 왼쪽 방향으로 회전한 다음 왼쪽으로 한 칸을 전진한다.
    왼쪽 방향에 가보지 않은 칸이 없다면, 왼쪽 방향으로 회전만 수행하고 1단계로 돌아간다.
    3. 만약 네 방향 모두 이미 가본 칸이거나 바다로 되어 있는 칸인 경우에는, 바라보는 방향을 유지한 채로 한 칸 뒤로 가고 
    1단계로 돌아간다.
    
    단, 이때 뒤쪽 방향이 바다인 칸이라 뒤로 갈 수 없는 경우에는 움직임을 멈춘다.
    
현민이는 위 과정을 반복적으로 수행하면서 캐릭터의 움직임에 이상이 있는지 테스트하려고 한다.
매뉴얼에 따라 캐릭터를 이동시킨 뒤에, 캐릭터가 방문한 칸의 수를 출력하는 프로그램을 만드시오.
```

#### 입력 조건

```
- 첫째 줄에 맵의 세로 크기 N과 가로 크기 M을 공백으로 구분하여 입력한다.
- 둘째 줄에 게임 캐릭터가 있는 칸의 좌표 (A, B)와 바라보는 방향 d가 각각 서로 공백으로 구분하여 주어진다. 방향 d의 값으로는 
다음과 같이 4가지가 존재한다.
    - 0: 북쪽
    - 1: 동쪽
    - 2: 남쪽
    - 3: 서쪽
- 셋째 줄부터 맵이 육지인지 바다인지에 대한 정보가 주어진다. N개의 줄에 맵의 상태가 북쪽부터 남쪽 순서대로, 각 줄의 데이터는 
서쪽부터 동쪽 순서대로 주어진다. 맵의 외곽은 항상 바다로 되어 있다.
    - 0: 육지
    - 1: 바다
- 처음에 게임 캐릭터가 위치한 칸의 상태는 항상 육지이다.
```


#### 입력 예시

```
4 4
1 1 0
1 1 1 1
1 0 0 1
1 1 0 1
1 1 1 1
```

#### 출력 예시

```
3
```