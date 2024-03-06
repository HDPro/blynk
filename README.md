Install Blynk Server For CentOS And Ubuntu

# INSTALL PACKAGE FOR CENTOS
```
# Install JAVA8, libXrender for BLYNK V14116
yum -y install wget java-1.8.0-openjdk
rpm -Uvh https://raw.githubusercontent.com/HDPro/blynk/master/files/libXrender-0.9.10-1.el7.x86_64.rpm

# Install JAVA11, libXrender for BLYNK V14117
yum -y install wget java-11-openjdk
rpm -Uvh https://raw.githubusercontent.com/HDPro/blynk/master/files/libXrender-0.9.10-1.el7.x86_64.rpm

# Open port 8080, 9443
firewall-cmd --permanent --add-port=9443/tcp
firewall-cmd --permanent --add-port=8080/tcp

```

# INSTALL PACKAGE FOR UBUNTU, ARMBIAN
```
# Install JAVA8, libXrender for BLYNK V14116
apt-get -y install openjdk-8-jdk libxrender1

# Install JAVA11, libXrender for BLYNK V14117
apt-get install openjdk-11-jdk libxrender1

# Open port 8080, 9443
iptables -A INPUT -p tcp --dport 9443 -j ACCEPT
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT

```

# CREATE, DOWNLOAD, RUN BLYNK SERVER
```
# Create folder and change dir
mkdir -p /var/www/html/blynk
cd /var/www/html/blynk

# Download blynk v14117 for JAVA11
wget -O server.jar https://raw.githubusercontent.com/HDPro/blynk/master/files/server-0.41.17.jar

# Download blynk v14116 for JAVA8
wget -O server.jar https://raw.githubusercontent.com/HDPro/blynk/master/files/server-0.41.16-java8.jar

# Run server
java -jar /var/www/html/blynk/server.jar -dataFolder /var/www/html/blynk &

# Your Server
# http://yourserver:9443
# email: admin@blynk.cc
# password: auto generate

# Autorun when server restart
crontab -e
@reboot java -jar /var/www/html/blynk/server.jar -dataFolder /var/www/html/blynk &
Press "#" => "Esc" => ":wq" => Enter

```

# FIX JAVA DUPLICATE VERSION
```
# Check java version
java -version

# Get Name JDK Package
rpm -qa | grep jdk

# Get Name Java Package
rpm -qa | grep java

# Delete Package
rpm -e XXX (With XXX is JDK Package Name Or Java Package Name)

```

# DOWNLOAD BLYNK

#### For Android: [Click Here](https://raw.githubusercontent.com/HDPro/blynk/master/files/Blynk_Legacy_For_Android.apk)