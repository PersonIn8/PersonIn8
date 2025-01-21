# People_In_Eight

<aside>

1. DB - main / ES - 이관 저장

![image](https://github.com/user-attachments/assets/4b9197e0-a51e-4c5c-bbe6-6e60c140a526)


1. 도메인(뉴스 기반으로 투자 추천)
    1. 뉴스 → 키워드 → 주식
        - 뉴스 경제 관련 키워드 별 크롤링 ex)정치,전쟁
        - ETF 동향 파악
            1. 주식 ETF
            2. 채권-(장기/단기)  ETF
            3. 금 ETF
            4. 원자재 ETF
            
            ![image](https://github.com/user-attachments/assets/b913f2c3-c864-43a1-9c1f-a8a2a7577e90)

            
    
    → 시간이 남는다면, 크롤링을 도입
    
    과거의 데이터를 통해서 주가에 대한 경향 분석
    
    1.  핵심 기능
        1. **경제 뉴스 데이터 크롤링 및 키워드 분석**:
            - 주요 경제 관련 키워드(예: 정치, 전쟁, 금리, 인플레이션 등)를 자동으로 식별.
            - 뉴스 카테고리(정치, 경제, 산업 등)와 관련 ETF의 연관성 매핑.
        2. **ETF 동향 분석**:
            - 주식, 채권(장기/단기), 금, 원자재 ETF의 실시간 변동 및 수급 분석.
            - 특정 뉴스 키워드가 ETF 동향에 미치는 영향을 가시화.
        3. **맞춤형 투자 추천**:
            - 사용자 관심사(예: 특정 자산군, 리스크 성향 등)에 따라 ETF 추천.
            - 경제 동향을 쉽게 이해할 수 있는 인터랙티브 대시보드 제공.
    2. 프로젝트 개요 : 
        - 현대 금융시장은 복잡성과 변동성이 점점 증가하고 있으며, 개인 투자자들은 이를 기반으로 한 의사결정에서 어려움을 겪고 있습니다. 이 프로젝트는 실시간으로 경제 뉴스를 분석하여 핵심 키워드를 추출하고, 이를 바탕으로 주식, 채권, 금, 원자재 등 다양한 ETF(상장지수펀드)의 동향을 파악하여 사용자에게 맞춤형 투자 인사이트를 제공하는 것을 목표로 합니다.
    3. 프로젝트 목적 : 
        1. 뉴스 정보 기반 데이터로 사용자에게 맞춤형 ETF 추천
        2. 경제 동향 파악을 위한 시각화 자료 제공
        3. 
        
        경제 뉴스 분석:
        
        경제 관련 뉴스에서 주요 키워드를 추출하여 경제 동향을 파악합니다.
        정치, 전쟁, 금리, 인플레이션 등 다양한 요인이 시장에 미치는 영향을 분석합니다.
        
        ETF 및 주식 동향 파악:
        
        주식 및 ETF의 현재 가격, 거래량, 수익률 등을 모니터링하여 시장 동향을 분석합니다.
        특정 키워드와 관련된 ETF 및 주식의 성과를 추적하여 투자 전략을 수립합니다.
        
        투자 추천 제공:
        
        사용자에게 맞춤형 투자 추천을 제공합니다. 예를 들어, 특정 경제적 사건이 발생했을 때 관련 ETF나 주식에 대한 추천을 생성합니다.
        추천 알고리즘을 통해 사용자 맞춤형 정보를 제공하여 투자 결정을 돕습니다.
        
        뉴스 데이터를 실시간으로 수집하고 분석하여 최신 정보를 반영합니다.
        사용자에게 신뢰할 수 있는 정보를 제공하여 투자 신뢰성을 높입니다.
        
        투자 관련 교육 자료 및 시장 분석을 통해 사용자에게 부가 가치를 제공합니다.
        
    4. 데이터
        
        네이버 뉴스 HeadLine 기사들만 크롤링 
        
        → 데이터 전처리 [섹션 번호, 제목, 링크, 요약, 언론사]
        
        문제 발생 
        
        주가 영향에 대한 부분은 개인이나 현재의 조가 임의로 지정할 수 없다고 생각하여 생성형 AI를 이용한 컬럼 추가를 진행
        
        → Chat GPT를 이용한 컬럼 추가
        
        종류 : 금,주식,채권,원자재
        
        값 : 상승,하락,관련 없음
        
        → CSV 파일로 저장
        
        <aside>
        
        섹션 구분
        
        100 -> 정치
        101 -> 경제
        102 -> 사회
        103 -> 생활/문화
        104 -> 세계
        105 -> IT/과학
        
        </aside>
        
    
</aside>

크롤링 사이트 : https://news.naver.com/

### GPT [main과 이관]

**뉴스 크롤링 ETF 동향 분석**에서 **RDBMS**와 **ElasticSearch(ES)**를 결합할 경우, 데이터의 특성과 사용 목적에 따라 **메인 저장소**와 **이관 저장소**의 역할을 다음과 같이 정의할 수 있습니다.

---

## **1. 어떤 RDBMS를 사용할까?**

### **추천 RDBMS**

- **MySQL / MariaDB**:
    - 오픈소스 RDBMS로 가볍고 빠르며 설정이 간단.
    - 뉴스 크롤링 데이터를 정리된 구조로 저장하기에 적합.
- **PostgreSQL**:
    - 관계형 데이터뿐만 아니라 JSON 데이터 처리도 가능.
    - ETF 기사 데이터를 구조화하면서도 비정형 데이터 일부를 함께 저장할 때 유리.
- **SQLite**:
    - 간단한 파일 기반 데이터베이스로, 초기 개발 및 테스트 단계에 적합.
    - 배포나 대규모 사용에는 적합하지 않을 수 있음.

### **선택 기준**

- **데이터 규모가 크지 않은 경우**: MySQL, MariaDB.
- **고급 쿼리와 JSON 데이터 지원이 필요한 경우**: PostgreSQL.
- **임시 개발 또는 단일 사용자 환경**: SQLite.

---

## **2. RDBMS와 ES의 역할 분담**

### **(1) RDBMS를 메인 저장소로 사용, ES를 이관 저장소로 사용**

### **구성**

1. RDBMS:
    - **크롤링한 뉴스 데이터를 원본 상태로 저장**.
    - 정형 데이터(기사 제목, 본문, URL, 날짜, 관련 ETF 분류 등)를 테이블 구조로 저장.
    - 예: `articles` 테이블
        
        ```sql
        CREATE TABLE articles (
            id SERIAL PRIMARY KEY,
            title TEXT,
            content TEXT,
            url TEXT,
            date TIMESTAMP,
            etf_category VARCHAR(50)
        );
        ```
        
2. ES:
    - 뉴스 데이터에서 **ETF 관련 키워드**를 추출한 후, 실시간 검색 및 분석을 위해 사용.
    - 사용자 입력(예: 특정 ETF 이름)을 기반으로 고속으로 관련 기사를 검색.

### **적합한 이유**

- **RDBMS**:
    - 뉴스 데이터를 정리된 상태로 장기 보관 및 관계형 쿼리 처리에 유리.
    - 크롤링된 원본 데이터를 손실 없이 저장.
- **ElasticSearch**:
    - ETF 동향 분석을 위해 키워드 기반 고속 검색 및 시각화(Kibana 활용).

### **적합한 사용 사례**

- ETF 키워드 트렌드 분석 대시보드.
- 기사 내 특정 ETF 카테고리의 관련도를 빠르게 검색.

---

### **(2) ES를 메인 저장소로 사용, RDBMS를 이관 저장소로 사용**

### **구성**

1. ES:
    - 뉴스 데이터를 **바로 인덱싱**하여 빠른 검색과 분석을 제공.
    - 기사 본문을 비정형 데이터로 저장하고, 실시간 검색 및 키워드 추출에 활용.
    - 인덱스 설계 예:
        
        ```json
        {
            "title": "ETF 시장 급등, 투자자 관심 집중",
            "content": "코스피200 ETF가 시장에서 주목받고 있다...",
            "url": "https://example.com/news123",
            "date": "2025-01-21T10:00:00",
            "etf_category": "코스피200"
        }
        
        ```
        
2. RDBMS:
    - 일정 시간이 지난 데이터를 **장기 보관용**으로 이관.
    - 데이터 아카이빙이나 정리된 통계 분석에 사용.

### **적합한 이유**

- **ElasticSearch**:
    - 대용량 비정형 데이터(뉴스 기사 본문)의 빠른 검색 및 필터링.
    - ETF 동향 분석에서 고속으로 시각화 결과를 생성.
- **RDBMS**:
    - 오래된 데이터를 구조화하여 보관 및 이관 후의 데이터 정리를 수행.

### **적합한 사용 사례**

- 실시간 대시보드에서 특정 ETF 카테고리 관련 기사를 빠르게 필터링.
- 과거 데이터를 RDBMS에서 보관하며 월별/분기별 통계 보고서 생성.

---

## **3. 최적의 선택은?**

### **주요 결정 요소**

1. **뉴스 데이터의 주요 사용 목적**:
    - **실시간 검색과 분석**이 중요하다면 **ElasticSearch를 메인 저장소**로.
    - **데이터 적합성 및 관계형 쿼리**가 중요하다면 **RDBMS를 메인 저장소**로.
2. **데이터 구조**:
    - 비정형 데이터(기사 본문 중심) → ElasticSearch.
    - 정형 데이터(관계형 모델로 관리 가능한 데이터) → RDBMS.
3. **데이터 크기**:
    - **대용량 데이터 처리 및 고속 검색** → ElasticSearch.
    - **소규모 데이터 정리 및 관리** → RDBMS.

---

### **추천 시나리오**

1. **RDBMS 메인, ElasticSearch 이관 (추천)**:
    - 뉴스 데이터를 크롤링하여 **RDBMS에 저장**하고, 실시간 분석이 필요한 경우 ElasticSearch에 동기화.
    - RDBMS를 통해 데이터 정합성 및 트랜잭션 관리.
    - ElasticSearch에서 빠른 ETF 트렌드 검색과 시각화.
2. **ElasticSearch 메인, RDBMS 이관**:
    - 실시간 검색 및 빠른 데이터 접근이 중요한 경우.
    - 장기 데이터 보관용으로 RDBMS를 사용.

---

### **결론**

- **RDBMS 메인, ElasticSearch 이관**은 **ETF 동향 분석**에서 **정확한 데이터 관리와 실시간 검색**의 균형을 맞출 수 있어 추천됩니다.
- 데이터 크기나 사용 목적이 ES 중심이라면 **ElasticSearch 메인**으로 전환도 고려 가능합니다.

더 구체적인 설계나 구현이 필요하다면 추가 요청해주세요!

| ETF_Name | Type | Price | Volume | 1D_Return | 1W_Return | 1M_Return | 3M_Return | 6M_Return | 1Y_Return | Risk_Level |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| KODEX 200 ETF | Stock ETF | 30,000 | 1,200,000 | 0.02 | 0.03 | 0.05 | 0.10 | 0.15 | 0.20 | Medium |
| KODEX 삼성그룹 ETF | Stock ETF | 25,000 | 800,000 | 0.01 | 0.02 | 0.04 | 0.09 | 0.13 | 0.18 | Medium |
| KODEX 국채 10년 ETF | Bond ETF | 110,000 | 500,000 | 0.00 | 0.01 | 0.02 | 0.03 | 0.06 | 0.04 | Low |
| KODEX 단기채권 ETF | Bond ETF | 105,000 | 450,000 | -0.01 | 0.00 | 0.01 | 0.02 | 0.05 | 0.02 | Low |
| KODEX 금 ETF | Gold ETF | 60,000 | 600,000 | 0.01 | 0.02 | 0.03 | 0.06 | 0.08 | 0.10 | Medium |
| KODEX 은 ETF | Gold ETF | 25,000 | 300,000 | 0.02 | 0.03 | 0.04 | 0.07 | 0.09 | 0.12 | Medium |
| KODEX 원자재 ETF | Commodity ETF | 30,000 | 200,000 | 0.01 | 0.02 | 0.03 | 0.05 | 0.07 | 0.10 | High |
| KODEX GSCI 원자재 ETF | Commodity ETF | 32,000 | 250,000 | -0.02 | 0.01 | 0.02 | 0.04 | 0.06 | 0.09 | High |

```
import requests
from bs4 import BeautifulSoup

# 크롤링할 웹사이트 URL
url = 'https://n.news.naver.com/mnews/article/421/0008034068'  # 원하는 사이트의 URL로 변경하세요.

# 웹 페이지 요청
response = requests.get(url)

# 응답 코드 확인
if response.status_code == 200:
    # 웹 페이지의 HTML 내용 파싱
    soup = BeautifulSoup(response.text, 'html.parser')

    # <meta> 태그에서 og:title 추출
    meta_title = soup.find('meta', property='og:title')
    
    if meta_title:
        # content 속성 출력
        print(meta_title['content'])
    else:
        print('og:title 메타 태그를 찾을 수 없습니다.')
else:
    print(f'웹 페이지 요청 실패: {response.status_code}')

```

[ DATA](https://www.notion.so/DATA-18273f948a0480c0b4e8d151260526e1?pvs=21)

트러블 슈팅 생각나는거 

인덱스 이름 : 대문자 불가 오류 발생 

트래킹 컬럼  이슈 : es에 계속 무한으로 저장됨 .

뉴스, etf 데이터 —> 크롤링 + 전처리 —> 파일빗 —> 로그스태시—> ES에 저장 —> ?? —> 필터링 —> mysql 

- etfnews.conf
    
    ```
    input {
      elasticsearch {
        hosts => ["http://localhost:9200"]
        index => "etfnews" 
        query => '{ "query": { "match_all": {} } }'  # 모든 문서를 가져오는 쿼리
      }
    }
    
    output {
      jdbc {
        jdbc_driver_library => "C:\02.devenv\ELK\logstash-7.11.1\lib\mysql-connector-j-8.0.33\mysql-connector-j-8.0.33.jar"  # JDBC 드라이버 경로
        jdbc_driver_class => "com.mysql.cj.jdbc.Driver"
        jdbc_connection_string => "jdbc:mysql://localhost:3306/ETFnews"
        jdbc_user => "user01"
        jdbc_password => "user01"
        statement => [
          "INSERT INTO users (username, email) VALUES (?, ?)",  # MySQL에 삽입할 쿼리
          "username", "email"
        ]
      }
    }
    
    ```
