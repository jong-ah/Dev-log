# 벨만-포드 알고리즘

다익스트라 알고리즘과 같은 단일 시작점 최단 경로 알고리즘

<br>

### 다익스트라 알고리즘과 차이점

1. 음수 간선이 있는 그래프에 대해서도 최단 경로를 찾을 수 있다.
2. 음수 싸이클이 있어 최단거리가 제대로 정의되지 않은 경우에도 찾을 수 있다.
- 음의 가중치는 허용하지만 가중치의 합이 음인 사이클은 허용하지 않다.
- 사이클의 합이 음수인 경우가 존재하는 경우 이를 발견하여 알려 줄 수 있다.

<br>

### 동작 과정

1. 시작점 → 시작점까지의 최단거리는 0이다. dist[start] = 0;
2. 나머지 원소들은 아주 큰 수(Number.MAX_SAFE_INTEGER)로 초기화한다.
3. u → v 최단 거리의 특성 : dist[v] <= dist[u] + w(u,v)
:: start → v까지의 최단거리는, start → u까지의 최단거리 + 가중치보다 클 수 없다.
4. dist[to] <= dist[from] + weight은 항상 성립한다.

<br>

### 시간 복잡도 : O(V * E) 

<br>

```
// 그래프 구현이 필요없는 알고리즘: O(V * E)
// V는 정점의 개수, E는 간선의 개수
function BellmanFord(num, edges, start) {
  const INF = Number.MAX_SAFE_INTEGER;
  const dist = Array(num + 1).fill(INF);
  dist[start] = 0;

  for (let v = 1; v <= num - 1; v++) {
    edges.forEach((e) => {
      const [src, dst, weight] = e;
      // 최단경로의 부분 경로 역시 최단경로이다.
      // dist[dst], 즉 start에서 dst까지의 최단 경로는
      //  1) 중간에 거쳐서 갈 수 있는 경로가 존재하고 (dist[src] !== INF)
      //  2) 그 경로를 통해서 가는 방법이 보다 짧으면,
      //     즉 start에서 src까지 갔다가 (dist[src]), src에서 dst까지 가는 (weight) 방법이 더 짧으면,
      // 해당 방법으로 갱신(update)한다.
      if (dist[src] !== INF && dist[src] + weight < dist[dst]) {
        dist[dst] = dist[src] + weight;
      }
    });
  }

  // 음의 사이클이 존재하는지 확인하고
  // 존재하면 빈 배열을 리턴한다.
  const hasNegCycle = edges.some((e) => {
    const [src, dst, weight] = e;
    if (dist[src] !== INF && dist[src] + weight < dist[dst]) {
      return true;
    }
  });

  return hasNegCycle ? [] : dist.slice(1);
}

let num = 5;
let edges = [
  [1, 2, -1],
  [1, 3, 4],
  [2, 3, 3],
  [2, 4, 2],
  [2, 5, 2],
  [4, 2, 1],
  [5, 4, -3],
];
let start = 1;
let output = BellmanFord(num, edges, start);
console.log(output); // --> [0, -1, 2, -2, 1]
```

<br>

### 참고자료

- [최단 경로(Shortest Path) 2 - 벨만-포드 알고리즘(Bellman-Ford Algorithm)](https://www.apexcel.blog/algorithm/graph/shortest-path/bellman-ford/)
- [벨만-포드 알고리즘](https://projooni.tistory.com/entry/%EB%B2%A8%EB%A7%8C%ED%8F%AC%EB%93%9C-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98)
- [다익스트라 알고리즘](https://www.zerocho.com/category/Algorithm/post/584bd46f580277001862f1af)
