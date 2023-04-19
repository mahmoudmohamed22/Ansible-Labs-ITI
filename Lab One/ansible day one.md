## section one

1-install ansible
![[Screenshot from 2023-04-02 15-58-15.png]]


2-Create a new user on control machine and new user on host 1
```
first created docker file to create controller machine and 
hosts machines
``` 
![[Pasted image 20230404140721.png]]
- create control machine with user devops
![[Pasted image 20230404140916.png]]
- create host1 machine with user anisble 
![[Pasted image 20230404141210.png]]
3- Make sure you can ssh into host 1 (using password)
![[Pasted image 20230404141936.png]]
![[Pasted image 20230404142003.png]]
```
connected with password using ssh
```
4-Generate SSH key pair on control machine
- first i will cd to ~/.ssh
```
when i switched i don't exist home for user 
i created for user 
```
![[Pasted image 20230404142517.png]]
```
created .ssh 
```
![[Pasted image 20230404142748.png]]
```
generate public key and private key now 
```
![[Pasted image 20230404142923.png]]
5- Copy the public key to host 1
![[Pasted image 20230404143104.png]]
```
now i need created home dictory for ansible in host1

```
![[Pasted image 20230404143301.png]]
```
again occures send public key to server 
```
![[Pasted image 20230404143358.png]]

6- Make sure you can ssh into host 1 (using prv/pub)
![[Pasted image 20230404143512.png]]

------------------------------------------------------------------------

## section two

Create the inventory file
Put the IP of host 1 in the inventory file
![[Pasted image 20230404144957.png]]

Use the inventory file path in your ad-hoc command instead of using
the IP hard-coded
Example:
ansible all -i inventory --private-key ~/.ssh/devops -u ubuntu -m ping
```
write copy with hands copy public key and private key in cotroller machine in docker contianer

```
![[Pasted image 20230404152842.png]]
```
connected when i created another public and private and generate with my machine and send 
```
![[Pasted image 20230404152723.png]]


-------------------------------------------------------
## section three

1- Create the configuration file
2- Insert some values in the configuration file
![[Pasted image 20230404154528.png]]
3- Run the minimized ad-hoc command
 Example: ansible all -m ping
 ```
when dir has all permissions rwx 
```
 ![[Pasted image 20230404154549.png]]
 ```
 when dir don't have write permission in dir
 
```
![[Pasted image 20230404161234.png]]

------------------------------------------

## section four
when apply 
```
ansible all -m command -a "whoami"
```
![[Pasted image 20230404161746.png]] 
Insert the correct values in the configuration file
![[Pasted image 20230404162002.png]]
Example: ansible all -m command -a "whoami"
What is the output of the command ?
![[Pasted image 20230404162025.png]]
```
changed and add
echo "PermitEmptyPasswords yes" >> /etc/ssh/sshd_config
echo "PermitRootLogin yes" >> /etc/ssh/sshd_config
root@cb97a73ea432:/etc/ssh# service ssh restart
 * Restarting OpenBSD Secure Shell server sshd  [ OK ]  
```

```
still exist problem how run command as root
```
![[Screenshot from 2023-04-04 16-55-26.png]]
```
wait minuties and return try again
```
![[Pasted image 20230404172539.png]]


--------------------------------------------------------

## section five
Write your first playbook file
![[Pasted image 20230404172718.png]]Stop gather_facts and update cache
![[Pasted image 20230404172743.png]]


## section six
- Explore some built-in modules like:
(apt, dnf, package, service, command, copy, user, group, lineinfile, authorized_key, etc.)
ansible-builtin modules
- Update cache
- Install latest nginx
- Copy index.html from controller to host 1
- Restart nginx service
![[Pasted image 20230404174350.png]]
-  Can you see your index.html file when you hit host 1 on port 80 ?
