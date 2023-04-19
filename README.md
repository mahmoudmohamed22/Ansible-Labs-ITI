# Ansible-Labs-ITI

# lab one 
Explore some built-in modules like:

(apt, dnf, package, service, command, copy, user, group, lineinfile, authorized_key, etc.)
ansible-builtin modules

 Update cache

 Install latest nginx

 Copy index.html from controller to host 1

 Restart nginx service

 Can you see your index.html file when you hit host 1 on port 80 ?


# lab two 
Define these variables (package_name, package_version)

 on playbook level

 on inventory level

 on command line level

Use apt module with the package name and version from your variables

 Loop over a list of packages and install latest versions.

 Loop over a list of packages and perform different actions as per input.

 Install nginx or apache2 depending on distribution

 Restart nginx service if distribution is ubuntu and variable value is true

 View the value of your register variable using debug module

 Restart service if the installation task was changed or was not failed


# lab three

Create your first role with name (web)

The task book will include:

1.installing a package

(get the package name from vars)

2.Copying a file from controller to host using template

(get the template name & template message from vars)

(the actual template file will be stored in ./roles/web/templates)

(will also notify the restart handler)

3.copying a list of files from controller to host using loop

(get the list of file names from vars)

(the actual files will be stored in ./roles/web/files)

(will be executed using Handlers)

Restart the service of the installed package

(will be executed using Handlers chaining)
