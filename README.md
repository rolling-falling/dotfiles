# Dotfiles

Inspired by https://github.com/ALT-F4-LLC/dotfiles

# Packets

- nvim
- - TODO: git plugin
- - TODO: copy-paste plugin. make sure xclip & xsel are not used (disaster in wsl)
- - TODO: apt install python3-venv (for mason)
- mics
- - TODO: alias `grep --color=always` and `less -R` in .bashrc to preserve colors in less

# Prerequisites

- openssh
- `mkdir -p ~/code/github/rolling-falling`
- gh
    ```
    apt install gh
    gh auth
    gh repo ls
    gh repo clone rolling-falling/dotfiles
    gh completion -s bash > ${BASH_COMPLETION_USER_DIR:-${XDG_DATA_HOME:-$HOME/.local/share}/bash-completion}/completions/gh
    gh completion -s zsh > /usr/local/share/zsh/site-functions/_gh
    ```
- pipx
    ```
    sudo apt install pipx
    pipx ensurepath
    sudo pipx ensurepath --global
    ```
- ansible
    ```
    pipx install ansible --include-deps
    ```
    Lets get completions for ansible too.

    Ansible uses python's argcomplete.

    Argcomplete generates bash completion for all python scripts that use argparse.

    Enable global argcomplete's completion for current user

    `activate-global-python-argcomplete --dest=${BASH_COMPLETION_USER_DIR:-${XDG_DATA_HOME:-$HOME/.local/share}/bash-completion}/completions`

    The trick here is to fed it with correct bash-completion directory.

- ssh server on localhost
  ```
  systemctl enable sshd
  systemctl restart sshd
  systemctl status sshd
  ```
  authorize with your ssh key on localhost
  ```
  cat ~/.ssh/id_ed25519.pub >> ~/.ssh/authorized_keys
  chmod og-wx ~/.ssh/authorized_keys
  ```
- git config
  ```
  git config user.name "rolling-falling"
  git config user.email "..."
  ```
  git should use only the ssh key you've added to github
  ```
  git config core.sshCommand 'ssh -i ~/.ssh/id_ed25519_rolling_falling -o IdentitiesOnly=yes'
  ```
  check the config
  ```
  git config --list
  ```

- `cd ansible` # and continue there
