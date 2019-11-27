# 1단계 - 요구 사항 정리
## 실습 환경 구축
* ddd-strategic-design를 기반으로 미션을 진행한다.
* 미션 시작 버튼을 눌러 미션을 시작한다.
* 저장소에 자신의 GitHub 아이디로 된 브랜치가 생성되었는지 확인한다.
* 저장소를 자신의 계정으로 Fork 한다.
* 요구 사항에 대한 구현을 완료한 후, 작업이 다 되었으면 Push를 한다.
* next-step/ddd-strategic-design에서 Pull Request를 작성한다.
* 리뷰 받은 내용을 토대로 코드를 리팩터링하고 다시 Push를 한다.
* 모든 피드백을 완료하면 다음 단계를 도전하고 앞의 과정을 반복한다.

## 요구 사항
* kitchenpos 패키지의 코드를 보고 키친포스의 요구 사항을 README.md에 작성한다.
* 미션을 진행함에 있어 아래 문서를 적극 활용한다.
    * [마크다운(Markdown) - Dooray!](https://dooray.com/htmls/guides/markdown_ko_KR.html)

## 힌트
* http 디렉터리의 .http 파일(HTTP client)을 보고 어떤 요청을 받는지 참고한다.
    * [IntelliJ의 .http를 사용해 Postman 대체하기](https://jojoldu.tistory.com/266)

```
###
POST {{host}}/api/menu-groups
Content-Type: application/json

{
  "name": "추천메뉴"
}

###
GET {{host}}/api/menus-groups

###
```

* `src/main/resources/db/migration` 디렉터리의 `.sql` 파일을 보고 어떤 관계로 이루어져 있는지 참고한다.

```sql
CREATE TABLE orders (
    id BIGINT(20) NOT NULL AUTO_INCREMENT,
    order_table_id BIGINT(20) NOT NULL,
    order_status VARCHAR(255) NOT NULL,
    ordered_time DATETIME NOT NULL,
    PRIMARY KEY (id)
);
```

* 아래의 예제를 참고한다.
```
## 요구 사항

- 간단한 포켓몬 게임을 구현한다.
- 트레이너
    - [ ]  사용자는 트레이너라고 부른다.
    - [ ]  트레이너는 아이디를 등록할 수 있고 등록한 아이디로 로그인할 수 있어야 한다.
    - [ ]  트레이너는 레벨을 가지고 있으며 포켓몬을 잡을 때마다 레벨이 1씩 증가한다.
    - [ ]  레벨은 30까지 증가한다.
    - [ ]  최초 로그인 시 이상해씨, 파이리, 꼬부기 중 한 마리를 선택할 수 있다.
    - [ ]  가지고 있는 포켓몬 목록을 볼 수 있다.
    - [ ]  가지고 있는 아이템 목록을 볼 수 있다.
- 포켓몬
    - [ ]  전국 도감 번호 1번부터 151번까지의 포켓몬이 무작위로 등장한다.
    - [ ]  포켓몬은 고유의 포획률을 가지고 있다.
    - [ ]  트레이너는 가지고 있는 몬스터볼을 소비함으로써 포켓몬을 잡을 수 있다.
    - [ ]  포획률 = (포켓몬의 포획률 * 몬스터볼 보정 승수 * (레벨 11 이상의 트레이너 레벨 / 10)) * 100 / 255
    - [ ]  잡은 포켓몬은 닉네임을 지어 붙일 수 있다.
- 아이템
    - [ ]  몬스터볼은 고유의 보정 승수를 가지고 있다.
    (몬스터볼: 1.0, 수퍼볼: 1.5, 하이퍼볼: 2.0, 마스터볼: 255)
```