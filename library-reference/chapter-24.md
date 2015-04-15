---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">24</span><a name="anchor-24"></a>jpeg Module</h1>
<p>
The <code>jpeg</code> module provides measures to read/write image data in JPEG format. To utilize it, import the <code>jpeg</code> module using <code>import</code> function.
</p>
<p>
Below is an example to read a JPEG file:
</p>
<pre><code>import(jpeg)
img = image('foo.jpeg')
</code></pre>
<h2><span class="caption-index-2">24.1</span><a name="anchor-24-1"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code>image()</code> and instance method <code>image#write()</code> so that they can read/write JPEG files.
</p>
<p>
When function <code>image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a JPEG file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.jpeg</code>", "<code>.jpg</code>" or "<code>.jpe</code>".</li>
<li>The stream data begins with a byte sequence "<code>\xff\xd8</code>" that means SOI (start of Image) marker in JPEG specification.</li>
</ul>
<p>
When instance method <code>image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in JPEG format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.jpeg</code>", "<code>.jpg</code>" or "<code>.jpe</code>".</li>
</ul>
<h2><span class="caption-index-2">24.2</span><a name="anchor-24-2"></a>jpeg.exif Class</h2>
<p>
The <code>jpeg.exif</code> class provides EXIF information in a JPEG stream.
</p>
<p>
A <code>jpeg.exif</code> instance contains <code>jpeg.ifd</code> instances as properties named <code>jpeg.exif#ifd0</code> and <code>jpeg.exif#ifd1</code> that include a list of <code>jpeg.tag</code> instances.
</p>
<pre><code>+-----------+             +----------+        +----------+
| jpeg.exif |ifd0, ifd1   | jpeg.ifd |1..     | jpeg.tag |
|-----------*-------------+----------*--------+----------|
|           |             |          |        |          |
+-----------+             +----------+        +----------+
</code></pre>
<h3><span class="caption-index-3">24.2.1</span><a name="anchor-24-2-1"></a>Property</h3>
<p>
A <code>jpeg.exif</code> instance has the following properties:
</p>
<p>
<table>

<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>
jpeg.exif#endian</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
The endian type: <code>
`big</code>
 for big-endian and
<code>
`little</code>
 for little-endian.</td>
</tr>


<tr>
<td>
<code>
jpeg.exif#ifd0</code>
</td>
<td>
<code>
jpeg.ifd</code>
</td>
<td>
R</td>

<td>
IFD0 instance.</td>
</tr>


<tr>
<td>
<code>
jpeg.exif#ifd1</code>
</td>
<td>
<code>
jpeg.ifd</code>
</td>
<td>
R</td>

<td>
IFD1 instance.</td>
</tr>


<tr>
<td>
<code>
jpeg.exif#thumbnail</code>
</td>
<td>
<code>
image</code>
</td>
<td>
R</td>

<td>
Thumbnail image as <code>
image</code>
 value.</td>
</tr>


<tr>
<td>
<code>
jpeg.exif#thumbnail@jpeg</code>
</td>
<td>
<code>
binary</code>
</td>
<td>
R</td>

<td>
Thumbnail image as JPEG binary data.</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">24.2.2</span><a name="anchor-24-2-2"></a>Function to Create Instance</h3>
<p>
<strong>jpeg.exif</strong>
</p>
<p>
<code>jpeg.exif(stream?:stream:r):map:[raise] {block?}</code>
</p>
<p>
Reads EXIF data from <code>stream</code> and creates a <code>jpeg.exif</code> instance.
</p>
<p>
If no EXIF information exists in the stream, this function returns <code>nil</code>. If the attribute <code>:raise</code> is specified, an error occurs for that case.
</p>
<p>
If <code>block</code> is specified, it would be evaluated with a block parameter <code>|exif:jpeg.exif|</code>, where <code>exif</code> is the created instance. In this case, the block's result would become the function's returned value.
</p>
<h3><span class="caption-index-3">24.2.3</span><a name="anchor-24-2-3"></a>Method</h3>
<p>
<strong>jpeg.exif#each</strong>
</p>
<p>
<code>jpeg.exif#each() {block?}</code>
</p>
<p>
Creates an iterator that returns <code>jpeg.tag</code> values as elements that are stored in the property <code>jpeg.exif#ifd0</code>.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h2><span class="caption-index-2">24.3</span><a name="anchor-24-3"></a>jpeg.ifd Class</h2>
<h3><span class="caption-index-3">24.3.1</span><a name="anchor-24-3-1"></a>Property</h3>
<p>
A <code>jpeg.ifd</code> instance has the following properties:
</p>
<p>
<table>

<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>
jpeg.ifd#name</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>
jpeg.ifd#symbol</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">24.3.2</span><a name="anchor-24-3-2"></a>Method</h3>
<p>
<strong>jpeg.ifd#each</strong>
</p>
<p>
<code>jpeg.ifd#each() {block?}</code>
</p>
<p>
Creates an iterator that returns <code>jpeg.tag</code> values as elements that are stored in the target <code>jpeg.ifd</code> instance.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<h2><span class="caption-index-2">24.4</span><a name="anchor-24-4"></a>jpeg.tag Class</h2>
<h3><span class="caption-index-3">24.4.1</span><a name="anchor-24-4-1"></a>Property</h3>
<p>
A <code>jpeg.tag</code> instance has the following properties:
</p>
<p>
<table>

<tr>
<th>
Property</th>
<th>
Type</th>
<th>
R/W</th>
<th>
Explanation</th>
</tr>


<tr>
<td>
<code>
jpeg.tag#id</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Tag ID.</td>
</tr>


<tr>
<td>
<code>
jpeg.tag#name</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
Tag name.</td>
</tr>


<tr>
<td>
<code>
jpeg.tag#symbol</code>
</td>
<td>
<code>
symbol</code>
</td>
<td>
R</td>

<td>
Tag name as <code>
symbol</code>
.</td>
</tr>


<tr>
<td>
<code>
jpeg.tag#type</code>
</td>
<td>
<code>
number</code>
</td>
<td>
R</td>

<td>
Tag type.</td>
</tr>


<tr>
<td>
<code>
jpeg.tag#typename</code>
</td>
<td>
<code>
string</code>
</td>
<td>
R</td>

<td>
Tag type name.</td>
</tr>


<tr>
<td>
<code>
jpeg.tag#value</code>
</td>
<td>
<code>
any</code>
</td>
<td>
R</td>

<td>
Tag value. When the attribute <code>
:cooked</code>
 is specified,
numbers in some tags are translated to human-readable symbols.</td>
</tr>


<tr>
<td>
<code>
jpeg.tag#ifd</code>
</td>
<td>
<code>
jpeg.ifd</code>
</td>
<td>
R</td>

<td>
IFD instance. Valid only for tags <code>
Exif</code>
, <code>
GPSInfo</code>
 and
<code>
Interoperability</code>
.</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">24.5</span><a name="anchor-24-5"></a>Extension to image Class</h2>
<p>
This module extends the <code>image</code> class with methods described here.
</p>
<p>
<strong>image#read@jpeg</strong>
</p>
<p>
<code>image#read@jpeg(stream:stream:r):reduce</code>
</p>
<p>
Reads a JPEG image data from a stream.
</p>
<p>
<strong>image#write@jpeg</strong>
</p>
<p>
<code>image#write@jpeg(stream:stream:w, quality:number =&gt; 75):reduce</code>
</p>
<p>
Writes a JPEG image data to a stream.
</p>
<h2><span class="caption-index-2">24.6</span><a name="anchor-24-6"></a>Thanks</h2>
<p>
This module uses JPEG library which is distributed in the following site:
</p>
<p>
<a href="http://www.ijg.org/">http://www.ijg.org/</a>
</p>
<p />

{% endraw %}