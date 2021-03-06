# 15683 감시(삼성 역량 테스트)

하드 코딩방식으로 써내려 가도 풀수 있는 문제지만 코드가 너무 가독성이 떨어지고 규칙을 생각하지 않고 짜버리니 길이가 늘어나서 재수정했다.

## 접근법

> 조건을 만족시키는 DFS

- 감시 카메라에 관한 조건

<img width="974" alt="image" src="https://user-images.githubusercontent.com/33486820/54417033-62a77280-4744-11e9-803e-ba377a116196.png">

- 감시 카메라 1~5 타입에 따른 감시 구역이 다르다.또한 감시 카메라는 회전을 할수가 있다 
- 회전을 하여 결국 4방향을 모두 확인 할 수 있지만 한번에 확인 하는 것이 다르다
- 북 동 남 서 를 각각(0,1,2,3)으로 나누고 ex) 1번 카메라: 0,1,2,3 3번 카메라: (0,1), (1,2), (2,3) (3,0) 이런식으로 한 턴에 확인 할 수 있는 감시 구역의 규칙을 파악한다
    
> 최소의 사각지대일 때의 상황 : DFS를 통해 재귀로 탐색하자

- 슈도 코드

```java
ArrayList<Camera> list;			//감시 카메라의 위치(x,y), 타입을 저장해놓는 list

//curCnt : 현재 탐색 중인 감시 카메라의 번호 , camCnt = list.size (총 캠의 개수)
void DFS(int curCam, int camCnt) {
  
  //재귀 종료 조건 > 캠을 모두 탐색 했으면 배열의 사각지대를 탐색하여 이전 값과 비교
  if(curCam == camCnt) {
  //cnt = 사각지대의 개수
  ans = Math.min(cnt, ans);
  }
  
  //list에 삽입 되어있는 curCnt 현재 캠의 위치에서 시작
  switch(curCam.type) {
      //1,2,3,4,5 타입에 따라 감시 영역을 구하고 감시했음을 나타낸 다음 DFS(curCam+1, camCnt) 호출
      
  }
}
```
- 주의 할점: 매순간 DFS를 호출할때 1,2,3,4 번 타입의 카메라의 경우에는 경우의수가 존재 하기 때문에 현재 Map의 상태를 임시 저장하고 있는 temp 배열이 필요하고 감시를 하고 난 다음 DFS를 호출하고 배열을 변경 시켜 줘야한다.


