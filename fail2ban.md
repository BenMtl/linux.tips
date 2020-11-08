# Delete all fail2ban bans
```
#     unban --all                unbans all IP addresses (in all jails and database)
#     unban <IP> ... <IP>        unbans <IP> (in all jails and database)
# example:
fail2ban-client unban --all
```
`restart <JAIL>`, `reload <JAIL>` and `reload` commands also have the `--unban` option.

# Example links
- Practical guide for fail2ban<br>
    https://www.tecmint.com/install-fail2ban-to-protect-ssh-on-centos-rhel/
