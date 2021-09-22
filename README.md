# Django-virtual-host
set up django in apache virtual host configration 


<VirtualHost *:80>
    ServerName dj.localhost
    ServerAlias dj.localhost
    Alias /static /home/qu4d/djo/mysite/static
    <Directory /home/qu4d/djo/mysite/static>
        Require all granted
    </Directory>

    <Directory /home/qu4d/djo/mysite/mysite/>
        <Files wsgi.py>
            Require all granted
        </Files>
    </Directory>

    WSGIDaemonProcess mysite python-path=/home/qu4d/djo/mysite python-home=/home/qu4d/djo/mysite/mysiteenv
    WSGIProcessGroup mysite
    WSGIScriptAlias / /home/qu4d/djo/mysite/mysite/wsgi.py

</VirtualHost>
<VirtualHost *:8090>
    Alias /static /home/qu4d/myproject/static
    <Directory /home/qu4d/myproject/static>
        Require all granted
    </Directory>

    <Directory /home/qu4d/myproject/myproject>
        <Files wsgi.py>
            Require all granted
        </Files>
    </Directory>

    WSGIDaemonProcess myproject python-path=/home/qu4d/myproject python-home=/home/qu4d/myproject/myprojectenv
    WSGIProcessGroup myproject
    WSGIScriptAlias / /home/qu4d/myproject/myproject/wsgi.py

</VirtualHost>
