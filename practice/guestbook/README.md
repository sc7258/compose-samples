### 실습 2: 방명록 서비스 실행하기
다음과 같은 구성으로 docker-compose.yml 파일을 작성해보세요.


**프론트엔드**
| 정보  |  내용  |
|---|---|
| 이미지 | subicura/guestbook-frontend:latest |
| PORT 환경변수 | 서비스를 실행할 포트 |
| GUESTBOOK_API_ADDR 환경변수 | Backend 서버 주소 ex) backend:8000 |

**백엔드**
| 정보  |  내용  |
|---|---|
| 이미지 | subicura/guestbook-backend:latest |
| PORT 환경변수 | 서비스를 실행할 포트 |
| GUESTBOOK_DB_ADDR 환경변수 | DB 서버 주소 ex) mongodb:27017 |

**데이터베이스**
| 정보  |  내용  |
|---|---|
| 이미지 | mongo:4 |
| Listening Port | 27017 |
| 볼륨 설정 | /data/db |