1.Opening narrative
이 GitHub 저장소는 의학도서관 리포지터리에서 연구성과물을 일관된 XML 형식으로 기술하기 위한 메타데이터 스키마를 제공합니다. 
본 스키마 (metadata_for_medical_library_repository) 는 논문뿐 아니라 데이터셋, 이미지, 사운드, 비디오, 소프트웨어, 프로토콜, 기타 문서 자료도 기술할 수 있도록 설계되었습니다.
본 스키마는 리포지터리에 등록되는 객체의 유형, 제목, 날짜, 저자, 외부 식별자, 출처, 인용 정보, 상태, 관련 텍스트 정보, 객체 간 연결 정보, 라이선스/저작권 정보, 관리 메타데이터 등을 구조화하여 표현하는 것을 목표로 합니다.
특히 객체 간 연결을 PREMIS의 구조를 참고하여 식별자를 통해 처리하도록 설계하였습니다. 이를 통해 객체가 다른 객체와 어떻게 연결이 되어 있는지, 즉 어떤 문헌을 참고하고 어떤 문헌에게 인용되었는지, 어떤 Expression of Concern이 발생하였고 어떤 Correction이 있었으며 Retract 공지가 어떻게 처리되었는지 등을 유연하게 연결할 수 있습니다. 또한 인용정보 역시 API 혹은 URI와의 매핑을 통해 실시간으로 반영할 수 있도록 구축되어 있습니다. 

2. Relevant metadata standards
관련 메타데이터 표준은 학술지 메타데이터 유통 표준인 JATS (https://jats.nlm.nih.gov/publishing/1.4/) 와 보존메타데이터 표준인 PREMIS (https://www.loc.gov/standards/premis/) 입니다. XML 스키마로 바로 반영이 어려운 DTD 및 RDF 방식의 표준들을 참고하였기에 실제 Element는 Local에서 정의하는 방식으로 구현했습니다.

3. Vocabulary specification
요소를 정리한 스키마 파일은 MMLR_Schema.xsd입니다.
Schema.md는 각 요소의 의미와 입력 방식을 마크다운 방식으로 정리한 문서입니다.
Appendix.md는 object_category, article_type, author_type, publication_stage, rights_status, record_status 등의 요소에서 사용하는 미리 정의된 attribute와 value를 별도로 정리한 문서입니다.

4. XSD file
https://github.com/JehoYi/metadata_for_medical_library_repository/blob/main/MMLR_Schema.xsd

5. Sample XML records
https://github.com/JehoYi/metadata_for_medical_library_repository/blob/main/mmlr_example_1_retracted_article.xml
https://github.com/JehoYi/metadata_for_medical_library_repository/blob/main/mmlr_example_2_updated_article.xml
https://github.com/JehoYi/metadata_for_medical_library_repository/blob/main/mmlr_example_3_conference_paper.xml


구조에 대한 문의사항은 Comment를 남겨 주시면 확인하여 반영하도록 하겠습니다. 
