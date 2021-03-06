---
layout: page
title: Wall-E
description: 'Computer Science 30 Capstone Project'
nav-menu: true
image: assets/images/wall-e.png
---


<!-- Main -->
<div id="main" class="alt">

<!-- One -->
<section id="one">
	<div class="inner">
		<header class="major">
			<h1>Wall-E</h1>
		</header>

<!-- Content -->
<h2 id="content">My Computer Science 30 Capstone Project.</h2>
<div class="Fit"><span class="image fit"><img src="{% link assets/images/wall-e.png %}" alt="" /></span></div>
<p>For my capstone project, I decided to build a sleek wallpaper app using Flutter and Kotlin; it features a clean design and modules are implemented with BLOC pattern.</p>

<hr class="major" />
<section id="two" class="spotlights">
	<section>
		<a href="generic.html" class="image">
			<img src="{% link assets/images/wall-e2.png %}" alt="" data-position="center center" />
		</a>
		<div class="content">
			<div class="inner">
				<header class="major">
					<h3>Simple and Modern</h3>
				</header>
				<p>As someone who recognizes and appreciates the impact of a good user experience, my goal with Wall-E was to keep it as simple as possible. Just beautiful, curated wallpapers; no sharing, spammy notifications, or ads!</p>
			</div>
		</div>
	</section>
	
</section>
<hr class="major" />
<div class="row">
	<div class="6u 12u$(small)">
		<h3>How was it built?</h3>
		<p>The app is built using an open source software development framework known as Flutter. Using Flutter, users are able to access a wide variety of widgets to build layouts quickly and easily. Below is a code snippet depicting me easily building an app bar. </p>
		<pre><code>return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.transparent,
        elevation: 0.0,
        title: Text(
          widget.category,
          style: TextStyle(fontFamily: 'Raleway'),
        ),
        centerTitle: true,
      ),
</code></pre>
	</div>
	<div class="6u$ 12u$(small)">
		<h3>My Experience</h3>
		<p>Building apps with Flutter is extremely simple and quick to pick up compared to alternatives such as Java. As a result, scaffolding the frontend and creating the backend was a matter of only a few days' worth of work. Flow charts and pre-planning? Not needed.</p>
		<p>Another fantastic aspect of using Flutter is the growing amount of open source modules. If what you need is easy to implement, chances are that someone has already built a package exactly for what you need. Lastly, Kotlin was used in some parts of the project where Flutter could not be. For example, I needed to import an open source Shared Preferences module to store data in the device's memory.</p>
		<p>Regardless of these minor issues however, I greatly enjoyed the Flutter experience and highly suggest anyone interested in learning mobile app development to give it a try first.</p>

		
</div>
</div>

<hr class="major" />

<p>Lastly, here are the goods! If anybody would like to try out this simple app and give your device a makeover, download the app by clicking this <a href="https://github.com/valvze/Wall-E/raw/main/app-release.apk">link</a>. Remember, Android only!</p>

</div>



