---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">13</span><a name="anchor-13"></a>curl Module</h1>
<p>
The <code>curl</code> module provices measures to access Internet resources using cURL library. To utilize it, import the <code>curl</code> module using <code>import</code> function.
</p>
<h2><span class="caption-index-2">13.1</span><a name="anchor-13-1"></a>Module Functions</h2>
<p>
<strong>curl.version</strong>
</p>
<p>
<code>curl.version() {block?}</code>
</p>
<p>
Returns a string of the libcurl version.
</p>
<p>
<strong>curl.easy_init</strong>
</p>
<p>
<code>curl.easy_init() {block?}</code>
</p>
<p>
Initializes cURL and returns a easy<em>handle object.</em>
</p>
<h2><span class="caption-index-2">13.2</span><a name="anchor-13-2"></a>curl.easy_handle Class</h2>
<p>
<strong>curl.easy_handle#escape</strong>
</p>
<p>
<code>curl.easy_handle#escape(string:string):void</code>
</p>
<p>
<strong>curl.easy_handle#getinfo</strong>
</p>
<p>
<code>curl.easy_handle#getinfo(info:number)</code>
</p>
<p>
<strong>curl.easy_handle#perform</strong>
</p>
<p>
<code>curl.easy_handle#perform(stream?:stream:w):void</code>
</p>
<p>
<strong>curl.easy_handle#recv</strong>
</p>
<p>
<code>curl.easy_handle#recv(buflen:number)</code>
</p>
<p>
<strong>curl.easy_handle#reset</strong>
</p>
<p>
<code>curl.easy_handle#reset():void</code>
</p>
<p>
<strong>curl.easy_handle#send</strong>
</p>
<p>
<code>curl.easy_handle#send(buffer:binary)</code>
</p>
<p>
<strong>curl.easy_handle#setopt</strong>
</p>
<p>
<code>curl.easy_handle#setopt(option:number, arg):void</code>
</p>
<p>
<strong>curl.easy_handle#unescape</strong>
</p>
<p>
<code>curl.easy_handle#unescape(string:string):void</code>
</p>
<h2><span class="caption-index-2">13.3</span><a name="anchor-13-3"></a>Thanks</h2>
<p>
This module uses libcurl which is distributed in the following site:
</p>
<p>
<a href="http://curl.haxx.se/libcurl/">http://curl.haxx.se/libcurl/</a>
</p>
<p />

{% endraw %}
