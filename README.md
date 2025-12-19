# check-opnsense

## How to install

SSH into your OPNsense:
```
fetch -o /usr/local/etc/rc.syshook.d/start/99-checkmk_agent https://github.com/ane-energy/checkmk-opnsense-agent/raw/main/opnsense_checkmk_agent.py
chmod +x /usr/local/etc/rc.syshook.d/start/99-checkmk_agent
/usr/local/etc/rc.syshook.d/start/99-checkmk_agent
```

Ensure you create a packet filter rule to allow connections from your checkmk server to the firewall on port 6556.

## Checks

### Agent sections

- **apcupsd**
- **cpu**
- **df**
- **dhcp**
- **disk_smart_info**
- **haproxy**
- **ipmi**
- **kernel**
- **labels**
- **mounts**
- **netctr**
- **ntp**
- **ps**
- **squid**
- **sshd_config**
- **statgrab_mem**
- **statgrab_net**
- **tcp_conn_stats**
- **uptime**
- **zfs_arc_cache / zfsget**
- **zpool_status**
- **lnx_thermal**

### Local checks

- **ACME Cert** (`checklocal_acmeclient`)
- **Business Licence** (`checklocal_business`)
- **CARP** (`checklocal_carpstatus`)
- **CMK Tasks** (from task spool in `TASKDIR`)
- **Firmware** (`checklocal_firmware`)
- **Gateway** (`checklocal_gateway`)
- **IPsec Tunnel** (`checklocal_ipsec`)
- **IPsec Tunnel (swanctl)** (`checklocal_ipsec_new`)
- **Nginx** (`checklocal_nginx`)
- **OpenVPN Client/Server/Connection** (`checklocal_openvpn`)
- **Pkg Audit** (`checklocal_pkgaudit`)
- **Services** (`checklocal_services`)
- **Unbound DNS** (`checklocal_unbound`)
- **WireGuard Client** (`checklocal_wireguard`)

## Service blacklist

The local check **Services** supports a service blacklist file at:

`/usr/local/etc/checkmk_service_blacklist.conf`

If present, each non-empty, non-comment line is treated as a blacklisted entry. A service is considered blacklisted if either its service **name** or **description** matches an entry in this file.
