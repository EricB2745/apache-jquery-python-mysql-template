# apache-jquery-python-mysql-template

The purpose of this project is to create a recipe to quickly stand up a working
apache server configured to execute python scripts in a cgi-bin folder.

1. Install-configure Apache<br>
2. sudo apt-get install apache2<br>
3. create new site<br>
   - cd /var/www<br>
   - sudo mkdir site1<br>
   - sudo mkdir site1/js<br>
   - sudo mkdir site1/css<br>
   - sudo mkdir site1/cgi-bin<br>
4. take ownership of the new site and make it accessible<br>
   - sudo chown -R $USER:$USER /var/www/site1<br>
   - sudo chmod 755 -R /var/www<br>
5. Enable CGI<br>
   - sudo a2enmod cgi<br>
   - systemctl restart apache2
6. Add the following to the 000-default.conf file<br>
         <Directory "/var/www/site1/cgi-bin/"><br>
                AddHandler cgi-script .cgi .py<br>
                AllowOverride All<br>
                Options +Indexes +FollowSymLinks +ExecCGI<br>
                Order allow,deny<br>
                Allow from all<br>
        </Directory><br>

      
