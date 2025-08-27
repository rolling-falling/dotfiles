### Run playbook

`ansible-playbook main.yml -K`

`-K` ask for privilege escalation password

or

```bash
export ANSIBLE_STDOUT_CALLBACK=yaml
```

```bash
ansible-playbook -vv -i hosts main.yml -K --tags nvim
```
