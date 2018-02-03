## Sobre ##

Provisionamento do Openshift-origin na Azure usando ansible

## Requisitos ##

* Ansible 2.4
* Azure CLI 2.0 (pip install azure)
* Azure SDK modules (pip install ansible[azure])
* Conta Azure (com uma subscrição ativa)

## O que será criado ? ##

* Azure
    * Resource Group
    * Keyvault
    * Keyvault Secret
    * App Azure
    * Openshift Origin Deployment

## Pré-execução ##

* Gerando uma SSH key para o Openshift

```
ssh-keygen -f ~/.ssh/openshift_rsa -t rsa -N ''
```

* Configurando suas credenciais Azure em $HOME/.azure/credentials

> OBS: Recomendado a criação de uma conta no Azure Active Directory para uso exclusivo do Ansible, conforme documentação:
> http://docs.ansible.com/ansible/latest/guide_azure.html

```
[default]
ad_user=xxxxxxxxxxxxxxxxxxxxxxxxxxxx
password=xxxxxxxxxxxxxxxxxxxxxxxxxxx
subscription_id=xxxxxxxxxxxxxxxxxxxx
```
* Configurando parâmetros do Azure e Openshift:

```
group_vars/all.yaml
```

### Executando ###

* Exemplo:

```
ansible-playbook -i azure_rm.py playbooks/site.yaml
```