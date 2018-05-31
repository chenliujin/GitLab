# [GitLab Runner](https://docs.gitlab.com/runner/)

- [Run GitLab Runner on a Kubernetes cluster](https://docs.gitlab.com/runner/install/kubernetes.html)
- [Run GitLab Runner in a container](https://docs.gitlab.com/runner/install/docker.html)

---

# 配置
- `.gitlab-ci.yml`

```
- ls

//部署代码（注意目标路径的权限）
- rsync -avz ActiveRecord /usr/lib/php/pear/
- phpunit --configuration phpunit.xml
```

# Docker executor

```
image: php:5.6

test:
 script:
 - phpunit --configuration phpunit.xml 
```

# 参考文献

- https://scarletsky.github.io/2016/07/29/use-gitlab-ci-for-continuous-integration/
