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

- Create Virtual Machine in Azure
- Install Web Platform Installer
- Install osTicket v1.15.8
- Install HeidiSQL

<h2>Installation Steps</h2>

### Create Virutal Machine in Azure

Create a Resource Group

![Image](assets/resource.png)

Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs When creating the VM, allow it to create a new Virtual Network (Vnet):

Windows Virutal Machine

![Image](assets/windows.png)


Connect to your Virtual Machine with Remote Desktop

![Image](assets/remote.png)

Install / Enable IIS in Windows WITH CGI

 World Wide Web Services -> Application Development Features -> [X] CGI

![Image](assets/iis.png)

Download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

![Image](assets/php.png)

Download and install the Rewrite Module (rewrite_amd64_en-US.msi)
 
 ![Image](assets/rewrite.png)
 
Create the directory C:\PHP

![Image](assets/dir.png)

Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP

![Image](assets/unzip.png)

Download and install VC_redist.x86.exe

![Image](assets/visual.png)

Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)

Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Password1

![Image](assets/mysql.png)

![Image](assets/sql-p.png)

Open IIS as an Admin

![Image](assets/iis-admin.png)

Register PHP from within IIS

Reload IIS (Open IIS, Stop and Start the server)

![Image](assets/enablephp.png)



Install osTicket v1.15.8

Download osTicket (download from within lab files: link).

Extract and copy the “upload” folder INTO c:\inetpub\wwwroot:

![Image](assets/upload.png)

Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”:

rename to osTicket

![Image](assets/upload-rename.png)

Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket:

On the right, click “Browse *:80”:

![Image](assets/osTicket.png)


Enable Extensions in IIS: Note that some extensions are not enabled

Go back to IIS, sites -> Default -> osTicket.

Double-click PHP Manager:

Click “Enable or disable an extension”.

Enable: php_imap.dll.

Enable: php_intl.dll.

Enable: php_opcache.dll:

![Image](assets/php_extensions.png)

Refresh the osTicket site in your browser, observe the changes

![Image](assets/refersh.png)

Rename

From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php.

To: C:\inetpub\wwwroot\osTicket\include\ost-config.php:

![Image](assets/ost.png)

Assign Permissions: ost-config.php

Disable inheritance -> Remove All:

![Image](assets/disable.png)

New Permissions -> Everyone -> All:

![Image](assets/everyone.png)


Continue Setting up osTicket in the browser (click Continue)

Name SnehHelpdesk.

Default email (receives email from customers):

![Image](assets/continue.png)

![Image](assets/helpdesk.png)



> Download and Install HeidiSQL

![Image](assets/heidi.png)

Create a new session, root/Password1.

Connect to the session:

![Image](assets/2ndheidi.png)

Create a database called “osTicket”:

![Image](assets/Database.png)



> Continue Setting up osTicket in the browser

MySQL Database: osTicket

MySQL Username: root

MySQL Password: Password1:

Click “Install Now!”

Congratulations, hopefully it is installed with no errors!

![Image](assets/final-install.png)



> Clean up

Delete: C:\inetpub\wwwroot\osTicket\setup:

![Image](assets/delete.png)

Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php:

![Image](assets/disable.png)

![Image](assets/disallow.png)



> Login to the osTicket Admin Panel (http://localhost/osTicket/scp/login.php)

![Image](assets/finish.png)



I wish you luck installing osTicket using this guide.

And right now, you may practice running your own fictitious help desk locally to be ready for a job in an IT support or help desk role.

💡 Do not forget clean up your environment in Azure.

### *References:*
[Link to download files](https://docs.google.com/document/d/12QH7yrsaiUfYNOgZK7KgTSZQSJ-HYTSVcGFildWMRig/edit#)

