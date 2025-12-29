### docker run 명령어로 nginx 서버실행
| 정보  |  내용  |
|---|---|
| 이미지 | nginx:latest |
| Listening Port | 80 |
| HTML 경로 | /usr/share/nginx/html |

* 호스트의 60080 포트를 컨테이너의 80 포트로 연결하세요.
* index.html 파일을 만들고, NGINX 접속시 이 파일이 나타나게 해보세요.

```shell
docker run -it -p 60080:80 -v $(pwd):/usr/share/nginx/html/ nginx
```
