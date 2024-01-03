After going to the webpage http://clicker.htb we notice a login button

After testing some default creds and not succeeding we notice the following URL with each wrong credential validation:
http://clicker.htb/login.php?err=Authentication%20Failed

![[Pasted image 20231221191742.png]]

After modifying the URL, the message shown is different:

![[Pasted image 20231221191834.png]]


This is interesting can we get an XSS from this?
let's try with this payload:
```html
<image/src/onerror=prompt(8)>
```


And Bam we have an XSS
![[Pasted image 20231221191956.png]]



We can keep this in our backpocket for the moment, as we can upload a shell into the server this way.

Looking at our nmap scan we notice port 111 is running rpcbind 2.4

searching rpcbind 2.4 we find this article on Hacktricks


enumerating rpcbind using nmap

```bash
sudo nmap -p 111 --script=nfs-ls 10.10.11.232
```

we get:
![[Pasted image 20231222124646.png]]

```bash
sudo nmap -p 111 --script=nfs-showmount 10.10.11.232
```

we get:
![[Pasted image 20231222124719.png]]

```bash
sudo nmap -p 111 --script=nfs-statfs 10.10.11.232
```
we get:
![[Pasted image 20231222124827.png]]

ok so there is a backups folder that can be exploited. Let's try mounting to it:

just out of paranoia let's double check the folder name:

```bash
showmount -e 10.10.11.232
```
![[Pasted image 20231222125131.png]]



now mounting to the folder:
```bash
sudo mount -t nfs 10.10.11.232:/mnt/backups mounted -o nolock
```

there is a zipped backup folder in the drive:
![[Pasted image 20231222125451.png]]


after unzipping we find:
```bash
unzip -q clicker.htb_backup.zip -d ../unzippedmount
```

![[Pasted image 20231222125843.png]]


ok so we have a source code and some credentials of a DB that is hosted locally.


When looking further into the website we notice that after saving the game we are sending this request:
![[Pasted image 20231223162123.png]]

Can we change our role to admin?
![[Pasted image 20231223162101.png]]

ok we got this:
![[Pasted image 20231223162223.png]]


When checking the source code we notice that error is thrown when role is detected. can we try bypassing that?
After doing some investigation I came across CRLF injection:
https://book.hacktricks.xyz/pentesting-web/crlf-0d-0a

so trying to add %0D%0A before the role:
![[Pasted image 20231223163745.png]]


And bam
![[Pasted image 20231223162845.png]]


now let's log out and log back in, and we have access to admin.php
![[Pasted image 20231223163931.png]]
![[Pasted image 20231223163943.png]]


What does the export do?
![[Pasted image 20231223165151.png]]

creates a file on the system with info about the users

![[Pasted image 20231223165218.png]]

However look at the request:
![[Pasted image 20231223165232.png]]


can we change the extension?

![[Pasted image 20231223165305.png]]
it looks like we just did?

![[Pasted image 20231223165327.png]]


![[Pasted image 20231223165344.png]]


ok how can we play with that?

maybe create an account with a payload, that will execute once we open the export?

ok that did not work
![[Pasted image 20231223165630.png]]

how else can we change the nickname? maybe we can inject into that request?
![[Pasted image 20231223165945.png]]

![[Pasted image 20231223165950.png]]

ok it looks like it worked!


