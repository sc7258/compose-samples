프론트엔드와 백엔드, 데이터베이스까지 한꺼번에 도커 컴포즈로 실행해봅니다.

### 실습 1. Flask(python) + Redis 웹 서비스 실행하기
다음의 컨테이너 실행 조건과 파일 내용을 바탕으로 flask 앱을 빌드하고 도커 컴포즈로 컨테이너를 실행해봅니다.

**flask 컨테이너**

|  설정  |  설명  |
|---|---|
| 연결할 포트 | 5000 |
| redis 호스트 이름 | redis |

**redis 컨테이너**

|  설정  |  설명  |
|---|---|
| 이미지 | redis |

**app.py**

```python
import time

import redis
from flask import Flask

app = Flask(__name__)
cache = redis.Redis(host='redis', port=6379)


def get_hit_count():
    retries = 5
    while True:
        try:
            return cache.incr('hits')
        except redis.exceptions.ConnectionError as exc:
            if retries == 0:
                raise exc
            retries -= 1
            time.sleep(0.5)


@app.route('/')
def hello():
    count = get_hit_count()
    return 'Hello World! I have been seen {} times.\n'.format(count)
```

**requirements.txt**

```txt
flask
redis
```

**Dockerfile**

```dockerfile
FROM python:3.7-alpine
WORKDIR /code
ENV FLASK_APP app.py
ENV FLASK_RUN_HOST 0.0.0.0
RUN apk add --no-cache gcc musl-dev linux-headers
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
COPY . .
CMD ["flask", "run"]
```