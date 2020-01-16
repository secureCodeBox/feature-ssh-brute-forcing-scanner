---
title: 'Nrack'
path: 'scanner/Nrack'
category: 'scanner'
usecase: 'Network Scanner'
release: 'https://img.shields.io/github/release/secureCodeBox/scanner-infrastructure-nrack.svg'
---

![Nrack logo](https://nmap.org/ncrack/images/ncrack_logo.png)

> "Ncrack is a high-speed network authentication cracking tool. It was built to help companies secure their networks by proactively testing all their hosts and networking devices for poor passwords. Security professionals also rely on Ncrack when auditing their clients. Ncrack was designed using a modular approach, a command-line syntax similar to Nmap and a dynamic engine that can adapt its behaviour based on network feedback. It allows for rapid, yet reliable large-scale auditing of multiple hosts. Ncrack's features include a very flexible interface granting the user full control of network operations, allowing for very sophisticated bruteforcing attacks, timing templates for ease of use, runtime interaction similar to Nmap's and many more. Protocols supported include SSH, RDP, FTP, Telnet, HTTP(S), Wordpress, POP3(S), IMAP, CVS, SMB, VNC, SIP, Redis, PostgreSQL, MQTT, MySQL, MSSQL, MongoDB, Cassandra, WinRM, OWA, and DICOM " https://nmap.org/ncrack/

<!-- end -->

# About

This repository contains a self contained µService utilizing the Ncrack Credential scanner for the secureCodeBox project. To learn more about Ncrack itself visit [https://nmap.org/ncrack/].

## Example

Example configuration:

```json
[
    {
        "name": "ncrack",
        "context": "SSH Credential Scans",
        "target": {
            "name": "Local SSH",
            "location": "ssh://192.168.0.1",
            "attributes": {
                "NCRACK_PARAMTER": "--user root --pass 123456"
            }
        }
    }
]
```

Example Output:

```json
{
    "findings": [
        {
            "name": "Credentials for Service ssh://192.168.0.1:22 discovered via bruteforce.",
            "description": "",
            "location": "ssh://192.168.0.1:22",
            "category": "Discovered Credentials",
            "severity": "HIGH",
            "osi_layer": "APPLICATION",
            "attributes": {
                "username": "root",
                "password": "123456",
                "ip_address": "192.168.0.1",
                "port": "22",
                "protocol": "tcp",
                "service": "ssh"
            }
        }
    ]
}
```

## Development

### Configuration Options

To configure this service specify the following environment variables:

| Environment Variable       | Value Example |
| -------------------------- | ------------- |
| ENGINE_ADDRESS             | http://engine |
| ENGINE_BASIC_AUTH_USER     | username      |
| ENGINE_BASIC_AUTH_PASSWORD | 123456        |

### Local setup

1.  Clone the repository
2.  Install the dependencies `npm install`
3.  Run locally `npm start`

### Test

To run the testsuite run:

`npm test`

### Build with docker

To build the docker container run: `docker build -t CONTAINER_NAME:LABEL .`

[![Build Status](https://travis-ci.com/secureCodeBox/scanner-infrastructure-ncrack.svg?branch=master)](https://travis-ci.com/secureCodeBox/scanner-infrastructure-ncrack)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Known Vulnerabilities](https://snyk.io/test/github/secureCodeBox/scanner-infrastructure-ncrack/badge.svg)](https://snyk.io/test/github/secureCodeBox/scanner-infrastructure-ncrack)
[![GitHub release](https://img.shields.io/github/release/secureCodeBox/scanner-infrastructure-ncrack.svg)](https://github.com/secureCodeBox/scanner-infrastructure-ncrack/releases/latest)
