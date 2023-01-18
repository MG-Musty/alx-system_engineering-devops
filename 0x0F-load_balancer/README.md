# 0x0F LOAD_BALANCER


### More info
[Shellcheck](https://github.com/koalaman/shellcheck) is a tool that will help you write proper Bash scripts. It will make recommendations on your syntax and semantics and provide advice on edge cases that you might not have thought about. Shellcheck is your friend! **All your Bash scripts must pass ``Shellcheck`` without any error or you will not get any points on the task**. Also, for every feedback, Shellcheck will provide a code that you can use to get more information about the issue, for example for code ``SC2034``, you can browse [https://github.com/koalaman/shellcheck/wiki/SC2034](https://github.com/koalaman/shellcheck/wiki/SC2034).
``Shellcheck`` is available on the school’s computers. If you want to use it on your own computer, here is how to [install it](https://github.com/koalaman/shellcheck#installing).

# SOLUTION GETTING THE CONFIGURATION TO THE WEB_SERVER-02

* Go to you root directory `( cd ~)`
`( cd .ssh)` directory
* `( ls - la)` to all the files inside the didirecto, reason to be sure if you have the required files in it, don't touch anything not yet.
* Generate a new key using the name any name `web-02`. Remember we are doing all this in the root directory `( cd ~)`. 
* Then ask for a new server for `web-02`.
* `Vim` / open the file `config` in your `/root/.ssh/` directory edit `Add a new-line HOST with the web-02 ip_address` save it.
* Run the command `( echo YOUR-PUBLIC-KEY-IN-WEB-02 >> ~/.ssh/authorized_keys)`
* Then refresh your server by `/etc/init.d/ssh restart`
* Finally run  `(  ssh -v ubuntu@WEB-02-IP)`

WAHLAH! YOU IN!!!

# 📚 Author 🖋️

[Mustapha Aliyu Galadima](https://github.com/MG-Musty/)
