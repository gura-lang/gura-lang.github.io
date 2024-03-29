---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-29.html#naviitem-selected
nextpage: chapter-31.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">30</span>jpeg Module</h1>
<h2><span class="caption-index-2">30.1</span><a name="anchor-30-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">jpeg</code> module provides measures to read/write image data in JPEG format. To utilize it, import the <code class="highlighter-rouge">jpeg</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to read a JPEG file:
</p>
<pre class="highlight"><code>import(jpeg)
img = image('foo.jpeg')
</code></pre>
<h2><span class="caption-index-2">30.2</span><a name="anchor-30-2"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code class="highlighter-rouge">image()</code> and instance method <code class="highlighter-rouge">image#write()</code> so that they can read/write JPEG files.
</p>
<p>
When function <code class="highlighter-rouge">image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a JPEG file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.jpeg</code>", "<code class="highlighter-rouge">.jpg</code>" or "<code class="highlighter-rouge">.jpe</code>".</li>
<li>The stream data begins with a byte sequence "<code class="highlighter-rouge">\xff\xd8</code>" that means SOI (start of Image) marker in JPEG specification.</li>
</ul>
<p>
When instance method <code class="highlighter-rouge">image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in JPEG format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.jpeg</code>", "<code class="highlighter-rouge">.jpg</code>" or "<code class="highlighter-rouge">.jpe</code>".</li>
</ul>
<h2><span class="caption-index-2">30.3</span><a name="anchor-30-3"></a>jpeg.exif Class</h2>
<h3><span class="caption-index-3">30.3.1</span><a name="anchor-30-3-1"></a>Overview</h3>
<p>
The <code class="highlighter-rouge">jpeg.exif</code> class provides EXIF information in a JPEG stream.
</p>
<p>
A <code class="highlighter-rouge">jpeg.exif</code> instance contains <code class="highlighter-rouge">jpeg.ifd</code> instances as properties named <code class="highlighter-rouge">jpeg.exif#ifd0</code> and <code class="highlighter-rouge">jpeg.exif#ifd1</code> that include a list of <code class="highlighter-rouge">jpeg.tag</code> instances.
</p>
<pre class="highlight"><code>+-----------+             +----------+        +----------+
| jpeg.exif |ifd0, ifd1   | jpeg.ifd |1..     | jpeg.tag |
|-----------*-------------+----------*--------+----------|
|           |             |          |        |          |
+-----------+             +----------+        +----------+
</code></pre>
<h3><span class="caption-index-3">30.3.2</span><a name="anchor-30-3-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">jpeg.exif</code> instance has the following properties:
</p>
<div class="mb-2"><code>jpeg.exif#endian</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">
The endian type: <code class="highlighter-rouge">`big</code> for big-endian and <code class="highlighter-rouge">`little</code> for little-endian.
</div>
<div class="mb-2"><code>jpeg.exif#ifd0</code> &hellip; <code>jpeg.ifd</code> [read-only]</div>
<div class="mb-2 ml-4">
IFD0 instance.
</div>
<div class="mb-2"><code>jpeg.exif#ifd1</code> &hellip; <code>jpeg.ifd</code> [read-only]</div>
<div class="mb-2 ml-4">
IFD1 instance.
</div>
<div class="mb-2"><code>jpeg.exif#thumbnail</code> &hellip; <code>image</code> [read-only]</div>
<div class="mb-2 ml-4">
Thumbnail image as <code class="highlighter-rouge">image</code> value.
</div>
<div class="mb-2"><code>jpeg.exif#thumbnail@jpeg</code> &hellip; <code>binary</code> [read-only]</div>
<div class="mb-2 ml-4">
Thumbnail image as JPEG binary data.
</div>
<h3><span class="caption-index-3">30.3.3</span><a name="anchor-30-3-3"></a>Constructor</h3>
<div class="mb-2"><code>jpeg.exif(stream?:stream:r):map:[raise] {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Reads EXIF data from <code class="highlighter-rouge">stream</code> and creates a <code class="highlighter-rouge">jpeg.exif</code> instance.
</p>
<p>
If no EXIF information exists in the stream, this function returns <code class="highlighter-rouge">nil</code>. If the attribute <code class="highlighter-rouge">:raise</code> is specified, an error occurs for that case.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would be evaluated with a block parameter <code class="highlighter-rouge">|exif:jpeg.exif|</code>, where <code class="highlighter-rouge">exif</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>

</div>
<h3><span class="caption-index-3">30.3.4</span><a name="anchor-30-3-4"></a>Method</h3>
<div class="mb-2"><code>jpeg.exif#each() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that returns <code class="highlighter-rouge">jpeg.tag</code> values as elements that are stored in the property <code class="highlighter-rouge">jpeg.exif#ifd0</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<h2><span class="caption-index-2">30.4</span><a name="anchor-30-4"></a>jpeg.ifd Class</h2>
<h3><span class="caption-index-3">30.4.1</span><a name="anchor-30-4-1"></a>Overview</h3>
<h3><span class="caption-index-3">30.4.2</span><a name="anchor-30-4-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">jpeg.ifd</code> instance has the following properties:
</p>
<div class="mb-2"><code>jpeg.ifd#name</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>jpeg.ifd#symbol</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h3><span class="caption-index-3">30.4.3</span><a name="anchor-30-4-3"></a>Method</h3>
<div class="mb-2"><code>jpeg.ifd#each() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates an iterator that returns <code class="highlighter-rouge">jpeg.tag</code> values as elements that are stored in the target <code class="highlighter-rouge">jpeg.ifd</code> instance.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code class="highlighter-rouge">:iter</code> .. An iterator. This is the default behavior.</li>
<li><code class="highlighter-rouge">:xiter</code> .. An iterator that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:list</code> .. A list.</li>
<li><code class="highlighter-rouge">:xlist</code> .. A list that eliminates <code class="highlighter-rouge">nil</code> from its elements.</li>
<li><code class="highlighter-rouge">:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code class="highlighter-rouge">:xset</code> .. A list that eliminates duplicated values and <code class="highlighter-rouge">nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code class="highlighter-rouge">|value, idx:number|</code> where <code class="highlighter-rouge">value</code> is the iterated value and <code class="highlighter-rouge">idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>

</div>
<h2><span class="caption-index-2">30.5</span><a name="anchor-30-5"></a>jpeg.tag Class</h2>
<h3><span class="caption-index-3">30.5.1</span><a name="anchor-30-5-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">jpeg.tag</code> instance has the following properties:
</p>
<div class="mb-2"><code>jpeg.tag#id</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Tag ID.
</div>
<div class="mb-2"><code>jpeg.tag#ifd</code> &hellip; <code>undefined</code> [read-only]</div>
<div class="mb-2 ml-4">
IFD instance. Valid only for tags <code class="highlighter-rouge">Exif</code>, <code class="highlighter-rouge">GPSInfo</code> and <code class="highlighter-rouge">Interoperability</code>.
</div>
<div class="mb-2"><code>jpeg.tag#name</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Tag name.
</div>
<div class="mb-2"><code>jpeg.tag#symbol</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">
Tag name as <code class="highlighter-rouge">symbol</code>.
</div>
<div class="mb-2"><code>jpeg.tag#type</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">
Tag type.
</div>
<div class="mb-2"><code>jpeg.tag#typename</code> &hellip; <code>string</code> [read-only]</div>
<div class="mb-2 ml-4">
Tag type name.
</div>
<div class="mb-2"><code>jpeg.tag#value</code> &hellip; <code>any</code> [read-only]</div>
<div class="mb-2 ml-4">
Tag value. When the attribute <code class="highlighter-rouge">:cooked</code> is specified, numbers in some tags are translated to human-readable symbols.
</div>
<h2><span class="caption-index-2">30.6</span><a name="anchor-30-6"></a>Extension to image Class</h2>
<p>
This module extends the <code class="highlighter-rouge">image</code> class with methods described here.
</p>
<div class="mb-2"><code>image#read@jpeg(stream:stream:r, size?:number):reduce:[fast,rough]</code></div>
<div class="mb-2 ml-4">
<p>
Reads a JPEG image data from the specified <code class="highlighter-rouge">stream</code>.
</p>
<p>
When the argument <code class="highlighter-rouge">size</code> is specified, the image would be shrinked so that it is boxed within the size.
</p>
<p>
The attribute <code class="highlighter-rouge">:fast</code> indicates a fast but less-qualified decompression process.
</p>
<p>
The attriubte <code class="highlighter-rouge">:rough</code> is only valid when <code class="highlighter-rouge">size</code> is specified and makes the shrinked image with nearest neighbor method. Othereise, shrinking shall be done with bilinear method.
</p>

</div>
<div class="mb-2"><code>image#write@jpeg(stream:stream:w, quality:number =&gt; 75):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Writes a JPEG image data to the specified <code class="highlighter-rouge">stream</code>.
</p>
<p>
The argument <code class="highlighter-rouge">quality</code> takes a number between 0 and 100 with which a a higher number results in a higher quality of result but a less compression performance. The default value for it is 75.
</p>

</div>
<h2><span class="caption-index-2">30.7</span><a name="anchor-30-7"></a>Thanks</h2>
<p>
This module uses JPEG library which is distributed in the following site:
</p>
<p>
<a href="http://www.ijg.org/">http://www.ijg.org/</a>
</p>
{% endraw %}
