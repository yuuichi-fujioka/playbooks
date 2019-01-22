# All In One K8s on ubuntu 16.04 をAnsible Pullでインストールするためのもの

## 事前に必要なあれこれ

* ansibleをインストールしておく
* インベントリーを用意しておく
* Ansibleが使うその他必要なもののインストール

### Ansibleのインストール

好きにして

### インベントリー

* /etc/ansible/hosts

```ini
<ホスト名> ansible_connection=local
```

例:

```ini
fujioka-k8s-server ansible_connection=local
```

* /etc/ansible/host_vars/<ホスト名>/kubernetes.yml

```yaml
dplane_address: <APIが受け付けるIPアドレス>
k8s_api: <LBが受け付けるドメイン名>
```

例:

```yaml
dplane_address: 192.168.0.99
k8s_api: k8s.example.com
```

### その他諸々インストール

* pip
* docker

```
sudo apt install pip
```

```
curl https://get.docker.com  |sh
```

## 使い方

```
ansible-pull -U  git@github.com:yuuichi-fujioka/playbooks.git k8s/install_all_in_one.yml
```
