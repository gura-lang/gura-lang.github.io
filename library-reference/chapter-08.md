---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">8</span><a name="anchor-8"></a>base64 Module</h1>
<p>
The <code>base64</code> module provides measures to read/write text stream that is formatted in base64 format.
</p>
<h2><span class="caption-index-2">8.1</span><a name="anchor-8-1"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">base64.decode</strong></div>
<div style="margin-bottom:1em"><code>base64.decode(stream:stream:r) {block?}</code></div>
Reads text stream that is formatted in base64 and returns the decoded result in binary.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|data:binary|</code>, where <code>data</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">base64.encode</strong></div>
<div style="margin-bottom:1em"><code>base64.encode(stream:stream:r, linelen:number:nil =&gt; 76) {block?}</code></div>
Encodes content of the stream into base64 format and returns the result in binary.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|data:binary|</code>, where <code>data</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">base64.reader</strong></div>
<div style="margin-bottom:1em"><code>base64.reader(stream:stream:r) {block?}</code></div>
Creates a stream instance that reads data formatted in base64 from <code>stream</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">base64.writer</strong></div>
<div style="margin-bottom:1em"><code>base64.writer(stream:stream:w, linelen:number:nil =&gt; 76) {block?}</code></div>
Creates a stream instance that encodes data to base64 format and writes it to the <code>stream</code>.
</p>
<p>
The number of characters per line is specified by an argument <code>linelen</code>. If omitted, that is 76.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">8.2</span><a name="anchor-8-2"></a>Extension to stream Class</h2>
<p>
This module extends the <code>stream</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">stream#reader@base64</strong></div>
<div style="margin-bottom:1em"><code>stream#reader@base64() {block?}</code></div>
Creates a stream instance that reads data formatted in base64 from the target stream instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div><strong style="text-decoration:underline">stream#writer@base64</strong></div>
<div style="margin-bottom:1em"><code>stream#writer@base64(linelen:number:nil =&gt; 76) {block?}</code></div>
Creates a stream instance that encodes data to base64 format and writes it to the target stream instance.
</p>
<p>
The number of characters per line is specified by an argument <code>linelen</code>. If omitted, that is 76.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p />

{% endraw %}
