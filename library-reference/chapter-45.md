---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">45</span><a name="anchor-45"></a>path Module</h1>
<h2><span class="caption-index-2">45.1</span><a name="anchor-45-1"></a>Overview</h2>
<p>
The <code>path</code> module provides functions related to path operations. This is a built-in module, so you can use it without being imported.
</p>
<p>
Below is an example to list path names that exist in the current directory.
</p>
<pre><code>println(path.dir('.'))
</code></pre>
<p>
Below is an example to list path names that exist in the current directory and its child directories.
</p>
<pre><code>println(path.walk('.'))
</code></pre>
<p>
Below is an example to list path names that matches a wild card pattern "<code>*.txt</code>".
</p>
<pre><code>println(path.glob('*.txt'))
</code></pre>
<h2><span class="caption-index-2">45.2</span><a name="anchor-45-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">path.absname</strong></div>
<div style="margin-bottom:1em"><code>path.absname(name:string):map:[uri]</code></div>
Returns an absolute path name of the given name.
</p>
<p>
<div><strong style="text-decoration:underline">path.basename</strong></div>
<div style="margin-bottom:1em"><code>path.basename(pathname:string):map</code></div>
Removes a suffix part of a path name.
</p>
<p>
<div><strong style="text-decoration:underline">path.bottom</strong></div>
<div style="margin-bottom:1em"><code>path.bottom(pathname:string):map</code></div>
Returns the last part of a path name.
</p>
<p>
<div><strong style="text-decoration:underline">path.cutbottom</strong></div>
<div style="margin-bottom:1em"><code>path.cutbottom(pathname:string):map</code></div>
Returns a path name after eliminating its bottom part.
</p>
<p>
<div><strong style="text-decoration:underline">path.dir</strong></div>
<div style="margin-bottom:1em"><code>path.dir(directory?:directory, pattern*:string):flat:map:[case,dir,file,icase,stat] {block?}</code></div>
Creates an iterator that lists item names in the specified directory. If pathname is omitted, the current directory shall be listed.
</p>
<p>
Though the default sensitiveness of character cases during pattern matching depends on the target directory, it can be changed by attributes <code>:case</code> for case-sensitive and <code>:icase</code> for case-insensitive.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">path.dirname</strong></div>
<div style="margin-bottom:1em"><code>path.dirname(pathname:string):map</code></div>
Splits a pathname by a directory separator and returns a directory name part.
</p>
<p>
<div><strong style="text-decoration:underline">path.exists</strong></div>
<div style="margin-bottom:1em"><code>path.exists(pathname:string):map</code></div>
Returns true if the specified file exists in a file system.
</p>
<p>
<div><strong style="text-decoration:underline">path.extname</strong></div>
<div style="margin-bottom:1em"><code>path.extname(pathname:string):map</code></div>
Extracts a suffix part of a path name.
</p>
<p>
<div><strong style="text-decoration:underline">path.filename</strong></div>
<div style="margin-bottom:1em"><code>path.filename(pathname:string):map</code></div>
Splits a pathname by a directory separator and returns a file name part.
</p>
<p>
<div><strong style="text-decoration:underline">path.glob</strong></div>
<div style="margin-bottom:1em"><code>path.glob(pattern:string):flat:map:[case,dir,file,icase,stat] {block?}</code></div>
Creates an iterator for item names that match with a pattern supporting UNIX shell-style wild cards. In default, case of characters is distinguished.
</p>
<p>
Though the default sensitiveness of character cases during pattern matching depends on the current platform, it can be changed by attributes <code>:case</code> for case-sensitive and <code>:icase</code> for case-insensitive.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<div><strong style="text-decoration:underline">path.join</strong></div>
<div style="margin-bottom:1em"><code>path.join(paths+:string):map:[uri]</code></div>
Returns a path name that joins given strings with directory separators.
</p>
<p>
<div><strong style="text-decoration:underline">path.match</strong></div>
<div style="margin-bottom:1em"><code>path.match(pattern:string, name:string):map:[case,icase]</code></div>
Returns true if a name matches with a pattern that supports UNIX shell-style wild cards.
</p>
<p>
Though the default sensitiveness of character cases depends on the current platform, it can be changed by attributes <code>:case</code> for case-sensitive and <code>:icase</code> for case-insensitive.
</p>
<p>
<div><strong style="text-decoration:underline">path.regulate</strong></div>
<div style="margin-bottom:1em"><code>path.regulate(name:string):map:[uri]</code></div>
Returns a regulated path name of the given name.
</p>
<p>
<div><strong style="text-decoration:underline">path.split</strong></div>
<div style="margin-bottom:1em"><code>path.split(pathname:string):map:[bottom]</code></div>
Splits a pathname by a directory separator and returns a list containing a directory name as the first element and a base name as the second one. This has the same result as calling path.dirname() and path.filename().
</p>
<p>
<div><strong style="text-decoration:underline">path.splitext</strong></div>
<div style="margin-bottom:1em"><code>path.splitext(pathname:string):map</code></div>
Splits a pathname by a dot character indicating a beginning of an extension and returns a list containing a path name without an extention and an extention part.
</p>
<p>
<div><strong style="text-decoration:underline">path.stat</strong></div>
<div style="margin-bottom:1em"><code>path.stat(directory:directory):map</code></div>
Returns a stat object associated with the specified item.
</p>
<p>
<div><strong style="text-decoration:underline">path.walk</strong></div>
<div style="margin-bottom:1em"><code>path.walk(directory?:directory, maxdepth?:number, pattern*:string):flat:map:[case,dir,file,icase,stat] {block?}</code></div>
Creates an iterator that recursively lists item names under the specified directory. If <code>directory</code> is omitted, search starts at the current directory.
</p>
<p>
Though the default sensitiveness of character cases during pattern matching depends on the target directory, it can be changed by attributes <code>:case</code> for case-sensitive and <code>:icase</code> for case-insensitive.
</p>
<p>
In default, this returns an iterator as its result value. Specifying the following attributes would customize the returned value:
</p>
<ul>
<li><code>:iter</code> .. An iterator. This is the default behavior.</li>
<li><code>:xiter</code> .. An iterator that eliminates <code>nil</code> from its elements.</li>
<li><code>:list</code> .. A list.</li>
<li><code>:xlist</code> .. A list that eliminates <code>nil</code> from its elements.</li>
<li><code>:set</code> ..  A list that eliminates duplicated values from its elements.</li>
<li><code>:xset</code> .. A list that eliminates duplicated values and <code>nil</code> from its elements.</li>
</ul>
<p>
See the chapter of Mapping Process in Gura Language Manual for the detail.
</p>
<p>
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p />

{% endraw %}
