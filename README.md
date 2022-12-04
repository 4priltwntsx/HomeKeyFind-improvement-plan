
# 📋 알고리즘 적용을 통한 홈키파 개선 기획안
#### 🔎 **프로젝트 명**

🏚 **홈키파 (HomeKey파)** : Home을 Keyword로 파인드(FIND)!!

 #### 🔎 **프로젝트 일정**

 - 2022-10-12

#### 🔎 **팀원**

- [손민혁](https://github.com/sonmh79)
- [김지희](https://github.com/4priltwntsx)

## 📢  홈키파 서비스 소개

 - 전국 주택 거래 정보를 원하는 조회 조건에 따라 사용자에게 결과 데이터를 제공한다. 
 

 - 관심지역의 주변 인프라 정보 제공.


## 📌 개선 방법

- 로그인/회원가입 시 **해시 함수**를 사용하는 알고리즘을 적용한다.

- **너비우선탐색(BFS)** 을 사용해 해당 매물의 일정 반경 이내 사용자가 찾는 시설의 개수를 찾아 보여준다.

- 조회 결과를 보여줄 때 **퀵 정렬**을 이용해 정렬의 효율성을 높인다.

- **브루트포스 알고리즘**과 **백트래킹**을 이용해 매물을 보러 가기 위한 최단 경로 추천해준다. 

## 💡 적용 알고리즘 및 서비스 개발 개요

#### 해시 알고리즘(Hash Algorithm)

- 회원가입 시, 사용자의 비밀번호를 `해시 함수` 로 변환하여 해시값을 안전하게 DB에 저장한다. 로그인 시, 입력받은 비밀번호를 해시함수로 변환해 DB에 저장된 해시값과 일치 여부를 확인한다. 하지만! 동일한 입력 값에 대해 항상 동일한 해시 값을 반환한다는 취약점이 있다. 따라서, `Salt`(입력 값에 랜덤 문자열을 추가하여 해시 함수에 넣는 방법)와 `Key Stretching` (해시 동작을 N번 반복하는 작업) 기법을 적용하여 보완한다.

#### 너비우선탐색(BFS)

- 너비우선탐색은 루트 노드(혹은 다른 임의의 노드)에서 시작해서 인접한 노드를 먼저 탐색하는 방법이다.
사용자로부터 입력받은 반경 정보와 키워드를 이용해 각 매물을 기준으로 일정 반경 이내 키워드에 해당하는 주변 시설의 개수를 센다. 매물과 주변 시설의 위도와 경도를 유클리드 거리로 계산 후, km로 단위로 변환하여 제한 반경 내의 있는 주변 시설을 `너비우선탐색` 알고리즘을 이용해 개수를 센다.

#### 퀵 정렬(Quick Sort)

- `퀵 정렬` 알고리즘이란 하나의 리스트를 피벗(pivot)을 기준으로 두 개의 비균등한 크기로 분할하고 분할된 부분 리스트를 정렬한 다음, 두 개의 정렬된 부분 리스트를 합하여 전체가 정렬된 리스트가 되게 하는 방법이다. 분할 정복 알고리즘의 하나로, 평균적으로 매우 빠른 수행 속도를 자랑하는 정렬 방법이다.
사용자로부터 입력받은 기준으로 오름차순 또는 내림차순 정렬을 해서 보여준다. 

- 최초 조회 시, 사용자가 입력한 기준으로 정렬하고, 키워드를 입력해 검색 시, 너비우선탐색으로 탐색한 주변시설의 개수를 기준으로 내림차순 정렬하여 보여준다. 결과적으로, 사용자는 일정 반경 이내의 주변 시설이 많이 위치한 매물을 먼저 볼 수 있다.

#### 브루트포스(Brute Force), 백트래킹(Backtracking)

- `브루트포스` 는 가능한 모든 경우의 수를 모두 탐색하면서 요구조건에 충족되는 결과만을 가져오는 완전탐색 알고리즘이다. 그 중 하나인 `깊이우선탐색(DFS)` 을 사용해서 사용자에게 입력받은 노드들을 모두 탐색하며 가중치의 합이 최소가 되는 경로를 찾는다. 그 과정에서 `백트래킹` 을 사용해 탐색 효율성을 높인다. 가중치는 교통량과 거리, 비용 등을 고려하여 계산한다.

## 🧩출처

https://gmlwjd9405.github.io/2018/08/15/algorithm-bfs.html


https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiXxaD6k9r6AhUhnFYBHejNCukQFnoECBAQAw&url=https%3A%2F%2Fko.wikipedia.org%2Fwiki%2F%25ED%2595%25B4%25EC%258B%259C_%25ED%2595%25A8%25EC%2588%2598&usg=AOvVaw19Fbsp9s5DeISkCDfUkx7b

https://hcr3066.tistory.com/26
