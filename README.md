<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Internet Information Services(IIS)
- osTicket Installation Files

<h2>Installation Steps</h2>

Alright, welcome to the tutorial! To start, we'll need to create a virtual machine using Microsoft Azure. Feel free to name the VM anything you want, as long as it makes sense to you. The VM should be running Windows 10 and have at least 2-4 vcpus so that the VM will run smoothly.
<p>
<img src="https://imgur.com/O2lgWbL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

Next, we're going to connect to the VM using RDP. Use the VM's public IPv4 address when connecting. 
<p>
<img src="https://imgur.com/Rx7Wm0d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

Once connected to the VM, go to control panel--> uninstall or change a program--> Turn Windows features on or off. Then enable Internet Information Services(IIS) and CGI.
<p>
<img src="https://imgur.com/O69o2l4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/N5Bxbju.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

After applying the changes, we'll need to download a few things so OSticket can run on the VM. Click this link to download the necessary files: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6 . First, download and install PHP Manager for IIS and rewrite moduel. Make sure to download the files on the Google Drive through your VM and not on your own computer. After downloading, create the directory C:\PHP.
<p>
<img src="https://imgur.com/otghrd5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

Next, download the php-7.3.8 file. Extrace the files to the PHP folder we created earlier. After, download the VC_redist and mysql-5.5.62 files.
<p>
<img src="https://imgur.com/HqdONz9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

After we install mysql-5.5.62, we need to create a root password. Write this down somewhere so you do not forget as we will need to use it later.
<p>
<img src="https://imgur.com/oPugtVm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

Great, now go to the start menu and type IIS and right click it, then click "Run as Administrator". Double click "PHP Manager" and then click "Register new PHP version".
<p>
<img src="https://imgur.com/gvpdfPg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

Next, download the OSticket file from the installation files. We're going to copy the "upload" folder to c:\inetpub\wwwroot. Then rename the "upload" folder to "osTicket". Open IIS, and stop and start the server. In IIS, click Sites-> Default-> osticket. On the right, click "Browse*:80"

<p>
<img src="https://imgur.com/xrWaVci.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://imgur.com/vAy3b5P.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
 
</p>
<br />

After clicking, something like this should pop up. Some extensions will not be enabled. Go back to IIS, then navigate to Sites-> Default-> osTicket, then double-click "PHP Manager". Click "Enable or disable an extension". Enable: php_imap.dll, php_intl.dll, php_opcache.dll

<p>
<img src="https://imgur.com/L6fUR0E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://imgur.com/THNIgAd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />

After enabling those, refresh the osTicket site in the browser and notice the changes. In filer explorer, go to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename "ost-sampleconfig.php" to "ost-config.php". After this, right-click on this file and disable inheritance. Then add permissions for everyone to have full control.
<p>
 <img src="https://imgur.com/BzzEiCQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
<img src="https://imgur.com/mRwEWeg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

Once this done, go back to osTicket in the browser and begin setting it up. Create a username and password. Before filling out next section, download HeidiSQL from the installation files. Once installed, click new and type in the password you created when you downloaded mysql.
<p>
<img src="https://imgur.com/6n7XH6U.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://imgur.com/zdUsilC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />

In HeidiSQL, right-click "unamed" and select create new-> database and then name it "osTicket". Go back to "Osticket in the browser, fill out Database settings then hit "install now". Congratulations! We've successfully installed osTicket!
<p>
<img src="https://imgur.com/h7UPRVV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://imgur.com/dB3xMFz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />

Lastly, we need to do some clean up. We need to delete the setup folder in C:\inetpub\wwwroot\osTicket. We will also set permissions to "Read" only for the "ost-config.php" folder. After that, osTicket is ready to be used!
