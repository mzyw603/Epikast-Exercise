# Epikast Exercise
IT Administrator assignment for Epikast

## Description
For this assignment we will host a website using a serverlsess service called [pico.sh](https://pico.sh/)

## Getting started
### Prerequisites
* Linux or MacOS

Windows can be used as well but, in that case we suggest running a Linux distro (ex. [Ubuntu](https://ubuntu.com/download)) on a Virtual Machine (ex. [VirtualBox](https://www.virtualbox.org/wiki/Downloads)).

### Generate a SSH key
Pico.sh is a platform based entirely on SSH. To be able to use it we need a SSH key that uses ED25519. To generate a key:
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Provide the file location of where to store the key and after that you will be asked to provide for a password to secure the key.

### Create a pico.sh account
With the SSH key connect to pico.sh:
```
ssh pico.sh
```
You may be requested for permission to proceed with the connection, after which you will be asked for the password that was provided while creating the SSH key. After you connect, provide a suitable username.

### Create a html file to upload
We will not be creating a website from scratch. We will copy the source code of https://www.karl.berlin/simplicity.html

Right click anywhere on the website (that is not a link), select "View Page Source" and copy the source code. Paste the source code in an html file in a directory of your choosing (ex. "~/epikast/public/Exercise in Simplicity.html").

"Exercise in Simplicity v2.html" is the same website but with changed banner color from blue to red.

### Upload the website
Once the file with the website is created simply execute the following command if already inside the directory with the html file:
```
rsync -rv ./ pgs.sh:/sites
```
Alternatively you can use the full path to the folder. For our example we can use
```
rsync -rv ~/epikast/public/ pgs.sh:/sites
```
**Note**: "sites" is the project name and can be changed to anything as long as it only contrains lower case letters (a-z) and numbers (0-9).

With that all the HTML files in the provided directory are uploaded.

### Find the SSH public key
Last thing is to add our public SSH key to a file in the the repo. If you saved the key in the default location use
```
cat ~/.ssh/id_ed25519.pub
```
to print the key in the terminal. We pasted ours in additional/public_key.txt. If you saved the key initially somewhere else change the file path accordingly.

## Additional Content
Links to the pages that were created
* [Exercise in Simplicity](https://matzyw-sites.pgs.sh/Exercise%20in%20Simplicity.html)
* [Exercise in Simplicity v2](https://matzyw-sites.pgs.sh/Exercise%20in%20Simplicity%20v2.html)

Documentation can be found [here](https://drive.google.com/file/d/1tJ8olRhbAh7JfSpC1C7VBGrtVNleP-zX/view?usp=sharing).
