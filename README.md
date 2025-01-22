# ElasticSearch, Logstash, mySQL 활용 실습
<aside>

## 프로젝트 개요
현대 금융시장은 복잡성과 변동성이 점점 증가하고 있으며, 개인 투자자들은 이를 기반으로 한 의사결정에서 어려움을 겪고 있습니다. 이 프로젝트는 실시간으로 경제 뉴스를 분석하여 핵심 키워드를 추출하고, 이를 바탕으로 주식, 채권, 금, 원자재 등 다양한 ETF(상장지수펀드)의 동향을 파악하여 사용자에게 맞춤형 투자 인사이트를 제공하는 것을 목표로 합니다.

## 프로젝트 목표

   1. 뉴스 정보 기반 데이터로 사용자에게 맞춤형 ETF 추천
       -
   2. 경제 동향 파악을 위한 시각화 자료 제공
       -
   3. 맞춤형 투자 정보 제공
       -

## 💡 기술적 목표 
**1. ElasticSearch에 csv데이터를 업로드**
 
     
**2. ElasticSearch에 업로드 된 데이터를 mySQL로 이관**

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
    
- 데이터
    
    [ DATA](https://www.notion.so/DATA-18273f948a0480c0b4e8d151260526e1?pvs=21)
    
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
    
- System Architecture
    - 이 시스템은 **ETF 종목별 변동성을 분석하고 실시간으로 제공하기 위해 설계**되었습니다. Filebeat는 데이터 변동 사항을 감지하고 Logstash는 자동 스케줄링을 통해 데이터를 처리하여 Elasticsearch에 저장합니다. **Elasticsearch**는 비정형 기사 데이터를 인덱싱 및 집계하여 빠르게 검색할 수 있는 **메인 저장소** 역할을 하며, 변동성이 큰 종목을 분석하여 일자별로 **정리된 데이터를 MySQL에 저장**합니다. 이러한 구조는 대량의 기사 데이터를 효율적으로 처리하고, 필요한 정보만 제공하는 데 적합하며 실시간 데이터 분석 및 저장을 효과적으로 지원합니다.
    
   ![window_TD](https://github.com/user-attachments/assets/aebbf289-e6f6-408c-9bd2-ebd9d2d7d774)

    
    ![add_title](https://github.com/user-attachments/assets/063c7cca-bed6-4d20-a26a-dbf0d474657c)

    
    ### mermaid code
    
    ```sql
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
    
    ```
    
- ETF란?
    
    ETF(Exchange Traded Fund)는 **상장지수펀드**로, 특정 지수나 자산(금, 원자재, 주식, 채권 등)을 추종하며 주식시장에 상장되어 주식처럼 거래되는 펀드입니다. ETF는 투자자에게 **분산 투자**, **높은 유동성**, **낮은 비용**의 장점을 제공하며, 다양한 자산군에 간편하게 투자할 수 있는 효율적인 금융 상품
    
- Key Points
    - Logstash를 2개 사용하는 이유와 효과
        
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
        
        ---
        
        **단점**
        
        1. **관리 복잡성 증가**:
            - Logstash 2개를 운영하면 설정 및 유지보수가 더 복잡해집니다. 각 Logstash의 파이프라인 및 동작을 세밀히 관리해야 합니다.
        2. **리소스 소모 증가**:
            - Logstash는 상대적으로 높은 CPU 및 메모리 사용량을 가지므로, 인스턴스를 2개로 늘릴 경우 서버 리소스 부담이 증가할 수 있습니다.
        3. **동기화 문제**:
            - 두 Logstash가 동일한 Elasticsearch와 상호작용할 경우 데이터 충돌 또는 동기화 문제를 방지하기 위해 추가적인 조정이 필요할 수 있습니다.
    - ES를 메인 저장소로 사용, RDBMS를 이관 저장소로 사용
        
        **ElasticSearch 메인, RDBMS 이관**:
        
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
        
        ### **적합한 사용 [프로젝트에서 보여지는]**
        
        - 실시간 대시보드에서 특정 ETF 카테고리 관련 기사를 빠르게 필터링.
        - 과거 데이터를 RDBMS에서 보관하며 월별/분기별 통계 보고서 생성.
        
        ---
        
        ### **주요 결정 요소**
        
        1. **뉴스 데이터의 주요 사용 목적**:
            - **실시간 검색과 분석**이 중요하다면 **ElasticSearch를 메인 저장소**로.
        2. **데이터 구조**:
            - 비정형 데이터(기사 본문 중심) → ElasticSearch.
            - 정형 데이터(관계형 모델로 관리 가능한 데이터) → RDBMS.
        3. **데이터 크기**:
            - **대용량 데이터 처리 및 고속 검색** → ElasticSearch.
            - **소규모 데이터 정리 및 관리** → RDBMS.
        
        ---
        
    - 크롤링
        1. 네이버 뉴스의 한 기사만 크롤링 해보기
            
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

            
</aside>

크롤링 사이트 : https://news.naver.com/

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
    
    ```sql
    input {
      elasticsearch {
        hosts => ["http://localhost:9200"]
        index => "etfnews"
        query => '{ "query": { "match_all": {} } }'  # 모든 데이터를 가져오는 쿼리
      }
    }
    
    filter {
      # 1. 데이터 정제: 필요한 필드만 추출하고 이름 매핑
      mutate {
        rename => {
          "type" => "category"  # 'type'을 'category'로 변경
          "value" => "status"   # 'value'를 'status'로 변경
        }
        remove_field => ["section", "category", "title"]  # 섹션, 분야, 제목은 제거
      }
    
      # 2. 데이터 집계: category별로 status를 집계
      aggregate {
        task_id => "%{category}"  # 각 category를 기준으로 작업 수행
        code => "
          map['count'] ||= {}
          map['count'][event.get('status')] ||= 0
          map['count'][event.get('status')] += 1
        "
        push_map_as_event_on_timeout => true
        timeout => 120
        timeout_task_id_field => "category"
      }
    
      # 3. 최대값 계산: 집계된 status 중 가장 큰 값을 선택
      ruby {
        code => "
          counts = event.get('count') || {}
          max_status = counts.max_by { |status, count| count }
          if max_status
            event.set('max_status', max_status[0])  # 가장 많은 status
            event.set('max_count', max_status[1])   # 해당 status의 개수
          else
            event.cancel  # 유효하지 않은 이벤트는 삭제
          end
        "
      }
    
      # 4. 불필요한 필드 제거 (최종 데이터 정리)
      mutate {
        remove_field => ["count"]  # 집계된 임시 필드 제거
      }
    }
    
    output {
      jdbc {
        jdbc_driver_library => "C:/Users/2-01/.m2/repository/mysql/mysql-connector-java/8.0.29/mysql-connector-java-8.0.29.jar"
        jdbc_driver_class => "com.mysql.cj.jdbc.Driver"
        jdbc_connection_string => "jdbc:mysql://localhost:3306/ETFnews"
        jdbc_user => "user01"
        jdbc_password => "user01"
        statement => [
          "INSERT INTO data_status (category, status) VALUES (?, ?)",
          "category", "max_status"
        ]
      }
    }
    
    ```
    

[mysql 서버 구축 윈도우 ](https://www.notion.so/mysql-2fc7f99791d242b6ba951e0ab8c4bba2?pvs=21)

# 🚀 트러블 슈팅
  <details>
  <summary> 인덱스 이름 : 대문자 불가 오류 발생 </summary>
  
  </details>
  
  <details>
  <summary> 트래킹 컬럼  이슈 : es에 계속 무한으로 저장됨 </summary>
  
  </details>

  <details>
  <summary> Logstash JDK 인식 문제 </summary>
  
  </details>

  <details>
  <summary> ES와 DB연결 문제 </summary>
  
  </details>
  
  <details>
    <summary> JDBC Driver </summary>
      
  - 설치 문제

     - **오류 내용: `logstash-output-jdbc` 플러그인 관련 오류**
      
     - **실제 오류 코드**:
                    
                    
                    복사편집
                    [2025-01-21T18:16:15,891][ERROR][logstash.plugins.registry] Tried to load a plugin's code, but failed. {:exception=>#<LoadError: no such file to load -- logstash/outputs/jdbc>, :path=>"logstash/outputs/jdbc", :type=>"output", :name=>"jdbc"}
                    [2025-01-21T18:16:15,903][FATAL][logstash.runner] The given configuration is invalid. Reason: Unable to configure plugins: (PluginLoadingError) Couldn't find any output plugin named 'jdbc'.
                    
  



   **해결 방법**:
  - `logstash-output-jdbc` 플러그인 재설치 명령 실행:
                                
                            
    
         복사편집
        logstash-plugin install logstash-output-jdbc
                                
                        
     </details>        
         
    <details>
        <summary>  
                오류 내용: JDK 인식 실패 문제
        </summary>
                    
     강제적으로 한번 더 인식 시켜주기
                    
                
                    set JAVA_HOME=C:\02.devEnv\ELK\logstash2-7.11.1\jdk
                    set PATH=%JAVA_HOME%\bin;%PATH%
                    logstash-plugin install logstash-output-jdbc

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
                

같은 path 참조 오류

![image 5](https://github.com/user-attachments/assets/a6083e0b-0855-4ce1-a4d4-d8d735275c1e)

1. DB - 이관 저장 / ES - main

![image](https://github.com/user-attachments/assets/ce52e6cd-fac1-4fa5-bf8c-e0cf57366731)


- 도메인(뉴스 기반으로 투자 추천)
    
    뉴스 → 키워드 → 주식
    
    - 뉴스 경제 관련 키워드 별 크롤링 ex)정치,전쟁
    - ETF 동향 파악
        1. 주식 ETF
        2. 채권-(장기/단기)  ETF
        3. 금 ETF
        4. 원자재 ETF
        
        ![image 3](https://github.com/user-attachments/assets/f524f570-4282-4301-8de7-c48061e3f980)

