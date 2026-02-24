# Python 알고리즘 패턴 요약

## 1. 투 포인터
사용 조건:
- 정렬된 배열
- 구간 합/쌍 찾기

핵심:
- `left`, `right`를 이동하며 상태를 줄여간다

```python
def two_sum_sorted(arr, target):
    left, right = 0, len(arr) - 1
    while left < right:
        s = arr[left] + arr[right]
        if s == target:
            return left, right
        if s < target:
            left += 1
        else:
            right -= 1
    return -1, -1
```

## 2. BFS (최단 거리/레벨 탐색)
사용 조건:
- 그래프/격자에서 최소 이동 횟수

```python
from collections import deque

def bfs(start, graph):
    dist = {start: 0}
    q = deque([start])
    while q:
        cur = q.popleft()
        for nxt in graph[cur]:
            if nxt in dist:
                continue
            dist[nxt] = dist[cur] + 1
            q.append(nxt)
    return dist
```

## 3. DFS + 백트래킹
사용 조건:
- 조합/순열/경로 전수 탐색

핵심:
- 선택 -> 재귀 -> 복구(undo)

## 4. DP
사용 조건:
- 중복 부분 문제
- 점화식 정의 가능

체크 포인트:
- 상태 정의가 명확한가
- 점화식이 이전 상태만 참조하는가
- 초기값(base case)이 올바른가

## 실전 메모
- 구현 문제는 "조건 분기표" 먼저 작성
- 시간복잡도는 루프 겹수로 빠르게 추정
- 제출 전 엣지케이스(빈 입력, 최소/최대 범위) 확인

