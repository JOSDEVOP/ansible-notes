# Ansible Playbook Explanation

This Ansible playbook is used to install the Apache web server (`apache2`) and copy a custom HTML file to the web server's root directory.

## Playbook Structure

### Play

- **Name:** Installing apache2
- **Hosts:** app
- **Become:** yes

This play targets the `app` host group and uses `become: yes` to execute tasks with elevated privileges.

### Tasks

1. **Installing Apache**
   - **Name:** Installing apache
   - **Module:** `ansible.builtin.apt`
   - **Parameters:**
     - `name: apache2`: Specifies the package name to install.
     - `state: present`: Ensures that the `apache2` package is installed.
     - `update_cache: yes`: Updates the package cache before installing the package.

2. **Copying the HTML File**
   - **Name:** Copy file with owner and permissions
   - **Module:** `ansible.builtin.copy`
   - **Parameters:**
     - `src: ./index.html`: Specifies the source file path on the control node.
     - `dest: /var/www/html`: Specifies the destination directory on the target host where the file should be copied.
     - `owner: root`: Sets the owner of the copied file to `root`.
     - `group: root`: Sets the group of the copied file to `root`.
     - `mode: '0644'`: Sets the file permissions to `0644` (readable by everyone, writable by the owner).

### Summary

This playbook installs the Apache web server and deploys a custom `index.html` file to the server's root directory. It ensures the correct ownership and permissions are set for the file.
