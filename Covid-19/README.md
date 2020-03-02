# `covid19.py`
코로나-19 에 대한 확진/완치/사망 에 대한 국내, 해외 정보를 수집합니다. \n
Data scrapes Covid-19 Confirmed/Cured/Deceases Cases.

## Covid19 Korea Data / 코로나 한국 자료
- `bs4` 를 활용하여 간단한 크롤러로 질병관리본부(KCDC)에 있는 환자 현황을 크롤합니다.
- Using `bs4`, scrapes Korea CDC(KCDC) page for current status of Covid-19 in Korea.

## Covid19 World Data
- [CSSEGISandData/CODIV-19](https://github.com/CSSEGISandData/COVID-19) 에서 사용 중인 ArcGIS API를 활용합니다.
- 
### Try it out
Submit arguments of what you what to Search
찾고싶은 사항에 대해서 arguments 로 입력하세요
```
Field: 
    "OBJECTID",
    "PROVINCE_STATE",
    "COUNTRY_REGION",
    "CONFIRMED",
    "DEATHS",
    "RECOVERED"
```
`Field` is query label used to search in the ArcGIS data table of the field value.
First argument takes one `Field` value. Same as `WHERE` in `sql`
Second argument takes more than one `Field` value. Needed for deciphering which `Field` data to return. Default: "*"(ALL)
Third argument takes  one `Field` value. Needed for returned data to be ordered according to the `Field` value
Fourth argument decides on which format the data to be returned in. Either in `HTML` or `JSON`. Default: "json"

`Field` 는 arcGIS REST API 에서 field 값 자료 데이블을 탐색하기 위해 쓰입니다.
첫 argument 는 `SQL`의 `WHERE` 구문과 같습니다. 테이블을 쿼리하기 위해 쓰입니다. `Field` 값과 그에 알맞는 값이 필요합니다. 
두번째 argument 는 하나 이상의 `Field` 값을 갖습니다. 어떤 `Field` 값을 반환할 지 정해줍니다. 기본 값 "*"(전체) 
세번째 argument 는 하나의 `Field` 값을 갖습니다. 반환 된 값의 순서를 정해줍니다. 
네번째 argument 는 반환 될 값의 포맷을 정해줍니다. `HTML` 아니면 `JSON` 둘중 하나 입니다. 기본 값: "json"


* Example / 예시
```
python3 covid19.py "Confirmed > 0" "*" "Confirmed" "json"
```
This searches for Values with more than 0 Confirmed cases and returns all `Field` values with it.
Returns in JSON format in order from least to most Confirmed cases.

Documents about ArcGIS FeatureService Rest API can be found here:
[ArcGIS-FeatureService](https://developers.arcgis.com/rest/services-reference/feature-service.htm)
[ArcGIS-FeatureService(Layer)](https://developers.arcgis.com/rest/services-reference/query-feature-service-layer-.htm)


### JSON data
 Data scraped from the API is returned in JSON format into `covid_dat.json` file.
 API 에서 크롤된 자료는 `covid_dat.json` 파일에 반환됩니다.

## Built With/사용된 파이썬 모듈
* [Python3](https://www.python.org/doc)
- [BeautifulSoup4](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) 
- [Requests](https://requests.readthedocs.io/en/master/)

## Authors

* **Sean Hong(홍성민)** 
* 현재 군인 현역으로 있는 학생이기 때문에 많이 부족합니다. 보완점을 가르쳐주시면 감사하겠습니다!
* Any lacking parts in my code are welcome to any suggestions and criticism.

## Acknowledgments

* World data scraped from - *github repo* - [Covid-19](https://github.com/CSSEGISandData/COVID-19) - [Service](https://services1.arcgis.com/0MSEUqKaxRlEPj5g/arcgis/rest/services/ncov_cases/FeatureServer)
* Korea data scraped from [질병관리본부(Korea CDC)](http://ncov.mohw.go.kr/index_main.jsp)

## Any problems please contact me at `seanhong2000@gmail.com`