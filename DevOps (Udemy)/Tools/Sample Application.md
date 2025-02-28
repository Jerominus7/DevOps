## Overview
For using a sample web app, that already has some basic functions such as APIs, etc. I forked the recommended application from the course instructor so I could mess with it as I see fit.

This app is using Gorm (https://gorm.io) as the backend database and the Go web app framework Echo (https://echo.labstack.com).

Github link: (https://github.com/ybkuroki/go-webapp-sample)


## Sample lab for getting familiar with the app

Clone app:
`git clone https://github.com/kodekloudhub/go-webapp-sample>` - this will clone the app to the current working directory

Run the app:
From here I had to locate the main.go file and run it.
`go run main.go` 

I actually ran it with the & after it so it gave me a PS id, and then I ran PS to ensure it was running.
`go run main.go &` - runs the following cmd and dumps out the process id it spawned under
`ps` - displays process IDs, checked for the process ID from the previous cmd

It took a while but the app ran successfully, and dumped out the debug logs from the run. Checked what port it was running on, launched browser and logged in with sample creds successfully.







