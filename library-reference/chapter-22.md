---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">22</span><a name="anchor-22"></a>gif Module</h1>
<h2><span class="caption-index-2">22.1</span><a name="anchor-22-1"></a>Overview</h2>
<p>
The <code>gif</code> module provides measures to read/write image data in GIF format. To utilize it, import the <code>gif</code> module using <code>import</code> function.
</p>
<p>
Below is an example to read a GIF file:
</p>
<pre><code>import(gif)
img = image('foo.gif')
</code></pre>
<p>
Below is an example to create a GIF file that contains multiple images:
</p>
<pre><code>import(gif)
g = gif.content()
g.addimage(['cell1.png', 'cell2.png', 'cell3.png'], 10) g.write('anim.gif')
</code></pre>
<h2><span class="caption-index-2">22.2</span><a name="anchor-22-2"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code>image()</code> and instance method <code>image#write()</code> so that they can read/write GIF files.
</p>
<p>
When function <code>image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a GIF file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.gif</code>".</li>
<li>The stream data begins with a byte sequence "<code>GIF87a</code>" or "<code>GIF89a</code>".</li>
</ul>
<p>
When instance method <code>image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in GIF format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code>.gif</code>".</li>
</ul>
<h2><span class="caption-index-2">22.3</span><a name="anchor-22-3"></a>gif.content Class</h2>
<p>
The <code>gif.content</code> class provides properties to explain GIF information and methods to manipulate contents of GIF file. Below is a class diagram of <code>gif.content</code>:
</p>
<pre><code>+-------------+                         +-----------------------------+
| gif.content |images                   |            image            |
|-------------*-------------------------+-----------------------------|
|             |                     1.. +-----------------------------+
|             |
|             |                         +-----------------------------+
|             |Header                   |         gif.Header          |
|             *-------------------------+-----------------------------|
|             |                         +-----------------------------+
|             |
|             |                         +-----------------------------+
|             |LogicalScreenDescriptor  | gif.LogicalScreenDescriptor |
|             *-------------------------+-----------------------------|
|             |                         +-----------------------------+
|             |
|             |                         +-----------------------------+
|             |CommentExtension         |    gif.CommentExtension     |
|             *-------------------------+-----------------------------|
|             |                         +-----------------------------+
|             |
|             |                         +-----------------------------+
|             |PlainTextExntension      |   gif.PlainTextExtension    |
|             *-------------------------+-----------------------------|
|             |                         +-----------------------------+
|             |
|             |                         +-----------------------------+
|             |ApplicationExntension    | gif.ApplicationExtension    |
|             *-------------------------+-----------------------------|
|             |                         +-----------------------------+
+-------------+
</code></pre>
<ul>
<li>A property of <code>gif.content</code> has one or more images. Multiple images are mainly used for animation.</li>
<li>The property named <code>Header</code> is an instance of <code>gif.Header</code> class.</li>
<li>The property named <code>LogicalScreenDescriptor</code> is an instance of <code>gif.LogicalScreenDescriptor</code> class.</li>
<li>The property named <code>CommentExtension</code> is an instance of <code>gif.CommentExtension</code> class.</li>
<li>The property named <code>PlainTextExtension</code> is an instance of <code>gif.PlainTextExtension</code> class.</li>
<li>The property named <code>ApplicationExtension</code> is an instance of <code>gif.ApplicationExtension</code> class.</li>
</ul>
<h3><span class="caption-index-3">22.3.1</span><a name="anchor-22-3-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">gif.content</strong></div>
<div style="margin-bottom:1em"><code>gif.content(stream?:stream:r, format:symbol =&gt; `rgba) {block?}</code></div>
Reads a GIF data from a stream and returns an object that contains GIF related information and images of a specified format. format is is <code>rgb,</code>rgba or <code>noimage. If</code>noimage is specified, only the information data is read
</p>
<h3><span class="caption-index-3">22.3.2</span><a name="anchor-22-3-2"></a>Property</h3>
<p>
A <code>gif.content</code> instance has the following properties:
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
<code>images</code></td>
<td>
<code>image[]</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>Header</code></td>
<td>
<code>gif.Header</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>LogicalScreenDescriptor</code></td>
<td>
<code>gif.LogicalScreenDescriptor</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>CommentExtension</code></td>
<td>
<code>gif.CommentExtension</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>PlainTextExtension</code></td>
<td>
<code>gif.PlainTextExtension</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>ApplicationExtension</code></td>
<td>
<code>gif.ApplicationExtension</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h3><span class="caption-index-3">22.3.3</span><a name="anchor-22-3-3"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">gif.content#addimage</strong></div>
<div style="margin-bottom:1em"><code>gif.content#addimage(image:image, delayTime:number =&gt; 10, leftPos:number =&gt; 0, topPos:number =&gt; 0, disposalMethod:symbol =&gt; `none):map:reduce</code></div>
Adds an image to GIF information.
</p>
<p>
You can add multiple images that can be played as a motion picture.
</p>
<p>
The argument <code>delayTime</code> specifies the delay time in 10 milli seconds between images.
</p>
<p>
The arguments <code>leftPost</code> and <code>topPos</code> specifies the rendered offset in the screen.
</p>
<p>
The argument <code>disposalMethod</code> takes one of following symbols that specifies how the image will be treated after being rendered.
</p>
<ul>
<li><code>`none</code> .. </li>
<li><code>`keep</code> .. </li>
<li><code>`background</code>.. </li>
<li><code>`previous</code> .. </li>
</ul>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">gif.content#write</strong></div>
<div style="margin-bottom:1em"><code>gif.content#write(stream:stream:w):reduce</code></div>
Writes a GIF image to a stream.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<h2><span class="caption-index-2">22.4</span><a name="anchor-22-4"></a>gif.Header Class</h2>
<p>
A <code>gif.Header</code> instance provides information of Header structure in GIF format.
</p>
<h3><span class="caption-index-3">22.4.1</span><a name="anchor-22-4-1"></a>Property</h3>
<p>
A <code>gif.Header</code> instance has the following properties:
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
<code>Signature</code></td>
<td>
<code>binary</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>Version</code></td>
<td>
<code>binary</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">22.5</span><a name="anchor-22-5"></a>gif.LogicalScreenDescriptor Class</h2>
<p>
A <code>gif.LogicalScreenDescriptor</code> instance provides information of Logical Screen Descriptor structure in GIF format.
</p>
<h3><span class="caption-index-3">22.5.1</span><a name="anchor-22-5-1"></a>Property</h3>
<p>
A <code>gif.LogicalScreenDescriptor</code> instance has the following properties:
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
<code>LogicalScreenWidth</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>LogicalScreenHeight</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>GlobalColorTableFlag</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>ColorResolution</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>SortFlag</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>SizeOfGlobalColorTable</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>BackgroundColorIndex</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>BackgroundColor</code></td>
<td>
<code>color</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>PixelAspectRatio</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">22.6</span><a name="anchor-22-6"></a>gif.CommentExtension Class</h2>
<p>
A <code>gif.CommentExtnsion</code> instance provides information of Comment Extension structure in GIF format.
</p>
<h3><span class="caption-index-3">22.6.1</span><a name="anchor-22-6-1"></a>Property</h3>
<p>
A <code>gif.CommentExtension</code> instance has the following properties:
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
<code>CommentData</code></td>
<td>
<code>binary</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">22.7</span><a name="anchor-22-7"></a>gif.PlainTextExtension Class</h2>
<p>
A <code>gif.PlainTextExtnsion</code> instance provides information of Plain Text Extension structure in GIF format.
</p>
<h3><span class="caption-index-3">22.7.1</span><a name="anchor-22-7-1"></a>Property</h3>
<p>
A <code>gif.PlainTextExtension</code> instance has the following properties:
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
<code>TextGridLeftPosition</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>TextGridTopPosition</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>TextGridWidth</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>TextGridHeight</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>CharacterCellWidth</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>CharacterCellHeight</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>TextForegroundColorIndex</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>TextBackgroundColorIndex</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>PlainTextData</code></td>
<td>
<code>binary</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">22.8</span><a name="anchor-22-8"></a>gif.ApplicationExtension Class</h2>
<p>
A <code>gif.ApplicationExtnsion</code> instance provides information of Application Extension structure in GIF format.
</p>
<h3><span class="caption-index-3">22.8.1</span><a name="anchor-22-8-1"></a>Property</h3>
<p>
A <code>gif.ApplicationExtension</code> instance has the following properties:
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
<code>ApplicationIdentifier</code></td>
<td>
<code>binary</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>AuthenticationCode</code></td>
<td>
<code>binary</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>ApplicationData</code></td>
<td>
<code>binary</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">22.9</span><a name="anchor-22-9"></a>gif.GraphicControl Class</h2>
<p>
A <code>gif.GraphicControl</code> instance provides information of Graphi Control Extension structure in GIF format.
</p>
<h3><span class="caption-index-3">22.9.1</span><a name="anchor-22-9-1"></a>Property</h3>
<p>
A <code>gif.GraphicControl</code> instance has the following properties:
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
<code>DisposalMethod</code></td>
<td>
<code>symbol</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>UserInputFlag</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>TransparentColorFlag</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>DelayTime</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>TransparentColorIndex</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">22.10</span><a name="anchor-22-10"></a>gif.ImageDescriptor Class</h2>
<p>
A <code>gif.ImageDescriptor</code> instance provides information of Image Descriptor structure in GIF format.
</p>
<h3><span class="caption-index-3">22.10.1</span><a name="anchor-22-10-1"></a>Property</h3>
<p>
A <code>gif.ImageDescriptor</code> instance has the following properties:
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
<code>ImageLeftPosition</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>ImageTopPosition</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>ImageWidth</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>ImageHeight</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>LocalColorTableFlag</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>InterlaceFlag</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>SortFlag</code></td>
<td>
<code>boolean</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>SizeOfLocalColorTable</code></td>
<td>
<code>number</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">22.11</span><a name="anchor-22-11"></a>gif.imgprop Class</h2>
<p>
Below is a class diagram of <code>gif.imgprop</code>:
</p>
<pre><code>+-------------+        +-------------+                  +---------------------+
|    image    |gif     | gif.imgprop |GraphicControl    | gif.GraphicControl  |
|-------------*--------+-------------*------------------+---------------------|
+-------------+        |             |                  +---------------------+
                       |             |
                       |             |                  +---------------------+
                       |             |ImageDescriptor   | gif.ImageDescriptor |
                       |             *------------------+---------------------|
                       |             |                  +---------------------+
                       +-------------+
</code></pre>
<ul>
<li>An <code>image</code> instance that the gif module creates from GIF file holds a <code>gif.imgprop</code> instance as its property that is named <code>gif</code>.</li>
<li>The property named <code>GraphicControl</code> is an instance of <code>gif.GraphiControl</code> class.</li>
<li>The property named <code>ImageDescriptor</code> is an instance of <code>gif.ImageDescriptor</code> class.</li>
</ul>
<h3><span class="caption-index-3">22.11.1</span><a name="anchor-22-11-1"></a>Property</h3>
<p>
A <code>gif.imgprop</code> instance has the following properties:
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
<code>GraphicControl</code></td>
<td>
<code>gif.GraphicControl</code></td>
<td>
R</td>

<td>
</td>
</tr>


<tr>
<td>
<code>ImageDescriptor</code></td>
<td>
<code>gif.ImageDescriptor</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<h2><span class="caption-index-2">22.12</span><a name="anchor-22-12"></a>Extension to image Class</h2>
<p>
This module extends the <code>stream</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">image#read@gif</strong></div>
<div style="margin-bottom:1em"><code>image#read@gif(stream:stream:r):reduce</code></div>
Reads a GIF image from a stream.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<div><strong style="text-decoration:underline">image#write@gif</strong></div>
<div style="margin-bottom:1em"><code>image#write@gif(stream:stream:w):reduce</code></div>
Writes a GIF image to a stream.
</p>
<p>
This method returns the reference to the target instance itself.
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
<code>gif</code></td>
<td>
<code>gif.imgprop</code></td>
<td>
R</td>

<td>
</td>
</tr>


</table>

</p>
<p />

{% endraw %}
