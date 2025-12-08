# 📄 Read-Write-Modify a Dictionary: `read_edit_save_dict.yaml`
## Playbook Purpose
The playbook uses a single JSON file on the control machine to store a dictionary (data) and edit its contents and write back to the JSON file. 

Key Concepts Demonstrated:

- `include_vars`: Reading external data (JSON) directly into an Ansible variable.

- `set_fact` & `combine`: The standard Ansible pattern for dynamically modifying or merging dictionary variables in memory.

- copy with content: Writing a variable back to a file using Jinja2 filters.

- `to_nice_json`: A Jinja2 filter essential for converting the Python dictionary object back into a correctly formatted, human-readable JSON string.

## 🚀 How to Run the Playbook
`$ ansible-playbook read_edit_save_dict.yaml`

### Verify the results
After the playbook completes, inspect the content of basic_sample_data.json to verify the changes:

`$ cat basic_sample_data.json`


Expected Output (JSON):
```
{
    "apples": 5,
    "bananas": 8,
    "oranges": 10,  <-- Edited value
    "pears": 1      <-- Added value
}
```
