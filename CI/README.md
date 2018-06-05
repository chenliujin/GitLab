# CI 介绍 

持续集成

完成一些自动化工作：
- 打包
- 单元测试
- 部署

## Docker

- 根据 Dockerfile 构建 image
- 在 docker 上跑单元测试 
- 测试通过后推送到镜像仓库

### 单元测试

```
image: docker:1.13.1

test:
  script:
    - docker build -t <project>:tests -f Dockerfile.tests . 
    - docker run -i --rm <project>:tests phpunit --configuration /opt/<project>/tests/phpunit.xml
```

