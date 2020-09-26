---
layout: snippet
title: Jekyll Docker Compose
catagory: Docker
filename: docker-compose.yml
tag: docker-compose.yml docker-compose docker jekyll blog
---

```yml
version: "3.8"

services:
  site:
    image: jekyll/jekyll
    command: jekyll serve
    volumes: 
      - .:/srv/jekyll
      - ./vendor/bundle:/usr/local/bundle
    ports:
      - 4000:4000
    environment:
      JEKYLL_ENV: development
```