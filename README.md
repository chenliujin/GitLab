
# 升级
- https://gitlab.com/gitlab-org/gitlab-ce/blob/master/doc/update/8.4-to-8.5.md




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
