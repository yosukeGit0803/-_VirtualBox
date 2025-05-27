# オンプレ構成：VirtualBox上でのWeb/DNS/Mailサーバ構築

## 概要

このリポジトリは、VirtualBox上のUbuntuサーバにて構築した以下3種類のオンプレミスサービスの設定ファイル一式を保存したものです。

- Webサーバ（Nginx + PHP）
- DNSサーバ（Bind9）
- メールサーバ（Postfix + Dovecot）

全サービスが連携し、疎通確認が完了しています。

---

## 構成概要図

```
[Client PC]
    |
    | HTTP / DNS / SMTP / IMAP
    |
[VirtualBox上のUbuntu]
    ├── Nginx (Webサーバ)
    ├── Bind9 (DNSサーバ)
    └── Postfix + Dovecot (Mailサーバ)
```

---

## サーバ構成と確認内容

### Webサーバ（Nginx + PHP）
- `/etc/nginx/sites-available/default` による仮想ホスト設定
- `/var/www/html/index.php` によるPHP動作確認済み

### DNSサーバ（Bind9）
- `/etc/bind/named.conf.local`
- `/etc/bind/db.local` などのゾーンファイルを用意
- digによる名前解決確認済み

### メールサーバ（Postfix + Dovecot）
- `/etc/postfix/main.cf`
- `/etc/dovecot/conf.d/10-*.conf`
- `Thunderbird` にてIMAP/SMTP認証・送受信確認済み

---

## ディレクトリ構成

```
onprem-server-setup/
├── web/
│   ├── index.php
│   └── nginx.conf
├── dns/
│   ├── named.conf.local
│   ├── db.local 他ゾーンファイル
└── mail/
    ├── postfix/main.cf
    └── dovecot/10-*.conf
```

---

## 注意事項（GitHub公開にあたり）

- 本構成にはパスワードや秘密鍵は一切含まれていません。
- サーバ設定内容のみで、脆弱なデフォルト設定などは含まれていません。
- `README.md` や構成図はドキュメント目的で追加したものです。
