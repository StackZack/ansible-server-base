# ansible-server-base

```bash
brew install esolitos/ipa/sshpass
ansible-playbook -i inventory -u root -k server_playbook.yml
ansible-galaxy collection install community.general
```

TODO
1. Add key to key folder which needs to be made
2. Disable root login (at end)