# ansibleの良さ
- 最初は単独サーバのほうがAnsibleの価値を実感しやすい です。  
- 「100台管理できる」ことに注目しますが、単独サーバでも次のメリットがあります。

## 項目一覧
1. 手順の標準化
2. やり直しが簡単
3. ミス防止
4. 差分だけ適用される
5. 設計書代わりになる
6. Bashより保守しやすい  
まとめ  
memo  

### 1. 手順の標準化
---
例えば、Java環境構築を毎回手でやると、
```bash
sudo dnf install java-17-openjdk
mkdir -p /opt/app
cp app.jar /opt/app
chmod 755 /opt/app
```
という手順になります。

Ansibleなら
```yml
- name: Java導入
  package:
    name: java-17-openjdk
    state: present
```
などをPlaybookに残せます。
つまり、
「何をやったか」がコードとして残るのが大きいです。

### 2. やり直しが簡単
---
サーバを作り直した場合、  
ansible-playbook setup.yml  
だけで同じ環境を再現できます。  
手順書だと  
- ①Java導入
- ②設定変更
- ③ディレクトリ作成  
...  
を再度実施する必要があります。  

### 3. ミス防止
---
人間は意外と忘れます。  
例えば  
```bash
chmod 755  
```
のつもりが  
```bash
chmod 777  
```
を実行することがあります。  
Ansibleなら毎回同じ設定です。  

### 4. 差分だけ適用される
---
Ansibleの特徴は冪等性です。  
例えば 
```yml
- file:
    path: /tmp/work
    state: directory
```
を100回実行しても、  

既に存在する  
↓
何もしない、になります。  
Bashだと細かな存在チェックを書く場合があります。  

### 5. 設計書代わりになる
---
例えば
```text
roles/
 ├─ common
 ├─ java
 ├─ tomcat
 └─ app
 ```
を見れば、　
```text
共通設定
↓
Java
↓
Tomcat
↓
アプリ配置
```
というサーバ構成が一目で分かります。

### 6. Bashより保守しやすい
---
例えばディレクトリ作成。
- Bash
```bash
if [ ! -d /tmp/work ]; then
    mkdir /tmp/work
fi
```

- Ansible
```yaml
- file:
    path: /tmp/work
    state: directory
```

### まとめ
--- 
Ansibleのほうが、「何をしたいのか」が分かりやすいです。

「Bashで手続きを書く」から 「サーバのあるべき状態を書く」  
というAnsibleの考え方の違いが見えてきます。  
その段階で複数サーバ管理へ進むと理解しやすいです。 

### 参考
- AI先生
- 

### memo
---
- 
- 
- 
