# establish-a-mirror-vault
```
chmod 700 /root/zhmirror/keyring
export GNUPGHOME=/root/zhmirror/keyring

gpg --no-default-keyring \
  --keyring /root/zhmirror/keyring/trustedkeys.gpg \
  --import /usr/share/keyrings/ubuntu-archive-keyring.gpg

```

# Remote access to the office server
```
ssh-keygen -t rsa -b 4096 -C "我的邮箱@example.com"   # 生成公钥和私钥，接着把公钥拿给上级
ssh -p 端口 用户名@域名   # 在vscode里打开ssh
ssh 用户名@内网ip   # 接着输入密码就行
```

