# 配置
- .gitlab-ci.yml（project 根目录）
```

- ls

//部署代码（注意目标路径的权限）
- rsync -avz ActiveRecord /usr/lib/php/pear/
- phpunit --configuration phpunit.xml

```
