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
<p>
<div class="h5">os.clock</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>os.clock() {block?}</code></div>
Returns the time duration in second since the system has started.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, it would calculate how much time has been spent during evaluating the block.
</p>
<p>
<div class="h5">os.exec</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>os.exec(pathname:string, args*:string):map:[fork]</code></div>
Executes the specified executable file.
</p>
<p>
<div class="h5">os.fromnative</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>os.fromnative(buff:binary):map</code></div>
Converts binary data that includes OS's native string into Gura's regulated string.
</p>
<p>
<div class="h5">os.getenv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>os.getenv(name:string, default?:string):map</code></div>
Returns the value of an environment variable.
</p>
<p>
<div class="h5">os.putenv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>os.putenv(name:string, value:string):void</code></div>
Set the value of an environment variable.
</p>
<p>
<div class="h5">os.redirect</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>os.redirect(stdin:stream:nil:r, stdout:stream:nil:w, stderr?:stream:w) {block?}</code></div>
Modifies variables <code class="highlighter-rouge">os.stdin</code>, <code class="highlighter-rouge">os.stdout</code> and <code class="highlighter-rouge">os.stderr</code> with values of arguments. When <code class="highlighter-rouge">block</code> is specified, the modification only has effect within the block.
</p>
<p>
<div class="h5">os.sleep</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>os.sleep(secs:number)</code></div>
Sleeps for a time specified in seconds.
</p>
<p>
<div class="h5">os.symlink</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>os.symlink(src:string, tgt:string):map:void</code></div>
Creates a symbol link.
</p>
<p>
<div class="h5">os.tonative</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>os.tonative(str:string):map</code></div>
Converts Gura's regulated string into binary data that includes OS's native string.
</p>
<p>
<div class="h5">os.unsetenv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>os.unsetenv(name:string):void</code></div>
Unset an environment variable.
</p>
{% endraw %}
