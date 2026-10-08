# Install PgAdmin 4 using Apache2 in Ubuntu    

1. Add GPG key and repository  
```bash
sudo apt-get install wget ca-certificates 
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add - 
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" >> /etc/apt/sources.list.d/pgdg.list' 
```
2. Install PgAdmin4 & apache2 with default e-mail/user-id and password
	
```bash
	sudo apt-get install pgadmin4 pgadmin4-apache2 
```
	
Enter email & password to complete the installation process 

3. Go to [http://localhost/pgadmin4](browser) and login with email & password which you have given in the installation process

![output](Pgadmin4.png)
     

 