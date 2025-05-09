# Variable Notes

## Priority of Variable folders:

In Ansible, variables can be defined in multiple places, and there’s a priority order that determines which value gets used if the same variable is defined in multiple locations. Below is the priority order, from highest to lowest:
Ansible Variable Precedence (Highest to Lowest Priority)
- Extra Vars (-e option in CLI) – Variables passed via the command line (ansible-playbook playbook.yml -e "var=value") have the highest priority.
- Playbook Vars (vars section in playbook) – Variables defined inside the playbook YAML file under the vars: section.
- Role Vars (roles/role_name/vars/ folder) – Variables inside the vars/ folder of a role.
- Block Vars (vars inside a block: section) – Variables inside a block in a task.
- Task Vars (vars inside a task) – Variables directly assigned to a task.
- Include Vars (include_vars module or vars_files: section) – Variables loaded using include_vars or vars_files:.
- Registered Variables (register: module) – Variables created dynamically within tasks and stored for later use.
- Facts (set_fact or gathered by setup module) – Variables created using set_fact or automatically collected from hosts.
- Inventory Vars (inventory file or group_vars/host_vars folders) – Variables set in the inventory file or defined in group_vars/ and host_vars/.
- Role Defaults (roles/role_name/defaults/ folder) – Variables inside the defaults/ folder of a role (lowest precedence).
Key Takeaways:
- If a variable is set in multiple places, the highest-priority source wins.
- extra-vars (-e "var=value") always overrides everything.
- vars in a role overrides defaults in the same role.
- group_vars and host_vars are lower priority than playbook-defined vars.
This priority order ensures flexibility while maintaining structured variable management.

## Notes:
- For group vars, you have to create a folder and then add the yaml file with a group name that is present in inventory file. So, if you execute any playbook with only a particular group in inventory then the same group related file is taken under consideration for variables from groupname.yml file.
