---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-25.html#naviitem-selected
nextpage: chapter-27.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">26</span>gurcbuild Module</h1>
<p>
The <code class="highlighter-rouge">gurcbuild</code> module is prepared to help create a composite Gura file, which contains script and other data files.
</p>
<p>
The example below would create a composite Gura file named <code class="highlighter-rouge">hello.gurc</code> that contains three files:
</p>
<pre class="highlight"><code>import(gurcbuild)

gurcbuild.build(['hello.gura', 'startimg.jpg', 'README.txt'])
</code></pre>
<h2><span class="caption-index-2">26.1</span><a name="anchor-26-1"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">gurcbuild.build</strong></div>
<div style="margin-bottom:1em"><code>gurcbuild.build(pathNames[]:string, dirName?:string)</code></div>
Creates a composite Gura file from files specified by <code class="highlighter-rouge">pathNames</code>, which includes script and other data files. The first entry of <code class="highlighter-rouge">pathNames</code> must be a script file that is to be executed as a main script.
</p>
<p>
The result file would be created in the directory specified by <code class="highlighter-rouge">dirName</code>. If the argument is omitted, the file would be created in the current working directory.
</p>
{% endraw %}
