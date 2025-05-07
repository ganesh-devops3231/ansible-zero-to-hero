# Push your Ansible roles to Ansible Galaxy

1. Make sure your role is structured correctly. The basic structure should look like this:

```
my_role/
├── defaults/
│   └── main.yml
├── files/
├── handlers/
│   └── main.yml
├── meta/
│   └── main.yml
├── tasks/
│   └── main.yml
├── templates/
├── tests/
│   ├── inventory
│   └── test.yml
└── vars/
    └── main.yml
```

2. Make sure ansible-galaxy CLI exists

```
ansible-galaxy --version
```

3. Push Your Role to GitHub

```
cd <role-name>
git init
git remote add origin <https://github.com/your_github_username/my_role.git>
git add .
git commit -m "Initial commit"
git push -u origin main
```

4. Import the Role to Ansible Galaxy

```
ansible-galaxy role import <your_github_username> <role-name>
```
###Notes:
- Ansible-galaxy is a hub where it contains whole bunch of imported roles or collections from different users across the world. Even in your organization roles will be uploaded to ansible-galaxy.
- Download docker installation role from ansible-galaxy and practice it (bsmeding.docker is an example).
- To install any role from ansible-galaxy, installation command is available in every role information.
  ```ansible-galaxy role install roleName```
- ```ansible-galaxy role-h``` is the command which gives different commands and information about ansible-galaxy.
- Always update your author information in meta folder main.yml file.
