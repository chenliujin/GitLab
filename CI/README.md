# CI 介绍 

持续集成（Continuous Integration，简称CI）指的是，频繁地（一天多次）将代码集成到主干。

完成一些自动化工作：

- 自动化构建：编译，打包 
- 自动化测试：单元测试
- 自动化部署

## Docker

- 根据 Dockerfile 构建 image
- 在 docker 上跑单元测试 
- 测试通过后推送到镜像仓库

### 单元测试 `.gitlab-ci.yml`

```
image: docker:latest

stages:
  - build
  - test

build:
  stage: build
  script:
    - docker build -t <project>:tests -f Dockerfile.tests . 
  tags:
    - docker

test:
  stage: test
  script:
    - docker run -i --rm <project>:tests phpunit --configuration /opt/<project>/tests/phpunit.xml
  tags:
    - docker
```

# yml

- stages
- jobs

```
stages:
  - build
  - test
  - deploy
```
