

# how to configure NGINX when hosting an Angular application so that refreshing a page does not give you a 404 error

# Issue Demonstration:
Refreshing the same page results in a 404 error

# Steps to Fix the Issue:

# 1. Connect to the Server:

Use SSH to connect to the server

```bash
ssh your_user@your_server_ip

```
example : ssh admin@192.168.1.100

# 2. Edit Nginx Configuration:

# Navigate to the configuration directory:

```bash
cd /etc/nginx/sites-enabled/

```
# List the files to find your domain's config file

```bash
ls

```
example :  skipabit.com.conf , default


# Open the configuration file 

```bash
sudo nano yourdomain.com.conf

```
example :

```bash
sudo nano skipabit.com.conf

```
# Add this code inside the location / {} block

```bash
try_files $uri $uri/ /index.html;

```
# 3. Save the changes to the configuration file.

Press Ctrl + O     (the letter O, not zero)

Confirm the file name by pressing Enter.

# Exit nano:
Press Ctrl + X.


# 4.  Restart Nginx:

# Restart Nginx to apply the changes

```bash
sudo systemctl reload nginx.service

```
# Optionally, check Nginx status

```bash
sudo systemctl status nginx.service

```
# 4. Verification:

Perform a hard refresh on the website to ensure the issue is resolved.

Navigate to different pages and refresh to confirm that the 404 error no longer occurs.




