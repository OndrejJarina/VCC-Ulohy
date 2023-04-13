# NI-VCC Úloha 1

### Nasadenie OpenStacku
Pri nasadení OpenStacku som postupoval hlavne podľa návodu v [dokumentácii OpenStacku](https://docs.openstack.org/kolla-ansible/zed/user/quickstart.html).
1. Nainštaloval som potrebné packages a vytvoril virtuálne prostredie
```
sudo apt update
sudo apt upgrade
sudo apt install python3-venv
python3 -m venv python-venv
source python-venv/bin/activate
pip install -U pip
```

2. Nainštaloval som ansible a kolla-ansible

```
pip install 'ansible>=4,<6'
pip install git+https://opendev.org/openstack/kolla-ansible@stable/zed

sudo mkdir -p /etc/kolla
sudo chown $USER:$USER /etc/kolla

cp -r python-venv/share/kolla-ansible/etc_examples/kolla/* /etc/kolla

cp python-venv/share/kolla-ansible/ansible/inventory/* .
```
