# OpenVPN Installer for Linux
## Introduction
This script will setup a secure OpenVPN server on Ubuntu, Debian, CentOS, Fedora and Arch Linux.

## Features
*   Installs and configures a secure OpenVPN server on
    *   Amazon Linux 2 x64
    *   Arch Linux x64, arm64
    *   CentOS 7 x86, x64, armf, arm64
    *   CentOS 8 x64, arm64
    *   Ubuntu >= 18.04 x86, x64, armf, arm64
*   Automatic setup of firewall rules using iptables
*   Has many customizable options
*   Includes silent install
*   Ability to define a FQDN with OpenVPN
*   Manage OpenVPN server after install using "lmovpn" command:
    *   Add a new client
    *   List active clients
    *   Revoke existing client
    *   Debug OpenVPN using journalctl
    *   Restart OpenVPN service
    *   Uninstall OpenVPN

## Authors
*   Amin Babaeipanah

## Limitations
*   No IPv6 support

## Changelog
*   3.02:
    *   Fixed self-delete
*   3.01:
    *   Minor improvements
    *   Minor bugfixes
*   3.00:
    *   Complete rewrite
    *   Added CLI support with setup customization
    *   Added silent install with setup customization
*   2.00:
    *   Added multi distro support
    *   Minor improvements
*   1.58:
    *   Added auth-nocache to stop password caching of OpenVPN
    *   Changed deprecated ns-cert-type to --remote-cert-tls
    *   Removed unnecessary echo command
*   1.57:
    *   Minor bugfix
*   1.56:
    *   Firewall fix
*   1.55:
    *   KEY_NAME will have the same name as client
    *   KEY_CN will have the same name as client
    *   Added gateway detection. if not found, google dns will be used
    *   Automated key generation for both server and user
    *   Added openvpn restart after revoking a license
    *   Fixed “’link-mtu’ is used inconsistently” warning message
*   1.54:
    *   Changed RSA to 2048
    *   Added tls-auth and SHA256
    *   Fixed lmvpnd not revoking lics
    *   Fixed netCard variable
    *   Updated Windows client URL

## Usage
Download it using the command below and make it executeable:
```
curl -Ls https://raw.githubusercontent.com/leomoon-studios/openvpn-installer/master/src/openvpn-installer -O ~/openvpn-installer
chmod +x ~/openvpn-installer
```
Run it and follow the onscreen instructions:
```
cd ~/ && sudo ./openvpn-installer
```
After installation is done, use "sudo lmovpn" to manage your OpenVPN server.

## Silent Options
*   SILENT=[y|n]
*   PORT=[1-65535]
*   PROTOCOL=[tcp|udp]
    *   udp (default)
    *   tcp
*   DNS_TYPE=[1-11]
    *   1 = Google (global)
    *   2 = Cloudflare (global)
    *   3 = AdGuard DNS (global)
    *   4 = OpenDNS (global)
    *   5 = Quad9 (global)
    *   6 = Quad9 uncensored (global)
    *   7 = NextDNS (global)
    *   8 = FDN (France)
    *   9 = DNS.WATCH (Germany)
    *   10 = Yandex Basic (Russia)
    *   11 = Current system resolvers in /etc/resolv.conf
*   COMPRESSION=[y|n]
*   COMPRESSION_TYPE=[1-3]
    *   1 = lz4-v2 (default)
    *   2 = lz4
    *   3 = lzo
*   DATACIPHER_TYPE=[1-6]
    *   1 = AES-256-GCM (default)
    *   2 = AES-192-GCM
    *   3 = AES-128-GCM
    *   4 = AES-256-CBC
    *   5 = AES-192-CBC
    *   6 = AES-128-CBC
*   CERT_TYPE=[1-2]
    *   1 = ECDSA (default)
        *   CURVE_TYPE=[1-3]
            *   1 = prime256v1 (default)
            *   2 = secp384r1
            *   3 = secp521r1
        *   CHANNELCIPHER_TYPE=[1-2]
            *   1 = TLS-ECDHE-ECDSA-WITH-AES-128-GCM-SHA256 (default)
            *   2 = TLS-ECDHE-ECDSA-WITH-AES-256-GCM-SHA384
    *   2 = RSA
        *   RSA_TYPE=[1-3]
            *   1 = 2048 bits (default)
            *   2 = 3072 bits
            *   3 = 4096 bits
        *   CHANNELCIPHER_TYPE=[1-2]
            *   1 = TLS-ECDHE-RSA-WITH-AES-128-GCM-SHA256 (default)
            *   2 = TLS-ECDHE-RSA-WITH-AES-256-GCM-SHA384
*   DH_TYPE=[1-2]
    * 1 = ECDH
        *   DHCURVE_TYPE = [1-3]
            *   1 = prime256v1 (default)
            *   2 = secp384r1
            *   3 = secp521r1
    * 2 = DH
        *   DHSIZE_TYPE = [1-3]
            *   1 = 2048 bits (default)
            *   2 = 3072 bits
            *   3 = 4096 bits
*   HMAC_TYPE[1-2]
    *   1 = SHA-256 (default)
    *   2 = SHA-384
    *   3 = SHA-512
*   TLS_TYPE[1-2]
    *   1 = tls-crypt (default)
    *   2 = tls-auth
*   DOMAIN="domain.tld"

## Silent Install
You can also run this script silently with default options.
```
SILENT=y sudo -E ./openvpn-installer
```
Here are some examples if you want to install silently with custom options:
```
#change PORT to 2432 and PROTOCOL to tcp
SILENT=y PORT=2432 PROTOCOL=tcp sudo -E ./openvpn-installer

#enable compression and use the default COMPRESSION_TYPE if not defined
SILENT=y COMPRESSION=y sudo -E ./openvpn-installer

#change PORT to 23423, PROTOCOL to tcp and DNS_TYPE to Cloudflare
SILENT=y PORT=23423 DNS_TYPE=2 sudo -E ./openvpn-installer

#change DATACIPHER_TYPE to AES-256-CBC and CERT_TYPE to RSA
#since RSA_TYPE and CHANNELCIPHER_TYPE are not defined,
#default 2048 bits will be used for RSA_TYPE
#and TLS-ECDHE-RSA-WITH-AES-128-GCM-SHA256 will be used for CHANNELCIPHER_TYPE
SILENT=y DATACIPHER_TYPE=4 CERT_TYPE=2 sudo -E ./openvpn-installer
```

## Silent Management
You can also perform management options silently while using lmovpn. Here are some examples:

```
#add a new client
MENU=1 CLIENT=amin PASS=n sudo -E lmovpn

#add multiple clients
userlist=(desktop laptop mobile)
for user in ${userlist[@]};do
   MENU=1 CLIENT=$user PASS=n sudo -E lmovpn
done

#restart OpenVPN server
MENU=5 sudo -E lmovpn
```

## Compatibility
*   Amazon Linux 2 x64
*   Arch Linux x64, arm64
*   CentOS 7 x86, x64, armf, arm64
*   CentOS 8 x64, arm64
*   Ubuntu >= 18.04 x86, x64, armf, arm64