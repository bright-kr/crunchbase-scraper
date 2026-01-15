# Crunchbase Scraper

[![Bright Data Promo](https://github.com/bright-kr/LinkedIn-Scraper/raw/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://brightdata.co.kr/products/web-scraper/crunchbase)

이 저장소는 Crunchbase에서 비즈니스 인텔리전스 데이터를 추출하기 위한 두 가지 접근 방식을 제공합니다:

1. **기본 스크레이핑 스크립트:** 제한된 데이터 수집을 위한 경량의 브라우저 자동화 스크레이핑 도구입니다.
2. **Bright Data Crunchbase Scraper API:** 대용량 및 신뢰할 수 있는 데이터 추출을 위한 견고하고 확장 가능하며 유지보수가 필요 없는 솔루션입니다.

## Table of Contents
- [Basic Crunchbase Scraper](#1-basic-crunchbase-scraper)
    - [Features](#features)
    - [Prerequisites](#prerequisites)
    - [Implementation](#implementation)
    - [Sample Output](#sample-output)
    - [Limitations & Challenges](#significant-limitations--challenges)
- [Bright Data Crunchbase Scraper API](#2-bright-data-crunchbase-scraper-api)
    - [Key Benefits](#key-benefits)
    - [Getting Started](#getting-started)
    - [API Methods](#api-methods)
      - [A. Collect Crunchbase Data by URL](#a-collect-crunchbase-data-by-url)
      - [B. Discover Crunchbase Data by Keyword](#b-discover-crunchbase-data-by-keyword)
- [API Configuration & Delivery Options](#api-configuration--delivery-options)
- [No-Code Scraper Interface](#no-code-scraper-interface)
- [Alternative: Pre-Collected Crunchbase Datasets](#alternative-pre-collected-crunchbase-datasets)
- [Resources & Support](#resources--support)


## 1. Basic Crunchbase Scraper

Crunchbase 프로필에서 기본적인 회사 데이터를 추출하는 방법을 보여주는 Python 구현입니다.

<img width="800" alt="Bright Data Platform Interface" src="https://github.com/bright-kr/crunchbase-scraper/blob/main/images/440236063-03b5a4c6-ba43-4595-bab8-96161740e197.png" />

### Features

이 스크립트는 다음을 포함하여 공개적으로 이용 가능한 데이터 포인트를 수집합니다:

- 회사 기본 정보(설명, 웹사이트, 설립일)
- 연락처 정보(이메일, 전화번호)
- 운영 지표(상태, 직원 수, 위치)
- 리더십 정보(창업자)
- 산업 분류

### Prerequisites

* Python 3.x 설치
* SeleniumBase 라이브러리: `pip install seleniumbase`

### Implementation

1. **코드 가져오기:** 스크립트 파일은 여기에서 확인합니다: [free-crunchbase-scraper/crunchbase-scraper.py](https://github.com/bright-kr/crunchbase-scraper/blob/main/free-crunchbase-scraper/crunchbase-scraper.py)
2. **대상 URL 설정:** 스크립트를 열고 `target_url` 변수를 스クレイピング하려는 특정 Crunchbase 회사 프로필로 수정합니다.
    
    ```python
    target_url = "https://www.crunchbase.com/organization/your-target-company"
    ```
    
3. **스크립트 실행:** 터미널에서 스크립트를 실행합니다: `python crunchbase-scraper.py`


💡 **Note:** 이 스크립트는 CAPTCHAs 및 기타 브라우저 챌린지를 처리하기 위한 내장 도구를 제공하는 고급 Selenium 래퍼인 [SeleniumBase](https://seleniumbase.io/)를 사용합니다. 자세히 알아보기: [Web Scraping with SeleniumBase](https://brightdata.co.kr/blog/web-data/web-scraping-with-seleniumbase) 및 [SeleniumBase with Proxies](https://brightdata.co.kr/blog/proxy-101/seleniumbase-with-proxies).


### Sample Output

이 스크립트는 다음 형식으로 구조화된 데이터를 추출합니다:

```jsonc
{
  "description": "Bright Data offers a platform for ethical web data collection and analysis.",
  "website_url": "[https://brightdata.co.kr](https://brightdata.co.kr/)",
  "founding_date": "2018-07-01",
  "email": "[sales@brightdata.com](mailto:sales@brightdata.com)",
  "phone": "(888) 538-9204",
  "company_overview": "Bright Data is a data collection platform that helps businesses gather publicly available web data...",
  "headquarters_location": "New York, United States, North America",
  "operating_status": "active",
  "employee_count": "251-500",
  "founder_names": [
    "Derry Shribman",
    "Ofer Vilenski"
  ],
  "industry_categories": [
    "Business Intelligence",
    "Cloud Data Services", "/* ... */"
  ]
}
```

### Significant Limitations & Challenges

이 접근 방식은 프로덕션 규모 데이터 수집에는 부적합하게 만드는 심각한 [web scraping challenges](https://brightdata.co.kr/blog/web-data/web-scraping-challenges)에 직면합니다:

- **IP 차단 및 속도 제한:** Crunchbase는 개별 IP 주소에서 발생하는 요청를 적극적으로 모니터링하고 제한합니다. 몇 차례 스크레이핑 시도 후 IP가 빠르게 차단될 가능성이 큽니다.
- **정교한 안티봇 대책:** Crunchbase는 CAPTCHAs(예: [Cloudflare Turnstile](https://brightdata.co.kr/products/web-unlocker/captcha-solver/cloudflare-turnstile)) 및 행동 분석을 포함한 고급 보안을 사용하며, 자동화 스크립트를 탐지하고 차단하도록 특별히 설계되어 있습니다.

  <img width="800" alt="Crunchbase CAPTCHA Challenge" src="https://github.com/bright-kr/crunchbase-scraper/blob/main/images/440239044-44cb5a79-e943-454b-9354-28b78ef67b57.png" />

- **동적 웹사이트 구조:** Crunchbase는 웹사이트 레이아웃과 코드를 자주 업데이트합니다. 어떤 변경이든 스크립트를 깨뜨릴 수 있어 지속적이고 시간 소모적인 유지보수가 필요합니다.
- **확장성 문제:** 이 방법은 여러 URL을 효율적으로 처리하거나 대량의 데이터를 처리하도록 확장할 수 없습니다.
- **유지보수 오버헤드:** 인프라 관리, 차단 대응, 스크립트 업데이트, 규정 준수 보장을 사용자가 직접 담당해야 합니다.


## 2. Bright Data Crunchbase Scraper API
[Bright Data Crunchbase Scraper API](https://brightdata.co.kr/products/web-scraper/crunchbase)는 스크레이핑의 복잡성을 다루지 않고도 Crunchbase에서 포괄적인 데이터를 추출할 수 있는 견고하고 확장 가능하며 번거로움이 없는 방법을 제공합니다.

### Key Benefits

- **기술적 과제 우회:** 고급 프록시 로ーテ이션 및 웹 언락킹 기술을 사용하여 IP 차단, CAPTCHAs, 속도 제한을 자동으로 처리합니다.
- **엔터프라이즈 확장성:** 대용량 데이터 수집을 위해 설계되었습니다.
- **높은 신뢰성:** 엔터프라이즈급 가동 시간으로 일관된 데이터 전달을 보장합니다.
- **개발자 친화적:** 간단한 API 통합으로 복잡한 스크레이핑 도구 개발 및 유지보수가 필요 없습니다.
- **구조화된 데이터 형식:** 분석 준비가 된 깔끔하고 정규화된 데이터를 제공합니다.
- **규제 준수:** GDPR 및 CCPA를 포함한 데이터 프라이버시 규정을 준수합니다.
- **유연한 가격:** 성공적인 데이터 전달을 기준으로 하는 종량제 모델입니다.
- **전담 지원:** 24/7 전문가 기술 지원을 이용할 수 있습니다.
- **구현 옵션:** API를 프로그래밍 방식으로 사용하거나 [No-Code Scraper](https://brightdata.co.kr/products/web-scraper/no-code) 인터페이스를 통해 사용할 수 있습니다.

### Getting Started

1. **계정 생성:** [Bright Data account](https://brightdata.co.kr/)에 가입합니다 *(신규 사용자는 결제 수단을 추가하면 $5 크레딧을 받습니다)*.
2. **API 토큰 생성:** 대시보드에서 고유한 [API key](https://docs.brightdata.com/general/account/api-token)를 발급받습니다.
3. **구현 가이드:** 두 API 방법과 No-Code 인터페이스 모두에 대한 상세 구성 단계는 다음을 참조하십시오:
[setup-bright-data-crunchbase-scraper.md](https://github.com/bright-kr/crunchbase-scraper/blob/main/setup-bright-data-crunchbase-scraper.md)


### API Methods

이 API는 두 가지 주요 데이터 수집 접근 방식을 제공합니다:

### A. Collect Crunchbase Data by URL

특정 Crunchbase 회사 URL에 대한 포괄적인 프로필 정보를 가져옵니다.

**입력 파라미터:**

| Parameter | Required | Description |
| --- | --- | --- |
| `url` | Yes | 전체 Crunchbase 회사 URL입니다. |

**요청 예시 (Python):**

```python
config = {
    "api_token": "YOUR_API_TOKEN",  # Replace with actual token
    "organizations": [
        {"url": "https://www.crunchbase.com/organization/apple"},
        {"url": "https://www.crunchbase.com/organization/brightdata"},
    ],
    "output_file": "crunchbase-company-profiles.json", # Optional custom filename
}
# ... rest of the script uses this config
```

- `"YOUR_API_TOKEN"`을 실제 Bright Data API 토큰으로 교체하십시오.
- `organizations` 목록을 대상 Crunchbase URL로 수정하십시오.
- 실행 가능한 전체 스크립트는 여기에서 확인하십시오: [crunchbase-scraper-api/crunchbase-profile-fetcher.py](https://github.com/bright-kr/crunchbase-scraper/blob/main/crunchbase-scraper-api/crunchbase-profile-fetcher.py)

**요청 예시 (cURL):**

```bash
curl -X POST \
  "https://api.brightdata.com/datasets/v3/trigger?dataset_id=gd_l1vijqt9jfj7olije&include_errors=true" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '[{"url":"https://www.crunchbase.com/organization/apple"},{"url":"https://www.crunchbase.com/organization/brightdata"}]'
```


**샘플 출력 일부:**

API는 포괄적이고 구조화된 데이터를 반환합니다. 아래는 단일 회사에 대해 사용 가능한 필드의 일부 예시입니다:

```jsonc
{
  "companyName": "Bright Data",
  "legalName": "Bright Data",
  "website": "https://brightdata.co.kr",
  "description": "Offers a platform for ethical web data collection and analysis...",
  "foundedDate": "2014-01-01",
  "location": {"city": "New York", "state": "New York", "country": "United States"},
  "companyType": "For-Profit",
  "operatingStatus": "Active",
  "ipoStatus": "Private (Acquired)",
  "employeeSizeRange": "251-500",
  "industries": ["Business Intelligence", "Cloud Data Services", "..."],
  "keyPersonnel": {
    "ceo": {"name": "Or Lenchner", "...": "..."},
    "founders": [{"name": "Derry Shribman", "...": "..."}, {"name": "Ofer Vilenski", "...": "..."}]
  },
  "webTraffic": {"monthlyVisits": 865525, "source": "Semrush", "...": "..."},
  "technology": {"activeTechCount": 19, "exampleTechUsed": ["Cloudflare Hosting", "..."]},
  "products": {"totalActive": 23, "exampleProductNames": ["Residential Proxies", "..."]},
  "acquisitionDetails": {"acquiredBy": "EMK Capital", "priceUSD": 200000000, "...": "..."},
  "intellectualProperty": {"patentsGranted": 199, "trademarksRegistered": 18}
  // Additional data fields available
}
```

전체 샘플 응답 보기: [crunchbase-data/crunchbase-company-profiles.json](https://github.com/bright-kr/crunchbase-scraper/blob/main/crunchbase-data/crunchbase-company-profiles.json)

### B. Discover Crunchbase Data by Keyword

특정 키워드 또는 산업(예: "AI", "Venture Capital", "SaaS")과 연관된 회사를 식별합니다.

<img width="800" alt="Discover by Keyword Interface Example" src="https://github.com/bright-kr/crunchbase-scraper/blob/main/images/440271152-56e59e94-19fa-4977-84a0-4b70c794cb20.png" />

**입력 파라미터:**

| Parameter | Required | Description |
| --- | --- | --- |
| `keyword` | Yes | 관련 회사를 검색할 키워드입니다. |

**요청 예시 (Python):**

```python
config = {
    "api_token": "YOUR_API_TOKEN",  # Replace with actual token
    "keywords": [
        {"keyword": "AI"},
        {"keyword": "Venture Capital"},
        {"keyword": "SaaS"}
        # Add more keywords as needed
    ],
    "output_file": "crunchbase-keyword-results.json", # Optional: Customize output filename
}
# ... (script uses this config to make the API call)
```

- `"YOUR_API_TOKEN"`을 교체하십시오.
- `keywords` 목록을 수정하십시오.
- 실행 가능한 전체 스크립트는 여기에서 확인하십시오: [`crunchbase-scraper-api/crunchbase-keyword-search.py`](https://github.com/bright-kr/crunchbase-scraper/blob/main/crunchbase-scraper-api/crunchbase-keyword-search.py)

**요청 예시 (cURL):**

```bash
curl -X POST \
  "https://api.brightdata.com/datasets/v3/trigger?dataset_id=gd_l1vijqt9jfj7olije&include_errors=true&type=discover_new&discover_by=keyword" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '[{"keyword":"AI"},{"keyword":"Venture Capital"}]'

```

**샘플 출력 일부:**

응답에는 키워드 검색과 일치하는 *여러* 회사의 데이터가 포함됩니다. 아래는 한 개 결과의 구조를 보여줍니다:

```jsonc
{
  "companyName": "Airbus", // Example result for "AI" keyword
  "legalName": "Airbus Defense and Space Holdings, Inc.",
  "website": "https://us.airbus.com",
  "description": "Airbus designs, manufactures, and delivers aerospace products...",
  "foundedDate": "2014-01-01",
  "location": {
    "city": "Herndon",
    "state": "Virginia",
    "country": "United States"
  },
  "companyType": "For-Profit",
  "operatingStatus": "Active",
  "ipoStatus": "Private",
  "employeeSizeRange": "10001+",
  "industries": [
    "Aerospace",
    "Commercial",
    "Manufacturing"
  ],
  // ... includes similar detailed fields as the 'Collect by URL' method
}
```

전체 샘플 응답 보기: [crunchbase-data/crunchbase-keyword-results.json](https://github.com/bright-kr/crunchbase-scraper/blob/main/crunchbase-data/crunchbase-keyword-results.json)

### API Configuration & Delivery Options

API 요청 내 추가 파라미터를 사용하여 데이터 수집 작업을 커스터마이즈할 수 있습니다:

| Parameter | Type | Description | Example |
| --- | --- | --- | --- |
| `limit` | `integer` | 입력( URL 또는 키워드)당 최대 결과 수를 설정합니다. | `limit=50` |
| `include_errors` | `boolean` | 문제가 발생할 경우 응답에 상세 오류 정보를 포함합니다. | `include_errors=true` |
| `format` | `enum` | 원하는 출력 형식(`json`, `csv`, `ndjson`)을 지정합니다. | `format=csv` |
| `notify` | `url` | 작업 완료 시 알림을 받을 webhook URL을 제공합니다. | `notify=https://...` |

데이터는 선호하는 [external storage](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview#via-deliver-to-external-storage%3A)로 직접 전달하거나, [webhook](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/overview#via-webhook%3A)을 통해 전달할 수 있습니다.

Web Scraper API 및 수집 트리거에 대한 종합 문서는 다음을 참조하십시오:

- [Bright Data Web Scraper API Documentation](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview)
- [Trigger Collection API Reference](https://docs.brightdata.com/api-reference/web-scraper-api/trigger-a-collection)



### No-Code Scraper Interface

시각적 포인트앤클릭 방식을 선호하는 사용자를 위해 Bright Data는 [No-Code Scraper](https://brightdata.co.kr/products/web-scraper/no-code)도 제공합니다. 이 인터페이스를 사용하면 코드를 작성하지 않고도 동일한 강력한 기반 인프라를 활용하여 Crunchbase 데이터 수집 작업을 구성하고 실행할 수 있습니다. 안내는 [Setup Guide](https://github.com/bright-kr/crunchbase-scraper/blob/main/setup-bright-data-crunchbase-scraper.md)를 참조하십시오.

## Alternative: Pre-Collected Crunchbase Datasets

직접 스크레이핑 작업을 실행하지 않고도 대량의 구조화된 Crunchbase 데이터를 즉시 이용해야 한다면, Bright Data의 사전 수집된 [Crunchbase Datasets](https://brightdata.co.kr/products/datasets/crunchbase)를 고려하십시오.

- **즉시 사용 가능:** 검증되고 구조화된 Crunchbase 데이터에 즉시 접근합니다.
- **포괄적인 커버리지:** 데이터셋에는 회사 프로필당 100개 이상의 데이터 포인트가 포함됩니다.
- **정기 업데이트:** 다양한 데이터 최신성 옵션(일간, 주간, 월간 또는 커스텀) 중에서 선택합니다.
- **유연한 구매 옵션:** 전체 데이터셋 또는 요구사항과 예산에 맞춘 특정 서브셋을 구매할 수 있습니다.
- **쉬운 통합:** API 또는 직접 다운로드로 데이터셋을 원활하게 통합합니다.
- **샘플 데이터 제공:** 데이터 품질과 적합성을 평가할 수 있도록 샘플을 요청할 수 있습니다.


## Resources & Support

- **Bright Data Documentation:**
    - [Crunchbase Scraper API Product Page](https://brightdata.co.kr/products/web-scraper/crunchbase)
    - [Web Scraper API Documentation](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview)
    - [API Reference: Trigger Collection](https://docs.brightdata.com/api-reference/web-scraper-api/trigger-a-collection)
    - [Datasets Product Page](https://brightdata.co.kr/products/datasets)
    - [Getting Your API Token](https://docs.brightdata.com/general/account/api-token)
- **Guides & Blog Posts:**
    - [How to Scrape Crunchbase (Comprehensive Guide)](https://brightdata.co.kr/blog/web-data/how-to-scrape-crunchbase)
    - [Web Scraping Without Getting Blocked](https://brightdata.co.kr/blog/web-data/web-scraping-without-getting-blocked)
    - [Setup Guide for Bright Data Crunchbase Scraper (in this repo)](https://github.com/bright-kr/crunchbase-scraper/blob/main/setup-bright-data-crunchbase-scraper.md)
- **Technical Support:** 계정 대시보드를 통해 24/7 Bright Data 지원팀에 문의하거나 [support@brightdata.com](mailto:support@brightdata.com)으로 이메일을 보내실 수 있습니다.