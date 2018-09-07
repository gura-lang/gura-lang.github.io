---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-59.html#naviitem-selected
nextpage: chapter-61.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">60</span>xpm Module</h1>
<h2><span class="caption-index-2">60.1</span><a name="anchor-60-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">xpm</code> module provides measures to write image data in XPM format and to parse a list of strings that is described in the format. To utilize it, import the <code class="highlighter-rouge">xpm</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to parse a list of strings described in XPM format.
</p>
<pre class="highlight"><code>import(xpm)
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
<h2><span class="caption-index-2">60.2</span><a name="anchor-60-2"></a>Extension to image Class</h2>
<p>
This module extends the <code class="highlighter-rouge">image</code> class with methods described here.
</p>
<div class="mb-2"><code>image#write@xpm(stream:stream:w):reduce</code></div>
<div class="mb-2 ml-4">
Writes a xpm image to a stream.
</div>
<div class="mb-2"><code>image#xpmdata(xpm[]:string):reduce</code></div>
<div class="mb-2 ml-4">
Read xpm data from a string list.
</div>
{% endraw %}
