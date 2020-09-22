<div align="center">

## VB6 Apps and Vista


</div>

### Description

Discussion of Installation of Vb6 Applications on Vista under the new default limited access standard user.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Anthony Awx](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/anthony-awx.md)
**Level**          |Intermediate
**User Rating**    |4.5 (54 globes from 12 users)
**Compatibility**  |VB 6\.0
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__1-1.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/anthony-awx-vb6-apps-and-vista__1-66696/archive/master.zip)





### Source Code

While this is not a 'code' article per say, I believe it is worth posting here, since most of us want our applications to work on Vista (right?). No votes necessary - just some food for thought to perhaps assist you in making your applications work on Vista, or, so you know what to expect. I hope you find it helpful.
<br><br>
I (like perhaps many of you) am trying to figure out how we can use our apps on Vista. The vb6 apps themselves will work on Vista. The largest 'snag' of it all is, in Vista, ALL applications get run as a standard (non-admin) user.
<br><br>
While some Win2000 and XP systems are set up like this, typically, they are in large corporate environments where workers UNDERSTAND they cannot install or run any software they want. On Vista, ALL USERS will be faced with this limitation, and I fear, will not understand how to get software installed (I am beginning to wonder if Vista will be successful at all).
<br><br>
So, over the past several weeks, I have been tinkering around, trying to resolve the following objectives:
<br><br>
1) Enable a standard (non-admin) user to INSTALL our software.<br><br>
2) Enable a standard (non-admin) user to RUN our software.
<br><br>
I want do discuss each one, because I believe they are very important to understand, and, I am looking for any additional opinions and thoughts on these very essential topics:
<br><br>
<br><br>
===========
1) The first one (INSTALLING as non-admin) is perhaps a bit contraversial. The whole purpose (I presume) of a standard user is to NOT allow them to install software. However, our users right now pretty much ALL run on single-user (non-corporate) systems, which means, whether they realize it or not, they are operating with full admin priviledges, and can therfore install any software they choose.
<br><br>
Installers typically WRITE FILES to the c:\program files\ folder, and make several registry entries (ocx and dll files). Both of these tasks are impossible as a standard user.
Therefore, a standard user under Vista (again, this is THE DEFAULT), in order to install most software, will need to run the installer as admin.
<br><br>
Will our users understand how to do that? Hmm.. I think they might just think its broke, or, doesn't work with Vista, and move on to another piece of software.
<br><br>
People don't read instructions -- they double click, and click OK OK OK. If the message says RUN THIS INSTALLER AS ADMIN etc etc, they are just going to click OK. Nothing will happen, and they will wonder what is going on. They will not understand what 'AS ADMIN' means, and my guess is, we will lose half of our prospects!
<br><br>
Our solution? <br>
Well, still working it out, but here is what we KNOW WILL WORK:
<br><br>
1) Wrap the OCX and DLL files into the EXE.
There is a very nice software program called molebox that enables you to wrap your dll and ocx files into your vb6 exe. When your user runs the exe, the dll and ocx are extracted into MEMORY instead of getting registered with the registry. We are still testing it out, but so far, it has been a dream come true. Highly recommended!
<br><br>
2) Set the default install path to the Vista equivalent of c:\documents and settings\all users\application data\appname\ (I believe it is c:\users\public\application data\).
<br>
I don't like doing this, but right now, I dont see any other way to enable Vista users to be able to install software without having to understand the admin rights system. The net result of installing here is what a user running Win98 or WinME or XP-with-admin-rights gets - just double-click the installer, click NEXT NEXT NEXT or OK OK OK, and it gets installed.
<br><br>
<br><br>
==========
2) Enabling a standard user to RUN the application is highly dependent on WHERE the application is installed.
<br><br>
Up until now, we have installed all applications and its data files together -- in other words, everything gets installed into c:\program files\appname\, and the .exe expects to be able to read and write files and folders within that directory.
<br><br>
Apparently since Windows 2000, the recommended methodology is to write the data files to c:\documents and settings\all users\application data\{companyname}\{appname}\ or c:\documents and settings\{your_user_name}\application data\{companyname}\{appname}\.
<br><br>
YUK! No offense, but our users are not developers or very technical. Add the fact that the \application data\ folder is HIDDEN by default, there was just no hope to using this.
<br><br>
Vista changes (or forces upon us) a revisit to this. You see, in Vista, EVEN IF YOU ARE THE ADMINISTRATOR running an application, the application itself DOES NOT RUN with admin rights. This means that the application CAN NOT WRITE to its own folder in the c:\program files\ folder. In other words, if you application sits inside of c:\program files\app1\, and tries to write a file named c:\program files\app1\data.txt, it will fail in Vista! Note: You can FORCE the application to run using admin rights, but most users will not know how to do that, and, it takes several extra steps to do it.
<br><br>
The solution:
<br><br>
1) Recode our software to point all of its reading and writing to the ..\application data\ folder mentioned above. I personally don't like this, but, perhaps in the long run, users will get used to it. I think the application, and its data, should be in one place - I may be in the minority on this though.
<br><br>
2) Install the application as well as the data files into the ..\application data\ folder. I talked about this above. Not sure this is a good way to do it, but it is transparent to the user, and more importantly, easier for users to get INSTALLED since they wont need to be admin to install the files there.
<br><br>
===============
I hope this is helpful to some of you, and, I hope some of you will contribute to the thread. I am certainly not an expert at any of this, and am hopeful some of you guru's out there can contribute some godly logic to this.
<br><br>
Thanks -
--
Anthony Dunleavy
http://onenerd.blogspot.com/

