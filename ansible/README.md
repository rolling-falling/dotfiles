# Ansible

### Lets get completions for ansible too.

Ansible uses python's argcomplete.

Argcomplete generates bash completion for all python scripts that use argparse.

Enable global argcomplete's completion for current user

`activate-global-python-argcomplete --dest=${BASH_COMPLETION_USER_DIR:-${XDG_DATA_HOME:-$HOME/.local/share}/bash-completion}/completions`

The trick here is to fed it with correct bash-completion directory.

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
