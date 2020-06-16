# Win Autostart
Ansible role to create an autostart link for a command on a Windows 10 machine.

## Role Variables
Available variables are listed below, along with default values `(see defaults/main.yml)`:
```yaml
app_name: null
executable_path: null
autostart_user: null
autostart_user_dir: "C:\\Users\\{{ autostart_user }}"
executable_arguments: ""
```

Mandatory variables (role will fail if the variables are not set):
```yaml
app_name: "string"
executable_path: "string"
autostart_user: "string"
```

The role will create an autostart link for `executable_path executable_arguments` for the `autostart_user` and a link from the `Startup` dierectory to the `autostart_user` Desktop.
