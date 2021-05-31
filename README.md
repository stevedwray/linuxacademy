There are two playbooks, one for puppet enterprise, the other for puppet opensource.

To build PE master:
ansible-playbook -i inventory/puppet_enterprise.yml ./pe_lab.yml --ask-vault-pass --tags pe_master --skip-tags pe_node
Once master is built, build nodes:
ansible-playbook -i inventory/puppet_enterprise.yml ./pe_lab.yml --ask-vault-pass --tags pe_node --skip-tags pe_master

This one builds opensource:
ansible-playbook -i inventory/puppet_opensource.yml ./po_lab.yml --ask-vault-pass --tags po_master --skip-tags po_node

The Opensource playbook is less stable than the Enterprise one.

You will want to change the vault in:
roles/pe_master/vars/vault
It contains the variable which sets the password for the PE web interface:
vault_puppet_console_admin_password
Used in:
roles/pe_master/templates/master_pe.conf.j2
