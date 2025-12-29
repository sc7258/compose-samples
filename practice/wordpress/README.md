## 실습: 워드프레스를 도커 컴포즈로 실행하기
### Wordpress 컨테이너
|  설정  |  설명  |
|---|---|
| 이미지 | wordpress |
| Listening Port | 80 |
| WORDPRESS_DB_HOST 환경변수 | 디비 주소 (db:3306) |
| WORDPRESS_DB_USER 환경변수 | 디비 사용자 (wp) |
| WORDPRESS_DB_PASSWORD 환경변수 | 디비 패스워드 (wp) |
| WORDPRESS_DB_NAME 환경변수 | 디비 이름 (wp) |

### MySQL 컨테이너
|  설정  |  설명  |
|---|---|
| 이미지 | mysql:5.7 |
| Listening Port | 3306 |
| MYSQL_ROOT_PASSWORD 환경변수 | 디비 root 비밀번호 |
| MYSQL_DATABASE 환경변수 | 디비 데이터베이스 (wp) |
| MYSQL_USER 환경변수 | 디비 사용자 (wp) |
| MYSQL_PASSWORD 환경변수 | 디비 패스워드 (wp) |
| 디비 데이터 저장 디렉토리 | /var/lib/mysql |