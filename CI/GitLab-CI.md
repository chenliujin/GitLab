# gitlab-runner

## executor
- docker-ssh
- parallels
- shell
- ssh
- docker-ssh+machine
- docker
- virtualbox
- docker+machine
- kubernetes

## 安装 gitlab-runner

版本：

- gitlab/gitlab-runner:latest
- gitlab-ce-8.15.2 使用版本 gitlab/gitlab-runner:v1.11.4 

```
docker run \
  -d \
  --name=gitlab-runner \
  --restart=always \
  --privileged=true \
  -v /etc/gitlab-runner:/etc/gitlab-runner \
  -v /var/run/docker.sock:/var/run/docker.sock \
  gitlab/gitlab-runner:v1.11.4
```

## 注册 gitlab-runner

```
gitlab-ci-multi-runner register
```













# [GitLab Runner](https://docs.gitlab.com/runner/)


- [Run GitLab Runner on a Kubernetes cluster](https://docs.gitlab.com/runner/install/kubernetes.html)
- [Run GitLab Runner in a container](https://docs.gitlab.com/runner/install/docker.html)


/etc/gitlab-runner/config.toml

```
concurrent = 1
check_interval = 0

[[runners]]
  name = "docker"
  url = "https://g5.iot-sw.net/"
  token = "71eadc4c9938f288d9a5ad7f49f47e"
  executor = "docker"
  [runners.docker]
    tls_verify = false
    image = "docker:latest"
    privileged = true
    pull_policy = "if-not-present"
    disable_cache = false
    volumes = ["/cache", "/usr/bin/docker:/usr/bin/docker", "/var/run/docker.sock:/var/run/docker.sock"]
  [runners.cache]
```




---

# 配置

`.gitlab-ci.yml`

# [The Docker executor](https://docs.gitlab.com/runner/executors/docker.html) 


## 私有镜像仓库

- https://docs.gitlab.com/ce/ci/docker/using_docker_images.html#define-an-image-from-a-private-docker-registry

- project > setting > Variables

登陆私有仓库后设置 

Key: DOCKER_AUTH_CONFIG 

Value: .docker/config.json


---

# 参考文献

- https://scarletsky.github.io/2016/07/29/use-gitlab-ci-for-continuous-integration/
- https://segmentfault.com/a/1190000012279248
