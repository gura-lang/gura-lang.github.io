---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-52.html#naviitem-selected
nextpage: chapter-54.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">53</span>sys Module</h1>
<h2><span class="caption-index-2">53.1</span><a name="anchor-53-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">sys</code> module provides system-related information. This is a built-in module, so you can use it without being imported.
</p>
<h2><span class="caption-index-2">53.2</span><a name="anchor-53-2"></a>Module Variable</h2>
<ul>
<li><code class="highlighter-rouge">sys.argv</code></li>
<li><code class="highlighter-rouge">sys.path</code></li>
<li><code class="highlighter-rouge">sys.maindir</code></li>
<li><code class="highlighter-rouge">sys.version</code></li>
<li><code class="highlighter-rouge">sys.banner</code></li>
<li><code class="highlighter-rouge">sys.timestamp</code></li>
<li><code class="highlighter-rouge">sys.build</code></li>
<li><code class="highlighter-rouge">sys.platform</code></li>
<li><code class="highlighter-rouge">sys.ps1</code></li>
<li><code class="highlighter-rouge">sys.ps2</code></li>
<li><code class="highlighter-rouge">sys.langcode</code></li>
<li><code class="highlighter-rouge">sys.executable</code></li>
<li><code class="highlighter-rouge">sys.incdir</code></li>
<li><code class="highlighter-rouge">sys.libdir</code></li>
<li><code class="highlighter-rouge">sys.datadir</code></li>
<li><code class="highlighter-rouge">sys.moddir</code></li>
<li><code class="highlighter-rouge">sys.localdir</code></li>
<li><code class="highlighter-rouge">sys.appdir</code></li>
<li><code class="highlighter-rouge">sys.cfgdir</code></li>
<li><code class="highlighter-rouge">sys.workdir</code></li>
</ul>
<h2><span class="caption-index-2">53.3</span><a name="anchor-53-3"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">sys.echo</strong></div>
<div style="margin-bottom:1em"><code>sys.echo(flag:boolean)</code></div>
Enables or disables echo-back functionality according to flag.
</p>
<p>
<div><strong style="text-decoration:underline">sys.exit</strong></div>
<div style="margin-bottom:1em"><code>sys.exit(status?:number)</code></div>
Terminates the program with a specified status number.
</p>
<p>
<div><strong style="text-decoration:underline">sys.interactive</strong></div>
<div style="margin-bottom:1em"><code>sys.interactive()</code></div>
Enters to interactive mode.
</p>
<p>
<div><strong style="text-decoration:underline">sys.required_version</strong></div>
<div style="margin-bottom:1em"><code>sys.required_version(major:number, minor:number, patch:number)</code></div>
Raises an error if the running interpreter doesn't satisfy the required version.
</p>
{% endraw %}
