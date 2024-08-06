<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure Virtual Machine
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 pro</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure VM
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2>


<p>
1.) <b>Create Virtual Machine on Azure</b>
  
- Create Resource Group <b>RG-Lab-osTicket</b>
- Create Windows 10 Virtual Machine <b>VM-osTicket</b> with at least 2 Virtual CPUs
- Allow the VM with a new Virtual Network (Vnet) <b>VM-osTicket-vnet/default</b>
- Login info
  - Username: <b>johnan</b>
  - Password: <b>Passpassword1</b>
- Enter into the virtual machine with Remote Desktop Connection using the public IP address (<b>20.118.218.35</b>) of VM-osTicket
</p>

<p>
<img src="https://i.imgur.com/qiFSgFs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<b>2.) Install / Enable IIS under Programs > Windows Features with the following:</b>

- World Wide Web Services >
  - Application Development Features > CGI
  - Common HTTP Features > All
<img src="https://i.imgur.com/6czKMBe.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/CrORIAy.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

</p>

<p>
<b>3.) Download/Install PHP Manager for IIS</b>
</p>
<p>
  <img src="https://i.imgur.com/mvlgOtB.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>4.) Download/Install Rewrite Module</b>
</p>
<p>
<img src="https://i.imgur.com/1sypVUw.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>5.) Create the directory C:\PHP</b>
</p>
<p>
<img src="https://i.imgur.com/tlVC0Jz.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>6.) PHP 7.3.8 → unzip the content to C:\PHP</b>
</p>
<p>
<img src="https://i.imgur.com/okaAxm8.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>7.) Download/Install VC_redist.x86.exe</b>
</p>
<p>
<img src="https://i.imgur.com/cFVN55H.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>8.) Download/Install MySQL 5.5.62 with following configuration:</b>

- Typical Setup ->
- Launch configuration Wizard ->
- Standard Configuration ->
- Install As Windows Service
- root password: <b>Password1</b>
</p>
<p>
<img src="https://i.imgur.com/dmmfDp5.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/Fc93wox.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>9.) Open IIS as an Admin</b>
  
- Register PHP within IIS
  - Register new PHP version with path <b>C:\PHP\php-cgi.exe</b>
- Restart IIS
</p>
<p>
<img src="https://i.imgur.com/sHNxe80.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/NFeXWgQ.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/ZQbPKcA.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>10.) Install osTicket v1.15.8</b>
  
- Extract and copy “<b>upload</b>” folder to <b>C:\inetpub\wwwroot</b>
- Within <b>C:\inetpub\wwwroot</b> folder, rename “<b>upload</b>” to “<b>osTicket</b>”.
</p>
<p>
<img src="https://i.imgur.com/If7l8Pf.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>


<p>
<b>11.) Restart IIS</b>
  
  - Go back to IIS, sites > Default > osTicket
  - Go to PHP Manager and click “<b>Enable or disable an extension</b>”
    - Enable: <b>php_imap.dll</b>
    - Enable: <b>php_intl.dll</b>
    - Enable: <b>php_opcache.dll</b>
  - Go to “<b>Browse *:80</b>” and changes are reflected to the site.
</p>

<p>
<img src="https://i.imgur.com/a1pe9JF.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/27T7fGO.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>12.) Rename ost-config.php</b>
  
  - From C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  - To C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<p>
<img src="https://i.imgur.com/gO7LITH.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>13.) Assign permission for ost-config.php</b>
  
  - <b>Disable inheritance</b> - remove all
  - New permission - everyone - all
</p>
<p>
<img src="https://i.imgur.com/v6nsXHP.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/kPEoygG.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>14.) Continue to setup screen on osTicket browser</b>
 
  - Go to IIS > site > default > osTicket > <b>browse *:80 (http)</b>
  - Add helpdesk name, default email, first and last name, username, and password
</p>
<p>
<img src="https://i.imgur.com/uta9nHz.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/vmMKNA2.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>15.) Download/Install HeidiSQL</b>
  
- Open Heidi SQL
- Create a new session, root/Password1
- In Heidi SQL, right click <b>Unamed</b> > <b>Create New</b> > <b>New database</b>
- Create a database called “<b>osTicket</b>”
</p>
<p>
<img src="https://i.imgur.com/SL3f7Ma.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/DmbTnp8.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/5uwkfAq.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
<b>16.) Continue Setting up osTicket in the browser</b>
  
  - MySQL Database: <b>osTicket</b>
  - MySQL Username: <b>root</b>
  - MySQL Password: <b>Password1</b>
  - Click: <b>Install Now</b>
</p>
<p>
<img src="https://i.imgur.com/z9i9v5B.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>

<p>
- Browser to the help desk login page: http://localhost/osTicket/scp/login.php
- End Users osTicket URL: http://localhost/osTicket/ 
</p>

<p>
<b>17.) Clean up</b>
  
  - Delete C:\inetpub\wwwroot\osTicket\setup
  - Set Permission to “<b>Read</b>” only:
  - C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>

<p>
Full configured osTicket
  
- Help desk login page: http://localhost/osTicket/scp/login.php
</p>

<p>
  
- End user page: http://localhost/osTicket/ 
</p>
