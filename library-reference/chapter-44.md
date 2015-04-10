---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">44</span><a name="anchor-44"></a>xpm Module</h1>
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
<h2><span class="caption-index-2">44.1</span><a name="anchor-44-1"></a>Extension to image Class</h2>
<p>
This module extends the <code>image</code> class with methods described here.
</p>
<p>
<strong>image#write@xpm</strong>
</p>
<p>
<code>image#write@xpm(stream:stream:w):reduce</code>
</p>
<p>
Writes a xpm image to a stream.
</p>
<p>
<strong>image#xpmdata</strong>
</p>
<p>
<code>image#xpmdata(xpm[]:string):reduce</code>
</p>
<p>
Read xpm data from a string list.
</p>
<p />

{% endraw %}
