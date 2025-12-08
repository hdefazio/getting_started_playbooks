# 📄 Hello World File Creation
## 📝 Playbook Purpose
This playbook writes the text "Hello world!" to a file named /tmp/hello_world.txt on the target host(s).

Key Concepts Demonstrated:
- Variables: Using the `target_fp` variable to define the file path dynamically.

- Module Use: Utilizing the `ansible.builtin.copy` module with the content parameter to manage file contents directly.

- Lookup Plugin: Using `ansible.builtin.file` (via the `lookup` function) to read the file's content back to the control node for verification.

- Permissions: Setting explicit file permissions using the octal mode: '0644'.

- Idempotency: If the file already exists with the correct content and permissions, the playbook will report ok and make no changes.

## 🚀 How to Run the Playbook
```$ ansible-playbook hello_world_file.yaml```

## Verify the results
Check the file permissions
`$ ls -l /tmp/hello_world.txt`
Expected Permissions: `-rw-r--r--`

### Test Idempotency
Run the playbook again without making any changes to the file. The output for the task should now show ok=1 and changed=0, confirming that Ansible made no changes because the desired state was already met.