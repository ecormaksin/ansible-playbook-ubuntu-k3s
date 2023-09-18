# Ansible Playbook for Ubuntu K3s

## Usage

- Before execute this playbook, we need to create the yaml files from templates as the table below.

    | source file | target file |
    | --- | --- |
    | ./host_vars/ag-01.dist.yml | ./host_vars/ag-01.yml |
    | ./host_vars/sv-01.dist.yml | ./host_vars/sv-01.yml |
    | ./vars_per_env.dist.yml | ./vars_per_env.yml |

- Execute an any command as follows:

  - for syntax check

    ```sh
    ansible-playbook -vv --syntax-check -i production.yml --extra-vars @vars_per_env.yml site.yml
    ```

  - for dry-run

    ```sh
    ansible-playbook -vv --check -i production.yml --extra-vars @vars_per_env.yml site.yml
    ```

  - for actual execution

    ```sh
    ansible-playbook -vv -i production.yml --extra-vars @vars_per_env.yml site.yml
    ```

  - start from a specified task

    ```sh
    ansible-playbook -vv -i production.yml --extra-vars @vars_per_env.yml site.yml --start-at="<task name>"
    ```