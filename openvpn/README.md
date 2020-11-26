# OpenVPN for Docker

### Quick Start

* Pick a name for the ```$OVPN_DATA``` data volume container. It's recommended to use the `ovpn-data-` prefix to operate seamlessly with the reference systemd service.  Users are encourage to replace `example` with a descriptive name of their choosing.

    OVPN_DATA="ovpn-data-example"

* Initialize the ```$OVPN_DATA``` container that will hold the configuration files and certificates.  The container will prompt for a passphrase to protect the private key used by the newly generated certificate authority.

    docker volume create --name $OVPN_DATA

    docker run -v $OVPN_DATA:/etc/openvpn --log-driver=none --rm kylemanna/openvpn ovpn_genconfig -u udp://VPN.SERVERNAME.COM

    docker run -v $OVPN_DATA:/etc/openvpn --log-driver=none --rm -it kylemanna/openvpn ovpn_initpki

* Start OpenVPN server process

    docker run -v $OVPN_DATA:/etc/openvpn -d -p 1194:1194/udp --cap-add=NET_ADMIN kylemanna/openvpn

* Generate a client certificate without a passphrase

    docker run -v $OVPN_DATA:/etc/openvpn --log-driver=none --rm -it kylemanna/openvpn easyrsa build-client-full CLIENTNAME nopass

* Retrieve the client configuration with embedded certificates

    docker run -v $OVPN_DATA:/etc/openvpn --log-driver=none --rm kylemanna/openvpn ovpn_getclient CLIENTNAME > CLIENTNAME.ovpn

* Example script to run
    # !/bin/bash
    docker-compose run --rm openvpn ovpn_genconfig -u udp://machmeier-it.de
    docker-compose run --rm openvpn ovpn_initpki

    chown -R $(whoami): ./openvpn-data

    docker-compose up -d openvpn

    export CLIENTNAME="user1"
    # with a passphrase (recommended)
    # docker-compose run --rm openvpn easyrsa build-client-full $CLIENTNAME
    # without a passphrase (not recommended)
    docker-compose run --rm openvpn easyrsa build-client-full $CLIENTNAME nopass

    export CLIENTNAME_NEXT="user2"
    # with a passphrase (recommended)
    # docker-compose run --rm openvpn easyrsa build-client-full $CLIENTNAME_NEXT
    # without a passphrase (not recommended)
    docker-compose run --rm openvpn easyrsa build-client-full $CLIENTNAME_NEXT nopass

    docker-compose run --rm openvpn ovpn_getclient $CLIENTNAME > $CLIENTNAME.ovpn
    docker-compose run --rm openvpn ovpn_getclient $CLIENTNAME_NEXT > $CLIENTNAME_NEXT.ovpn