---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">44</span><a name="anchor-44"></a>os Module</h1>
<h2><span class="caption-index-2">44.1</span><a name="anchor-44-1"></a>Overview</h2>
<p>
The <code>os</code> module provides functions that are specific to each OS environment. This is a built-in module, so you can use it without being imported.
</p>
<h2><span class="caption-index-2">44.2</span><a name="anchor-44-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">os.clock</strong></div>
<div style="margin-bottom:1em"><code>os.clock() {block?}</code></div>
Returns the time duration in second since the system has started.
</p>
<p>
If <code>block</code> is specified, it would calculate how much time has been spent during evaluating the block.
</p>
<p>
<div><strong style="text-decoration:underline">os.exec</strong></div>
<div style="margin-bottom:1em"><code>os.exec(pathname:string, args*:string):map:[fork]</code></div>
Executes the specified executable file.
</p>
<p>
<div><strong style="text-decoration:underline">os.fromnative</strong></div>
<div style="margin-bottom:1em"><code>os.fromnative(buff:binary):map</code></div>
Converts binary data that includes OS's native string into Gura's regulated string.
</p>
<p>
<div><strong style="text-decoration:underline">os.getenv</strong></div>
<div style="margin-bottom:1em"><code>os.getenv(name:string, default?:string):map</code></div>
Returns the value of an environment variable.
</p>
<p>
<div><strong style="text-decoration:underline">os.putenv</strong></div>
<div style="margin-bottom:1em"><code>os.putenv(name:string, value:string):void</code></div>
Set the value of an environment variable.
</p>
<p>
<div><strong style="text-decoration:underline">os.redirect</strong></div>
<div style="margin-bottom:1em"><code>os.redirect(stdin:stream:nil:r, stdout:stream:nil:w, stderr?:stream:w) {block?}</code></div>
Modifies variables <code>os.stdin</code>, <code>os.stdout</code> and <code>os.stderr</code> with values of arguments. When <code>block</code> is specified, the modification only has effect within the block.
</p>
<p>
<div><strong style="text-decoration:underline">os.sleep</strong></div>
<div style="margin-bottom:1em"><code>os.sleep(secs:number)</code></div>
Sleeps for a time specified in seconds.
</p>
<p>
<div><strong style="text-decoration:underline">os.symlink</strong></div>
<div style="margin-bottom:1em"><code>os.symlink(src:string, tgt:string):map:void</code></div>
Creates a symbol link.
</p>
<p>
<div><strong style="text-decoration:underline">os.tonative</strong></div>
<div style="margin-bottom:1em"><code>os.tonative(str:string):map</code></div>
Converts Gura's regulated string into binary data that includes OS's native string.
</p>
<p>
<div><strong style="text-decoration:underline">os.unsetenv</strong></div>
<div style="margin-bottom:1em"><code>os.unsetenv(name:string):void</code></div>
Unset an environment variable.
</p>
<p />

{% endraw %}
