# 21 - SSH (Secure Socket Shell)
- https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-ssh.html
- https://github.com/jtesta/ssh-audit
- Known bad keys: https://github.com/rapid7/ssh-badkeys/tree/master/authorized
- https://github.com/MegaManSec/SSH-Snake
## Commands
- Login - `ssh username@host`
- Login with SSH Key - `ssh -i /path/to/private_key username@host`
- Create new SSH key pair - `ssh-keygen -t rsa -b 4096`
- Execute command without logging in - `ssh username@host "command"`
- Check auth methods of SSH - `nmap -p22 --script ssh-auth-methods <TARGET-IP>`

### Have an SSH port?
 - What version of SSH is running?
   - `nmap -p 22 --script ssh2-enum-algos,ssh-hostkey,sshv1 <IP>`
   - `nc <IP> 22`
 - Are there any known vulnerabilities for the SSH version?
   - `searchsploit OpenSSH <VERSION>`
   - `msfconsole search OpenSSH`
 - Can I enumerate valid usernames?
   - `hydra -L users.txt -p test123 ssh://<IP> -V`

## Notes
- An SSH connection is typically much more stable than a reverse shell connection and can often be used as a "jump host" to enumerate and attack other hosts in the network, transfer tools, set up persistence, etc
