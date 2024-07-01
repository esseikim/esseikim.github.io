---
title: "[Interview] Database"
categories: [Study, Interview]
---

## **오라클 시퀀스 (Oracle Sequence)**

---

- 오라클 시퀀스는 고유한(UNIQUE) 값을 생성해주는 오라클 객체이다. 주로 기본 키(PK)와 같이 순차적으로 증가하는 값을 자동으로 생성하는 데 사용된다.
- 시퀀스를 생성하는 SQL 구문은 다음과 같다.
    
    ```sql
    CREATE SEQUENCE 시퀀스이름
        START WITH n
        INCREMENT BY n
        [옵션들]
    ```
    
    - **`START WITH n`**: 시퀀스가 시작하는 초기 값
    - **`INCREMENT BY n`**: 시퀀스가 증가하는 간격을 지정한다. 양수로 지정하면 증가, 음수로 지정하면 감소한다.
    - **`[옵션들]`**: 시퀀스 생성 시 추가로 설정할 수 있는 옵션들(예: **`MAXVALUE`**, **`MINVALUE`**, **`CYCLE`**, **`NOCYCLE`**, **`CACHE`**, **`NOCACHE`** 등).
- 시퀀스를 사용하여 값을 생성하려면 **`NEXTVAL`** 키워드를 사용한다.
    
    ```sql
    SELECT 시퀀스이름.NEXTVAL FROM DUAL;
    ```
    
- 시퀀스 값을 참조하려면 **`CURRVAL`** 키워드를 사용한다.
    
    ```sql
    SELECT 시퀀스이름.CURRVAL FROM DUAL;
    ```
    

## **DBMS란?**

---

- 데이터베이스 관리 시스템(DBMS)은 다수의 사용자가 데이터베이스 내의 데이터를 효율적으로 접근하고 관리할 수 있도록 설계된 소프트웨어 시스템이다.
- DBMS는 데이터 무결성, 보안, 데이터 회복, 동시성 제어 등 다양한 기능을 통해 데이터베이스의 안정적 운영을 지원한다.
    - **데이터 무결성**: 데이터의 정확성과 일관성을 유지한다.
    - **보안**: 권한 관리 및 접근 제어를 통해 데이터를 보호한다.
    - **데이터 회복**: 장애 발생 시 데이터를 복구할 수 있도록 한다.
    - **동시성 제어**: 다수의 사용자가 동시에 데이터베이스에 접근할 때 발생할 수 있는 충돌을 방지한다.
- DBMS는 다음과 같은 주요 기능을 제공한다.
    1. **정의 기능 (DDL: Data Definition Language)**
        - 데이터베이스 구조를 정의하는 기능으로, 데이터베이스가 어떤 용도로 사용되며 어떻게 이용될 것인지에 대한 정의를 포함한다.
        - 주요 명령어: **`CREATE`**, **`ALTER`**, **`DROP`**, **`RENAME`**
            - **CREATE**: 데이터베이스 객체(테이블, 인덱스, 시퀀스 등)를 생성한다.
            - **ALTER**: 기존 데이터베이스 객체의 구조를 변경한다.
            - **DROP**: 데이터베이스 객체를 삭제한다.
            - **RENAME**: 데이터베이스 객체의 이름을 변경한다.
    2. **조작 기능 (DML: Data Manipulation Language)**
        - 데이터베이스에 저장된 데이터를 조회, 삽입, 수정, 삭제하는 기능을 제공한다.
        - 주요 명령어: **`SELECT`**, **`INSERT`**, **`UPDATE`**, **`DELETE`**
            - **SELECT**: 데이터베이스에서 데이터를 조회한다.
            - **INSERT**: 데이터베이스에 새 데이터를 삽입한다.
            - **UPDATE**: 기존 데이터를 수정한다.
            - **DELETE**: 데이터베이스에서 데이터를 삭제한다.
    3. **제어 기능 (DCL: Data Control Language)**
        - 데이터베이스 접근을 제어하고, 사용자에게 권한을 부여하거나 회수하는 기능을 포함한다.
        - 주요 명령어: **`GRANT`**, **`REVOKE`**
            - **GRANT**: 사용자에게 특정 권한을 부여한다.
            - **REVOKE**: 사용자에게 부여된 권한을 회수한다.

## **UML이란?**

---

- UML(Unified Modeling Language)은 소프트웨어 개발에서 시스템을 시각적으로 표현하는 데 사용되는 표준화된 모델링 언어이다. 복잡한 시스템을 이해하기 쉽게 표현하고 의사소통을 원활하게 하기 위해 만들어졌다.
- **주요 특징**
    - **다양한 다이어그램 제공**: UML은 클래스 다이어그램, 시퀀스 다이어그램, 유스 케이스 다이어그램 등 다양한 다이어그램을 통해 시스템의 구조와 동작을 시각화한다.
    - **표준화된 표기법**: 일관된 표기법을 사용하여 개발자 간의 의사소통을 용이하게 한다.
    - **소프트웨어 개발 프로세스 지원**: 요구 분석, 설계, 구현, 테스트 등 소프트웨어 개발의 모든 단계에서 활용된다.

## **DB에서 View는 무엇인가?**

---

- 뷰(View)는 데이터베이스 내에서 하나 이상의 테이블에서 유도된 가상 테이블이다.
- **주요 특징**
    - **가상 테이블**: 실제 데이터를 저장하지 않고, 쿼리를 통해 생성된 결과를 제공하는 가상 테이블이다.
    - **데이터 제한**: 허용된 데이터를 제한적으로 보여줄 수 있어 보안과 데이터 접근 제어에 유용하다.
    - **유도된 데이터**: 사용자가 뷰에 접근할 때마다, 뷰에 정의된 쿼리를 실행하여 원본 데이터에서 필요한 데이터를 가져온다.
    - **보호 기능**: 중요한 데이터를 직접 노출하지 않고, 뷰를 통해 접근함으로써 데이터를 보호할 수 있다.

## **정규화란?**

---

- 정규화(Normalization)는 데이터베이스 설계에서 데이터 중복을 최소화하고 데이터의 무결성을 유지하기 위해 데이터를 구조화하는 과정이다. 이는 데이터를 논리적이고 일관되게 저장하는 것을 목표로 한다.
- 이상현상이 일어나지 않도록 정규화한다.
- 데이터 구조화: 데이터를 중복 없이 구조화하여 저장한다.
- 정규화는 데이터베이스 설계의 중요한 부분으로, 올바르게 적용하면 데이터의 일관성을 유지하고 저장 공간을 효율적으로 사용하며, 데이터베이스의 성능을 최적화할 수 있다.

### **정규화의 목적**

---

- **중복 데이터 최소화**: 데이터를 중복 없이 저장하여 저장 공간을 효율적으로 사용하고, 데이터 일관성을 유지한다.
- **데이터 무결성 유지**: 데이터 삽입, 갱신, 삭제 시 발생할 수 있는 이상 현상(Anomalies)을 방지한다.

### **정규화 과정**

---

- 정규화는 여러 단계로 이루어지며, 각 단계는 특정 규칙을 준수한다. 각 단계는 이전 단계의 문제점을 해결하며, 주로 다음과 같은 단계로 나뉜다.
    1. **제1정규형 (1NF)**: 모든 컬럼이 원자 값을 가지도록 테이블을 구조화한다.
    2. **제2정규형 (2NF)**: 제1정규형을 만족하며, 부분 함수 종속을 제거한다.
    3. **제3정규형 (3NF)**: 제2정규형을 만족하며, 이행 함수 종속을 제거한다.
    4. **BCNF (Boyce-Codd Normal Form)**: 모든 결정자가 후보 키인 것을 요구한다.
    5. **제4정규형 (4NF)**: 다치 종속을 제거한다.
    6. **제5정규형 (5NF)**: 조인 종속을 제거한다.

### **정규화의 중요성**

---

- 정규화를 통해 데이터베이스의 구조를 개선하고 데이터의 무결성을 보장할 수 있다.
- 데이터의 중복을 줄여 저장 공간을 효율적으로 사용하고, 데이터 일관성을 유지한다.
- 이상 현상이 발생하지 않도록 테이블을 설계하여 데이터베이스의 안정성과 신뢰성을 높인다.

## **이상현상이란?**

---

- 이상현상(Anomalies)은 데이터베이스의 릴레이션에서 일부 속성들의 종속으로 인해 데이터 중복이 발생하고, 이로 인해 데이터 일관성이 깨지는 현상을 말한다.
- **주요 유형**
    1. **삽입 이상 (Insertion Anomaly)**: 새로운 데이터를 삽입할 때 불필요한 데이터도 함께 삽입해야 하는 문제.
    2. **갱신 이상 (Update Anomaly)**: 데이터를 갱신할 때 데이터의 일부만 갱신되어 데이터 불일치가 발생하는 문제.
    3. **삭제 이상 (Deletion Anomaly)**: 데이터를 삭제할 때 의도하지 않은 데이터까지 함께 삭제되는 문제.

## **데이터베이스를 설계할 때 가장 중요한 것**

---

- 데이터베이스 설계에서 가장 중요한 것은 **데이터 무결성을 보장하는 것**이다. 무결성은 데이터의 정확성과 일관성을 유지하는 것을 의미한다.

### **무결성 보장 방법**

---

1. **프로그램 내 검증**: 데이터 생성, 수정, 삭제 시 애플리케이션 내에서 무결성 조건을 검증한다.
2. **트리거 사용**: 특정 이벤트 발생 시 자동으로 실행되는 트리거를 사용하여 무결성 조건을 강제한다.
3. **DB 제약조건 선언**: 데이터베이스에서 제공하는 제약조건(Constraints)을 사용하여 무결성을 보장한다.
    - **기본 키(Primary Key)**: 각 행을 고유하게 식별한다.
    - **외래 키(Foreign Key)**: 참조 무결성을 유지한다.
    - **고유 키(Unique Key)**: 중복을 허용하지 않는 필드를 정의한다.
    - **체크 제약조건(Check Constraint)**: 특정 조건을 만족하는 데이터만 입력되도록 한다.

### **데이터베이스 무결성이란?**

---

- 데이터베이스 무결성(Integrity)이란 데이터베이스 내의 데이터가 정확하고 일관되며, 신뢰성을 유지하는 것을 의미한다.
- **주요 원칙**
    - **유일한 식별자**: 각 테이블의 모든 행은 유일한 식별자(Primary Key)를 가져야 한다. 즉, 동일한 값이 존재할 수 없다.
    - **참조 무결성**: 외래 키(Foreign Key) 값은 NULL이거나 참조하는 테이블의 기본 키(Primary Key) 값이어야 한다.
    - **데이터 유효성**: 각 컬럼에 대해 NULL 허용 여부, 자료형, 그리고 타당한 데이터 값을 지정하여 유효한 데이터만 입력되도록 한다.

### **트리거란?**

---

- 트리거(Trigger)는 데이터베이스에서 특정 이벤트가 발생할 때 자동으로 실행되도록 정의된 저장 프로시저이다.
- **주요 특징**
    - **자동 실행**: 데이터베이스 테이블에 대해 **`INSERT`**, **`UPDATE`**, **`DELETE`** 문이 실행될 때 자동으로 호출된다.
    - **업무 규칙 보장**: 데이터의 일관성을 유지하고, 특정 비즈니스 로직을 자동으로 실행하여 규칙을 보장한다.
    - **데이터 무결성 강화**: 데이터베이스의 무결성을 유지하고, 자동화된 처리를 통해 데이터 일관성을 강화한다.
    

## **오라클과 MySQL의 차이**

---

### **오라클(Oracle)**

- **대규모 트랜잭션 처리**: 대규모 트랜잭션 로드를 처리할 수 있는 기능을 제공한다.
- **성능 최적화**: 여러 서버에 대용량 데이터베이스를 분산시켜 성능을 최적화할 수 있다.
- **고급 기능**: 데이터 보안, 고가용성, 복구 기능 등이 뛰어나고, 엔터프라이즈 환경에 적합하다.

### **MySQL**

- **단일 데이터베이스**: 주로 단일 데이터베이스로 운영되며, 대규모 데이터베이스 처리에는 적합하지 않다.
- **작은 프로젝트에 적합**: 소규모 프로젝트나 웹 애플리케이션에 적합하며, 설정과 관리가 상대적으로 간단하다.
- **복구 기능**: 이전 상태를 복원하는 데 **`COMMIT`**과 **`ROLLBACK`**을 사용하여 트랜잭션 관리를 지원한다.

## **Commit과 Rollback이란?**

---

### **Commit**

- **정의**: 하나의 논리적 단위(트랜잭션)에 대한 작업이 성공적으로 끝났을 때, 그 트랜잭션이 행한 모든 변경 내용을 데이터베이스에 반영하는 연산이다.
- **용도**: 트랜잭션 완료를 데이터베이스 관리자에게 알리고, 데이터를 영구적으로 저장한다.

### **Rollback**

- **정의**: 하나의 트랜잭션 처리가 비정상적으로 종료되거나 오류가 발생했을 때, 해당 트랜잭션이 행한 모든 변경 내용을 취소하는 연산이다.
- **용도**: 데이터베이스의 일관성을 유지하고, 변경 내용을 원래 상태로 되돌린다.

## **JDBC와 ODBC의 차이**

---

### **JDBC(Java Database Connectivity)**

- **정의**: 자바 애플리케이션에서 데이터베이스에 접근하여 데이터를 조회, 삽입, 수정, 삭제할 수 있도록 하는 API이다.
- **특징**: DBMS 종류에 따라 맞는 JDBC 드라이버를 설치해야 한다.
- **주요 사용처**: 자바 기반 애플리케이션과 데이터베이스 간의 통신을 지원한다.

### **ODBC(Open Database Connectivity)**

- **정의**: 다양한 응용 프로그램에서 데이터베이스에 접근하기 위한 표준 개방형 API이다.
- **특징**: Microsoft에서 개발하였으며, Excel, 텍스트 파일 등 여러 종류의 데이터에 접근할 수 있다.
- **주요 사용처**: 플랫폼 독립적으로 다양한 데이터 소스에 접근할 수 있도록 지원한다.

## **데이터베이스에서 인덱스(색인)이란 무엇인가요?**

---

- 인덱스(Index)는 데이터베이스 테이블에서 특정 데이터를 신속하게 검색하기 위해 사용하는 데이터 구조이다. 이를 책의 목차에 비유할 수 있다.

### **역할**

---

- 인덱스는 데이터 읽기 속도를 높이기 위해 설계된 기능으로, 데이터가 정렬된 상태로 저장된다. 이로 인해 저장 성능이 약간 희생되지만, 검색 속도가 현저히 향상된다.
- 특히, 양이 많은 테이블에서 특정 데이터를 검색할 때 전체 테이블을 스캔하지 않고도 빠르게 데이터를 찾을 수 있다.

### **종류**

---

1. **B+-Tree 인덱스**
    - **정의**: 원래의 값을 이용하여 인덱싱을 수행한다.
    - **특징**: 대부분의 관계형 데이터베이스에서 널리 사용되며, 정렬된 데이터 구조를 유지하여 검색 성능을 최적화한다.
2. **Hash 인덱스**
    - **정의**: 컬럼 값으로 해시 값을 계산하여 인덱싱을 수행한다.
    - **특징**: 메모리 기반 데이터베이스에서 많이 사용되며, 특정 값의 검색에 매우 효율적이다.
    - **비교**: B+-Tree 인덱스가 범위 검색 및 정렬된 데이터 검색에 더 우수하다.
    

### **생성 시 고려해야 할 점**

---

1. **데이터 조회 비율**
    - 테이블 전체 로우 수의 15% 이하 데이터를 조회할 때 인덱스를 생성하는 것이 효과적이다.
2. **테이블 크기**
    - 테이블의 레코드 수가 적다면 인덱스를 생성하지 않는 것이 좋다. 이 경우 전체 테이블 스캔이 더 빠를 수 있다.
3. **자주 사용하는 컬럼**
    - 검색 빈도가 높은 컬럼을 인덱스로 지정하는 것이 효율적이다.
4. **DML 작업**
    - **`INSERT`**, **`UPDATE`**, **`DELETE`**와 같은 DML 작업이 많은 테이블은 인덱스 생성 시 신중해야 한다. DML 작업 시 인덱스에도 수정 작업이 동시에 발생하여 성능이 저하될 수 있다.

### **인덱스의 장단점**

---

- **장점**: 검색 성능 향상, 특정 데이터에 대한 빠른 접근.
- **단점**: 인덱스를 유지하기 위한 추가 저장 공간 필요, DML 작업 시 성능 저하.
- 인덱스는 데이터베이스 성능을 최적화하는 중요한 요소이지만, 모든 경우에 인덱스를 사용하는 것이 바람직한 것은 아니다. 테이블의 크기, 사용 빈도, DML 작업의 빈도 등을 종합적으로 고려하여 인덱스를 설계하고 관리하는 것이 중요하다.