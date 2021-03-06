KeyBox
======

About
-----
KeyBox provides a way to manage OpenSSH v2 public keys and can start a web-based ssh terminal to execute commands and scripts on multiple ssh sessions simultaneously.


Prerequisites
-------------
Java JDK 1.6 or greater
http://www.oracle.com/technetwork/java/javase/overview/index.html

Maven 3 or greater ( Only needed if building from source )
http://maven.apache.org

Must run on *nix with OpenSSH version 2


To Run Jetty Build
------
Download keybox-jetty-vX.XX.tar.gz

https://github.com/skavanagh/KeyBox/releases

Export environment variables

     export JAVA_HOME=/path/to/jdk
     export PATH=$JAVA_HOME/bin:$PATH

Start KeyBox

        ./startKeyBox.sh


To Build from Source and Run with Maven
------
Export environment variables

    export JAVA_HOME=/path/to/jdk
    export M2_HOME=/path/to/maven
    export PATH=$JAVA_HOME/bin:$M2_HOME/bin:$PATH

In the directory that contains the pom.xml run

	mvn package jetty:run

**Note: Doing a mvn clean will delete the H2 DB and wipe out all the data.


Using KeyBox
------
Open browser to http://localhost:8090

Login with 

	username:admin 
	password:changeme

Steps:

1. Create users with public key
2. Create systems
3. Create profiles
4. Assign systems to profile
5. Assign profiles to users
6. Generate and distribute authorized key file for systems or users
7. Start composite-ssh sessions or create and execute a script across multiple sessions


Stuff to Know
-------------
KeyBox generates its own ssh-key with a unique passphrase upon initial startup.  To regenerate 
KeyBox's public-key delete 'id_rsa' and 'id_rsa.pub' in the classes/com/keybox/common/db 
directory and restart the application.

The H2 DB may be backed up by copying 'keybox.h2.db' in the classes/com/keybox/common/db directory.



Author
------
Sean Kavanagh - sean.p.kavanagh6@gmail.com
