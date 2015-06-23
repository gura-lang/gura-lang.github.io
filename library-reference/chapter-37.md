---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">37</span><a name="anchor-37"></a>os Module</h1>
<p>
The <code>os</code> module provides functions that are specific to each OS environment. This is a built-in module, so you can use it without being imported.
</p>
<h2><span class="caption-index-2">37.1</span><a name="anchor-37-1"></a>Module Function</h2>
<p>
<strong>os.clock</strong>
</p>
<p>
<code>os.clock()</code>
</p>
<p>
<strong>os.exec</strong>
</p>
<p>
<code>os.exec(pathname:string, args*:string):map:[fork]</code>
</p>
<p>
Executes the specified executable file.
</p>
<p>
<strong>os.fromnative</strong>
</p>
<p>
<code>os.fromnative(buff:binary):map</code>
</p>
<p>
Converts binary data that includes OS's native string into Gura's regulated string.
</p>
<p>
<strong>os.getenv</strong>
</p>
<p>
<code>os.getenv(name:string, default?:string):map</code>
</p>
<p>
Returns the value of an environment variable.
</p>
<p>
<strong>os.putenv</strong>
</p>
<p>
<code>os.putenv(name:string, value:string):void</code>
</p>
<p>
Set the value of an environment variable.
</p>
<p>
<strong>os.redirect</strong>
</p>
<p>
<code>os.redirect(stdin:stream:nil:r, stdout:stream:nil:w, stderr?:stream:w) {block?}</code>
</p>
<p>
Modifies variables <code>os.stdin</code>, <code>os.stdout</code> and <code>os.stderr</code> with values of arguments. When <code>block</code> is specified, the modification only has effect within the block.
</p>
<p>
<strong>os.sleep</strong>
</p>
<p>
<code>os.sleep(secs:number)</code>
</p>
<p>
Sleeps for a time specified in seconds.
</p>
<p>
<strong>os.symlink</strong>
</p>
<p>
<code>os.symlink(src:string, tgt:string):map:void</code>
</p>
<p>
Creates a symbol link.
</p>
<p>
<strong>os.tonative</strong>
</p>
<p>
<code>os.tonative(str:string):map</code>
</p>
<p>
Converts Gura's regulated string into binary data that includes OS's native string.
</p>
<p>
<strong>os.unsetenv</strong>
</p>
<p>
<code>os.unsetenv(name:string):void</code>
</p>
<p>
Unset an environment variable.
</p>
<p />

{% endraw %}
