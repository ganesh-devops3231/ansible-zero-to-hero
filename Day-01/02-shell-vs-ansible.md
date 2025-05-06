# Comparison with Shell Scripting and also Python

- Shell Scripting works only for Linux.

- Becomes complex and less readable(for non-experts) as the script size goes high.

- Idempotence and predictability

When the system is in the state your playbook describes Ansible does not change anything, even if the playbook runs multiple times.

for example, run the below shell script twice and you will notice the script will fail. Which means shell scripting is not idempotent in nature.

```
#/bin/bash

set -e 

mkdir test-demo
echo "hi"
```

- Scalability and flexibility

Easily and quickly scale the systems you automate through a modular design that supports a large range of operating systems, cloud platforms, and network devices.

**Comparing Python & Ansible:**
- Python is a indpendent in all platforms, because of this reason you can achieve what ever to modify in the VMs. But it requires the maintenance whenever python upgrades need to check some syntaxes changes. Also for connecting other target VMs, python requires some additional extensions/installations to connect to VMs.
- Whereas ansible is less in maintenance and also it is easy in authentication purpose.
