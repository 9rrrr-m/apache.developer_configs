apache.developer_configs
=========

  💜 제작자: 9rrrr-m

  💜 Contact: 9rrrrm@gmail.com

---
Ansible을 이용하여 관리 호스트를 Apache vhost 서버로 설정해주는 Ansible-galaxy role 입니다.
- 사용자를 생성합니다.
- 방화벽 서비스를 설치하고 기동합니다. 서비스할 서비스 포트와 비표준 포트를 오픈합니다.
- Apache vhost 서버를 생성합니다. (다음 설정 파일은 검토되어야 합니다.)

  - `files/httpd.conf` 파일의 Listen 포트 및 그 외 설정
  - `templates/developer.conf.j2` 템플릿의 포트 설정

요구사항
------------
제어 노드에 Ansible이 설치되어 있어야 합니다.

역할 변수
--------------
`vars/main.yml`에 다음과 같이 변수를 설정하세요.

변수로 지정된 사용자가 새로 생성되며, 해당 포트의 vhost 사용자로 생성됩니다.
```
web_developers:
  - username: student1
    pw_hash: Gryffindor
    name: Harry Potter
    user_port: 9081
  - username: student2
    pw_hash: Gryffindor
    name: Ronald Weasley
    user_port: 9082
```

플레이북 예시
----------------
다음과 같이 플레이북에 역할을 지정하여 사용합니다.
```
- name: Configure Dev Web Server
  hosts: dev_servers
  roles:
    - apache.developer_configs
```
#
---

apache.developer_configs
=========

  💜 Author: 9rrrr-m

  💜 Contact: 9rrrrm@gmail.com

---
This is an Ansible Galaxy role that configures the managed host as an Apache vhost server using Ansible.
- Creates users.
- Installs and starts the firewall service, opening the service and any non-standard ports needed.
- Creates an Apache vhost server. (The following configuration files should be reviewed.)

  - `files/httpd.conf` for the Listen port and other settings.
  - `templates/developer.conf.j2` template for port configuration.

Requirements
------------
Ansible must be installed on the control node.

Role Variables
--------------
The specified user is newly created as a vhost user on the designated port.

Set the following variables in `vars/main.yml`:
```
web_developers:
  - username: student1
    pw_hash: Gryffindor
    name: Harry Potter
    user_port: 9081
  - username: student2
    pw_hash: Gryffindor
    name: Ronald Weasley
    user_port: 9082
```

Example Playbook
----------------
Specify the role in your playbook as follows:
```
- name: Configure Dev Web Server
  hosts: dev_servers
  roles:
    - apache.developer_configs
```
