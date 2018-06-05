# CI 介绍 

持续集成

完成一些自动化工作：
- 打包
- 单元测试
- 部署


## 单元测试

```
image: docker:1.13.1

test:
  script:
    - cd ..
    - docker build -t tests -f <project>/Dockerfile.tests . 
    - docker run -i --rm tests phpunit /opt/<project>/tests/test.xml
```

