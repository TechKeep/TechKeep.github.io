---
title: How to install ArchLinux in seconds
subtitle: Yes, I made an ArchLinux install script. Using this script can save you a lot of time. It goes through all the initial steps automatically, so the only thing you need to do is launch the script and wait until it's done. Get the script, launch the script, done. Here's how.
metadescription: This unattended ArchLinux installation script can save you a lot of time. Get the script, launch the script, done.
layout: post
category: post
date: 2022-04-25 12:39:15
categories: ['linux', 'linux-tips']
cattagText: Linux
cattag: linux
image: /img/post-headers/archlinux_logo_bg.png
photocredit: <!--<em>(Photo credit - <a href="#" target="_blank">Source Name</a>)</em>-->
---

{% include post-image.html %}

<p>Over time, I found myself having to install ArchLinux on various devices and Virtual Machines a lot for test purposes. Of course, I could've installed it once and then simply cloned it to new devices or VMs, but this was not always ideal. Sometimes, I needed fresh and up-to-date installs.</p>

<p>So, I recently re-made my personal install script and <a href="https://github.com/TechKeep/archun" target="_blank">made it available over on TechKeep's GitHub repository</a> and named it "ArchUn".</p>

&nbsp;

<h4>Preparing for installation</h4>

<p>The first thing you need to do is to grab ArchLinux's latest <em>.iso</em> file from their <a href="https://archlinux.org/download/" target="_blank">downloads page</a>. Once you have that, prepare the installation media of your choice using tools such as <a href="https://www.balena.io/etcher/" target="_blank">etcher</a> or <a href="https://rufus.ie/en/" target="_blank">rufus</a> (<em>you do not need to use these tools if you are installing ArchLinux in a Virtual Machine; you only need the .iso file</em>) and boot up the machine with the installation media.</p>

<p>Once you have booted into the installation media and are presented with a command prompt, you can start the process below.</p>

&nbsp;

<h5>Step 1 - Getting the script</h5>

<ul>
	<li>Type in the following (I WILL SHORTEN IT LATER):</li>
	<li style="list-style-type:none;"><code class="language-bash">curl raw.github.com/TechKeep/archun/main/archun.sh -o archun.sh</code></li>
</ul>

<p>ArchUn comes with pre-configured settings that you can change prior to launching it.</p>

<h5>Step 2 - Launching ArchUn</h5>

<ol>
	<li>Copy and paste the following into the text field:</li>
	<li style="list-style-type:none;"><code class="">reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve</code></li>
	<li value="3">Confirm the dialog (or press Enter)</li>
	<li>Either reboot your computer, or restart "explorer.exe" using the task manager.</li>
</ol>