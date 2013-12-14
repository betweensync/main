### 1차 작업 R&R

* 각 파트(구간)별 데모 환경 구축

1. Mobile에서 변경 내용 감지 (JD)
2. 파일 메타를 Couch에 저장해서 서버 Couch와 동기화 및 이벤트 (MH)
3. Client에서 파일을 읽어 ActiveMQ에 저장까지 (CJ)
4. ActiveMQ에서 읽어 S3에 저장 (JW)

* 2차 계획: 각자 만든 Demo 환경 연동

### Jerry

* Client를 CouchDB로 가정하여 Cloudant 서버 DB와 동기화 테스트
* CouchDB에 데이터를 넣으면 Cloudant DB에서 데이터를 Event 형태로 수신
* Event 수신은 Java 프로그램에서 담당
* Cloudant DB에서 발생한 변경 내용을 CouchDB의 각 DB(각 user를 가정)로 동기화
* Client에서 발생한 Event를 Java 프로그램에서 수신
* DB 스키마를 파일 메타에 맞게 작성

* 시간이 허락하면 Mobile용 DB를 설치하고 동일한 시나리오 테스트


### Jiwoong
* Amazon AWS : https://919279951576.signin.aws.amazon.com/console
* ActiveMQ: http://54.238.120.65:8161/hawtio/#/activemq/browseQueue?nid=root-org.apache.activemq-Broker-localhost-Queue-storage-sync
* 현재 랩탑의 File을 ActiveMQ로 전송하고, 소비된 데이터를 Local에 저장
* 로컬에 저장된 데이터는 S3를 통해 사용자 버킷/서버 디렉토리/파일의 형태로 모바일과 동일한 구성을 가지도록 함.
* ActiveMQ, S3 현재 연동된 상태
* TODO: 아마존 디렉토리 구조 생성 및 putObject 

### Jongdae


### Changjae
* ActiveMQ 를 위해서 MQTT, STOMP 두개 사용 고민
* MQTT 는 topic 만 지원하고, 너무 simple 한 protocol 이라 일단 framework 개발이 필요함 - ToDo 
* 데모는 STOMP 로 개발 (http://activemq.apache.org/apollo/documentation/stomp-manual.html)
* HA/LB 를 위해서 JMSXGroupId, JMSXGroupSec


