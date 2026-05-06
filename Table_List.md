# 테이블 리스트

<p align="right">작성자: 이주현 (최종 편집일: 2026-5-6)</p>

## **1. 데이터 개요**
- 본 테이블 리스트는 [OpenAlex Snapshot 데이터](https://openalex.s3.amazonaws.com/browse.html) (2026년 4월 14일 다운로드)를 파싱한 결과임
- works 테이블 기준, **총 492,361,307건**의 논문이 존재함
<br>

## **2. 테이블 리스트**
- 총 9개의 테이블이 존재함
- (1) cwts
- (2) works
- (3) works_abstract
- (4) works_counts
- (5) works_grants
- (6) works_keywords
- (7) works_referencedworks
- (8) works_relatedworks
- (9) works_topics

| No | Table | FIELD | DESCRIPTION |
|---:|---|---|---|
| 1 | cwts | oaid_w | OpenAlex ID for the work (unique identifier. Start with 'W'). |
| 2 | cwts | doi | Digital Object Identifier (DOI) for the work. |
| 3 | cwts | publication_year | The year the work was published. |
| 4 | cwts | is_core_pub | Flag indicating if oaid_w published core journal |
| 5 | cwts | cluster_id | CWTS Open Edition micro-level cluster id |
| 6 | works | oaid_w | OpenAlex ID for the work (unique identifier. Start with 'W'). |
| 7 | works | title | The title of the work. |
| 8 | works | publication_year | The year the work was published. |
| 9 | works | publication_date | The date the work was published (ISO 8601). |
| 10 | works | language | The language the work is written in (ISO 639-1 format). |
| 11 | works | is_oa | Boolean indicating if the work is open access. |
| 12 | works | oa_status | The open access status (gold, green, hybrid, bronze, closed). |
| 13 | works | is_retracted | Boolean indicating if the work has been retracted. |
| 14 | works | is_paratext | Boolean indicating if the work is paratext (e.g., front matter). |
| 15 | works | is_indexed_in_crossref | Boolean indicating if indexed in Crossref. |
| 16 | works | is_indexed_in_arxiv | Boolean indicating if indexed in arXiv. |
| 17 | works | is_indexed_in_pubmed | Boolean indicating if indexed in PubMed. |
| 18 | works | doi | Digital Object Identifier (DOI) for the work. |
| 19 | works | issn_l | The linking ISSN for the source (journal). |
| 20 | works | source_display_name | The name of the source (journal) where published. |
| 21 | works | version | The version of the work (e.g., publishedVersion). |
| 22 | works | has_source | Flag indicating existence of a source. |
| 23 | works | oaid_s | Primary code name (start with ‘S’) of the source (journal) where published. |
| 24 | works | volume | Journal volume number. |
| 25 | works | issue | Journal issue number. |
| 26 | works | first_page | First page of the work. |
| 27 | works | last_page | Last page of the work. |
| 28 | works | oa_url | URL to the open access version of the work. |
| 29 | works | any_repository_has_fulltext | Flag if any repository contains fulltext. |
| 30 | works | apc_list_value | Listed Article Processing Charge (APC). |
| 31 | works | apc_list_currency | Currency for the listed APC. |
| 32 | works | apc_list_value_usd | Listed APC value in USD. |
| 33 | works | apc_list_provenance | Provenance of the listed APC. |
| 34 | works | apc_paid_value | Actual APC paid. |
| 35 | works | apc_paid_currency | Currency for the actual APC paid. |
| 36 | works | apc_paid_value_usd | Actual APC paid in USD. |
| 37 | works | apc_paid_provenance | Provenance of the actual APC paid. |
| 38 | works | has_concept | Flag indicating existence of a concept. |
| 39 | works | has_grant | Flag indicating existence of a grant. |
| 40 | works | has_keyword | Flag indicating existence of a keyword. |
| 41 | works | has_referencedwork | Flag indicating existence of a referenced work. |
| 42 | works | has_relatedwork | Flag indicating existence of a related work. |
| 43 | works | has_sdg | Flag indicating existence of a sdg. |
| 44 | works | has_topic | Flag indicating existence of topics. |
| 45 | works | primary_topic_id | OpenAlex ID for the topic. |
| 46 | works | primary_topic | The display name of the topic. |
| 47 | works | primary_topic_score | Connection strength score for the topic. |
| 48 | works | primary_domain_id | Identifier for the topic domain. |
| 49 | works | primary_domain | Display name of the domain. |
| 50 | works | primary_field_id | Identifier for the topic field. |
| 51 | works | primary_field | Display name of the field. |
| 52 | works | primary_subfield_id | Identifier for the topic subfield. |
| 53 | works | primary_subfield | Display name of the subfield. |
| 54 | works | updated_date | Date the record was last updated in OpenAlex. |
| 55 | works | created_date | Date the record was created in OpenAlex. |
| 56 | works_abstract | oaid_w | OpenAlex ID for the work (unique identifier. Start with 'W'). |
| 57 | works_abstract | has_abstract | Flag indicating if an abstract exists. |
| 58 | works_abstract | abstract | The full text of the work's abstract. |
| 59 | works_counts | oaid_w | OpenAlex ID for the work (unique identifier. Start with 'W'). |
| 60 | works_counts | countries_distinct_count | Count of distinct countries among affiliations. |
| 61 | works_counts | institutions_distinct_count | Count of distinct institutions among affiliations. |
| 62 | works_counts | corresponding_institutions_count | Count of institutions of corresponding authors. |
| 63 | works_counts | authors_count | Total number of authors. |
| 64 | works_counts | corresponding_authors_count | Total number of corresponding authors. |
| 65 | works_counts | topics_count | Number of topics assigned to the work. |
| 66 | works_counts | concepts_count | Number of concepts assigned to the work. |
| 67 | works_counts | referenced_works_count | Number of works that this work cites. |
| 68 | works_counts | locations_count | Number of locations where the work is available. |
| 69 | works_counts | cited_by_count | Total number of citations received. |
| 70 | works_counts | fwci | Field-weighted Citation Impact, calculated as citations received. |
| 71 | works_counts | citation_normalized_percentile | Percentile of citation count normalized by work type, year, and subfield. |
| 72 | works_counts | is_in_top_1_percent | Boolean indicating if in top 1% by citations. |
| 73 | works_counts | is_in_top_10_percent | Boolean indicating if in top 10% by citations. |
| 74 | works_counts | cited_by_percentile_year_min | Min(Percentile rank compared to other works published in the same year.) |
| 75 | works_counts | cited_by_percentile_year_max | Max(Percentile rank compared to other works published in the same year) |
| 76 | works_counts | updated_date | Date the record was last updated in OpenAlex. |
| 77 | works_counts | created_date | Date the record was created in OpenAlex. |
| 78 | works_grants | oaid_w | OpenAlex ID for the work (unique identifier. Start with 'W'). |
| 79 | works_grants | has_grant | Flag indicating if grants exist. |
| 80 | works_grants | funders_count | Number of funders assigned. |
| 81 | works_grants | oaid_f | Primary code name (start with ‘F’) of the funder. |
| 82 | works_grants | funder_display_name | Name of the funder. |
| 83 | works_grants | award_id | Funding ID (Ex. K26L2M3C7) |
| 84 | works_keywords | oaid_w | OpenAlex ID for the work (unique identifier. Start with 'W'). |
| 85 | works_keywords | has_keyword | Flag indicating if keywords exist. |
| 86 | works_keywords | keywords_count | Number of keywords assigned. |
| 87 | works_keywords | keyword_seq | Sequence number for keyword ranking. |
| 88 | works_keywords | keywords | List of keyword strings for the work. |
| 89 | works_keywords | keyword_score | Score for the keyword assignment. |
| 90 | works_referencedworks | oaid_w | OpenAlex ID for the work (unique identifier. Start with 'W'). |
| 91 | works_referencedworks | has_referencedwork | Flag indicating existence of referenced works. |
| 92 | works_referencedworks | referenced_works_count | Number of works that this work cites. |
| 93 | works_referencedworks | referenced_oaid_w | OpenAlex ID of the referenced work. |
| 94 | works_relatedworks | oaid_w | OpenAlex ID for the work (unique identifier. Start with 'W'). |
| 95 | works_relatedworks | has_relatedwork | Flag indicating existence of related works. |
| 96 | works_relatedworks | related_works_count | Number of related works. |
| 97 | works_relatedworks | work_seq | Sequence number for related work ranking. |
| 98 | works_relatedworks | related_oaid_w | OpenAlex ID of the related work. |
| 99 | works_topics | oaid_w | OpenAlex ID for the work (unique identifier. Start with 'W'). |
| 100 | works_topics | has_topic | Flag indicating existence of topics. |
| 101 | works_topics | topics_count | Number of topics assigned to the work. |
| 102 | works_topics | topic_seq | Sequence number for topic ranking. |
| 103 | works_topics | topic_id | OpenAlex ID for the topic. |
| 104 | works_topics | topic | The display name of the topic. |
| 105 | works_topics | topic_score | Connection strength score for the topic. |
| 106 | works_topics | domain_id | Identifier for the topic domain. |
| 107 | works_topics | domain | Display name of the domain. |
| 108 | works_topics | field_id | Identifier for the topic field. |
| 109 | works_topics | field | Display name of the field. |
| 110 | works_topics | subfield_id | Identifier for the topic subfield. |
| 111 | works_topics | subfield | Display name of the subfield. |
<br>
