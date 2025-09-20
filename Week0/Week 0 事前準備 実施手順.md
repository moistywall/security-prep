# Docker をインストール

以下の URL の Docker のドキュメント内の「Windows に Docker Desktop をインストール」に従って Docker をインストールする。
[Windows に Docker Desktop をインストール](https://docs.docker.jp/desktop/install/windows-install.html#id4)

以下のコマンドで正常にバージョン情報が表示されればインストール完了。
```
docker --version
```

# VirtualBox をインストール

1. 以下の URL から Virtual Box の公式サイトに行く
2. Windows Hosts 向けの Virtual Box のインストーラをダウンロードする
3. インストーラを起動して、Virtual Box をインストールする
# Kali Linux 環境の導入

## Kali Linux を入手する

以下のサイトから Kali Linux を入手する。
いくつか種類があるが、Virtual Machines と書いてあるものを選択すればよい。
https://www.kali.org/get-kali/#kali-platforms

## VirtualBox に Kali Linux をインポートする

1. VirutalBox を起動する
2. 起動後にインポートボタンを押す
3. ダウンロードした ova ファイルを選択する ( ファイル名例は右のようになっている、年月などの数字はダウンロード時期で変わる kali-linux-2022.2-virtualbox-amd64.ova )
4. 設定変更は特に不要でインポートボタンを押す
5. ライセンス同意する
6. インポート完了

## Kali Linux 起動、ログイン

Virutal Box の画面から、Kali Linux を選択して「起動」ボタンを押す。
ログイン ID やパスワードは「 Kali / Kali 」のはずだが変更の可能性もあるため以下の初期認証情報から確認する。
[https://www.kali.org/docs/introduction/default-credentials/](https://www.kali.org/docs/introduction/default-credentials/)
# JuiceShop

Host マシン（Windows 側）での実施作業。
以下のコマンドを実行して juice shop の container を pull し、環境を起動する。
```
docker pull bkimminich/juice-shop
docker run --rm -p 3000:3000 bkimminich/juice-shop
```

ここまでで、JuiceShop 動作環境の作成と起動は完了である。
以下、正常に起動できているか確認する。

Host 側で以下のコマンドを実行し IP アドレスを確認する。
```
ipconfig
```
※ 以降上記で確認した IP アドレスを < Host IP > とする。

Kali Linux 側の Firefox を起動して以下の URL を入力する(< Host IP > は ipconfig で調べた内容で置き換える)。
```
< Host IP >:3000
```

ブラウザに以下のような画面が表示されれば OK
![[Pasted image 20250920100618.png]]

# DVWA (Damn Vulnerable Web Application)

Host マシン（Windows 側）での実施作業。
以下のコマンドを実行して DVWA の container を pull し、環境を起動する。
```
docker pull infoslack/dvwa
docker run --rm -p 3001:80 bkimminich/juice-shop
```

ここまでで、DVWA 動作環境の作成と起動は完了。
以下、正常に起動できているか確認する。

Kali Linux 側の Firefox を起動して以下の URL を入力する(< Host IP > は JuiceShop の ipconfig の手順で調べた内容で置き換える)。
```
< Host IP >:3001
```

ブラウザに以下のような画面が表示されれば OK
![[Pasted image 20250920103447.png]]

# GitHubリポジトリ作成してメモ用READMEを用意

# 起動した環境の停止方法

## Docker コンテナの停止

以下のコマンドを実行して、 JuiceShop と DVWA の CONTAINER ID を確認する。
```
docker ps
```

2つの CNTAINER ID に対して、以下のコマンドを実行する(< CONTAINER ID > には直前で確認した CONTANER ID を入れる)。
```
docker stop < CONTAINER ID >
```
## Kali Linux の停止

右上の電源ボタン（もしくは、電源ボタンに似たマーク）をクリックすると LOG OUT メニューが表示されるので、ShutDown を選択してシャットダウンする。
# 参考 URL

- [Docker Docs](https://docs.docker.com/)
- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)
- [DVWA](https://github.com/digininja/DVWA)
- [VirtualBox](https://www.virtualbox.org/)
- [Kali Linux](https://www.kali.org/)
- [What is Kali Linux & Kali's features](https://www.kali.org/docs/introduction/)
