# Jenkins Installation Role for Debian 12.04 using Ansible

This role is designed for automatically installing Jenkins on a Debian 12.04 system with a Java dependency. It includes tasks to install Java (if it's not already installed), set up Jenkins, and configure the necessary repositories and keys for package installation.

## Role Structure

1. **defaults/main.yml** — default variables for Java and Jenkins installation.
2. **tasks/java.yml** — tasks to install Java (if it's not already installed).
3. **tasks/jenkins.yml** — tasks to install and configure Jenkins.
4. **tasks/main.yml** — main file that includes other tasks.

## Variables

* **java_package_url** — URL for downloading the OpenJDK package.
* **jdk_deb_file** — path to temporarily store the downloaded OpenJDK package.
* **jenkins_repo_url** — URL for the Jenkins repository.
* **jenkins_key_url** — URL for downloading the Jenkins GPG key.

## Usage

1. Clone this role into the `roles/jenkins/` directory.
2. Add the role to your playbook as shown below:

```yaml
- name: Install Jenkins and Java
  hosts: jenkins
  become: yes
  roles:
    - jenkins
```

3. Run the playbook with the following command:

```bash
ansible-playbook -i inventory.ini playbook.yml
```

## Features

* The role checks if Java is installed on the target system. If Java is not installed, it will be installed.
* Installs all necessary dependencies for Jenkins.
* Adds the Jenkins repository and keys to ensure the latest version is installed.
* Includes handlers to restart Jenkins if necessary.

## License

This role is licensed under the MIT License.
