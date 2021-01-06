### create a user on all machines ( controller & all targets )

	useradd sakar -m -d /home/sakar -s /bin/bash

### add user to sudoers for root previliges  on all machines ( all targets )

	echo -e 'sakar  ALL=(ALL)  NOPASSWD:  ALL' > /etc/sudoers.d/sakar

### genereate ssh keys for above user on contrller machine 

```
	1) switch to user ( su - sakar )
	2) run "ssh-keygen" command as user ( this will genereate ssh keys for the user ) 
```
```
        on ansible controller machine
		cd /home/sakar/.ssh 
		cat id_rsa.pub (copy the content)
```
### copy user ssh keys from ansible contrller to all target hosts

```
	1) on all target machines
		   swith to the user ( su - sakar )
		   mkdir -p /home/sakar/.ssh
		   touch /home/sakar/.ssh/authorized_keys
		   chmod -R 700 /home/sakar/.ssh
		   vi /home/sakar/.ssh/authorized_keys  (enter the copied contet of id_rsa.pub from controller & save the file)
```	
	

