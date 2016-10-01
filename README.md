# Docker Cairo Meetup

## What You Need

- VirtualBox
- Vagrant
- Ansible

## Setup

The setup consists of 3 virtual machines:
- master
- node1
- node2
- db1

To bring up the 3 virtual machines:

```bash
vagrant up
```

To make sure the machines are up:

```bash
vagrant status
```

Add ssh keys of the host's known_hosts

```bash
ssh-keyscan -H 192.168.55.10 >> ~/.ssh/known_hosts
ssh-keyscan -H 192.168.55.11 >> ~/.ssh/known_hosts
ssh-keyscan -H 192.168.55.12 >> ~/.ssh/known_hosts
ssh-keyscan -H 192.168.55.13 >> ~/.ssh/known_hosts
```

Now, provision the machines using ansible

```bash
cd ansible
ansible-playbook --inventory-file=dev -v --sudo site.yml
```

## Troubleshooting

- To remove stale containers from an overlay network `docker network disconnect -f {network} {container}`

## Cleanup

- To cleanup a single node, for example `node2`

```bash
ansible-playbook --inventory-file=dev -v --sudo --limit node2 --extra-vars "@cleanup-node2-vars.json" cleanup.yml
```

- To cleanup the whole machines:

```bash
ansible-playbook --inventory-file=dev -v --sudo --extra-vars "@cleanup-all-vars.json" cleanup.yml
```
