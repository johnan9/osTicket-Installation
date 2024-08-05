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
<img src="https://i.imgur.com/Clzj7Xs.png" height="80%" width="80%" alt="Logo"/>
</p>
<br />

<p>
2.) Install / Enable IIS in Windows Features with the following:

- Web Management Tools > IIS Management Console
- World Wide Web Services >
  - Application Development Features > CGI
  - Common HTTP Features
</p>

<p>
3.) Download/Install PHP Manager for IIS
</p>

<p>
4.) Download/Install Rewrite Module
</p>

<p>
5.) Create the directory C:\PHP
</p>

<p>
6.) PHP 7.3.8 → unzip the content to C:\PHP
</p>

<p>
7.) Download/Install VC_redist.x86.exe
</p>

<p>
8.) Download/Install MySQL 5.5.62 with following configuration:

- Typical Setup ->
- Launch configuration Wizard ->
- Standard Configuration ->
- Install As Windows Service
- password: <b>Password1</b>
</p>

<p>
9.) Open IIS as an Admin
  
- Register PHP within IIS
  - Register new PHP version with path C:\PHP\php-cgi.exe
- Restart IIS

</p>

<p>
10.) Install osTicket v1.15.8
  
- Extract and copy “upload” folder to C:\inetpub\wwwroot
- Within C:\inetpub\wwwroot folder, rename “upload” to “osTicket”.

</p>

<p>
11.) Restart IIS
  
  - Go back to IIS, sites > Default > osTicket
  - Go to PHP Manager and click “Enable or disable an extension”
    - Enable: php_imap.dll
    - Enable: php_intl.dll
    - Enable: php_opcache.dll
  - Go to “Browse *:80” and changes are reflected to the site.

</p>

<p>
12.) Rename ost-config.php
  
  - From C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  - To C:\inetpub\wwwroot\osTicket\include\ost-config.php

</p>

<p>
13.) Assign permission for ost-config.php
  
  - Disable inheritance - remove all
  - New permission - everyone - all
</p>

<p>
14.) Continue to setup screen on osTicket browser
  
  - Add helpdesk name, default email, first and last name, username, and password
</p>

<p>
15.) Download/Install HeidiSQL
  
- Open Heidi SQL
- Create a new session, root/Password1
- Connect to the session
- Create a database called “osTicket”
</p>

<p>
16.) Continue Setting up osTicket in the browser
  
  - MySQL Database: osTicket
  - MySQL Username: root
  - MySQL Password: Password1
  - Click “Install Now”
</p>

<p>
  
- Browser to the help desk login page: http://localhost/osTicket/scp/login.php
- End Users osTicket URL: http://localhost/osTicket/ 
</p>

<p>
17.) Clean up
  
  - Delete C:\inetpub\wwwroot\osTicket\setup
  - Set Permission to “Read” only:
  - C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>

<p>
Full configured osTicket
  
- Help desk login page: http://localhost/osTicket/scp/login.php
</p>

<p>
  
- End user page: http://localhost/osTicket/ 
</p>
