# 가상 미래에이전트 연구를 위한 데이터 설명

<p align="right">작성자: 이주현 (최종 편집일: 2026-5-6)</p>

## **1. 데이터 개요**

- 본 문서는 KISTI 에이전트응용연구센터에서 가상 미래에이전트 연구를 위해 필요한 데이터에 대한 해설 자료임
- [Leiden CWTS Cluster (Open Edition) 2025](https://open.leidenranking.com/) 데이터와 [OpenAlex Snapshot 데이터](https://openalex.s3.amazonaws.com/browse.html) (2026년 4월 14일 다운로드)를 병합한 결과임
- Leiden CWTS Cluster (Open Edition) 2025는 2006년부터 2023년 사이에 출판된 논문 **46,136,771건**(**=데이터A**)으로 구성되어 있으며, 총 [4,521개](https://open.leidenranking.com/information/fields)의 micro-level cluster 정보가 할당되어 있음
- OpenAlex Snapshot을 가져와 파싱했으며, **총 492,361,307건**(**=데이터B**)"의 논문이 존재함
- 아래 서술된 "**분석 데이터**"는 **데이터A**를 기준으로 [데이터B에서 분석에 필요한 정보](https://github.com/lee-ju/leiden_open2025/Tables.md)를 추출해서 병합한 결과임
<br>

## **2. 개발 환경**

### **2.1 파이썬 및 패키지 버전**
- python _3.11.15_
- numpy _2.4.3_
- pandas _3.0.1_
- pyarrow _23.0.1_
<br>

### **2.2 파일 저장 및 로딩**
- 파일 용량 관리 및 로딩 효율성을 위해 pickle이 아닌 [pyarrow.parquet](https://arrow.apache.org/docs/python/parquet.html)을 패키지를 활용해서 저장함
- pyarrow.parquet은 파일 용량 관리에 효과적이며, 특정 컬럼만 지정해서 로딩할 수 있는 장점이 있음
- 로딩에는 pandas.read_parquet을 사용하며, 이후 pandas.DataFrame과 동일한 방식으로 작업이 가능함
- pyarrow.parquet으로 저장한 "biblio.pq" 파일을 불러오는 파이썬 코드는 아래와 같음

```python
import pandas as pd
df1 = pd.read_parquet(".../leiden_open2025_biblio.pq")

# 특정 컬럼만 불러오는 경우
df2 = pd.read_parquet(".../leiden_open2025_biblio.pq", columns=["oaid_w", "publication_year"])
print(df2.shape[1]) # [Out] 2
```
<br>

## **3. 분석 데이터**

### **3.1 서지 정보 데이터 (`leiden_open2025_biblio.pq`)**

- 데이터A에 대한 서지 정보를 추출한 결과임
- **총 46,136,771건**에 대한 **54개 필드**

| 번호 | 필드 | 내용 |
|---|---|---|
| 1 | `oaid_w` | OpenAlex 논문 고유 ID (W로 시작하는 가변길이 문자열) |
| 2 | `doi` | 논문의 DOI 링크 |
| 3 | `publication_year` | 출판년도 |
| 4 | `is_core_pub` | [core 저널 여부](https://open.leidenranking.com/information/indicators) |
| 5 | `cluster_id` | [Leiden 클러스터 번호](https://open.leidenranking.com/information/fields) |
| 6 | `title` | 논문 제목 |
| 7 | `language` | 논문 언어 |
| 8 | `is_oa` | Open Access (OA) 여부 |
| 9 | `oa_status` | OA 상태 (green, gold 등) |
| 10 | `is_retracted` | 철회논문 여부 |
| 11 | `is_paratext` | 서문 포함 여부 |
| 12 | `is_indexed_in_crossref` | CrossRef 인덱싱 여부 |
| 13 | `is_indexed_in_arxiv` | ArXiv 인덱싱 여부 |
| 14 | `is_indexed_in_pubmed` | PubMed 인덱싱 여부 |
| 15 | `source_display_name` | source 등의 명칭 |
| 16 | `has_source` | 저널 등(source라 칭함)에 관한 정보 포함 여부 |
| 17 | `oaid_s` | source의 고유 ID (S로 시작하는 가변길이 문자열) |
| 18 | `any_repository_has_fulltext` | 전문을 포함하는 repository 존재 여부 |
| 19 | `apc_list_value` | Article Processing Charge (APC) 비용 |
| 20 | `apc_list_currency` | APC 화폐 단위 (USD 등) |
| 21 | `apc_list_value_usd` | USD로 변환한 APC |
| 22 | `apc_paid_value` | 지불된 APC 비용 |
| 23 | `apc_paid_currency` | 지불된 APC의 화폐 단위 (USD 등) |
| 24 | `apc_paid_value_usd` | 지불된 APC 비용 (USD 기준) |
| 25 | `has_concept` | [concept](https://developers.openalex.org/api-reference/concepts) entity 포함 여부 |
| 26 | `has_grant` | [grant](https://developers.openalex.org/api-reference/works/get-a-single-work#response-awards) entity 포함 여부 |
| 27 | `has_keyword` | [keyword](https://developers.openalex.org/api-reference/works/get-a-single-work#response-keywords) entity 포함 여부 |
| 28 | `has_referencedwork` | [referenced work](https://developers.openalex.org/api-reference/works/get-a-single-work#response-referenced-works) entity 포함 여부 |
| 29 | `has_relatedwork` | [related work](https://developers.openalex.org/api-reference/works/get-a-single-work#response-related-works) entity 포함 여부 |
| 30 | `has_sdg` | [sdg](https://developers.openalex.org/api-reference/sdgs) entity 포함 여부 |
| 31 | `has_topic` | [topic](https://github.com/ourresearch/openalex-topic-classification/tree/main) entity 포함 여부 |
| 32 | `primary_topic_id` | topic entity 중 첫 번째 토픽 고유 ID (T로 시작하는 가변길이 문자열) |
| 33 | `primary_topic` | topic entity 중 첫 번째 토픽 |
| 34 | `primary_topic_score` | topic entity 중 첫 번째 [토픽 점수](https://docs.google.com/document/d/1bDopkhuGieQ4F8gGNj7sEc8WSE8mvLZS/edit?pli=1#heading=h.5w2tb5fcg77r) |
| 35 | `primary_domain_id` | topic entity 중 첫 번째 도메인 고유 ID (접두사 없는 문자열. 예: `"3"`) |
| 36 | `primary_domain` | topic entity 중 첫 번째 도메인 |
| 37 | `primary_field_id` | topic entity 중 첫 번째 필드 고유 ID (접두사 없는 문자열. 예: `"3"`) |
| 38 | `primary_field` | topic entity 중 첫 번째 필드 |
| 39 | `primary_subfield_id` | topic entity 중 첫 번째 서브필드 고유 ID (접두사 없는 문자열. 예: `"3"`) |
| 40 | `primary_subfield` | topic entity 중 첫 번째 서브필드 |
| 41 | `countries_distinct_count` | 저자 소속기관이 분포한 국가 수 |
| 42 | `authors_count` | 저자 수 |
| 43 | `corresponding_authors_count` | 교신저자 수 |
| 44 | `topics_count` | 토픽 수 |
| 45 | `concepts_count` | [컨셉](https://developers.openalex.org/api-reference/concepts) 수 |
| 46 | `referenced_works_count` | 레퍼런스 수 |
| 47 | `locations_count` | 논문에 접근 가능한 위치(`locations`) 수 |
| 48 | `cited_by_count` | 인용 횟수. [* cited_by_count for each of the last ten years](https://developers.openalex.org/api-reference/works/get-a-single-work#response-counts-by-year)|
| 49 | `fwci` | Field-weighted Citation Impact |
| 50 | `citation_normalized_percentile` | 연도 및 서브필드 등의 분야별 정규화된 인용 백분위수 |
| 51 | `is_in_top_1_percent` | 상위 1% 인용 여부 |
| 52 | `is_in_top_10_percent` | 상위 10% 인용 여부 |
| 53 | `cited_by_percentile_year_min` | 동일 연도에 발표된 다른 연구 결과와 비교한 인용 백분위 수 (최소값) |
| 54 | `cited_by_percentile_year_max` | 동일 연도에 발표된 다른 연구 결과와 비교한 인용 백분위 수 (최대값) |
<br>

### **3.2 텍스트 데이터 (`leiden_open2025_text.pq`)**

- 데이터A에 대한 초록 정보를 추출한 결과임
- **총 46,136,771건**에 대한 **7개 필드**

| 번호 | 필드 | 내용 |
|---|---|---|
| 1 | `oaid_w` | OpenAlex 논문 고유 ID (W로 시작하는 가변길이 문자열) |
| 2 | `doi` | 논문의 DOI 링크 |
| 3 | `publication_year` | 출판년도 |
| 4 | `cluster_id` | [Leiden 클러스터 번호](https://open.leidenranking.com/information/fields) |
| 5 | `is_core_pub` | [core 저널 여부](https://open.leidenranking.com/information/indicators) |
| 6 | `has_abstract` | 초록 포함 여부 |
| 7 | `abstract` | 초록 |
<br>

### **3.3 참고문헌 데이터 (`leiden_open2025_link/link_<YEAR>.pq`)**

- 데이터A에 대한 참고문헌 정보를 추출한 결과임
- 각 논문의 참고문헌이 여러 행으로 존재함
- 2006년부터 2023년까지 데이터A에 대한 참고문헌 **총 1,598,747,915건**임
- 연도별 참고문헌 데이터에는 **7개 필드**가 있음

| 번호 | 필드 | 내용 |
|---|---|---|
| 1 | `oaid_w` | OpenAlex 논문 고유 ID (W로 시작하는 가변길이 문자열) |
| 2 | `publication_year` | 출판년도 |
| 3 | `cluster_id` | [Leiden 클러스터 번호](https://open.leidenranking.com/information/fields) |
| 4 | `is_core_pub` | [core 저널 여부](https://open.leidenranking.com/information/indicators) |
| 5 | `has_referencedwork` | 참고문헌 포함 여부 |
| 6 | `referenced_works_count` | 참고문헌 수 |
| 7 | `referenced_oaid_w` | 참고문헌의 `oaid_w` |
