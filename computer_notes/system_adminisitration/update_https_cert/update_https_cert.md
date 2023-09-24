# 更新Let's Encrypt证书
  Let’s Encrypt证书是是免费、开放和自动化的证书。     

更新证书    
---------------------------
`certbot renew //更新证书`    
`certbot renew --dry-run //--dry-run测试但不真的运行。`    

使用ansible来更新证书    
---------------------------------
```bash
- name: Update HTTPS cert
  hosts: reverse_proxy

  tasks:
    - name: Update HTTPS cert
      ansible.builtin.command:
        cmd: certbot renew
    - name: Restart Nginx daemon
      ansible.builtin.service:
        name: nginx
        state: restarted                             
  #保存update-https-cert.yml
  #运行 ansible-playbook reverse-proxy/update-https-cert.yml
```
配置inventory.yml    
---------------------------------------------
```bash
all:
  hosts:
  vars:
    ansible_user: root
  children:
    reverse_proxy:
      hosts:
        manlin-verlag.de:
    wordpress:
      hosts:
        91.107.202.88:
    docker_swarm:
      hosts:
        88.198.109.219:
        142.132.236.166:
    database:
      hosts:
        23.88.45.151:
```
配置ansible.cfg    
-------------------------------------
```bash
[defaults]
inventory = ./inventory.yml
host_key_checking = false
```
[System Adminisitration](../system_adminisitration.md)