# How do hostvars work?

### Command to run

`ansible-playbook -i ansible.inventory site.yml -clocal`

### Actual output

```
PLAY [foos] *******************************************************************

GATHERING FACTS ***************************************************************
ok: [localhost]

TASK: [hostvars | debug msg=vars] *********************************************
ok: [localhost] => {
    "msg": "vars"
}

TASK: [hostvars | debug msg={{ ansible_hostname }}] ***************************
ok: [localhost] => {
    "msg": "mjallday-2"
}

PLAY RECAP ********************************************************************
localhost                  : ok=3    changed=0    unreachable=0    failed=0
```

### Expected output

I would expect group_vars or host_vars to override the vars file and set the value to `host` rather than `var`.

```
TASK: [hostvars | debug msg=vars] *********************************************
ok: [localhost] => {
    "msg": "host"
}

```
