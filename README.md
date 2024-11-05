**(참조) Storage 서비스 개발에 활용되는 AWS 서비스들**

(면접관) 스토리지에 어떤 유형들이 있는지 설명해줄 수 있나요? 이력서에 기술된 프로젝트 진행 시 경험했던 AWS 스토리지 서비스들에 대해서도 아는 바가 있다면 설명을 부탁해요!

| **접근 방식** | **서비스 이름** | **주요 특징** | **일반적 사용 사례** |
| --- | --- | --- | --- |
| **Block Storage** | **EBS** (Elastic Block Store) | - EC2 인스턴스에 직접 연결 <br> - 고성능, 낮은 지연시간 <br> - 단일 AZ에서만 사용 가능 | - 데이터베이스 <br> - 부팅 볼륨 <br> - Raw 디바이스 접근 필요 시 |
|  | **Instance Store** | - EC2에 물리적으로 연결된 임시 스토리지 <br> - 인스턴스 중지/종료 시 데이터 삭제 <br> - 매우 높은 I/O 성능 | - 임시 데이터 <br> - 캐시 <br> - 스크래치 데이터 |
| **Object Storage** | **S3** (Simple Storage Service) | - 무제한 확장성 <br> - 높은 내구성 <br> - 버전 관리 지원 <br> - 정적 웹 호스팅 가능 | - 정적 웹 콘텐츠 <br> - 백업/아카이브 <br> - 데이터 레이크 |
| **File System** | **EFS** (Elastic File System) | - 완전 관리형 NFS <br> - 다중 AZ 지원 <br> - 자동 확장/축소 | - 웹 서빙 <br> - 콘텐츠 관리 <br> - 데이터 공유 |
|  | **FSx for Windows** | - Windows 파일 서버 <br> - SMB 프로토콜 지원 <br> - Active Directory 통합 | - Windows 워크로드 <br> - 홈 디렉토리 <br> - 비즈니스 애플리케이션 |
|  | **FSx for Lustre** | - 고성능 병렬 파일 시스템 <br> - S3와 통합 <br> - 높은 처리량 | - HPC <br> - 기계 학습 <br> - 빅데이터 처리 |
| **Backup** | **AWS Backup** | - 중앙 집중식 백업 관리 <br> - 다중 서비스 지원 <br> - 자동화된 백업 정책 | - 규정 준수 백업 <br> - 재해 복구 <br> - 중앙화된 백업 관리 |
|  | **S3 Cross-Region Replication** | - 자동 복제 <br> - 지역 간 데이터 복제 <br> - 지연 시간 최소화 | - 재해 복구 <br> - 규정 준수 <br> - 지역 간 데이터 접근 |
|  | **EBS Snapshots** | - 증분 백업 <br> - S3에 저장 <br> - 지역 간 복사 가능 | - 볼륨 백업 <br> - 데이터 복구 <br> - 볼륨 마이그레이션 |
|  | **S3 Glacier** | - 장기 보관용 저비용 스토리지 <br> - 다양한 검색 옵션 <br> - 높은 내구성 | - 장기 데이터 보관 <br> - 규정 준수 아카이브 <br> - 백업 데이터 |

### 추가 고려사항:

1. **비용 관점**
   - S3: 접근 빈도에 따른 다양한 스토리지 클래스
   - EBS: 프로비저닝된 용량에 대한 지불
   - EFS: 사용한 만큼만 지불

2. **성능 관점**
   - Block: 가장 높은 I/O 성능
   - Object: 높은 처리량, 높은 지연시간
   - File: 중간 수준의 성능

3. **확장성 관점**
   - S3: 무제한 확장
   - EBS: 볼륨 단위로 제한
   - EFS: 자동 확장/축소

4. **가용성 관점**
   - S3: 99.99% 가용성
   - EBS: 단일 AZ
   - EFS: 다중 AZ
