# DEND

## 1 WEEK

- data engineer skill sets and roles
- data storage and processing
- move/store/explore/transform

- conceptional, logical, physical

- what is data modeling
    - the process of creating data models

- ddl(Data Definition Language)
    - CREATE, DROP, ALTER, TRUNCATE

- schema란 서로 연결되어 있는 테이블들의 모음이다
- ad-hoc 쿼리란 즉시, 바로, 임시의 의미를 가지고 있다. 
- acid(atomicity,consistency,isolation,durability)
- 일치하는 값을 포함하는 각 테이블의 열이있는 한 두 테이블을 조인 할 수 있다.
- When Not to Use a Relational Database
    - Have large amounts of data
    - Need to be able to store different data type formats
    - Need high throughput -- fast reads
    - Need a flexible schema
    - Need high availability
    - Need horizontal scalability

- 관계형 데이터베이스는 적은 양의 데이터가 있고 테이블에 조인하거나 집계를 수행해야하거나 데이터를 분석해야하는 경우 최적의 데이터베이스 선택입니다. ACID 트랜잭션을 허용하므로 비즈니스 요구에 중요하다면 관계형 데이터베이스를 유지하십시오.

- 카산드라
    -  A keyspace is a collection of tables

- relational Databases Modelingd
    - Standardization of data model
    - Flexibility in adding and altering tables
    - Data Integrity
    - Standard Query Language (SQL)
    - Simplicity 
    - Intuitive Organization


- 정규화 : 데이터 중복성을 줄이고 데이터 무결성을 향상시킵니다.

- Objectives of Normal Form:
```
To free the database from unwanted insertions, updates, & deletion dependencies
To reduce the need for refactoring the database as new types of data are introduced
To make the relational model more informative to users
To make the database neutral to the query statistics
```

- 역정규화(denormalization)
 이전에 정규화된 데이터베이스에서 성능을 개선하기 위해 사용되는 전략이다. 컴퓨팅에서 역정규화는 일부 쓰기 성능의 손실을 감수하고 데이터를 묶거나 데이터의 복제 사본을 추가함으로써 데이터베이스의 읽기 성능을 개선하려고 시도하는 과정이다.[1][2] 아주 많은 수의 읽기 작업을 처리할 필요가 있는 관계형 데이터베이스 소프트웨어의 성능이나 스케일링에서 고려된다. 역정규화는 비정규화(unnormalized form)와는 구별한다. 데이터베이스/테이블은 이들을 효율적으로 역정규화하기 위해 우선 정규화되어야 한다.

 -  Normalization  데이터의 사본 수를 줄임으로써 데이터 무결성을 높이려는 것입니다. 추가하거나 업데이트해야하는 데이터는 가능한 한 적은 곳에서 처리됩니다.


- Denormalization 는 조인이 느려질 수 있으므로 테이블 간의 조인 수를 줄여 성능을 향상 시키려고합니다. JOINS를 줄이기 위해 데이터의 사본이 더 많아지기 때문에 데이터 무결성이 잠재적 인 영향을 미칩니다.

- 스타 스키마는 데이터 웨어하우스 스키마 중 가장 단순한 종류의 스키마인데, 한 개의 사실 테이블과 주 키 및 각 차원과 추가적인 사실들로 이루어진 스키마이다. 스타 스키마라는 이름은 스키마 다이어그램이 마치 "별표(star)" 모양이라 해서 붙인 이름이다

- 유니크 키 
본 키(primary key)는 주 키 또는 프라이머리 키라고 하며, 관계형 데이터베이스에서 조(레코드)의 식별자로 이용하기에 가장 적합한 것을 관계 (테이블)마다 단 한 설계자에 의해 선택, 정의된 후보 키를 말한다.

- 외래키 
관계형 데이터베이스에서 외래 키(외부 키, Foreign Key)는 한 테이블의 필드(attribute) 중 다른 테이블의 행(row)을 식별할 수 있는 키를 말한다.

- upsert
In RDBMS language, the term upsert refers to the idea of inserting a new row in an existing table, or updating the row if it already exists in the table. The action of updating or inserting has been described as "upsert"


- when not to use SQL

데이터에서 고 가용성 필요 : 시스템이 항상 가동 중이며 가동 중지 시간이 없음을 나타냅니다.
많은 양의 데이터 보유
선형 확장 성 필요 : 시스템에 노드를 추가해야 성능이 선형 적으로 증가합니다.
낮은 대기 시간 : 전송 지시가 수신되면 데이터가 전송되기 전에 짧은 지연.
빠른 읽기 쓰기 필요

- CAP Theorem

Consistency: Every read from the database gets the latest (and correct) piece of data or an error

Availability: Every request is received and a response is given -- without a guarantee that the data is the latest update

Partition Tolerance: The system continues to work regardless of losing network connectivity between nodes

- 아파치 카산드라
조인이 없기에, 비정규화를 제대로 시켜놓고 개발자가 미리 숙지해야함.

- CQL
no JOIN no GROUP BY and there's not any subqueries


- 
1. primary key 

DB의 pk와 비슷하다. row를 유일무이하게 해주는 key를 의미한다. 1개 이상의 키가 필요하다. 

2. composite(compound) key

primary key가 2개 이상이면 composite key라 부른다.

3. partition key

partition key는 primary key의 1번째 key(예시에서는 col1)를 의미한다. 저장소 row key로 직접 변환하고 해시 알고리즘에 따라 클러스터에 저장(분배)된다. 대부분의 질의는 partition key를 제공해서 카산드라는 요청된 데이터가 어느 노드에 있는지 알게 된다. 

4. clustering key

primary key의 1번째 key외 나머지 key를 clustering key(또는 clustering column)라 한다. 해당 key는 디스크에 데이터 순서를 안다. 하지만 어느 노드에 저장될지는 결정하지 않는다. 
순서 관련해서 오름차순, 내림차순으로 변경할 수 있다. 

[출처](https://knight76.tistory.com/entry/cassandra-키의-종류-primary-key-partition-key-clustering-key-compositecompound-key-composite-partition-key)