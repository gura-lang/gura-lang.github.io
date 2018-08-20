---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-46.html#naviitem-selected
nextpage: chapter-48.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">47</span>ppm Module</h1>
<h2><span class="caption-index-2">47.1</span><a name="anchor-47-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">ppm</code> module provides measures to read/write image data in PPM format. To utilize it, import the <code class="highlighter-rouge">ppm</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to read a PPM file:
</p>
<pre class="highlight"><code>import(ppm)
img = image('foo.ppm')
</code></pre>
<h2><span class="caption-index-2">47.2</span><a name="anchor-47-2"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code class="highlighter-rouge">image()</code> and instance method <code class="highlighter-rouge">image#write()</code> so that they can read/write PPM files.
</p>
<p>
When function <code class="highlighter-rouge">image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a PPM file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.ppm</code>" or "<code class="highlighter-rouge">.pbm</code>".</li>
<li>The stream data begins with a byte sequence "<code class="highlighter-rouge">P2</code>", "<code class="highlighter-rouge">P3</code>" or "<code class="highlighter-rouge">P6</code>".</li>
</ul>
<p>
When instance method <code class="highlighter-rouge">image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in PPM format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.ppm</code>" or "<code class="highlighter-rouge">.pbm</code>".</li>
</ul>
<h2><span class="caption-index-2">47.3</span><a name="anchor-47-3"></a>Extension to image Class</h2>
<p>
This module extends the <code class="highlighter-rouge">image</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">image#read@ppm</strong></div>
<div style="margin-bottom:1em"><code>image#read@ppm(stream:stream:r):reduce</code></div>
Reads a PPM/PGM image from a stream.
</p>
<p>
<div><strong style="text-decoration:underline">image#write@ppm</strong></div>
<div style="margin-bottom:1em"><code>image#write@ppm(stream:stream:w):reduce:[gray]</code></div>
Writes a PPM/PGM image to a stream.
</p>
{% endraw %}
