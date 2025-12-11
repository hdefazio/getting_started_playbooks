# 📄 Basic Web Server Deployment: `deploy_web_server.yaml`
## Playbook Purpose
This playbook demonstrates configuring and deploying a simple static website on a host. 

Key Concepts Demonstrated:
- `become: true`: Set at the play level, this ensures all tasks run with elevated privileges (sudo), which is mandatory for installing packages and writing files to system directories like /etc/nginx/ and /var/www/.

- Fact Gathering: Automatically collects extensive data about the operating system, network, and hardware (`gather_facts: true`)

- Ansible Facts: Utilizing automatically gathered variables like ansible_hostname and ansible_distribution

- Package Installation: The `ansible.builtin.package` module ensures the package is installed if missing, but takes no action if it is already present. This module abstracts away distribution differences, automatically using apt, yum, or dnf as required by the target host.

- Templating: Renders the index.html.j2 and nginx.conf.j2 files, ensuring the configuration and content are customized for the specific host they are deployed to. 

- Symbolic Permissions: Setting file permissions using symbolic notation (u=rw,g=r,o=r) instead of the traditional octal (0644).

## 🚀 How to Run the Playbook
```$ ansible-playbook deploy_web_server.yaml --ask-become-pass```

### Verify the results
`curl http://<ip>`

Expected Output (Values will vary depending on your host): 
```
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Ansible Information</title>
</head>
<body>
</body>
<h1>Your Ansible host:</h1>
<ul>
    <li>Name: host-name</li>
    <li>OS: Fedora 42</li>
    <li>Memory: 1000 MB / 1500 MB</li>
    <li>Python: 3.13.0</li>
</ul>
</html>
```
