# OpenVPN Ubuntu Installer
## Introduction

Having your own self hosted OpenVPN is very important these days but setting one up can be very tedious! This script makes it very easy for anyone to setup their own OpenVPN server at home.

## Features

*   Automatic setup of OpenVPN Server on Ubuntu 16.04
*   Automatic setup of firewall rules using iptables
*   Supports both desktop and server versions of Ubuntu
*   Can be installed on VPS or home internet
*   Adds new commands to easily mange your OpenVPN server

## Donations

Future development of this project depends on community donations. All proceeds will go towards the development. You can donate using [[THIS LINK]](https://www.paypal.me/aminpersia) and make sure to include which project you want to support.

## Donors

*   NA

## Programmers

*   Amin Babaeipanah

## Changelog

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

## How to install

1.  Download and extract ovpnSetup to your Ubuntu machine
2.  Change the variables in VARIABLES TO CHANGE section and save
3.  Make it executable by running the command below

*   chmod +x ovpnSetup

5.  Run it using the command below

*   sudo ./ovpnSetup

7.  Follow the instructions
8.  You can use the commands below to manage your OpenVPN server

*   To add a client use: sudo lmvpna
*   To deactivate a client use: sudo lmvpnd
*   To list all licenses use: sudo lmvpnl
*   To restart OpenVPN server use: sudo lmvpnr
*   To see realtime status of OpenVPN for debugging use: sudo lmvpns

## Future ideas

*   NA

## Compatibility

Ubuntu 16.04
