# Setting Up the Bright Data Crunchbase Scraper

이 가이드는 Crunchbase를 위한 Bright Data Web Scraper를 설정하고 사용하는 방법을 단계별로 안내합니다. Bright Data의 강력한 인프라를 활용하여 API를 통해 프로그래밍 방식으로 또는 사용하기 쉬운 노코드 인터페이스를 통해 Crunchbase 프로필에서 데이터를 수집할 수 있습니다.

**Prerequisites:**

* 활성화된 Bright Data 계정이 필요합니다.

## Steps

1.  **Bright Data에 로그인합니다:**
    Bright Data 대시보드에 접속합니다.
2.  **Web Scrapers Library로 이동합니다:**
    * 왼쪽 메뉴에서 **Web Scrapers** 탭을 선택합니다.
    * **Web Scrapers Library** 하위 탭을 선택합니다.

    ![Bright Data Dashboard](https://github.com/user-attachments/assets/f680db57-a15a-4bd9-8dfc-f7cab5e3219b)

3.  **Crunchbase Scraper를 찾습니다:**
    * 검색창을 사용하여 "crunchbase"를 입력합니다.
    * 검색 결과에서 **crunchbase.com** 스크레이퍼를 선택합니다.

    ![Search for Crunchbase Scraper](https://github.com/user-attachments/assets/faf6ef56-859c-4cd9-baef-ace81d6cfe1d)

4.  **스크레이퍼 유형을 선택합니다:**
    Crunchbase에 사용할 수 있는 다양한 스크레이퍼 템플릿이 표시됩니다. 이 가이드는 **Collect by URL** 옵션에 중점을 둡니다. 해당 옵션을 선택합니다.

    ![Select Collect by URL](https://github.com/user-attachments/assets/fc1cc4dc-b637-44db-b782-81a9be0cf92f)

5.  **상호작용 방법을 선택합니다:**
    Bright Data는 스크레이퍼를 사용하는 두 가지 방법을 제공합니다:
    * **Scraper APIs:** 애플리케이션에 프로그래밍 방식으로 통합하기 위한 방식입니다.
    * **No-code scraper:** 코드를 작성하지 않고 사용자 인터페이스 기반으로 접근하는 방식입니다.

    필요에 가장 적합한 방법을 선택한 다음 **Next**를 선택합니다.

    ![Choose Scraper API or No-code](https://github.com/user-attachments/assets/3b9518a2-ce00-4e90-9f8b-44ff3be30d54)

### Option A: Using the Scraper API

**Scraper APIs**를 선택했다면 API 구성 대시보드로 이동합니다.

![Crunchbase Scraper API Dashboard](https://github.com/user-attachments/assets/63e80d6e-5c57-4f2e-8d3c-300baa5f43a1)

**Configuration and Usage:**

1.  **API Request Builder:**
    * **Inputs:** 스크레이핑할 특정 Crunchbase URL을 추가합니다.
    * **Output Format:** 원하는 데이터 형식(JSON, CSV)을 선택합니다.
    * **Data Delivery:** 데이터를 수신할 방법을 구성합니다:
        * [Deliver to External Storage](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview#via-deliver-to-external-storage%3A) (예: Email, S3, Google Cloud Storage, SFTP).
        * [Send to Webhook](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview#via-webhook%3A).
    * **Notifications:** 작업 완료 또는 실패 시 알림을 받을 URL을 설정합니다.

2.  **스크레이퍼 실행:**
    * 설정을 조정하면 오른쪽의 요청 빌더가 자동으로 업데이트됩니다.
    * 즉시 사용할 수 있는 **cURL command** 또는 다양한 프로그래밍 언어(Python, Node.js, Java, C#, PHP 등)의 코드 스니펫을 제공합니다.
    * 생성된 코드를 복사하여 터미널에서 실행하거나 애플리케이션에 통합합니다.

3.  **추가 기능:**
    * **Overview Tab:** API 사용에 대한 일반 정보입니다.
    * **Management APIs Tab:** 스크레이퍼 인스턴스를 프로그래밍 방식으로 관리하기 위한 API입니다.
    * **Logs Tab:** API 요청 및 스크레이퍼 실행에 대한 상세 로그입니다.

모든 설정에 대한 포괄적인 개요는 [Web Scraper API Documentation](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview)를 참조하십시오.

### Option B: Using the No-code Scraper

**No-code scraper**를 선택했다면 구성을 위한 사용자 친화적인 인터페이스가 표시됩니다.

**Configuration and Execution:**

1.  **Input URLs:**
    * 여러 Crunchbase URL을 입력 필드에 직접 붙여넣습니다(한 줄에 URL 1개).
    * 또는 URL 목록이 포함된 **CSV file**을 업로드합니다.

2.  **Data Delivery Settings:**
    * 데이터를 어떤 방식으로 어디에 전달할지 구성합니다(예: Email, cloud storage).
    * 구성을 위해 전달 설정 토글을 선택합니다. 자세한 내용은 [Data Delivery Settings](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview#via-deliver-to-external-storage%3A)를 참조하십시오.

3.  **Start and Download:**
    * 입력값과 전달 설정 구성이 완료되면 **Start collecting** 버튼을 선택합니다.

      ![No-code Scraper Input Configuration](https://github.com/user-attachments/assets/ee2b3bc4-9d42-45c2-99f2-e9387548ff26)

    * 수집이 완료되면 선호하는 형식(JSON, CSV, JSONL, 또는 NDJSON)으로 데이터를 다운로드합니다.
    
      ![Download Data Options](https://github.com/user-attachments/assets/f3fd94f3-c995-46a5-aaaa-3f5ad3361e4c)