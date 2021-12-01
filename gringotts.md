---
layout: page
title: I Made a Homeserver
nav-menu: true
image: assets/images/googlephotos.jpg
show_tile: true
---

<!-- Main -->
<div id="main" class="alt">

<!-- One -->
<section id="one">
	<div class="inner">
		<header class="major">
			<h1>A Summary of My Experience Building a Homeserver</h1>
		</header>

<!-- Content -->
<h2 id="content">Whammy From Alphabet</h2>
<p><span class="image right"><img src="{% link assets/images/googlephotos.jpg %}" alt="" /></span>On June 1st of this year, Google announced an end to their "free, unlimited" cloud storage solution for anyone with access to their service. Instead, uploading media to their servers would now count towards a 15 GB quota that would need to carefully be managed by the user as the space would be shared between Google Drive, Google Photos, and Gmail. Fast forward to November and I begin to receive a barrage of complaints from my parents regarding space running out on their Google accounts; the free 15 GB had filled up surprisingly quick.
</p>

<p>
Initially, I resolved to the low effort problem solving strategy at first and helped them sort out what needed to be kept and what needed to be trashed by sitting down with them one evening. But eventually this cycle began to repeat itself on a week-by-week basis until I realized I needed to come up with an alternative solution; otherwise, I would be driven mad. 
</p>

<p>
Compounded with the growing... <i>*ahem*</i>... torrented media in my possession and my dad's specific need of making the data on his hard drive to be accessible from anywhere, I decided it was time to brainstorm a creative solution to handle it all together.
</p>

<hr class="major" />

<h2>Why a Homeserver</h2>
<p><span class="image left"><img src="{% link assets/images/server.jpg %}" alt="" /></span>In the beginning brainstorm stage, I recognized two options: Find a solution for archiving my family's data locally or convince my parents to purchase cloud storage. The latter was especially attractive at first considering how cheap plans like <a href="https://one.google.com/about/plans">Google One</a> are. At the time of writing this, a 2 TB space is only $13.99 CAD a month. For the general population, this buy and forget solution is the de-facto solution for a safe space to store sensitive data and media. And it comes with other benefits such as being accessible from anywhere and the integration with the Google ecosystem which is invaluable to many.</p>
<p>
But my needs for a storage solution were different; I wanted fast transfer speeds, flexibility, and storage larger than 2 TB for all the torrented media in my possession. And past a certain point, cloud storage becomes increasingly expensive compared to running a server of your own with similar capacity. For instance, a 12 TB server ran at home with the spare hardware I had laying around would cost me about $25 dollars worth of electricity where I live. I'm only counting electricity as an expense here because unlimited internet is something my parents would pay for regardless. On the flip side, a similar 12 TB solution hosted through a cloud storage solution such as Google One would run me a monthly bill of $84. No thanks, I must save for my tuition!
</p>
<p>
And so, I decided; I was going to transform an old office Dell that my family owned and turn it into a modest, but performant home server for our needs.
</p>

<hr class="major" />


<h2>A Look at the Hardware</h2>
<span class="image fit"><img src="{% link assets/images/dell.jpg %}" alt="" /></span>
<p>In terms of hardware, literally everything in the case is stock and came as is from the factory. The only upgrades that have been made are adding more storage and a larger stick of RAM. Here are the specs:</p>

<dl>
	<dt>Pentium G630</dt>
	<dd>
		<p>A basic dual-core CPU, nothing special here. I’m on the active lookout for finding a more performant i-series processor that would allow me to transcode footage on Plex without jumping to 100% usage every time. Otherwise, it does everything else quite well. </p>
	</dd>
	<dt>12 GB DDR3 Memory</dt>
	<dd>
		<p>Nothing to say here except that I think it may be overkill. I’m not complaining however as having more doesn’t come with any sacrifice other than a few extra watts of power consumption.</p>
	</dd>
	<dt>3 x 4 TB 3.5” internal hard drives from Western Digital</dt>
	<dd>
		<p>Two of the three drives are basic Blue series drives utilizing CMR (conventional magnetic recording) which will be utilized in a RAID 1 array. The third drive is a Red series drive that I picked up for cheap this Black Friday but unfortunately it runs using SMR (shingled magnetic recording) instead. From my understanding, this technology isn’t the ideal in a RAID setup due to poor performance. Instead, I’ve opted to use it as storage for all my non-sensitive media on Plex.</p>
	</dd>
	<dt>Stock Motherboard and Cooling</dt>
	<dd>
		<p>I haven’t delved much into what parts these are but I’m assuming it’s Dell hardware. The board itself is Micro ATX so perhaps down the line I can migrate all the components into a case that is sleeker with better airflow.</p>
	</dd>
</dl>

<p>
All in all, it’s a mediocre computer. But the hardware is rarely the fun part in an old re-purposed desktop computer, even if they’re new. Instead, let’s switch focus to the software that I’m running and what I use it for. 
</p>

<hr class="major" />

<h2>Setting Up Ubuntu and RAID</h2>

<p><span class="image left"><img src="{% link assets/images/ubuntu.jpg %}" alt="" /></span>The OS of choice is the popular Ubuntu Linux distribution. As I am using the PC as a server, I’ve also chosen to opt for the server edition and not the desktop one as a keyboard, mouse, and monitor will not be connected. All the operations I will do aside from the OS setup installation will be performed through command line on my laptop through SSH (secure shell). Doing this will allow me to minimize system stress as an external monitor and peripherals won’t be driven by the computer.
</p>
<p>The installation was seamless: <a href="https://ubuntu.com/download/server">download an image</a>, burn it onto a USB with Balena Etcher, and boot off the USB with the help of the BIOS. Follow the straightforward prompts to customize the installation to your liking and you’ll be running the core of your system in no time.
</p>
<p>During my own installation, I opted to setup a RAID configuration directly out of the gate during installation. RAID, an acronym for Redundant Array of Independent Disks, is a technology to merge physical drives into combined units. Doing so allows you to improve performance, create redundancy, or do both.
</p>
<p>Following this brilliant guide from <a href="https://gist.io/@fevangelou/2f7aa0d9b5cb42d783302727665bf80a">fevangelou</a>, I was able to setup RAID 1 (mirroring) on two of my WD Blue drives which would ensure I had data redundancy in the event that one of my drives ever failed. In that scenario, I still would be able to run a functioning server with all my data until I acquired a replacement. The only downside to this setup is that even though I have 8 TB worth of space, only half of it is usable. But that’s a price I’m willing to pay for having peace of mind in the event that one of my drives unexpectedly gives up.
</p>

<p><span class="image right"><img src="{% link assets/images/ubuntu.png %}" alt="" /></span>With the framework laid out for my server, I configured SSH (secure shell) and then found a home for the server in my dad's office. SSH allows you to use another computer's command line to remote into the server and operate it as if you were physically in front of it.</p>

<hr class="major" />

<h2>Key Programs</h2>

<h3>Nextcloud</h3>

<span class="image fit"><img src="{% link assets/images/nextcloud.png %}" alt="" /></span>

<p><span class="image right"><img src="{% link assets/images/Nextcloud.jpg %}" alt="" /></span>To begin sorting out my mom’s phone storage woes immediately, I installed <a href="https://nextcloud.com/">Nextcloud</a>. Nextcloud is a self hosted cloud platform that can be used to store files, setup Email servers, Calendars, and so on. You can think of it like Google Drive but with no paltry 15 GB storage limit. Instead, Nextcloud gets as much space as you provide it, in this case it is 4 TB. For my installation, I chose to go down the Snap path. My use case for Nextcloud is as vanilla as it gets so, I didn’t see any reason to pick the native path regardless of how configurable it may be. 
</p>
<p>Additionally, the <a href="https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-nextcloud-on-ubuntu-20-04">guide</a> that I followed provided very easy instructions to setup SSL (encryption) on a domain/dynamic DNS host you owned. In simpler terms, this allowed me to make my Nextcloud account accessible from anywhere in the world while maintaining a decent amount of security for my family’s sensitive data. There were a few ports that needed to be forwarded but luckily the Sasktel router that my house came with had such functionality.
</p>
<p>Once the service on my server was up and running, I set up user accounts and installed the mobile phone apps for everyone in my family that needed the photo backups. The feature works brilliantly; when a photo is taken by a user, it automatically backs it up to Nextcloud. Google’s paltry 15 GB of space would no longer be filled in a pinch! I also setup a sync between my dad’s external hard drive connected to his main PC and Nextcloud so that his data would be accessible from everywhere without having to lug around a hard drive safely. And since his personal PC and the server are connected through a Gigabit ethernet switch, he has access to mass high speed storage when he’s working at home.</p>

<pre><code>sudo snap install nextcloud</code></pre>

<hr class="major" />

<h3>Plex</h3>
<p>The next program that I installed and configured was <a href="https://www.plex.tv/">Plex</a>. Plex is an amazing streaming service that organizes the media you have by tagging it with metadata and presenting it in a neat manner via the many clients it has. Plus, you can access the media on your server from anywhere meaning that while I’m across the Pacific in Australia, I’ll be able to sit back and watch my collection of movies and family videos without having to download or carry them. For Plex, I also went the Snap installation route and after getting my libraries setup, I let the program do all the work. </p>

<p>As all the Plex libraries are located on the 4 TB WD Red drive separate from my Nextcloud installation, I can’t manage the folders/files on this drive without the help of a handy <a href="https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/external_storage_configuration_gui.html">app</a> in the Nextcloud store. This allows you to link folders outside of your Nextcloud data directory to be accessible within the service. This way I can manage my entire Plex library from inside Nextcloud.</p>
<pre><code>sudo snap install plexmediaserver</code></pre>
<span class="image fit"><img src="{% link assets/images/plex.png %}" alt="" /></span>

<hr class="major" />

<h3>qBittorrent</h3>

<p>My Plex installation wouldn’t really be complete without a torrent client to go along with it. My personal preference is to use <a href="https://www.qbittorrent.org/">qBittorrent</a> as it’s what I’m familiar with on Windows. It’s accessible to control via a web interface in a browser, or you could also download a phone client such as Transdroid on your phone for convenience.</p>
<pre><code>sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-stable
sudo apt install qbittorrent-nox</code></pre>

<hr class="major" />

<h3>OpenVPN</h3>
<p><span class="image right"><img src="{% link assets/images/OpenVPN.jpg %}" alt="" /></span>Finally, the last application that I will use the server for is <a href="https://openvpn.net/">OpenVPN</a>. Like most VPN services, OpenVPN encrypts your data and keeps it away from prying eyes such as your ISP and other onlookers on the internet. It also lets me remotely tunnel into my home’s network if I needed to do so. For example, if the Kangaroonian Netflix doesn’t have a show I like, I can tunnel into my home’s network and view everything Canadian Netflix has in its catalogue. A niche utility, sure but it’ll be nice to have in a pinch if my parents need me to randomly fix the router while I’m away. </p>

<p>Once again, the installation was straightforward as I followed this simple five-minute <a href="https://www.cyberciti.biz/faq/howto-setup-openvpn-server-on-ubuntu-linux-14-04-or-16-04-lts/">guide</a> without delving into anything too excessive for my usage.</p>

<pre><code>wget https://git.io/vpn -O openvpn-install.sh
sudo chmod +x openvpn-install.sh
sudo bash openvpn-install.sh</code></pre>

<hr class="major" />

<h3>Misc Utillities worth Mentioning</h3>
<p>And that’s it. I installed a few minor programs here and there, mostly to help me with getting access to information without memorizing obscure commands I would need rarely. For example, Glances is an excellent task manager like tool that I can use to see what my server is doing from anywhere through SSH.</p>
<p>Midnight Commander is also a useful command line file explorer that made me a bit more trustworthy of the commands I was executing as I could see the changes I was making easily.</p>

<hr class="major" />

<h2>Wrap Up</h2>
<p>So far, I’ve been running this setup for two weeks and am very satisfied with the lack of performance issues I’ve had. There have been a few glitchy experiences with the Nextcloud app on mobile regarding the auto photo uploads but they can be easily resolved with an app restart. Another gripe that I’ve had is the lack of speed between a client and the server on a Gigabit connection through Nextcloud. Instead of getting anywhere close to the theoretical data transfer speeds of 1000 mb/s, instead it’s closer to approximately 400 or so. I believe this issue is specific to Nextcloud as file shares using protocols other than WebDAV (what Nextcloud uses) such as FTP or SMB yield closer to the full 1000 mb/s. Currently, I have no solution for this issue despite forum posts with similar topics being discussed. For now, the speed is fine for my father’s usage as he doesn’t deal with too much data transfer at once. It’s also serviceable for other applications such as photo backups and Plex streaming which needs to utilize far less data through put.</p>
<p>In terms of the upsides, my grandparents and parents alike are also enjoying having old family media accessible through Plex on their tablets and phones without dealing with easily misplaced USBs. In fact, these past weeks have been a trip down memory lane as we all gather around the TV to seamlessly browse through years of photos and videos together. My dad’s life has also been made easier as his 250 GB worth of business data can be accessed from anywhere he goes at speed comparable to Google Drive, but with no expense associated. And in terms of myself, well I’m perfectly content with being able to watch my movies and shows without the prospect of my mother calling me out of room to sort her phone out.</p>
<p>Thank you for making it to the end of my summary building a homeserver; I hope this entices you to do something similar for the sake of breathing new life into abandoned gear. If you have any questions or need help regarding anything I discussed today, please do not hesitate to ask and thank you once again!</p>

