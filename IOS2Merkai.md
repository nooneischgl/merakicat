### Details on how to use Meraki Cat just for IOS to Meraki Config Translation

Meraki Cat from Unbuntu Deskstop 24. LTS 
* [Download Link](https://ubuntu.com/download/desktop/thank-you?version=24.04&architecture=amd64&lts=true)
* [Install Guide](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)


* Preform normal installation using Ubuntu Install Docs 
* SSH into the VM
    * Loginto the GUI / Console
    * Update Repos with `sudo apt update`
    * Install SSH Server with `sudo apt-get install openssh-server`
    * Use the ip address command to find the IP 
    * On Local Computer use the `ssh <username>@<IP address>` to SSH into the server 

* Install Git with `sudo apt install git`
* Install Python3-11 
```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.11 python3.11-venv
```

* Clone Meraki Cat `git clone https://github.com/ecoen66/merakicat.git`
* Setup virtual python envierment  `python3.11 -m venv .venv`
    * Activate Virt Env `source .venv/bin/activate`
* Install Python packages `pip install -r requirements_dev.txt`
* Add Meraki Org Name and API Key 
    * `cd src/merakicat/`
    * `nano mc_user_info.py`
    * At end of file remove the # and add API Key and Meraki Org Name
    * ENSURE API Key ONLY has access to 1 Meraki Org
  
* Clean up and copy switch config over. 
    * Ensure Port numbers match 24 to 24, 48 to 48
    * Only include the  interface configs 
    * Interface Names / desc with angle brackets need the brackets removed 
    * SCP from local computer to Server 
        * `scp /Local/Dir/SWConfig.txt scp://<username>@<serverIP>/~/Configs/`



### Meraki Cat Usaged
- `python merakicat.py translate file <Switchconfigfile.txt> to <Serial Number#1> <Serial Number#2 (if Stacked>`

