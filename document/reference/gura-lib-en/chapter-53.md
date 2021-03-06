---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-52.html#naviitem-selected
nextpage: chapter-54.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">53</span>tar Module</h1>
<h2><span class="caption-index-2">53.1</span><a name="anchor-53-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">tar</code> module provides measures to read/write TAR files. To utilize it, import the <code class="highlighter-rouge">tar</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<h2><span class="caption-index-2">53.2</span><a name="anchor-53-2"></a>tar.reader Class</h2>
<h3><span class="caption-index-3">53.2.1</span><a name="anchor-53-2-1"></a>Function To Create Instance</h3>
<div class="mb-2"><code>tar.reader(stream:stream:r, compression?:symbol) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Reads a tar file from <code class="highlighter-rouge">stream</code> and returns a <code class="highlighter-rouge">tar.reader</code> instance that is to be used to read contents from the archive.
</p>
<p>
The argument <code class="highlighter-rouge">compression</code> specifies the compression format of the tar file and takes one of the following symbols:
</p>
<ul>
<li><code class="highlighter-rouge">`auto</code> .. determins the format from a suffix name of the stream.</li>
<li><code class="highlighter-rouge">`gzip</code> .. gzip format</li>
<li><code class="highlighter-rouge">`bzip2</code> .. bzip2 format</li>
</ul>

</div>
<h3><span class="caption-index-3">53.2.2</span><a name="anchor-53-2-2"></a>Method</h3>
<div class="mb-2"><code>tar.reader#entries() {block?}</code></div>
<div class="mb-2 ml-4">
Creates an iterator that returns stream instances for each entry in the tar file.
</div>
<h2><span class="caption-index-2">53.3</span><a name="anchor-53-3"></a>tar.writer Class</h2>
<h3><span class="caption-index-3">53.3.1</span><a name="anchor-53-3-1"></a>Function To Create Instance</h3>
<div class="mb-2"><code>tar.writer(stream:stream:w, compression?:symbol) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Creates a tar file on <code class="highlighter-rouge">stream</code> and returns a <code class="highlighter-rouge">tar.writer</code> instance that is to be used to write contents to the archive.
</p>
<p>
The argument <code class="highlighter-rouge">compression</code> specifies the compression format of the tar file and takes one of the following symbols:
</p>
<ul>
<li><code class="highlighter-rouge">`auto</code> .. determins the format from a suffix name of the stream.</li>
<li><code class="highlighter-rouge">`gzip</code> .. gzip format</li>
<li><code class="highlighter-rouge">`bzip2</code> .. bzip2 format</li>
</ul>

</div>
<h3><span class="caption-index-3">53.3.2</span><a name="anchor-53-3-2"></a>Method</h3>
<div class="mb-2"><code>tar.writer#add(stream:stream:r, filename?:string):map:reduce</code></div>
<div class="mb-2 ml-4">
<p>
Adds an entry to the tar archive with a content from <code class="highlighter-rouge">stream</code> and a name of <code class="highlighter-rouge">filename</code>.
</p>
<p>
If the argument <code class="highlighter-rouge">filename</code> is omitted, an identifier associated with the <code class="highlighter-rouge">stream</code> would be used as the entry name.
</p>

</div>
<div class="mb-2"><code>tar.writer#close():reduce</code></div>
<div class="mb-2 ml-4">
Flushes all the unfinished writing processes and invalidates the <code class="highlighter-rouge">tar.writer</code> instance.
</div>
<h2><span class="caption-index-2">53.4</span><a name="anchor-53-4"></a>Thanks</h2>
<p>
This module uses zlib and bzip2 library which are distributed in the following sites:
</p>
<ul>
<li><a href="http://zlib.net/">http://zlib.net/</a></li>
<li><a href="http://www.bzip.org/">http://www.bzip.org/</a></li>
</ul>
{% endraw %}
