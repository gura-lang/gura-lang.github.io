---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">26</span><a name="anchor-26"></a>gurcbuild Module</h1>
<p>
The <code>gurcbuild</code> module is prepared to help create a composite Gura file, which contains script and other data files.
</p>
<p>
The example below would create a composite Gura file named <code>hello.gurc</code> that contains three files:
</p>
<pre><code>import(gurcbuild)

gurcbuild.build(['hello.gura', 'startimg.jpg', 'README.txt'])
</code></pre>
<h2><span class="caption-index-2">26.1</span><a name="anchor-26-1"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">gurcbuild.build</strong></div>
<div style="margin-bottom:1em"><code>gurcbuild.build(pathNames[]:string, dirName?:string)</code></div>
Creates a composite Gura file from files specified by <code>pathNames</code>, which includes script and other data files. The first entry of <code>pathNames</code> must be a script file that is to be executed as a main script.
</p>
<p>
The result file would be created in the directory specified by <code>dirName</code>. If the argument is omitted, the file would be created in the current working directory.
</p>
<p />

{% endraw %}
