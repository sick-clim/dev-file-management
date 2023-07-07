
```bash
multipass launch --name dev --cpus 2 --memory 2G --disk 20G --cloud-init cloud-init.yml

multipass ls
multipass shell dev

multipass delete vm
multipass purge
```

cloud-init.yml に ssh 公開鍵を追加
```yaml
ssh_authorized_keys:
  - {{公開鍵}}
```

```bash
# ip 確認
multipass ls
ssh ubuntu@{{ip}}
```

ssh {{name}} で接続できるよう設定
cloud-init.yml で avahi-daemon をインストール

```
ssh ubuntu@{{name}}.local

# ssh/config に設定追加
Host dev
    HostName dev.local
    User ubuntu
```

mount 設定
```bash
# HOME 配下にある sandbox をマウントする
multipass mount ~/sandbox {{name}}:~/sandbox

# 確認
multipass info {{name}}

# 解除
multipass umount {{name}}
```

