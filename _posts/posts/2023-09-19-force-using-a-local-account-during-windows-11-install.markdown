---
title: Force using a local account during Windows 11 install
subtitle: Here's how to easily bypass having to log in to a Microsoft Account while installing Windows 11 and use a local account instead, like we used to be able to do. This method works as of september 2023.
metadescription: For various reasons, we sometimes need to set up Windows with a local account. Microsoft really wants to push having to log in to an online account and keeps patching out known methods. Here's a method which still works as of september 2023.
author: TechKeep
authormainsociallink: https://twitter.com/TechKeepNet/
layout: post
category: post
date: 2023-09-19 15:51:09
categories: ['pinned', 'windows', 'windows-tips']
cattagText: Windows
cattag: windows
image: /img/post-headers/force-use-local-account-win11-install.png
photocredit: <em>(Photo credit - <a href="https://news.microsoft.com/june-24-2021/" target="_blank" rel="noreferrer noopener">Microsoft</a>)</em>
twitterlink: https://twitter.com/TechKeepNet/status/1704240910165303307
redditlink: https://www.reddit.com/r/TechKeep/comments/16n2g54/force_using_a_local_account_during_windows_11/
---

{% include post-image.html %}

<p>For various reasons, we sometimes need to set up Windows with a local account. Microsoft really wants to push having to log in to an online account and keeps patching out known methods. Here's a method which still works as of september 2023.</p>

&nbsp;

<h4>Installing Windows 11 with a local account</h4>

<p>When you reach the step where it prompts you to log in to (or create) an online account, here's what you need to do. I will use <em>TechKeep</em> as the username; replace it with yours.</p>
 

<ol class="ol-li-separation">
	<li>Press <em>SHIFT+F10</em>. This will open a command prompt.</li>
	<li>Type the following:</li>
	<li style="list-style-type:none;"><pre><code class="language-powershell">net.exe user "TechKeep" /add</code></pre></li>
	<li value="3">Press <em>ENTER</em>, and type the following (<em>note that the group is language-sensitive. For example, in French, it's "Administrateurs"</em>):</li>
	<li style="list-style-type:none;"><pre><code class="language-powershell">net.exe localgroup "Administrators" "TechKeep" /add</code></pre></li>
	<li value="4">Press <em>ENTER</em> again, then type this:</li>
	<li style="list-style-type:none;"><pre><code class="language-powershell">cd OOBE</code></pre></li>
	<li value="5">Press <em>ENTER</em> once more, then finish up by typing the following:</li>
	<li style="list-style-type:none;"><pre><code class="language-powershell">msoobe.exe && shutdown.exe -r</code></pre></li>
	<li value="6">Press <em>ENTER</em> one last time.</li>
	<li>The system will now reboot. Once restarted, you will get a dialog prompt stating that the entered password is invalid. Press "Ok".</li>
	<li>You may now select your newly-created local user on the bottom-left corner of the login page and log in as normal. Note that we didn't set a password in the previous steps, so simply log in with a blank password field.</li>
	<li>Using this workaround will leave the "defaultuser0" account active. Navigate to the User Accounts section of the Control Panel and delete it along with all its files.</li>
	<li>While in the User Accounts settings, feel free to set a password to your local account.</li>
</ol>

&nbsp;

<p>There we go. We now have created a local user account.</p>

<p style="font-style:italic;text-align:right;" class="last-edited-date">Last edited on September 19 2023</p>

{% include comments-social.html %}