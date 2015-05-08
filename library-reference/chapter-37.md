---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">37</span><a name="anchor-37"></a>path Module</h1>
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
<h2><span class="caption-index-2">37.1</span><a name="anchor-37-1"></a>Module Function</h2>
<p>
<strong>path.absname</strong>
</p>
<p>
<code>path.absname(name:string):map:[uri]</code>
</p>
<p>
Returns an absolute path name of the given name.
</p>
<p>
<strong>path.basename</strong>
</p>
<p>
<code>path.basename(pathname:string):map</code>
</p>
<p>
Removes a suffix part of a path name.
</p>
<p>
<strong>path.bottom</strong>
</p>
<p>
<code>path.bottom(pathname:string):map</code>
</p>
<p>
Returns the last part of a path name.
</p>
<p>
<strong>path.cutbottom</strong>
</p>
<p>
<code>path.cutbottom(pathname:string):map</code>
</p>
<p>
Returns a path name after eliminating its bottom part.
</p>
<p>
<strong>path.dir</strong>
</p>
<p>
<code>path.dir(directory?:directory, pattern*:string):map:flat:[dir,file,stat] {block?}</code>
</p>
<p>
Creates an iterator that lists item names in the specified directory. If pathname is omitted, the current directory shall be listed. In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
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
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>path.dirname</strong>
</p>
<p>
<code>path.dirname(pathname:string):map</code>
</p>
<p>
Splits a pathname by a directory separator and returns a directory name part.
</p>
<p>
<strong>path.exists</strong>
</p>
<p>
<code>path.exists(pathname:string):map</code>
</p>
<p>
Returns true if the specified file exists in a file system.
</p>
<p>
<strong>path.extname</strong>
</p>
<p>
<code>path.extname(pathname:string):map</code>
</p>
<p>
Extracts a suffix part of a path name.
</p>
<p>
<strong>path.filename</strong>
</p>
<p>
<code>path.filename(pathname:string):map</code>
</p>
<p>
Splits a pathname by a directory separator and returns a file name part.
</p>
<p>
<strong>path.glob</strong>
</p>
<p>
<code>path.glob(pattern:string):map:flat:[dir,file,stat] {block?}</code>
</p>
<p>
Creates an iterator for item names that match with a pattern supporting UNIX shell-style wild cards. In default, case of characters is distinguished. In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
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
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p>
<strong>path.join</strong>
</p>
<p>
<code>path.join(paths+:string):map:[uri]</code>
</p>
<p>
Returns a path name that joins given strings with directory separators.
</p>
<p>
<strong>path.match</strong>
</p>
<p>
<code>path.match(pattern:string, name:string):map</code>
</p>
<p>
Returns true if a name matches with a pattern that supports UNIX shell-style wild cards. In default, case of characters is distinguished.
</p>
<p>
<strong>path.regulate</strong>
</p>
<p>
<code>path.regulate(name:string):map:[uri]</code>
</p>
<p>
Returns a regulated path name of the given name.
</p>
<p>
<strong>path.split</strong>
</p>
<p>
<code>path.split(pathname:string):map:[bottom]</code>
</p>
<p>
Splits a pathname by a directory separator and returns a list containing a directory name as the first element and a base name as the second one. This has the same result as calling path.dirname() and path.filename().
</p>
<p>
<strong>path.splitext</strong>
</p>
<p>
<code>path.splitext(pathname:string):map</code>
</p>
<p>
Splits a pathname by a dot character indicating a beginning of an extension and returns a list containing a path name without an extention and an extention part.
</p>
<p>
<strong>path.stat</strong>
</p>
<p>
<code>path.stat(directory:directory):map</code>
</p>
<p>
Returns a stat object associated with the specified item.
</p>
<p>
<strong>path.walk</strong>
</p>
<p>
<code>path.walk(directory?:directory, maxdepth?:number, pattern*:string):map:flat:[dir,file,stat] {block?}</code>
</p>
<p>
Creates an iterator that recursively lists item names under the specified directory. If pathname is omitted, search starts at the current directory In default, this returns an iterator as its result value. Specifying the following attributes would convert it into other formats:
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
If a block is specified, it would be evaluated repeatingly with block parameters <code>|value, idx:number|</code> where <code>value</code> is the iterated value and <code>idx</code> the loop index starting from zero. In this case, the last evaluated value of the block would be the result value. If one of the attributes listed above is specified, an iterator or a list of the evaluated value would be returned.
</p>
<p />

{% endraw %}
