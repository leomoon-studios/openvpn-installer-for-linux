# Changelog

## 3.1.2 (2024-10-23)

- Add tag-triggered GitHub releases

## 3.1.1 (2024-08-03)

- Added 10-year certificate validity
- Fixed the Rocky Linux version check

## 3.1.0 (2023-08-15)

- Enabled EPEL for Oracle Linux
- Added a retry when using curl to get the WAN IP address
- Added `--no-same-owner` when extracting Easy-RSA
- Added DNS lookup when icanhazip fails
- Added support for CentOS 9
- Updated Easy-RSA from 3.0.7 to 3.1.2, with minor fixes
- Removed unnecessary removal of hardcoded ciphers on Fedora
- Fixed the OpenVPN uninstall option text
- Fixed the OpenVPN uninstall option on non-Ubuntu distributions

## 3.05 (2021-09-04)

- Added compatibility with AlmaLinux 8
- Added compatibility with Rocky Linux 8
- Added compatibility with Oracle Linux 8
- Fixed compatibility with RHEL and EPEL
- Minor improvements

## 3.04 (2021-01-13)

- Increased sysctl priority
- Fixed AdGuard IP addresses
- Fixed the `key-direction` setting from `tls-crypt`

## 3.03

- Fixed the OpenVPN service path
- Minor fix for the OpenVPN uninstall function

## 3.02

- Fixed self-delete

## 3.01

- Minor improvements
- Minor bug fixes

## 3.00

- Complete rewrite
- Added CLI support with setup customization
- Added silent installation with setup customization

## 2.00

- Added multi-distribution support
- Minor improvements

## 1.58

- Added `auth-nocache` to stop password caching
- Replaced deprecated `ns-cert-type` with `--remote-cert-tls`
- Removed an unnecessary `echo` command

## 1.57

- Minor bug fix

## 1.56

- Firewall fix

## 1.55

- Used the client name for `KEY_NAME` and `KEY_CN`
- Added gateway detection, with Google DNS as a fallback
- Automated server and client key generation
- Restarted OpenVPN after revoking a license
- Fixed the “`link-mtu` is used inconsistently” warning

## 1.54

- Changed RSA to 2048 bits
- Added `tls-auth` and SHA-256
- Fixed `lmvpnd` not revoking licenses
- Fixed the `netCard` variable
- Updated the Windows client URL