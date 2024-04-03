# Sina Kashanchi #A01344903
# nginx-2420

# Step 1: Installing Necessary Software

First, update your package lists to ensure you can install the latest versions of the software:


`sudo pacman -Syu`

Then, install Nginx and Vim:


`sudo pacman -S nginx`
`sudo systemctl start nginx`
`sudo systemctl enable nginx`

`sudo pacman -S vim`
`sudo systemctl start vim`
`sudo systemctl enable vim`

# Step 2: Creating a Project Directory

Create a new directory for your website files. This guide uses /web/html/nginx-2420 as the project root:


`sudo mkdir -p /web/html/nginx-2420`

# Step 3: Adding Your HTML Document

Place your HTML document


`sudo vim /web/html/nginx-2420/index.html`

We paste the provided HTML content into the file, save, and exit the editor.
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

# Step 5: Managing the Nginx Service

Reload Nginx to apply the changes:


`sudo systemctl reload nginx`

Ensure Nginx starts on boot:

`sudo systemctl enable nginx`

# Step 6: Oprn broswer and go to IP address of server

Type `http://64.23.162.251/`

And you should able to see this on your screen:
