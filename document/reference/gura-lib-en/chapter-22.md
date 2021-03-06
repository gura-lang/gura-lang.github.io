---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-21.html#naviitem-selected
nextpage: chapter-23.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">22</span>gif Module</h1>
<h2><span class="caption-index-2">22.1</span><a name="anchor-22-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">gif</code> module provides measures to read/write image data in GIF format. To utilize it, import the <code class="highlighter-rouge">gif</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to read a GIF file:
</p>
<pre class="highlight"><code>import(gif)
img = image('foo.gif')
</code></pre>
<p>
Below is an example to create a GIF file that contains multiple images:
</p>
<pre class="highlight"><code>import(gif)
g = gif.content()
g.addimage(['cell1.png', 'cell2.png', 'cell3.png'], 10) g.write('anim.gif')
</code></pre>
<h2><span class="caption-index-2">22.2</span><a name="anchor-22-2"></a>Exntension to Function's Capability</h2>
<p>
This module extends the capability of function <code class="highlighter-rouge">image()</code> and instance method <code class="highlighter-rouge">image#write()</code> so that they can read/write GIF files.
</p>
<p>
When function <code class="highlighter-rouge">image()</code> is provided with a stream that satisfies the following conditions, it would recognize the stream as a GIF file.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.gif</code>".</li>
<li>The stream data begins with a byte sequence "<code class="highlighter-rouge">GIF87a</code>" or "<code class="highlighter-rouge">GIF89a</code>".</li>
</ul>
<p>
When instance method <code class="highlighter-rouge">image#write()</code> is provided with a stream that satisfies the following condition, it would write image data in GIF format.
</p>
<ul>
<li>The identifier of the stream ends with a suffix "<code class="highlighter-rouge">.gif</code>".</li>
</ul>
<h2><span class="caption-index-2">22.3</span><a name="anchor-22-3"></a>gif.content Class</h2>
<p>
The <code class="highlighter-rouge">gif.content</code> class provides properties to explain GIF information and methods to manipulate contents of GIF file. Below is a class diagram of <code class="highlighter-rouge">gif.content</code>:
</p>
<pre class="highlight"><code>+-------------+                         +-----------------------------+
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
<li>A property of <code class="highlighter-rouge">gif.content</code> has one or more images. Multiple images are mainly used for animation.</li>
<li>The property named <code class="highlighter-rouge">Header</code> is an instance of <code class="highlighter-rouge">gif.Header</code> class.</li>
<li>The property named <code class="highlighter-rouge">LogicalScreenDescriptor</code> is an instance of <code class="highlighter-rouge">gif.LogicalScreenDescriptor</code> class.</li>
<li>The property named <code class="highlighter-rouge">CommentExtension</code> is an instance of <code class="highlighter-rouge">gif.CommentExtension</code> class.</li>
<li>The property named <code class="highlighter-rouge">PlainTextExtension</code> is an instance of <code class="highlighter-rouge">gif.PlainTextExtension</code> class.</li>
<li>The property named <code class="highlighter-rouge">ApplicationExtension</code> is an instance of <code class="highlighter-rouge">gif.ApplicationExtension</code> class.</li>
</ul>
<h3><span class="caption-index-3">22.3.1</span><a name="anchor-22-3-1"></a>Constructor</h3>
<div class="mb-2"><code>gif.content(stream?:stream:r, format:symbol =&gt; `rgba) {block?}</code></div>
<div class="mb-2 ml-4">
Reads a GIF data from a stream and returns an object that contains GIF related information and images of a specified format. format is is <code class="highlighter-rouge">rgb,</code>rgba or <code class="highlighter-rouge">noimage. If</code>noimage is specified, only the information data is read
</div>
<h3><span class="caption-index-3">22.3.2</span><a name="anchor-22-3-2"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gif.content</code> instance has the following properties:
</p>
<div class="mb-2"><code>gif.content#ApplicationExtension</code> &hellip; <code>undefined</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.content#CommentExtension</code> &hellip; <code>undefined</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.content#Header</code> &hellip; <code>undefined</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.content#LogicalScreenDescriptor</code> &hellip; <code>undefined</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.content#PlainTextExtension</code> &hellip; <code>undefined</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.content#images</code> &hellip; <code>list</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h3><span class="caption-index-3">22.3.3</span><a name="anchor-22-3-3"></a>Method</h3>
<div class="mb-2"><code>gif.content#addimage(image:image, delayTime:number =&gt; 10, leftPos:number =&gt; 0, topPos:number =&gt; 0, disposalMethod:symbol =&gt; `none):map:reduce</code></div>
<div class="mb-2 ml-4">
<p>
Adds an image to GIF information.
</p>
<p>
You can add multiple images that can be played as a motion picture.
</p>
<p>
The argument <code class="highlighter-rouge">delayTime</code> specifies the delay time in 10 milli seconds between images.
</p>
<p>
The arguments <code class="highlighter-rouge">leftPost</code> and <code class="highlighter-rouge">topPos</code> specifies the rendered offset in the screen.
</p>
<p>
The argument <code class="highlighter-rouge">disposalMethod</code> takes one of following symbols that specifies how the image will be treated after being rendered.
</p>
<ul>
<li><code class="highlighter-rouge">`none</code> .. </li>
<li><code class="highlighter-rouge">`keep</code> .. </li>
<li><code class="highlighter-rouge">`background</code>.. </li>
<li><code class="highlighter-rouge">`previous</code> .. </li>
</ul>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>gif.content#write(stream:stream:w):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Writes a GIF image to a stream.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<h2><span class="caption-index-2">22.4</span><a name="anchor-22-4"></a>gif.Header Class</h2>
<p>
A <code class="highlighter-rouge">gif.Header</code> instance provides information of Header structure in GIF format.
</p>
<h3><span class="caption-index-3">22.4.1</span><a name="anchor-22-4-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gif.Header</code> instance has the following properties:
</p>
<div class="mb-2"><code>gif.Header#Signature</code> &hellip; <code>binary</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.Header#Version</code> &hellip; <code>binary</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">22.5</span><a name="anchor-22-5"></a>gif.LogicalScreenDescriptor Class</h2>
<p>
A <code class="highlighter-rouge">gif.LogicalScreenDescriptor</code> instance provides information of Logical Screen Descriptor structure in GIF format.
</p>
<h3><span class="caption-index-3">22.5.1</span><a name="anchor-22-5-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gif.LogicalScreenDescriptor</code> instance has the following properties:
</p>
<div class="mb-2"><code>gif.LogicalScreenDescriptor#BackgroundColor</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.LogicalScreenDescriptor#BackgroundColorIndex</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.LogicalScreenDescriptor#ColorResolution</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.LogicalScreenDescriptor#GlobalColorTableFlag</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.LogicalScreenDescriptor#LogicalScreenHeight</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.LogicalScreenDescriptor#LogicalScreenWidth</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.LogicalScreenDescriptor#PixelAspectRatio</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.LogicalScreenDescriptor#SizeOfGlobalColorTable</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.LogicalScreenDescriptor#SortFlag</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">22.6</span><a name="anchor-22-6"></a>gif.CommentExtension Class</h2>
<p>
A <code class="highlighter-rouge">gif.CommentExtnsion</code> instance provides information of Comment Extension structure in GIF format.
</p>
<h3><span class="caption-index-3">22.6.1</span><a name="anchor-22-6-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gif.CommentExtension</code> instance has the following properties:
</p>
<div class="mb-2"><code>gif.CommentExtension#CommentData</code> &hellip; <code>binary</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">22.7</span><a name="anchor-22-7"></a>gif.PlainTextExtension Class</h2>
<p>
A <code class="highlighter-rouge">gif.PlainTextExtnsion</code> instance provides information of Plain Text Extension structure in GIF format.
</p>
<h3><span class="caption-index-3">22.7.1</span><a name="anchor-22-7-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gif.PlainTextExtension</code> instance has the following properties:
</p>
<div class="mb-2"><code>gif.PlainTextExtension#CharacterCellHeight</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.PlainTextExtension#CharacterCellWidth</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.PlainTextExtension#PlainTextData</code> &hellip; <code>binary</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.PlainTextExtension#TextBackgroundColorIndex</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.PlainTextExtension#TextForegroundColorIndex</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.PlainTextExtension#TextGridHeight</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.PlainTextExtension#TextGridLeftPosition</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.PlainTextExtension#TextGridTopPosition</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.PlainTextExtension#TextGridWidth</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">22.8</span><a name="anchor-22-8"></a>gif.ApplicationExtension Class</h2>
<p>
A <code class="highlighter-rouge">gif.ApplicationExtnsion</code> instance provides information of Application Extension structure in GIF format.
</p>
<h3><span class="caption-index-3">22.8.1</span><a name="anchor-22-8-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gif.ApplicationExtension</code> instance has the following properties:
</p>
<div class="mb-2"><code>gif.ApplicationExtension#ApplicationData</code> &hellip; <code>binary</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.ApplicationExtension#ApplicationIdentifier</code> &hellip; <code>binary</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.ApplicationExtension#AuthenticationCode</code> &hellip; <code>binary</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">22.9</span><a name="anchor-22-9"></a>gif.GraphicControl Class</h2>
<p>
A <code class="highlighter-rouge">gif.GraphicControl</code> instance provides information of Graphi Control Extension structure in GIF format.
</p>
<h3><span class="caption-index-3">22.9.1</span><a name="anchor-22-9-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gif.GraphicControl</code> instance has the following properties:
</p>
<div class="mb-2"><code>gif.GraphicControl#DelayTime</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.GraphicControl#DisposalMethod</code> &hellip; <code>symbol</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.GraphicControl#TransparentColorFlag</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.GraphicControl#TransparentColorIndex</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.GraphicControl#UserInputFlag</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">22.10</span><a name="anchor-22-10"></a>gif.ImageDescriptor Class</h2>
<p>
A <code class="highlighter-rouge">gif.ImageDescriptor</code> instance provides information of Image Descriptor structure in GIF format.
</p>
<h3><span class="caption-index-3">22.10.1</span><a name="anchor-22-10-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gif.ImageDescriptor</code> instance has the following properties:
</p>
<div class="mb-2"><code>gif.ImageDescriptor#ImageHeight</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.ImageDescriptor#ImageLeftPosition</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.ImageDescriptor#ImageTopPosition</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.ImageDescriptor#ImageWidth</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.ImageDescriptor#InterlaceFlag</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.ImageDescriptor#LocalColorTableFlag</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.ImageDescriptor#SizeOfLocalColorTable</code> &hellip; <code>number</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.ImageDescriptor#SortFlag</code> &hellip; <code>boolean</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">22.11</span><a name="anchor-22-11"></a>gif.imgprop Class</h2>
<p>
Below is a class diagram of <code class="highlighter-rouge">gif.imgprop</code>:
</p>
<pre class="highlight"><code>+-------------+        +-------------+                  +---------------------+
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
<li>An <code class="highlighter-rouge">image</code> instance that the gif module creates from GIF file holds a <code class="highlighter-rouge">gif.imgprop</code> instance as its property that is named <code class="highlighter-rouge">gif</code>.</li>
<li>The property named <code class="highlighter-rouge">GraphicControl</code> is an instance of <code class="highlighter-rouge">gif.GraphiControl</code> class.</li>
<li>The property named <code class="highlighter-rouge">ImageDescriptor</code> is an instance of <code class="highlighter-rouge">gif.ImageDescriptor</code> class.</li>
</ul>
<h3><span class="caption-index-3">22.11.1</span><a name="anchor-22-11-1"></a>Property</h3>
<p>
A <code class="highlighter-rouge">gif.imgprop</code> instance has the following properties:
</p>
<div class="mb-2"><code>gif.imgprop#GraphicControl</code> &hellip; <code>any</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>gif.imgprop#ImageDescriptor</code> &hellip; <code>any</code> [read-only]</div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">22.12</span><a name="anchor-22-12"></a>Extension to image Class</h2>
<p>
This module extends the <code class="highlighter-rouge">stream</code> class with methods described here.
</p>
<div class="mb-2"><code>image#read@gif(stream:stream:r):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Reads a GIF image from a stream.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
<div class="mb-2"><code>image#write@gif(stream:stream:w):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Writes a GIF image to a stream.
</p>
<p>
This method returns the reference to the target instance itself.
</p>

</div>
{% endraw %}
