---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">33</span><a name="anchor-33"></a>ppm Module</h1>
<p>
The <code>ppm</code> module provides measures to read/write image data in PPM format. To utilize it, import the <code>ppm</code> module using <code>import</code> function.
</p>
<p>
Below is an example to read a PPM file:
</p>
<pre><code>import(ppm)
img = image('foo.ppm')
</code></pre>
<h2><span class="caption-index-2">33.1</span><a name="anchor-33-1"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code>image()</code> and instance method <code>image#write()</code> so that they can read/write PPM files.
</p>
<p>
When function <code>image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a PPM file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.ppm</code>" or "<code>.pbm</code>".</li>
<li>The stream data begins with a byte sequence "<code>P2</code>", "<code>P3</code>" or "<code>P6</code>".</li>
</ul>
<p>
When instance method <code>image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in PPM format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.ppm</code>" or "<code>.pbm</code>".</li>
</ul>
<h2><span class="caption-index-2">33.2</span><a name="anchor-33-2"></a>Extension to image Class</h2>
<p>
This module extends the <code>image</code> class with methods described here.
</p>
<p>
<strong>image#read@ppm</strong>
</p>
<p>
<code>image#read@ppm(stream:stream:r):reduce</code>
</p>
<p>
Reads a PPM/PGM image from a stream.
</p>
<p>
<strong>image#write@ppm</strong>
</p>
<p>
<code>image#write@ppm(stream:stream:w):reduce:[gray]</code>
</p>
<p>
Writes a PPM/PGM image to a stream.
</p>
<p />

{% endraw %}