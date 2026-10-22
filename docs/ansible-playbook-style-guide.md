# Ansibleの書き方
## Ansibleの基本モジュールを1つずつ触る段階 です。

- Ansibleの基本モジュールとは
  -  詳細：ansible-basic-modules.md

## 項目一覧
1. ファイル作成
2. ファイルに文字を書き込む
3. コマンド実行
4. 変数を使う
5. 条件分岐
6. 繰り返し処理
7. Linuxサーバ管理でよく使う例
8. memo

### 1. ファイル作成
```yml
---
- name: Create file
  hosts: localhost
  gather_facts: false

  tasks:
    - name: ファイル作成
      file:
        path: /tmp/test.txt
        state: touch
```

実行
``` bash
ansible-playbook create_file.yml
```

確認
``` bash
ls -l /tmp/test.txt
``` 

### 2. ファイルに文字を書き込む
```yml
- name: Write file
  hosts: localhost
  gather_facts: false

  tasks:
    - name: テキスト出力
      copy:
        content: "Hello Ansible\n"
        dest: /tmp/test.txt
```
確認
```bash
cat /tmp/test.txt
```

### 3. コマンド実行
```yml
- name: Execute command
  hosts: localhost
  gather_facts: false

  tasks:
    - name: date実行
      command: date
```
結果
```text
現在日時が表示
```

### 4. 変数を使う
```yml
- name: Variable sample
  hosts: localhost
  gather_facts: false

  vars:
    message: "Hello Ryuma"

  tasks:
    - debug:
        msg: "{{ message }}"
```
- Ansibleでは、**{{ 変数名 }}**で参照します。

### 5. 条件分岐
```yml
- hosts: localhost
  gather_facts: false

  vars:
    env: dev

  tasks:
    - debug:
        msg: "開発環境"

      when: env == "dev"
```

### 6. 繰り返し処理
```yml
- hosts: localhost
  gather_facts: false

  tasks:
    - debug:
        msg: "{{ item }}"
      loop:
        - Java
        - Linux
        - AWS
```
- 実行結果
```text
Java
Linux
AWS
```

### 7. Linuxサーバ管理でよく使う例
```yml
ディレクトリ作成
- file:
    path: /tmp/work
    state: directory

権限変更
- file:
    path: /tmp/work
    mode: '0755'

パッケージ導入
- yum:
    name: git
    state: present
```

次の目標としては  
- localhostでPlaybook実行  
- ファイル操作  
- 変数・条件分岐・loop  
- 複数サーバ管理（inventory）  
- Role化  
- AWS構築自動化  
の順番が理解しやすいと思います。  

特に Role化 まで行けると実務のAnsibleらしくなります。
```text 
roles/
 ├─ java/
 ├─ tomcat/
 └─ app/
```
のように部品化して、「Java導入→Tomcat導入→アプリ配置」を自動で実行できるようになります。
これは基盤構築案件でよく使われる構成です。

### 参考
---
- AI先生
- 

### memo
---
- 
- 
- 
