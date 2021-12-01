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
<h2 id="content">Introduction</h2>
<p>On June 1st of this year, Google announced an end to their "free, unlimited" cloud storage solution for anyone with access to their service. Instead, uploading media to their servers would now count towards a 15 GB quota that would need to carefully be managed by the user as the space would be shared between Google Drive, Google Photos, and Gmail. Fast forward to November and I begin to receive a barrage of complaints from my parents regarding space running out on their Google accounts; the free 15 GB had filled up surprisingly quick.
</p>

<p>
Initially, I resolved to the low effort problem solving strategy at first and helped them sort out what needed to be kept and what needed to be trashed by sitting down with them one evening. But eventually this cycle began to repeat itself on a week-by-week basis until I realized I needed to come up with an alternative solution; otherwise, I would be driven mad. 
</p>

<p>
Compounded with the growing <i>ahem</i> torrented media in my possession and my dad's specific need of making the data on his hard drive to be accessible from anywhere, I decided it was time to brainstorm a creative solution to handle it all together.
</p>








<h2 id="content">Why a Homeserver</h2>

<section id="one">
	<div class="inner">
		<header class="major">
			<h2>What is this?</h2>
		</header>
		<p>In the November of 2019, I decided to build a weather app in my mission to learn mobile app development. After countless nights of trial and error in my attempt to learn Java, I decided to make things easier for myself and delved into Flutter. Flutter's simple scaffolding implementation allowed me to build a fairly versatile app in the matter of days.</p>
		<p>Powered by Dark Sky, Weather by Falcon is a reliable source of weather information and is a joy to use with it's beautiful user interface. Try it for yourself by clicking this <a href="https://play.google.com/store/apps/details?id=com.parthshah.falcon_weather&hl=en&gl=US">link</a>.</p>
	</div>
</section>

<div class="row">
	<div class="6u 12u$(small)">
		<p>In the beginning brainstorm stage, I recognized two options: Find a solution for archiving my family's data locally or convince my parents to purchase cloud storage. The latter was especially attractive at first considering how cheap plans like Google One are. At the time of writing this, a 2 TB space is only $13.99 CAD a month. For the general population, this buy and forget solution is the de-facto solution for a safe space to store sensitive data and media. And it comes with other benefits such as being accessible from anywhere and the integration with the Google ecosystem which is invaluable to many.</p>
	</div>
	<div class="6u$ 12u$(small)">
		<p>But my needs for a storage solution were different; I wanted fast transfer speeds, flexibility, and storage larger than 2 TB for all the torrented media in my possession. And past a certain point, cloud storage becomes increasingly expensive compared to running a server of your own with similar capacity. For instance, a 12 TB server ran at home with the spare hardware I had laying around would cost me about $25 dollars worth of electricity where I live. I'm only counting electricity as an expense here because unlimited internet is something my parents would pay for regardless. On the flip side, a similar 12 TB solution hosted through a cloud storage solution such as Google One would run me a monthly bill of $84. No thanks, I must save for my tuition!</p>
	</div>
	<span class="image fit"><img src="{% link assets/images/server.jpg %}" alt="" /></span>
	<!-- Break -->
	
</div>

<hr class="major" />

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
