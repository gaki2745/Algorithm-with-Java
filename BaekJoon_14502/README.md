# 14502 연구소


## 접근법

> BFS를 이용해 BackTracking 을 통한 완전탐색

- temp: 3개의 벽을 세웠을때의 임시 배열, spreadLab: bfs를 위한 temp의 배열 카피

- 벽 3개를 완전 탐색을 통해 모든 0 인곳의 경우의 수를 구한다.

```java
wallSetting(int cnt) {
  if(cnt == 3)
    //벽이 3개가 정해졌으므로 bfs 수행
 	bfs();
  
  //완전 탐색을 통해 벽3개를 구하는 경우의 수를 재귀로 구현
  if(map[i][j] == 0)
  	temp[i][j] = 1;
 	wallSetting(cnt + 1);
  	//완전 탐색을 위해 해당 구역을 다시 0 으로 초기화 한뒤 재귀 반복
  	temp[i][j] = 0;
}
```

- Queue를 이용한 BFS를 통해 바이러스를 퍼뜨린 후 값을 구하고 최종값과 Max값을 구한다.

## 개선방향

> 벽 3개를 세우는 방법이 완전 탐색 밖에 없는지 확인 해보고, 3개의 벽을 선정 후 세울때 최소의 시간이 걸리는 방법 모색하기

