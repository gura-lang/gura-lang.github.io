---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-43.html#naviitem-selected
nextpage: chapter-45.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">44</span>os Module</h1>
<h2><span class="caption-index-2">44.1</span><a name="anchor-44-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">os</code> module provides functions that are specific to each OS environment. This is a built-in module, so you can use it without being imported.
</p>
<h2><span class="caption-index-2">44.2</span><a name="anchor-44-2"></a>Module Function</h2>
<div class="mb-2"><code>os.clock() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
Returns the time duration in second since the system has started.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would calculate how much time has been spent during evaluating the block.
</p>

</div>
<div class="mb-2"><code>os.exec(pathname:string, args*:string):map:[fork]</code></div>
<div class="mb-2 ml-4">
Executes the specified executable file.
</div>
<div class="mb-2"><code>os.fromnative(buff:binary):map</code></div>
<div class="mb-2 ml-4">
Converts binary data that includes OS's native string into Gura's regulated string.
</div>
<div class="mb-2"><code>os.getenv(name:string, default?:string):map</code></div>
<div class="mb-2 ml-4">
Returns the value of an environment variable.
</div>
<div class="mb-2"><code>os.putenv(name:string, value:string):void</code></div>
<div class="mb-2 ml-4">
Set the value of an environment variable.
</div>
<div class="mb-2"><code>os.redirect(stdin:stream:nil:r, stdout:stream:nil:w, stderr?:stream:w) {block?}</code></div>
<div class="mb-2 ml-4">
Modifies variables <code class="highlighter-rouge">os.stdin</code>, <code class="highlighter-rouge">os.stdout</code> and <code class="highlighter-rouge">os.stderr</code> with values of arguments. When <code class="highlighter-rouge">block</code> is specified, the modification only has effect within the block.
</div>
<div class="mb-2"><code>os.sleep(secs:number)</code></div>
<div class="mb-2 ml-4">
Sleeps for a time specified in seconds.
</div>
<div class="mb-2"><code>os.symlink(src:string, tgt:string):map:void</code></div>
<div class="mb-2 ml-4">
Creates a symbol link.
</div>
<div class="mb-2"><code>os.tonative(str:string):map</code></div>
<div class="mb-2 ml-4">
Converts Gura's regulated string into binary data that includes OS's native string.
</div>
<div class="mb-2"><code>os.unsetenv(name:string):void</code></div>
<div class="mb-2 ml-4">
Unset an environment variable.
</div>
{% endraw %}
