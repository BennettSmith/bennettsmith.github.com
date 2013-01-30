---
title: How I setup Ubuntu 11.04 Server using VirtualBox on a MacBook Air
author: Admin
layout: post
permalink: /2011/07/how-i-setup-ubuntu-11-04-server-using-virtualbox-on-a-macbook-air/
categories:
  - Linux
  - Mac
  - Software
---
Download and install the latest version of VirtualBox from http://www.virtualbox.org. As I write this article the current version is 4.1.

Download the Ubuntu 11.04 Server .ISO file from http://www.ubuntu.com. I first tried the 64-bit version but it seems that VirtualBox has trouble with it. The 32-bit version worked just fine, and for the sort of development tasks I am planning it will be okay so I didn’t look any further into why the 64-bit version failed to install.

Create a new virtual machine. I called mine “ubuntu-11.04″. This one will be used as a basis for other machines I clone.  I went with 512MB of RAM and 40GB of hard drive space, making sure that the hard drive was configured to grow dynamically.  I accepted all of the default settings during the installation process. I did not install any additional packages at this stage.  Since I plan on using Vagrant (http://vagrantup.com) to manage my virtual machines I chose to name this machine ubuntu and gave it a user name of “Vagrant Manager” with a login of “vagrant” and a password of “vagrant”.

Shutdown the virtual machine and then create a snapshot (I called mine “Fresh Install”).

You are now ready to create a clone of this machine and start playing around.  Right-click on the virtual machine you just created and select “Clone…” from the context menu.  Give your new virtual machine a unique name and be sure to check the “Reinitialize the MAC address of all network cards” option. I assigned the name “vagrant-ubuntu-natty” since that is in keeping with the conventions mentioned on the Vagrant site. I choose to only clone the current machine state.

Boot up the new virtual machine once the clone operation completes.  Log in using vagrant/vagrant.  You will now need to correct issues with the ethernet drivers.  Basically, when you asked VirtualBox to reinitialize the MAC addresses it caused the operating system to no longer recognize the virtual ethernet adapter hardware.  The steps to correct this are:

<pre>sudo rm /etc/udev/rules.d/70-persistent-net.rules</pre>

<pre>sudo service udev restart</pre>

<pre>sudo shutdown -r now</pre>

By running these three commands your virtual machine will be reconfigured to now recognize the new virtual ethernet adapters with their reinitialized MAC addresses.

Now you can proceed to install the VirtualBox Guest Additions software.  Start by updating the Ubuntu software using these commands:

<pre>sudo apt-get update</pre>

<pre>sudo apt-get -y upgrade</pre>

<pre>sudo apt-get -y install linux-headers-$(uname -r)</pre>

<pre>sudo apt-get -y install dkms</pre>

<pre>sudo shutdown -r now</pre>

At this point you are actually ready to do the installation of the Guest Additions. From the Devices menu in VirtualBox select the “Install Guest Additions…” menu item. This will “insert” the CD containing the guest additions software into the virtual machine.Now, from your virtual machine run the following commands.

<pre>sudo mkdir /tmp/cdrom</pre>

<pre>sudo mount /dev/cdrom /tmp/cdrom</pre>

<pre>cd /tmp/cdrom</pre>

<pre>sudo ./VBoxLinuxAdditions.run</pre>

Note, the installation of the Window System drivers will fail. This is okay; remember, we are running the server variant of Ubuntu and don’t have any of the windowing system components installed.

Now change the hostname for the system so it can be used as a Vagrant base box.

<pre>sudo hostname vagrant-ubuntu-natty.vagrantup.com</pre>

Edit the /etc/hosts file and change the second line where localhost is defined. Set the fully qualified domain name for the host and the short name for the host.

Edit the /etc/hostname file and replace “ubuntu” with “vagrant-ubuntu-natty”.

Edit the /etc/resolv.conf file and replace the domain and search values with “vagrantup.com”.

Reboot the machine once more using

<pre>sudo shutdown -r now</pre>

It is now time to setup the rest of the required software on the guest in order for it to be used as a Vagrant base box.

Start by editing /etc/sudoers using

<pre>sudo vim /etc/sudoers</pre>

Add or change the line giving sudo access to administrators to read as follows:

<pre>%admin ALL=NOPASSWD: ALL</pre>

Add the following line right after the “Defaults env_reset” line:

<pre>Defaults env_keep="SSH_AUTH_SOCK"</pre>

Run the command:

<pre>sudo /etc/init.d/sudo restart</pre>

Now setup the software Vagrant relies upon to provide all it’s goodness.

<pre>sudo apt-get install -y ruby-dev</pre>

<pre>sudo apt-get install -y rubygems</pre>

<pre>sudo apt-get install -y puppet</pre>

<pre>sudo apt-get install -y chef</pre>

<pre>sudo gem install chef</pre>

<pre>sudo apt-get install -y openssh-server openssh-client</pre>

When installing the chef package (above) you will be prompted for the URL of the Chef server. Just press enter here and ignore that step. We are only interested in chef-solo, and this URL is only used by chef-client. The package installer will go ahead and configure the chef client to run automatically. We now need to disable this by running the following command:

<pre>sudo /usr/sbin/update-rc.d chef-client disable</pre>

Edit the file /etc/ssh/sshd_config and add the following line (case matters here):

<pre>UseDNS no</pre>

Configure a secure key pair for our new Vagrant base box by running the following command on the host system.

<pre>ssh-keygen -P "" -t rsa -C "Some meaningful comment" -f ./vagrant-id_rsa</pre>

This command will create two files in the local directory called vagrant-id\_rsa and vagrant-id\_rsa.pub.  You will need to copy vagrant-id\_rsa.pub into the ~/.ssh/authorized\_keys file on the guest system. To do this you will need to setup port forwarding between the host and guest. The first step is to learn what the IP address of the host and guest systems are.  Use the following command to view the network adapters that are configured on each system:

<pre>ifconfig</pre>

Run this on both the host and guest. Once you know both IP addresses you need to add a port forwarding rule in Virtual Box for the SSH port. This is done by selecting the “Settings…” menu item from the “Machine” menu.  Once you have the settings dialog box open select the “Network” button and then open the “Advanced” section.  You will see a button labeled “Port Forwarding”. Press it to open the port forwarding rule editor. Here you need to create a rule as follows:

<pre>Name: SSH</pre>

<pre>Protocol: TCP</pre>

<pre>Host IP: &lt;fill in host IP address from ifconfig&gt;</pre>

<pre>Host Port: 9999</pre>

<pre>Guest IP: &lt;fill in guest IP address from ifconfig&gt;</pre>

<pre>Guest Port: 22</pre>

Close the panel and dismiss the settings dialog box. You should now have a port open between the host and the guest for SSH/SCP.  To verify this, enter the following command in a terminal window on the host system.

<pre>ssh -p 9999 vagrant@&lt;host ip address&gt;</pre>

When prompted for a password enter “vagrant”. You should now be in an ssh session on the guest system. If this worked you are ready to propogate the public key generated earlier. You can exit out of the SSH session now by typing exit in the guest. Back on the host type the following command to copy the public key.

<pre>cat vagrant-id_rsa.pub | ssh -p 9999 vagrant@&lt;host ip address&gt; 'sh -c "cat - &gt;&gt;~/.ssh/authorized_keys"'</pre>

You will be prompted for the guest password. Type “vagrant” again. You will now want to test that the key propogated successfully. On the host system enter the following commands.

<pre>ssh-add ./vagrant-id_rsa</pre>

<pre>ssh -p 9999 vagrant@&lt;host ip address&gt;</pre>

If everything worked in the earlier steps you should be in an SSH session on the guest without the need to enter your password!

As a final step before packaging a vagrant base box you should clean things up in the guest by running the following commands:

<pre>sudo apt-get clean</pre>

<pre>sudo apt-get autoclean</pre>

You are now ready to package the vagrant base box. Back on the host system in a terminal window first create a Vagrantfile that points to the SSH private key. Here is an example of what it might look like if you decide to copy your key (generated earlier). Call this file Vagrantfile.pkg.

<pre>Vagrant::Config.run do |config|</pre>

<pre>  config.ssh.private_key_path = "lcl-vagrant-id_rsa"</pre>

<pre>end</pre>

Now invoke this command in the terminal window to create the package.

<pre>vagrant package --base vagrant-ubuntu-natty --include lcl-vagrant-id_rsa --vagrantfile Vagrantfile.pkg</pre>

The packaging takes a little while. Once it completes you should test the base box using these steps:

<pre>mv package.box vagrant-ubuntu-natty.box</pre>

<pre>vagrant box add lclbase32 vagrant-ubuntu-natty.box</pre>

<pre>mkdir test_environment</pre>

<pre>cd test_environment</pre>

<pre>vagrant init lclbase32</pre>

<pre>vagrant up</pre>

<pre>vagrant ssh</pre>

If all went well you are now finished with building a Vagrant base box. Congratulations!

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_68">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2011%2F07%2Fhow-i-setup-ubuntu-11-04-server-using-virtualbox-on-a-macbook-air%2F&linkname=How%20I%20setup%20Ubuntu%2011.04%20Server%20using%20VirtualBox%20on%20a%20MacBook%20Air" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2011%2F07%2Fhow-i-setup-ubuntu-11-04-server-using-virtualbox-on-a-macbook-air%2F&linkname=How%20I%20setup%20Ubuntu%2011.04%20Server%20using%20VirtualBox%20on%20a%20MacBook%20Air" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2011%2F07%2Fhow-i-setup-ubuntu-11-04-server-using-virtualbox-on-a-macbook-air%2F&linkname=How%20I%20setup%20Ubuntu%2011.04%20Server%20using%20VirtualBox%20on%20a%20MacBook%20Air" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>