# Red Hat JBoss Web Server and Red Hat Fuse Example


### Introduction
An example which shows how to use the Camel Servlet from Red Hat Fuse with Red Hat JBoss Web Server.

### Build
You will need to package this example first:

	mvn package

### Run

To run the example, deploy it in Red Hat JBoss Web Server by copying the `.war` to the
deploy folder of Red Hat JBoss Web Server.

And then hit this url from a webbrowser which has further
instructions

	http://localhost:8080/jws-fuse
<http://localhost:8080/jws-fuse/>

The servlet is located at

	http://localhost:8080/jws-fuse/camel/hello
<http://localhost:8080/jws-fuse/camel/hello>