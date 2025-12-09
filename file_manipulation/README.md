# 📄 Hello World File Creation: `hello_world_file.yaml`
## Playbook Purpose
This playbook writes the text "Hello world!" to a file named /tmp/hello_world.txt on the target host(s).

Key Concepts Demonstrated:
- Variables: Using the `target_fp` variable to define the file path dynamically.

- Module Use: Utilizing the `ansible.builtin.copy` module with the content parameter to manage file contents directly.

- Lookup Plugin: Using `ansible.builtin.file` (via the `lookup` function) to read the file's content back to the control node for verification.

- Symbolic Permissions: Setting file permissions using symbolic notation (u=rw,g=r,o=r) instead of the traditional octal (0644).

- Idempotency: If the file already exists with the correct content and permissions, the playbook will report ok and make no changes.

## 🚀 How to Run the Playbook
```$ ansible-playbook hello_world_file.yaml```

### Verify the results
Check the file permissions
`$ ls -l /tmp/hello_world.txt`
Expected Permissions: `-rw-r--r--`

### Test Idempotency
Run the playbook again without making any changes to the file. The output for the task should now show ok=1 and changed=0, confirming that Ansible made no changes because the desired state was already met.

# 📄 System Info Report using a Template: `save_system_facts_using_template.yaml`
## Playbook Purpose
This playbook demonstrates how to use Ansible Facts to create dynamic configuration files on target hosts.

Key Concepts Demonstrated:
- Fact Gathering: Automatically collects extensive data about the operating system, network, and hardware (`gather_facts: true`)

- Ansible Facts: Utilizing automatically gathered variables like ansible_hostname and ansible_distribution

- Variables: Using the `target_dir` and `target_fp` variables to define the file path dynamically.

- Lookup Plugin: Using `ansible.builtin.file` (via the `lookup` function) to read the file's content back to the control node for verification.

- Templating: Renders the system_facts_template.j2 file

- Symbolic Permissions: Setting file permissions using symbolic notation (u=rw,g=r,o=r) instead of the traditional octal (0644).

## 🚀 How to Run the Playbook
```$ ansible-playbook save_system_facts_using_template.yaml```

### Verify the results
The output will display a debug message containing the contents of the newly created file, confirming that Ansible successfully gathered facts, rendered the template, and deployed the file using the dynamic path.
