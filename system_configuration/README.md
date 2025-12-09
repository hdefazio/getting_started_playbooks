# 📄 Install a package: `install_cowsay.yaml`
## Playbook Purpose
This playbook provides a simple and fun example of installing and then utilizing a package.

Key Concepts Demonstrated:
- Per-Task `become`: The play is set to `become: false` by default, but the installation task explicitly overrides this with `become: true` and `become_user: root`. This demonstrates running only one specific task with elevated privileges. The playbook is run with `--ask-become-pass` in order to provide the sudo password. 

- Command registration: The `register: cowsay_hello` variable captures the output, return code, and status of the `cowsay` command.

- Conditional Execution (`when`): The final debug task uses `when: cowsay_hello.failed is false` to ensure the output is only printed if the cowsay command exited successfully.

- Package Installation: The `ansible.builtin.package` module ensures the package is installed if missing, but takes no action if it is already present. This module abstracts away distribution differences, automatically using apt, yum, or dnf as required by the target host.

- Idempotency Reporting: By default, Ansible often reports changed every time the command module is run, as it assumes the command might have caused a system change. This can be overwritten with `changed_when: false` to have Ansible report it as "ok" instead of "changed" when the command does not modify the configuration of the system. 

## 🚀 How to Run the Playbook
```$ ansible-playbook install_cowsay.yaml --ask-become-pass```

### Verify the results
Expected Output (JSON): 
```
"cowsay_hello.stdout_lines": [
        " ________",
        "< hello! >",
        " --------",
        "        \\   ^__^",
        "         \\  (oo)\\_______",
        "            (__)\\       )\\/\\",
        "                ||----w |",
        "                ||     ||"
    ]
```