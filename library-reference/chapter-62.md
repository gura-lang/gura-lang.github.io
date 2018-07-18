---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">62</span><a name="anchor-62"></a>xpm Module</h1>
<h2><span class="caption-index-2">62.1</span><a name="anchor-62-1"></a>Overview</h2>
<p>
The <code>xpm</code> module provides measures to write image data in XPM format and to parse a list of strings that is described in the format. To utilize it, import the <code>xpm</code> module using <code>import</code> function.
</p>
<p>
Below is an example to parse a list of strings described in XPM format.
</p>
<pre><code>import(xpm)
foo_xpm = @{
"13 13 2 2 0 0",
"   c #000000",
"#  c #ffffff",
"          #               ",
"          #               ",
"  # # # # # # # # # #     ",
"          #               ",
"          #     #         ",
"        # # # # # #       ",
"      #   #     #   #     ",
"    #     #   #       #   ",
"  #       #   #       #   ",
"  #       #   #       #   ",
"  #       # #         #   ",
"    # # #           #     ",
"                # #       ",
}
img = image(`rgba).xpmdata(foo_xpm)
</code></pre>
<h2><span class="caption-index-2">62.2</span><a name="anchor-62-2"></a>Extension to image Class</h2>
<p>
This module extends the <code>image</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">image#write@xpm</strong></div>
<div style="margin-bottom:1em"><code>image#write@xpm(stream:stream:w):reduce</code></div>
Writes a xpm image to a stream.
</p>
<p>
<div><strong style="text-decoration:underline">image#xpmdata</strong></div>
<div style="margin-bottom:1em"><code>image#xpmdata(xpm[]:string):reduce</code></div>
Read xpm data from a string list.
</p>
<p />

{% endraw %}
