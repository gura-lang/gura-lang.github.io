---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">45</span><a name="anchor-45"></a>tar Module</h1>
<p>
The <code>tar</code> module provides measures to read/write TAR files. To utilize it, import the <code>tar</code> module using <code>import</code> function.
</p>
<h2><span class="caption-index-2">45.1</span><a name="anchor-45-1"></a>tar.reader Class</h2>
<h3><span class="caption-index-3">45.1.1</span><a name="anchor-45-1-1"></a>Function To Create Instance</h3>
<p>
<strong>tar.reader</strong>
</p>
<p>
<code>tar.reader(stream:stream:r, compression?:symbol) {block?}</code>
</p>
<h3><span class="caption-index-3">45.1.2</span><a name="anchor-45-1-2"></a>Method</h3>
<p>
<strong>tar.reader#entries</strong>
</p>
<p>
<code>tar.reader#entries() {block?}</code>
</p>
<h2><span class="caption-index-2">45.2</span><a name="anchor-45-2"></a>tar.writer Class</h2>
<h3><span class="caption-index-3">45.2.1</span><a name="anchor-45-2-1"></a>Function To Create Instance</h3>
<p>
<strong>tar.writer</strong>
</p>
<p>
<code>tar.writer(stream:stream:w, compression?:symbol) {block?}</code>
</p>
<h3><span class="caption-index-3">45.2.2</span><a name="anchor-45-2-2"></a>Method</h3>
<p>
<strong>tar.writer#add</strong>
</p>
<p>
<code>tar.writer#add(stream:stream:r, filename?:string):map:reduce</code>
</p>
<p>
<strong>tar.writer#close</strong>
</p>
<p>
<code>tar.writer#close():reduce</code>
</p>
<h2><span class="caption-index-2">45.3</span><a name="anchor-45-3"></a>Thanks</h2>
<p>
This module uses zlib and bzip2 library which are distributed in the following sites:
</p>
<ul>
<li><a href="http://zlib.net/">http://zlib.net/</a></li>
<li><a href="http://www.bzip.org/">http://www.bzip.org/</a></li>
</ul>
<p />

{% endraw %}
