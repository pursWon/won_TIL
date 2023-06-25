무한 스크롤의 원리 (Paging)
============

![스크린샷 2023-06-24 오전 9 30 31](https://github.com/pursWon/won_TIL/assets/99719661/126d7b11-7fcb-406b-8008-4b05dcf9adb3)

</br>

data source를 index 경로에서 cell에 대한 데이터 준비를 시작하도록 지시한다

</br>

→ 어려운 문장이지만, 대략 풀어보면, data를 index에 풀어서 cell이 다음에 나올 data를 보여줄 수 있게끔 하는 method라고 정의해놓았다.

</br>


tableView는 main dispatch queue에서 이 method를 호출하여 가까운 미래에 보여줄 cell에 대한 index 경로를 제공한다. 

</br>

해당 방법을 사용해서 비용이 많이 드는? (expensive) 데이터 로드 작업을 진행하세요. 항상 data를 비동기식으로 로드하고 결과를 table의 데이터 원본 객체에 전달합니다. 

</br>

⭐️ 무한 스크롤 방법

</br>

<aside>
    
</br>
➡️ perPage = 한 페이지 당 가지고 있는 객체의 수 (30개로 고정)

pageNum = 현재 페이지 넘버 

totalCount = 불러온 데이터의 총 개수

1. 불러온 데이터의 전체 페이지 수를 구한다.
    a. totalCount를 perPage로 나눈다.
    b. 나머지가 없을 경우 → 나눈 값이 전체 페이지 수
    c. 나머지가 있을 경우 → 나눈 값에 1을 더한 값이 전체 페이지 수 
        - 왜? → 나머지는 30보다 작을 수 밖에 없는데 나머지 객체들을 보여주기 위해선 30개의 객체를 보여줄 수 있는 1 페이지만이 필요하기 때문이다.
</br>
2. prefetchRowsAt()에서 pageNum이 전체 페이지 수보다 작고, 불러온 데이터의 개수가 perPage와 pageNum의 곱과 같을 때, pageNum을 1 증가시킨 값을 page 숫자와 검색어를 query로 넣어주는 API 데이터 함수에 query로 넣어준다.
    1. 왜? → 현재 page의 number가 전체 페이지수보다 작아야 다음 페이지를 불러올 수 있고, perPage(30)과 page의 number의 곱이 불러온 데이터의 개수 (예시 : 30 x 3 = 90)과 같아야 prefatch 함수에게 보여줄 수 있는 데이터를 보여줬으니 다음으로 보여줘야 할 데이터를 불러오라고 알려줄 수 있기 때문이다. 그리고 나서 pageNumber를 증가시킨 값을 API 통신을 통한 데이터를 불러오는 함수에 검색어와 같이 query로 넣게 되면, 다음 페이지에 있는 데이터를 불러오게 된다.
</br>
3. API 관련 데이터 수신함수에서 tableView나 collectionView에 데이터를 보여주는 일을 담당하는 배열에 수신한 데이터를 더해준다. collectionView나 tableView를 함수안에서 reload 시켜주고 업데이트 된 배열을 화면에 보여주게 된다.

  
</br>
</aside>
