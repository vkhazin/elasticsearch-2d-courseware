# Exercise Setup on AWS #

1. The objective is to make sure everyone is able to connect to their VM's and to understand where the VM's are running 
* AWS Regions and Availability Zones
* Elastic Search cluster should be setup in one region and using multiple availability zones
* EC2 t3.medium instances with Ubuntu 16.04, could have been any Linux Distribution
* Root access via ssh using public/private key
* For Windows user please download <a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html" target="_blank">putty
* For Mac and Linux users - ssh is available via terminal window
* You will be using private ssh key emailed to you before the course (or your own private key if you have pasted public key into the survey)
  * <a href="https://www.electrictoolbox.com/putty-rsa-dsa-keys/" target="_blank">How to import private key using Putty</a>
  * Setting permissions on Linux/MacOs: ```chmod 600 /path/to/private-key/file```
* Another option is to use [Secure Shell Chrome Extension to launch in-browser ssh](https://chrome.google.com/webstore/detail/secure-shell/pnhechapfaindjhompbnflcldabbghjo?utm_source=chrome-ntp-icon)