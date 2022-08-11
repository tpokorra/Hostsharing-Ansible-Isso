Hostsharing-Ansible-Isso
========================

https://isso-comments.de/ Isso - a commenting server like Disqus

This Ansible playbook will install the latest Isso release on a server from www.hostsharing.net.

To use these modules we have to create a file named ".hsadmin.properties" in the home directory of the package admins. Into that file we have to insert the packagename and password of the package admin. 

Example:

    xyz00@h99:~$ cat .hsadmin.properties 
    xyz00.passWord=insertpkgadminpasswordhere

This file should be protected, else it would be world readable:

    xyz00@h99:~$ chmod 600 .hsadmin.properties

We clone this git-repo to our machine:

    $ git clone https://github.com/tpokorra/Hostsharing-Ansible-Isso.git

Then we change the working directory:

    $ cd Hostsharing-Ansible-Isso

All needed parameters can be set in the inventory file now. Change xyz00 to the name of your package admin. Set the name of a domain, a new user and a password. We can edit the inventory file with:

    $ cp inventory-sample.yml inventory.yml
    $ vim inventory.yml
    
The option -i can be used to read this inventory file instead of the /etc/ansible/hosts file. We want to login with an SSH-Key. We run:

    $ ansible-playbook -i inventory.yml playbook-install.yml

Now we can reach our site for moderation of comments via:

    https://isso.example.org/admin

On https://blog.example.org, you can have an index.html with this content:

    <html>
    <body>
        <script data-isso="https://isso.example.org/"
            src="https://isso.example.org/js/embed.min.js"></script>
        <section id="isso-thread"></section>
    </body>
    </html>

--- Open Source Hosting ---
 https://www.hostsharing.net
