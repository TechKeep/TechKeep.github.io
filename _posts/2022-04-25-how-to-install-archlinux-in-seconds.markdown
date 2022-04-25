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

<p><b>A fair warning, however: this script will format and use the whole destination drive, so it's not meant to add ArchLinux as a dual-boot option</b>. Of course, you can always install this first, and then install a dual-boot-friendly operating system afterwards.</p>

&nbsp;

<h4>Preparing for installation</h4>

<p>The first thing you need to do is to grab ArchLinux's latest <em>.iso</em> file from their <a href="https://archlinux.org/download/" target="_blank">downloads page</a>. Once you have that, prepare the installation media of your choice using tools such as <a href="https://www.balena.io/etcher/" target="_blank">etcher</a> or <a href="https://rufus.ie/en/" target="_blank">rufus</a> (<em>you do not need to use these tools if you are installing ArchLinux in a Virtual Machine; you only need the .iso file</em>) and boot up the machine with the installation media.</p>

<p>Once you have booted into the installation media and are presented with a command prompt, you can start the process below.</p>

&nbsp;

<h5>Step 1 - Getting the script</h5>

<p>Type in the following and press ENTER:<br>
<code class="language-bash">curl raw.githubusercontent.com/TechKeep/archun/main/archun.sh -o archun.sh</code></p>


<p>ArchUn is now downloaded. This script comes with pre-configured settings that you can change prior to launching it by using a text editor.</p>

<p><span style="font-size:18px;">/!\ <b><em>WARNING</em></b>: The default settings assume your installation drive is <code>/dev/sda</code> /!\</span>
<br>You can find out the name of the drive you want to use using the following command (the -l is a lowercase L): <code class="language-bash">fdisk -l</code></p>



<div style="padding-top:25px;padding-bottom:25px;text-align:center;">
	<img alt="Fdisk command output" src="/img/uploads/2022-04-25/how-to-install-archlinux-in-seconds/fdisk_-l_output.png" style="width:100%;max-width:480px;"/>
	<br><span class="post-photo-credit"><em>The output of the fdisk command. I have highlighted what you want to know with a green rectangle.</em></span>
</div>


<p><b>If your drive's name is something other than <code>/dev/sda</code>, or if you want to use your own settings, please follow the instructions in "<em>Step 1.2 - Configuring the script</em>".</b></p>

&nbsp;

<h5>Step 1.2 - Configuring the script</h5>

<p><b>If you want to keep the default settings, skip this step and move to "<em>Step 2 - Launching ArchUn</em>".</b> Otherwise, keep reading.</p>

<p>As I mentioned above, you can change the settings by using a text editor. By default, the ArchLinux installer is bundled with <code>vim</code>, but you can easily install a different one (<em>and if you install a different one, it will <b>NOT</b> carry over to the installation. You are currently inside the bootable media's environment, which is temporary, so feel free to use whichever one you want. It will not bloat up the machine</em>). For this example, I will install and use <code>nano</code> to edit the file.</p>

<p>If you want to use <code>nano</code>, follow these steps. It's okay to use another text editor, but you will have to adjust your approach if you do so.</p>

<ol>
	<li>Install <code>nano</code>:</li>
	<li style="list-style-type:none;"><code class="language-bash">pacman -S nano</code></li>
	<li value="2">Use <code>nano</code> to open the script:</li>
	<li style="list-style-type:none;"><code class="language-bash">nano archun.sh</code></li>
	<li value="3">
		Move to a value within the <em>User-defined variables</em> section boundaries that you wish to change.</li>
	<li>Make sure to read the notes within the file to know exactly what everything does. In this example, we will be changing the default LINUX SWAP value, named <code>SWAPPART</code>. The number is in MiB. The default value for this one is 4000, for roughly 4GB of SWAP. If you want for example 8GB, you should replace the value with 8000, like so:
	</li>
	<li style="list-style-type:none;"><code class="language-bash">SWAPPART="8000"</code></li>
	<li value="5">a</li>
	<li style="list-style-type:none;"><code class="language-bash">a</code></li>
	<li value="6">a</li>
	<li style="list-style-type:none;"><code class="language-bash">a</code></li>
	<li value="7">a</li>
	<li style="list-style-type:none;"><code class="language-bash">a</code></li>
</ol>

&nbsp;

<h5>Step 2 - Launching ArchUn</h5>

