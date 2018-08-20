---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-40.html#naviitem-selected
nextpage: chapter-42.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">41</span>msico Module</h1>
<h2><span class="caption-index-2">41.1</span><a name="anchor-41-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">msico</code> module provides measures to read/write image data in Microsoft Icon file format. To utilize it, import the <code class="highlighter-rouge">msico</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to read an ICO file:
</p>
<pre class="highlight"><code>import(msico)
img = image('foo.ico')
</code></pre>
<p>
This module has been implemented referring to the specification: <a href="http://msdn.microsoft.com/en-us/library/ms997538.aspx">http://msdn.microsoft.com/en-us/library/ms997538.aspx</a>.
</p>
<h2><span class="caption-index-2">41.2</span><a name="anchor-41-2"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code class="highlighter-rouge">image()</code> and instance method <code class="highlighter-rouge">image#write()</code> so that they can read/write ICO files.
</p>
<p>
When function <code class="highlighter-rouge">image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a ICO file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.ico</code>".</li>
</ul>
<p>
When instance method <code class="highlighter-rouge">image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in ICO format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.ico</code>".</li>
</ul>
<h2><span class="caption-index-2">41.3</span><a name="anchor-41-3"></a>msico.content Class</h2>
<h3><span class="caption-index-3">41.3.1</span><a name="anchor-41-3-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">msico.content</strong></div>
<div style="margin-bottom:1em"><code>msico.content(stream?:stream:r, format:symbol =&gt; `rgba) {block?}</code></div>

</p>
<h3><span class="caption-index-3">41.3.2</span><a name="anchor-41-3-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">msico.content#write</strong></div>
<div style="margin-bottom:1em"><code>msico.content#write(stream:stream:w):reduce</code></div>
Writes an ICO image to a stream.
</p>
<p>
<div><strong style="text-decoration:underline">msico.content#addimage</strong></div>
<div style="margin-bottom:1em"><code>msico.content#addimage(image:image):map:reduce</code></div>

</p>
<h2><span class="caption-index-2">41.4</span><a name="anchor-41-4"></a>Extension to image Class</h2>
<p>
This module extends the <code class="highlighter-rouge">image</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">image#read@msico</strong></div>
<div style="margin-bottom:1em"><code>image#read@msico(stream:stream:r, idx:number =&gt; 0):reduce</code></div>
Reads an ICO image from a stream.
</p>
{% endraw %}
