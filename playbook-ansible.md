# Playbook - Ansible

## Ansible Playbook

1. Replace the <mark style="color:red;">`hosts:`</mark> option to <mark style="color:red;">**localhost**</mark> or other <mark style="color:red;">**host**</mark> of your choice.

```yaml
---

- name: Configure and Install Suricata
  hosts: localhost
  become: yes

  tasks:
    - name: System Update
      apt:
        update_cache: yes
      changed_when: false

    - name: Dist Upgrade
      apt:
        upgrade: dist
      register: upgrade_output

    - name: Install software-properties-common
      apt:
        name: software-properties-common
        state: present

    - name: Add Suricata PPA
      apt_repository:
        repo: ppa:oisf/suricata-stable
        state: present

    - name: Update apt Cache
      apt:
        update_cache: yes

    - name: Install Suricata
      apt:
        name: suricata
        state: present

    - name: Replace Network in Suricata YAML
      replace:
        path: /etc/suricata/suricata.yaml
        regexp: 'HOME_NET: "\[192\.168\.0\.0/16,10\.0\.0\.0/8,172\.16\.0\.0/12\]"'
        replace: 'HOME_NET: "[network/prefix]"'

    - name: Replace Interface in Suricata YAML
      replace:
        path: /etc/suricata/suricata.yaml
        regexp: '- interface: eth0'
        replace: '- interface: your_interface'

    - name: Run suricata-update
      command: sudo suricata-update

    - name: Restart Suricata
      service:
        name: suricata
        state: restarted
```
