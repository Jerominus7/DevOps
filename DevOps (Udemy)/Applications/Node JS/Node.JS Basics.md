
#node #js 
JavaScript was a language used to develop web pages that can do almost anything. It paved the way for other client side frameworks jQuery, Angular, react.JS, amber.JS, etc.

The key piece is that JavaScript is a client-side framework.

##### Node.JS took Javascript out of the clients and onto the servers. It is a server-side JavaScript environment that can be used to develop applications such as webservers using JavaScript.

An important feature with Node.Js is its ability to handle a large number of concurrent connections by implementing a non-bloating I/O model.

It's free and compatible with various platforms i.e. Windows, Linux, etc.

#### Installing Node.JS

First you must add the repository, by using the curl command.

`curl -sL https://rpm.nodesource.com/setup_13.x | bash -`

`yum install nodejs`

#### NodeJS Commands

Check version

`node -v`

If you need to run an application in node js, you use the node command and then the file name:

`node add.js`

output:
**Addition: 15** 


# NPM 

Node Package Manager is a repository with tons of packages for use.

These packages could be anything:
1. Files
2. Web Servers
3. Databases
4. Security
5. More

Check version
`npm -v`


You can search for packages by using the cmd below:
`npm search file`

You can then install a package:
`npm install file`

By default NPM uses the node_modules under the present working directory:

Node_modules
	File
		License
		README.md
		package.json
		LIB

The package.json has the metadata for the package if you need to troubleshoot issues.

You can install NPM packages for the current application you are working on, or you can install it globally across the system.

`npm install file`
This uses the current directory.

i.e:
My_application
	node_modules
		File
			Licence
			Readme.md
			package.json
			LIB
	app.js

This command searches for all node_modules directories:

`node -e "console.log(module.paths)"`
output will be the location of the node_modules directories for use:
[ '/app/node_modules', '/node_modules' ]

If you want to install NPM modules globally:
`npm install file -g`


### Common Modules

#### Built-In Modules
\
**fs** - to handle filesystem
**http** - to host an HTTP server
**os** - to work with the Operating System
**events** - to handle events
**tls** - to implement TLS and SSL
**url** - To parse URL strings


To look at all the modules available on Linux systems:
`ls /usr/lib/node_modules/npm/node_modules/`

#### External Modules
**express** - Fast, unopinionated, minimalist web framework
**react** - To create user interfaces
**debug** - To debug applications
**async** - To work with asynchronous JS
**lodash** - To work with arrays, objects, strings, etc.

To view external modules:
`ls /usr/lib/node_modules/`

### Application Dependencies

Recorded in the package.json in the root of the modules


