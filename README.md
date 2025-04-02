# k8s_gitlab_lab

1. Run vagrant:
```bash
vagrant up
```

It's also install dnsmasq server automatically.

2. Install kubespray
```bash
ansible-galaxy install -r ansible/roles/kubespray/requirements.yml
```

3. Make enviroment for ansible and kubespray
```bash
python3 -m venv .kubespray
source .kubespray/bin/activate
pip install -U -r ansible/roles/kubespray/requirements.txt
pip install ruamel.yaml
export ANSIBLE_LIBRARY=./.kubespray/lib/python3.11/site-packages/ansible/modules
export ANSIBLE_MODULE_UTILS=./.kubespray/lib/python3.11/site-packages/ansible/module_utils
export PYTHONPATH=./.kubespray/lib/python3.11/site-packages:$PYTHONPATH
```

4. Run playbook

```bash
ansible-playbook -i ansible/roles/kubespray/inventory/kubernetes.dev.local/hosts.yml --become --become-user=root ansible/playbook/kubernetes.yml
```