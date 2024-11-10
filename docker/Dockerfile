# docker build --target base -t postsneakernet/web -f docker/Dockerfile .
# docker run -d --name postsneakernet-web -p 9000:9000 --env-file docker/web.env postsneakernet/web
# docker start postsneakernet-web
# docker stop postsneakernet-web
# docker rm postsneakernet-web
# docker exec -it postsneakernet-web bash

FROM python:3.12-bookworm as base

RUN apt update
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && apt-get install -y nodejs

WORKDIR /app

COPY ./web/requirements.txt ./web/requirements.txt
RUN pip install -r web/requirements.txt

COPY ./web ./web

WORKDIR /app/web

EXPOSE 9000
EXPOSE 9001
CMD ["sh", "run-dev.sh"]
