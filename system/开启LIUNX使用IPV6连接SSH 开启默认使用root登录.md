### 使IPV6生效

执行命令打开`/etc/ssh/`文件夹下的`sshd_config`文件。

```shell
vim /etc/ssh/sshd_config
```

按`{i}`换至编辑模式，将`#AddressFamily any`前的#（注释）删除，更改完成后按`{ESC}`输入`:wq`保存并退出。

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668864030-image-1668864028933.png?x-oss-process=style%2Ffull)

执行`systemctl reload sshd`命令重新加载配置。

执行`netstat -tupln`查看sshd在IPV6侧是否正常运行。

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668864413-image-1668864411262.png?x-oss-process=style%2Ffull)

### 使用密码登录root

将`#PermitRootLogin`前的#（注释）删除，并将后面的`prohibit-password`更改为`yes`，更改完成后按`{ESC}`输入`:wq`保存并退出，执行`service sshd restart`重启sshd服务。

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668865663-image-1668865662157.png?x-oss-process=style%2Ffull)