---
layout: page
title: Gringotts - creating a home server
nav-menu: false
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
Compounded with the growing <i>ahem</i> torrented media in my possession and my dad's specific need of making the data on his hard drive to be accessible from anywhere, I decided it was time to brainstorm a creative solution to handle it all together.
</p>

<hr class="major" />

<h2>Why a Homeserver</h2>
<p><span class="image left"><img src="{% link assets/images/server.jpg %}" alt="" /></span>In the beginning brainstorm stage, I recognized two options: Find a solution for archiving my family's data locally or convince my parents to purchase cloud storage. The latter was especially attractive at first considering how cheap plans like Google One are. At the time of writing this, a 2 TB space is only $13.99 CAD a month. For the general population, this buy and forget solution is the de-facto solution for a safe space to store sensitive data and media. And it comes with other benefits such as being accessible from anywhere and the integration with the Google ecosystem which is invaluable to many.</p>
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
<p>The installation was seamless: download an image, burn it onto a USB with Balena Etcher, and boot off the USB with the help of the BIOS. Follow the straightforward prompts to customize the installation to your liking and you’ll be running the core of your system in no time.
</p>
<p>During my own installation, I opted to setup a RAID configuration directly out of the gate during installation. RAID, an acronym for Redundant Array of Independent Disks, is a technology to merge physical drives into combined units. Doing so allows you to improve performance, create redundancy, or do both.
</p>
<p>Following this brilliant guide from fevangelou, I was able to setup RAID 1 (mirroring) on two of my WD Blue drives which would ensure I had data redundancy in the event that one of my drives ever failed. In that scenario, I still would be able to run a functioning server with all my data until I acquired a replacement. The only downside to this setup is that even though I have 8 TB worth of space, only half of it is usable. But that’s a price I’m willing to pay for having peace of mind in the event that one of my drives unexpectedly gives up.
</p>

<p><span class="image right"><img src="{% link assets/images/ubuntu.png %}" alt="" /></span>With the framework laid out for my server, I configured SSH (secure shell) and then found a home for the server in my dad's office. SSH allows you to use another computer's command line to remote into the server and operate it as if you were physically in front of it.</p>

<hr class="major" />

<h2>Key Programs</h2>

<h3>Nextcloud</h3>

<span class="image fit"><img src="{% link assets/images/nextcloud.png %}" alt="" /></span>

<p><span class="image right"><img src="{% link assets/images/Nextcloud.jpg %}" alt="" /></span>To begin sorting out my mom’s phone storage woes immediately, I installed Nextcloud. Nextcloud is a self hosted cloud platform that can be used to store files, setup Email servers, Calendars, and so on. You can think of it like Google Drive but with no paltry 15 GB storage limit. Instead, Nextcloud gets as much space as you provide it, in this case it is 4 TB. For my installation, I chose to go down the Snap path. My use case for Nextcloud is as vanilla as it gets so, I didn’t see any reason to pick the native path regardless of how configurable it may be. 
</p>
<p>Additionally, the guide that I followed provided very easy instructions to setup SSL (encryption) on a domain/dynamic DNS host you owned. In simpler terms, this allowed me to make my Nextcloud account accessible from anywhere in the world while maintaining a decent amount of security for my family’s sensitive data. There were a few ports that needed to be forwarded but luckily the Sasktel router that my house came with had such functionality.
</p>
<p>Once the service on my server was up and running, I set up user accounts and installed the mobile phone apps for everyone in my family that needed the photo backups. The feature works brilliantly; when a photo is taken by a user, it automatically backs it up to Nextcloud. Google’s paltry 15 GB of space would no longer be filled in a pinch! I also setup a sync between my dad’s external hard drive connected to his main PC and Nextcloud so that his data would be accessible from everywhere without having to lug around a hard drive safely. And since his personal PC and the server are connected through a Gigabit ethernet switch, he has access to mass high speed storage when he’s working at home.</p>

<hr class="major" />

<h3>Plex</h3>

<p>The next program that I installed and configured was Plex. Plex is an amazing streaming service that organizes the media you have by tagging it with metadata and presenting it in a neat manner via the many clients it has. Plus, you can access the media on your server from anywhere meaning that while I’m across the Pacific in Australia, I’ll be able to sit back and watch my collection of movies and family videos without having to download or carry them. For Plex, I also went the Snap installation route and after getting my libraries setup, I let the program do all the work. </p>

<p>As all the Plex libraries are located on the 4 TB WD Red drive separate from my Nextcloud installation, I can’t manage the folders/files on this drive without the help of a handy app in the Nextcloud store. This allows you to link folders outside of your Nextcloud data directory to be accessible within the service. This way I can manage my entire Plex library from inside Nextcloud.</p>

<!-- Elements -->
<h2 id="elements">Elements</h2>
<div class="row 200%">
	<div class="6u 12u$(medium)">

<!-- Text stuff -->
<h3>Text</h3>
<p>This is <b>bold</b> and this is <strong>strong</strong>. This is <i>italic</i> and this is <em>emphasized</em>.
This is <sup>superscript</sup> text and this is <sub>subscript</sub> text.
This is <u>underlined</u> and this is code: <code>for (;;) { ... }</code>.
Finally, this is a <a href="#">link</a>.</p>
<hr />
<h2>Heading Level 2</h2>
<h3>Heading Level 3</h3>
<h4>Heading Level 4</h4>
<hr />
<p>Nunc lacinia ante nunc ac lobortis. Interdum adipiscing gravida odio porttitor sem non mi integer non faucibus ornare mi ut ante amet placerat aliquet. Volutpat eu sed ante lacinia sapien lorem accumsan varius montes viverra nibh in adipiscing blandit tempus accumsan.</p>

<!-- Lists -->
<h3>Lists</h3>
<div class="row">
	<div class="6u 12u$(small)">

		<h4>Unordered</h4>
		<ul>
			<li>Dolor etiam magna etiam.</li>
			<li>Sagittis lorem eleifend.</li>
			<li>Felis dolore viverra.</li>
		</ul>

		<h4>Alternate</h4>
		<ul class="alt">
			<li>Dolor etiam magna etiam.</li>
			<li>Sagittis lorem eleifend.</li>
			<li>Felis feugiat viverra.</li>
		</ul>

	</div>
	<div class="6u$ 12u$(small)">

		<h4>Ordered</h4>
		<ol>
			<li>Dolor etiam magna etiam.</li>
			<li>Etiam vel lorem sed viverra.</li>
			<li>Felis dolore viverra.</li>
			<li>Dolor etiam magna etiam.</li>
			<li>Etiam vel lorem sed viverra.</li>
			<li>Felis dolore viverra.</li>
		</ol>

		<h4>Icons</h4>
		<ul class="icons">
			<li><a href="#" class="icon fa-twitter"><span class="label">Twitter</span></a></li>
			<li><a href="#" class="icon fa-facebook"><span class="label">Facebook</span></a></li>
			<li><a href="#" class="icon fa-instagram"><span class="label">Instagram</span></a></li>
			<li><a href="#" class="icon fa-github"><span class="label">Github</span></a></li>
			<li><a href="#" class="icon fa-dribbble"><span class="label">Dribbble</span></a></li>
			<li><a href="#" class="icon fa-tumblr"><span class="label">Tumblr</span></a></li>
		</ul>
		<ul class="icons">
			<li><a href="#" class="icon alt fa-twitter"><span class="label">Twitter</span></a></li>
			<li><a href="#" class="icon alt fa-facebook"><span class="label">Facebook</span></a></li>
			<li><a href="#" class="icon alt fa-instagram"><span class="label">Instagram</span></a></li>
		</ul>

	</div>
</div>

<h4>Definition</h4>
<dl>
	<dt>Item1</dt>
	<dd>
		<p>Lorem ipsum dolor vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent. Lorem ipsum dolor.</p>
	</dd>
	<dt>Item2</dt>
	<dd>
		<p>Lorem ipsum dolor vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent. Lorem ipsum dolor.</p>
	</dd>
	<dt>Item3</dt>
	<dd>
		<p>Lorem ipsum dolor vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent. Lorem ipsum dolor.</p>
	</dd>
</dl>

<h4>Actions</h4>
<ul class="actions">
	<li><a href="#" class="button special">Default</a></li>
	<li><a href="#" class="button">Default</a></li>
</ul>
<ul class="actions small">
	<li><a href="#" class="button special small">Small</a></li>
	<li><a href="#" class="button small">Small</a></li>
</ul>
<div class="row">
	<div class="6u 12u$(small)">
		<ul class="actions vertical">
			<li><a href="#" class="button special">Default</a></li>
			<li><a href="#" class="button">Default</a></li>
		</ul>
	</div>
	<div class="6u$ 12u$(small)">
		<ul class="actions vertical small">
			<li><a href="#" class="button special small">Small</a></li>
			<li><a href="#" class="button small">Small</a></li>
		</ul>
	</div>
	<div class="6u 12u$(small)">
		<ul class="actions vertical">
			<li><a href="#" class="button special fit">Default</a></li>
			<li><a href="#" class="button fit">Default</a></li>
		</ul>
	</div>
	<div class="6u$ 12u$(small)">
		<ul class="actions vertical small">
			<li><a href="#" class="button special small fit">Small</a></li>
			<li><a href="#" class="button small fit">Small</a></li>
		</ul>
	</div>
</div>

<!-- Blockquote -->
<h3>Blockquote</h3>
<blockquote>Fringilla nisl. Donec accumsan interdum nisi, quis tincidunt felis sagittis eget tempus euismod. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan faucibus. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis.</blockquote>

<!-- Table -->
<h3>Table</h3>

<h4>Default</h4>
<div class="table-wrapper">
	<table>
		<thead>
			<tr>
				<th>Name</th>
				<th>Description</th>
				<th>Price</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Item1</td>
				<td>Ante turpis integer aliquet porttitor.</td>
				<td>29.99</td>
			</tr>
			<tr>
				<td>Item2</td>
				<td>Vis ac commodo adipiscing arcu aliquet.</td>
				<td>19.99</td>
			</tr>
			<tr>
				<td>Item3</td>
				<td> Morbi faucibus arcu accumsan lorem.</td>
				<td>29.99</td>
			</tr>
			<tr>
				<td>Item4</td>
				<td>Vitae integer tempus condimentum.</td>
				<td>19.99</td>
			</tr>
			<tr>
				<td>Item5</td>
				<td>Ante turpis integer aliquet porttitor.</td>
				<td>29.99</td>
			</tr>
		</tbody>
		<tfoot>
			<tr>
				<td colspan="2"></td>
				<td>100.00</td>
			</tr>
		</tfoot>
	</table>
</div>

<h4>Alternate</h4>
<div class="table-wrapper">
	<table class="alt">
		<thead>
			<tr>
				<th>Name</th>
				<th>Description</th>
				<th>Price</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Item1</td>
				<td>Ante turpis integer aliquet porttitor.</td>
				<td>29.99</td>
			</tr>
			<tr>
				<td>Item2</td>
				<td>Vis ac commodo adipiscing arcu aliquet.</td>
				<td>19.99</td>
			</tr>
			<tr>
				<td>Item3</td>
				<td> Morbi faucibus arcu accumsan lorem.</td>
				<td>29.99</td>
			</tr>
			<tr>
				<td>Item4</td>
				<td>Vitae integer tempus condimentum.</td>
				<td>19.99</td>
			</tr>
			<tr>
				<td>Item5</td>
				<td>Ante turpis integer aliquet porttitor.</td>
				<td>29.99</td>
			</tr>
		</tbody>
		<tfoot>
			<tr>
				<td colspan="2"></td>
				<td>100.00</td>
			</tr>
		</tfoot>
	</table>
</div>

</div>
<div class="6u$ 12u$(medium)">

<!-- Buttons -->
<h3>Buttons</h3>
<ul class="actions">
	<li><a href="#" class="button special">Special</a></li>
	<li><a href="#" class="button">Default</a></li>
</ul>
<ul class="actions">
	<li><a href="#" class="button big">Big</a></li>
	<li><a href="#" class="button">Default</a></li>
	<li><a href="#" class="button small">Small</a></li>
</ul>
<ul class="actions">
	<li><a href="#" class="button special big">Big</a></li>
	<li><a href="#" class="button special">Default</a></li>
	<li><a href="#" class="button special small">Small</a></li>
</ul>
<ul class="actions fit">
	<li><a href="#" class="button special fit">Fit</a></li>
	<li><a href="#" class="button fit">Fit</a></li>
</ul>
<ul class="actions fit small">
	<li><a href="#" class="button special fit small">Fit + Small</a></li>
	<li><a href="#" class="button fit small">Fit + Small</a></li>
</ul>
<ul class="actions">
	<li><a href="#" class="button special icon fa-search">Icon</a></li>
	<li><a href="#" class="button icon fa-download">Icon</a></li>
</ul>
<ul class="actions">
	<li><span class="button special disabled">Special</span></li>
	<li><span class="button disabled">Default</span></li>
</ul>

<!-- Form -->
<h3>Form</h3>

<form method="post" action="#">
	<div class="row uniform">
		<div class="6u 12u$(xsmall)">
			<input type="text" name="demo-name" id="demo-name" value="" placeholder="Name" />
		</div>
		<div class="6u$ 12u$(xsmall)">
			<input type="email" name="demo-email" id="demo-email" value="" placeholder="Email" />
		</div>
		<!-- Break -->
		<div class="12u$">
			<div class="select-wrapper">
				<select name="demo-category" id="demo-category">
					<option value="">- Category -</option>
					<option value="1">Manufacturing</option>
					<option value="1">Shipping</option>
					<option value="1">Administration</option>
					<option value="1">Human Resources</option>
				</select>
			</div>
		</div>
		<!-- Break -->
		<div class="4u 12u$(small)">
			<input type="radio" id="demo-priority-low" name="demo-priority" checked>
			<label for="demo-priority-low">Low</label>
		</div>
		<div class="4u 12u$(small)">
			<input type="radio" id="demo-priority-normal" name="demo-priority">
			<label for="demo-priority-normal">Normal</label>
		</div>
		<div class="4u$ 12u$(small)">
			<input type="radio" id="demo-priority-high" name="demo-priority">
			<label for="demo-priority-high">High</label>
		</div>
		<!-- Break -->
		<div class="6u 12u$(small)">
			<input type="checkbox" id="demo-copy" name="demo-copy">
			<label for="demo-copy">Email me a copy</label>
		</div>
		<div class="6u$ 12u$(small)">
			<input type="checkbox" id="demo-human" name="demo-human" checked>
			<label for="demo-human">I am a human</label>
		</div>
		<!-- Break -->
		<div class="12u$">
			<textarea name="demo-message" id="demo-message" placeholder="Enter your message" rows="6"></textarea>
		</div>
		<!-- Break -->
		<div class="12u$">
			<ul class="actions">
				<li><input type="submit" value="Send Message" class="special" /></li>
				<li><input type="reset" value="Reset" /></li>
			</ul>
		</div>
	</div>
</form>

<!-- Image -->
<h3>Image</h3>

<h4>Fit</h4>
<span class="image fit"><img src="{% link assets/images/pic03.jpg %}" alt="" /></span>
<div class="box alt">
	<div class="row 50% uniform">
		<div class="4u"><span class="image fit"><img src="{% link assets/images/pic08.jpg %}" alt="" /></span></div>
		<div class="4u"><span class="image fit"><img src="{% link assets/images/pic09.jpg %}" alt="" /></span></div>
		<div class="4u$"><span class="image fit"><img src="{% link assets/images/pic10.jpg %}" alt="" /></span></div>
		<!-- Break -->
		<div class="4u"><span class="image fit"><img src="{% link assets/images/pic10.jpg %}" alt="" /></span></div>
		<div class="4u"><span class="image fit"><img src="{% link assets/images/pic08.jpg %}" alt="" /></span></div>
		<div class="4u$"><span class="image fit"><img src="{% link assets/images/pic09.jpg %}" alt="" /></span></div>
		<!-- Break -->
		<div class="4u"><span class="image fit"><img src="{% link assets/images/pic09.jpg %}" alt="" /></span></div>
		<div class="4u"><span class="image fit"><img src="{% link assets/images/pic10.jpg %}" alt="" /></span></div>
		<div class="4u$"><span class="image fit"><img src="{% link assets/images/pic08.jpg %}" alt="" /></span></div>
	</div>
</div>

<h4>Left &amp; Right</h4>
<p><span class="image left"><img src="{% link assets/images/pic09.jpg %}" alt="" /></span>Lorem ipsum dolor sit accumsan interdum nisi, quis tincidunt felis sagittis eget. tempus euismod. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent tincidunt felis sagittis eget. tempus euismod. Vestibulum ante ipsum primis sagittis eget. tempus euismod. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent tincidunt felis sagittis eget tempus vestibulum ante ipsum primis in faucibus magna blandit adipiscing eu felis iaculis.</p>
<p><span class="image right"><img src="{% link assets/images/pic10.jpg %}" alt="" /></span>Lorem ipsum dolor sit accumsan interdum nisi, quis tincidunt felis sagittis eget. tempus euismod. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent tincidunt felis sagittis eget. tempus euismod. Vestibulum ante ipsum primis sagittis eget. tempus euismod. Vestibulum ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent tincidunt felis sagittis eget tempus vestibulum ante ipsum primis in faucibus magna blandit adipiscing eu felis iaculis.</p>

<!-- Box -->
<h3>Box</h3>
<div class="box">
	<p>Felis sagittis eget tempus primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus. Integer ac pellentesque praesent tincidunt felis sagittis eget. tempus euismod. Magna sed etiam ante ipsum primis in faucibus vestibulum. Blandit adipiscing eu ipsum primis in faucibus vestibulum. Blandit adipiscing eu felis iaculis volutpat ac adipiscing accumsan eu faucibus lorem ipsum.</p>
</div>

<!-- Preformatted Code -->
<h3>Preformatted</h3>
<pre><code>i = 0;

while (!deck.isInOrder()) {
    print 'Iteration ' + i;
    deck.shuffle();
    i++;
}

print 'It took ' + i + ' iterations to sort the deck.';
</code></pre>

</div>
</div>

</div>
</section>

</div>
