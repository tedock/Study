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
