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




