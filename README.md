# mymoji-devops

## 需要先安裝 Ansible

```
$ pip install ansible
```

## SSH Login To GCE

### Create SSH Key

為了方便等一下登入 GCE，請先建立好你的 SSH key，可以參考以下指令來建立：

```
$ ssh-keygen -t rsa -f ~/.ssh/[KEY_FILENAME] -C [USERNAME]
$ chmod 400 ~/.ssh/[KEY_FILENAME]
```

可以到目錄 ~/.ssh 下查 ssh key，會有一個公鑰（public key）和私鑰（private key），檔案名稱分別是：

- 公鑰：[KEY_FILENAME].pub
- 私鑰：[KEY_FILENAME]

接著要透過 ssh 遠端登入到 GCE，在這之前有請你先建立了 ssh key，請到  `~/.ssh`  目錄下找到你剛剛建立的 ssh key 並將 public key 的內容複製下來

接著到 GCP 的 web console，並找到  **Compute Engine**  下的**中繼資料**，按下「新增 SSH 金鑰」：

![https://jiepeng.me/static/essays/2020/04/14/gcp-04.png](https://jiepeng.me/static/essays/2020/04/14/gcp-04.png)

將剛剛複製的 public key 貼上：

![https://jiepeng.me/static/essays/2020/04/14/gcp-05.png](https://jiepeng.me/static/essays/2020/04/14/gcp-05.png)

這樣就完成新增了，接下來透過 ssh 的方式來登入，`KEY_FILENAME`  就是你私鑰的名稱，`username`  則是使用者名稱，`severIP`  則是 GCE 公開的 IP：

```
$ ssh -i ~/.ssh/[KEY_FILENAME] [username]@[serverIP]
```
