# Schema

이 문서는 Metadata for Medical Library Repository 스키마에에서 사용되는 요소에 대한 정리표입니다. 
Libreoffice Calc에서 내용을 정리한 뒤 ChatGPT를 통해 마크다운 형식으로 다듬었습니다. 
원본 파일은 schema and appendix.ods를 참고해 주시기 바랍니다. 

## Legend

- `Required` / `Repeatable`의 `O`는 해당, `X`는 해당 없음, `N/A`는 적용 대상이 아님을 의미합니다.
- XML 예시는 GitHub에서 태그가 사라지지 않도록 코드 블록으로 분리했습니다.

## Elements Summary

| Element | Description | Required | Repeatable |
|---|---|---:|---:|
| [`object_type`](#object_type) | 레코드가 표현하는 객체가 어떤 종류의 객체인지를 선언합니다. | O | O |
| [`object_title`](#object_title) | 레코드가 표현하는 객체의 제목입니다. | O | O |
| [`original_title`](#original_title) | 레코드가 표현하는 객체의 원 제목입니다. | O | X |
| [`translated_title`](#translated_title) | 레코드가 표현하는 객체의 번역된 제목입니다. | X | O |
| [`published_date`](#published_date) | 객체가 출판되거나 공개된 날짜와 관련된 정보입니다. | X | X |
| [`received_date`](#received_date) | 주로 학술지에서 논문을 투고받은 날짜입니다. | X | X |
| [`revised_date`](#revised_date) | 주로 학술지에서 논문을 리뷰한 뒤 이를 토대로 수정본이 제출된 날짜입니다. | X | X |
| [`accepted_date`](#accepted_date) | 자료의 심사가 완료되어 게재/등록이 확정된 날짜입니다. | X | X |
| [`first_published_date`](#first_published_date) | 자료가 처음으로 인터넷 등에 공개된 날짜입니다. | O | X |
| [`issue_published_date`](#issue_published_date) | 주로 논문의 경우 공식 권호 등을 통해 출간된 날짜입니다. | X | X |
| [`author_information`](#author_information) | 객체의 저자/제작자와 관련된 정보입니다. | O | O |
| [`author_type`](#author_type) | 객체의 저자가 맡은 역할에 대한 정보입니다. | O | O |
| [`author_name`](#author_name) | 객체의 저자가 가진 이름정보입니다. | O | X |
| [`full_name`](#full_name) | 저자의 전체 이름입니다. | O | X |
| [`given_name`](#given_name) | 저자의 이름입니다. | X | X |
| [`middle_name`](#middle_name) | 저자의 가운데 이름입니다. | X | X |
| [`family_name`](#family_name) | 저자의 성입니다. | X | X |
| [`author_identifier`](#author_identifier) | 저자 고유의 식별자입니다. | X | O |
| [`author_address`](#author_address) | 저자의 소속기관 정보 혹은 주소입니다. | X | O |
| [`author_email`](#author_email) | 저자의 이메일 정보입니다. | X | O |
| [`author_position`](#author_position) | 논문에서 저자가 몇번째에 기재되었는지에 대한 정보입니다. | O | X |
| [`object_external_identifier`](#object_external_identifier) | 레코드가 표현하는 객체가 외부 리포지터리 등에 등록되어 있고, 그 리포지터리에서 고유의 식별자를 가진 경우 그에 대한 정보입니다. | X | O |
| [`object_source`](#object_source) | 레코드가 표현하는 객체가 게시된 매체에 대한 사항입니다. | X | X |
| [`journal`](#journal) | 객체가 학술지에 실린 경우 그 학술지와 연결하기 위한 정보입니다. | X | O |
| [`journal_identifier`](#journal_identifier) | 학술지의 식별자입니다. | X | O |
| [`journal_title`](#journal_title) | 학술지 제목입니다. | X | O |
| [`database`](#database) | 객체가 데이터베이스에 수록된 경우 그 데이터베이스와 연결하기 위한 정보입니다. | X | O |
| [`database_identifier`](#database_identifier) | 데이터베이스의 식별자입니다. | X | O |
| [`database_name`](#database_name) | 데이터베이스의 이름입니다. | X | O |
| [`conference`](#conference) | 컨퍼런스 관련 정보입니다. | X | O |
| [`conference_title`](#conference_title) | 컨퍼런스의 이름입니다. | X | O |
| [`conference_identifier`](#conference_identifier) | 컨퍼런스의 식별자를 입력합니다. | X | X |
| [`conference_date`](#conference_date) | 컨퍼런스가 열린 기간 정보입니다. | X | X |
| [`start_date`](#start_date) | 컨퍼런스가 개최된 날짜의 정보입니다. | X | X |
| [`end_date`](#end_date) | 컨퍼런스가 폐막한 날짜의 정보입니다. | X | X |
| [`citation_information`](#citation_information) | 인용/피인용과 관련된 정보입니다. | X | X |
| [`citation_source`](#citation_source) | 인용/피인용 정보의 정보원을 상세히 기재합니다. | X | O |
| [`object_status`](#object_status) | 객체의 상태에 대한 정보입니다. 출판단계, 출판이후단계, 리포지터리처리단계, 기타 상태 등이 포함됩니다. | O | X |
| [`publication_stage`](#publication_stage) | 출판 또는 공개 단계에 대한 정보입니다. | O | X |
| [`post_publication_status`](#post_publication_status) | 출판 후 이의제기, 논문철회, 수정 등 상태를 표현합니다. | X | O |
| [`repository_status`](#repository_status) | 이 객체가 리포지터리에 제출되고 나서의 상태입니다. | X | X |
| [`status_note`](#status_note) | 객체 상태와 관련된 주기사항입니다. | X | X |
| [`text_information`](#text_information) | 레코드가 표현하는 객체와 관련된 각종 텍스트 정보 (초록, 저자노트, 키워드 등) 로서 검색을 용이하게 만드는 정보입니다. | X | X |
| [`abstract`](#abstract) | 객체의 초록 정보입니다. 데이터베이스 설명 / 이미지 설명 (figure legend) 도 여기에 포함됩니다. | X | X |
| [`note_from_article`](#note_from_article) | 객체 자체가 제공하는 각종 노트(부가사항) 정보입니다. | X | O |
| [`keywords`](#keywords) | 객체에 포함된 키워드 정보입니다. | X | O |
| [`MeSH_headings`](#mesh_headings) | PubMed에 색인된 레코드에 부여되는 MeSH 통제어입니다. | X | O |
| [`object_link_information`](#object_link_information) | 객체가 다른 객체 등과 연결되는 정보입니다 | X | X |
| [`link`](#link) | 객체 간 개별 연결에 대한 정보입니다. | X | O |
| [`rights_information`](#rights_information) | 객체의 저작권과 관련된 정보입니다. | X | X |
| [`rights_status`](#rights_status) | 저작권의 현재 상태에 대한 서술입니다. | X | X |
| [`access_model`](#access_model) | 객체의 접근 방식과 관련된 정보입니다. | X | X |
| [`publishing_model`](#publishing_model) | 학술지 아티클의 출판 모델 정보입니다. | X | X |
| [`license_information`](#license_information) | 라이선스 관련 정보입니다. | X | O |
| [`rights_holder`](#rights_holder) | 라이선스 보유자에 대한 정보입니다. | X | O |
| [`rights_statement`](#rights_statement) | 라이선스 관련하여 객체가 별도로 표시한 내용을 옮겨 적습니다 | X | O |
| [`administrative_metadata`](#administrative_metadata) | 리포지터리의 관리 메타데이터 입력란입니다. | O | X |
| [`repo_register_id`](#repo_register_id) | 리포지터리 등록번호입니다. | O | O |
| [`record_status`](#record_status) | 메타데이터 레코드 자체에 대한 관리 메타데이터 영역입니다 | O | X |
| [`created_date`](#created_date) | 메타데이터 레코드 생성 시각입니다. | O | X |
| [`last_modified_date`](#last_modified_date) | 레코드가 최종적으로 수정된 시점입니다. | X | X |
| [`note_by_repository`](#note_by_repository) | 리포지터리에서 레코드 보완 등을 위한 정보입니다. | X | O |

## Element Details

### object_type

| Field | Value |
|---|---|
| Description | 레코드가 표현하는 객체가 어떤 종류의 객체인지를 선언합니다. |
| Required | O |
| Repeatable | O |
| How to use | 6개의 Attribute (object_category / article_type / dataset_type / image_type / sound_type) 를 제한된 용어를 이용해 기술합니다. |
| Refines / refinement | N/A |
| Controlled vocabulary | (1) object_category<br>See appendix 1-1.<br>(2) article_type<br>See appendix 1-2.<br>(3) dataset_type<br>See appendix 1-3.<br>(4) image_type<br>See appendix 1-4..<br>(5) sound_type<br>See appendix 1-5. |
| Additional info | N/A |

#### Example

```xml
<object_type object_category="article" article_type="Review_Article"/>
<object_type object_category="article" article_type="Original_Article"/>
```

### object_title

| Field | Value |
|---|---|
| Description | 레코드가 표현하는 객체의 제목입니다. |
| Required | O |
| Repeatable | O |
| How to use | 하위 요소를 이용해 객체의 제목을 기재합니다. |
| Refines / refinement | 하위 요소 : original_title / translated_title |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<object_title>
  <original_title>Pharmacotherapy for mild hypertension</original_title>
  <translated_title language="Español">Farmacoterapia para la hipertensión leve</translated_title>
  <translated_title language="فارسی">دارودرمانی در مدیریت بالینی هیپرتانسیون خفیف</translated_title>
  <translated_title language="Français">Pharmacothérapie pour l'hypertension légère</translated_title>
  <translated_title language="Português">Tratamento medicamentoso para hipertensão leve</translated_title>
</object_title>
```

### original_title

| Field | Value |
|---|---|
| Description | 레코드가 표현하는 객체의 원 제목입니다. |
| Required | O |
| Repeatable | X |
| How to use | 원 자료가 스스로의 제목을 표현하는 방식을 따라 그대로 입력합니다. UTF-8인코딩 사용을 권장합니다. 메타데이터 반입 시 인코딩에 오류가 있을 경우 원제목을 UTF-8로 옮길 수 있는지 여부를 판단하고, 불가능하다면 원본 보존을 위해 깨진 상태로 반입해 주세요. |
| Refines / refinement | 상위 요소 : object_title |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<original_title>Pharmacotherapy for mild hypertension</original_title>
```

### translated_title

| Field | Value |
|---|---|
| Description | 레코드가 표현하는 객체의 번역된 제목입니다. |
| Required | X |
| Repeatable | O |
| How to use | 공식 번역 제목을 입력하고, attribute에 언어정보를 입력합니다. UTF-8인코딩 사용을 권장합니다. 메타데이터 반입 시 인코딩에 오류가 있을 경우 원제목을 UTF-8로 옮길 수 있는지 여부를 판단하고, 불가능하다면 원본 보존을 위해 깨진 상태로 반입해 주세요. |
| Refines / refinement | 상위 요소 : object_title |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<translated_title language="فارسی">دارودرمانی در مدیریت بالینی هیپرتانسیون خفیف</translated_title>
```

### published_date

| Field | Value |
|---|---|
| Description | 객체가 출판되거나 공개된 날짜와 관련된 정보입니다. |
| Required | X |
| Repeatable | X |
| How to use | 하위 요소에 자세한 정보를 입력합니다. |
| Refines / refinement | 하위 요소 : received_date, revised_date, accepted_date, first_published_date, issue_published |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<published_date>
  <first_published_date>2021-12-14</first_published_date>
</published_date>
```

### received_date

| Field | Value |
|---|---|
| Description | 주로 학술지에서 논문을 투고받은 날짜입니다. |
| Required | X |
| Repeatable | X |
| How to use | YYYY-MM-DD의 형식으로 입력합니다. |
| Refines / refinement | 상위 요소 : published_date |
| Controlled vocabulary | xs:date |
| Additional info | N/A |

#### Example

```xml
<received_date>2024-06-15</received_date>
```

### revised_date

| Field | Value |
|---|---|
| Description | 주로 학술지에서 논문을 리뷰한 뒤 이를 토대로 수정본이 제출된 날짜입니다. |
| Required | X |
| Repeatable | X |
| How to use | YYYY-MM-DD의 형식으로 입력합니다. |
| Refines / refinement | 상위 요소 : published_date |
| Controlled vocabulary | xs:date |
| Additional info | N/A |

#### Example

```xml
<revised_date>2024-06-15</revised_date>
```

### accepted_date

| Field | Value |
|---|---|
| Description | 자료의 심사가 완료되어 게재/등록이 확정된 날짜입니다. |
| Required | X |
| Repeatable | X |
| How to use | YYYY-MM-DD의 형식으로 입력합니다. |
| Refines / refinement | 상위 요소 : published_date |
| Controlled vocabulary | xs:date |
| Additional info | N/A |

#### Example

```xml
<accepted_date>2024-06-15</accepted_date>
```

### first_published_date

| Field | Value |
|---|---|
| Description | 자료가 처음으로 인터넷 등에 공개된 날짜입니다. |
| Required | O |
| Repeatable | X |
| How to use | YYYY-MM-DD의 형식으로 입력합니다. |
| Refines / refinement | 상위 요소 : published_date |
| Controlled vocabulary | xs:date |
| Additional info | N/A |

#### Example

```xml
<first_published_date>2024-06-15</first_published_date>
```

### issue_published_date

| Field | Value |
|---|---|
| Description | 주로 논문의 경우 공식 권호 등을 통해 출간된 날짜입니다. |
| Required | X |
| Repeatable | X |
| How to use | YYYY-MM-DD의 형식으로 입력합니다. |
| Refines / refinement | 상위 요소 : published_date |
| Controlled vocabulary | xs:date |
| Additional info | N/A |

#### Example

```xml
<issue_published_date>2024-06-15</issue_published_date>
```

### author_information

| Field | Value |
|---|---|
| Description | 객체의 저자/제작자와 관련된 정보입니다. |
| Required | O |
| Repeatable | O |
| How to use | 하나의author_information 요소는 한 명의 저자를 의미합니다. 하위 요소들을 이용해 상세히 기술합니다. |
| Refines / refinement | 하위 요소 : author_type, author_name, author_identifier, author_address, author_email, author_position |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<author_information>
  <author_type>1st_author</author_type>
  <author_type>corresponding_author</author_type>
  <!--첫번째 저자이면서 교신저자인 경우입니다-->
  <author_name>
    <full_name>Laura E. M. Wisse</full_name>
  </author_name>
  <author_address>Department of Clinical Science Lund, Lund University, Lund, Sweden</author_address>
  <author_email>laura.wisse@med.lu.se</author_email>
  <author_position>1</author_position>
</author_information>
```

### author_type

| Field | Value |
|---|---|
| Description | 객체의 저자가 맡은 역할에 대한 정보입니다. |
| Required | O |
| Repeatable | O |
| How to use | 저자의 역할을 통제어휘에서 골라 입력합니다. 만일 제 1 저자이면서 교신저자인 경우 author_type을 반복하여 2개 역할을 입력해 줍니다 |
| Refines / refinement | 상위 요소 : author_information |
| Controlled vocabulary | See appendix 2. |
| Additional info | N/A |

#### Example

```xml
<author_type>1st_author</author_type>
<author_type>corresponding_author</author_type>
```

### author_name

| Field | Value |
|---|---|
| Description | 객체의 저자가 가진 이름정보입니다. |
| Required | O |
| Repeatable | X |
| How to use | 이름에 대한 하위 요소 4개를 이용해 이름 정보를 자세하게 기술합니다. 성 / 가운데이름 / 이름을 구분할 수 없는 경우 full_name만 입력합니다. |
| Refines / refinement | 상위 요소 : author_information / 하위 요소 : full_name, given_name, middle_name, family_name |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<author_name>
  <full_name>Oskar Hansson</full_name>
</author_name>
```

### full_name

| Field | Value |
|---|---|
| Description | 저자의 전체 이름입니다. |
| Required | O |
| Repeatable | X |
| How to use | 저자의 전체 이름을 논문에 표기된 그대로 입력합니다. |
| Refines / refinement | 상위 요소 : author_name |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<full_name>Dominic Wang</full_name>
```

### given_name

| Field | Value |
|---|---|
| Description | 저자의 이름입니다. |
| Required | X |
| Repeatable | X |
| How to use | 저자의 이름을 구분할 수 있는 경우 논문에 표기된 그대로 입력합니다. |
| Refines / refinement | 상위 요소 : author_name |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<given_name>Dominic</given_name>
```

### middle_name

| Field | Value |
|---|---|
| Description | 저자의 가운데 이름입니다. |
| Required | X |
| Repeatable | X |
| How to use | 저자의 가운데 이름을 구분할 수 있는 경우 논문에 표기된 그대로 입력합니다. |
| Refines / refinement | 상위 요소 : author_name |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<middle_name>Carla</middle_name>
```

### family_name

| Field | Value |
|---|---|
| Description | 저자의 성입니다. |
| Required | X |
| Repeatable | X |
| How to use | 저자의 성을 구분할 수 있는 경우 논문에 표기된 그대로 입력합니다. |
| Refines / refinement | 상위 요소 : author_name |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<family_name>Medeiros Silva</family_name>
```

### author_identifier

| Field | Value |
|---|---|
| Description | 저자 고유의 식별자입니다. |
| Required | X |
| Repeatable | O |
| How to use | 저자 식별자를 논문 혹은 리포지터리 전거 DB에서 확인할 수 있는 경우 입력합니다. |
| Refines / refinement | 상위 요소 : author_information |
| Controlled vocabulary | See appendix 3. |
| Additional info | N/A |

#### Example

```xml
<author_identifier type="orcid">0000-0003-0211-8654</author_identifier>
```

### author_address

| Field | Value |
|---|---|
| Description | 저자의 소속기관 정보 혹은 주소입니다. |
| Required | X |
| Repeatable | O |
| How to use | 저자 소속기관 정보를 논문에 표기된 그대로 입력합니다. 2개 이상 기관에 소속된 경우 요소를 반복 입력하여 전부 표현합니다. |
| Refines / refinement | 상위 요소 : author_information |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<author_address>Department of Health Research Methods, Evidence, and Impact, McMaster University, Hamilton, Ontario, Canada.</author_address>
```

### author_email

| Field | Value |
|---|---|
| Description | 저자의 이메일 정보입니다. |
| Required | X |
| Repeatable | O |
| How to use | 저자의 이메일이 논문에 명시되어 있을 경우 이를 입력합니다. 2개 이상의 이메일이 표기된 경우 요소를 반복 입력하여 전부 표현합니다. |
| Refines / refinement | 상위 요소 : author_information |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<author_email>millsej@mcmaster.ca</author_email>
```

### author_position

| Field | Value |
|---|---|
| Description | 논문에서 저자가 몇번째에 기재되었는지에 대한 정보입니다. |
| Required | O |
| Repeatable | X |
| How to use | 저자 순서는 양수로만 표기가 가능하므로, 양수(xs:positiveInteger)로 입력합니다. |
| Refines / refinement | 상위 요소 : author_information |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<author_position>4</author_position>
```

### object_external_identifier

| Field | Value |
|---|---|
| Description | 레코드가 표현하는 객체가 외부 리포지터리 등에 등록되어 있고, 그 리포지터리에서 고유의 식별자를 가진 경우 그에 대한 정보입니다. |
| Required | X |
| Repeatable | O |
| How to use | attribute “type”에 식별자의 이름을 string 형태로 입력하고, 식별자를 텍스트로 기재합니다. |
| Refines / refinement | N/A |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<object_external_identifier type="PMID">34927127</object_external_identifier>
```

### object_source

| Field | Value |
|---|---|
| Description | 레코드가 표현하는 객체가 게시된 매체에 대한 사항입니다. |
| Required | X |
| Repeatable | X |
| How to use | 하위 요소들을 통해 어떤 매체에 게시되었는지를 상세히 기술합니다. |
| Refines / refinement | 하위 요소 : journal, database, conference |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<object_source>
  <journal>
    <journal_identifier>2667-193X</journal_identifier>
    <journal_title>The Lancet Regional Health - Americas</journal_title>
  </journal>
</object_source>
```

### journal

| Field | Value |
|---|---|
| Description | 객체가 학술지에 실린 경우 그 학술지와 연결하기 위한 정보입니다. |
| Required | X |
| Repeatable | O |
| How to use | 하위 요소 journal identifier와 journal title을 이용해 자세한 정보를 표현합니다. |
| Refines / refinement | 상위 요소 : object_source / 하위 요소 : journal_identifier, journal_title |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<journal>
  <journal_identifier>2667-193X</journal_identifier>
  <journal_title>The Lancet Regional Health - Americas</journal_title>
</journal>
```

### journal_identifier

| Field | Value |
|---|---|
| Description | 학술지의 식별자입니다. |
| Required | X |
| Repeatable | O |
| How to use | 학술지 식별자를 NLM Catalog (https://www.ncbi.nlm.nih.gov/nlmcatalog/), Journal Citation Reports (jcr.clarivate.com), Scopus (https://www.scopus.com/sources) 등에서 확인하여 입력합니다. |
| Refines / refinement | 상위 요소 : journal |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<journal_identifier>2667-193X</journal_identifier>
```

### journal_title

| Field | Value |
|---|---|
| Description | 학술지 제목입니다. |
| Required | X |
| Repeatable | O |
| How to use | 학술지 제목을 학술지 식별자가 있는 경우 신뢰할 수 있는 목록에서 가져오며, 그렇지 않은 경우 논문 등에 표기된 그대로 입력합니다. |
| Refines / refinement | 상위 요소 : journal |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<journal_title>The Lancet Regional Health - Americas</journal_title>
```

### database

| Field | Value |
|---|---|
| Description | 객체가 데이터베이스에 수록된 경우 그 데이터베이스와 연결하기 위한 정보입니다. |
| Required | X |
| Repeatable | O |
| How to use | 하위 요소 database_identifier와 database_title을 이용해 자세한 정보를 표현합니다. |
| Refines / refinement | 상위 요소 : object_source / 하위 요소 : database_identifier, database_title |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<database>
  <database_name>Micromedex</database_name>
</database>
```

### database_identifier

| Field | Value |
|---|---|
| Description | 데이터베이스의 식별자입니다. |
| Required | X |
| Repeatable | O |
| How to use | URL, DOI 혹은 기타 식별자를 확인하여 입력합니다. |
| Refines / refinement | 상위 요소 : database |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<database_identifier>https://www.micromedexsolutions.com</database_identifier>
```

### database_name

| Field | Value |
|---|---|
| Description | 데이터베이스의 이름입니다. |
| Required | X |
| Repeatable | O |
| How to use | 데이터베이스의 공식 명칭을 웹페이지, 소개자료 등에서 확인하여 기재합니다. |
| Refines / refinement | 상위 요소 : database |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<database_name>Micromedex</database_name>
```

### conference

| Field | Value |
|---|---|
| Description | 컨퍼런스 관련 정보입니다. |
| Required | X |
| Repeatable | O |
| How to use | 하위 요소를 이용하여 자세하게 기술합니다. |
| Refines / refinement | 상위 요소 : object_source / 하위 요소 : conference_title, conference_identifier, conference_date |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<conference>
  <conference_title>Alzheimer’s Association International Conference</conference_title>
  <conference_date>
    <start_date>2024-07-28</start_date>
    <end_date>2024-07-28</end_date>
  </conference_date>
</conference>
```

### conference_title

| Field | Value |
|---|---|
| Description | 컨퍼런스의 이름입니다. |
| Required | X |
| Repeatable | O |
| How to use | 컨퍼런스의 정식 명칭을 찾아 입력하되, 정식 명칭을 찾기 어려운 경우 논문에 기재된 그대로 입력합니다. |
| Refines / refinement | 상위 요소 : conference |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<conference_title>Alzheimer’s Association International Conference</conference_title>
```

### conference_identifier

| Field | Value |
|---|---|
| Description | 컨퍼런스의 식별자를 입력합니다. |
| Required | X |
| Repeatable | X |
| How to use | 컨퍼런스의 URL, DOI등 식별자 정보를 확인하여 입력합니다. |
| Refines / refinement | 상위 요소 : conference |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<conference_identifier>https://neurips.cc/Conferences/2025</conference_identifier>
```

### conference_date

| Field | Value |
|---|---|
| Description | 컨퍼런스가 열린 기간 정보입니다. |
| Required | X |
| Repeatable | X |
| How to use | 하위 요소 start_date와 end_date를 이용해 컨퍼런스 기간 정보를 입력합니다. 하루동안 진행된 경우 동일한 날짜를 start_date와 end_date에 입력합니다. |
| Refines / refinement | 상위 요소 : conference, 하위 요소 : start_date, end_date |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<conference_date>
  <start_date>2024-07-28</start_date>
  <end_date>2024-07-28</end_date>
</conference_date>
```

### start_date

| Field | Value |
|---|---|
| Description | 컨퍼런스가 개최된 날짜의 정보입니다. |
| Required | X |
| Repeatable | X |
| How to use | YYYY-MM-DD의 형식으로 입력합니다. |
| Refines / refinement | 상위 요소 : conference_date |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<start_date>2024-07-28</start_date>
```

### end_date

| Field | Value |
|---|---|
| Description | 컨퍼런스가 폐막한 날짜의 정보입니다. |
| Required | X |
| Repeatable | X |
| How to use | YYYY-MM-DD의 형식으로 입력합니다. |
| Refines / refinement | 상위 요소 : conference_date |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<end_date>2024-07-28</end_date>
```

### citation_information

| Field | Value |
|---|---|
| Description | 인용/피인용과 관련된 정보입니다. |
| Required | X |
| Repeatable | X |
| How to use | 하위 요소 citation_source를 이용해 이 객체의 인용정보를 어떤 출처에서 가져올 수 있는지 기재합니다. 인용횟수 등은 출처와 연결되며 자동으로 갱신됩니다. |
| Refines / refinement | 하위 요소 : citation_source |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<citation_information>
<citation_source source="altmetric" identifier_type="url" identifier="https://cochrane.altmetric.com/details/194628783" last_checked="2026-06-12"/>
</citation_information
```

### citation_source

| Field | Value |
|---|---|
| Description | 인용/피인용 정보의 정보원을 상세히 기재합니다. |
| Required | X |
| Repeatable | O |
| How to use | attribute “source”에 출처를 기재하고, identifier_type에는 인용/피인용 정보원에서 객체를 표시하는 식별자의 종류를 기재합니다. identifier에 실제 식별자 값을 입력합니다. last_checked attribute는 시스템이 자동으로 처리합니다. |
| Refines / refinement | 상위 요소 : citation_information |
| Controlled vocabulary | source: see Appendix 4-1 / identifier_type: see Appendix 4-2. |
| Additional info | N/A |

#### Example

```xml
<citation_source source="altmetric" identifier_type="url" identifier="https://cochrane.altmetric.com/details/194628783" last_checked="2026-06-12"/>
```

### object_status

| Field | Value |
|---|---|
| Description | 객체의 상태에 대한 정보입니다. 출판단계, 출판이후단계, 리포지터리처리단계, 기타 상태 등이 포함됩니다. |
| Required | O |
| Repeatable | X |
| How to use | 하위 요소 4개를 이용해 객체의 현재 상태를 표현합니다. |
| Refines / refinement | 하위 요소 : publication_stage, post_publication_status, repository_status, status_note |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<object_status>
  <publication_stage>online_published</publication_stage>
  <post_publication_status status="retracted"/>
  <repository_status>under_review</repository_status>
  <status_note>Retraction 된 기관 소속 연구자의 논문을 리포지터리에 등록할 것인지 내부 정책 논의 중</status_note>
</object_status>
```

### publication_stage

| Field | Value |
|---|---|
| Description | 출판 또는 공개 단계에 대한 정보입니다. |
| Required | O |
| Repeatable | X |
| How to use | 미리 규정된 용어집에서 단계를 선택하여 입력합니다. |
| Refines / refinement | 상위 요소 : object_status |
| Controlled vocabulary | See Appendix 5-1. |
| Additional info | N/A |

#### Example

```xml
<publication_stage>online_published</publication_stage>
```

### post_publication_status

| Field | Value |
|---|---|
| Description | 출판 후 이의제기, 논문철회, 수정 등 상태를 표현합니다. |
| Required | X |
| Repeatable | O |
| How to use | 논문의 현재 상태를 API나 직접 검색 등으로 확인한 뒤 status attribute에는 정해진 값을 입력하고, status_date에 상태 변경된 날짜를 xs:date타입으로, source에는 이를 확인한 학술지/pubpeer 등 플랫폼을, source_uri는 출처의 uri를 기재합니다. |
| Refines / refinement | 상위 요소 : object_status |
| Controlled vocabulary | See Appendix 5-2. |
| Additional info | N/A |

#### Example

```xml
<post_publication_status status="retracted"/>
```

### repository_status

| Field | Value |
|---|---|
| Description | 이 객체가 리포지터리에 제출되고 나서의 상태입니다. |
| Required | X |
| Repeatable | X |
| How to use | 미리 정해진 value를 요소에 입력합니다. |
| Refines / refinement | 상위 요소 : object_status |
| Controlled vocabulary | See Appendix 5-3. |
| Additional info | N/A |

#### Example

```xml
<repository_status>under_review</repository_status>
```

### status_note

| Field | Value |
|---|---|
| Description | 객체 상태와 관련된 주기사항입니다. |
| Required | X |
| Repeatable | X |
| How to use | 필요에 따라 객체 상태를 string 형태로 수기 입력합니다. |
| Refines / refinement | N/A |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<status_note>Retraction 된 기관 소속 연구자의 논문을 리포지터리에 등록할 것인지 내부 정책 논의 중</status_note>
```

### text_information

| Field | Value |
|---|---|
| Description | 레코드가 표현하는 객체와 관련된 각종 텍스트 정보 (초록, 저자노트, 키워드 등) 로서 검색을 용이하게 만드는 정보입니다. |
| Required | X |
| Repeatable | X |
| How to use | 하위 요소를 활용해 상세히 기재합니다. |
| Refines / refinement | 하위 요소 : abstract, note_from_article_keywords, MeSH_headings |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<text_information>
  <abstract>Background: Observational studies have postulated a therapeutic role of metformin in treating COVID-19. … There were also no differences between metformin and placebo observed for other secondary clinical outcomes.</abstract>
  <keywords>Brazil; COVID-19; Hospitalization; Metformin; Outpatients; Randomized clinical trial.</keywords>
</text_information>
```

### abstract

| Field | Value |
|---|---|
| Description | 객체의 초록 정보입니다. 데이터베이스 설명 / 이미지 설명 (figure legend) 도 여기에 포함됩니다. |
| Required | X |
| Repeatable | X |
| How to use | 초록, 데이터베이스 설명, 이미지 설명 등 각종 설명 문구를 확인하여 string 형태로 옮깁니다. |
| Refines / refinement | 상위 요소 : text_information |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<abstract>Background: Observational studies have postulated a therapeutic role of metformin in treating COVID-19. … There were also no differences between metformin and placebo observed for other secondary clinical outcomes.</abstract>
```

### note_from_article

| Field | Value |
|---|---|
| Description | 객체 자체가 제공하는 각종 노트(부가사항) 정보입니다. |
| Required | X |
| Repeatable | O |
| How to use | 객체에서 확인할 수 있는 부가사항 등을 찾아 입력하고, 상황에 따라 동일 요소를 반복하여 기재합니다. |
| Refines / refinement | 상위 요소 : text_information |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<note_from_article>These authors contributed equally as co-senior authors of this work.</note_from_article>
```

### keywords

| Field | Value |
|---|---|
| Description | 객체에 포함된 키워드 정보입니다. |
| Required | X |
| Repeatable | O |
| How to use | 하나의 요소에 전체 키워드를 구분자 (;, “,”, Tab, 기타) 로 구분하여 입력하거나, 개별 요소마다 하나의 키워드를 입력합니다. |
| Refines / refinement | 상위 요소 : text_information |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<keywords>Brazil; COVID-19; Hospitalization; Metformin; Outpatients; Randomized clinical trial.</keywords>
```

### MeSH_headings

| Field | Value |
|---|---|
| Description | PubMed에 색인된 레코드에 부여되는 MeSH 통제어입니다. |
| Required | X |
| Repeatable | O |
| How to use | PubMed API, PubMed XML 등에서 MeSH 통제어 정보를 확인한 뒤, 하나의 요소에 전체 통제어를 구분자로 구분하여 입력하거나, 개별 요소마다 하나의 통제어를 입력합니다. |
| Refines / refinement | 상위 요소 : text_information |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<MeSH_headings>Adult</MeSH_headings>
<MeSH_headings>Antihypertensive Agents* / adverse effects</MeSH_headings>
<MeSH_headings>Antihypertensive Agents* / therapeutic use</MeSH_headings>
<MeSH_headings>Cardiovascular Diseases / mortality</MeSH_headings>
```

### object_link_information

| Field | Value |
|---|---|
| Description | 객체가 다른 객체 등과 연결되는 정보입니다 |
| Required | X |
| Repeatable | X |
| How to use | 객체의 참고문헌/.참고자료 목록을 확인하여 그 식별자를 입력합니다. 식별자가 없는 경우 별도의 임시 레코드를 리포지터리에 생성한 뒤 그 식별자를 연결해 주거나 attribute other선택 후 unavailable로 입력 가능합니다. 하나의 요소에는 하나의 식별자만 입력합니다. |
| Refines / refinement | 하위 요소 : link |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<object_link_information>
  <link link_type="cites" identifier_type="doi">10.1016/j.bbadis.2017.05.027</link>
  <link link_type="citedBy" identifier_type="pmid">35120771</link>
  <link link_type="hasRetraction" identifier_type="other">https://www.sciencedirect.com/science/article/pii/S2667193X21001381</link>
  <link link_type="hasExpressionOfConcern" identifier_type="doi">10.1016/j.lana.2024.100703</link>
</object_link_information>
```

### link

| Field | Value |
|---|---|
| Description | 객체 간 개별 연결에 대한 정보입니다. |
| Required | X |
| Repeatable | O |
| How to use | attribute link_type에서 이 연결이 어떤 의미인지를 통제어를 통해 기술하고, attribute identifier_type을 통해 식별자의 종류가 무엇인지 기술합니다. 그리고 string 정보로 식별자 값을 입력합니다. |
| Refines / refinement | 상위 요소 : object_link_information |
| Controlled vocabulary | See Appendix 6-1, 6-2. |
| Additional info | N/A |

#### Example

```xml
<link link_type="cites" identifier_type="doi">10.1016/j.bbadis.2017.05.027</link>
```

### rights_information

| Field | Value |
|---|---|
| Description | 객체의 저작권과 관련된 정보입니다. |
| Required | X |
| Repeatable | X |
| How to use | 하위 요소들을 통해 저작권에 대한 정보를 분류하여 기술합니다 |
| Refines / refinement | 하위 요소 : rights_status, access_model, publishing_model, license_information, rights_holder, rights_statement |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<rights_information>
  <rights_status>other</rights_status>
  <access_model>open_access</access_model>
  <publishing_model>openaccess_gold</publishing_model>
  <license_information licence_type="creative_commons" licence_code="CC-BY-NC-ND 4.0"/>
</rights_information>
```

### rights_status

| Field | Value |
|---|---|
| Description | 저작권의 현재 상태에 대한 서술입니다. |
| Required | X |
| Repeatable | X |
| How to use | 미리 정해진 value 값을 appendix를 참고하여 입력합니다. |
| Refines / refinement | 상위 요소 : rights_information |
| Controlled vocabulary | See Appendix 7-1. |
| Additional info | N/A |

#### Example

```xml
<rights_status>other</rights_status>
```

### access_model

| Field | Value |
|---|---|
| Description | 객체의 접근 방식과 관련된 정보입니다. |
| Required | X |
| Repeatable | X |
| How to use | 비용을 지불해야 접근이 가능한 경우 subscription으로 입력합니다. 이외의 상태는 appendix를 참고하여 미리 규정된 통제어를 입력합니다. |
| Refines / refinement | 상위 요소 : rights_information |
| Controlled vocabulary | See Appendix 7-2. |
| Additional info | N/A |

#### Example

```xml
<access_model>open_access</access_model>
```

### publishing_model

| Field | Value |
|---|---|
| Description | 학술지 아티클의 출판 모델 정보입니다. |
| Required | X |
| Repeatable | X |
| How to use | appendix를 참고하여 학술지 상태에 대한 통제어를 입력합니다. |
| Refines / refinement | 상위 요소 : rights_information |
| Controlled vocabulary | See Appendix 7-3. |
| Additional info | N/A |

#### Example

```xml
<publishing_model>openaccess_gold</publishing_model>
```

### license_information

| Field | Value |
|---|---|
| Description | 라이선스 관련 정보입니다. |
| Required | X |
| Repeatable | O |
| How to use | license_type attribute에 라이선스 형식을 appendix 7-4를 참고하여 입력하고, license_code에 CC-BY-4.0, Apache와 같은 특정 라이선스 코드를 입력합니다. 관련된 URI가 있는 경우 license_uri attribute에 입력합니다. |
| Refines / refinement | 상위 요소 : rights_information |
| Controlled vocabulary | See Appendix 7-4. |
| Additional info | N/A |

#### Example

```xml
<license_information licence_type="creative_commons" licence_code="CC-BY-NC-ND 4.0"/>
```

### rights_holder

| Field | Value |
|---|---|
| Description | 라이선스 보유자에 대한 정보입니다. |
| Required | X |
| Repeatable | O |
| How to use | 라이선스 보유자를 자유롭게 string 형식으로 입력합니다 (회사, 개인 등) |
| Refines / refinement | 상위 요소 : rights_information |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<rights_holder>Microsoft</rights_holder>
```

### rights_statement

| Field | Value |
|---|---|
| Description | 라이선스 관련하여 객체가 별도로 표시한 내용을 옮겨 적습니다 |
| Required | X |
| Repeatable | O |
| How to use | 라이선스 관련하여 객체가 별도로 표시한 내용을 자유롭게 String 형식으로 입력합니다. |
| Refines / refinement | 상위 요소 : rights_information |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<rights_statement>1999 All rights reserved.</rights_statement>
```

### administrative_metadata

| Field | Value |
|---|---|
| Description | 리포지터리의 관리 메타데이터 입력란입니다. |
| Required | O |
| Repeatable | X |
| How to use | 하위 요소를 활용하여 리포지터리에서 레코드를 관리할 때 사용하는 정보를 기재합니다. |
| Refines / refinement | 하위 요소 : repo_register_id, record_status, created_date, last_modified_date, note_by_repository |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<administrative_metadata>
  <repo_register_id>MMLR2026-38714457</repo_register_id>
  <record_status>created</record_status>
  <created_date>2026-06-12T18:00:00</created_date>
  <last_modified_date>2026-06-12T18:00:00</last_modified_date>
</administrative_metadata>
```

### repo_register_id

| Field | Value |
|---|---|
| Description | 리포지터리 등록번호입니다. |
| Required | O |
| Repeatable | O |
| How to use | 리포지터리마다 단순 정수를 사용할 수도, 문자열과 숫자, 혹은 특수문자가 포함된 ID를 사용할 수 있습니다. |
| Refines / refinement | 상위 요소 : administrative_metadata |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<repo_register_id>MMLR2026-38714457</repo_register_id>
```

### record_status

| Field | Value |
|---|---|
| Description | 메타데이터 레코드 자체에 대한 관리 메타데이터 영역입니다 |
| Required | O |
| Repeatable | X |
| How to use | 미리 정해진 통제어를 사용해 메타데이터 레코드 상태를 기재합니다. |
| Refines / refinement | 상위 요소 : administrative_metadata |
| Controlled vocabulary | See Appendix 8. |
| Additional info | N/A |

#### Example

```xml
<record_status>created</record_status>
```

### created_date

| Field | Value |
|---|---|
| Description | 메타데이터 레코드 생성 시각입니다. |
| Required | O |
| Repeatable | X |
| How to use | xs:dateTime (YYYY-MM-DDTHH:MM:SS 형식으로 입력합니다. 보통 시스템이 자동으로 입력하도록 설계합니다. |
| Refines / refinement | 상위 요소 : administrative_metadata |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<created_date>2026-06-12T18:00:00</created_date>
```

### last_modified_date

| Field | Value |
|---|---|
| Description | 레코드가 최종적으로 수정된 시점입니다. |
| Required | X |
| Repeatable | X |
| How to use | xs:dateTime (YYYY-MM-DDTHH:MM:SS 형식으로 입력합니다. 보통 시스템이 자동으로 입력하도록 설계합니다. 설계에 따라 각 수정 버전은 별도의 아카이브 DB에서 관리합니다. |
| Refines / refinement | 상위 요소 : administrative_metadata |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<revised_date>2026-06-15T13:26:24</revised_date>
```

### note_by_repository

| Field | Value |
|---|---|
| Description | 리포지터리에서 레코드 보완 등을 위한 정보입니다. |
| Required | X |
| Repeatable | O |
| How to use | string 형태로 자유롭게 기술하며, 여러 번 입력할 수 있습니다. |
| Refines / refinement | 상위 요소 : administrative_metadata |
| Controlled vocabulary | N/A |
| Additional info | N/A |

#### Example

```xml
<note_by_repository>메타데이터의 일부 영역 인코딩이 깨진 것으로 보여, 복구가 필요합니다</note_by_repository>
```
