# proxy

$ vim /etc/gitlab/gitlab.rb

```
external_url 'http://www.chenliujin.com/gitlab'
```

```
$ gitlab-ctl reconfigure
$ gitlab-ctl restart
```

## nginx

```
server {
  listen 80;
  server_name www.chenliujin.com;
  location /gitlab {
    client_max_body_size 1024m; # 设置最大允许上传单个的文件大小
    proxy_redirect off;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_pass http://127.0.0.1:8080/gitlab;
    index index.html index.htm;
  }
}
```

# https

```
external_url 'https://gitlab.example.com'
nginx['redirect_http_to_https'] = true
nginx['ssl_certificate'] = "/etc/gitlab/ssl/gitlab.crt"
nginx['ssl_certificate_key'] = "/etc/gitlab/ssl/gitlab.key"
```

## nginx

```
    proxy_pass https://127.0.0.1:10443;
```

---





# 备份
```
$ gitlab-rake gitlab:backup:create
$ cd /var/opt/gitlab/backups
```

---

# 还原

- 先运行原来版本的 gitlab
- 将备份文件拷贝到备份路径：/var/opt/gitlab/backups/，修改权限 `chmod 777 xxx_gitlab_backup.rar`
- 运行起来后在容器里面还原

```
$ gitlab-rake gitlab:backup:restore BACKUP=1526912928_2018_05_21
```

---

# 升级

- 下载最新的 gitlab image
- docker run
- 重新配置

```
$ /opt/gitlab/bin/gitlab-ctl reconfigure
$ /opt/gitlab/bin/gitlab-ctl restart
```

- https://gitlab.com/gitlab-org/gitlab-ce/blob/master/doc/update/8.4-to-8.5.md

---

# 中文 

```
docker pull twang2218/gitlab-ce-zh:latest
```

---


# branch
- master
- 除 master 外的 branch

## 1. 查看分支

### 查看本地所属分支
```
$ git branch --list
```

### 查看远程分支
```
$ git branch --list -r
```


## 2. 分支创建

```
$ git branch testing 
```

or 

```
$ git checkout -b testing master
```


## 3. 分支切换/选择
```
$ git checkout testing
```

## 4. 分支提交

```
$ git push origin testing
```



## 5. 分支的合并（merge）
1. 选择要合并到的 branch，如 master
1. 合并指定的 branch，如 testing 

把 testing branch 的代码合并回 master:
```
$ git checkout master
$ git merge --no-ff testing 
```

## 6. 删除远程分支

```
$ git push --delete origin testing
```

## 已经被删除

```
rm -f .git/refs/remotes/origin/testing
```

## 7. bug fix
- issue -> New branch
- Create Merge Request



---

# tag

## 1. 版本号

## 2. 打标签
```
$ git tag -a 1.0.0 -m 'v1.0.0'
$ git show 1.0.0
$ git push origin 1.0.0
```

## 3. 获取指定 tag 的代码
```
$ git checkout 1.0.0
```

## 4. 删除 Tag

### 删除远程 tag

```
$ git push --delete origin 1.0.0
```

### 删除本地 Tag

```
$ git push --delete 1.0.0
```

## 5. 重命名 Tag

```
$ git tag 1.0.0-beta.0 1.0.0-alpha.0
$ git tag --delete 1.0.0-alpha.0
```


---

# 回滚

```
$ git checkout master
$ git merge --no-ff develop
$ git reset --hard //回滚 merge 操作
```

---





## 历史版本（Changelog.txt）

```
# Release 1.0.0
Released: 2017-07-31

## Major change
广西南宁

## Features
- Fixed issue #100: xxx
- Fixed issue #101: xxx
- Update Nginx:1.12.1

## Bug fixes
- Fixed issue #200: xxx
- Fixed issue #201: xxx
```


# 参考文献
- [打标签](https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E6%89%93%E6%A0%87%E7%AD%BE) 
- [Git分支管理策略](http://www.ruanyifeng.com/blog/2012/07/git.html)
