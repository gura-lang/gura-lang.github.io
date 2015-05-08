---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">44</span><a name="anchor-44"></a>sys Module</h1>
<p>
The <code>sys</code> module provides system-related information. This is a built-in module, so you can use it without being imported.
</p>
<h2><span class="caption-index-2">44.1</span><a name="anchor-44-1"></a>Module Variable</h2>
<ul>
<li><code>sys.argv</code></li>
<li><code>sys.path</code></li>
<li><code>sys.maindir</code></li>
<li><code>sys.version</code></li>
<li><code>sys.banner</code></li>
<li><code>sys.build</code></li>
<li><code>sys.platform</code></li>
<li><code>sys.ps1</code></li>
<li><code>sys.ps2</code></li>
<li><code>sys.langcode</code></li>
<li><code>sys.executable</code></li>
<li><code>sys.incdir</code></li>
<li><code>sys.libdir</code></li>
<li><code>sys.datadir</code></li>
<li><code>sys.moddir</code></li>
<li><code>sys.localdir</code></li>
<li><code>sys.appdir</code></li>
<li><code>sys.cfgdir</code></li>
<li><code>sys.workdir</code></li>
</ul>
<h2><span class="caption-index-2">44.2</span><a name="anchor-44-2"></a>Module Function</h2>
<p>
<strong>sys.echo</strong>
</p>
<p>
<code>sys.echo(flag:boolean)</code>
</p>
<p>
Enables or disables echo-back functionality according to flag.
</p>
<p>
<strong>sys.exit</strong>
</p>
<p>
<code>sys.exit(status?:number)</code>
</p>
<p>
Terminates the program with a specified status number.
</p>
<p>
<strong>sys.required_version</strong>
</p>
<p>
<code>sys.required_version(major:number, minor:number, patch:number)</code>
</p>
<p>
Raises an error if the running interpreter doesn't satisfy the required version.
</p>
<p />

{% endraw %}
