# [GitLab Runner](https://docs.gitlab.com/runner/)

## 版本
- gitlab-ce-8.15.2 > gitlab/gitlab-runner:v1.11.4 


- [Run GitLab Runner on a Kubernetes cluster](https://docs.gitlab.com/runner/install/kubernetes.html)
- [Run GitLab Runner in a container](https://docs.gitlab.com/runner/install/docker.html)

```
gitlab-ci-multi-runner register



```

# executor
- docker-ssh
- parallels
- shell
- ssh
- docker-ssh+machine
- docker
- virtualbox
- docker+machine
- kubernetes



phpunit

- 安装 phpunit

```
curl http://phar.phpunit.cn/phpunit-5.7.phar > phpunit-5.7.phar
chmod +x phpunit-5.7.phar
mv phpunit-5.7.phar /usr/local/bin/phpunit
```

```
composer require phpunit/phpunit
```


- 根据 Dockerfile 构建 image
- phpunit

```
docker run -it --rm test phpunit --version
```

- 测试通过后推送到镜像仓库



- 执行测试
- 构建 docker image

yum install -y composer


---

# 配置
- `.gitlab-ci.yml`

```
- ls

//部署代码（注意目标路径的权限）
- rsync -avz ActiveRecord /usr/lib/php/pear/
- phpunit --configuration phpunit.xml
```

# [The Docker executor](https://docs.gitlab.com/runner/executors/docker.html) 


```
image: php:5.6

test:
 script:
 - phpunit --configuration phpunit.xml 
```

## 私有镜像仓库

- https://docs.gitlab.com/ce/ci/docker/using_docker_images.html#define-an-image-from-a-private-docker-registry

- project > setting > Variables

登陆私有仓库后设置 

Key: DOCKER_AUTH_CONFIG 

Value: .docker/config.json


---

# 参考文献

- https://scarletsky.github.io/2016/07/29/use-gitlab-ci-for-continuous-integration/
