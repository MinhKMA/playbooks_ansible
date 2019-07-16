# debug

- file yml

```
---
- name: node_exporter
  hosts: "client"
  tasks:
    - name: debug 
      debug:
        msg: 'hi MinhKMA'
```
- run 

```
ansible-playbook debug.yml
```

- output 

```
[root@ansible ~]# ansible-playbook debug.yml 

PLAY [node_exporter] ***********************************************************************************************************************************************************

TASK [Gathering Facts] *********************************************************************************************************************************************************
ok: [192.168.80.243]
ok: [192.168.80.242]
ok: [192.168.80.241]

TASK [debug] *******************************************************************************************************************************************************************
ok: [192.168.80.241] => {
    "msg": "hi MinhKMA"
}
ok: [192.168.80.242] => {
    "msg": "hi MinhKMA"
}
ok: [192.168.80.243] => {
    "msg": "hi MinhKMA"
}

PLAY RECAP *********************************************************************************************************************************************************************
192.168.80.241             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
192.168.80.242             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
192.168.80.243             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0  
```

# vars 

- file yml

```
---
- name: node_exporter
  hosts: "client"
  tasks:
    - name: shell
      shell: 'ip a'
      register: result
    - name: debug 
      debug:
        var: result
```

- run 

```
ansible-playbook vars.yml
```

- output 

```
[root@ansible ~]# ansible-playbook vars.yml 

PLAY [node_exporter] ***********************************************************************************************************************************************************

TASK [Gathering Facts] *********************************************************************************************************************************************************
ok: [192.168.80.242]
ok: [192.168.80.243]
ok: [192.168.80.241]

TASK [shell] *******************************************************************************************************************************************************************
changed: [192.168.80.243]
changed: [192.168.80.242]
changed: [192.168.80.241]

TASK [debug] *******************************************************************************************************************************************************************
ok: [192.168.80.241] => {
    "result": {
        "changed": true, 
        "cmd": "ip a", 
        "delta": "0:00:00.007620", 
        "end": "2019-07-16 09:42:27.189046", 
        "failed": false, 
        "rc": 0, 
        "start": "2019-07-16 09:42:27.181426", 
        "stderr": "", 
        "stderr_lines": [], 
        "stdout": "1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000\n    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00\n    inet 127.0.0.1/8 scope host lo\n       valid_lft forever preferred_lft forever\n    inet6 ::1/128 scope host \n       valid_lft forever preferred_lft forever\n2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:dc:c9:b6 brd ff:ff:ff:ff:ff:ff\n    inet 192.168.80.241/24 brd 192.168.80.255 scope global noprefixroute eth0\n       valid_lft forever preferred_lft forever\n    inet6 fe80::e9e:d473:fc40:c37d/64 scope link noprefixroute \n       valid_lft forever preferred_lft forever\n3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:de:60:95 brd ff:ff:ff:ff:ff:ff", 
        "stdout_lines": [
            "1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000", 
            "    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00", 
            "    inet 127.0.0.1/8 scope host lo", 
            "       valid_lft forever preferred_lft forever", 
            "    inet6 ::1/128 scope host ", 
            "       valid_lft forever preferred_lft forever", 
            "2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000", 
            "    link/ether 52:54:00:dc:c9:b6 brd ff:ff:ff:ff:ff:ff", 
            "    inet 192.168.80.241/24 brd 192.168.80.255 scope global noprefixroute eth0", 
            "       valid_lft forever preferred_lft forever", 
            "    inet6 fe80::e9e:d473:fc40:c37d/64 scope link noprefixroute ", 
            "       valid_lft forever preferred_lft forever", 
            "3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000", 
            "    link/ether 52:54:00:de:60:95 brd ff:ff:ff:ff:ff:ff"
        ]
    }
}
ok: [192.168.80.242] => {
    "result": {
        "changed": true, 
        "cmd": "ip a", 
        "delta": "0:00:00.007362", 
        "end": "2019-07-16 09:42:26.984626", 
        "failed": false, 
        "rc": 0, 
        "start": "2019-07-16 09:42:26.977264", 
        "stderr": "", 
        "stderr_lines": [], 
        "stdout": "1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000\n    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00\n    inet 127.0.0.1/8 scope host lo\n       valid_lft forever preferred_lft forever\n    inet6 ::1/128 scope host \n       valid_lft forever preferred_lft forever\n2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:e3:99:64 brd ff:ff:ff:ff:ff:ff\n    inet 192.168.80.242/24 brd 192.168.80.255 scope global noprefixroute eth0\n       valid_lft forever preferred_lft forever\n    inet6 fe80::c1b3:8fa8:3c98:8073/64 scope link noprefixroute \n       valid_lft forever preferred_lft forever\n3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:a4:ce:03 brd ff:ff:ff:ff:ff:ff", 
        "stdout_lines": [
            "1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000", 
            "    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00", 
            "    inet 127.0.0.1/8 scope host lo", 
            "       valid_lft forever preferred_lft forever", 
            "    inet6 ::1/128 scope host ", 
            "       valid_lft forever preferred_lft forever", 
            "2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000", 
            "    link/ether 52:54:00:e3:99:64 brd ff:ff:ff:ff:ff:ff", 
            "    inet 192.168.80.242/24 brd 192.168.80.255 scope global noprefixroute eth0", 
            "       valid_lft forever preferred_lft forever", 
            "    inet6 fe80::c1b3:8fa8:3c98:8073/64 scope link noprefixroute ", 
            "       valid_lft forever preferred_lft forever", 
            "3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000", 
            "    link/ether 52:54:00:a4:ce:03 brd ff:ff:ff:ff:ff:ff"
        ]
    }
}
ok: [192.168.80.243] => {
    "result": {
        "changed": true, 
        "cmd": "ip a", 
        "delta": "0:00:00.006742", 
        "end": "2019-07-16 09:42:26.481373", 
        "failed": false, 
        "rc": 0, 
        "start": "2019-07-16 09:42:26.474631", 
        "stderr": "", 
        "stderr_lines": [], 
        "stdout": "1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000\n    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00\n    inet 127.0.0.1/8 scope host lo\n       valid_lft forever preferred_lft forever\n    inet6 ::1/128 scope host \n       valid_lft forever preferred_lft forever\n2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:3e:0c:28 brd ff:ff:ff:ff:ff:ff\n    inet 192.168.80.243/24 brd 192.168.80.255 scope global noprefixroute eth0\n       valid_lft forever preferred_lft forever\n    inet6 fe80::ee72:dff5:5f21:612e/64 scope link noprefixroute \n       valid_lft forever preferred_lft forever\n3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:fb:c9:97 brd ff:ff:ff:ff:ff:ff", 
        "stdout_lines": [
            "1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000", 
            "    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00", 
            "    inet 127.0.0.1/8 scope host lo", 
            "       valid_lft forever preferred_lft forever", 
            "    inet6 ::1/128 scope host ", 
            "       valid_lft forever preferred_lft forever", 
            "2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000", 
            "    link/ether 52:54:00:3e:0c:28 brd ff:ff:ff:ff:ff:ff", 
            "    inet 192.168.80.243/24 brd 192.168.80.255 scope global noprefixroute eth0", 
            "       valid_lft forever preferred_lft forever", 
            "    inet6 fe80::ee72:dff5:5f21:612e/64 scope link noprefixroute ", 
            "       valid_lft forever preferred_lft forever", 
            "3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000", 
            "    link/ether 52:54:00:fb:c9:97 brd ff:ff:ff:ff:ff:ff"
        ]
    }
}

PLAY RECAP *********************************************************************************************************************************************************************
192.168.80.241             : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
192.168.80.242             : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
192.168.80.243             : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

- file yml 

```
---
- name: node_exporter
  hosts: "client"
  tasks:
    - name: shell
      shell: 'ip a'
      register: result
    - name: debug
      debug:
        var: result.stdout
```

- output

```
[root@ansible ~]# ansible-playbook vars.yml 

PLAY [node_exporter] ***********************************************************************************************************************************************************

TASK [Gathering Facts] *********************************************************************************************************************************************************
ok: [192.168.80.243]
ok: [192.168.80.242]
ok: [192.168.80.241]

TASK [shell] *******************************************************************************************************************************************************************
changed: [192.168.80.243]
changed: [192.168.80.242]
changed: [192.168.80.241]

TASK [debug] *******************************************************************************************************************************************************************
ok: [192.168.80.241] => {
    "result.stdout": "1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000\n    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00\n    inet 127.0.0.1/8 scope host lo\n       valid_lft forever preferred_lft forever\n    inet6 ::1/128 scope host \n       valid_lft forever preferred_lft forever\n2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:dc:c9:b6 brd ff:ff:ff:ff:ff:ff\n    inet 192.168.80.241/24 brd 192.168.80.255 scope global noprefixroute eth0\n       valid_lft forever preferred_lft forever\n    inet6 fe80::e9e:d473:fc40:c37d/64 scope link noprefixroute \n       valid_lft forever preferred_lft forever\n3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:de:60:95 brd ff:ff:ff:ff:ff:ff"
}
ok: [192.168.80.242] => {
    "result.stdout": "1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000\n    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00\n    inet 127.0.0.1/8 scope host lo\n       valid_lft forever preferred_lft forever\n    inet6 ::1/128 scope host \n       valid_lft forever preferred_lft forever\n2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:e3:99:64 brd ff:ff:ff:ff:ff:ff\n    inet 192.168.80.242/24 brd 192.168.80.255 scope global noprefixroute eth0\n       valid_lft forever preferred_lft forever\n    inet6 fe80::c1b3:8fa8:3c98:8073/64 scope link noprefixroute \n       valid_lft forever preferred_lft forever\n3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:a4:ce:03 brd ff:ff:ff:ff:ff:ff"
}
ok: [192.168.80.243] => {
    "result.stdout": "1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000\n    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00\n    inet 127.0.0.1/8 scope host lo\n       valid_lft forever preferred_lft forever\n    inet6 ::1/128 scope host \n       valid_lft forever preferred_lft forever\n2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:3e:0c:28 brd ff:ff:ff:ff:ff:ff\n    inet 192.168.80.243/24 brd 192.168.80.255 scope global noprefixroute eth0\n       valid_lft forever preferred_lft forever\n    inet6 fe80::ee72:dff5:5f21:612e/64 scope link noprefixroute \n       valid_lft forever preferred_lft forever\n3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000\n    link/ether 52:54:00:fb:c9:97 brd ff:ff:ff:ff:ff:ff"
}

PLAY RECAP *********************************************************************************************************************************************************************
192.168.80.241             : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
192.168.80.242             : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
192.168.80.243             : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

# extra-vars

- file yml 

```
---
- name: node_exporter
  hosts: "client"
  tasks:
    - name: debug 
      debug:
        msg: "hi {{minhkma}}"
```

- run 

```
ansible-playbook demo.yml --extra-vars '{"minhkma":"minh nguyen"}'
```

Truyền biến dạng json '{"minhkma":"minh nguyen","dep trai":"co"}'

- output 

```
[root@ansible ~]# ansible-playbook demo.yml --extra-vars '{"minhkma":"minh nguyen"}'

PLAY [node_exporter] ***********************************************************************************************************************************************************

TASK [Gathering Facts] *********************************************************************************************************************************************************
ok: [192.168.80.243]
ok: [192.168.80.242]
ok: [192.168.80.241]

TASK [debug] *******************************************************************************************************************************************************************
ok: [192.168.80.241] => {
    "msg": "hi minh nguyen"
}
ok: [192.168.80.242] => {
    "msg": "hi minh nguyen"
}
ok: [192.168.80.243] => {
    "msg": "hi minh nguyen"
}

PLAY RECAP *********************************************************************************************************************************************************************
192.168.80.241             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
192.168.80.242             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
192.168.80.243             : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0 
```