# PEOPLE_IN_EIGHT 8️⃣
<aside>

## 👨🏻‍💻 프로젝트 개요
현대 금융시장은 **복잡성과 변동성이 점점 증가**하고 있으며, 개인 투자자들은 이를 기반으로 한 의사결정에서 어려움을 겪고 있습니다. 이 프로젝트는 **실시간**으로 경제 **뉴스를 분석**하여 핵심 키워드를 추출하고, 이를 바탕으로 **주식, 채권, 금, 원자재 등 다양한 ETF(상장지수펀드)의 동향을 파악**하여 사용자에게 맞춤형 투자 인사이트를 제공하는 것을 목표로 합니다.

## 👨‍👨‍👦‍👦 팀원 소개
| <img src="https://github.com/wns5120.png" width="200px"> | <img src="https://github.com/JaeHee-devSpace.png" width="200px"> | <img src="https://github.com/andytjdqls.png" width="200px"> | <img src="https://github.com/wild-turkey.png" width="200px"> |
| :---: | :---: | :---: | :---: |
| [유호준](https://github.com/wns5120) | [박재희](https://github.com/JaeHee-devSpace) | [이성빈](https://github.com/andytjdqls) | [김지훈](https://github.com/wild-turkey) |

## 📚 기술 스택

### 1. **프로그래밍 언어 및 데이터 처리**
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white) ![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-FFD700?style=flat&logo=python&logoColor=black) ![Requests](https://img.shields.io/badge/Requests-00599C?style=flat&logo=python&logoColor=white)

### 2. **통합 개발 환경 (IDE)**
![Visual Studio Code](https://img.shields.io/badge/VSCode-007ACC?style=flat&logo=visualstudiocode&logoColor=white) ![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=flat&logo=googlecolab&logoColor=black)

### 3. **ELK 스택 및 데이터 파이프라인**
![FileBeat](https://img.shields.io/badge/FileBeat-0077C8?style=flat&logo=elastic&logoColor=white) ![Logstash](https://img.shields.io/badge/Logstash-005571?style=flat&logo=elastic&logoColor=white) ![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?style=flat&logo=elastic&logoColor=white) ![Kibana](https://img.shields.io/badge/Kibana-005571?style=flat&logo=elastic&logoColor=white)

### 4. **가상화 및 OS 관리**
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black) ![VirtualBox](https://img.shields.io/badge/VirtualBox-183A61?style=flat&logo=virtualbox&logoColor=white) ![MobaXterm](https://img.shields.io/badge/MobaXterm-008FBA?style=flat&logoColor=white)

### 5. **데이터베이스 및 쿼리 도구**
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white) ![DBeaver](https://img.shields.io/badge/DBeaver-1C2834?style=flat&logoColor=white)

### 6. **구조도 작성 도구**
![Markdown](https://img.shields.io/badge/Markdown-000000?style=flat&logo=markdown&logoColor=white) ![Mermaid](https://img.shields.io/badge/Mermaid-4995DA?style=flat&logo=mermaid&logoColor=white)

### 7. **데이터 활용 도구**
![ChatGPT](https://img.shields.io/badge/ChatGPT-412991?style=flat&logo=openai&logoColor=white)


## 🎯 프로젝트 목표
**1. 뉴스 정보 기반 데이터로 사용자에게 맞춤형 ETF 추천**
       
**2. 경제 동향 파악을 위한 시각화 자료 제공**

       

## 💡 기술적 목표 
**1. ElasticSearch에 csv데이터를 업로드**
 
**2. 2개의 Logstash를 활용한 pipeline 구축**
     
**3. ElasticSearch에 업로드 된 데이터를 mySQL로 이관**

## ⚙ 핵심 기능

1. **경제 뉴스 데이터 크롤링 및 키워드 분석**:
    - 주요 경제 관련 키워드(예: 정치, 전쟁, 금리, 인플레이션 등)를 자동으로 식별.
    - 뉴스 카테고리(정치, 경제, 산업 등)와 관련 ETF의 연관성 매핑.
2. **ETF 동향 분석**:
    - 주식, 채권(장기/단기), 금, 원자재 ETF의 실시간 변동 및 수급 분석.
    - 특정 뉴스 키워드가 ETF 동향에 미치는 영향을 가시화.
3. **맞춤형 투자 추천**:
    - 사용자 관심사(예: 특정 자산군, 리스크 성향 등)에 따라 ETF 추천.
    - 경제 동향을 쉽게 이해할 수 있는 인터랙티브 대시보드 제공.       
            

## 📐 System Architecture
 이 시스템은 **ETF 종목별 변동성을 분석하고 실시간으로 제공하기 위해 설계**되었습니다. Filebeat는 데이터 변동 사항을 감지하고 Logstash는 자동 스케줄링을 통해 데이터를 처리하여 Elasticsearch에 저장합니다. **Elasticsearch**는 비정형 기사 데이터를 인덱싱 및 집계하여 빠르게 검색할 수 있는 **메인 저장소** 역할을 하며, 변동성이 큰 종목을 분석하여 일자별로 **정리된 데이터를 MySQL에 저장**합니다. 이러한 구조는 대량의 기사 데이터를 효율적으로 처리하고, 필요한 정보만 제공하는 데 적합하며 실시간 데이터 분석 및 저장을 효과적으로 지원합니다.
    
   ![window_TD](https://github.com/user-attachments/assets/aebbf289-e6f6-408c-9bd2-ebd9d2d7d774)

    

    
    ### mermaid code

    
    flowchart
        
        subgraph Linux["Linux"]
            F2["MySQL"]
        end
    
        subgraph Window["Window"]
            B["Data Generation CSV"]
            A["Naver News Crawling"]
            C["FileBeat"]
            D["LogStash 1"]
            E["Elasticsearch"]
            F["LogStash 2"]
            Linux
        end
    
        subgraph TitleStyle ["System Architecture"]
            direction TB
        end
    
        A --> B
        B --> C
        C --> D
        D --> E
        E --> F
        F --> F2
    
        style TitleStyle fill:#000000,stroke:#FFFFFF,color:#FFFFFF,font-size:18px,font-weight:bold
        style B fill:#FFF4D2,stroke:#FFB703,stroke-width:2px,rx:15,ry:15  %% CSV
        style A fill:#FFDDC1,stroke:#E2711D,stroke-width:2px,rx:20,ry:20  %% Crawling
        style C fill:#E9FFDB,stroke:#90BE6D,stroke-width:2px,rx:10,ry:10  %% FileBeat
        style D fill:#D2EFFF,stroke:#0077B6,stroke-width:2px,shape:rect  %% LogStash 1
        style E fill:#FFD6E8,stroke:#D72638,stroke-width:2px,shape:stadium  %% Elasticsearch
        style F fill:#D2EFFF,stroke:#0077B6,stroke-width:2px,shape:rect  %% LogStash 2

## 🛢 데이터베이스

- 스키마
  
```sql
-- 1. 테이블 생성 (이미 존재하면 삭제 후 새로 생성)
DROP TABLE IF EXISTS data_status;

CREATE TABLE data_status (
    id INT AUTO_INCREMENT PRIMARY KEY, -- 고유 ID (자동 증가)
    category VARCHAR(255) NOT NULL,    -- 종류 (예: 원자재, 금)
    status VARCHAR(255) NOT NULL,      -- 값 (예: 상승, 하락)
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP -- 데이터 삽입 시간
);

-- 2. 결과 확인 (선택적: 남아 있는 데이터 확인)
SELECT * FROM data_status;
```
- 테이블 구조
![image](https://github.com/user-attachments/assets/9b3d766b-81e0-46dd-a598-3bcd4a31d53e)


## 📊 데이터
</details>

네이버 뉴스 HeadLine 기사들만 크롤링 → 데이터 전처리 [섹션 번호, 제목, 링크, 요약, 언론사]
 
 #### ⚠ 문제 발생
 주가 영향에 대한 부분은 개인이나 현재의 조가 임의로 지정할 수 없음
 → Chat GPT를 이용한 검색을 통해 컬럼 추가
 <br>
 [종류 : 금,주식,채권,원자재 / 값 : 상승,하락,관련 없음] → CSV 파일로 저장
 
 <aside>
 
 섹션 구분

 ```
 100 -> 정치
 101 -> 경제
 102 -> 사회
 103 -> 생활/문화
 104 -> 세계
 105 -> IT/과학
 ```
 </aside>
 
<details>
   <summary> 🗂️크롤링 과정🗂️ </summary>

   1. 네이버 뉴스의 한 기사만 크롤링 해보기
            
            
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
            
            
            
        2. 섹션의 전체 크롤링하기
            
            페이지의 HeadLine 기사들을 나타내는 HTML 태그 <li.sa_item._SECTION_HEADLINE> 를 찾아서 크롤링하기
            
            ```sql
            import requests
            from bs4 import BeautifulSoup
            import pandas as pd
            
            def get_news_articles(start_section_id, end_section_id, pages=1):
                """
                네이버 뉴스 섹션에서 기사 제목, 링크 등을 크롤링하는 함수 (100~105 섹션 범위)
                :param start_section_id: 시작 섹션 ID (예: 100)
                :param end_section_id: 끝 섹션 ID (예: 105)
                :param pages: 각 섹션에서 가져올 페이지 수
                :return: 모든 섹션 기사 데이터프레임
                """
                base_url = "https://news.naver.com/main/main.naver?mode=LSD&mid=shm&sid1="
                article_list = []
            
                for section_id in range(start_section_id, end_section_id + 1):
                    for page in range(1, pages + 1):
                        url = f"{base_url}{section_id}&page={page}"
                        headers = {
                            "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36"
                        }
                        response = requests.get(url, headers=headers)
            
                        if response.status_code != 200:
                            print(f"페이지를 가져올 수 없습니다: {url}")
                            continue
            
                        soup = BeautifulSoup(response.text, 'html.parser')
            
                        # 기사 크롤링 (HTML 구조 기반)
                        articles = soup.select("li.sa_item._SECTION_HEADLINE")
                        for article in articles:
                            try:
                                title_tag = article.select_one("a.sa_text_title")
                                title = title_tag.get_text(strip=True) if title_tag else "제목 없음"
                                link = title_tag["href"] if title_tag and title_tag.has_attr("href") else "링크 없음"
            
                                summary_tag = article.select_one("div.sa_text_lede")
                                summary = summary_tag.get_text(strip=True) if summary_tag else "요약 없음"
            
                                press_tag = article.select_one("div.sa_text_press")
                                press = press_tag.get_text(strip=True) if press_tag else "언론사 없음"
            
                                article_list.append({
                                    "섹션 번호": section_id,
                                    "제목": title,
                                    "링크": link,
                                    "요약": summary,
                                    "언론사": press
                                })
                            except Exception as e:
                                print(f"크롤링 중 오류 발생 (섹션 {section_id}): {e}")
            
                return pd.DataFrame(article_list)
            
            # 섹션 ID 범위 설정 및 크롤링 실행
            start_section_id = 100  # 시작 섹션 번호
            end_section_id = 105  # 끝 섹션 번호
            pages = 2  # 각 섹션에서 가져올 페이지 수
            
            # 크롤링 실행
            articles = get_news_articles(start_section_id, end_section_id, pages)
            
            # 결과 확인 및 저장
            print(articles.head())
            articles.to_csv("news_section_100_to_105.csv", index=False, encoding="utf-8-sig")
            
            # Colab에서 파일 다운로드
            from google.colab import files
            files.download("news_section_100_to_105.csv")
            
            ```
            
           ![image 4](https://github.com/user-attachments/assets/d5514e06-fb51-4626-be26-64b1324eee46)

            크롤링 사이트 : https://news.naver.com/
</aside>

## 📈 Kibana 시각화

- 종목별상승하락비율
![image](https://github.com/user-attachments/assets/e5819b23-24a8-470b-8a31-1f48d1038d82)

- 분야별 ETF 영향
![image](https://github.com/user-attachments/assets/41d6376c-4db3-44f7-970a-12cc08b49c47)


 ## 📝 **키포인트 요약**
     
1. **뉴스 데이터의 주요 사용 목적**:
  - **실시간 검색과 분석**이 중요하다면 **ElasticSearch를 메인 저장소**로.
2. **데이터 구조**:
  - 비정형 데이터(기사 본문 중심) → ElasticSearch.
  - 정형 데이터(관계형 모델로 관리 가능한 데이터) → RDBMS.
3. **데이터 크기**:
  - **대용량 데이터 처리 및 고속 검색** → ElasticSearch.
  - **소규모 데이터 정리 및 관리** → RDBMS.


    
## Key Points

- ### 📌 ElasticSearch 메인, RDBMS 이관
        
     
     
     - 실시간 검색 및 빠른 데이터 접근이 중요한 경우.
     - 장기 데이터 보관용으로 RDBMS를 사용.
     
     **구성**
     
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
     
      **적합한 이유**
     
     - **ElasticSearch**:
         - 대용량 비정형 데이터(뉴스 기사 본문)의 빠른 검색 및 필터링.
         - ETF 동향 분석에서 고속cs으로 시각화 결과를 생성.
     - **RDBMS**:
         - 오래된 데이터를 구조화하여 보관 및 이관 후의 데이터 정리를 수행.
     
      **적합한 사용 [프로젝트에서 보여지는]**
     
     - 실시간 대시보드에서 특정 ETF 카테고리 관련 기사를 빠르게 필터링.
     - 과거 데이터를 RDBMS에서 보관하며 월별/분기별 통계 보고서 생성.

       

- ### 📌 Logstash 2개
     
     **장점**
     
     1. **워크로드 분리**:
         - 하나의 Logstash는 데이터 수집과 전처리에 집중하고, 다른 Logstash는 Elasticsearch에서 데이터를 읽어 집계 및 후처리에 집중합니다.
         - 이러한 분리는 병렬 처리를 가능하게 하며 데이터 처리 속도를 높입니다.
     2. **유연성 강화**:
         - 각각의 Logstash가 독립된 파이프라인으로 작동하여 특정 요구사항에 맞는 데이터 처리가 가능합니다.
         - 예를 들어, Logstash 1은 실시간 데이터 전처리에 초점을 맞추고, Logstash 2는 Elasticsearch의 집계 데이터를 MySQL로 전송하는 데 초점을 맞출 수 있습니다.
     3. **안정성 향상**:
         - 하나의 Logstash에서 장애가 발생해도 다른 Logstash는 독립적으로 동작하여 전체 시스템 가용성을 유지합니다.
         - 특정 Logstash가 과부하를 받지 않도록 역할을 분리하여 시스템 안정성을 높입니다.
     4. **확장성**:
         - 데이터 처리량이 증가할 경우, 추가 Logstash를 도입해 특정 작업(예: 데이터 필터링, 추가 저장소와의 통합)을 쉽게 분리할 수 있습니다.
     
     
     **단점**
     
     1. **관리 복잡성 증가**:
         - Logstash 2개를 운영하면 설정 및 유지보수가 더 복잡해집니다. 각 Logstash의 파이프라인 및 동작을 세밀히 관리해야 합니다.
     2. **리소스 소모 증가**:
         - Logstash는 상대적으로 높은 CPU 및 메모리 사용량을 가지므로, 인스턴스를 2개로 늘릴 경우 서버 리소스 부담이 증가할 수 있습니다.
     3. **동기화 문제**:
         - 두 Logstash가 동일한 Elasticsearch와 상호작용할 경우 데이터 충돌 또는 동기화 문제를 방지하기 위해 추가적인 조정이 필요할 수 있습니다.


--------------------------------------------------------------------------------------------------



# 🚀 트러블 슈팅
  <details>
  <summary> 인덱스 이름 : 대문자 불가 오류 발생 </summary>

```sql
Successfully started Logstash API endpoint {:port=>9600}
C:/02.devenv/ELK/logstash-7.11.1/vendor/bundle/jruby/2.5.0/gems/rufus-scheduler-3.0.9/lib/rufus/scheduler/cronline.rb:77: warning: constant ::Fixnum is deprecated
[2025-01-21T14:42:01,985][INFO ][logstash.inputs.jdbc     ][main][6d4aeb4cd79e7f4c0f50afe35f6d7ad8a963fbf373d6c987fb9b705bc46d85ca] (0.040607s) SELECT * FROM users
[2025-01-21T14:42:02,454][ERROR][logstash.outputs.elasticsearch][main][6582090182203f038cf99cd5d36f9dd357e61d1c1f01d3e4debb937dd404b023] Could not index event to Elasticsearch. {:status=>400, :action=>["index", {:_id=>nil, :_index=>"ETFnews", :routing=>nil, :_type=>"_doc"}, #LogStash::Event:0x6147c224], :response=>{"index"=>{"_index"=>"ETFnews", "_type"=>"_doc", "_id"=>nil, "status"=>400, "error"=>{"type"=>"invalid_index_name_exception", "reason"=>"Invalid index name [ETFnews], must be lowercase", "index_uuid"=>"na", "index"=>"ETFnews"}}}}
[2025-01-21T14:42:02,461][ERROR][logstash.outputs.elasticsearch][main][6582090182203f038cf99cd5d36f9dd357e61d1c1f01d3e4debb937dd404b023] Could not index event to Elasticsearch. {:status=>400, :action=>["index", {:_id=>nil, :_index=>"ETFnews", :routing=>nil, :_type=>"_doc"}, #LogStash::Event:0x7c4775fd], :response=>{"index"=>{"_index"=>"ETFnews", "_type"=>"_doc", "_id"=>nil, "status"=>400, "error"=>{"type"=>"invalid_index_name_exception", "reason"=>"Invalid index name [ETFnews], must be lowercase", "index_uuid"=>"na", "index"=>"ETFnews"}}}}
[2025-01-21T14:42:02,461][ERROR][logstash.outputs.elasticsearch][main][6582090182203f038cf99cd5d36f9dd357e61d1c1f01d3e4debb937dd404b023] Could not index event to Elasticsearch. {:status=>400, :action=>["index", {:_id=>nil, :_index=>"ETFnews", :routing=>nil, :_type=>"_doc"}, #LogStash::Event:0x3757b92], :response=>{"index"=>{"_index"=>"ETFnews", "_type"=>"_doc", "_id"=>nil, "status"=>400, "error"=>{"type"=>"invalid_index_name_exception", "reason"=>"Invalid index name [ETFnews], must be lowercase", "index_uuid"=>"na", "index"=>"ETFnews"}}}}
[2025-01-21T14:43:00,095][INFO ][logstash.inputs.jdbc     ][main][6d4aeb4cd79e7f4c0f50afe35f6d7ad8a963fbf373d6c987fb9b705bc46d85ca] (0.002554s) SELECT * FROM users
[2025-01-21T14:43:00,224][ERROR][logstash.outputs.elasticsearch][main][6582090182203f038cf99cd5d36f9dd357e61d1c1f01d3e4debb937dd404b023] Could not index event to Elasticsearch. {:status=>400, :action=>["index", {:_id=>nil, :_index=>"ETFnews", :routing=>nil, :_type=>"_doc"}, #LogStash::Event:0x4ea59bdb], :response=>{"index"=>{"_index"=>"ETFnews", "_type"=>"_doc", "_id"=>nil, "status"=>400, "error"=>{"type"=>"invalid_index_name_exception", "reason"=>"Invalid index name [ETFnews], must be lowercase", "index_uuid"=>"na", "index"=>"ETFnews"}}}}
```

Logstash 실행 시 인덱스 찾을 수 없는 오류 발생 

"Invalid index name [ETFnews], must be lowercase”

인덱스 이름이 대문자여서 명명규칙 위반
  </details>
  
---

   <details>
  <summary> 스케쥴링 </summary>
  1분마다 현재 시간과 비교 및 삽입 →  자동 스케쥴링 시간과 동일시 해줘야 하는 문제 발생
→ 1분 기준으로 스케줄링 코드 추가
      
      input {
     elasticsearch {
       hosts => ["http://localhost:9200"]
       index => "news"
       query => '{
         "query": {
           "range": {
             "@timestamp": {
               "gt": "now-1m",
               "lte": "now"
             }
           }
         }
       }'
       schedule => "*/1 * * * *"
     }

  </details>
  
  ---
  
   <details>
  <summary> DB 저장에서의 중복 저장 문제 </summary>

   데이터가 ES에서 받아오는 그대로 저장 → 그 이전에 이미 저장되었던 정보들이 중복해서 저장됨

   input을 변경해서, timestamp를 활용하여 비교를 통해 이전에 삽입되었던 정보들은 제외하고 삽입하기

```
   # 수정 전
input {
  elasticsearch {
    hosts => ["http://localhost:9200"]
    index => "news"
    query => '{
      "query": {
        "range": {
          "@timestamp": {
            "gt": "now-1m/m"
          }
        }
      }
    }'
  }
}

# 수정 후
input {
  elasticsearch {
    hosts => ["http://localhost:9200"]
    index => "news"
    query => '{
      "query": {
        "range": {
          "@timestamp": {
            "gt": "now-1m/m"
          }
        }
      }
    }'
  }
}
```
  </details>
  
---

  <details>
  <summary> Logstash JDK 인식 문제 </summary>

   JDK를 자체적으로 보유하고 있음에도 불구하고 인식하지 못하는 현상 발생

```markdown
set JAVA_HOME="C:\02.devEnv\ELK\logstash-7.11.1\jdk"
setx PATH "%PATH%;%JAVA_HOME%\bin"
```

강제적으로 인식시켜주기 후, 실행 성공
  
  </details>
  
---

  <details>
  <summary> ES와 DB연결 문제 </summary>
     - 연결 문제 확인
     - Logstash[output용]의 Es 데이터 수신 확인을 위한 txt 파일 도출
      
   [메모장에 넣기 ](https://www.notion.so/4f590a11c2d744a4aebe4ef422b3e202?pvs=21)
      
   ![image 1](https://github.com/user-attachments/assets/60cdb3c5-ec38-4a3d-9d51-783315ce6eaa)

      
  - Logstash[output용]의 Es 동적 움직임 감지 테스트
      
      위의 txt 파일 도출을 사용해서 filebeat에서 감지한 데이터의 변형이 반영되는지를 확인하기 (동적 감지 확인을 위해 filter 부분 제외)
      
      ```json
      input {
        elasticsearch {
          hosts => ["http://localhost:9200"]
          index => "news"
          query => '{ "query": { "match_all": {} } }'
          docinfo => true
        }
      }
      output {
        file {
          path => "C:/02.devEnv/ELK/logstash_output.txt"  # 저장할 파일 경로
          codec => line { format => "%{type}, %{value}" }  # 각 필드를 원하는 형식으로 저장
        }
      }
      ```
      
      ![image 2](https://github.com/user-attachments/assets/037d02b2-bbf2-4933-9776-077bc449a472)

      
  - Logstash[output용]과 Mysql의 연결 부분 문제 테스트
      
      Window에 Mysql 설치하여 window → Linux → mysql 이 아니라 window OS의 동일 선상에서 사용할 수 있도록 테스트
      
  - Logstash[output용]의 conf 파일의 설정 문제 테스트
      
      JDBC Driver Encoding 방식의 충돌 : UTF-8
      
      파일의 enconding 방식을 강제적으로 파일에 명시하였지만, 실패
      
      JDBC Driver에서의 [statement] 변경, 실패
      
      conf 파일의 filter 부분 삭제, 연결 성공
      
      → 중복을 삭제하기 위해서 filter 구성 다시하기
  </details>
  
  ------------
  
  <details>
    <summary> JDBC Driver </summary>
      
  - 설치 문제

     - **오류 내용: `logstash-output-jdbc` 플러그인 관련 오류**
      
     - **실제 오류 코드**:
                    
                    
       
                    [2025-01-21T18:16:15,891][ERROR][logstash.plugins.registry] Tried to load a plugin's code, but failed. {:exception=>#<LoadError: no such file to load -- logstash/outputs/jdbc>, :path=>"logstash/outputs/jdbc", :type=>"output", :name=>"jdbc"}
                    [2025-01-21T18:16:15,903][FATAL][logstash.runner] The given configuration is invalid. Reason: Unable to configure plugins: (PluginLoadingError) Couldn't find any output plugin named 'jdbc'.
                    
  



   **해결 방법**:
  - `logstash-output-jdbc` 플러그인 재설치 명령 실행:
                                
                            
    
        logstash-plugin install logstash-output-jdbc
                                
                        
     </details>        
     
     ---
    
    <details>
        <summary>  
                오류 내용: JDK 인식 실패 문제
        </summary>
                    
     강제적으로 한번 더 인식 시켜주기
                    
                
                    set JAVA_HOME=C:\02.devEnv\ELK\logstash2-7.11.1\jdk
                    set PATH=%JAVA_HOME%\bin;%PATH%
                    logstash-plugin install logstash-output-jdbc


</details>
                

----

# 🤔 회고

- 데이터를 관리하는 여러 스택간의 유기적인 활용을 실습해 볼 수 있어서 좋았습니다.
- 그림으로만 보던 파이프라인을 구축하는 경험을 하게 되어 이해하는데 큰 도움이 되었습니다.
- 짧은 프로젝트 기간으로 인해서 처음에 계획했었던 실시간 크롤링 기능과, 구체적인 시각화 기능을 구현하지 못해 아쉽습니다.

Special Thanks to 김우현
