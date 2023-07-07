
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
