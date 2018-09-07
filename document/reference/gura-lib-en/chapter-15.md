---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-14.html#naviitem-selected
nextpage: chapter-16.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">15</span>curl Module</h1>
<h2><span class="caption-index-2">15.1</span><a name="anchor-15-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">curl</code> module provices measures to access Internet resources using cURL library. To utilize it, import the <code class="highlighter-rouge">curl</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<h2><span class="caption-index-2">15.2</span><a name="anchor-15-2"></a>Module Function</h2>
<div class="mb-2"><code>curl.version() {block?}</code></div>
<div class="mb-2 ml-4">
Returns a string of the libcurl version.
</div>
<div class="mb-2"><code>curl.easy_init() {block?}</code></div>
<div class="mb-2 ml-4">
Initializes cURL and returns a easy_handle object.
</div>
<h2><span class="caption-index-2">15.3</span><a name="anchor-15-3"></a>curl.easy_handle Class</h2>
<div class="mb-2"><code>curl.easy_handle#escape(string:string):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>curl.easy_handle#getinfo(info:number)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>curl.easy_handle#recv(buflen:number)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>curl.easy_handle#reset():void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>curl.easy_handle#send(buffer:binary)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>curl.easy_handle#setopt(option:number, arg):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>curl.easy_handle#unescape(string:string):void</code></div>
<div class="mb-2 ml-4">

</div>
<h2><span class="caption-index-2">15.4</span><a name="anchor-15-4"></a>Thanks</h2>
<p>
This module uses libcurl which is distributed in the following site:
</p>
<p>
<a href="http://curl.haxx.se/libcurl/">http://curl.haxx.se/libcurl/</a>
</p>
{% endraw %}
