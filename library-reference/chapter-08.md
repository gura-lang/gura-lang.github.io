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
<strong>base64.decode</strong>
</p>
<p>
<code>base64.decode(stream:stream:r) {block?}</code>
</p>
<p>
Reads text stream that is formatted in base64 and returns the decoded result in binary.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|data:binary|</code>, where <code>data</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>base64.encode</strong>
</p>
<p>
<code>base64.encode(stream:stream:r, linelen:number:nil =&gt; 76) {block?}</code>
</p>
<p>
Encodes content of the stream into base64 format and returns the result in binary.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|data:binary|</code>, where <code>data</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>base64.reader</strong>
</p>
<p>
<code>base64.reader(stream:stream:r) {block?}</code>
</p>
<p>
Creates a stream instance that reads data formatted in base64 from <code>stream</code>.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>base64.writer</strong>
</p>
<p>
<code>base64.writer(stream:stream:w, linelen:number:nil =&gt; 76) {block?}</code>
</p>
<p>
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
<strong>stream#reader@base64</strong>
</p>
<p>
<code>stream#reader@base64() {block?}</code>
</p>
<p>
Creates a stream instance that reads data formatted in base64 from the target stream instance.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|s:stream|</code>, where <code>s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<strong>stream#writer@base64</strong>
</p>
<p>
<code>stream#writer@base64(linelen:number:nil =&gt; 76) {block?}</code>
</p>
<p>
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
