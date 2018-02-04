# OpenVPN
Docker image for OpenVPN server.

## Usage
The NET_ADMIN capability is required for running the image `--cap-add NET_ADMIN`.

For IPv6, add the following sysctls with the `--sysctl` flag
* net.ipv6.conf.all.disable_ipv6=0
* net.ipv6.conf.default.forwarding=1
* net.ipv6.conf.all.forwarding=1

## Get client certificate
Export client certificate by running

    docker exec <CONTAINER_ID> export-client <CLIENT_NAME> > client.ovpn

A default certificate called `client` is generated on server startup, but you
can generate more by exec-ing into the container and running

    source vars
    ./pkitool <CLIENT_NAME>
