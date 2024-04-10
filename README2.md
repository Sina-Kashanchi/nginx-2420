# Sina Kashanchi #A01344903
## nginx-2420 Assignment 3 Part 2
### Adding Firewall and Reverse Proxy

- Note: Update packages before you start
`pacman -Syu`

# Step 1: Setting Up UFW 
- Installing UFW:

`sudo pacman -S ufw`

## Configuring UFW

- Before enabling the firewall, set the default rules:


```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```
![image](https://github.com/Sina-Kashanchi/nginx-2420/assets/148367803/4881a453-68f6-416b-ad53-223896eab1ab)

- This configuration denies all incoming connections by default and allows all outgoing connections, enhancing security. Now, allow specific services:

- Enable basic firewall rules, allowing SSH connections to ensure you don't lock yourself out, and allowing HTTP/HTTPS traffic for your Nginx server:

``` bash
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https
```

![image](https://github.com/Sina-Kashanchi/nginx-2420/assets/148367803/3f108174-2bf7-4003-b446-bb7a03fcb7cb)

#### Enable UFW:

`sudo ufw enable`


Check the status to ensure it's active and the rules are applied:

`sudo ufw status`

![image](https://github.com/Sina-Kashanchi/nginx-2420/assets/148367803/cbb9a317-cad0-42e9-ac00-4ae7ca91396f)


# Step 2: Preparing the Backend Service

- Create a new systemd service file:


`sudo vim /etc/systemd/system/hello-server.service`

- Populate the file with the following:

```bash
[Unit]
Description=Hello Server Backend

[Service]
ExecStart=/usr/local/bin/hello-server
Restart=always
User=www-data
Group=www-data

[Install]
WantedBy=multi-user.target
```
- Enable and start the service:

`sudo systemctl enable hello-server`
`sudo systemctl start hello-server`

# Step 3: Configuring Nginx for Reverse Proxy

Edit your Nginx server block configuration to reverse proxy requests to the backend:



![image](https://github.com/Sina-Kashanchi/nginx-2420/assets/148367803/e925f371-3b2e-492a-b5b4-9925a675d473)


`sudo vim /etc/systemd/system/hello-server.service`

Modify the server block created in Part 1 to reverse proxy requests to the backend.

`sudo vim /etc/nginx/sites-available/nginx-2420`




