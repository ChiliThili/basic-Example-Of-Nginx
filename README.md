# This is a basic Project with NGINX
In this Project I will bring you near to NGINX and how you can create projects. You should have a bit of an understanding of HTML, CSS and JAVASCRIPT if you don't. Please consider looking for a free course on any Website for example w3schools.com. You will learn in this Example:
* How NGINX can be used to create a simple project
* How we use file navigation in NGINX
* How we create a reverse Proxy
* And More

## Installation
  The installation of NGINX is pretty easy for anyone who has an unix/gnu-based OS if you use Windows you should look for the installation     here https://nginx.org/en/docs/windows.html
  * Arch: sudo pacman -S nginx
  * Ubuntu: sudo apt-get install nginx
  * Fedora: sudo dnf install nginx
  * Mac: brew install nginx
  * Mac(MacPorts): sudo port install nginx
  * For other Distros look up the nginx page here: https://nginx.org/en/

## Setting up
  First, we need to see if NGINX works so (on Mac) we type nginx | (on Linux) sudo systemctl start nginx.service in the Terminal. Then you should start your browser and visit the localhost:8080 Site or the localhost:80 Site. If you get the Error: PORT IS IN USE please look if you have Apache installed or any other program that uses a port of these please stop them or wait because I will explain how to avoid this problem later. 
  The Problem could also be that you have just started nginx twice. Then it won't be a problem for you and will work just fine.
  
## Creating the Project  
After that go to the Folder /usr/local/etc/nginx or if not exist /etc/nginx in this folder you will find many files in there but the needed one is nginx.conf. Erase all the code in there and paste the code (in this Repo) with it. If you are done with that create a html file where ever you want and copy the path to the directory. Paste the copied dir into the root in the location context. And do nginx -s restart or systemctl restart nginx.service (This is the command you need if you change the nginx.conf file)

## Explenation
How does this work? This a good question because it isn't very easy to understand this in NGINX we call things that have {} after **context** and lines without **directives** http is where you define everything(unless it's smth like events). Server contexts are the servers where server-specific code is defined for example the **port** and the **name** it is running on with listen **port**; and server_name **name**; in here is also the Location context that defines obviously the location of the html php or htm file. Here you can define the root directive and this is the location of your dir to your PHP html or etc. The / in the Location refinement is if you want to locate the _name: port/_ of your website. You can add another location so you get to another page if you type _name:port/example_. The index directive is for NGINX to get what index._whatever_ you have just add index._whatever_ to this file. In this example I created another server(reverse_proxy) that is for connecting to the _othername:otherport_ you get to the _name:port_ website. You then just add to the proxy_pass directive _name: port_ so it looks like this _proxy_pass name:port_. After that everytime you connect to the second server you will get the content of the first server.

## Conclusion
NGINX is a powerful tool to build websites it is even used for websites like Twitch or Instagram. I hope with this example I could bring you NGINX a bit nearer of course this is not the bottom of the Iceberg and if you want to get there you need way more than this. But with what you learned today you can talk with these guys at the NGINX party.
