# notes
test

[Unit]
Description=Apache Tomcat Web Application Container
After=network.target

[Service]
Type=forking

User=tomcat
Group=tomcat

Environment="JAVA_HOME=/usr/lib/jvm/jre"
Environment="CATALINA_PID=/opt/apache-tomcat-9.0.80/temp/tomcat.pid"
Environment="CATALINA_HOME=/opt/apache-tomcat-9.0.80"
Environment="CATALINA_BASE=/opt/apache-tomcat-9.0.80"
Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"
Environment="JAVA_OPTS=-Djava.awt.headless=true -Djava.security.egd=file:/dev/./urandom"

ExecStart=/opt/apache-tomcat-9.0.80/bin/startup.sh
ExecStop=/opt/apache-tomcat-9.0.80/bin/shutdown.sh

Restart=on-failure

[Install]
WantedBy=multi-user.target
