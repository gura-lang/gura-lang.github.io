---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-53.html#naviitem-selected
nextpage: chapter-55.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">54</span>tiff Module</h1>
<h2><span class="caption-index-2">54.1</span><a name="anchor-54-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">tiff</code> module provides measures to read/write image data in TIFF format. To utilize it, import the <code class="highlighter-rouge">tiff</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to read a TIFF file:
</p>
<pre class="highlight"><code>import(tiff)
img = image('foo.tiff')
</code></pre>
<h2><span class="caption-index-2">54.2</span><a name="anchor-54-2"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code class="highlighter-rouge">image()</code> and instance method <code class="highlighter-rouge">image#write()</code> so that they can read/write TIFF files.
</p>
<p>
When function <code class="highlighter-rouge">image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a TIFF file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.tif</code>" or "<code class="highlighter-rouge">.tiff</code>".</li>
</ul>
<p>
When instance method <code class="highlighter-rouge">image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in TIFF format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.tif</code>" or "<code class="highlighter-rouge">.tiff</code>".</li>
</ul>
<h2><span class="caption-index-2">54.3</span><a name="anchor-54-3"></a>Extension to image Class</h2>
<p>
This module extends the <code class="highlighter-rouge">image</code> class with methods described here.
</p>
<div class="mb-2"><code>image#read@tiff(stream:stream:r):reduce</code></div>
<div class="mb-2 ml-4">
Reads a TIFF image from a stream.
</div>
<h2><span class="caption-index-2">54.4</span><a name="anchor-54-4"></a>Thanks</h2>
<p>
This module uses libtiff which is distributed in the following site:
</p>
<p>
<a href="http://www.libtiff.org/">http://www.libtiff.org/</a>
</p>
{% endraw %}
