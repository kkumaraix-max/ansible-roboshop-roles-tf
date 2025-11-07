- name: disable default redis
  ansible.builtin.command: dnf module disable redis -y

- name: enable redis 7
  ansible.builtin.command: dnf module enable redis:7 -y

- name: install redis
  ansible.builtin.package:
    name: redis
    state: present

- name: allow remote connections
  ansible.builtin.replace:
    path: /etc/redis/redis.conf
    regexp: '127.0.0.1'
    replace: '0.0.0.0'

- name: disable proctected mode
  ansible.builtin.lineinfile:
    path: /etc/redis/redis.conf
    regexp: 'protected-mode'
    line: 'protected-mode no'

- name: start and enable redis
  ansible.builtin.service:
    name: redis
    enabled: yes
    state: started