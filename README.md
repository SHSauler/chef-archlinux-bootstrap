# chef-archlinux-bootstrap

Bootstrapping `chef-client` in Arch Live environment.

## Prep steps

* Needs a Chef server. This docker image works for me: https://hub.docker.com/r/cbuisson/chef-server/
* `chef-dk` must be deployed on your workstation. It's in AUR.

### On the node

* Boot the Arch iso
* Check that you have a internet connection
* Set root passwd (`passwd root`)
* Start SSH daemon (`systemctl start sshd`)
* Note IP of node (`ip addr`)


### On the workstation

* Put `archlinux-chef-client.erb` in `.chef/bootstrap`

```
knife bootstrap <node_ip/node_hostname> --ssh-user root --node-name <node_name> -t archlinux-chef-client`

Example:
knife bootstrap 192.168.56.101 --ssh-user root --node-name arch01 -t archlinux-chef-client
```
