---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-06.html#naviitem-selected
nextpage: chapter-08.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">7</span>base64 Module</h1>
<h2><span class="caption-index-2">7.1</span><a name="anchor-7-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">base64</code> module provides measures to decode/encode data formatted in base64 format.
</p>
<p>
To decode a stream that is formatted in base64, use one of the following functions:
</p>
<ul>
<li><code class="highlighter-rouge">base64.decode()</code> .. Reads base64 sequence from the given stream and returns a decoded data as <code class="highlighter-rouge">binary</code>. This is convenient when the data size is expected to be small.</li>
<li><code class="highlighter-rouge">base64.reader()</code> .. Creates a stream that decodes base64 sequence from the given stream. <code class="highlighter-rouge">stream#reader@base64()</code> method is another form of this function. You should use this way if the data size is expected to be large.</li>
</ul>
<p>
To encode a data into base64 format, use one of the following functions:
</p>
<ul>
<li><code class="highlighter-rouge">base64.encode()</code> .. Encodes the stream from the given stream and returns a encoded data as <code class="highlighter-rouge">binary</code>. This is convenient when the data size is expected to be small.</li>
<li><code class="highlighter-rouge">base64.writer()</code> .. Creates a stream that encodes data from <code class="highlighter-rouge">write()</code> method into the given stream. <code class="highlighter-rouge">stream#writer@base64()</code> method is another form of this function. You should use this way if the data size is expected to be large.</li>
</ul>
<h2><span class="caption-index-2">7.2</span><a name="anchor-7-2"></a>Module Function</h2>
<p>
<div class="h5">base64.decode</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>base64.decode(stream:stream:r) {block?}</code></div>
Reads text stream that is formatted in base64 and returns the decoded result in binary.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|data:binary|</code>, where <code class="highlighter-rouge">data</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div class="h5">base64.encode</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>base64.encode(stream:stream:r, linelen:number:nil =&gt; 76) {block?}</code></div>
Encodes content of the stream into base64 format and returns the result in binary.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|data:binary|</code>, where <code class="highlighter-rouge">data</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div class="h5">base64.reader</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>base64.reader(stream:stream:r) {block?}</code></div>
Creates a stream instance that reads data formatted in base64 from <code class="highlighter-rouge">stream</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|s:stream|</code>, where <code class="highlighter-rouge">s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div class="h5">base64.writer</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>base64.writer(stream:stream:w, linelen:number:nil =&gt; 76) {block?}</code></div>
Creates a stream instance that encodes data to base64 format and writes it to the <code class="highlighter-rouge">stream</code>.
</p>
<p>
The number of characters per line is specified by an argument <code class="highlighter-rouge">linelen</code>. If omitted, that is 76.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|s:stream|</code>, where <code class="highlighter-rouge">s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h2><span class="caption-index-2">7.3</span><a name="anchor-7-3"></a>Extension to stream Class</h2>
<p>
This module extends the <code class="highlighter-rouge">stream</code> class with methods described here.
</p>
<p>
<div class="h5">stream#reader@base64</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>stream#reader@base64() {block?}</code></div>
Creates a stream instance that reads data formatted in base64 from the target stream instance.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|s:stream|</code>, where <code class="highlighter-rouge">s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<p>
<div class="h5">stream#writer@base64</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>stream#writer@base64(linelen:number:nil =&gt; 76) {block?}</code></div>
Creates a stream instance that encodes data to base64 format and writes it to the target stream instance.
</p>
<p>
The number of characters per line is specified by an argument <code class="highlighter-rouge">linelen</code>. If omitted, that is 76.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|s:stream|</code>, where <code class="highlighter-rouge">s</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
{% endraw %}
