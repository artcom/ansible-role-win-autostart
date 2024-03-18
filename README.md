# Win Autostart

Ansible role to create an autostart link for a command on a Windows 10 machine.

## Requirements

This role requires a reboot handler.

## Role Variables

Available variables are listed below, along with default values `(see defaults/main.yml)`:

```yaml
autostart_app_name: null
autostart_executable_path: null
autostart_user: null
autostart_description: "{{ autostart_app_name }}"
autostart_user_dir: "C:\\Users\\{{ autostart_user }}"
autostart_executable_arguments: ""
autostart_executable_working_directory: ""
```

Required variables (role will fail if the variables are not set):

```yaml
autostart_app_name: "string"
autostart_executable_path: "string"
autostart_user: "string"
```

The role will create an autostart link for `autostart_executable_path autostart_executable_arguments` for the `autostart_user` and a link to the `autostart_user` Desktop.

## Dependencies

- [check-required-variables](https://github.com/artcom/ansible-role-check-required-variables)

# Example Playbook

```yaml
- name: set up autostart
  hosts: all
  handlers:
    - name: reboot
      win_reboot:

  tasks:
    - import_role:
        name: win-autostart
      vars:
        autostart_app_name: "my_app"
        autostart_executable_path: "path_to_my_exe"
        autostart_user: "{{ ansible_user }}"
```

## License

MIT
