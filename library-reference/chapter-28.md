---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">28</span><a name="anchor-28"></a>msico Module</h1>
<p>
The <code>msico</code> module provides measures to read/write image data in Microsoft Icon file format. To utilize it, import the <code>msico</code> module using <code>import</code> function.
</p>
<p>
Below is an example to read an ICO file:
</p>
<pre><code>import(msico)
img = image('foo.ico')
</code></pre>
<h2><span class="caption-index-2">28.1</span><a name="anchor-28-1"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code>image()</code> and instance method <code>image#write()</code> so that they can read/write ICO files.
</p>
<p>
When function <code>image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a ICO file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.ico</code>".</li>
</ul>
<p>
When instance method <code>image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in ICO format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.ico</code>".</li>
</ul>
<h2><span class="caption-index-2">28.2</span><a name="anchor-28-2"></a>msico.content Class</h2>
<h3><span class="caption-index-3">28.2.1</span><a name="anchor-28-2-1"></a>Function to Create Instance</h3>
<p>
<strong>msico.content</strong>
</p>
<p>
<code>msico.content(stream?:stream:r, format:symbol =&gt; `rgba) {block?}</code>
</p>
<h3><span class="caption-index-3">28.2.2</span><a name="anchor-28-2-2"></a>Method</h3>
<p>
<strong>msico.content#write</strong>
</p>
<p>
<code>msico.content#write(stream:stream:w):reduce</code>
</p>
<p>
Writes an ICO image to a stream.
</p>
<p>
<strong>msico.content#addimage</strong>
</p>
<p>
<code>msico.content#addimage(image:image):map:reduce</code>
</p>
<h2><span class="caption-index-2">28.3</span><a name="anchor-28-3"></a>Extension to image Class</h2>
<p>
This module extends the <code>image</code> class with methods described here.
</p>
<p>
<strong>image#read@msico</strong>
</p>
<p>
<code>image#read@msico(stream:stream:r, idx:number =&gt; 0):reduce</code>
</p>
<p>
Reads an ICO image from a stream.
</p>
<p />

{% endraw %}
