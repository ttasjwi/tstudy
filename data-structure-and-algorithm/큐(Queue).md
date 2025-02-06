# 큐(Queue)

---

### 큐(Queue)
- 시퀀스의 한쪽 끝에는 엔티티를 추가하고, 다른 반대쪽 끝에는 제거할 수 있는 엔티티 컬렉션
- 선입 선출(First-In, First-Out)
- 구현 방법
  - 연결 리스트
  - 배열
- 주 사용처
  - 너비우선 탐색(BFS: Breadth-First Search)
  - 캐시

---

### Python 에서
- Python
```python
from collections import deque

q = deque()
q.append(1) # 맨 뒤 추가
q.append(2)
q.append(3)
print(q[-1]) # 맨끝 (3)
print(q[0]) # 맨앞 (1)
print(q.popleft()) # 맨 앞 꺼내기 (1)
print(q.pop()) # 맨뒤 꺼내기 (3)

q.appendleft(4) # 맨 앞 추가
print(q[0]) # 맨 앞(4)
```

---
