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

Please enter the gitlab-ci coordinator URL (e.g. https://gitlab.com/):
https://gitlab.chenliujin.com/
Please enter the gitlab-ci token for this runner: # https://gitlab.chenliujin.com/admin/runners
xxxxxx
Please enter the gitlab-ci description for this runner:
[f914ea57a101]: donald
Please enter the gitlab-ci tags for this runner (comma separated):
donald
Whether to run untagged builds [true/false]:
[false]: true
Registering runner... succeeded                     runner=B_KAXHWX
Please enter the executor: parallels, ssh, docker-ssh+machine, kubernetes, docker, docker-ssh, shell, virtualbox, docker+machine:
docker
Please enter the default Docker image (e.g. ruby:2.1):
docker:latest
Runner registered successfully. Feel free to start it, but if it's running already the config should be automatically reloaded!
```

/etc/gitlab-runner/config.toml

```
concurrent = 1
check_interval = 0

[[runners]]
  name = "docker"
  url = "https://github.com/"
  token = "72b154cb8000f90921e16712a213da91"
  executor = "docker"
  [runners.docker]
    tls_verify = false
    image = "docker:latest"
    privileged = true
    pull_policy = "if-not-present"
    disable_cache = false
    volumes = ["/cache", "/var/run/docker.sock:/var/run/docker.sock"]
  [runners.cache]
```













# [GitLab Runner](https://docs.gitlab.com/runner/)


- [Run GitLab Runner on a Kubernetes cluster](https://docs.gitlab.com/runner/install/kubernetes.html)
- [Run GitLab Runner in a container](https://docs.gitlab.com/runner/install/docker.html)





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
