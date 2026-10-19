# ansible Training
- ansible 学習用リポジトリです。

## 学習方針
単にコードを動かすだけでなく、なぜその設計にするのか
- なぜその設計を採用するのか
- 例外や異常系をどのように扱うのか
- 保守性・可読性をどのように確保するのか  
を考えながら学習・検証を行っています。

## 目的
- ansible の基礎構文の習得

## ディレクトリ構成
```text 
training_00
training_01
training_02
```

## 学習内容
- ansible 基本文法

## 実行方法
- 前提条件
- ansibleがインストールされていること  
```text 
ansible --version
sudo apt install ansible-core
```

## 開発環境
- OS : Linux(Ubuntu 24.04 LTS)
- 構成管理ツール : ansible [core 2.16.3]
- バージョン管理 : Git / GitHub
- 開発ツール : VS Code

## memo
- 実行コマンド
```text 
ansible-playbook  hello.yml
ansible-playbook -i localhost, -c local hello.yml
```

- shellsriptの自動化とどのように違うのか？
- ansibleは応用すると何になるの？
- ansibleの利用はなにが幸せになるの？
