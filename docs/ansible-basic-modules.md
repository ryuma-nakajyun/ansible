# Ansibleの基本モジュールとは
モジュールとは、Ansibleがリモートサーバで実行する「処理の部品」です。

例えば、
- ファイルをコピーする
- パッケージをインストールする
- サービスを起動する
- ユーザーを作成する
といった処理をモジュールが担当します。

### よく使う基本モジュール
| モジュール | 用途 |
| ------ | ---- |
| copy | ファイルをコピー | 
| file | ファイル・ディレクトリ作成、権限変更 | 
| template | Jinja2テンプレート展開 | 
| yum / dnf | パッケージ管理（RHEL系） | 
| apt | パッケージ管理（Ubuntu系） | 
| service | サービス起動・停止 | 
| systemd | systemdサービス管理 | 
| user | ユーザー管理 | 
| group | グループ管理 | 
| command | コマンド実行 | 
| shell | シェル実行 | 
| get_url | URLからダウンロード | 
| unarchive | 圧縮ファイル展開 | 
| lineinfile | ファイルの1行編集 | 
| replace | 文字列置換 | 
| stat | ファイル情報取得 | 
| debug | 変数表示・デバッグ | 

例1: ファイルコピー
```yaml
- name: 設定ファイルを配置
  copy:
    src: app.conf
    dest: /etc/app.conf
    mode: '0644'
```

例2: パッケージインストール
```yaml
- name: nginxインストール
  yum:
    name: nginx
    state: present
```
または
```yaml
- name: nginxインストール
  dnf:
    name: nginx
    state: present
```
例3: サービス起動
```yaml
- name: nginx起動
  systemd:
    name: nginx
    state: started
    enabled: true
```

例4: ユーザー作成
```yaml
- name: ユーザー作成
  user:
    name: appuser
    shell: /bin/bash
```

### 使用頻度が高いモジュール  
優先度順に並べると、
- file
- copy
- template
- systemd
- yum / dnf / apt
- user
- lineinfile
- stat
- command
- shell
です。

### Ansible の Playbookの基本
- file
- copy
- template
- systemd
- yum(dnf)
- stat

### 参考
---
- AI先生
- 書籍たち

### memo
--- 
- 
- 
-  