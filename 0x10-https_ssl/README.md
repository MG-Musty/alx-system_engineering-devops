# 0x10. HTTPS SSL

## Resources:books:
Read or watch:
* [What is HTTPS?](https://intranet.hbtn.io/rltoken/pawxG_0c1o86psexBOikIw)
* [What are the 2 main elements that SSL is providing](https://intranet.hbtn.io/rltoken/jXCB9Hn-ALcP78kPMHtnSA)
* [HAProxy SSL termination on Ubuntu16.04](https://intranet.hbtn.io/rltoken/UkbvWfKF6ZAY_CUvlM32lA)
* [SSL termination](https://intranet.hbtn.io/rltoken/VFq2MQ9qHXw2Nb11tnWF6Q)
* [Bash function](https://intranet.hbtn.io/rltoken/v4PUYiN5CxhYKSycYaVvLw)

---
## Learning Objectives:bulb:
What you should learn from this project:

* What is HTTPS SSL 2 main roles
* What is the purpose encrypting traffic
* What SSL termination means

---

### [0. World wide web](./1-world_wide_web)
* Configure your domain zone so that the subdomain www points to your load-balancer IP (lb-01).
Let’s also add other subdomains to make our life easier, and write a Bash script that will display information about subdomains.


### [1. HAproxy SSL termination](./1-haproxy_ssl_termination)
* “Terminating SSL on HAproxy” means that HAproxy is configured to handle encrypted traffic, unencrypt it and pass it on to its destination.


### [100. No loophole in your website traffic](./100-redirect_http_to_https)
* A good habit is to enforce HTTPS traffic so that no unencrypted traffic is possible. Configure HAproxy to automatically redirect HTTP traffic to HTTPS.

# :books: Author :pen:

[Mustapha Aliyu Galadima](https://github.com/MG-Musty/)
