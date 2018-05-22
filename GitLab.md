

# ssh
```
$ vim /etc/gitlab/gitlab.rb
gitlab_rails['gitlab_shell_ssh_port'] = 10022
$ gitlab-ctl reconfigure
```

# 邮件通知
## 阿里邮箱（企业版）
```
$ vim /etc/gitlab/gitlab.rb
gitlab_rails['gitlab_email_from'] = 'liujin.chen@qq.com'
gitlab_rails['smtp_enable'] = true
gitlab_rails['smtp_address'] = "smtp.mxhichina.com"
gitlab_rails['smtp_port'] = 25
gitlab_rails['smtp_user_name'] = "liujin.chen@qq.com"
gitlab_rails['smtp_password'] = "123456"
gitlab_rails['smtp_domain'] = "smtp.mxhichina.com"
gitlab_rails['smtp_authentication'] = "plain"
gitlab_rails['smtp_enable_starttls_auto'] = true
$ gitlab-ctl reconfigure
```

# 参考文献
- [使用docker运行gitlab服务](http://blog.csdn.net/felix_yujing/article/details/52139070)
- [Installing GitLab on Kubernetes](http://docs.gitlab.com/ce/install/kubernetes/)
