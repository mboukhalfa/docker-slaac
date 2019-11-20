# docker-slaac

## ovs
### Install
`sudo apt-get install openvswitch-switch`
### Add bridge
`sudo ovs-vsctl add-br br0`

## LXD
### Install
`sudo apt-get install LXD`
### Initial configuration 
`sudo lxd init`

### Create profile
LXD profile contains the network Initialization
 1. copy default profile
 `sudo lxc profile copy default new_profile`
 2. edit new profile to add ovs-bridge check file: new_profile[a relative link](new_profile)
 `sudo lxc profile edit new_profile`
### Launch LXD

`sudo lxc launch ubuntu:16.04 container1`

`sudo lxc launch ubuntu:16.04 container2`

### Add ip address to containers
`sudo lxc exec container1 ip addr add 10.0.0.1/24 dev eth1`

`sudo lxc exec container2 ip addr add 10.0.0.2/24 dev eth1`
## Check container connection
`sudo lxc exec container1 ping 10.0.0.2`

## It works ! solve the ipv6 problem
### hint

http://containertutorials.com/network/ovs_docker.html
