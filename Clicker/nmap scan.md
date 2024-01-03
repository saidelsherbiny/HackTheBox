```nmap -sC -sV -v  10.10.11.232        
Starting Nmap 7.93 ( https://nmap.org ) at 2023-12-21 19:10 EST
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 19:10
Completed NSE at 19:10, 0.00s elapsed
Initiating NSE at 19:10
Completed NSE at 19:10, 0.00s elapsed
Initiating NSE at 19:10
Completed NSE at 19:10, 0.00s elapsed
Initiating Ping Scan at 19:10
Scanning 10.10.11.232 [2 ports]
Completed Ping Scan at 19:10, 0.02s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 19:10
Completed Parallel DNS resolution of 1 host. at 19:10, 0.02s elapsed
Initiating Connect Scan at 19:10
Scanning 10.10.11.232 [1000 ports]
Discovered open port 80/tcp on 10.10.11.232
Discovered open port 22/tcp on 10.10.11.232
Discovered open port 111/tcp on 10.10.11.232
Discovered open port 2049/tcp on 10.10.11.232
Completed Connect Scan at 19:10, 0.47s elapsed (1000 total ports)
Initiating Service scan at 19:10
Scanning 4 services on 10.10.11.232
Completed Service scan at 19:10, 6.06s elapsed (4 services on 1 host)
NSE: Script scanning 10.10.11.232.
Initiating NSE at 19:10
Completed NSE at 19:10, 1.20s elapsed
Initiating NSE at 19:10
Completed NSE at 19:10, 0.13s elapsed
Initiating NSE at 19:10
Completed NSE at 19:10, 0.00s elapsed
Nmap scan report for 10.10.11.232
Host is up (0.027s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 89d7393458a0eaa1dbc13d14ec5d5a92 (ECDSA)
|_  256 b4da8daf659cbbf071d51350edd81130 (ED25519)
80/tcp   open  http    Apache httpd 2.4.52 ((Ubuntu))
|_http-title: Did not follow redirect to http://clicker.htb/
|_http-server-header: Apache/2.4.52 (Ubuntu)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
111/tcp  open  rpcbind 2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  3,4         2049/tcp   nfs
|   100003  3,4         2049/tcp6  nfs
|   100005  1,2,3      35633/udp6  mountd
|   100005  1,2,3      38980/udp   mountd
|   100005  1,2,3      42313/tcp6  mountd
|   100005  1,2,3      46961/tcp   mountd
|   100021  1,3,4      32858/udp   nlockmgr
|   100021  1,3,4      35159/tcp   nlockmgr
|   100021  1,3,4      37279/tcp6  nlockmgr
|   100021  1,3,4      46813/udp6  nlockmgr
|   100024  1          37585/udp6  status
|   100024  1          40874/udp   status
|   100024  1          56337/tcp   status
|   100024  1          59715/tcp6  status
|   100227  3           2049/tcp   nfs_acl
|_  100227  3           2049/tcp6  nfs_acl
2049/tcp open  nfs_acl 3 (RPC #100227)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
Initiating NSE at 19:10
Completed NSE at 19:10, 0.00s elapsed
Initiating NSE at 19:10
Completed NSE at 19:10, 0.00s elapsed
Initiating NSE at 19:10
Completed NSE at 19:10, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.33 seconds
                                                               
```