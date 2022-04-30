---
title: How to install ArchLinux in seconds
subtitle: Using this script can save you a lot of time. It goes through all the initial steps automatically, so the only thing you need to do is launch the script and wait until it's done. Get the script, launch the script, done. Here's how.
metadescription: This unattended ArchLinux installation script can save you a lot of time. Get the script, launch the script, done.
author: TechKeep
authormainsociallink: https://twitter.com/TechKeepNet/
layout: post
category: post
date: 2022-04-25 12:39:15
categories: ['pinned', 'linux', 'linux-tips']
cattagText: Linux
cattag: linux
image: /img/post-headers/archlinux_logo_bg.png
photocredit: <!--<em>(Photo credit - <a href="#" target="_blank" rel="noreferrer noopener">Source Name</a>)</em>-->
twitterlink: https://twitter.com/TechKeepNet/status/1519167145942429697
redditlink: https://www.reddit.com/r/TechKeep/comments/ucskt6/how_to_install_archlinux_in_seconds/
---

{% include post-image.html %}

<p>Yes, I made an ArchLinux install script. Over time, I found myself having to install ArchLinux on various devices and Virtual Machines a lot for test purposes. Of course, I could've installed it once and then simply cloned it to new devices or VMs, but this was not always ideal. Sometimes, I needed fresh and up-to-date installs.</p>

<p>So, I recently re-made my personal install script which I <a href="https://github.com/TechKeep/archun" target="_blank" rel="noreferrer noopener">made available over on TechKeep's GitHub repository</a> and named it "ArchUn".</p>

<p>It only takes a few seconds to download and launch the script with its default settings. With it, performing a basic ArchLinux installation <b><em>takes around 1 minute</em></b> (depending on download speeds). <!--Please note that the script doesn't install a Desktop Environment automatically yet, but it eventually will have an option for it. In the meantime, I have included an extra step at the bottom of the article to show you how to do it manually (and it's very simple).--> The whole process (initial installation <em>and</em> installing a Desktop Environment) takes under 5 minutes in total. <a href="https://www.youtube.com/watch?v=vbfKL4s_P-Y" target="_blank" rel="noreferrer noopener">Here's a demo (of an early version) I uploaded to YouTube; it only took under 4 minutes.</a></p>

<p><b>A fair warning, however: this script will format and use the whole destination drive (in other words, erase <em>everything</em>), so it's not meant to be used to add ArchLinux as a dual-boot option</b>. Of course, you can always install this first, and then install a dual-boot-friendly operating system afterwards.</p>

<p><em>Please note that this script is still in an experimental state and will be enhanced over time.</em></p>

&nbsp;

<h4>Preparing for installation</h4>

<p>The first thing you need to do is to grab ArchLinux's latest <em>.iso</em> file from their <a href="https://archlinux.org/download/" target="_blank" rel="noreferrer noopener">download page</a>. Once you have that, prepare the installation media of your choice using tools such as <a href="https://www.balena.io/etcher/" target="_blank" rel="noreferrer noopener">etcher</a> or <a href="https://rufus.ie/en/" target="_blank" rel="noreferrer noopener">rufus</a> (<em>you do not need to use these tools if you are installing ArchLinux in a Virtual Machine; you only need the .iso file</em>) and boot up the machine with the installation media.</p>

<p>Once you have booted into the installation media and are presented with a command prompt, you can start the process below.</p>

&nbsp;

<h4>Step 1 - Getting the script</h4>

<ol class="ol-li-separation">&nbsp;
	<li><b>Type in the following and press ENTER (yes, you also need to include the <code>https://</code>):</b></li>
	<li style="list-style-type:none;"><pre><code class="language-bash">curl https://raw.githubusercontent.com/TechKeep/archun/main/archun.sh -o archun.sh</code></pre></li>
	<li value="2"><b>ArchUn is now downloaded.</b></li>
</ol>
&nbsp;

<h4 id="step1p2InstallationDrive">Step 1.2 - Installation Drive</h4>
<div style="background-color:#fff4e0;border:1px solid black;padding:5px;text-align:center;margin-top:30px;">
	<p><span style="font-size:18px;">/!\ <b><em>WARNING</em></b>: The default settings assume your installation drive is <code>/dev/sda</code> /!\</span></p>
	<p>You can find out the name of the drive you want to use using the following command (the -l is a lowercase L): <code class="language-bash">fdisk -l</code></p>
	<div style="padding-top:25px;padding-bottom:25px;text-align:center;">
		<img alt="Fdisk command output" src="/img/uploads/2022-04-25/how-to-install-archlinux-in-seconds/fdisk_-l_output.png" width="100%" height="100%" style="max-width:480px;"/>
		<br><span class="post-photo-credit"><em>The output of the fdisk command. I have highlighted what you want to know with a green rectangle.</em></span>
	</div>
	<ul style="text-align:left;">
		<li><b>If your drive's name is something other than <code>/dev/sda</code>, please follow the instructions below.</b></li>
		<li><b>If your drive's name IS <code>/dev/sda</code>, you can move directly to "<em><a href="#step2LaunchingArchUn">Step 2 - Launching ArchUn</a></em>".</b></li>
	</ul>
</div>

&nbsp;

<p>In order to change your installation drive, you must follow these steps:</p>

<ol class="ol-li-separation">
	<li value="1"><b>Use <code>nano</code> to open the script in text mode:</b></li>
	<li style="list-style-type:none;">
		<pre><code class="language-bash">nano archun.sh</code></pre>
	</li>
	<li value="2"><b>Find the <code>DEFAULTDISK</code> variable within the "<em>User-defined variables</em>" section.</b></li>
	<li><b>Change <code>/dev/sda</code> to the name your drive uses (which you found out with the <code>fdisk -l</code> command).</b></li>
	<li><b>If you have an NVMe drive and its name is something like <code>/dev/nvme0n1</code>, pay attention to the comments around the variable.</b></li>
	<li value="4"><b>Once everything is set correctly, save and exit out of the text editor.</b>
		<br>With <code>nano</code>, you need to press <em>CTRL+X</em>, press <em>Y</em> and then press <em>ENTER</em>.
	</li>
</ol>

&nbsp;

<h4 id="step2LaunchingArchUn">Step 2 - Launching ArchUn</h4>

<p><em><b>(OPTIONAL)</b> If you want to edit any settings, open the script with a text editor (<a href="#theExtras">more info at the bottom of the page</a>).</em></p>

<p>If everything looks fine and you understand that <b><em>this script will format and use the whole destination drive (which will overwrite and erase everything)</em></b>, you are ready to proceed.</p>

<ol class="ol-li-separation">
	<li><b>Launch the script:</b></li>
	<li style="list-style-type:none;">
		<pre><code class="language-bash">bash archun.sh</code></pre>
	</li>
	<li value="2"><b>Press <em>1</em> and then <em>ENTER</em> to select the option named "I understand".</b></li>
	<li><b>You will be presented with a detailed menu asking you in which mode you want to proceed. Choose carefully.</b></li>
	<li><b>You will once again get a few warnings about erasing the whole drive. Press <em>ENTER</em> a few times to accept and proceed.</b></li>
	<li><b>Once everything is over, you will be asked to create a password.</b><br>This will be the password for the <code>root</code> account.</li>
	<li><b>If you chose to install extras at the beginning, this is when the menu will appear. If not, the script will exit.</b></li>
	<li><b>Installation complete!</b></li>
</ol>

&nbsp;

<h4>Conclusion</h4>

<p>The installation is complete. You can now eject your installation media and reboot the machine and be met with GRUB2 (a boot manager), which will allow you to boot into your ArchLinux installation.</p>

<p>If you installed a Desktop Environment, don't forget to select it in the Session Manager before logging in.</p>

<div style="padding-top:25px;padding-bottom:25px;text-align:center;">
	<img alt="Screenshot of Neofetch output in command-line" src="/img/uploads/2022-04-25/how-to-install-archlinux-in-seconds/neofetch-logged-in-as-root.png" width="100%" height="100%" style="max-width:618px;"/>
	<br><span class="post-photo-credit"><em><code>NEOFETCH</code> was used to display system information in command-line mode.</em></span>
</div>

<div style="padding-top:25px;padding-bottom:25px;text-align:center;">
	<img alt="Desktop Environment selection form" src="/img/uploads/2022-04-25/how-to-install-archlinux-in-seconds/select-xfce-session.png" width="100%" height="100%" style="max-width:305px;"/>
	<br><span class="post-photo-credit"><em>With <code>LXDM</code>, this is located in the bottom left corner.</em></span>
</div>

<div style="padding-top:25px;padding-bottom:25px;text-align:center;">
	<img alt="Screenshot of XFCE4's Desktop Environment" src="/img/uploads/2022-04-25/how-to-install-archlinux-in-seconds/xfce4-desktop-environment.png" width="100%" height="100%" style="max-width:800px;"/>
	<br><span class="post-photo-credit"><em>Screenshot of the final result when using <code>XFCE</code> as a Desktop Environment with its default configuration.<code></code></em></span>
</div>

&nbsp;

<h4 id="theExtras">(OPTIONAL) Changing the default settings</h4>

&nbsp;

<ol class="ol-li-separation">
	<li value="1"><b>This is the list of settings you can edit:</b></li>
	<li style="list-style-type:none;">
		<pre><code class="language-bash">
			DEFAULTDISK="/dev/sda"
			BOOTPARTNUM="1"
			SWAPPARTNUM="2"
			ROOTPARTNUM="3"
			TIMEZONESTRING="America/Toronto"
			LOCALEGEN="en_CA.UTF-8 UTF-8"
			LOCALELANG="LANG=en_CA.UTF-8"
			THEHOSTNAME="arch"
			BOOTPART="300"
			SWAPPART="4000"
			ROOTPART="100"
			ROOTPARTSIZETYPE="%"
		</code></pre>
	</li>
	<li value="2"><b>If you want to edit any of these settings, open the script with a text editor:</b></li>
	<li style="list-style-type:none;">
		<pre><code class="language-bash">nano archun.sh</code></pre>
	</li>
	<li value="3"><b>Move to a value that you wish to change within the "<em>User-defined variables</em>" section.</b></li>
	<li><b>MAKE SURE TO READ THE NOTES AROUND THESE VARIABLES WITHIN THE FILE TO KNOW EXACTLY WHAT THEY DO.</b><br>For this example, we will be changing the default LINUX SWAP value, named <code>SWAPPART</code>. The number is in MiB. The default value for this one is 4000, which is roughly 4GB of SWAP (around 4.19GB). If you want for example 8GB, you would replace this value with 8000, like so:
	</li>
	<li style="list-style-type:none;">
		<pre><code class="language-bash">
			# Swap partition size in MiB. Number only.
			SWAPPART="8000"
		</code></pre>
		<em>The amount of SWAP you need depends heavily on your use case. A good rule of thumb is to use 4GB or to follow these guidelines:
			<ul>
				<li>2x your amount of RAM when you have 2GB of RAM or less,</li>
				<li>1x your amount of RAM when you have between 2GB and 8GB of RAM,</li>
				<li>0.5x your amount of RAM (minimum 4GB of SWAP) when you have between 8GB and 64GB of RAM,</li>
				<li>absolute minimum of 4GB of SWAP when you have over 64GB of RAM.</li>
			</ul>
		This is why I used 4GB as a default. Please note that none of these choices have hibernation in mind.</em>
	</li>
	<li value="5"><b>Once you are happy with your settings, save and exit out of the text editor.</b>
		<br>With <code>nano</code>, you need to press <em>CTRL+X</em>, press <em>Y</em> and then press <em>ENTER</em>.
	</li>
	<li><b>You can carry on with the installation by following "<em><a href="#step2LaunchingArchUn">Step 2 - Launching ArchUn</a></em>".</b></li>
</ol>

&nbsp;

<p style="font-style:italic;text-align:center;">Last edited on April 30 2022</p>

{% include comments-social.html %}