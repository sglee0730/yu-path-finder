## Technologies Used

Web: ReactJS, NextJS

State management: Recoil

API: 카카오맵 API

CSS: Ant design, Sass


## About

시중에 나와있는 지도 서비스들은 캠퍼스 안에서 길을 찾을 때 정확도가 많이 떨어집니다. 특히 제 모교인 영남대는 특히 캠퍼스 면적이 매우 커 학교 외부인이나 신입생들에게는 길을 찾는 것이 쉽지 않습니다. 영남대 학생들과 학교를 방문한 외부인에게 편리한 길찾기 서비스를 제공하고자 하는게 이번 프로젝트의 목표입니다.


길을 찾아 주는 기능은 경로 탐색으로 구현하였으며 다익스트라와 A* 알고리즘을 사용해보았습니다. 다익스트라 알고리즘은 한 정점에서 모든 정점의 경로를 모두 계산하는 알고리즘으로, 여러가지 버전이 있지만 우선순위 큐를 사용하는 방식으로 구현하였습니다. 그러나 정확도를 높이려면 노드의 갯수가 100개가 넘어갈 것이라 추정되고, 다익스트라는 최단 경로를 보장해주지 않기때문에 A* 알고리즘을 채택하였습니다. 이 때 우선순위 큐를 사용한 다익스트라 알고리즘의 시간복잡도는 
```
O(|Edge| + |Vertex|log|Vertex|) 
```


A* 알고리즘 역시 여러가지 방식으로 최적화하는 방법이 있지만 저는 제일 많이 사용되는 openList와 closedList를 사용하는 방식으로 구현하였습니다. 

<a href="http://www.gisdeveloper.co.kr/?p=3897">참고한 사이트</a>

```
f(n) = g(n) + h(n)

g(n): 출발 꼭짓점으로부터 꼭짓점 n까지의 경로 가중치
h(n): 꼭짓점 n으로부터 목표 꼭짓점까지의 추정 경로 가중치
현재 n과 목표 꼭짓점의 좌표 차이를 계산하여 절대값으로 반환한다. 
```


맵API를 사용하기 때문에 Grid 상이 아닌 그래프로 표현하고자 했으며 A* 알고리즘은 대부분 Grid 상에서 구현하는 사례가 대부분이라 참고할 자료가 거의 없었습니다. 그래서 알고리즘의 이론을 보고 직접 구현하였습니다.


## Demo

현재는 샘플로 7개 Edge만 있고 직접 측정하여서 릴리즈 예정입니다.

Netlify에서 배포하려 도메인도 구입하고 ssl 인증서도 발급 받았으나, 

카카오맵 api 인증에 문제가 있어 임시로 오라클 클라우드 인스턴스에서 실행 중입니다.

https 설정되지 않아 경고가 발생해 불편을 드려 죄송합니다.

<a href="http://193.123.237.166:4321/">Demo Link</a>








