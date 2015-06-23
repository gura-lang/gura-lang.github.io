---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">21</span><a name="anchor-21"></a>gif Module</h1>
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
<h2><span class="caption-index-2">21.1</span><a name="anchor-21-1"></a>Exntension to Function's Capability</h2>
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
<h2><span class="caption-index-2">21.2</span><a name="anchor-21-2"></a>gif.content Class</h2>
<p>
<strong>gif.content</strong>
</p>
<p>
<code>gif.content(stream?:stream:r, format:symbol =&gt; `rgba) {block?}</code>
</p>
<p>
Reads a GIF data from a stream and returns an object that contains GIF related information and images of a specified format. format is is <code>rgb,</code>rgba or <code>noimage. If</code>noimage is specified, only the information data is read
</p>
<p>
<strong>gif.content#addimage</strong>
</p>
<p>
<code>gif.content#addimage(image:image, delayTime:number =&gt; 10, leftPos:number =&gt; 0, topPos:number =&gt; 0, disposalMethod:symbol =&gt; `none):map:reduce</code>
</p>
<p>
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
<strong>gif.content#write</strong>
</p>
<p>
<code>gif.content#write(stream:stream:w):reduce</code>
</p>
<p>
Writes a GIF image to a stream.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<h2><span class="caption-index-2">21.3</span><a name="anchor-21-3"></a>Extension to image Class</h2>
<p>
This module extends the <code>stream</code> class with methods described here.
</p>
<p>
<strong>image#read@gif</strong>
</p>
<p>
<code>image#read@gif(stream:stream:r):reduce</code>
</p>
<p>
Reads a GIF image from a stream.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p>
<strong>image#write@gif</strong>
</p>
<p>
<code>image#write@gif(stream:stream:w):reduce</code>
</p>
<p>
Writes a GIF image to a stream.
</p>
<p>
This method returns the reference to the target instance itself.
</p>
<p />

{% endraw %}
