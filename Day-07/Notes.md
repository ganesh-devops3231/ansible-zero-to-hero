### Notes:
- Above first task is for printing all the gathered facts about the IPs that we are passing through inventory while giving executing command
  for playbook.
- Based on the list of gathered facts we receive, we can decide which facts we can use for conditioning in when. Like above we just want to
  shutdown the ubuntu machines, so thats the reason we used  ansible_facts['os_family'] == "Debian" where in gathered facts we can see
  os_family element with value as Debian.
