# unicorn-java-tomcat
A tomcat application that shows the use of Java EE web application in containers. The project shows the use of Servlets, JSPs, Simple Tag Support, Tag Files, JDBC, SQL, Log4J, Bootstrap, Jackson

The project is originally taken from  git@github.com:awslabs/eb-tomcat-snakes.git

## INSTRUCTIONS
Install the Java 8 JDK. The java compiler is required to run the build script.
If you would like to run the web app locally, install Tomcat 8 and Postgresql 9.4.

You can deploy the ROOT.war archive that build.sh generates to an AWS Elastic Beanstalk web server environment running the Tomcat 8 platform.

### To download, build and deploy the project
Clone the project (SSH):

	~$ git clone git@github.com:awslabs/eb-tomcat-snakes.git

Or with HTTPS:

	~$ git clone https://github.com/sduru/unicorn-java-tomcat.git

Run ``build.sh`` to compile the web app and create a WAR file (OS X or Linux):

	~$ cd unicorns
	~/unicorns$ ./build.sh

Or in Windows with Git Bash:

	~/unicorns$ ./build-windows.sh

**IMPORTANT**
Always run build.sh from the root of the project directory.

The script compiles the project's classes, packs the necessary files into a web archive, and then attempts to copy the WAR file to ``/Library/Tomcat`` for local testing. If you installed Tomcat to another location, change the path in ``build.sh``:

	if [ -d "/path/to/Tomcat/webapps" ]; then
	  cp ROOT.war /path/to/Tomcat/webapps

Open [localhost:8080](http://localhost:8080/) in a web browser to view the application running locally.

## Site Functionality

The front page is a very basic introduction with a little bit of Javascript. All pages use a tag file for the header, and Bootstrap CSS for mobile friendly rendering.

The **Browse Movies** page shows a list of movies from the database generated with a simple tag.

The **Add a Movie** page is a form that lets a user add a movie to the database. It takes a movie name, link to IMDB or IMDB movie ID (e.g. tt0118615), and a boolean value that indicates whether the movie has snakes in it or not. Form input is validated with a regex in the movies model.

The **Search** page lets you perform a basic search for a movie with full name matches only.
