# Appendix

이 문서는 Metadata for Medical Library Repository 스키마에서 사용되는 사전 정의된 attribue 및 value들에 대한 정리표입니다. 
Libreoffice Calc에서 내용을 정리한 뒤 ChatGPT를 통해 마크다운 형식으로 다듬었습니다. 
원본 파일은 schema and appendix.ods를 참고해 주시기 바랍니다. 

## Contents

- [Appendix 1-1. object_category attributes](#appendix-1-1-object_category-attributes)
- [Appendix 1-2. article_type attributes](#appendix-1-2-article_type-attributes)
- [Appendix 1-3. dataset_type attributes](#appendix-1-3-dataset_type-attributes)
- [Appendix 1-4. image_type](#appendix-1-4-image_type)
- [Appendix 1-5. sound_type](#appendix-1-5-sound_type)
- [Appendix 2. author_type](#appendix-2-author_type)
- [Appendix 3. author_identifier](#appendix-3-author_identifier)
- [Appendix 4-1. source](#appendix-4-1-source)
- [Appendix 4-2. identifier_type](#appendix-4-2-identifier_type)
- [Appendix 5-1. publication_stage](#appendix-5-1-publication_stage)
- [Appendix 5-2. post_publication_status](#appendix-5-2-post_publication_status)
- [Appendix 5-3. repository_status](#appendix-5-3-repository_status)
- [Appendix 6-1. link_type](#appendix-6-1-link_type)
- [Appendix 6-2. identifier_type](#appendix-6-2-identifier_type)
- [Appendix 7-1. rights_status](#appendix-7-1-rights_status)
- [Appendix 7-2. access_model](#appendix-7-2-access_model)
- [Appendix 7-3. publishing_model](#appendix-7-3-publishing_model)
- [Appendix 7-4. license_type](#appendix-7-4-license_type)
- [Appendix 8. record_status](#appendix-8-record_status)

## Appendix 1-1. object_category attributes

| Attribute | 설명 |
|---|---|
| `article` | 일반 논문 계통인 경우 article로 입력합니다 |
| `dataset` | 데이터 모음집(데이터셋) 인 경우 dataset으로 입력합니다 이미지, 사운드, 비디오 등의 모음집도 데이터셋으로 처리합니다 |
| `image` | 데이터셋에 포함되지 않는 개별 이미지인 경우 image로 처리합니다 |
| `sound` | 데이터셋에 포함되지 않는 개별 소리 자료인 경우 sound로 처리합니다 |
| `video` | 데이터셋에 포함되지 않는 영상자료인 경우 video로 처리합니다 |
| `software` | 연구자가 개발한 소프트웨어, 혹은 링크 등에 필요한 상용 소프트웨어를 입력할 때 사용합니다. 소스 코드도 소프트웨어로 처리합니다 |
| `protocol` | 정식 논문으로 발표되지 않는 실험 프로토콜 등을 여기에 입력합니다 |
| `other` | 기타 문서 자료 등을 처리하기 위해 사용합니다. 특정한 문서자료가 늘어날 경우 해당 문서의 범주를 새로 등록하는 것도 고려해 볼 수 있습니다 |

## Appendix 1-2. article_type attributes

| Attribute | 설명 |
|---|---|
| `original_article` | 일반적으로 원저로 인식되는 원고를 origianl_article로 입력합니다. 기관 지침에 따라 다른 article_type과 병행하여 입력할 수 있습니다. |
| `review_article` | 일반적으로 종설으로 인식되는 원고를 review_article로 입력합니다. 기관의 정책에 따라 original article과 병행해서 사용할 수 있습니다 |
| `case_report` | 일반적으로 증례보고으로 인식되는 원고를 case_report로 입력합니다. 기관의 정책에 따라 original article과 병행해서 사용할 수 있습니다 |
| `randomized_controlled_trial` | 일반적으로 무작위대조임상시험(RCT)으로 인식되는 원고를 randomized_controlled_trial로 입력합니다. 기관의 정책에 따라 original article과 병행해서 사용할 수 있습니다 |
| `editorial` | 일반적으로 학술지 편집자 주 등으로 인식되는 원고를 editorial로 입력합니다. |
| `correction` | 기존 출판된 논문의 수정사항으로 인식되는 원고를 correction으로 입력합니다. |
| `letter` | 학술지 등에서 편집자 또는 타 논문 저자에게 투고된 편지 형식으로 인식되는 원고를 letter로 입력합니다. |
| `conference_paper` | 컨퍼런스에서 발표된 논문 형식의 원고를 conference_paper로 입력합니다. |
| `conference_poster` | 컨퍼런스에서 발표된 포스터 형식의 원고를 conference_poster로 입력합니다. |
| `preprint` | 정식 출판되지 않았지만 공개된 리포지터리(arXiv, medRxiv, etc) 등에 업로드된 출판 전 원고를 preprint로 입력합니다 |
| `others` | 그 외 판단하기 어려운 원고는 others로 입력합니다. |

## Appendix 1-3. dataset_type attributes

| Attribute | 설명 |
|---|---|
| `clinical_dataset` | 임상시험 혹은 임상현장과 관련된 데이터셋입니다 |
| `experimental_dataset` | 임상시험 외 실험과 관련된 데이터셋입니다. |
| `survey_dataset` | 설문조사와 관련된 데이터셋입니다. 경우에 따라 임상시험 데이터셋과 함께 쓰일 수 있습니다. |
| `imaging_dataset` | CT/MRI 영상 등 이미지 데이터셋입니다 |
| `genomic_dataset` | 유전자 검사, 혹은 유전자 시뮬레이션 데이터 등과 관련된 데이터셋입니다 |
| `administrative_dataset` | 실험 등과 직접적으로 관련되지 않은, 업무 관리 등에 해당하는 데이터셋입니다. 학술지 출판 APC 지원 데이터 등을 할당할 수 있습니다. |
| `statistical_dataset` | 통계와 관련된 데이터셋입니다. 경우에 따라 임상시험 데이터셋 등과 함께 쓰일 수 있습니다. |
| `other_dataset` | 기타 데이터셋입니다 |

## Appendix 1-4. image_type

| Attribute | 설명 |
|---|---|
| `clinical_image` | 임상시험 혹은 임상현장과 관련된 이미지입니다 |
| `article_image` | 논문과 관련된 이미지입니다(Figure n 등) |
| `dataset_image` | 데이터셋과 관련된 이미지입니다(데이터셋 구조도 등) |
| `experiment_image` | 실험과 관련된 이미지입니다(실험실 사진 등) |
| `interview_image` | 인터뷰와 관련된 이미지입니다 (참가자 사진 등) |
| `other_image` | 기타 이미지입니다. |

## Appendix 1-5. sound_type

| Attribute | 설명 |
|---|---|
| `clinical_sound` | 임상시험 혹은 임상현장과 관련된 소리자료입니다 |
| `article_sound` | 논문출판과 관련된 소리자료입니다 |
| `dataset_sound` | 데이터셋과 관련된 소리자료입니다 |
| `experiment_sound` | 실험과 관련된 소리자료입니다 |
| `interview_sound` | 인터뷰와 관련된 소리자료입니다 |
| `other_sound` | 기타 소리자료입니다 |

## Appendix 2. author_type

| Attribute | 설명 |
|---|---|
| `1st_author` | 저자가 제1저자로 확인되는 경우 입력합니다. 공동 제1저자도 포함됩니다. |
| `co_author` | 저자가 특별한 표기가 없는 공동저자인 경우 입력합니다. |
| `senior_author` | 논문에서 저자가 Senior Author로 지정되어 있는 경우 입력합니다 |
| `corresponding_author` | 논문에서 저자가 교신저자로 지정되어 있는 경우 입력합니다 |
| `other` | 기타 특수한 저자 형태인 경우 입력합니다 |

## Appendix 3. author_identifier

| Attribute | 설명 |
|---|---|
| `orcid` | ORCID 식별자를 입력합니다 |
| `researcherid` | Web of Science에서 사용하는 ResearcherID를 입력합니다 |
| `scopus` | Scopus에서 자동으로 생성된 저자ID를 입력합니다 |
| `other` | 기타 식별자를 입력합니다. 가급적 [식별자명]ID의 형태로 입력합니다. 예) [CustomID]0002_ST_4018 |

## Appendix 4-1. source

| Attribute | 설명 |
|---|---|
| `opencitations` | opencitations 데이터셋에서 인용정보를 수집한 경우 입력합니다. |
| `google_scholar` | google scholar에서 인용정보를 수집한 경우 입력합니다. |
| `pubmed` | 미의학도서관 PubMed에서 인용정보를 수집한 경우 입력합니다. |
| `wos` | Clarivate Web of Science에서 인용정보를 수집한 경우 입력합니다. |
| `scopus` | Elsevier Scopus에서 인용정보를 수집한 경우 입력합니다. |
| `altmetric` | Altmetric에서 인용정보를 수집한 경우 입력합니다. |
| `demensions` | Demensions에서 인용정보를 수집한 경우 입력합니다. |
| `crossref` | CrossRef에서 인용정보를 수집한 경우 입력합니다. |
| `internal` | 리포지터리 내에서의 인용정보를 입력할 때 사용합니다. 시스템이 구축되어 있다면 자동으로 인용-피인용 링크 정보를 이용해 갱신합니다. |
| `other` | 기타 인용정보 출처입니다. |

## Appendix 4-2. identifier_type

| Attribute | 설명 |
|---|---|
| `doi` | DOI 식별자를 입력합니다. |
| `pmid` | PubMed에서 사용하는 PMID 식별자를 입력합니다. |
| `pmcid` | PubMed Central 에 등록된 논문의 경우 PMCID를 입력합니다 |
| `wos_ut` | Web of Science에 색인된 논문의 경우 그 고유식별자인 UT를 입력합니다. |
| `scopus_eid` | Scopus에 색인된 논문의 경우 그 고유식별자인 EID를 입력합니다 |
| `internal_id` | 리포지터리 내에서의 인용정보를 입력할 때 사용합니다. repo_register_id를 입력할 때 이 속성을 사용합니다. |
| `url` | URL을 식별자로 사용할 때 입력합니다. |
| `other` | 기타 식별자입니다. |

## Appendix 5-1. publication_stage

| Attribute | 설명 |
|---|---|
| `Value` | 설명 |
| `not_submitted` | 제출 전 자료를 의미합니다 |
| `submitted` | 학술지, DB, 컨퍼런스 등에 제출하고 현재 평가가 진행중인 상태입니다 |
| `accepted_not_opened` | 내부적으로 출판 등이 승인되었으나 외부에 공개되지 않은 상태입니다 |
| `just_accepted` | 승인되어 공개되었으나 포맷 등이 적용되지 않은 상태입니다 |
| `online_published` | 정식 권호 출판은 되지 않고, 온라인 형태로 포맷이 적용된 상태입니다 |
| `issue_published` | 정식 권호로 출판된 상태입니다. 온라인 학술지의 경우 issue가 없을 수 있습니다 |
| `conference_published` | 컨퍼런스에서 발표된 경우 사용합니다 |
| `preprint_posted` | arXiv와 같은 프리프린트 서버에 게시된 경우입니다 |
| `unpublished` | 출판되지 않은 자료입니다 |
| `not_applicable` | 출판 단계에 대해 기술하기 어려운 자료를 의미합니다 |
| `unknown` | 고아 저작물 등을 수집했을 때 그 자료의 상태를 알기 어려운 경우 등에 사용합니다 |
| `other` | 기타 상태를 의미합니다. |

## Appendix 5-2. post_publication_status

| Attribute | 설명 |
|---|---|
| `corrected` | 출판 후 오류 등이 수정된 상태입니다. erratum, corrigendum 등을 포함합니다 |
| `expression_of_concern` | 출판 후 그 내용에 대해 이의가 제기된 상태입니다 |
| `withdrawn_by_author` | 출판 후 저자가 직접 철회한 상태입니다 |
| `retracted` | 출판 후 학술지나 출판사 등 저자 외의 주체에 의해 논문 등이 철회 또는 게시에서 내려간 상태입니다 |
| `unknown` | 상태의 정확한 확인이 어려운 경우 입력합니다. |
| `other` | 기타 상태를 의미합니다. |

## Appendix 5-3. repository_status

| Attribute | 설명 |
|---|---|
| `Value` | 설명 |
| `submitted` | 리포지터리에 등록을 요청한 상태입니다. |
| `under_review` | 리포지터리 등록 여부를 결정하기 위한 리뷰 단계입니다. |
| `approved` | 리포지터리 등록이 승인되었으나 아직 공개되지 않은 단계입니다. |
| `published` | 리포지터리 등록 후 공개된 단계입니다. |
| `rejected` | 리포지터리 리뷰 단계에서 탈락한 경우 입력합니다. |
| `withdrawn_by_author` | 리포지터리 등록 요청 단계 이후, 리포지터리 제출자가 직접 등록 해제 요청 시 사용합니다 |
| `archived_not_published` | 리포지터리에 등록이 승인되었으나 제출자가 공개를 거부했을 때 기재합니다 |
| `deleted` | 보관기관 만료 등으로 인해 삭제된 경우 기재합니다 |
| `unknown` | 객체의 상태를 알 수 없는 경우 기재합니다. |
| `other` | 기타 상태사항입니다. |

## Appendix 6-1. link_type

| Attribute | 설명 |
|---|---|
| `cites` | 본 레코드가 참조하는 객체가 인용한 다른 객체들을 서술합니다 |
| `citedBy` | 본 레코드가 참조하는 객체를 인용하는 다른 객체들을 서술합니다 |
| `hasRetraction` | retraction이 발생했을 경우 그 공지문을 연결합니다 |
| `isRetractionOf` | 객체 자체가 다른 객체에 대한 철회문일 경우 그 대상 객체를 연결합니다 |
| `hasExpressionOfConcern` | 객체에 대한 우려 표명(expression of concern)이 발행되었을 때 그 대상 객체를 연결합니다 |
| `isExpressionOfConernOf` | 객체 자체가 다른 객체에 대한 우려 표명인 경우 그 객체를 연결합니다 |
| `hasErratum` | 객체에 대한 수정사항(erratum, correction 등)이 발행되었을 때 그 대상 객체를 연결합니다 |
| `isErratumOf` | 객체 자체가 다른 객체에 대한 수정사항인 경우 그 객체를 연결합니다 |
| `hasReply` | 객체에 대한 응답 letter (reply/comment) 가 발행된 경우 그 객체를 연결합니다 |
| `isReplyOf` | 객체 자체가 다른 객체에 대한 응답 letter (reply/comment) 인 경우 그 대상 객체를 연결합니다 |
| `isVersionOf` | 본 레코드가 참조하는 객체의 최초 버전이 있는 경우, 그 최초 버전의 객체를 연결합니다 |
| `hasNewerVersion` | 본 레코드가 참조하는 객체의 새로운 버전이 있는 경우, 그 새로운 버전의 객체를 연결합니다 |
| `isRelatedWith` | 위에 정의된 방식 외 본 레코드와 연관된 객체를 연결합니다 |

## Appendix 6-2. identifier_type

| Attribute | 설명 |
|---|---|
| `doi` | DOI 식별자를 입력합니다. |
| `pmid` | PubMed의 PMID 식별자를 입력합니다. |
| `repository_id` | 리포지터리에 저장된 식별자를 입력합니다. |
| `other` | 기타 정의되지 않은 식별자의 경우입니다. 식별자가 없는 자료인 경우 리포지터리에 임시 레코드를 생성하거나, other>unavailable로 입력 가능합니다. |

## Appendix 7-1. rights_status

| Attribute | 설명 |
|---|---|
| `Value` | 설명 |
| `copyrighted` | 저작권 보호가 유효한 자료인 경우 이 값을 이용합니다 |
| `public_domain` | 현재 저작권이 만료되어 퍼블릭 도메인 상태인 경우 이 값을 이용합니다. |
| `unknown` | 저작권이 만료되었는지, 혹은 누군가에게 귀속되어 있는지 알 수 없는 경우 이 값을 이용합니다. |
| `not_applicable` | 저작권 관련 정보를 지정할 수 없는 객체의 경우 이 값을 이용합니다. |
| `other` | 기타 특수한 상태인 경우 이 값을 이용합니다. |

## Appendix 7-2. access_model

| Attribute | 설명 |
|---|---|
| `Value` | 설명 |
| `open_access` | 어떠한 형태로든 OpenAccess로 접근 가능하면 사용합니다 |
| `free_to_read` | OpenAccess가 아니지만 출판사 등 저작권자에 의해 임의로 개방된 자료의 경우 사용합니다 |
| `restricted` | 접근이 제한된 경우 입력합니다. Paywall을 통해 제한된 경우 아래의 subscription을 사용합니다 |
| `embargoed` | 공개 전까지 엠바고가 걸려 있는 자료의 경우 입력합니다 |
| `subscription` | Paywall 등으로 접근이 제한되어 비용을 지불할 경우 열람이 가능하다면 입력합니다 |
| `institution_member_only` | 학회, 기관 회원인 경우에만 열람 가능한 경우 입력합니 |
| `unknown` | 접근권에 대한 정보가 없는 경우 입력합니다 |
| `other` | 기타 접근 권한에 대해 입력합니다 |

## Appendix 7-3. publishing_model

| Attribute | 설명 |
|---|---|
| `Value` | 설명 |
| `traditional` | 전통적인 학술지 출판 방식 (출판사/학술지가 저작권 소유, Paywalled) 인 경우 입력합니다 |
| `openaccess_gold` | Gold Open Access 방식 (주로 APC) 인 경우 입력합니다 |
| `openaccess_green` | Green Open Access 방식 (저자가 직접 논문을 리포지터리에 기탁하여 공개되는 경우) 입력합니다 |
| `openaccess_hybrid` | OA가 아닌 학술지에서 OA 옵션을 제공하여 이를 통해 OA 형식으로 출판된 논문의 경우 입력합니다 |
| `openaccess_diamond` | APC가 없는 Diamond OA 방식으로 출판된 경우 입력합니다 |
| `openaccess_other` | 기타 방식으로 OA 출판이 된 경우 입력합니다 |
| `not_applicable` | 출판방식을 적용할 수 없는 객체들(Editorial, Invited Review, Comment 등)에 대해 이 값을 적용합니다 |
| `unknown` | 출판방식을 알 수 없는 경우 적용합니다 |
| `other` | 기타 출판방식입니다 |

## Appendix 7-4. license_type

| Attribute | 설명 |
|---|---|
| `creative_commons` | Creative Commons 방식으로 출판/공개된 경우 적용합니다 |
| `open_source` | 오픈소스 방식으로 공개된 경우 적용합니다 |
| `proprietary` | 저작권이 특정 저작권자에게 귀속되어 보호받고 소스가 공개되지 않은 경우 적용합니다. 저작권이 출판사에게 있는 경우에도 이를 적용합니다(특수한 경우 제외) |
| `public_domain` | 저작권이 만료되어 공공에게 개방된 경우 적용합니다 |
| `rights_statement` | 특정한 형태로 권리가 선언된 경우 적용합니다 (개인사용 가능, 재배포 또는 상업적 이용 시 저작권자 허락 등 CC외 저작권자가 임의로 지정한 경우) |
| `unknown` | 라이선스 정보를 알 수 없는 경우 적용합니다 |
| `other` | 기타 정의되지 않은 라이선스 정보입니다. |

## Appendix 8. record_status

| Attribute | 설명 |
|---|---|
| `created` | 메타데이터가 생성된 경우 기재합니다. |
| `revised` | 메타데이터가 수정된 경우 기재합니다. |
| `deprecated` | 만료되어 삭제될 예정인 레코드의 경우 시스템이 자동으로 값을 deprecated로 전환합니다. |
| `superseded_by_other_record` | 다른 레코드로 이 레코드가 대체/갱신되었을 때 기재합니다. |
| `deleted` | 메타데이터가 삭제된 경우 기재합니다. |
| `unknown` | 메타데이터의 상태를 알 수 없는 경우 기재합니다. |
| `other` | 기타 특수한 상황에 대해 기재합니다. |
