---
title: How to install ArchLinux in seconds
subtitle: Yes, I made an ArchLinux install script. Using this script can save you a lot of time. It goes through all the initial steps automatically, so the only thing you need to do is launch the script and wait until it's done. Get the script, launch the script, done. Here's how.
metadescription: This unattended ArchLinux installation script can save you a lot of time. Get the script, launch the script, done.
author: TechKeep
authormainsociallink: https://twitter.com/TechKeepNet/
layout: post
category: post
date: 2022-04-25 12:39:15
categories: ['sidebar-posts', 'linux', 'linux-tips']
cattagText: Linux
cattag: linux
image: /img/post-headers/archlinux_logo_bg.png
photocredit: <!--<em>(Photo credit - <a href="#" target="_blank">Source Name</a>)</em>-->
twitterlink: https://twitter.com/TechKeepNet/status/1519167145942429697
redditlink: https://www.reddit.com/r/TechKeep/comments/ucskt6/how_to_install_archlinux_in_seconds/
---

{% include post-image.html %}

<p>Over time, I found myself having to install ArchLinux on various devices and Virtual Machines a lot for test purposes. Of course, I could've installed it once and then simply cloned it to new devices or VMs, but this was not always ideal. Sometimes, I needed fresh and up-to-date installs.</p>

<p>So, I recently re-made my personal install script and <a href="https://github.com/TechKeep/archun" target="_blank">made it available over on TechKeep's GitHub repository</a> and named it "ArchUn".</p>

<p>It only takes a few seconds to download and launch the script with its default settings. With it, performing a basic ArchLinux installation <b><em>takes about 1 minute</em></b> (depending on download speeds). Please note that the script doesn't install a Desktop Environment automatically yet, but it eventually will have an option for it. In the meantime, I have included an extra step at the bottom of the article to show you how to do it manually (and it's very simple). The whole process (initial installation <em>and</em> installing a Desktop Environment) takes under 5 minutes in total. <a href="https://www.youtube.com/watch?v=vbfKL4s_P-Y" target="_blank">Here's a demo I uploaded to YouTube; it only took under 4 minutes.</a></p>

<p><b>A fair warning, however: this script will format and use the whole destination drive (in other words, erase <em>everything</em>), so it's not meant to be used to add ArchLinux as a dual-boot option</b>. Of course, you can always install this first, and then install a dual-boot-friendly operating system afterwards.</p>

&nbsp;

<h4>Preparing for installation</h4>

<p>The first thing you need to do is to grab ArchLinux's latest <em>.iso</em> file from their <a href="https://archlinux.org/download/" target="_blank">download page</a>. Once you have that, prepare the installation media of your choice using tools such as <a href="https://www.balena.io/etcher/" target="_blank">etcher</a> or <a href="https://rufus.ie/en/" target="_blank">rufus</a> (<em>you do not need to use these tools if you are installing ArchLinux in a Virtual Machine; you only need the .iso file</em>) and boot up the machine with the installation media.</p>

<p>Once you have booted into the installation media and are presented with a command prompt, you can start the process below.</p>

&nbsp;

<h5>Step 1 - Getting the script</h5>

<p>Type in the following and press ENTER (yes, you also need to include the <code>https://</code>):<br>
<pre><code class="language-bash">curl https://raw.githubusercontent.com/TechKeep/archun/main/archun.sh -o archun.sh</code></pre></p>


<p>ArchUn is now downloaded. This script comes with pre-configured settings that you can change prior to launching it by using a text editor.</p>

<p><span style="font-size:18px;">/!\ <b><em>WARNING</em></b>: The default settings assume your installation drive is <code>/dev/sda</code> /!\</span>
<br>You can find out the name of the drive you want to use using the following command (the -l is a lowercase L): <code class="language-bash">fdisk -l</code></p>



<div style="padding-top:25px;padding-bottom:25px;text-align:center;">
	<img alt="Fdisk command output" src="/img/uploads/2022-04-25/how-to-install-archlinux-in-seconds/fdisk_-l_output.png" width="100%" height="100%" style="max-width:480px;"/>
	<br><span class="post-photo-credit"><em>The output of the fdisk command. I have highlighted what you want to know with a green rectangle.</em></span>
</div>

<ul>
	<li><b>If your drive's name is something other than <code>/dev/sda</code>, <em>OR</em> if you want to use your own settings, please follow the instructions in "<em><a href="#step1p2ConfiguringTheScript">Step 1.2 - Configuring the script</a></em>".</b></li>
	<li><b>If your drive's name IS <code>/dev/sda</code> <em>AND</em> you want to use the default settings, you can move directly to "<em><a href="#step2LaunchingArchUn">Step 2 - Launching ArchUn</a></em>".</b></li>
</ul>

&nbsp;

<h5 id="step1p2ConfiguringTheScript">Step 1.2 - Configuring the script</h5>

<p>As I mentioned above, you can change the settings by using a text editor. By default, the ArchLinux installer is bundled with <code>vim</code>, but you can easily install a different one (<em>and if you install a different one, it will <b>NOT</b> carry over to the installation. You are currently inside the bootable media's environment, which is temporary, so feel free to use whichever one you want. It will not bloat up the machine</em>). For this example, I will install and use <code>nano</code> to edit the file.</p>

<p>If you want to use <code>nano</code>, follow these steps. It's okay to use another text editor, but you will have to adjust your approach if you do so.</p>

<ol class="ol-li-separation">
	<li><b>Install <code>nano</code>:</b></li>
	<li style="list-style-type:none;">
		<pre><code class="language-bash">pacman -Sy nano</code></pre>
		<em>(Usually, we want to use <code>-Syu</code> at all times, but it's okay to use <code>-Sy</code> in this specific scenario, because we only want to download <code>nano</code> and it won't break even if we don't update everything else yet)</em>
	</li>
	<li value="2"><b>Use <code>nano</code> to open the script:</b></li>
	<li style="list-style-type:none;">
		<pre><code class="language-bash">nano archun.sh</code></pre>
	</li>
	<li value="3"><b>Move to a value within the <em>User-defined variables</em> section boundaries that you wish to change.</b></li>
	<li><b>Make sure to read the notes within the file to know exactly what everything does.</b><br>For this example, we will be changing the default LINUX SWAP value, named <code>SWAPPART</code>. The number is in MiB. The default value for this one is 4000, which is roughly 4GB of SWAP (around 4.19GB). If you want for example 8GB, you would replace this value with 8000, like so:
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
</ol>

&nbsp;

<h5 id="step2LaunchingArchUn">Step 2 - Launching ArchUn</h5>

<p>If everything looks okay and you understand that <b><em>this script will format and use the whole destination drive</em></b>, you are ready to proceed.</p>

<ol class="ol-li-separation">
	<li><b>Launch the script:</b></li>
	<li style="list-style-type:none;">
		<pre><code class="language-bash">bash archun.sh</code></pre>
	</li>
	<li value="2"><b>Press <em>1</em> and then <em>ENTER</em> to select the option named "Proceed".</b></li>
	<li><b>You will be presented with a few warnings about erasing the whole drive. Press <em>ENTER</em> a few times to accept and proceed.</b></li>
	<li><b>Once everything is over, you will be presented with a prompt to create a password.</b><br>This will be the password for the <code>root</code> account.</li>
	<li><b>The script will exit.</b></li>
</ol>

<p>The basic ArchLinux installation is now complete. You can now eject your installation media and reboot the machine and be met with GRUB2 (a boot manager), which will allow you to boot into your ArchLinux installation.</p>

<p>Of course, this script only installed the base operating system. You will boot in commandline mode. If you want a <em>Desktop Environment</em> and some basic apps, check out my recommendations in <b><em>Step 3 - Bells and Whistles</em></b>.</p>

<div style="padding-top:25px;padding-bottom:25px;text-align:center;">
	<img alt="Screenshot of Neofetch output in commandline" src="/img/uploads/2022-04-25/how-to-install-archlinux-in-seconds/neofetch-logged-in-as-root.png" width="100%" height="100%" style="max-width:618px;"/>
	<br><span class="post-photo-credit"><em><code>NEOFETCH</code> was used to display system information in commandline mode.</em></span>
</div>

&nbsp;

<h5>Step 3 - Bells and Whistles</h5>

<p>This section will be expanded on later, but here's my basic recommendations for the time being.</p>

<ol class="ol-li-separation">
	<li><b>Start by refreshing packages and updating everything:</b><br><em>(If there's an error, send the command again. It... should work.)</em></li>
	<li style="list-style-type:none;">
		<pre><code class="language-bash">pacman -Syu</code></pre>
	</li>
	<li value="2"><b>Use the following command to install a few things:</b>
	</li>
	<li style="list-style-type:none;">
		<pre><code class="language-none">pacman -Syu lxdm xfce4 xfce4-goodies pulseaudio pavucontrol sudo firefox neofetch</code></pre>
	</li>
	<li value="3"><b>In order to automatically launch the session manager (that you just installed) at boot, you will need to manually enable it with the following command:</b></li>
	<li style="list-style-type:none;">
		<pre><code class="language-none">systemctl enable lxdm</code></pre>
	</li>
	<li value="4"><b>Once all of this is done, simply reboot and you should be met with the session manager.</b></li>
	<li value="5"><b>Don't forget to select your Desktop Environment in the Session Manager of your choice before logging in.</b></li>
</ol>

<div style="padding-top:25px;padding-bottom:25px;text-align:center;">
	<img alt="Desktop Environment selection form" src="/img/uploads/2022-04-25/how-to-install-archlinux-in-seconds/select-xfce-session.png" width="100%" height="100%" style="max-width:305px;"/>
	<br><span class="post-photo-credit"><em>With <code>LXDM</code>, this is located in the bottom left corner.</em></span>
</div>

&nbsp;

<h5>Conclusion</h5>

<p>You now have a full Desktop Environment with ArchLinux. You can customize it however you want!</p>

<div style="padding-top:25px;padding-bottom:25px;text-align:center;">
	<img alt="Screenshot of XFCE4's Desktop Environment" src="/img/uploads/2022-04-25/how-to-install-archlinux-in-seconds/xfce4-desktop-environment.png" width="100%" height="100%" style="max-width:800px;"/>
	<br><span class="post-photo-credit"><em>Screenshot of the final result when using <code>XFCE</code> as a Desktop Environment with its default configuration.<code></code></em></span>
</div>

{% include comments-social.html %}