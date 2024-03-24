# Redis(Remote Dictionary Server)
- key-value 구조의 비정형 데이터를 저장하고 관리하기 위한 오픈 소스 기반의 DBMS

In-Memory         모든 데이터를 RAM에 저장
single Threaded   단일 thread에서 모든 task 처리 (성능 이점, side effect 낮음)
Cluster Mode      다중 노드에 데이터를 분산 저장하여 안정성, 고가용성 제공
Persistence       Redis는 주로 캐시로 사용되지만 영속성 옵션 제공(SSD 와같은 영구 저장 장치에 데이터 저장)
                  RDB(스냅샷 일부 데이터 유실 위험 및 스냅샷 생성 중 클라이언트 요청 지연 발생) + AOF(모든 write 작업을 모두 log 로 저장 데이터 유실 위험 낮음, 재난 복구 시 write 작업을 다시 적용하기 때문에 RDB 보다 느림)
                  통해 영속성 옵션 제공(휘발성 데이터를 저장하지만 영속적으로 관리 가능)
Pub/Sub

장점
- 모든 데이터를 메모리에 저장하기 때문에 매우 빠른 읽기/쓰기 속도 보장
- Redis Data type 지원

Caching, Rate Limiter(API 호출제한등..), Message Broker(메세지 큐) ....

cache hit:  cache가 존재하여 정상 데이터 return
cache miss: cache가 존재하지 않아 return 된 데이터가 없음

<b>Cache-Aside pattern</b>
- 캐시를 사용 하는 가장 흔한 패턴으로 먼저 캐시를 조회하여 cache hit면 cache사용하여 조회 cache miss면 원본 데이터 조회
