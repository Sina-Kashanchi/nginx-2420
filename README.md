# Sina Kashanchi #A01344903
# nginx-2420 Assignment 3 Part 1

# Step 1: Installing Necessary Software

First, update your package lists to ensure you can install the latest versions of the software:


`sudo pacman -Syu`
![image](https://github.com/Sina-Kashanchi/nginx-2420/assets/148367803/918c993d-e1d4-4f49-b3da-4d34602d1e02)


Then, install Nginx and Vim:


`sudo pacman -S nginx`
`sudo systemctl start nginx`
`sudo systemctl enable nginx`
![image](https://github.com/Sina-Kashanchi/nginx-2420/assets/148367803/540c191e-1749-4d31-9ead-9c424a4bc15d)
Then we check the status of nginx service:

`sudo systemctl status nginx`

![image](https://github.com/Sina-Kashanchi/nginx-2420/assets/148367803/2fa2380a-3c0f-49d7-a435-bb8d1744405a)


# Step 2: Creating a Project Directory

Create a new directory for your website files. This guide uses /web/html/nginx-2420 as the project root:

`sudo mkdir -p /web/html/nginx-2420`

# Step 3: Adding Your HTML Document

Place your HTML document

`sudo vim /web/html/nginx-2420/index.html`

We paste the provided HTML content into the file, save, and exit the editor.

![image](https://github.com/Sina-Kashanchi/nginx-2420/assets/148367803/fcdbaed6-6e82-42c1-ab32-ab6c8bf96aaa)

# Step 4: Configuring Nginx
Creating a Server Block

Nginx configuration for your project should be in its own file, not in the main nginx.conf. Create a new configuration file in /etc/nginx/sites-available and symlink it to /etc/nginx/sites-enabled to enable it:


`sudo mkdir -p /etc/nginx/sites-available /etc/nginx/sites-enabled`

`sudo vim /etc/nginx/sites-available/nginx-2420`

Add the following configuration, adjusting paths as necessary:

# nginx-2420.conf
```
server {
    listen 80;
    server_name 64.23.162.251;

    root /web/html/nginx-2420;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```


Enable this configuration by creating a symlink:


`sudo ln -s /etc/nginx/sites-available/nginx-2420 /etc/nginx/sites-enabled/`

Updating Nginx Configuration to Include Server Blocks

Edit the main Nginx configuration file to include enabled server blocks:

`sudo vim /etc/nginx/nginx.conf`

Add this line within the http block:

`include /etc/nginx/sites-enabled/*;`

![image](https://github.com/Sina-Kashanchi/nginx-2420/assets/148367803/fcd34334-d9da-464a-8b9b-65ab63f4b990)

# Step 5: Managing the Nginx Service

Reload Nginx to apply the changes:


`sudo systemctl reload nginx`

Ensure Nginx starts on boot:

`sudo systemctl enable nginx`

# Step 6: Open your  browser and go to the IP address of the server

Type `http://64.23.162.251/`

And you should able to see this on your screen:

![Screenshot (289)](https://github.com/Sina-Kashanchi/nginx-2420/assets/148367803/1cc05f41-779f-40ef-a5e9-30796cef8deb)
