---
title: How to fix Windows 10 to Windows 11 upgrade stuck at 99%
subtitle: The Windows 10 to Windows 11 upgrade tool can get stuck at 99% and will remain there forever. Sometimes, even rebooting and restarting the process altogether won't work.
metadescription: You seemingly tried everything and it just won't work? You're in luck! This is a very simple method to force the upgrade beyond 99% and actually go through with the upgrade.
author: TechKeep
authormainsociallink: https://twitter.com/TechKeepNet/
layout: post
category: post
date: 2023-09-19 12:35:49
categories: ['pinned', 'windows', 'windows-tips']
cattagText: Windows
cattag: windows
image: /img/post-headers/win10_to_win11_upgrade_stuck_at_99_percent.png
photocredit: <!-- <em>(Photo credit - <a href="#" target="_blank" rel="noreferrer noopener">TechKeep</a>)</em> -->
twitterlink: https://twitter.com/TechKeepNet/
redditlink: https://www.reddit.com/r/TechKeep/
---

{% include post-image.html %}

<p>You seemingly tried everything and it just won't work? You're in luck! This is a very simple method to force the upgrade beyond 99% and actually go through with the upgrade.</p>

&nbsp;

<h4>Fix the Windows 10 to Windows 11 upgrade tool from being stuck at 99%</h4>

<p>Obviously, the first step to do is to wait. However, sometimes, it's been hours and it just won't budge from 99%. If that's the case, here's what you need to do.</p>
 

<ol class="ol-li-separation">
	<li>Navigate to <code>C:\$GetCurrent</code> by opening up a run window (<em>Win+R</em>).</li>
	<li>Copy the <code>media</code> folder to your desktop (or somewhere else if you don't have enough available space, like a USB drive).</li>
	<li>Reboot your computer.</li>
	<li>Once rebooted, navigate to <code>C:\$GetCurrent</code> once more.</li>
	<li>Delete the <code>media</code> folder from there.</li>
	<li>Copy and paste your previous copy of the <code>media</code> folder you have on your desktop (or previous location from step 2) in the <code>C:\$GetCurrent</code> folder.</li>
	<li>Navigate to <code>C:\$GetCurrent\media</code> - you should see a bunch of files.</li>
	<li>Launch <code>setup.exe</code> directly from there and proceed with the installation.</li>
</ol>

&nbsp;

<p>All done!</p>

<p style="font-style:italic;text-align:right;" class="last-edited-date">Last edited on September 19 2023</p>

{% include comments-social.html %}