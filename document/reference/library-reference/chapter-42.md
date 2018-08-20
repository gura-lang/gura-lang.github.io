---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-41.html#naviitem-selected
nextpage: chapter-43.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">42</span>mtp Module</h1>
<h2><span class="caption-index-2">42.1</span><a name="anchor-42-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">mtp</code> module provides measures to read/write data on a mobile platform like an Android device.
</p>
<h2><span class="caption-index-2">42.2</span><a name="anchor-42-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">mtp.detect_devices</strong></div>
<div style="margin-bottom:1em"><code>mtp.detect_devices() {block?}</code></div>
Detects MTP devices and returns a list of <code class="highlighter-rouge">mtp.device</code> instances.
</p>
<h2><span class="caption-index-2">42.3</span><a name="anchor-42-3"></a>mtp.device Class</h2>
<h3><span class="caption-index-3">42.3.1</span><a name="anchor-42-3-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">mtp.device</code> instance has the following properties:
</p>
<p>
<table class="table">
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>friendlyname</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Friendly name.</td>
</tr>

<tr>
<td>
<code>manufacturer</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Manufacturer name.</td>
</tr>

<tr>
<td>
<code>storages</code></td>
<td>
<code>list</code></td>
<td>
R</td>

<td>
Returns a list of <code class="highlighter-rouge">mtp.storage</code> instances.</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">42.4</span><a name="anchor-42-4"></a>mtp.storage Class</h2>
<h3><span class="caption-index-3">42.4.1</span><a name="anchor-42-4-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">mtp.storage</code> instance has the following properties:
</p>
<p>
<table class="table">
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>access_capability</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
Returns one of the symbols: <code class="highlighter-rouge">`ReadWrite</code>, <code class="highlighter-rouge">`ReadOnly</code>, <code class="highlighter-rouge">`ReadOnlyWithObjectDeletion</code></td>
</tr>

<tr>
<td>
<code>filesystem_type</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
Returns one of the syhmbols: <code class="highlighter-rouge">`Undefined</code>, <code class="highlighter-rouge">`GenericFlat</code>, <code class="highlighter-rouge">`GenericHierarchical</code>, <code class="highlighter-rouge">`DCF</code></td>
</tr>

<tr>
<td>
<code>free_space_in_bytes</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Free space in the storage in bytes.</td>
</tr>

<tr>
<td>
<code>free_space_in_objects</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Free space in the storage in number of objects.</td>
</tr>

<tr>
<td>
<code>max_capacity</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
Maximum capacity of the storage in bytes.</td>
</tr>

<tr>
<td>
<code>storage_description</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Storage description.</td>
</tr>

<tr>
<td>
<code>storage_type</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
Returns one of the symbols: <code class="highlighter-rouge">`Undefined</code>, <code class="highlighter-rouge">`FixedROM</code>, <code class="highlighter-rouge">`RemovableROM</code>, <code class="highlighter-rouge">`FixedRAM</code>, <code class="highlighter-rouge">`RemovableRAM</code></td>
</tr>

<tr>
<td>
<code>volume_identifier</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Volume identifier.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">42.4.2</span><a name="anchor-42-4-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">mtp.storage#opendir</strong></div>
<div style="margin-bottom:1em"><code>mtp.storage#opendir(pathname:string) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">mtp.storage#recvfile</strong></div>
<div style="margin-bottom:1em"><code>mtp.storage#recvfile(pathname:string, stream:stream:w):reduce {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">mtp.storage#remove</strong></div>
<div style="margin-bottom:1em"><code>mtp.storage#remove(pathname:string):reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">mtp.storage#sendfile</strong></div>
<div style="margin-bottom:1em"><code>mtp.storage#sendfile(pathname:string, stream:stream:r):reduce {block?}</code></div>

</p>
<h2><span class="caption-index-2">42.5</span><a name="anchor-42-5"></a>mtp.stat Class</h2>
<h3><span class="caption-index-3">42.5.1</span><a name="anchor-42-5-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">mtp.stat</code> instance has the following properties:
</p>
<p>
<table class="table">
<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Note</th>
</tr>


<tr>
<td>
<code>dirname</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Directory name.</td>
</tr>

<tr>
<td>
<code>filename</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Filename.</td>
</tr>

<tr>
<td>
<code>isdir</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
Returns <code class="highlighter-rouge">true</code> for a directory and <code class="highlighter-rouge">false</code> for a file.</td>
</tr>

<tr>
<td>
<code>mtime</code></td>
<td>
<code>datetime</code></td>
<td>
R</td>

<td>
Returns a <code class="highlighter-rouge">datetime</code> instance indicating the modification time stamp.</td>
</tr>

<tr>
<td>
<code>pathname</code></td>
<td>
<code>string</code></td>
<td>
R</td>

<td>
Path name.</td>
</tr>

<tr>
<td>
<code>size</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
File size in bytes.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">42.5.2</span><a name="anchor-42-5-2"></a>Method</h3>
<h2><span class="caption-index-2">42.6</span><a name="anchor-42-6"></a>Thanks</h2>
<p>
This module uses libusb and libmtp library which is distributed in the following site:
</p>
<ul>
<li><a href="https://libusb.info/">https://libusb.info/</a></li>
<li><a href="http://libmtp.sourceforge.net/">http://libmtp.sourceforge.net/</a></li>
</ul>
{% endraw %}
