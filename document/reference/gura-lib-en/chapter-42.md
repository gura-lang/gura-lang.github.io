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
<p>
Below is an example that lists up files in the top directory of the device that is detected at first:
</p>
<pre class="highlight"><code>import(mtp)

devices = mtp.detect_devices()
device = devices[0]
println('Device: ', device.friendlyname)
storage = device.storages[0]
path.dir(storage.opendir('/')):stat {|stat|
    tm = stat.mtime
    if (stat.isdir) {
        printf('%04d/%02d/%02d %02d:%02d %12s  %s\n',
               tm.year, tm.month, tm.day, tm.hour, tm.min, '&lt;dir&gt;', stat.filename)
    } else {
        printf('%04d/%02d/%02d %02d:%02d %12d  %s\n',
               tm.year, tm.month, tm.day, tm.hour, tm.min, stat.size, stat.filename)
    }
}
</code></pre>
<h2><span class="caption-index-2">42.2</span><a name="anchor-42-2"></a>Module Function</h2>
<div class="mb-2"><code>mtp.detect_devices() {block?}</code></div>
<div class="mb-2 ml-4">
Detects MTP devices and returns a list of <code class="highlighter-rouge">mtp.device</code> instances.
</div>
<h2><span class="caption-index-2">42.3</span><a name="anchor-42-3"></a>mtp.device Class</h2>
<h3><span class="caption-index-3">42.3.1</span><a name="anchor-42-3-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">mtp.device</code> class provides information such as device's friendly name and manufacturer name. It also provides a list of <code class="highlighter-rouge">mtp.storage</code> instances through which you can transfer and manipulate files on the remote device.
</p>
<p>
You can call <code class="highlighter-rouge">mtp.detect_devices()</code> to get a list of <code class="highlighter-rouge">mtp.device</code> instances that are associated to connected devices.
</p>
<h3><span class="caption-index-3">42.3.2</span><a name="anchor-42-3-2"></a>Property</h3>
<p>
An <code class="highlighter-rouge">mtp.device</code> instance has the following properties:
</p>
<div class="mb-2"><code>mtp.device#friendlyname</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Friendly name.
</div>
<div class="mb-2"><code>mtp.device#manufacturer</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Manufacturer name.
</div>
<div class="mb-2"><code>mtp.device#storages</code> &hellip; <code>list</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns a list of <code class="highlighter-rouge">mtp.storage</code> instances.
</div>
<h2><span class="caption-index-2">42.4</span><a name="anchor-42-4"></a>mtp.storage Class</h2>
<h3><span class="caption-index-3">42.4.1</span><a name="anchor-42-4-1"></a>Overview</h3>
<p>
The class <code class="highlighter-rouge">mtp.storage</code> provices methods to transfer files from/to a device and to list and manipulate files on a device.
</p>
<h3><span class="caption-index-3">42.4.2</span><a name="anchor-42-4-2"></a>Property</h3>
<p>
An <code class="highlighter-rouge">mtp.storage</code> instance has following properties:
</p>
<div class="mb-2"><code>mtp.storage#access_capability</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
<p>
Indicates what access is permitted to the storage by following symbols:
</p>
<ul>
<li><code class="highlighter-rouge">`ReadWrite</code> .. Read/write capable.</li>
<li><code class="highlighter-rouge">`ReadOnly</code> .. Read-only.</li>
<li><code class="highlighter-rouge">`ReadOnlyWithObjectDeletion</code> .. Read-only but deleting operation is permitted.</li>
</ul>

</div>
<div class="mb-2"><code>mtp.storage#free_space_in_bytes</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the free space in the storage in bytes.
</div>
<div class="mb-2"><code>mtp.storage#free_space_in_objects</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the free space in the storage in number of objects.
</div>
<div class="mb-2"><code>mtp.storage#max_capacity</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the maximum capacity of the storage in bytes.
</div>
<div class="mb-2"><code>mtp.storage#storage_description</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the storage description.
</div>
<div class="mb-2"><code>mtp.storage#storage_type</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
<p>
Indicates the type of the storage by following symbols:
</p>
<ul>
<li><code class="highlighter-rouge">`Undefined</code> .. Undefined type.</li>
<li><code class="highlighter-rouge">`FixedROM</code> .. Non-removable and read-only.</li>
<li><code class="highlighter-rouge">`RemovableROM</code> .. Removable and read-only.</li>
<li><code class="highlighter-rouge">`FixedRAM</code> .. Non-removable and read/write capable.</li>
<li><code class="highlighter-rouge">`RemovableRAM</code> .. Removable and read/write capable.</li>
</ul>

</div>
<div class="mb-2"><code>mtp.storage#volume_identifier</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns the volume identifier.
</div>
<h3><span class="caption-index-3">42.4.3</span><a name="anchor-42-4-3"></a>Method</h3>
<p>
The <code class="highlighter-rouge">mtp.storage</code> class has following methods:
</p>
<div class="mb-2"><code>mtp.storage#opendir(pathname:string) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a <code class="highlighter-rouge">directory</code> instance that can be passed to functions that browse directories such as <code class="highlighter-rouge">path.dir()</code> and <code class="highlighter-rouge">path.walk()</code>. The argument <code class="highlighter-rouge">pathname</code> specifies the name of a directory on the device.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|directory:directory|</code>, where <code class="highlighter-rouge">directory</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<div class="mb-2"><code>mtp.storage#recvfile(pathname:string, stream:stream:w):reduce {block?}</code></div>
<div class="mb-2 ml-4">
Receives the content of a file on the device that is specified by the argument <code class="highlighter-rouge">pathname</code> and writes it to <code class="highlighter-rouge">stream</code>. If <code class="highlighter-rouge">block</code> is specified, it would be evaluated during the receiving process with a block parameter of <code class="highlighter-rouge">|recv:number, total:number|</code> where <code class="highlighter-rouge">recv</code> is a number of bytes that has been received and <code class="highlighter-rouge">total</code> is that of the total size. This functions returns the reference of the target.
</div>
<div class="mb-2"><code>mtp.storage#remove(pathname:string):reduce</code></div>
<div class="mb-2 ml-4">
Removes a file on the device that is specified by the argument <code class="highlighter-rouge">pathname</code>. This functions returns the reference of the target.
</div>
<div class="mb-2"><code>mtp.storage#sendfile(pathname:string, stream:stream:r):reduce {block?}</code></div>
<div class="mb-2 ml-4">
Reads data from <code class="highlighter-rouge">stream</code> and sends it to the device as a file that is specified by the argument <code class="highlighter-rouge">pathname</code>. If <code class="highlighter-rouge">block</code> is specified, it would be evaluated during the receiving process with a block parameter of <code class="highlighter-rouge">|sent:number, total:number|</code> where <code class="highlighter-rouge">sent</code> is a number of bytes that has been sent and <code class="highlighter-rouge">total</code> is that of the total size. This functions returns the reference of the target.
</div>
<h2><span class="caption-index-2">42.5</span><a name="anchor-42-5"></a>mtp.stat Class</h2>
<h3><span class="caption-index-3">42.5.1</span><a name="anchor-42-5-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">mtp.stat</code> class provides information about filename, timestamp and size of files on a portable device. An instance of <code class="highlighter-rouge">mtp.stat</code> is generated by calling <code class="highlighter-rouge">path.dir()</code> and <code class="highlighter-rouge">path.walk()</code> with a <code class="highlighter-rouge">directory</code> instance created by <code class="highlighter-rouge">mtp.storage#opendir()</code> for the argument and <code class="highlighter-rouge">:stat</code> attribute appended.
</p>
<h3><span class="caption-index-3">42.5.2</span><a name="anchor-42-5-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">mtp.stat</code> instance has following properties:
</p>
<div class="mb-2"><code>mtp.stat#dirname</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Directory name.
</div>
<div class="mb-2"><code>mtp.stat#filename</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Filename.
</div>
<div class="mb-2"><code>mtp.stat#isdir</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns <code class="highlighter-rouge">true</code> for a directory and <code class="highlighter-rouge">false</code> for a file.
</div>
<div class="mb-2"><code>mtp.stat#mtime</code> &hellip; <code>datetime</code> [read-only]</div>
<div class="mb-2 ml-4">
Returns a <code class="highlighter-rouge">datetime</code> instance indicating the modification time stamp.
</div>
<div class="mb-2"><code>mtp.stat#pathname</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Path name.
</div>
<div class="mb-2"><code>mtp.stat#size</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
File size in bytes.
</div>
<h2><span class="caption-index-2">42.6</span><a name="anchor-42-6"></a>Thanks</h2>
<p>
This module uses libusb and libmtp library which is distributed in the following site:
</p>
<ul>
<li><a href="https://libusb.info/">https://libusb.info/</a></li>
<li><a href="http://libmtp.sourceforge.net/">http://libmtp.sourceforge.net/</a></li>
</ul>
{% endraw %}
