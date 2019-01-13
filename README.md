Project Description:
    Linux server configration project is aim to understanding of exactly what the web applications are doing, how they are hosted.
I configured an Ubuntu Linux server instance on AmazoneLightsail and deployed a Flask app to the server.

These are the information to access the server:
  1- IP Address: 52.57.244.53
  2- SSH Port#: 2200
  3- User: grader, Password: grader
  4- Private key:
    -----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEA6DDKIJo0m1d/E2WWadL3ctHkZIJZHr2AaJHXl9tKv4jd1Iqj
QK1QUZUjtbtRq4/zm59BFUXxcRQMylB3B+LsdLCOcbhz7cf5aSMhFNjmWVtKcASg
FesRVUVgyHuRCjtUFpp6AxL9/Y58Eh9L+Nb9kV7XNWPkoQGE05d4OnMfYPdLt0tI
LIE8Hp+i7H7K9D2AfrviKXWYTgWAqsC1BbZAl5Jul2LX0LWW9qP+wyitQX8Ff75s
5BTQcdkcPY9vcbZ1k1t1+bH1Xx2mxVst0ZJglfb1A3R5VI4bWZ0IHmQVeCgKVBa7
nRsS9eVyUG2YWSugj09m070fKFyxn0jj4BCX2wIDAQABAoIBABALtxwzq+kETerY
PWHIy4Lq0F7Fx0ThkasoUP7Uj8DWw4W5oviIQaGxrcsUS9uQUiRyB/xhXgMTgKLG
lsM7wl16Cg3/0jsfc7P5UoLvTlPkhCtjlnCNUyBScBLKv0Y2vWPmfwIRYO4R168k
7IogyVsvc63j3lvmD/jTYeKgLA32R1XrU9GhW+8JYwc1266K40utM6KmxVCFsoMq
h7L+sai9xEbmFlEv941grUeHoRtF/gZHwwZAzT5pzO5UsBUGGTedDTpbinEicg+I
beOmzyp7RmNsYPsY/a6EFzIP/D1/uMnh1WFE8jz8xq7xokfYEbC9q1VJkGi0RabY
vMJ9F6kCgYEA+yxhOndBMO8/VJzyXy5TgEBHW9otrO2OBxkf9ujkTqfYV5YAzEV9
jRWroW6/hWSvVAmEhvS1FQXmpVReEvtfp0JaF7xbwlkKbTYdvgOVZcEJsetZkWmi
3AUS/ANopIRvj6pOmqWnaOy2Hc9ZgwBx+zEQbzR1L9YIRd5UTXvZpDcCgYEA7KcG
q3h55JznHQtF8N2twT5e26uQC/mXWlGGzjFCgVCWBrBOXMESIBLP2xXX2fokWanm
2Kai9+QPN1AzxLW/3x7aUY4RIzcWmvPh9L74PfdwPKrbLgmrgAWzRSFNf3OU2jZS
xNNe5BclSY3kQDjE3TmneiPWR+/hxNRvNix9X30CgYEA6R1Ka/HsrlcORyCXDmG3
m+uMjyJSjBG6ZLob4ZRK+Plsn/WXbf78xKmdLmnUFSDaXLuspXiObCGa7Ez+Ns3Y
/Cpn5WmrHBh5xdyZBBbdXKApuFh/O6d4QI3xDba4MyC7TfI5m+wtEQPJDqe4Iw6R
uxnRb/SW4rvZ18a+JV/SIkcCgYAlUcW0fsBCNBgiNWfnLx46jjppS+ngaZDbtmWa
2JvTRsER9vW0nOHd2vmaZBxxDIh0910nJ0gl7XoUz/oJ+Ft0tSnamJvNQN+4ueMV
NJRzOTUi7BK6dN3tx3hY24KcKb78lnqA/ZBGSfwgWFb5Zbpt5Kyrj0E4gPTKlHGh
SmzPBQKBgGI4URtyRf66wAcwdWGZ/pwswLLXwjJBi4GAdW6DOZl8yLrVQJ52WWwg
TH2nEzsCucySZhAlNwXSae0/NnQ0vg/SdqPNHRPzfcHsW7ngA6SxeIMWnZZ5j7SE
WYf5vIbiL3IpjpvJ29oy5j3PS2r+nx6GRzubXfN2oYmD8U9oFvLh
-----END RSA PRIVATE KEY-----

5- Private & Public Key:
    ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCx0D4pkdh16zzSZ9VTvbqNCWrInJPKlRsuaGxJvpO$
    
    SHA256:UX6CrIzHJRapJ36arF3I1VOUi5Wu5Q0KA0qPezKneUA 




Steps:
  1- Create a new Ubuntu Linux server instance on Amazon Lightsail.
  2- access the Linux server using the ssh command:  
    ssh -i ~/.ssh/Key.pem  ubuntu@52.57.244.53

  3- update and upgrade all installed packages using:
    sudo apt-get update & sudo apt-get upgrade
    
  4- Change the SSH port from 22 to 2200:
    sudo nano /etc/ssh/sshd_config

    and allow incomming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123):
      sudo ufw allow 2200/tcp
      sudo ufw allow 80/tcp
      sudo ufw allow 123/udp
        
  5- Enble firewall:
      sudo ufw enable
      sudo service ssh restart
      
  6- create new user "grader":
     sudo adduser grader
     
    Add sudo permission using the command "sudo nano /etc/sudoers" and add the following:
      grader ALL=(ALL) NOPASSWD:ALL
    
  7- Create an SSH key pair for grader using command:  
      ssh-keygen.
      
  8- Configure the local timezone to UTC.
      sudo dpkg-reconfigure tzdata
      
  9- install Apache2
      sudo apt-get install apache2 libapache2-mod-wsgi-py3
      then restart it : sudo service apache2 restart
      
  10- install and configure postgresql.
      sudo apt-get install postgresql
    
  11- create catalog database & catalog user
      sudo -u postgres psql
      inside psql shell, run the following.

        create user catalog with password 'password';
        create database catalog with owner catalog;
          To exit shell command: \q
  
  12- install git
      sudo apt-get install git
      
  13- Clone Item catalog project
      cd /var/www sudo git clone https://github.com/ShathaAlSaadan/FSND-Project2 catalog
      

