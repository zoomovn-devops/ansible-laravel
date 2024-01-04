# ansible-laravel

### Deploy Laravel Using Ansible

#### Copy ssh private key for ssh into server:

```
cp {your_server_ssh_key} ssh_key/id_rsa
```

#### Copy deploy key of github:

```
cp {your_github_deploy_key} scm_key/id_rsa
```

#### Setting source code directory and source version control:

`group_vars/all.yml`

#### Edit web server IP, SSH port:

`production.yml` or `staging.yml`

#### Run deploy command:

```
ansible-playbook -i production  main.yml
```
or

```
ansible-playbook -i staging main.yml
```

#### Create webserver with docker

```
docker run --name server-production \
    -p 8023:22 -p 8080:80 -p 8443:443 \
    -e AUTHORIZED_KEYS="ssh-rsa ---------- KEY ----------" \
    -e ROOT_PASSWORD="zoomo886Aa@" \
    -d toantd14/ubuntu-server
```
