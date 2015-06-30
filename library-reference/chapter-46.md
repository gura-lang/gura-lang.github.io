---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">46</span><a name="anchor-46"></a>tar Module</h1>
<p>
The <code>tar</code> module provides measures to read/write TAR files. To utilize it, import the <code>tar</code> module using <code>import</code> function.
</p>
<h2><span class="caption-index-2">46.1</span><a name="anchor-46-1"></a>tar.reader Class</h2>
<h3><span class="caption-index-3">46.1.1</span><a name="anchor-46-1-1"></a>Function To Create Instance</h3>
<p>
<div><strong style="text-decoration:underline">tar.reader</strong></div>
<div style="margin-bottom:1em"><code>tar.reader(stream:stream:r, compression?:symbol) {block?}</code></div>

</p>
<h3><span class="caption-index-3">46.1.2</span><a name="anchor-46-1-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">tar.reader#entries</strong></div>
<div style="margin-bottom:1em"><code>tar.reader#entries() {block?}</code></div>

</p>
<h2><span class="caption-index-2">46.2</span><a name="anchor-46-2"></a>tar.writer Class</h2>
<h3><span class="caption-index-3">46.2.1</span><a name="anchor-46-2-1"></a>Function To Create Instance</h3>
<p>
<div><strong style="text-decoration:underline">tar.writer</strong></div>
<div style="margin-bottom:1em"><code>tar.writer(stream:stream:w, compression?:symbol) {block?}</code></div>

</p>
<h3><span class="caption-index-3">46.2.2</span><a name="anchor-46-2-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">tar.writer#add</strong></div>
<div style="margin-bottom:1em"><code>tar.writer#add(stream:stream:r, filename?:string):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">tar.writer#close</strong></div>
<div style="margin-bottom:1em"><code>tar.writer#close():reduce</code></div>

</p>
<h2><span class="caption-index-2">46.3</span><a name="anchor-46-3"></a>Thanks</h2>
<p>
This module uses zlib and bzip2 library which are distributed in the following sites:
</p>
<ul>
<li><a href="http://zlib.net/">http://zlib.net/</a></li>
<li><a href="http://www.bzip.org/">http://www.bzip.org/</a></li>
</ul>
<p />

{% endraw %}
