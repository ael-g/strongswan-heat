# strongswan-heat
Openstack Heat template to deploy a strongswan IPSec VPN

## Usage
```
stack create -t https://github.com/ael-g/strongswan-heat/vpn.yml --parameter user=ael --parameter password=strongPSK --parameter public-network=public --parameter private-network=private --parameter flavor=t1.tiny --parameter=image Ubuntu vpn
```

Once created the template will deploy a VM (whose image should be debian-like because of apt usage) with strongswan installed and provisioned with *user* and *password* passed in parameters.
It will associate a floating IP from network parameter *public-network* and add a private interface on network *private-network*.

**You'll still have to add firewall rules to allow port 500 and 4500 for UDP proto on the Floating IP**

An *ipsec.conf* file is provided for client side configuration (password should be set in *ipsec.secrets*)
