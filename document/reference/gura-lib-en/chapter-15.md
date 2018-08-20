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
<p>
<div class="h5">curl.version</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>curl.version() {block?}</code></div>
Returns a string of the libcurl version.
</p>
<p>
<div class="h5">curl.easy_init</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>curl.easy_init() {block?}</code></div>
Initializes cURL and returns a easy_handle object.
</p>
<h2><span class="caption-index-2">15.3</span><a name="anchor-15-3"></a>curl.easy_handle Class</h2>
<p>
<div class="h5">curl.easy_handle#escape</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>curl.easy_handle#escape(string:string):void</code></div>

</p>
<p>
<div class="h5">curl.easy_handle#getinfo</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>curl.easy_handle#getinfo(info:number)</code></div>

</p>
<p>
<div class="h5">curl.easy_handle#recv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>curl.easy_handle#recv(buflen:number)</code></div>

</p>
<p>
<div class="h5">curl.easy_handle#reset</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>curl.easy_handle#reset():void</code></div>

</p>
<p>
<div class="h5">curl.easy_handle#send</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>curl.easy_handle#send(buffer:binary)</code></div>

</p>
<p>
<div class="h5">curl.easy_handle#setopt</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>curl.easy_handle#setopt(option:number, arg):void</code></div>

</p>
<p>
<div class="h5">curl.easy_handle#unescape</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>curl.easy_handle#unescape(string:string):void</code></div>

</p>
<h2><span class="caption-index-2">15.4</span><a name="anchor-15-4"></a>Thanks</h2>
<p>
This module uses libcurl which is distributed in the following site:
</p>
<p>
<a href="http://curl.haxx.se/libcurl/">http://curl.haxx.se/libcurl/</a>
</p>
{% endraw %}
