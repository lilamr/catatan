00:00:00	hello and welcome to bite my pie in this video we're going to get up and running with ubuntu server if you're not familiar with it this is a linux operating system made for servers the word server may sound daunting at first but don't let it put you off from little raspberry pies to honking great racks of machines proliferating data centers across the world almost any device can be turned into a server and it can be as simple or complex as you want to make it but why run a server you may ask well

00:00:31	perhaps you'd like to serve your own website or share some files maybe you'd just like a place to keep backups of your data or a device to act as a central hub for your media collection then again you might simply be curious as to how to set one up whatever the reason if building your own server sounds of interest to you stick around when setting up a server we first need to consider the hardware in this video i'll be putting ubuntu server on a mini pc with an intel cpu but the operating system is available

00:01:12	for multiple platforms whatever device you intend to use i'd suggest there are four main considerations what you choose for each of these will depend on what type of server you're going to run for example a file server may be better suited to a low power processor to save on energy costs but will need plenty of storage to house your data a web server on the other hand may require a decent amount of ram especially if lots of people are accessing it whereas unless you're hosting videos the amount of storage

00:01:41	will be considerably less when it comes to the physical size this will most likely depend on where you intend to store your server if we look more closely at ubuntu server the minimum requirements are actually quite modest but these should be seen as the absolute bare minimum and increase considerably for the optimal user experience for reference these are the specs of the little server i'm going to set up one final note on the subject of hardware i would strongly advise that the server is connected to your router

00:02:10	with a network cable ubuntu server can be installed on physical hardware or as a vm using software such as xc png or proxmox the advantage of virtual machines is that you could run several ubuntu servers all on the same physical hardware if you're planning to do this be aware that each vm will consume a portion of the underlying computer's resources for example if you're going to run two virtual servers assigning four gigabytes of ram to each the host machine would need to have at least eight gigabytes of available ram

00:02:44	notice how i said available ram due to the hypervisor itself also requiring memory the actual hardware would need to consist of more than this while virtual machines certainly have their uses in this video we'll be installing ubuntu server directly onto the bare metal that said if you'd like to start your journey into the magical world of virtualization check out my virtualbox video i've put a link in the description okay let's go grab the software we're going to search for ubuntu and it's this one we want ubuntu.com

00:03:19	let's click on the download tab and then on get ubuntu server from there select option two manual server installation and then click on download ubuntu server and save that to your computer depending on the speed of your internet connection the download may take a little while so while that's downloading let's search for another piece of software those who have watched my channel before are probably familiar with this one and it's called etcher we can get it from bellina dot io i'm going to grab the portable version

00:03:53	for windows and save that to my downloads directory once both of those have finished downloading you can close the web browser and now let's go and find them at this point i'm going to pop a usb stick into my computer and we're going to use etcher to copy the ubuntu server image we just downloaded onto it so first click flash from file then open the ubuntu server image hopefully your usb stick has been detected if not click change to select it and then we're going to click on flash and click yes to keep windows happy i'll

00:04:33	pause the video and come back when it's complete great now that that's done we can close any open windows and remove the usb stick connect the usb stick to your soon to be server and power on the computer then tap whichever key allows you to enter the boot menu or uefi bios if your mouse isn't supported use the cursor keys to highlight the usb stick entry and press enter to select it from the menu make sure that install ubuntu server is selected the installation of ubuntu server is basically the same whether you're

00:05:09	installing it in a virtual machine or on physical hardware so the following steps should be suitable for either scenario first we need to select our language so i'll use the cursor keys on my keyboard to highlight english uk and then press enter to select it next we need to choose the layout of our keyboard if this isn't correct use your cursor keys again to highlight the entry and press enter to select it you can then choose the one that you actually want from the list with that amended return to done and

00:05:40	then press enter to continue with our server connected directly to the router it should have automatically picked up an ip address but since this is a server we don't want this to change and for that reason we need to set what's known as a static ip address this can basically be done in one of two ways either on the server itself which is what i'll be doing here or on the router if you'd like to set yours on the router or just aren't sure about setting ip addresses in general feel free to have a look at my static ip

00:06:12	video i've put a link in the description to use this method you'll probably need your server's mac address and i'll show you how to obtain that in the networking section of this video if you're going to use your router to set your server's ip address you can simply select done on this screen to proceed to the next step but for those like me who would rather set the ip address manually let's press enter on the entry for the network adapter from here select edit ipv4 and then change automatic dhcp to manual

00:06:45	the first thing we need to do is enter our network subnet this is in the format network address forward slash subnet mask so for my network that would be 192.168.0.0 forward slash 24. hopefully you already know the ip range of your network again if you're not sure what i'm talking about have a gander at my static ip video let's say your network goes from 192.168.1.0 to 192.168.1.255 the network address is the very first one on a home network you're most likely using what is known as a class c address and here for the subnet entry we

00:07:25	need to enter the cider or classless inter-domain routing notation which for a class c network is slash 24 rather than its more common subnet mask notation which would be 255.255.255.0 next we need to enter the static ip address that we'd like to set i'm going to go with 192.168.0.200. be aware that we need to use an ip address that is outside of our router's dhcp range this is to avoid conflicts with other devices on our network that have been automatically given an address by the router the gateway

00:08:02	is the ip address of your router in my case this is 192.168.0.1 if you're not sure what yours is on a windows computer you can type ipconfig into the command prompt and the address will be listed next to default gateway for name servers we need to enter the ip addresses of the dns servers that we would like our server to use you could just enter the ip address of your router again if you'd like to use your internet service provider's dns server alternatively and what i'm going to do here is enter a couple of public dns

00:08:35	servers i'm going to use google's note if you enter more than one ip address you should put a comma and a space between them you have the option to include local search domains these are more useful in environments with lots of computers like a large business so i won't be entering anything in here okay let's save our entries and you can see quite quickly that the ip address has changed with the static ip address set let's select done to continue it's very unlikely on a home network that you'll be using a proxy server

00:09:11	but if you are you can enter its address here i'm going to select done to continue again the mirror address is what will be used to keep your server up to date and the default should be just fine here we need to configure our server's storage this is for the system drive the one that will contain the ubuntu operating system and it's going to use the entire disk so anything on there will be wiped if your server has more than one drive you can choose which one you want to use i'm going to leave it on the smaller

00:09:40	disk as i'll be using the larger ssd to store my data lvm or logical volume management can be useful but i won't be using it in this particular video so i'm going to deselect that and from there i'll continue with done this page gives us a summary of what it's about to do you can see that it's going to create two partitions on the system drive a small boot partition and a much larger one for root since i'm happy to proceed i'm going to select done and here we get a warning that continuing will begin the installation

00:10:13	process and wipe the data from any of the disks we've chosen so select continue to begin on this screen we're going to set up an admin account for our server and also give the server its name so first pop in a name for the account then press the tab key to move down to the next line now give your server a name i'm going to go with the highly original server then enter a username for the account it's a good idea to keep this all in lowercase and finally create a password and then confirm it and with that complete we can select

00:10:49	done it's often preferable to run a server without a monitor keyboard and mouse attached this is what's known as a headless server but in order to do this we need to be able to connect to it remotely and to do that we need to install the open ssh server package so press the space bar to put a cross in the install open ssh server box and then select done ubuntu server comes with a selection of snap packages that can be installed as part of the installation process personally i prefer to install the

00:11:20	server operating system first and then add any additional software later on so i'm going to press the tab key and choose done the installation may take a little while so i'll pause the video and come back when it's complete marvellous when it says install complete at the top press the tab key twice to highlight reboot now and then press enter to do so when you get this prompt remove the usb stick and press enter again if you get a screen similar to this just press the enter key to reach the login

00:11:55	prompt and congratulations you've successfully installed ubuntu server so let's log in by entering the username and password that we created during the installation and i'm going to clear the screen by typing the word clear and pressing enter and here we are logged into our brand new server though it doesn't look very exciting the command prompt actually tells us a few useful things firstly we can see that i'm logged into the user account by my this will be the name you chose for your user account

00:12:27	then following the at symbol we have the name of our server which in my case is simply server after the colon there is a tilde this represents the directory we're currently accessing which is the user's home directory we can confirm that's the case by typing pwd and pressing enter and you can see that i am indeed in forward slash home forward slash byte my pi to log out of the server just type exit and press enter perhaps one of the most important areas when it comes to servers is security so let's first make sure

00:13:01	that our server is bang up to date and we can do that by running the following two commands sudo apt update as this is an administrative command you'll need to pop in your password and then enter sudo apt upgrade and yes we do want to continue after running an update it's not a bad idea to restart the server and we can do that by entering sudo reboot running manual updates is all well and good but perhaps a better way is to automate the process ubuntu server should have the unattended upgrades package installed by default

00:13:47	but we can double check by running sudo apt install unattended dash upgrade then pop in your password and as you can see the server already has the newest version of the package as part of the automation it can be useful to allow the server to automatically restart itself to complete the update procedure and to do this we need to install another package so type sudo apt install update dash notifier dash common and it looks as though that one's already installed as well so if i clear the screen all that's left

00:14:32	to do is check the configuration to do that we're going to head to apps config directory by typing cd space forward slash etc forward slash apt forward slash apt.conf dot d you can see that we're now in the new directory as the command prompt has changed and we can list its contents by typing ls there are two files here that we're interested in the first is 50 unattended dash upgrades and to open it in the nano text editor we're going to type sudo nano 50 unattended dash upgrades if it asks for your

00:15:12	password pop that in there are three parts we should check in here the first is this unattended upgrade allow origins section specifically you want to make sure that the three highlighted lines aren't commented out if any of them were they would have two forward slashes at the start like in this highlighted line if that was the case simply remove the forward slashes fortunately this already looks good which means that the security updates will be applied automatically the second thing to check is the

00:15:41	automatic reboot line rather than trudging through the file trying to find it we can do a search so hold down the control key on your keyboard and press w and when the search bar appears type automatic dash reboot and press enter and hopefully it's taken you to this unattended upgrade automatic reboot false line use the arrow keys to move the cursor to beneath the letter u near the start of the line and then press the backspace key twice to uncomment the code next move along the line again and this time

00:16:18	remove the word false and instead type in true we've now told the server to restart automatically following an unattended upgrade and then the third entry we want to look at is here unattended upgrade automatic reboot time again we need to uncomment it at the start and then we're going to set the time so remove the current entry and then enter your own this is the time of day that the server will carry out its automatic restart in this case i've just set it to one o'clock in the morning and with that done we need to save our

00:16:54	changes so press control x on the keyboard then type y and press enter okay let's clear the screen and now let's check out the second config file this one's called 20 auto dash upgrade so let's open it with sudo nano 20 auto dash upgrade and as you can see there's a lot less going on in this one whereas the first config file we looked at contain the auto update settings this one actually enables them the first line makes sure that the software package lists are up to date so that the server gets the latest

00:17:31	available packages whereas the second enables the unattended upgrade itself the important thing to check other than both of these lines being present is that each of them is set to one as this is what enables the entry with that done press control x to exit out of there if you made any changes remember to save them right with the unattended upgrades configured let's restart the server for the changes to take effect the final thing worth checking is that this automatic update service is running okay and we can do

00:18:06	that by entering sudo systemctl status unattended dash upgrade and then enter your password and as you can see it's active and running to check the network connections on the server we can type ip and then an a this machine has two network adapters one wired which is what i'm using and another wireless adapters starting with the letters en are wired whereas those beginning wl are wireless if you're looking for the network adapter's mac address it should be listed next to link slash ether the network configuration is stored in

00:18:47	the zero zero dash installer dash config.yaml file located in the etsy netplan directory to take a closer look at this we can open it in the nano text editor by typing sudo nano forward slash etc forward slash netplan forward slash double zero dash installer dash config dot yaml if like me you earlier configured the server's wired network adapter with a static ip address the addresses should be familiar if you needed to make changes to any of these you can do so in here just remember to save the file when you

00:19:27	exit i'm just going to press ctrl x to exit out of there if you did make any changes you should enter the command shown on screen to apply them but if you were just browsing that's not necessary either if you recall during the installation we also installed ssh to allow us to remotely access our server if you chose not to do this but then later change your mind don't worry as you can soon add this functionality with the following command sudo apt install open ssh dash server enter your password and as you can see

00:20:04	i've already got the newest version installed but you could continue to install the package okay with the server now ready to accept a remote connection i've moved over onto a windows pc to try to connect first things first we need to make sure that the open ssh client is installed so open settings and head to apps from there click on optional features you're looking to see if the open ssh client is already in the installed list you can see that mine already is but if that wasn't the case you can click on add a

00:20:37	feature to add it i'm going to close out of there and now we can open the command prompt by typing cmd in the search box and selecting it to remotely connect into our server we need to type ssh followed by the username of the server account which in my case is by my pi the at symbol and then the ip address of the server which for me is 192.168.0.200. then enter that as it's the first time connecting we need to type yes to accept the server's fingerprint and then press enter and then enter the password for the

00:21:14	account on your server all being well you should now be successfully connected and you can carry out server tasks from the comfort of your desktop pc or laptop if you're planning on running your server headless now would be a good time to disconnect its monitor and keyboard to log out from the remote session just type the word exit and then you can close the window once installed and updated like many server operating systems ubuntu server in and of itself doesn't actually do much out of the gate

00:21:47	but what it does do is give us an excellent base on which to build so depending on what you plan to do next you may have gone far enough with this video but for those who want to roll up their sleeves and delve a bit deeper i'm going to run through a few of the more manual server tasks you may wish to consider now i know that not everyone likes the linux terminal maybe it's the endless gloom of a black background or the reams of text that can appear on screen perhaps a pretty gui simply offers a more comforting

00:22:16	environment whatever the reason if you'd like to add a desktop to your server that's what we'll be doing in this part of the video be aware that ubuntu server in its standard form uses far less resources than having a desktop bolted on top so if you intend to do this first think about your hardware and whether it's up to the job that said to try and keep the load down as much as possible we'll be installing a lightweight desktop environment known as lxde so to get started enter the following command

00:22:45	sudo apt install lxde dash core lx appearance lxde core will give us a minimal desktop but adding lx appearance will enable us to change the look and feel of the desktop should we wish to do so pop in your password you can see straight away how much extra software is required to run a gui even a lightweight one like lxde let's enter y to continue here we need to choose the default display manager as it tells us this will provide a graphical login window since we're trying to keep things as lightweight as possible

00:23:28	use your cursor keys to highlight light dm and then press enter to select it once the installation is complete let's restart the server and just like that you should now have a graphical login window before logging in make sure you click the ubuntu logo and select lxde and then enter your password to log in the desktop might not look like much but you now have a taskbar with a start menu giving you easy access to multiple tools indeed in the preferences section you'll find customized look and feel

00:24:10	this is the lx appearance package we installed if you'd like to customize your desktop next to the start menu we have a file manager and then over on the bottom right hand side as well as volume networking and time we also have a power button so you can easily restart your server at the moment in order to use this desktop we have to log into our server directly but what if you'd prefer to access it remotely over your local network well to do that we need to install some software open the start menu

00:24:42	and head to system tools we need to open lx terminal it's handy to put a shortcut to this on the desktop so let's right click on it and select add to desktop and then double click the shortcut to open the terminal emulator the first command we need to type is sudo apt install xrdp then pop in your password and yes we do want to continue with the xrdp package installed we need to edit its configuration file so i'm going to clear the screen and type sudo nano forward slash etc forward slash xrdp forward slash

00:25:26	start wm we need to head to the end of the file now you could use the cursor keys but a much faster way is to hold down the control key and press end if you use the arrow keys to move the cursor to the start of the test line we're going to comment it out by typing hash and then we're going to do the same thing on the exact line as well go back to the end of the file and press the enter key to create a new line and then type lx session space dash s space lxde all in capital letters space dash e space lxde once more in capital letters

00:26:09	then save and exit the file by holding down the control key and pressing x typing y and pressing enter then the last thing we need to do is add the xrdp user to the ssl cert group and we can do this by typing sudo add user xrdp ssl dash assert and now let's just do a reboot to make sure that all those changes take effect okay so i'm back on my windows computer and i'm going to open a remote desktop connection then type in the ip address of my server and click connect and then yes then we need to enter our username

00:26:55	and password for the ubuntu server and finally click on ok and that's it we're now remotely logged in to the ubuntu server desktop you can tell it's a remote session from the bar at the top of the screen and when you want to leave the server you can either come to the start menu and log out or alternatively if you'd like to leave something running on the desktop you can exit the session with a little cross and then return to it later in a moment i'll be dropping back into the dark recesses of the console window

00:27:27	or command prompt but if you've installed the desktop and want to continue following along just enter any of the commands into the lx terminal a more lightweight approach to administering our server through an easy to use interface would be to install a web console and a great tool for the job is cockpit once installed we'll be able to access the ubuntu server from any computer on the local network using nothing more than a web browser so let's get started first make sure that the software package manager is up to date by running

00:28:00	sudo apt update and enter your password to proceed and then type sudo apt install cockpit and yes we do want to continue when it's finished installing let's check that it's running by entering sudo system ctl status cockpit dot socket as you can see it's active and listening there's one more thing we need to do before using cockpit ubuntu server has changed its network manager and it no longer works with cockpit's default configuration but this is easily fixed so let's type sudo nano forward slash etc

00:28:51	forward slash netplan forward slash double zero dash installer dash config dot yaml and then press enter to edit the file you're looking for the line that says version two and then directly beneath it we're going to insert a new line press the space bar to indent it to the same position as the line above and then type renderer colon space network manager or one word with a capital n and a capital m and when you've done that hold down the control key and press x then press y and enter to save the

00:29:29	changes and exit to make our new configuration take effect we need to enter sudo netplum troy and then press enter again to accept the new configuration and with that done we can log out by typing exit note that it now gives us the address of the web console that we've just set up on a computer on the same network as the server we're going to open a web browser and then type in the web console address which is the ip address of the ubuntu server followed by a colon and the port number 9090 since cockpit uses a self-signed

00:30:09	certificate we need to click on advanced and then on proceed and here we are at the login screen for our ubuntu server's new web interface enter the same username and password that you'd use to log directly into the server to be able to carry out admin tasks you want to leave this box checked where it says reuse my password for privileged tasks and then we can click login as this isn't a video about cockpit specifically i'm not going to go through each of the settings just be aware that you can keep your

00:30:42	server up to date from the software updates section and you can even drop into the server's terminal should you wish to do so you can leave the web console by clicking your account name at the top right and selecting log out next back in the server console we're going to look at adding an additional user account and to do this we simply need to type sudo add user followed by the username we want for the new account i'm going to go with bits of pi if prompted enter the password for your current server account now we need to

00:31:19	enter a password for the new user account and then pop it in again to confirm it here we can enter the full name or alternatively you could just press enter to accept the default i'm not going to enter a room number so i'll just press enter on that one and the same again for work phone and home phone and also other yes the information is correct and that's it the new account is created and if we enter the home directory by typing cd forward slash home and then list the contents you can see that our new account also

00:31:58	has its own home directory at the moment bits of pi is just a standard user account so it wouldn't be able to perform any admin tasks this may well be what you want but if you need a second admin account we can easily achieve this by adding it to the sudo group to do this enter the command sudo user mod dash lowercase a dash capital g sudo and the name of your new user account which in my case is bits of pie then pop in the password for your original account if it asks for it and that's it bits of pie now has admin

00:32:37	right so let's test it out i'm going to log out by typing exit and then log in to the new account let's clear the screen and try running an admin task so i'll enter sudo apt update and then pop in the bits of pi password and as you can see the command executed successfully right let's log out of the new account and log back in to the original one now rather than logging out and back in again let's say you just wanted to switch accounts temporarily or you can do this using the su or switch user command

00:33:23	so if i type su dash and the name of the account that i want to switch into and then enter the password for that account and you can tell from the command prompt that i'm now in the bits of pi account and i can confirm this by entering the who am i command when you're ready to switch back to the original user just type exit another use for the su command is to temporarily become root this could be useful if you need to enter a lot of admin commands one after the other as it saves you from having to type sudo

00:33:58	each time so to switch into the root account type sudo su dash and then enter your account's password and we can now run admin commands without proceeding them with sudo for example sudo apt update simply becomes apt update you should be very careful while running as rude as someone once wisely said with great power comes great responsibility so let's exit out of there before we do any damage and you can see that i'm now safely back in my bike my pi account if you'd like to list all the user accounts on the server

00:34:35	you can do that by entering comp gen u for users as you can see the server contains a lot of system accounts but perhaps more importantly you should be able to see the accounts that you have created okay so what do we do if we want to remove a user well that's where the dell user or delete user command comes in so enter sudo dell user and the name of the account you want to remove then pop in your password and that's it the account is no more we can confirm this by entering the comp gen u command again and the account you just

00:35:14	removed should no longer be in the list for security reasons by default ubuntu server doesn't allow you to log in using the root account while this is a good idea there may be times when you're setting up a server that you need the root account to be fully active so if you're facing such a scenario you can type sudo p a double swd root you need to create a password for the root account and then confirm it and now if we log out we can log in as root note whenever you're running as root the command prompt changes to the hash sign

00:35:56	instead of the usual dollar right let's exit out of there if you later decide that you'd sooner restrict access to the root account after all just type sudo p a double swd dash l root then pop in your password and congratulations you've just disabled the root account login while it's best to get the name right from the start it is possible to rename your server let's say i got fed up with the generic server and wanted to change it to fort knox we can explicitly show the name of our server by typing

00:36:33	hostname for even more information you could type in hostname ctl now to change the name let's type sudo hostname ctl set dash hostname and then what you want to change it to which i'm going with for knox and then we need to enter our password and if we type host name now you can see that the server has a new name notice at the moment the prompt hasn't updated to reflect the change this is easily remedied by typing in exec bash if you do decide to change your server's host name there's one more

00:37:14	thing you should take a look at as the server boots it maps local host names to ip addresses these are stored in the etsy hosts file and we can view them by entering cat forward slash etc forward slash hosts we can clearly see that this still contains the old name of our server so to update that let's edit the file by typing sudo nano forward slash etc forward slash hosts use the cursor keys to navigate to the end of your old server name and the backspace key to delete it and then type in the new name for your

00:37:52	server with that updated we need to save the file and we can do that in the nano text editor by holding down the control key and pressing x type in y and then pressing enter great so our server is now renamed to check that it knows its name i'm just going to run a ping test using the host name so i'll type ping for knox and as you can see it's replying there's a very useful tool we can add to ubuntu server that makes installing some popular packages an absolute breeze and it's called task cell so let's install it now we'll first make

00:38:33	sure that the server's package manager is up to date by running sudo apt update and then we'll install the software by typing the command sudo apt install task cell and yes we do want to continue when it's finished installing we can run it with sudo task cell and you can see that there's quite a list of things we could install for the purposes of this video i'm going to install a lamp server so i'll use the cursor keys to move down the list and then press the space bar to select that entry then if i tap the tab key i can press

00:39:19	enter to select ok and when the command prompt reappears at the bottom of the screen the installation is complete a lamp stack consists of a bundle of open source software used for running web applications lamp is actually an acronym which stands for linux apache mysql and php we've already taken care of the linux part by installing ubuntu server i'll come back to apache in a moment mysql is a database and it's a good idea to make sure this is secure by running sudo mysql underscore secure underscore installation

00:40:04	it first asks us if we want the system to check that we use secure passwords when setting up a database that's a good idea so i'll enter yes for that one you then set the policy to enforce this i'll go with number two for strong passwords now we need to create a password for the root database user and then enter it again to confirm yes i do want to continue with the password provided for security it's a good idea to remove anonymous users we also want to prohibit remote login to any databases by the root user

00:40:40	and let's also remove the test database for those settings to take effect we need to reload the privilege tables and that's the database component ready to go returning to apache which is the web server part of the lamp stack i've jumped over onto a windows pc to demonstrate this if we open a web browser and enter the ip address of our ubuntu server you can see that we've reached the default page for the apache web server i'm going to move that over open the command prompt and pop that on the other side of the

00:41:16	screen and then ssh into the server the reason i've got these windows open side by side is to look at the final part of the lamp stack php is a scripting language that is widely used in web development to reveal some information about this we first need to visit the apache servers web directory and we can do this by typing cd forward slash var forward slash www forward slash html let's list the contents of that directory if you're curious the index.html file is this apache 2 ubuntu default page that

00:41:57	we're viewing we're going to create a new file in this directory we'll use the nano text editor by typing sudo nano and then the name of the new file which will be php info dot php if it asks for it pop in your password being a new file there's nothing in it at the moment so let's enter less than question mark php press enter to start a new line and then we'll type two forward slashes which means that this line will be a comment explaining the purpose of this file as follows then on the next line type php

00:42:36	info opening bracket closing bracket semicolon then finish with question mark greater than hold down the control key and tap x type y and press enter to save and exit to see what that's done head over to your web browser and following the ip address of your ubuntu server enter forward slash php info dot php this gives us lots and lots of information about our php installation and for this reason while not critical on a home network if this was an internet-facing web server you wouldn't want to expose this so to

00:43:17	be on the safe side let's delete that anyway and we can do that by typing sudo rm php info dot php and now if i refresh the web page you can see that the information has gone to make proper use of your lamp stack you'll need some additional software what that is precisely is entirely up to you but at least you now have all of the groundwork in place if you've been watching this video from the start you may recall that my server has a second physical drive and that i mentioned i'd be using this for data storage

00:43:51	this way the operating system can continue to use the primary drive and we can keep all of our files on a separate disk to make this process a little easier if you're not already i'd recommend remotely connecting to your server using ssh as this way we'll be able to easily copy and paste one of the longer entries if we clear the screen the first thing we want to do is list the drives connected to the server and we can do this by entering lsblk on my machine i'm looking for the gigabyte ssd which is this one here sda

00:44:25	we can see that it currently contains two partitions sda1 and sda2 but i want to start over by deleting the current partition table signature and we can do that by typing sudo wipe fs dash a which stands for all and then the path to the drive which in my case is forward slash dev forward slash sda it's important that you get this last part right as you don't want to do this to the wrong drive then pop in your password to continue okay now we're going to create the new drive layout since this is going to be used for

00:45:02	storing data it's quite likely that you're using a large drive so for that reason i'd suggest you use the g disk command to partition it as this will create a gpt partition table that is better suited to bigger drives and we can do that by typing sudo gdisk and then the path to your disk which in my case is forward slash dev forward slash sda again make sure you get the right disk so as to not cause big problems right we're going to type the letter n and press enter to create a new partition we'll give it the partition number one

00:45:38	we want it to start at the beginning of the drive so press enter to accept the default and to keep things simple i'm just going to create a single partition that fills the entire drive so press enter again to do this and we can press enter again to accept the default value for the hex code or guid with that done we need to write our changes to the disk and we can do that by entering the letter w and then typing y to proceed let's have a look at our new partition by entering sudo g disk dash l and then the path to the disk

00:46:13	and here you can see my single partition now that we have a partition we need to create a file system on it in windows you've probably heard of fat32 and ntfs but as this is linux i'd suggest we use ext4 so let's type the command sudo mkfs or make file system dot ext4 and then the partition we want to create it on which in my case is dev sda1 you can see that this is simply the drive followed by the partition number if you've been following along we only created a single partition so the number should be one let's press

00:46:51	enter to execute the command if you get a message that the partition currently contains a different file system just enter y to overwrite it okay with the second drive set up we now need to mount it unlike windows linux doesn't use drive letters instead the operating system is located in the root directory when we add an additional drive to make it accessible we need to mount it within this root directory handily there is an mnt or mount folder for just this purpose so let's first navigate to that by

00:47:25	typing cd or change directory forward slash mnt next let's create a mount point this is simply a folder that will mount our disk to and we can use the mkdir or make directory command to do this so type sudo mkdir and then the name you want to give it i'm just going to go with drive to if it prompts for your password just pop it in and if we run the ls command we should see our new folder i'm going to use the cd command to enter into it now at the moment if i was to create a file within there that's actually stored on my primary

00:48:06	operating system drive that's because although we've created our mount point we haven't actually mounted the second drive to it yet if i remove that file and return to the mnt directory by the way typing cd space two dots takes you up a level from the folder you're in this is known as the parent directory we're going to make our mount point immutable this means that we'll no longer be able to put any files within it this is a good thing because if for some reason our storage drive doesn't mount

00:48:37	we don't want all of the files ending up on the disk that contains the operating system so let's enter sudo ch attr or change attribute plus i and then the name of your mount point folder to make sure that's worked let's enter the folder again and try and create another test file and as you can see it won't let us and there's no test file in the directory so now that the mount point is ready to go i'll return to the mount directory when we mount the drive we could use its dev path and partition number

00:49:15	in my case that would be forward slash dev forward slash sda1 the trouble with this method is that if at some point you took your server apart and moved the disks around there's no guarantee when you put it back together the drives would get the same labels so a much more reliable way is to use what's known as the uuid or universally unique identifier to find this for our drive we can use the sudo blk id command knowing that my partition is sda1 i can see its uuid here we're going to copy the uuid by

00:49:49	moving the mouse pointer into position holding down the left button and then dragging until everything is selected from the first u to the final quote then let go of the button hold down the ctrl key on your keyboard and press c with that copied we're going to edit a file so type sudo nano forward slash etc forward slash fs tab we could manually mount our drive but then we'd have to do it every time we restarted the server by adding an entry to the fs tab file it will mount automatically whenever the

00:50:26	server boot so use the cursor keys to go to the bottom then move your mouse pointer inside the terminal window and right click to paste to complete the line we need to type space forward slash mnt forward slash and the name of your mount point which mine is drive2 space ext4 space default space 0 space 2 so that's going to take our additional drive mount it to the mount point we created using the ext4 file system and the default mount settings the last two fields stand for dump an fsck or file system checker respectively we

00:51:07	don't need to get into their values other than to say that on an additional nun system drive these should be set to zero and two right let's hold down the control key and press x then type y and press enter to save and exit it's a good idea to check that the new entry works as advertised as an error in the fs tab file can prevent your server from starting to make sure all is well type sudo mount dash a no errors is always a good sign running that last command has just mounted any drives listed in the fstab

00:51:40	file if they weren't already from now on this will happen auto magically whenever you start the server typing df h and then the name of the mount point shows us that the second drive has indeed been mounted also if we now enter the mounted drive and i try and create a test file we can see that that was successful remember we can no longer create files inside the mount point itself but now that we're writing to the second disk all is well when it comes to adding drives there's one more area i'd like to draw your

00:52:15	attention to and that's permissions if we add a dash l to the list command we can see a bit more information at the moment this directory and everything in it is owned by root and that's one of the reasons we have to keep using the sudo command moving forwards this probably isn't what you want so let's change that now i'm going to move up into the mnt directory and then issue a command to make my current user the owner of the drive2 directory which is as follows sudo ch own or change owner dash capital r

00:52:50	followed by the username that we want to take ownership and then the name of the directory followed by forward slash pop in your password if asked and if we enter the folder again and once more list the content you can see that my account by my pi now owns the files within this directory note this is because we used the dash capital r option on the ch own command without it although we'd have still taken ownership of the directory this wouldn't have applied to any existing files within it also when it comes to file permissions

00:53:24	we need to decide what kind of access users have you've no doubt noticed the letters and dashes at the start of each entry these visually identify a file's permissions and are arranged as owner group and others if we take the test file i created earlier as an example this currently has rw or read write permission assigned to the owner and r or read permission assigned to both the group and others while we could change the permissions on this file individually it's often more useful to do it on an

00:53:53	entire directory so let's return again to the mnt directory and this time we're going to use the chmod command to modify the permissions so type sudo chmod we'll use dash capital r again to make it recursive and i'm going to go with seven five zero these numbers represent the owner group and others respectively this is what's known as octal notation and it's quicker to write than using the letters rwx as you can see from the table on screen each number represents some permissions basically you only need to remember one

00:54:29	two and four as zero being no permission kind of makes sense and three five six and seven are generated by a combination of one two and four for example read which is four plus right which is two and execute which is one adds up to seven so in the current command the number seven will give read write and execute permission in other words full control to the owner the number five will give read and execute permission to the group and the number zero gives no permissions to others which is everyone else

00:55:00	this is a reasonably secure configuration to users default so to finish we just need to put the name of the directory that we're applying it to which in my case is drive2 and i'll pop a forward slash on the end and if we return to the directory and list its content notice that the owner currently bite my pie has read write and execute permission on all of the entries the group currently root has read and execute permission and others have no permissions right so without using sudo i should now be able to make changes

00:55:34	within this folder first i'll try and remove the test file and there it was gone and now i'll try and create a new file called plenty of pi and there we have it in the last section we added an extra drive for storage which is okay but to make this really useful and to justify putting it into the server in the first place this really wants to be made available over the network there are a few ways we could achieve this nfs sftp to name a couple but i'd suggest for best compatibility with the widest

00:56:13	range of devices we use samba first let's check that the package manager is up to date and now let's install samba yes we do want to do that with the software installed we now need to configure it let's start by setting up a user account to do this use an existing account on the server and add it to samba by typing sudo smb p a double swd dash a and then the username of the existing account so i'll be using buy my pie now we need to create a samba password for this user to keep things straight forward i'd

00:56:57	suggest using the same password that you normally use for this account so i'm going to end to bite my pie's password and then confirm it with an account set up let's enter the etsy samba directory and we're going to edit the smb config file but first let's make a backup of the original and then we can edit the file by typing sudo hold down the control key and press end to jump to the end of the file and i'm going to press enter to move down one line adding a comment is optional but it's good practice to

00:57:39	describe what any code you add is going to do so if we enter a hash and then type in a short description i'll just call it my shared drive on the next line we're going to give the share a name this needs to be typed inside square brackets i'm going to go with the usually imaginative share beneath that we need to enter path space equals space and then the path to the directory that you're going to share on the server which in my case is forward slash mnt forward slash drive to moving down type in valid space users

00:58:16	space equal space and then the username of your samba account which for me is bite my pie then on the final line enter read space only space equals space and if you want to be able to write to the drive type in no okay hold down the control key and press x type y and press enter with the configuration saved we need to restart the samba service for it to take effect so let's enter the command sudo system ctl restart smbd dot service finally let's check our samba configuration for errors you can see that the services

00:58:59	file loaded okay so let's press enter to output the service definitions and there's the samba share we created at the bottom hopping over onto a windows machine it's time to try it out i'll open file explorer and type in the address bar backslash backslash the ip address of the ubuntu server backslash and then the name that you gave to your share if you recall i simply called mineshare when you've typed yours in hit the enter key and it should ask for the credentials to connect to your server so type in the username and the password

00:59:36	of the account that you added to samba if you're going to use this a lot i'd suggest ticking the box remember my credentials and then click ok to connect and that's it we now have access to our shared drive you can see the plenty of pi file that i created earlier to save us having to type the address in every time we want to connect to our share if we click on the little folder icon and drag it into quick access and then let go we now have a handy shortcut that will take us straight to our network share

01:00:07	and as a final test let's try deleting plenty of pi and creating a new folder to put things in ubuntu server ships with a built-in firewall but by default it's turned off we can see this by running the command sudo ufw status in a moment we'll turn the firewall on however you need to be careful if you're logged in remotely as you could accidentally lock yourself out this is because by default the firewall will only allow outgoing traffic and will block anything trying to get in so if you intend to use it you need to

01:00:49	make sure that ssh access is allowed and to do this we'll add a firewall rule by entering sudo ufw allow ssh with that done let's turn on the firewall by typing sudo ufw enable and if i hop over to the command prompt of a windows machine and try to connect using ssh you can see that even though the firewall is now enabled we can still connect remotely returning to the server let's say you later decided you didn't want remote ssh access after all you can block it by entering sudo ufw deny ssh now if i try and connect remotely

01:01:35	from the windows machine you can see that after a short while the connection times out with the firewall operational you need to stop and think about all of your connections to the server even on your local network for example if you set up a network share using samba you'll also want to allow access to that you can see at the moment that it's currently blocked so back on the server we need to enter sudo ufw allow samba and if i try again on the windows computer we're now allowed back in if you decide configuring firewall rules

01:02:18	isn't for you and you'd rather turn the firewall back off you can do that by typing sudo ufw disable the whole point of a server is to serve services over a network so it can be very useful to get to know the netstat command as this displays information about network connections to get the most out of it we need to run it as admin by using sudo and to get even more out of it we can add some command line options a popular set of options is tu lpn as each of these will show us a different set of data as shown on screen

01:02:55	before we can run this command we first need to install it so type in sudo apt install net dash tools to do so and now let's run the netstat command each line represents a different network connection on the left is the type of network protocol either tcp or udp we have the local address and more importantly the port number whether the connection is listening in other words services that are running waiting to be contacted and the program name or the process that's creating that particular service

01:03:36	to try and make a little more sense of what's going on here let's take this line as an example we can see this is showing us the smbd or samba service it's using the tcp protocol and operating on port 445 it's also in a listening state and so is ready to be connected to by using the netstat command we can see at a glance what services the server is making available to the network although that was a pretty whistle-stop tour hopefully the output of the netstat command no longer looks like a list of

01:04:07	meaningless text another important area when monitoring a server is resources there are a couple of popular commands we can make use of here historically there's top this shows us the processes running on the server it's useful to be able to see what's using up the server's resources particularly in situations where you may not have very powerful hardware processes using the most resources are listed at the top let's press q to quit out of there a more useful and newer alternative is h-top though even this has been

01:04:40	around since 2004 you can think of h-top as being like top on steroids perhaps most usefully it's also interactive so as well as being able to monitor the system's resources by using the commands listed along the bottom of the screen we can analyze the information more closely let's say i wanted to search for processes connected with samba if i press the f3 key and enter smb it will highlight a running process that meets this criteria pressing f3 again will find the next process running smb and we can cycle through them using the

01:05:16	f3 key looking more closely at a particular process you can see that it shows the pid or process identifier this is the number assigned to it we can also see the user that the process is running as in this case root the cpu and memory columns are especially important as these reveal the percentage of the server's processor and ram respectively that the process is currently consuming and the command column displays the location of the commands that invoke the process here is slash user slash spin smbd

01:05:48	we can press the escape key to cancel out of search another useful option is f9 kill if a process has gone awry and is gobbling up far too much of your server's precious resources you can force it to close let's say h top itself went out of control being at the top of the list it is currently using the most resources but that's just because i'm not currently asking the server to do anything else still let's pretend the process has gone rogue and we need to kill it with the process highlighted we need to

01:06:20	press the f9 key this brings up the send signal command by default it will use sig term this is the polite way of asking the process to close but if the process was particularly stubborn you could opt for something more drastic like sig kill so let's press enter to politely kill h-top and you can see that we now have the command prompt back at the bottom of the screen of course if we run h-top again the better way to exit the program is to use the f10 key a couple of tips before we wrap up this video if you're typing a command

01:06:56	particularly one where you're navigating directories you can make your life easier by using something called tab completion as an example let's say i want to get to the root directory of the apache web server if i start typing cd slash var slash but then instead of typing the full directory name www i type w and then press the tab key notice how it automatically fills in the rest of the folder name and then if i do the same thing again this time instead of typing html i just type h and press the tab key once more it

01:07:32	auto completes the entry obviously this can save you quite a bit of typing particularly where longer paths are involved the final thing i'd like to mention is the man or manual command if you get stuck and aren't sure what a command does in the terminal you can take a look at its manual hopefully by now you know the purpose of the sudo command but if you weren't sure you could type man sudo and this gives you lots of information about the particular command including any available options when you've finished looking it up

01:08:04	you can press q to exit out of there and that's it i'm now going to shut down my server but you'll probably want to leave yours running and that brings us to the end of this video this one has been a little more technical than usual hopefully there hasn't been too much snoring going on in the back row running a server isn't for everyone but for those who like to take a closer look at the nuts and bolts of the system and gain a better understanding of what's going on behind the scenes manually setting up a server is a great

01:08:37	learning experience and with five years of updates for the lts version ubuntu server is a great place to start there's a whole world of servers out there maybe now there'll be one more as you start administering your own as always if you enjoyed this video please like and subscribe and if you'd like to be notified when i post the next one just click the bell icon thanks for watching and until next time take care you


===========================================



00:00:00 halo dan selamat datang untuk mencoba kue saya. Dalam video ini kita akan memulai dan menjalankan server ubuntu jika Anda belum mengenalnya ini adalah sistem operasi linux yang dibuat untuk server, server kata mungkin terdengar menakutkan pada awalnya, namun jangan biarkan hal ini membuat Anda berhenti dari kue raspberry kecil hingga membunyikan klakson di rak mesin yang menjamur pusat data di seluruh dunia. Hampir semua perangkat dapat diubah menjadi server dan bisa sesederhana atau serumit yang Anda inginkan. tapi mengapa menjalankan server Anda mungkin bertanya dengan baik

  

00:00:31 mungkin Anda ingin menyajikan situs web Anda sendiri atau berbagi beberapa file mungkin Anda hanya ingin tempat untuk menyimpan cadangan data Anda atau perangkat yang berfungsi sebagai hub pusat untuk koleksi media Anda, tapi mungkin Anda bisa melakukannya lagi hanya ingin tahu bagaimana cara mengaturnya apa pun alasannya jika membangun server Anda sendiri sepertinya menarik bagi Anda untuk tetap menggunakannya saat menyiapkan server pertama-tama kita perlu mempertimbangkan perangkat kerasnya dalam video ini saya akan memasang server ubuntu di mini pc dengan cpu intel tetapi sistem operasi tersedia

  

00:01:12 untuk berbagai platform, perangkat apa pun yang ingin Anda gunakan, saya sarankan ada empat pertimbangan utama. Apa yang Anda pilih untuk masing-masing platform akan bergantung pada jenis server yang akan Anda jalankan, misalnya server file mungkin lebih cocok untuk prosesor berdaya rendah untuk menghemat biaya energi tetapi akan membutuhkan banyak penyimpanan untuk menampung data Anda. Sebaliknya, server web mungkin memerlukan jumlah ram yang cukup terutama jika banyak orang yang mengaksesnya, kecuali Anda menghostingnya video jumlah penyimpanan

  

00:01:41 akan jauh lebih kecil dalam hal ukuran fisik. Hal ini kemungkinan besar akan tergantung pada di mana Anda ingin menyimpan server Anda. Jika kita melihat lebih dekat pada server ubuntu, persyaratan minimum sebenarnya cukup sederhana tetapi ini harus dilihat sebagai minimum mutlak dan meningkat secara signifikan untuk pengalaman pengguna yang optimal sebagai referensi ini adalah spesifikasi server kecil saya akan menyiapkan satu catatan terakhir mengenai masalah perangkat keras saya sangat menyarankan agar server terhubung ke router Anda

  

00:02:10 dengan kabel jaringan server ubuntu dapat diinstal pada perangkat keras fisik atau sebagai vm menggunakan perangkat lunak seperti xc png atau proxmox keuntungan dari mesin virtual adalah Anda dapat menjalankan beberapa server ubuntu semuanya pada perangkat keras fisik yang sama jika Anda Jika Anda berencana untuk melakukan hal ini, ketahuilah bahwa setiap vm akan menggunakan sebagian dari sumber daya komputer yang mendasarinya, misalnya jika Anda akan menjalankan dua server virtual yang menetapkan empat gigabyte ram untuk masing-masing mesin host, maka mesin host harus memiliki setidaknya delapan gigabyte dari ram yang tersedia

  

00:02:44 perhatikan bagaimana saya mengatakan ram yang tersedia karena hypervisor itu sendiri juga memerlukan memori, perangkat keras sebenarnya harus terdiri dari lebih dari ini sementara mesin virtual pasti memiliki kegunaannya dalam video ini kami akan menginstal server ubuntu langsung ke bare metal yang mengatakan jika Anda ingin memulai perjalanan Anda ke dunia magis virtualisasi, lihat video kotak virtual saya. Saya telah memasang tautan di deskripsi oke ayo ambil perangkat lunaknya, kita akan mencari ubuntu dan ini dia yang kami inginkan ubuntu.com

  

00:03:19 mari kita klik pada tab unduh dan kemudian dapatkan server ubuntu dari sana pilih opsi dua instalasi server manual dan kemudian klik unduh server ubuntu dan simpan ke komputer Anda tergantung pada kecepatan koneksi internet Anda yang mungkin diperlukan untuk mengunduh sebentar, sementara itu sedang mengunduh mari kita cari perangkat lunak lain. Mereka yang telah menonton saluran saya sebelumnya mungkin akrab dengan yang ini dan namanya etsa. Kita bisa mendapatkannya dari bellina dot io. Saya akan mengambil versi portabelnya

  

00:03:53 untuk windows dan simpan ke direktori unduhan saya setelah keduanya selesai diunduh, Anda dapat menutup browser web dan sekarang ayo pergi dan temukan keduanya. Pada titik ini saya akan memasukkan stik usb ke komputer saya dan kita akan menggunakan etcher untuk menyalin gambar server ubuntu yang baru saja kita unduh ke dalamnya, jadi pertama klik flash dari file kemudian buka gambar server ubuntu semoga stik usb Anda terdeteksi jika tidak klik ubah untuk memilihnya dan kemudian kita pergi untuk mengklik flash dan klik ya agar windows tetap senang, saya akan melakukannya

  

00:04:33 jeda video dan kembali lagi ketika sudah selesai bagus sekarang setelah selesai kita dapat menutup semua jendela yang terbuka dan melepas stik usb, sambungkan stik usb ke server Anda yang akan segera menjadi server dan nyalakan komputer lalu ketuk tombol mana pun yang memungkinkan Anda harus masuk ke menu boot atau uefi bios jika mouse Anda tidak didukung gunakan tombol kursor untuk menyorot entri stik usb dan tekan enter untuk memilihnya dari menu pastikan bahwa instal server ubuntu dipilih instalasi server ubuntu pada dasarnya sama apakah kamu

  

00:05:09 menginstalnya di mesin virtual atau pada perangkat keras fisik sehingga langkah-langkah berikut harus sesuai untuk skenario mana pun. Pertama-tama kita harus memilih bahasa kita jadi saya akan menggunakan tombol kursor pada keyboard saya untuk menyorot bahasa inggris uk lalu tekan enter untuk memilihnya selanjutnya kita perlu memilih tata letak keyboard kita jika ini tidak benar gunakan tombol kursor Anda lagi untuk menyorot entri dan tekan enter untuk memilihnya Anda kemudian dapat memilih salah satu yang sebenarnya Anda inginkan dari daftar dengan itu diubah kembali menjadi selesai dan

  

00:05:40 lalu tekan enter untuk melanjutkan dengan server kami yang terhubung langsung ke router, seharusnya secara otomatis mengambil alamat ip tetapi karena ini adalah server kami tidak ingin ini berubah dan oleh karena itu kami perlu mengatur apa itu Dikenal sebagai alamat ip statis, ini pada dasarnya dapat dilakukan dengan salah satu dari dua cara, baik di server itu sendiri, itulah yang akan saya lakukan di sini atau di router jika Anda ingin mengaturnya di router atau tidak. yakin tentang pengaturan alamat ip secara umum, silakan lihat ip statis saya

  

00:06:12 video Saya telah memasang tautan di deskripsi untuk menggunakan metode ini Anda mungkin memerlukan alamat mac server Anda dan saya akan menunjukkan cara mendapatkannya di bagian jaringan video ini jika Anda ingin pergi untuk menggunakan router Anda untuk mengatur alamat ip server Anda, Anda cukup memilih selesai di layar ini untuk melanjutkan ke langkah berikutnya tetapi bagi yang seperti saya yang lebih suka mengatur alamat ip secara manual mari tekan enter pada entri untuk adaptor jaringan dari sini pilih edit ipv4 lalu ubah dhcp otomatis ke manual

  

00:06:45 hal pertama yang perlu kita lakukan adalah memasukkan subnet jaringan kita ini dalam format alamat jaringan subnet mask garis miring jadi untuk jaringan saya itu adalah 192.168.0.0 garis miring 24. semoga anda sudah mengetahui range ip nya jaringan Anda lagi jika Anda tidak yakin dengan apa yang saya bicarakan lihat sekilas video ip statis saya katakanlah jaringan Anda berubah dari 192.168.1.0 menjadi 192.168.1.255 alamat jaringan adalah yang pertama di jaringan rumah Anda kemungkinan besar kami menggunakan apa yang dikenal sebagai alamat kelas c dan di sini untuk entri subnet kami

  

00:07:25 perlu memasukkan notasi perutean antar-domain cider atau tanpa kelas yang untuk jaringan kelas c adalah garis miring 24 daripada notasi subnet mask yang lebih umum yaitu 255.255.255.0 selanjutnya kita perlu memasukkan alamat ip statis itu kami ingin mengatur saya akan menggunakan 192.168.0.200. perlu diketahui bahwa kita perlu menggunakan ip address yang berada di luar jangkauan dhcp router kita hal ini untuk menghindari konflik dengan perangkat lain di jaringan kita yang sudah otomatis diberi alamat oleh router gateway

  

00:08:02 adalah alamat ip router Anda dalam kasus saya ini adalah 192.168.0.1 jika Anda tidak yakin apa milik Anda di komputer windows, Anda dapat mengetik ipconfig ke dalam command prompt dan alamatnya akan tercantum di sebelah default gateway untuk server nama kita perlu memasukkan alamat ip server dns yang kita ingin server kami gunakan. Anda cukup memasukkan alamat ip router Anda lagi jika Anda ingin menggunakan server dns penyedia layanan internet Anda sebagai alternatif dan apa yang akan saya lakukan di sini adalah memasukkan beberapa DNS publik

  

00:08:35 server saya akan menggunakan catatan Google jika Anda memasukkan lebih dari satu alamat ip Anda harus memberi koma dan spasi di antaranya Anda memiliki opsi untuk memasukkan domain pencarian lokal ini lebih berguna dalam lingkungan dengan banyak komputer seperti bisnis besar jadi saya tidak akan memasukkan apa pun di sini oke mari simpan entri kita dan Anda dapat melihat dengan cepat bahwa alamat ip telah berubah dengan kumpulan alamat ip statis mari pilih selesai untuk melanjutkan sangat tidak mungkin di jaringan rumah bahwa Anda akan menggunakan server proxy

  

00:09:11 tetapi jika ya, Anda dapat memasukkan alamatnya di sini saya akan memilih selesai untuk melanjutkan lagi alamat cermin itulah yang akan digunakan untuk menjaga server Anda tetap mutakhir dan defaultnya akan baik-baik saja di sini yang kita perlukan untuk mengkonfigurasi penyimpanan server kami ini untuk drive sistem yang akan berisi sistem operasi ubuntu dan itu akan menggunakan seluruh disk jadi apa pun di sana akan dihapus jika server Anda memiliki lebih dari satu drive Anda dapat memilih yang mana yang Anda inginkan untuk menggunakannya saya akan membiarkannya lebih kecil

  

00:09:40 disk karena saya akan menggunakan SSD yang lebih besar untuk menyimpan data saya, lvm atau manajemen volume logis dapat berguna tetapi saya tidak akan menggunakannya dalam video khusus ini jadi saya akan membatalkan pilihan itu dan dari sana saya akan melanjutkan dengan selesai Halaman ini memberi kita ringkasan tentang apa yang akan dilakukan. Anda dapat melihat bahwa ini akan membuat dua partisi pada drive sistem, partisi boot kecil dan partisi yang jauh lebih besar untuk root karena saya senang untuk melanjutkan saya akan memilih selesai dan di sini kita mendapat peringatan bahwa melanjutkan akan memulai instalasi

  

00:10:13 memproses dan menghapus data dari disk mana pun yang kami pilih, jadi pilih lanjutkan untuk memulai, di layar ini kami akan menyiapkan akun admin untuk server kami dan juga memberi nama servernya, jadi pop pertama dalam nama untuk akun lalu tekan tombol tab untuk turun ke baris berikutnya sekarang beri nama server Anda Saya akan menggunakan server yang sangat orisinal lalu masukkan nama pengguna untuk akun tersebut, sebaiknya simpan semua ini dalam huruf kecil dan terakhir buat kata sandi lalu konfirmasikan dan setelah selesai kita bisa memilih

  

00:10:49 selesai sering kali lebih baik menjalankan server tanpa monitor keyboard dan mouse terpasang. Inilah yang dikenal sebagai server tanpa kepala tetapi untuk melakukan ini kita harus dapat menyambungkannya dari jarak jauh dan untuk melakukan itu kita perlu untuk menginstal paket server ssh terbuka jadi tekan spasi untuk memberi tanda silang di kotak instal server ssh terbuka dan kemudian pilih selesai server ubuntu dilengkapi dengan pilihan paket snap yang dapat diinstal sebagai bagian dari proses instalasi secara pribadi saya lebih suka instal

  

00:11:20 sistem operasi server terlebih dahulu dan kemudian menambahkan perangkat lunak tambahan apa pun nanti jadi saya akan menekan tombol tab dan memilih selesai. Instalasi mungkin memakan waktu agak lama jadi saya akan menjeda video dan kembali lagi setelah selesai luar biasa ketika dikatakan instalasi selesai di bagian atas tekan tombol tab dua kali untuk menyorot reboot sekarang dan kemudian tekan enter untuk melakukannya ketika Anda mendapatkan prompt ini lepaskan stik usb dan tekan enter lagi jika Anda mendapatkan layar yang mirip dengan ini cukup tekan enter kunci untuk mencapai login

  

00:11:55 prompt dan selamat Anda telah berhasil menginstal server ubuntu jadi mari kita login dengan memasukkan nama pengguna dan kata sandi yang kita buat saat instalasi dan saya akan membersihkan layar dengan mengetikkan kata clear dan tekan enter dan di sini kami masuk ke server baru kami meskipun tampaknya tidak terlalu menarik, command prompt sebenarnya memberi tahu kami beberapa hal berguna. Pertama, kami dapat melihat bahwa saya masuk ke akun pengguna oleh saya. Ini akan menjadi nama yang Anda pilih untuk Anda akun pengguna

  

00:12:27 lalu mengikuti simbol at kami memiliki nama server kami yang dalam kasus saya hanyalah server setelah titik dua ada tanda gelombang ini mewakili direktori yang sedang kami akses yang merupakan direktori home pengguna, kami dapat mengonfirmasinya kasusnya dengan mengetikkan pwd dan menekan enter dan Anda dapat melihat bahwa saya memang dalam garis miring ke depan home garis miring byte pi saya untuk keluar dari server cukup ketik keluar dan tekan enter mungkin salah satu area terpenting dalam hal server adalah keamanan jadi mari kita pastikan dulu

  

00:13:01 bahwa server kami sudah diperbarui dan kami dapat melakukannya dengan menjalankan dua perintah berikut sudo apt update karena ini adalah perintah administratif, Anda harus memasukkan kata sandi Anda lalu masukkan sudo apt upgrade dan ya kami ingin melanjutkan setelah menjalankan pembaruan, bukan ide yang buruk untuk memulai ulang server dan kami dapat melakukannya dengan memasukkan sudo reboot menjalankan pembaruan manual semuanya baik-baik saja tetapi mungkin cara yang lebih baik adalah mengotomatiskan proses yang seharusnya dimiliki server ubuntu paket pemutakhiran tanpa pengawasan diinstal secara default

  

00:13:47 tetapi kami dapat memeriksa ulang dengan menjalankan sudo apt install tanpa pengawasan dasbor peningkatan lalu masukkan kata sandi Anda dan seperti yang Anda lihat server sudah memiliki versi terbaru dari paket sebagai bagian dari otomatisasi, akan berguna untuk mengizinkan server untuk secara otomatis memulai kembali sendiri untuk menyelesaikan prosedur pembaruan dan untuk melakukan ini kita perlu menginstal paket lain jadi ketik sudo apt install update dash notifier dash common dan sepertinya paket itu sudah diinstal juga jadi jika saya menghapus layar semua yang tersisa

  

00:14:32 yang perlu dilakukan adalah memeriksa konfigurasi. Untuk melakukan itu, kita akan menuju ke direktori konfigurasi aplikasi dengan mengetikkan cd spasi ke depan garis miring dll garis miring ke depan apt ke depan garis miring apt.conf dot d Anda dapat melihat bahwa kita sekarang masuk direktori baru karena command prompt telah berubah dan kita dapat membuat daftar isinya dengan mengetik ls ada dua file di sini yang kami minati, yang pertama adalah 50 peningkatan dasbor tanpa pengawasan dan untuk membukanya di editor teks nano kita akan pergi ke ketik sudo nano 50 peningkatan dasbor tanpa pengawasan jika diminta

  

00:15:12 kata sandi muncul bahwa di sana ada tiga bagian yang harus kita periksa di sini yang pertama adalah peningkatan tanpa pengawasan ini izinkan bagian asal secara khusus Anda ingin memastikan bahwa tiga baris yang disorot tidak dikomentari jika ada di antara mereka yang akan melakukannya memiliki dua garis miring di awal seperti pada baris yang disorot ini, jika demikian, hapus saja garis miringnya, untungnya ini sudah terlihat bagus yang berarti pembaruan keamanan akan diterapkan secara otomatis, hal kedua yang harus diperiksa adalah

  

00:15:41 garis reboot otomatis daripada menelusuri file untuk mencoba menemukannya, kita dapat melakukan pencarian jadi tahan tombol kontrol pada keyboard Anda dan tekan w dan ketika bilah pencarian muncul ketik reboot dasbor otomatis dan tekan enter dan semoga itu membawa Anda ke pemutakhiran tanpa pengawasan ini, reboot otomatis, baris palsu gunakan tombol panah untuk memindahkan kursor ke bawah huruf u di dekat awal baris, lalu tekan tombol spasi mundur dua kali untuk menghapus komentar pada kode, selanjutnya pindahkan sepanjang baris lagi dan kali ini

  

00:16:18 hapus kata false dan ketikkan true, sekarang kita telah meminta server untuk memulai ulang secara otomatis setelah pemutakhiran tanpa pengawasan, lalu entri ketiga yang ingin kita lihat ada di sini pemutakhiran tanpa pengawasan, waktu reboot otomatis lagi, kita perlu menghapus komentar itu di awal dan kemudian kita akan mengatur waktunya jadi hapus entri saat ini dan kemudian masukkan entri Anda sendiri. Ini adalah waktu di mana server akan melakukan restart otomatis dalam hal ini saya baru saja mengaturnya ke satu jam di pagi hari dan setelah itu selesai kita harus menyelamatkan milik kita

  

00:16:54 berubah jadi tekan control x pada keyboard lalu ketik y dan tekan enter oke mari kita bersihkan layar dan sekarang mari kita periksa file konfigurasi kedua yang ini disebut 20 auto dash upgrade jadi mari kita buka dengan sudo nano 20 auto dash tingkatkan dan seperti yang Anda lihat, tidak banyak yang terjadi dalam hal ini sedangkan file konfigurasi pertama yang kami lihat berisi pengaturan pembaruan otomatis, yang ini benar-benar mengaktifkannya, baris pertama memastikan bahwa daftar paket perangkat lunak mutakhir sehingga server mendapat yang terbaru

  

00:17:31 paket yang tersedia sedangkan yang kedua memungkinkan pemutakhiran tanpa pengawasan itu sendiri, hal penting yang harus diperiksa selain dari kedua baris ini ada adalah bahwa masing-masing baris disetel ke satu karena inilah yang memungkinkan entri dengan kontrol pers yang dilakukan x untuk keluar dari sana jika Anda membuat perubahan, ingatlah untuk menyimpannya dengan benar dengan pemutakhiran tanpa pengawasan yang dikonfigurasi, mari kita mulai ulang server agar perubahan diterapkan. Hal terakhir yang perlu diperiksa adalah layanan pembaruan otomatis ini berjalan dengan baik dan dapat kita lakukan

  

00:18:06 dengan memasukkan sudo systemctl status tanpa pengawasan dasbor peningkatan dan kemudian masukkan kata sandi Anda dan seperti yang Anda lihat itu aktif dan berjalan untuk memeriksa koneksi jaringan di server kita dapat mengetik ip dan kemudian mesin ini memiliki dua adaptor jaringan satu kabel yang saya gunakan dan adaptor nirkabel lainnya yang dimulai dengan huruf en adalah kabel sedangkan yang berawalan wl adalah nirkabel jika Anda mencari alamat mac adaptor jaringan itu harus terdaftar di sebelah tautan garis miring eter konfigurasi jaringannya adalah disimpan di

  

00:18:47 file zero zero dash installer dash config.yaml terletak di direktori etsy netplan untuk melihat lebih dekat ini kita dapat membukanya di editor teks nano dengan mengetik sudo nano garis miring dll garis miring netplan garis miring ganda zero dash installer dash config dot yaml jika seperti saya, Anda sebelumnya mengonfigurasi adaptor jaringan kabel server dengan alamat ip statis, alamatnya harus familier jika Anda perlu membuat perubahan pada salah satu dari ini, Anda dapat melakukannya di sini, ingatlah untuk menyimpan file ketika kamu

  

00:19:27 keluar Saya hanya akan menekan ctrl x untuk keluar dari sana jika Anda melakukan perubahan, Anda harus memasukkan perintah yang ditampilkan di layar untuk menerapkannya tetapi jika Anda hanya menjelajah, itu juga tidak perlu jika Anda ingat selama instalasi kami juga menginstal ssh untuk memungkinkan kami mengakses server kami dari jarak jauh jika Anda memilih untuk tidak melakukan ini tetapi kemudian berubah pikiran jangan khawatir karena Anda dapat segera menambahkan fungsionalitas ini dengan perintah berikut sudo apt install open ssh dash server masukkan kata sandi Anda dan seperti yang Anda lihat

  

00:20:04 Saya sudah menginstal versi terbaru tetapi Anda dapat terus menginstal paket oke dengan server sekarang siap menerima koneksi jarak jauh Saya telah pindah ke PC windows untuk mencoba menghubungkan hal pertama yang pertama kita perlu memastikan bahwa klien ssh terbuka terinstal jadi buka pengaturan dan buka aplikasi dari sana klik fitur opsional yang Anda cari untuk melihat apakah klien ssh terbuka sudah ada dalam daftar terinstal Anda dapat melihat bahwa milik saya sudah ada tetapi jika bukan itu masalahnya, Anda dapat mengklik tambahkan a

  

00:20:37 fitur untuk menambahkannya saya akan menutupnya dan sekarang kita dapat membuka command prompt dengan mengetik cmd di kotak pencarian dan memilihnya untuk terhubung dari jarak jauh ke server kami, kami perlu mengetik ssh diikuti dengan nama pengguna akun server yang dalam kasus saya adalah dengan pi saya simbol at dan kemudian alamat ip server yang bagi saya adalah 192.168.0.200. lalu masukkan itu karena ini pertama kali menghubungkan kita perlu mengetikkan yes untuk menerima sidik jari server lalu tekan enter lalu masukkan kata sandi untuk

  

00:21:14 akun di server Anda semuanya baik-baik saja. Anda sekarang sudah berhasil terhubung dan Anda dapat menjalankan tugas server dari kenyamanan PC desktop atau laptop Anda jika Anda berencana menjalankan server tanpa kepala sekarang adalah saat yang tepat untuk memutuskan sambungan monitor dan keyboardnya untuk keluar dari sesi jarak jauh cukup ketikkan kata keluar dan kemudian Anda dapat menutup jendela setelah diinstal dan diperbarui seperti banyak sistem operasi server, server ubuntu sendiri sebenarnya tidak melakukan banyak hal di luar gerbang

  

00:21:47 namun fungsinya adalah memberi kami dasar yang baik untuk membangun. Jadi, bergantung pada apa yang Anda rencanakan selanjutnya, Anda mungkin sudah cukup melangkah dengan video ini, namun bagi mereka yang ingin menyingsingkan lengan baju dan mendalami sedikit lebih dalam saya akan membahas beberapa tugas server manual yang mungkin ingin Anda pertimbangkan sekarang saya tahu bahwa tidak semua orang menyukai terminal linux, mungkin karena latar belakang hitam yang suram atau rima teks yang dapat muncul di layar mungkin gui yang cantik hanya menawarkan kenyamanan yang lebih

  

00:22:16 lingkungan apa pun alasannya jika Anda ingin menambahkan desktop ke server Anda itulah yang akan kita lakukan di bagian video ini, ketahuilah bahwa server ubuntu dalam bentuk standarnya menggunakan sumber daya yang jauh lebih sedikit daripada memiliki a desktop dibaut di atas jadi jika Anda ingin melakukan ini, pertama-tama pikirkan tentang perangkat keras Anda dan apakah itu sesuai dengan pekerjaan yang dikatakan untuk mencoba dan menjaga beban sesedikit mungkin, kami akan memasang lingkungan desktop ringan yang dikenal sebagai lxde sehingga untuk memulai masukkan perintah berikut

  

00:22:45 sudo apt install lxde dash core lx penampilan lxde core akan memberi kita desktop minimal tetapi menambahkan tampilan lx akan memungkinkan kita mengubah tampilan dan nuansa desktop jika kita ingin melakukannya masukkan kata sandi Anda, Anda dapat melihat langsung berapa banyak perangkat lunak tambahan yang diperlukan untuk menjalankan gui bahkan yang ringan seperti lxde mari kita masukkan y untuk melanjutkan di sini kita perlu memilih manajer tampilan default karena ini memberitahu kita bahwa ini akan memberikan jendela login grafis karena kita mencoba untuk menyimpannya segala sesuatunya seringan mungkin

  

00:23:28 gunakan tombol kursor Anda untuk menyorot light dm lalu tekan enter untuk memilihnya setelah instalasi selesai mari kita restart server dan seperti itu Anda sekarang harus memiliki jendela login grafis sebelum login pastikan Anda mengklik ubuntu logo dan pilih lxde lalu masukkan kata sandi Anda untuk masuk ke desktop mungkin tidak terlihat banyak tetapi Anda sekarang memiliki bilah tugas dengan menu mulai yang memberi Anda akses mudah ke beberapa alat memang di bagian preferensi Anda akan menemukan tampilan dan nuansa yang disesuaikan

  

00:24:10 ini adalah paket tampilan lx yang kami instal jika Anda ingin menyesuaikan desktop Anda di sebelah menu mulai kami memiliki pengelola file dan kemudian di sisi kanan bawah serta jaringan volume dan waktu kami juga memiliki tombol daya sehingga Anda dapat dengan mudah me-restart server Anda saat ini untuk menggunakan desktop ini kita harus masuk ke server kami secara langsung tetapi bagaimana jika Anda lebih suka mengaksesnya dari jarak jauh melalui jaringan lokal Anda, untuk melakukan itu kami perlu melakukannya instal beberapa perangkat lunak, buka menu mulai

  

00:24:42 dan menuju ke alat sistem, kita perlu membuka terminal lx. Sangat berguna untuk meletakkan pintasan ini di desktop jadi mari kita klik kanan padanya dan pilih tambahkan ke desktop lalu klik dua kali pintasan tersebut untuk membuka emulator terminal perintah pertama yang perlu kita ketik adalah sudo apt install xrdp lalu masukkan kata sandi Anda dan ya, kami ingin melanjutkan dengan paket xrdp yang terinstal, kami perlu mengedit file konfigurasinya jadi saya akan menghapus layar dan mengetik sudo nano forward garis miring dll garis miring ke depan xrdp garis miring ke depan

  

00:25:26 mulai wm kita harus menuju ke akhir file sekarang Anda bisa menggunakan tombol kursor tetapi cara yang lebih cepat adalah dengan menahan tombol kontrol dan tekan akhir jika Anda menggunakan tombol panah untuk memindahkan kursor ke awal baris tes kita akan mengomentarinya dengan mengetikkan hash dan kemudian kita akan melakukan hal yang sama pada baris yang sama juga kembali ke akhir file dan tekan tombol enter untuk membuat baris baru lalu ketik lx session space dash s space lxde semua dengan huruf kapital space dash e space lxde sekali lagi dengan huruf kapital

  

00:26:09 lalu simpan dan keluar dari file dengan cara tahan tombol control dan tekan x ketik y dan tekan enter maka hal terakhir yang perlu kita lakukan adalah menambahkan pengguna xrdp ke grup ssl cert dan kita bisa melakukannya dengan mengetik sudo add user xrdp ssl dash menegaskan dan sekarang mari kita lakukan reboot untuk memastikan bahwa semua perubahan itu berlaku oke jadi saya kembali ke komputer windows saya dan saya akan membuka koneksi desktop jarak jauh lalu mengetikkan alamat ip dari server saya dan klik sambungkan lalu ya maka kita perlu memasukkan nama pengguna kita

  

00:26:55 dan kata sandi untuk server ubuntu dan terakhir klik ok dan itu saja, kita sekarang masuk ke desktop server ubuntu dari jarak jauh. Anda dapat mengetahui bahwa ini adalah sesi jarak jauh dari bilah di bagian atas layar dan kapan Anda ingin meninggalkan server, Anda dapat membuka menu mulai dan keluar atau sebagai alternatif jika Anda ingin membiarkan sesuatu berjalan di desktop, Anda dapat keluar dari sesi dengan sedikit tanda silang lalu kembali lagi nanti. akan kembali ke relung gelap jendela konsol

  

00:27:27 atau command prompt tetapi jika Anda telah menginstal desktop dan ingin terus mengikuti, cukup masukkan salah satu perintah ke terminal lx, pendekatan yang lebih ringan untuk mengelola server kami melalui antarmuka yang mudah digunakan adalah dengan menginstal konsol web dan alat yang hebat untuk pekerjaan itu adalah kokpit, setelah terinstal, kita akan dapat mengakses server ubuntu dari komputer mana pun di jaringan lokal menggunakan tidak lebih dari browser web, jadi mari kita mulai terlebih dahulu, pastikan bahwa manajer paket perangkat lunak diperbarui dengan menjalankan

  

00:28:00 sudo apt update dan masukkan kata sandi Anda untuk melanjutkan lalu ketik sudo apt install cockpit dan ya kami ingin melanjutkan setelah selesai menginstal mari kita periksa apakah itu berjalan dengan memasukkan sudo system ctl status cockpit dot socket seperti yang Anda lihat itu aktif dan mendengarkan ada satu hal lagi yang perlu kita lakukan sebelum menggunakan kokpit, server ubuntu telah mengubah manajer jaringannya dan tidak lagi berfungsi dengan konfigurasi default kokpit tetapi ini mudah diperbaiki jadi mari kita ketik sudo nano forward smash dll

  

00:28:51 garis miring ke depan netplan garis miring ganda pemasang dasbor nol dasbor config dot yaml lalu tekan enter untuk mengedit file yang Anda cari baris yang bertuliskan versi dua lalu tepat di bawahnya kita akan memasukkan yang baru baris tekan spasi untuk membuat indentasi ke posisi yang sama dengan baris di atas lalu ketik renderer titik dua spasi network manager atau satu kata dengan huruf kapital n dan huruf kapital m dan setelah selesai tahan tombol kontrol dan tekan x lalu tekan y dan enter untuk menyimpan

  

00:29:29 berubah dan keluar agar konfigurasi baru kita diterapkan, kita perlu memasukkan sudo netplum troy lalu tekan enter lagi untuk menerima konfigurasi baru dan setelah itu selesai kita dapat keluar dengan mengetik catatan keluar yang sekarang memberi kita alamat konsol web yang baru saja kita atur di komputer di jaringan yang sama dengan server kita akan membuka browser web lalu mengetikkan alamat konsol web yang merupakan alamat ip server ubuntu diikuti dengan titik dua dan nomor port 9090 karena kokpit menggunakan tanda tangan sendiri

  

00:30:09 sertifikat kita perlu mengklik lanjutan lalu melanjutkan dan di sini kita berada di layar login untuk antarmuka web baru server ubuntu kita, masukkan nama pengguna dan kata sandi yang sama dengan yang Anda gunakan untuk login langsung ke server yang akan digunakan. dapat melakukan tugas admin Anda ingin membiarkan kotak ini dicentang di mana dikatakan gunakan kembali kata sandi saya untuk tugas istimewa dan kemudian kita dapat mengklik login karena ini bukan video tentang kokpit secara khusus saya tidak akan membahas setiap pengaturan Sadarilah bahwa Anda dapat menjaga milik Anda

  

00:30:42 server diperbarui dari bagian pembaruan perangkat lunak dan Anda bahkan dapat masuk ke terminal server jika Anda ingin melakukannya, Anda dapat meninggalkan konsol web dengan mengklik nama akun Anda di kanan atas dan memilih logout berikutnya kembali di konsol server kita akan melihat penambahan akun pengguna tambahan dan untuk melakukan ini kita hanya perlu mengetik sudo add user diikuti dengan nama pengguna yang kita inginkan untuk akun baru. Saya akan menggunakan sedikit pi jika diminta masukkan kata sandi untuk akun server Anda saat ini, sekarang kami perlu melakukannya

  

00:31:19 masukkan kata sandi untuk akun pengguna baru lalu masukkan lagi untuk mengonfirmasinya. Di sini kita dapat memasukkan nama lengkap atau sebagai alternatif, Anda cukup menekan enter untuk menerima default saya tidak akan memasukkan nomor kamar jadi saya tekan enter saja yang itu dan sama lagi untuk telpon kantor dan telpon rumah dan juga yang lainnya ya informasinya benar dan itu saja akun baru dibuat dan jika kita masuk ke direktori home dengan mengetikkan cd forward garis miring home dan lalu daftar isinya, Anda dapat melihat akun baru kita juga

  

00:31:58 memiliki direktori home sendiri saat ini bits pi hanyalah akun pengguna standar sehingga tidak dapat melakukan tugas admin apa pun, ini mungkin yang Anda inginkan tetapi jika Anda memerlukan akun admin kedua kami dapat dengan mudah mencapai ini dengan menambahkannya ke grup sudo untuk melakukan ini, masukkan perintah sudo user mod dash huruf kecil a dash capital g sudo dan nama akun pengguna baru Anda yang dalam kasus saya adalah potongan kue lalu masukkan kata sandi untuk Anda akun asli jika diminta dan hanya itu sekarang memiliki admin

  

00:32:37 benar jadi mari kita uji. Saya akan keluar dengan mengetik exit lalu masuk ke akun baru mari kita bersihkan layar dan coba jalankan tugas admin jadi saya akan memasukkan sudo apt update lalu pop dalam potongan kata sandi pi dan seperti yang Anda lihat, perintah berhasil dijalankan dengan benar, mari kita keluar dari akun baru dan masuk kembali ke akun asli sekarang daripada keluar dan masuk kembali katakanlah Anda hanya ingin berpindah akun sementara atau Anda dapat melakukan ini menggunakan perintah su atau switch pengguna

  

00:33:23 jadi jika saya mengetik su dash dan nama akun yang ingin saya gunakan lalu masukkan kata sandi untuk akun itu dan Anda dapat mengetahui dari command prompt bahwa saya sekarang berada di bit akun pi dan saya dapat mengonfirmasinya dengan memasukkan perintah siapa saya ketika Anda siap untuk beralih kembali ke pengguna asli cukup ketik exit kegunaan lain untuk perintah su untuk sementara menjadi root ini bisa berguna jika Anda perlu memasukkan banyak admin memerintahkan satu demi satu karena Anda tidak perlu mengetik sudo

  

00:33:58 setiap kali untuk beralih ke akun root, ketik sudo su dash lalu masukkan kata sandi akun Anda dan sekarang kita dapat menjalankan perintah admin tanpa melanjutkannya dengan sudo misalnya sudo apt update menjadi apt update Anda harus sangat berhati-hati sambil berlari kasar seperti seseorang yang pernah dengan bijak berkata dengan kekuatan besar datanglah tanggung jawab yang besar jadi mari kita keluar dari sana sebelum kita melakukan kerusakan apa pun dan Anda dapat melihat bahwa saya sekarang dengan selamat kembali ke sepeda saya, akun pi saya jika Anda ingin daftar semua akun pengguna di server

  

00:34:35 Anda dapat melakukannya dengan memasukkan comp gen u untuk pengguna karena Anda dapat melihat server berisi banyak akun sistem tetapi mungkin yang lebih penting Anda harus dapat melihat akun yang telah Anda buat oke jadi apa yang harus kami lakukan jika kita ingin menghapus pengguna dengan baik disitulah perintah pengguna dell atau hapus pengguna masuk jadi masukkan sudo pengguna dell dan nama akun yang ingin Anda hapus lalu masukkan kata sandi Anda dan hanya itu akun tersebut tidak ada lagi kami dapat mengonfirmasi ini dengan memasukkan kembali perintah comp gen u dan akun yang baru saja Anda buat

  

00:35:14 dihapus seharusnya tidak lagi ada dalam daftar karena alasan keamanan secara default server ubuntu tidak mengizinkan Anda masuk menggunakan akun root meskipun ini adalah ide bagus mungkin ada saatnya Anda sedang menyiapkan server bahwa Anda memerlukan akun root untuk aktif sepenuhnya jadi jika Anda menghadapi skenario seperti itu Anda dapat mengetik sudo pa double swd root Anda perlu membuat kata sandi untuk akun root dan kemudian mengonfirmasinya dan sekarang jika kita logout kita dapat log out sebagai catatan root setiap kali Anda menjalankan sebagai root, prompt perintah berubah menjadi tanda pagar

  

00:35:56 alih-alih menggunakan dolar biasa, ayo keluar dari sana jika nanti Anda memutuskan bahwa Anda akan segera membatasi akses ke akun root, ketik saja sudo pa double swd dash l root lalu masukkan kata sandi Anda dan selamat Anda baru saja menonaktifkan login akun root sementara yang terbaik adalah mendapatkan nama sejak awal, dimungkinkan untuk mengganti nama server Anda, katakanlah saya muak dengan server generik dan ingin mengubahnya menjadi fort knox, kami dapat secara eksplisit menampilkan namanya server kami dengan mengetik

  

00:36:33 nama host untuk informasi lebih lanjut Anda dapat mengetikkan nama host ctl sekarang untuk mengubah nama, mari ketik sudo nama host ctl setel nama host dasbor lalu apa yang ingin Anda ubah ke yang akan saya gunakan untuk knox dan kemudian kita perlu untuk memasukkan kata sandi kami dan jika kami mengetikkan nama host sekarang Anda dapat melihat bahwa server memiliki pemberitahuan nama baru pada saat prompt belum diperbarui untuk mencerminkan perubahan ini mudah diatasi dengan mengetikkan exec bash jika Anda memutuskan untuk mengubahnya nama host server Anda, ada satu lagi

  

00:37:14 hal yang harus Anda perhatikan saat server melakukan booting, ia memetakan nama host lokal ke alamat ip. Ini disimpan dalam file host etsy dan kita dapat melihatnya dengan memasukkan cat ke depan, garis miring, dll, host garis miring, kita dapat melihat dengan jelas bahwa ini masih berisi nama lama server kita jadi untuk memperbaruinya mari kita edit file dengan mengetikkan sudo nano garis miring ke depan dll host garis miring menggunakan tombol kursor untuk menavigasi ke akhir nama server lama Anda dan tombol spasi mundur untuk menghapusnya dan lalu ketikkan nama baru untuk Anda

  

00:37:52 dengan pembaruan itu kita perlu menyimpan file dan kita bisa melakukannya di editor teks nano dengan menahan tombol kontrol dan menekan x ketik y lalu tekan enter hebat sehingga server kita sekarang diganti namanya untuk memeriksa yang mengetahui namanya Saya hanya akan menjalankan tes ping menggunakan nama host jadi saya akan mengetik ping untuk knox dan seperti yang Anda lihat, ia membalas, ada alat yang sangat berguna yang dapat kita tambahkan ke server ubuntu yang membuat instalasi menjadi populer paket sangat mudah dan itu disebut sel tugas jadi mari kita instal sekarang kita akan membuatnya terlebih dahulu

  

00:38:33 pastikan manajer paket server sudah yang terbaru dengan menjalankan sudo apt update dan kemudian kita akan menginstal perangkat lunak dengan mengetikkan perintah sudo apt install task cell dan ya kita ingin melanjutkan ketika sudah selesai instalasi kita bisa jalankan dengan sudo task cell dan Anda dapat melihat bahwa ada cukup banyak daftar hal yang dapat kami instal untuk keperluan video ini saya akan menginstal server lampu jadi saya akan menggunakan tombol kursor untuk berpindah ke bawah daftar dan kemudian tekan bilah spasi untuk memilih entri itu, lalu jika saya mengetuk tombol tab, saya dapat menekan

  

00:39:19 masuk untuk memilih ok dan ketika command prompt muncul kembali di bagian bawah layar, instalasi selesai, tumpukan lampu terdiri dari sekumpulan perangkat lunak sumber terbuka yang digunakan untuk menjalankan aplikasi web, lampu sebenarnya adalah akronim yang merupakan singkatan dari linux apache mysql dan php kami telah menangani bagian linux dengan menginstal server ubuntu saya akan kembali ke apache sebentar lagi mysql adalah database dan merupakan ide bagus untuk memastikan ini aman dengan menjalankan sudo mysql underscore secure underscore instalasi

  

00:40:04 pertama-tama sistem menanyakan apakah kami ingin sistem memeriksa bahwa kami menggunakan kata sandi yang aman saat menyiapkan database, itu ide yang bagus, jadi saya akan memasukkan ya untuk kata sandi itu, lalu Anda tetapkan kebijakan untuk menerapkannya, saya akan gunakan nomor dua untuk kata sandi yang kuat sekarang kita perlu membuat kata sandi untuk pengguna basis data root dan kemudian memasukkannya lagi untuk mengonfirmasi ya saya ingin melanjutkan dengan kata sandi yang diberikan untuk keamanan, sebaiknya hapus pengguna anonim kami juga ingin melarang login jarak jauh ke database apa pun oleh pengguna root

  

00:40:40 dan mari kita hapus juga database pengujian agar pengaturan tersebut dapat diterapkan, kita perlu memuat ulang tabel hak istimewa dan itulah komponen database yang siap untuk kembali ke Apache yang merupakan bagian server web dari tumpukan lampu yang telah saya lompati ke pc windows untuk mendemonstrasikan ini jika kita membuka browser web dan memasukkan alamat ip server ubuntu kita, Anda dapat melihat bahwa kita telah mencapai halaman default untuk server web apache, saya akan memindahkannya ke buka perintah prompt dan letakkan itu di sisi lain

  

00:41:16 layar dan kemudian ssh ke server alasan saya membuka jendela ini berdampingan adalah untuk melihat bagian akhir dari tumpukan lampu php adalah bahasa skrip yang banyak digunakan dalam pengembangan web untuk mengungkapkan beberapa informasi tentang ini pertama-tama kita perlu mengunjungi direktori web server apache dan kita bisa melakukannya dengan mengetikkan cd forwardslash var forwardslash www forwardslash html mari kita daftar isi direktori itu jika penasaran file index.html apache ini 2 halaman default ubuntu itu

  

00:41:57 kita melihat kita akan membuat file baru di direktori ini kita akan menggunakan editor teks nano dengan mengetik sudo nano dan kemudian nama file baru yang akan menjadi info php dot php jika itu memintanya muncul di kata sandi Anda karena file baru tidak ada apa pun di dalamnya saat ini jadi mari kita masukkan kurang dari tanda tanya php tekan enter untuk memulai baris baru dan kemudian kita akan mengetikkan dua garis miring yang berarti baris ini akan menjadi a komentar menjelaskan tujuan file ini sebagai berikut lalu pada baris berikutnya ketik php

  

00:42:36 info kurung buka kurung tutup titik koma lalu selesaikan dengan tanda tanya lebih besar daripada tahan tombol kontrol dan ketuk x ketik y dan tekan enter untuk menyimpan dan keluar untuk melihat apa yang telah dilakukan, buka browser web Anda dan ikuti ip alamat server ubuntu Anda masukkan garis miring ke depan info php dot php ini memberi kami banyak sekali informasi tentang instalasi php kami dan untuk alasan ini meskipun tidak penting di jaringan rumah jika ini adalah server web yang terhubung ke internet, Anda tidak akan mau mengungkapkan hal ini kepada

  

00:43:17 berhati-hatilah, mari kita hapus itu dan kita dapat melakukannya dengan mengetik sudo rm php info dot php dan sekarang jika saya menyegarkan halaman web, Anda dapat melihat bahwa informasi tersebut telah digunakan untuk memanfaatkan lampu Anda dengan benar tumpukan Anda memerlukan beberapa perangkat lunak tambahan, apa sebenarnya itu sepenuhnya terserah Anda, tetapi setidaknya Anda sekarang memiliki semua dasar jika Anda telah menonton video ini dari awal, Anda mungkin ingat bahwa server saya memiliki server fisik kedua. drive dan yang saya sebutkan saya akan menggunakan ini untuk penyimpanan data

  

00:43:51 dengan cara ini sistem operasi dapat terus menggunakan drive utama dan kami dapat menyimpan semua file kami di disk terpisah untuk membuat proses ini sedikit lebih mudah jika Anda belum melakukannya, saya sarankan menghubungkan dari jarak jauh ke Anda server menggunakan ssh karena dengan cara ini kita akan dapat dengan mudah menyalin dan menempelkan salah satu entri yang lebih panjang. Jika kita membersihkan layar, hal pertama yang ingin kita lakukan adalah membuat daftar drive yang terhubung ke server dan kita dapat melakukannya dengan memasukkan lsblk di mesin saya, saya mencari gigabyte SSD yang ini di sini sda

  

00:44:25 kita dapat melihat bahwa saat ini berisi dua partisi sda1 dan sda2 tetapi saya ingin memulai dari awal dengan menghapus tanda tangan tabel partisi saat ini dan kita dapat melakukannya dengan mengetik sudo wipe fs dash a yang merupakan singkatan dari all dan kemudian path ke drive yang dalam kasus saya adalah forwardslash dev forwardslashsda penting bagi Anda untuk mendapatkan bagian terakhir ini dengan benar karena Anda tidak ingin melakukan ini pada drive yang salah lalu masukkan kata sandi Anda untuk melanjutkan oke sekarang kita akan buat tata letak drive baru karena ini akan digunakan

  

00:45:02 menyimpan data kemungkinan besar Anda menggunakan drive besar jadi oleh karena itu saya sarankan Anda menggunakan perintah g disk untuk mempartisinya karena ini akan membuat tabel partisi gpt yang lebih cocok untuk drive yang lebih besar dan kita bisa melakukannya dengan mengetikkan sudo gdisk lalu path ke disk anda yang dalam kasus saya adalah forwardslash dev forwardslash sda lagi pastikan anda mendapatkan disk yang tepat agar tidak menimbulkan masalah besar kan kita akan mengetikkan huruf n dan tekan enter untuk membuat partisi baru kita akan memberikannya partisi nomor satu

  

00:45:38 kami ingin ini dimulai di awal drive, jadi tekan enter untuk menerima default dan untuk mempermudah, saya hanya akan membuat satu partisi yang memenuhi seluruh drive, jadi tekan enter lagi untuk melakukan ini dan kita dapat menekan enter lagi untuk menerima nilai default untuk kode hex atau panduan. Selesai, kita perlu menulis perubahan kita ke disk dan kita dapat melakukannya dengan memasukkan huruf w lalu mengetik y untuk melanjutkan, mari kita lihat partisi baru kita dengan memasukkan sudo g disk dash l dan kemudian jalur ke disk

  

00:46:13 dan di sini Anda dapat melihat partisi tunggal saya sekarang karena kita memiliki partisi, kita perlu membuat sistem file di dalamnya di windows Anda mungkin pernah mendengar tentang FAT32 dan ntfs tetapi karena ini Linux, saya sarankan kami menggunakan ext4 jadi mari kita ketik perintah sudo mkfs atau make file system dot ext4 dan kemudian partisi yang ingin kita buat yang dalam kasus saya adalah dev sda1 Anda dapat melihat bahwa ini hanyalah drive yang diikuti dengan nomor partisi jika Anda pernah selanjutnya kita hanya membuat satu partisi jadi jumlahnya harus satu ayo tekan

  

00:46:51 masuk untuk menjalankan perintah jika Anda mendapat pesan bahwa partisi saat ini berisi sistem file yang berbeda cukup masukkan y untuk menimpanya oke dengan pengaturan drive kedua kita sekarang perlu memasangnya tidak seperti windows linux tidak menggunakan huruf drive sebaliknya sistem operasi terletak di direktori root ketika kita menambahkan drive tambahan agar dapat diakses, kita perlu memasangnya di dalam direktori root ini dengan mudah ada folder mnt atau mount hanya untuk tujuan ini jadi mari kita navigasikan dulu ke sana dengan

  

00:47:25 mengetik cd atau mengubah direktori maju garis miring mnt selanjutnya mari kita buat titik mount ini hanyalah sebuah folder yang akan memasang disk kita dan kita dapat menggunakan perintah mkdir atau membuat direktori untuk melakukan ini, ketik sudo mkdir lalu nama yang ingin Anda berikan, saya hanya akan menggunakan drive jika diminta kata sandi Anda cukup masukkan dan jika kita menjalankan perintah ls kita akan melihat folder baru kita, saya akan menggunakan perintah cd untuk masuk ke dalamnya sekarang jika saya membuat file di dalamnya yang sebenarnya disimpan di file utama saya

  

00:48:06 drive sistem operasi itu karena meskipun kami telah membuat titik pemasangan, kami belum benar-benar memasang drive kedua ke sana jika saya menghapus file itu dan kembali ke direktori mnt dengan cara mengetik cd space two dots mengambil Anda naik satu level dari folder tempat Anda berada. Ini dikenal sebagai direktori induk. Kami akan membuat titik mount kami tidak dapat diubah. Ini berarti kami tidak dapat lagi meletakkan file apa pun di dalamnya. Ini adalah hal yang baik karena jika karena alasan tertentu drive penyimpanan kita tidak dapat dipasang

  

00:48:37 kami tidak ingin semua file berakhir di disk yang berisi sistem operasi, jadi masukkan sudo ch attr atau ubah atribut plus i lalu nama folder titik pemasangan Anda untuk memastikan itu berfungsi. masukkan folder itu lagi dan coba buat file pengujian lain dan seperti yang Anda lihat, file tersebut tidak mengizinkan kami dan tidak ada file pengujian di direktori jadi sekarang titik mount siap digunakan, saya akan kembali ke direktori mount ketika kami pasang drive kita bisa menggunakan jalur dev dan nomor partisinya

  

00:49:15 dalam kasus saya itu adalah forwardslash dev forwardslashsda1 masalah dengan metode ini adalah jika suatu saat Anda membongkar server dan memindahkan disk, tidak ada jaminan ketika Anda memasangnya kembali, drive akan dapatkan label yang sama sehingga cara yang lebih dapat diandalkan adalah dengan menggunakan apa yang dikenal sebagai uuid atau pengidentifikasi unik universal untuk menemukan ini untuk drive kita, kita dapat menggunakan perintah sudo blk id mengetahui bahwa partisi saya adalah sda1 saya dapat melihat uuidnya di sini kita' kembali akan menyalin uuid oleh

  

00:49:49 menggerakkan penunjuk mouse ke posisinya sambil menahan tombol kiri lalu menyeret hingga semuanya terseleksi dari u pertama hingga kutipan terakhir lalu lepaskan tombol, tahan tombol ctrl pada keyboard Anda dan tekan c dengan itu disalin kita akan mengedit file jadi ketik sudo nano garis miring dll garis miring fs tab kita bisa memasang drive secara manual tetapi kemudian kita harus melakukannya setiap kali kita me-restart server dengan menambahkan entri ke file tab fs itu akan dipasang secara otomatis setiap kali

  

00:50:26 boot server jadi gunakan tombol kursor untuk menuju ke bawah lalu gerakkan penunjuk tetikus Anda ke dalam jendela terminal dan klik kanan untuk menempelkan untuk melengkapi baris yang perlu kita ketikkan spasi ke depan, garis miring mnt, garis miring ke depan, dan nama Anda mount point yang milik saya adalah drive2 space ext4 space default space 0 space 2 jadi itu akan membawa drive tambahan kita mount ke titik mount yang kita buat menggunakan sistem file ext4 dan pengaturan mount default dua bidang terakhir singkatan dari dump an fsck atau pemeriksa sistem file masing-masing kita

  

00:51:07 tidak perlu masuk ke nilainya selain mengatakan bahwa pada drive sistem nun tambahan ini harus disetel ke nol dan dua kan, tahan tombol kontrol dan tekan x lalu ketik y dan tekan enter untuk simpan dan keluar, sebaiknya periksa apakah entri baru berfungsi seperti yang diiklankan karena kesalahan pada file tab fs dapat mencegah server Anda mulai memastikan semuanya baik-baik saja, ketik sudo mount dash dan tidak ada kesalahan selalu merupakan pertanda baik menjalankannya perintah terakhir baru saja memasang drive apa pun yang terdaftar di fstab

  

00:51:40 jika belum ada mulai sekarang, ini akan terjadi secara ajaib secara otomatis setiap kali Anda memulai server mengetik df h dan kemudian nama titik pemasangan menunjukkan kepada kita bahwa drive kedua memang telah dipasang juga jika kita sekarang masukkan drive yang terpasang dan saya mencoba dan membuat file pengujian kita dapat melihat bahwa itu berhasil ingat kita tidak dapat lagi membuat file di dalam titik mount itu sendiri tetapi sekarang kita sedang menulis ke disk kedua semuanya baik-baik saja ketika harus menambahkan drive ada satu area lagi yang ingin saya gambar

  

00:52:15 perhatian dan itu izin jika kita menambahkan tanda hubung l ke perintah daftar, kita dapat melihat lebih banyak informasi saat ini direktori ini dan semua yang ada di dalamnya dimiliki oleh root dan itulah salah satu alasan kita harus menyimpannya menggunakan perintah sudo ke depan ini mungkin bukan yang Anda inginkan jadi mari kita ubah sekarang saya akan pindah ke direktori mnt dan kemudian mengeluarkan perintah untuk menjadikan pengguna saya saat ini sebagai pemilik direktori drive2 yaitu sebagai berikut sudo ch memiliki atau mengubah modal tanda hubung pemilik r

  

00:52:50 diikuti dengan nama pengguna yang ingin kita ambil kepemilikannya lalu nama direktori diikuti dengan garis miring pop di kata sandi Anda jika diminta dan jika kita masuk ke folder itu lagi dan sekali lagi daftar konten Anda dapat melihat bahwa saya akun oleh pi saya sekarang memiliki file dalam direktori ini catatan ini karena kami menggunakan opsi dash capital r pada perintah ch sendiri tanpanya meskipun kami masih mengambil kepemilikan direktori ini tidak akan diterapkan pada file yang ada di dalamnya juga ketika menyangkut izin file

  

00:53:24 kita perlu memutuskan jenis akses apa yang dimiliki pengguna. Anda pasti memperhatikan huruf dan tanda hubung di awal setiap entri. Ini secara visual mengidentifikasi izin file dan diatur sebagai grup pemilik dan lainnya jika kita mengikuti tes file yang saya buat sebelumnya sebagai contoh saat ini memiliki izin rw atau baca tulis yang diberikan kepada pemilik dan izin r atau baca yang diberikan kepada grup dan orang lain sementara kita dapat mengubah izin pada file ini satu per satu, seringkali lebih berguna untuk melakukannya di

  

00:53:53 seluruh direktori jadi mari kita kembali lagi ke direktori mnt dan kali ini kita akan menggunakan perintah chmod untuk mengubah izin jadi ketik sudo chmod kita akan menggunakan tanda hubung kapital r lagi untuk membuatnya rekursif dan i' Saya akan menggunakan tujuh lima nol. Angka-angka ini masing-masing mewakili grup pemilik dan yang lainnya. Inilah yang dikenal sebagai notasi oktal dan lebih cepat untuk menulis daripada menggunakan huruf rwx seperti yang Anda lihat dari tabel di layar, setiap angka mewakili beberapa izin pada dasarnya Anda hanya perlu mengingat satu

  

00:54:29 dua dan empat sebagai nol karena tidak ada izin masuk akal dan tiga lima enam dan tujuh dihasilkan oleh kombinasi satu dua dan empat misalnya baca yang empat ditambah kanan yang dua dan jalankan yang satu tambah hingga tujuh jadi dalam perintah saat ini angka tujuh akan memberikan izin baca tulis dan eksekusi dengan kata lain kontrol penuh kepada pemilik nomor lima akan memberikan izin baca dan eksekusi kepada grup dan angka nol tidak memberikan izin kepada orang lain yaitu semua orang kalau tidak

  

00:55:00 ini adalah konfigurasi yang cukup aman bagi pengguna default sehingga untuk menyelesaikannya kita hanya perlu memasukkan nama direktori tempat kita menerapkannya yang dalam kasus saya adalah drive2 dan saya akan membuat garis miring ke depan pada end dan jika kita kembali ke direktori dan mencantumkan isinya, perhatikan bahwa pemilik saat ini menggigit pai saya telah membaca, menulis, dan menjalankan izin pada semua entri, grup saat ini root telah membaca dan menjalankan izin dan yang lain tidak memiliki izin, jadi tanpa menggunakan sudo saya sekarang seharusnya bisa melakukan perubahan

  

00:55:34 di dalam folder ini pertama saya akan mencoba dan menghapus file tes dan itu hilang dan sekarang saya akan mencoba dan membuat file baru bernama banyak pi dan itu dia di bagian terakhir kami menambahkan sebuah drive tambahan untuk penyimpanan tidak apa-apa tetapi untuk membuatnya benar-benar berguna dan untuk membenarkan memasukkannya ke dalam server, ini benar-benar ingin tersedia melalui jaringan ada beberapa cara yang bisa kita lakukan untuk mencapai nfs sftp ini dan lain-lain. tapi saya sarankan untuk kompatibilitas terbaik dengan yang terluas

  

00:56:13 berbagai perangkat kita menggunakan samba terlebih dahulu mari kita periksa apakah manajer paket sudah yang terbaru dan sekarang mari kita instal samba ya kita ingin melakukan itu dengan perangkat lunak yang terinstal kita sekarang perlu mengkonfigurasinya mari kita mulai dengan menyiapkan a akun pengguna untuk melakukan ini gunakan akun yang ada di server dan tambahkan ke samba dengan mengetikkan sudo smb pa double swd dash a dan kemudian nama pengguna akun yang ada jadi saya akan menggunakan beli pai saya sekarang kita perlu membuat samba kata sandi untuk pengguna ini agar segala sesuatunya tetap lancar, saya akan melakukannya

  

00:56:57 sarankan menggunakan kata sandi yang sama yang biasa Anda gunakan untuk akun ini jadi saya akan menggigit kata sandi pai saya dan kemudian mengonfirmasinya dengan pengaturan akun. Mari masuk ke direktori etsy samba dan kita akan pergi ke edit file konfigurasi seseorang tetapi pertama-tama mari kita buat cadangan dari yang asli dan kemudian kita dapat mengedit file dengan mengetik sudo tahan tombol kontrol dan tekan end untuk melompat ke akhir file dan saya akan tekan enter untuk pindah menambahkan satu baris komentar adalah opsional tetapi merupakan praktik yang baik

  

00:57:39 jelaskan apa yang akan dilakukan kode apa pun yang Anda tambahkan, jadi jika kita memasukkan hash lalu mengetikkan deskripsi singkat, saya akan menyebutnya drive bersama saya di baris berikutnya kita akan memberikan bagiannya a nama ini perlu diketik di dalam tanda kurung siku saya akan menggunakan bagian yang biasanya imajinatif di bawahnya kita perlu memasukkan spasi jalur sama dengan spasi dan kemudian jalur ke direktori yang akan Anda bagikan di server yang menurut saya kasusnya adalah garis miring mnt ke depan garis miring drive untuk mengetik ke bawah pada pengguna ruang yang valid

  

00:58:16 spasi sama spasi lalu nama pengguna akun samba anda yang bagi saya adalah bite my pie lalu pada baris terakhir masukkan read space only space sama spasi dan jika ingin bisa menulis ke drive ketik no oke tahan tombol kontrol dan tekan x ketik y dan tekan enter dengan konfigurasi disimpan kita perlu me-restart layanan samba agar dapat diterapkan jadi mari kita masukkan perintah sudo system ctl restart smbd dot service akhirnya mari kita periksa konfigurasi samba kita untuk kesalahan Anda dapat melihat bahwa layanannya

  

00:58:59 file dimuat oke jadi mari kita tekan enter untuk menampilkan definisi layanan dan ada share samba yang kita buat di bagian bawah melompat ke mesin windows saatnya mencobanya saya akan membuka file explorer dan mengetikkan alamatnya bar backslash backslash alamat ip server ubuntu backslash dan kemudian nama yang Anda berikan untuk share Anda jika Anda ingat saya cukup memanggilmineshare ketika Anda mengetik milik Anda, tekan tombol enter dan itu akan meminta kredensial untuk terhubung ke Anda server jadi ketikkan nama pengguna dan kata sandi

  

00:59:36 dari akun yang Anda tambahkan ke samba jika Anda akan sering menggunakan ini, saya sarankan mencentang kotak ingat kredensial saya lalu klik ok untuk menghubungkan dan hanya itu, kami sekarang memiliki akses ke drive bersama kami Anda dapat melihat banyak file pi yang saya buat sebelumnya untuk menyelamatkan kita dari keharusan mengetikkan alamat setiap kali kita ingin terhubung ke share kita jika kita mengklik ikon folder kecil dan menyeretnya ke akses cepat lalu lepaskan kita sekarang memiliki pintasan praktis yang akan membawa kita langsung ke jaringan berbagi kita

  

01:00:07 dan sebagai tes terakhir mari kita coba menghapus banyak pi dan membuat folder baru untuk meletakkan sesuatu di server ubuntu dikirimkan dengan firewall bawaan tetapi secara default dimatikan kita dapat melihatnya dengan menjalankan perintah sudo ufw status sebentar lagi kami akan mengaktifkan firewall namun Anda harus berhati-hati jika Anda login dari jarak jauh karena Anda dapat mengunci diri secara tidak sengaja. Hal ini karena secara default firewall hanya mengizinkan lalu lintas keluar dan akan memblokir apa pun yang mencoba masuk jadi jika Anda ingin menggunakannya, Anda perlu melakukannya

  

01:00:49 pastikan bahwa akses ssh diizinkan dan untuk melakukan ini kita akan menambahkan aturan firewall dengan memasukkan sudo ufw izinkan ssh setelah itu selesai mari kita nyalakan firewall dengan mengetik sudo ufw aktifkan dan jika saya melompat ke perintah prompt dari mesin windows dan mencoba untuk terhubung menggunakan ssh Anda dapat melihat bahwa meskipun firewall sekarang diaktifkan kita masih dapat terhubung dari jarak jauh kembali ke server katakanlah Anda kemudian memutuskan Anda tidak ingin akses ssh jarak jauh setelah semua Anda dapat memblokirnya dengan memasukkan Sudo ufw reject ssh sekarang jika saya mencoba dan terhubung dari jarak jauh

  

01:01:35 dari mesin windows Anda dapat melihat bahwa setelah beberapa saat koneksi terputus dengan operasional firewall Anda harus berhenti dan memikirkan semua koneksi Anda ke server bahkan di jaringan lokal Anda misalnya jika Anda mengatur berbagi jaringan menggunakan samba Anda juga ingin mengizinkan akses yang dapat Anda lihat saat ini diblokir jadi kembali ke server kita perlu memasukkan sudo ufw izinkan samba dan jika saya coba lagi di komputer windows kita sekarang diizinkan masuk kembali jika Anda memutuskan untuk mengonfigurasi aturan firewall

  

01:02:18 bukan untuk Anda dan Anda lebih suka mematikan firewall kembali. Anda dapat melakukannya dengan mengetik sudo ufw menonaktifkan inti dari server adalah untuk melayani layanan melalui jaringan sehingga bisa sangat berguna untuk mendapatkannya untuk mengetahui perintah netstat karena ini menampilkan informasi tentang koneksi jaringan untuk mendapatkan hasil maksimal kita perlu menjalankannya sebagai admin dengan menggunakan sudo dan untuk mendapatkan lebih banyak manfaat darinya kita dapat menambahkan beberapa opsi baris perintah. Serangkaian opsi yang populer adalah tu lpn karena masing-masingnya akan menunjukkan kepada kita kumpulan data yang berbeda seperti yang ditunjukkan di layar

  

01:02:55 sebelum kita dapat menjalankan perintah ini, kita harus menginstalnya terlebih dahulu, jadi ketik sudo apt install net dash tools untuk melakukannya dan sekarang mari kita jalankan perintah netstat, setiap baris mewakili koneksi jaringan yang berbeda di sebelah kiri adalah jenisnya protokol jaringan baik tcp atau udp kami memiliki alamat lokal dan yang lebih penting nomor port apakah koneksi mendengarkan dengan kata lain layanan yang sedang berjalan menunggu untuk dihubungi dan nama program atau proses yang membuat layanan tersebut

  

01:03:36 untuk mencoba dan lebih memahami apa yang terjadi di sini mari kita ambil baris ini sebagai contoh. Kita dapat melihat ini menunjukkan kepada kita layanan smbd atau samba yang menggunakan protokol tcp dan beroperasi pada port 445, juga dalam format keadaan mendengarkan dan siap untuk dihubungkan dengan menggunakan perintah netstat kita dapat melihat sekilas layanan apa yang disediakan server untuk jaringan meskipun itu adalah tur yang cukup mudah-mudahan keluaran dari perintah netstat tidak lagi tampak seperti daftar

  

01:04:07 teks tidak berarti Area penting lainnya saat memantau server adalah sumber daya ada beberapa perintah populer yang dapat kita gunakan di sini secara historis, yang teratas ini menunjukkan kepada kita proses yang berjalan di server, berguna untuk dapat melihat apa yang digunakan meningkatkan sumber daya server terutama dalam situasi di mana Anda mungkin tidak memiliki proses perangkat keras yang sangat kuat dengan menggunakan sebagian besar sumber daya yang tercantum di atas, mari tekan q untuk keluar dari sana, alternatif yang lebih berguna dan lebih baru adalah h-top meskipun hal ini telah terjadi

  

01:04:40 sekitar sejak tahun 2004 Anda dapat menganggap h-top seperti steroid, mungkin yang paling berguna, ia juga interaktif sehingga dapat memantau sumber daya sistem dengan menggunakan perintah yang tercantum di bagian bawah layar. dapat menganalisis informasi lebih dekat katakanlah saya ingin mencari proses yang terhubung dengan samba jika saya menekan tombol f3 dan memasukkan seseorang itu akan menyorot proses yang sedang berjalan yang memenuhi kriteria ini menekan f3 lagi akan menemukan proses selanjutnya berjalan seseorang dan kita dapat siklus melalui mereka menggunakan

  

01:05:16 kunci f3 melihat lebih dekat pada proses tertentu Anda dapat melihat bahwa itu menunjukkan pid atau pengidentifikasi proses ini adalah nomor yang ditetapkan padanya kita juga dapat melihat pengguna bahwa proses sedang berjalan seperti dalam kasus ini root cpu dan kolom memori sangat penting karena kolom ini menunjukkan persentase masing-masing prosesor dan ram server yang sedang digunakan proses dan kolom perintah menampilkan lokasi perintah yang menjalankan proses di sini adalah garis miring pengguna garis miring spin smbd

  

01:05:48 kita dapat menekan tombol escape untuk membatalkan pencarian opsi lain yang berguna adalah f9 kill jika suatu proses menjadi kacau dan menghabiskan terlalu banyak sumber daya berharga server Anda, Anda dapat menutupnya secara paksa, katakanlah h top sendiri menjadi tidak terkendali karena berada di urutan teratas daftar saat ini menggunakan sumber daya paling banyak tetapi itu hanya karena saat ini saya tidak meminta server untuk melakukan hal lain, tetap saja anggap saja prosesnya tidak berjalan dengan baik dan kita harus mematikannya dengan proses yang disoroti perlu kita lakukan

  

01:06:20 tekan tombol f9 ini menampilkan perintah kirim sinyal secara default akan menggunakan istilah sig ini adalah cara sopan untuk meminta proses ditutup tetapi jika prosesnya sangat keras kepala Anda dapat memilih sesuatu yang lebih drastis seperti sig kill jadi mari kita tekan enter untuk mematikan h-top dengan sopan dan Anda dapat melihat bahwa kita sekarang memiliki command prompt kembali di bagian bawah layar tentu saja jika kita menjalankan h-top lagi cara yang lebih baik untuk keluar dari program adalah dengan menggunakan f10 kunci beberapa tip sebelum kita menyelesaikan video ini jika Anda mengetik perintah

  

01:06:56 khususnya saat Anda menavigasi direktori, Anda dapat membuat hidup Anda lebih mudah dengan menggunakan sesuatu yang disebut penyelesaian tab sebagai contoh, katakanlah saya ingin membuka direktori root server web Apache jika saya mulai mengetik cd garis miring var garis miring tapi kemudian alih-alih mengetikkan nama direktori lengkap www saya mengetik w lalu tekan tombol tab perhatikan bagaimana secara otomatis mengisi sisa nama folder dan kemudian jika saya melakukan hal yang sama lagi kali ini alih-alih mengetik html saya cukup mengetik h dan tekan tombol tab sekali lagi

  

01:07:32 otomatis menyelesaikan entri jelas ini dapat menghemat banyak pengetikan terutama jika melibatkan jalur yang lebih panjang. Hal terakhir yang ingin saya sebutkan adalah perintah man atau manual jika Anda mengalami kebuntuan dan tidak yakin apa sebuah perintah dilakukan di terminal Anda dapat melihat manualnya semoga sekarang Anda tahu tujuan dari perintah sudo tetapi jika Anda tidak yakin Anda bisa mengetik man sudo dan ini memberi Anda banyak informasi tentang perintah tertentu termasuk perintah apa pun opsi yang tersedia setelah Anda selesai mencarinya

  

01:08:04 Anda dapat menekan q untuk keluar dari sana dan itu saja. Sekarang saya akan mematikan server saya, tetapi Anda mungkin ingin membiarkan server Anda tetap berjalan dan itu membawa kita ke akhir video yang satu ini. menjadi sedikit lebih teknis dari biasanya semoga tidak terlalu banyak dengkuran yang terjadi di barisan belakang menjalankan server bukan untuk semua orang tetapi bagi mereka yang ingin melihat lebih dekat mur dan baut sistem dan mendapatkan keuntungan pemahaman yang lebih baik tentang apa yang terjadi di balik layar menyiapkan server secara manual adalah hal yang bagus

  

01:08:37 pengalaman belajar dan dengan pembaruan selama lima tahun untuk versi lts, server ubuntu adalah tempat yang bagus untuk memulai, ada banyak sekali server di luar sana, mungkin sekarang akan ada satu lagi saat Anda mulai mengelola server Anda sendiri seperti biasa jika Anda menikmati video ini, silakan suka dan berlangganan dan jika Anda ingin diberi tahu saat saya memposting video berikutnya, cukup klik ikon lonceng, terima kasih telah menonton dan sampai jumpa lagi.
