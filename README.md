# establish-a-mirror-vault
```
chmod 700 /root/zhmirror/keyring
export GNUPGHOME=/root/zhmirror/keyring

gpg --no-default-keyring \
  --keyring /root/zhmirror/keyring/trustedkeys.gpg \
  --import /usr/share/keyrings/ubuntu-archive-keyring.gpg

