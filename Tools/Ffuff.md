# Ffuf

Note that FFuF works slightly differently than Gobuster's DNS mode - it makes HTTP requests rather than DNS lookups, so it's testing if the webserver responds to the subdomain, not if the subdomain actually resolves in DNS. However, these is a workaround: `ffuf -w subdomains-top1million-20000.txt -u http://planning.htb/ -H "Host: FUZZ.planning.htb" -mc all`
