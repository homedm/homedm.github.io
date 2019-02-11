---
layout: post
title: Debianをthinkpad x1 carbon 第一世代にインストールした。
---

# 概要
表題にあるようにthinkpad x1 carbonのOSなしを中古で購入したので、Debianをインストールした。

購入したthinkpadのスペックはメモリ8GB、SSD240GB, CPU I7 3667Uで、初めからLinuxの専用機として使おうと考えていた。

今回Debianを以下の理由で選んだ。

- Ubuntu、Cent OSはすでに触ったことがある
- 初期設定で苦労はしたくないが、Linuxの学習ができるぐらいは設定を弄びたい。
- 動きが早いこと
- 情報量が多いこと

# 手順
まず、以下のURLからdebian-9.6.0-amd64-DVD-1.isoをUSBに保存しました。

[Index of/debian-cd/current/amd64/iso-dvd](https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/)

大体の場合は上のisoイメージだけでインストールがうまくいくらしいのですが、thinkpad x1 carbon 第一世代にインストールしようとしたところiwlwifi関連のファームウェアがないと言われてしまったので、ここからfirmware.zgpをダウンロードした。展開した.debファイルを別のUSBのルートディレクトリに保存した。ルートディレクトリが汚れるのが嫌なら、新しくfirmwareディレクトリを作成しその直下においてもうまくいくはずである。また、上で用意したUSBのisoイメージの中にあるfirmwareディレクトリ下に展開しても良い。

このUSBをインストール時にPCに指しておくことで無線LANのファームウェアが読み込まれ無線LANの設定ができるようになる。

あとはここに書いてあるとおりにインストールを進めていけばインストールが完了する。

デスクトップ環境の選択では一度目はLXDEを選んだが、デザインがしっくり来なかったためGNOMEにしてインストールし直した。また、他はサーバー用途で使うわけではないのでweb server, print server, SSH serverのチェックは外し、standart system utilitiesのみチェックを入れた。

インストール後、すぐに日本語入力が使えた。ひとまずGit, golang, vim, nodejsを入れ最低限、開発に使える環境を整えた。

再起動後、なぜかパスワード認証が通らずいろいろ試し、何時間か悩んだ結果どうも起動直後にキーボードのレイアウトが正しく認識されておらず、Shift+7で&、Shift+4で#が入力されてしまうという状態だったため記号の部分で入力文字列と保存されたパスワードが合わなかったためだと判明した。
どうも英字配列として認識されているようだった。

ログイン後はキーボードレイアウトが正しく認識されたので、xwindowやgnomeのせいではないのでブート時の問題らしい。
[Keyboard - Debian Wiki](https://wiki.debian.org/Keyboard)を参考に試してみたが、解決できなかった。
