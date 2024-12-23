# How-To-Setup-FTP-Access

You need to be outside of any folder or file or  directory and You must Be in root user mode ``sudo -s`` or ``sudo su``.

# Create User:
```sudo useradd -d /var/www username```

# Set a Password:
```sudo passwd username```

# Set directory permission for the user:
```nano /etc/ssh/sshd_config```

# Paste the lines:
`subsystem sftp internal-sftp` #(Ignore this line if it is already there in the file, just uncomment the exsisting line.) <br> 
`Match User username`<br>
`   ChrootDirectory %h`<br>
`   AllowTCPForwarding no`<br>
`   X11Forwarding no`<br>
`   ForceCommand internal-sftp`<br>

# Image
![Image](https://i.postimg.cc/SR5JxmGX/304946863-036215e0-3976-49d9-9da1-879dff28139a.png)

# Set permission(important):
```sudo chown -R username:username /var/www/pterodactyl```
```sudo chmod -R 755 /var/www/pterodactyl```

# Restart the SSH:
```sudo service ssh restart```
```sudo systemctl restart sshd```



> [!NOTE]
> The Port `22` Shoud Be Opened In The Firewall.
> 
