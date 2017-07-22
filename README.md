

# 版本号


# 分支

- 主分支：Master

## 创建开发分支 Develop
```
$ git checkout -b develop master 
$ git push origin develop

# 切换分支
$ git checkout develop
$ git push origin develop

```



- 功能分支：Feature
开发测试完成后，合并回 Develop 和 Master，Master 打 Tag，则此 feature 有独立的 tag，可以单独发布。

- 预发布分支
 - release-0.1

- 修补 bug 分支
 - fixbug-0.1

- Tag
 - tag-0.1


# 参考文献
- [Git分支管理策略](http://www.ruanyifeng.com/blog/2012/07/git.html)
