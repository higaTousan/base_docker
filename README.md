# Mac の Docker 環境基本テンプレート

これはオレオレ Docker 環境テンプレートです。

- VirtualBox
- Vagrant
- Mutagen

# Features

`vagrant up` で VirtualBox 上の Ubuntu に Docker 環境が立ち上がります。

# Requirement

* VirtualBox
* Vagrant
* Mutagen

# Installation

## 1. cask のインストール
Mac の GUI アプリをコマンドでもインストールできるようにするヤツです。
```bash
brew cask
```
## 2. VirtualBox のインストール
```bash
brew cask install virtualbox
```
## 3. Vagrant のインストール
```bash
brew cask install vagrant
```
## 4. Vagrant Plugin のインストール
```bash
vagrant plugin install vagrant-disksize vagrant-hostsupdater vagrant-mutagen vagrant-docker-compose
```
## 5. Mutagen のインストール
ファイル同期を簡単に行うツールです。VM と mac の間でファイルを同期するために利用します。
```bash
brew install mutagen-io/mutagen/mutagen
```
## 6. Vagrant Box のダウンロード
ubuntu のイメージをダウンロードします。
```bash
vagrant box add ubuntu/xenial64
```

# Usage
## リポジトリをクローンする
```bash
git clone git@github.com:higaTousan/base_docker.git
cd base_docker
```
## vagrant を起動する
```bash
vagrant up
```
## vagrant 起動後、ssh します
```bash
vagrant ssh
```
## アプリケーションディレクトリへ移動
ローカル PC の app ディレクトリが VM の app ディレクトリと同期しています
```bash
cd app
```
## Docker コマンドを実行
`docker-compose up` で docker が起動します
```bash
docker-compose up
```
### Docker を停止する
vagrant ssh して、アプリケーションディレクトリで `docker halt` を実行する
```bash
docker halt
```

## 参考にしたドキュメント
▼ Vagrantを使う「Mac最速のDocker環境」を初心者向けに解説【遅いMac for Dockerを卒業】
https://qiita.com/necocoa/items/bd62ed3dba14b17552f2

▼ DXを大幅に低下させるDocker for Macを捨ててMac最速のDocker環境を手に入れる
https://qiita.com/yuki_ycino/items/cb21cf91a39ddd61f484

# Note

