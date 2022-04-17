echo "changing directory to /opt"
cd /opt

echo "installing utilities"
sudo yum -y install wget net-tools

echo "creating splunk home"


mkdir /opt/splunk

echo "grabbing splunk binaries from the mothership"
sudo wget -O splunk-8.1.0-f57c09e87251-Linux-x86_64.tgz 'https://www.splunk.com/bin/splunk/DownloadActivityServlet?architecture=x86_64&platform=linux&version=8.1.0&product=splunk&filename=splunk-8.1.0-f57c09e87251-Linux-x86_64.tgz&wget=true'

echo "installing splunk"
tar -xvzf splunk-8.1.0-f57c09e87251-Linux-x86_64.tgz -C /opt

echo "creating splunk user and home and setting password"
sudo useradd -md /opt/splunk splunk && echo magnificent | passwd --stdin splunk
#verify with grep splunk /etc/passwd

echo "giving splunk superuser role"
usermod -aG wheel splunk

#Verify with groups splunk
echo "making splunk own splunk file system"
chown -R splunk:splunk /opt/splunk

echo "changing directory to splunk bin"
cd /opt/splunk/bin/

echo "starting splunk and accepting licensing"
/opt/splunk/bin/splunk start --accept-license --answer-yes --no-prompt --seed-passwd magnificent

echo "to enable starting splunk at boot"
/opt/splunk/bin/splunk enable boot-start
