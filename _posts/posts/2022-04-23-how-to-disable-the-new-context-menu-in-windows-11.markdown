---
title: Disable the new context menu in Windows 11
subtitle: Here's how to easily disable or re-enable the new Windows 11 context menu, also known as the "right-click" menu.
metadescription: For some people, it's way more convenient to not have an extra layer to click through in order to quickly access something within the context menu. Fortunately, it's possible to revert it, at least for now. Here's how.
author: TechKeep
authormainsociallink: https://twitter.com/TechKeepNet/
layout: post
category: post
date: 2022-04-23 23:39:05
categories: ['sidebar-posts', 'windows', 'windows-tips']
cattagText: Windows
cattag: windows
image: /img/post-headers/windows11_logo_bg.jpg
photocredit: <em>(Photo credit - <a href="https://news.microsoft.com/june-24-2021/" target="_blank" rel="noopener">Microsoft</a>)</em>
twitterlink: https://twitter.com/TechKeepNet/status/1519166970054287360
redditlink: https://www.reddit.com/r/TechKeep/comments/ucskgs/disable_the_new_context_menu_in_windows_11/
---

{% include post-image.html %}

<p>For some people, it's way more convenient to not have an extra layer to click through in order to quickly access something within the context menu. Fortunately, it's possible to revert it, at least for now. Here's how.</p>

&nbsp;

<h4>Disable the new context menu</h4>

<p>This is a pretty straightforward process.</p>

<ol>
	<li>Open up the "Run" dialog using <em>Win+R</em> (pressing the Windows key and the R key at the same time)</li>
	<li>Copy and paste the following into the text field:</li>
	<li style="list-style-type:none;"><pre><code class="language-powershell">reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve</code></pre></li>
	<li value="3">Confirm the dialog (or press Enter)</li>
	<li>Either reboot your computer, or restart "explorer.exe" using the task manager.</li>
</ol>

&nbsp;

<h4>Re-enable the new context menu</h4>

<p>If you previously have disabled the new context menu and wish to re-enable it, the process is just as easy.</p>

<ol>
	<li>Open up the "Run" dialog using <em>Win+R</em> (pressing the Windows key and the R key at the same time)</li>
	<li>Copy and paste the following into the text field:</li>
	<li style="list-style-type:none;"><pre><code class="language-powershell">reg.exe delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f</code></pre></li>
	<li value="3">Confirm the dialog (or press Enter)</li>
	<li>Either reboot your computer, or restart "explorer.exe" using the task manager.</li>
</ol>

{% include comments-social.html %}