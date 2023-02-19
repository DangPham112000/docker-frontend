```yml
language: generic
sudo: required
services:
  - docker
before_install:
  - docker build -t dangpham/docker-frontend -f Dockerfile.dev .
script:
  - docker run -e CI=true dangpham/docker-frontend npm run test
deploy:
  provider: elasticbeanstalk
  region: "ap-northeast-1"
  app: "docker-frontend"
  env: "Dockerfrontend-env"
  bucket_name: "elasticbeanstalk-ap-northeast-1-485654636061"
  bucket_path: "docker-frontend"
  on:
    branch: master

```