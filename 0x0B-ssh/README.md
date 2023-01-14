# 0x0B. SSH


### More info
[Shellcheck](https://github.com/koalaman/shellcheck) is a tool that will help you write proper Bash scripts. It will make recommendations on your syntax and semantics and provide advice on edge cases that you might not have thought about. Shellcheck is your friend! **All your Bash scripts must pass ``Shellcheck`` without any error or you will not get any points on the task**. Also, for every feedback, Shellcheck will provide a code that you can use to get more information about the issue, for example for code ``SC2034``, you can browse [https://github.com/koalaman/shellcheck/wiki/SC2034](https://github.com/koalaman/shellcheck/wiki/SC2034).
``Shellcheck`` is available on the school’s computers. If you want to use it on your own computer, here is how to [install it](https://github.com/koalaman/shellcheck#installing).

# SOLUTIO GETTING THE LOGIN TO THE WEB_SERVER
* Go to you root directory `( cd ~)`
`( cd .ssh)` directory
* `( ls - la)` to all the files inside the didirecto, reason to be sure if you have the required files in it, don't touch anything not yet.
* Remember the old we generated during the first project before this, that we paste save in our profile. Generate a new key using the name school. Remember we are doing all this in the root directory `( cd ~)`. 
* Go to your profile edit the SSH PUBLIC KEY copy and paste the public key of the school.pub key save it.
* Then ask for a new server.
* `Vim` / open the file config in your root directory edit `(HOST to the ip address on your server)` add this `( PublicKeyAuthentication yes)` save it.
* Run the command `( echo YOUR-PUBLIC-KEY-IN-SCHOOL.PUB >> ~/.ssh/authorized_key)`
Then refresh your server by `/etc/init.d/ssh restart`
* Finally run  `(  ssh - v ubuntu@YOUR-IP)`
* *Bonus* : Do this for the task to add the key given to us   `( echo YOUR-PUBLIC-KEY-IN-SCHOOL.PUB >> ~/.ssh/authorized_key)`

# 📚 Author 🖋️

[Mustapha Aliyu Galadima](https://github.com/MG-Musty/)
