[![Build Status](https://travis-ci.org/lbryio/aioupnp.svg?branch=master)](https://travis-ci.org/lbryio/aioupnp)
[![codecov](https://codecov.io/gh/lbryio/aioupnp/branch/master/graph/badge.svg)](https://codecov.io/gh/lbryio/aioupnp)
[![PyPI version](https://badge.fury.io/py/aioupnp.svg)](https://badge.fury.io/py/aioupnp)
[![Python 3.6](https://img.shields.io/badge/python-3.6-blue.svg)](https://www.python.org/downloads/release/python-360/)
[![Python 3.7](https://img.shields.io/badge/python-3.7-blue.svg)](https://www.python.org/downloads/release/python-370/)
[![Python 3.8](https://img.shields.io/badge/python-3.8-blue.svg)](https://www.python.org/downloads/release/python-380/)

# UPnP for asyncio

`aioupnp` is a python 3.6-8 library and command line tool to interact with UPnP gateways using asyncio. `aioupnp` requires the `netifaces` module.

## Supported devices
    Actiontec
    Airlive
    ARRIS
    ASUS
    Belkin
    Broadcom
    Cisco
    DD-WRT
    D-Link
    Huawei
    libupnp
    Linksys
    miniupnpd
    Netgear
    TP-Link
    ZyXEL


## Installation

Verify python is version 3.6-8
```
python --version
```

Installation for normal usage
```
pip install aioupnp
```

Installation for development
```
git clone https://github.com/lbryio/aioupnp.git
cd aioupnp
pip install -e .
```


## Usage

```
aioupnp [-h] [--debug_logging] [--interface=<interface>] [--gateway_address=<gateway_address>]
        [--lan_address=<lan_address>] [--timeout=<timeout>]
        [(--<case sensitive m-search header>=<value>)...]
        command [--<arg name>=<arg>]...

If m-search headers are provided as keyword arguments all of the headers to be used must be provided,
in the order they are to be used. For example:

aioupnp --HOST=239.255.255.250:1900 --MAN=\"ssdp:discover\" --MX=1 --ST=upnp:rootdevice m_search
```
cli_commands = [
    'm_search',
    'get_external_ip',
    'add_port_mapping',
    'get_port_mapping_by_index',
    'get_redirects',
    'get_specific_port_mapping',
    'delete_port_mapping',
    'get_next_mapping'
]
### Commands
    m_search | m_search | add_port_mapping | get_port_mapping_by_index | get_redirects | get_specific_port_mapping | delete_port_mapping | get_next_mapping


### Examples

#### To get the external ip address from the UPnP gateway
    
    aioupnp get_external_ip
    
#### To list the active port mappings on the gateway

    aioupnp get_redirects

#### To debug the gateway discovery

    aioupnp --debug_logging m_search

#### To debug a gateway on a non default network interface

    aioupnp --interface=vmnet1 --debug_logging m_search

#### To debug a gateway on a non default network interface that isn't the router

    aioupnp --interface=vmnet1 --gateway_address=192.168.1.106 --debug_logging m_search
    
## License

This project is MIT licensed. For the full license, see [LICENSE](LICENSE).

## Contact

The primary contact for this project is [@jackrobison](mailto:jackrobison@lbry.com)
