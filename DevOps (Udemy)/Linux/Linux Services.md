
## Managing Services

**serive httpd start** - start HTTPD service (legacy)

**systemctl start httpd** - Start HTTPD service

**systemctl stop httpd** - Stop HTTPD service

**systemctl status httpd** - check HTTPD service Status

**systemctl enable httpd** - Configure HTTPD to start at startup

**systemctl disable httpd** - Configure HTTPD to not start at startup

## Starting a web server

**/usr/bin/python3 /opt/code/my_app.py** - starts the application my_app.py as a service, and runs a webserver

**curl http://localhost:5000**  - returns the response from the webserver running 

**systemctl start my_app** - starts the service

**systemctl stop my_app** - stop the service

### Configure the program as a service

#### Configure the program to run as a service

The systemd services are located at /etc/systemd/system

**my_app.service** - name of the service, this file will need to exist in the directory below

Inside of the my_app.service file, it will need to contain code to point to the app.

Inside of the my_app.service:

[Service]
ExecStart = /usr/bin/python3 /opt/code/my_app.py 

#### Reload the daemon and then start the service

Once this is saved, you will need to restart the daemon to ensure the new service is seen:

**systemctl daemon-reload** - This will restart the daemon for the new service

**systemctl start my_app** - start the service you just created

**systemctl status my_app** - show status of the service

**curl http://localhost:5000** - this will return the response of the webserver that your server is running on.

#### Configure and customize the service settings to run at startup, etc.

You can edit the same file you created in the /etc/systemd/system directory.

The file already contains the [Service] portion, now you can add an [Install] section.

[Install]
WantedBy=multi-user.target

You can add additional data as well in the same file for information for other people by adding the [Unit] section

[Unit] 
Description=My python web app

If there are prerequisites of your service, you can add them to the service section.

[Service]
ExecStart= /user/bin/python3 /opt/code/my_app.py
ExecStartPre=/opt/code/configure_db.sh
ExecStartPost=/opt/code/email_status.sh
Restart=always



