# establish-a-mirror-vault
```
chmod 700 ~/zhmirror/keyring
export GNUPGHOME=~/zhmirror/keyring

gpg --no-default-keyring \
  --keyring ~/zhmirror/keyring/trustedkeys.gpg \
  --import /usr/share/keyrings/ubuntu-archive-keyring.gpg

```
用以下命令确定密钥确实导入成功了
```
gpg --no-default-keyring \
    --keyring ~/zhmirror/keyring/trustedkeys.gpg \
    --list-keys
```


# Remote access to the office server
```
ssh-keygen -t rsa -b 4096 -C "我的邮箱@example.com"   # 生成公钥和私钥，接着把公钥拿给上级
ssh -p 端口 用户名@域名   # 在vscode里打开ssh
ssh 用户名@内网ip   # 接着输入密码就行
```

# sync ubuntu
```
mkdir -p "$HOME/zhmirror"/{repos,logs}
mkdir -p "$HOME/zhmirror/repos"/{ubuntu,ubuntu-ports}
```

```
debmirror \
  --method=rsync \
  --host="rsync.mirrors.ustc.edu.cn" \
  --root="ubuntu" \
  --dist="noble,noble-updates,noble-security,noble-backports" \
  --section="main,restricted,universe,multiverse" \
  --arch="amd64" \
  --keyring="$HOME/zhmirror/keyring/trustedkeys.gpg" \
  --no-source \
  --progress \
  "$HOME/zhmirror/repos/ubuntu" \
  | tee "$HOME/zhmirror/logs/ubuntu-amd64-noble-$(date +%F_%H%M%S).log"
```

```
