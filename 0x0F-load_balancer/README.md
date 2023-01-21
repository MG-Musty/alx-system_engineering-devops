# 0x0F LOAD_BALANCER


### More info
[Shellcheck](https://github.com/koalaman/shellcheck) is a tool that will help you write proper Bash scripts. It will make recommendations on your syntax and semantics and provide advice on edge cases that you might not have thought about. Shellcheck is your friend! **All your Bash scripts must pass ``Shellcheck`` without any error or you will not get any points on the task**. Also, for every feedback, Shellcheck will provide a code that you can use to get more information about the issue, for example for code ``SC2034``, you can browse [https://github.com/koalaman/shellcheck/wiki/SC2034](https://github.com/koalaman/shellcheck/wiki/SC2034).
``Shellcheck`` is available on the school’s computers. If you want to use it on your own computer, here is how to [install it](https://github.com/koalaman/shellcheck#installing).

# SOLUTION GETTING THE CONFIGURATION TO THE WEB_SERVER-02

Make sure you `cd 92429-lb-01 server` example `ssh ubuntu@ip_address`.

### Step 1) Install HAProxy Load Balancer

```
$ sudo apt update
$ sudo apt show haproxy
```

![image](https://user-images.githubusercontent.com/106968663/213882857-4193c4a0-37eb-4f0b-90c2-19e05eabc100.png)

* But the latest long term support release is HAProxy is 2.6, So to install HAProxy 2.6, first enable PPA repository, run following command

```
$ sudo add-apt-repository ppa:vbernat/haproxy-2.6 -y
```

* Now install haproxy 2.6 by executing the following commands

```
$ sudo apt update
$ sudo apt install -y haproxy=2.6.\*
```

* Once installed, confirm the version of HAProxy installed as shown

```
$ haproxy -v
```

![image](https://user-images.githubusercontent.com/106968663/213885697-2f06bfbd-5e67-4402-95ca-b407613799de.png)


* Upon installation, the HAProxy service starts by default and listens to TCP  port 80. To verify HAProxy is running, run the command

```
$ sudo systemctl status haproxy
```

![image](https://user-images.githubusercontent.com/106968663/213885761-6a6feec9-c360-4507-9592-09973f578785.png)


* It’s recommended to enable the service to auto-start on very system reboot as shown.

```
$ sudo systemctl enable haproxy
```

### Step 2) Configure HAProxy

* The next step is to configure HAProxy to distribute traffic evenly between two web servers. The configuration file for haproxy is `/etc/haproxy/haproxy.cfg`.

* Before making any changes to the file, first, make a backup copy.

```
$ sudo cp /etc/haproxy/haproxy.cfg /etc/haproxy/haproxy.cfg.bk
```

* Then open the file using your preferred text editor. Here, we are using Nano

```
$ sudo nano /etc/haproxy/haproxy.cfg
```

### Haproxy configuration file is made up of the following sections:

* **global**: This is the first section that you see at the very top. It contains system-wide settings that handle performance tuning and security.
* **defaults**: As the name suggests, this section contains settings that should work well without additional customization. These settings include timeout and error reporting configurations.
* **frontend and backend**: These are the settings that define the frontend and backend settings. For the frontend, we will define the HAProxy server as the front end which will distribute requests to the backend servers which are the webservers. We will also set HAProxy to use round robbin load balancing criteria for distributing traffic.
* **listen**: This is an optional setting that enables you to enable monitoring of HAProxy statistics.

### Now define the frontend and backend settings:

```
frontend linuxtechi
   bind *:80
   model http
   stats uri /haproxy?stats
   default_backend web-servers

backend web-servers
    balance roundrobin
    server 12345-web1 10.128.0.27:80 check
    server 12345-web2 10.128.0.26:80 check
```

* In order to enable viewing the HAProxy statistics from a browser, add the following `‘listen’ section`.

```
listen stats
   bind *:8080
   stats enable
   stats uri /
   stats refresh 5s
   stats realm Haproxy\ Statistics
   #stats auth linuxtechi:P@ss123-(Not neccessary)     #Login User and Password for the monitoring
```

![image](https://user-images.githubusercontent.com/106968663/213886155-5146d9aa-ca2d-4c8a-8957-90c937315ac2.png)

* Now save all the changes and exit the configuration file. To reload the new settings, restart haproxy service.

```
$ sudo systemctl restart haproxy
```

* Next edit the `/etc/hosts` file.

```
$ sudo /etc/hosts
```

* Define the hostnames and IP addresses of the haproxy main server and the webservers.

```
10.128.0.25 haproxy
10.128.0.27 web1
10.128.0.27 web2
```

* Save the changes and exit.

### Step 3) Configure Web Servers.

* In this step, we will configure the remaining Linux systems which are the web servers.

* So, log in to each of the web servers `(web-01, web-02)` and install the Nginx web server package using Ubuntu.

* To install nginx, run the following commands:

```
$ sudo apt update
$ sudo apt install nginx
```

* Install the prerequisites:

```
$ sudo apt install curl gnupg2 ca-certificates lsb-release ubuntu-keyring
```


# 📚 Author 🖋️

[Mustapha Aliyu Galadima](https://github.com/MG-Musty/)
