---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-12.html#naviitem-selected
nextpage: chapter-14.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">13</span>conio Module</h1>
<h2><span class="caption-index-2">13.1</span><a name="anchor-13-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">conio</code> module provides following measures to work on a console screen:
</p>
<ul>
<li>Moves the cursor where texts are printed.</li>
<li>Changes text colors.</li>
<li>Retrieves console size.</li>
<li>Waits for keyboard input.</li>
</ul>
<p>
To utilize it, import the <code class="highlighter-rouge">conio</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<p>
Below is an example to print a frame around a console:
</p>
<pre class="highlight"><code>import(conio)

conio.clear()
[w, h] = conio.getwinsize()
conio.moveto(0, 0) {
    print('*' * w)
}
conio.moveto(0, 1 .. (h - 2)) {
    print('*', ' ' * (w - 2), '*')
}
conio.moveto(0, h - 1) {
    print('*' * w)
}
conio.waitkey():raise
</code></pre>
<h2><span class="caption-index-2">13.2</span><a name="anchor-13-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">conio.clear</strong></div>
<div style="margin-bottom:1em"><code>conio.clear(region?:symbol):void</code></div>
Clears the screen.
</p>
<p>
In default, it clears whole the screen. Argument <code class="highlighter-rouge">region</code> that takes one of the symbols below would specify the region to be cleared.
</p>
<ul>
<li><code class="highlighter-rouge">`line</code> .. clears characters in the line where the cursor exists.</li>
<li><code class="highlighter-rouge">`left</code> .. clears characters on the left side of the cursor.</li>
<li><code class="highlighter-rouge">`right</code> .. clears characters on the right side of the cursor.</li>
<li><code class="highlighter-rouge">`top</code> .. clears characters on the above side of the cursor.</li>
<li><code class="highlighter-rouge">`bottom</code> .. clears characters on the below side of the cursor.</li>
</ul>
<p>
<div><strong style="text-decoration:underline">conio.getwinsize</strong></div>
<div style="margin-bottom:1em"><code>conio.getwinsize()</code></div>
Returns the screen size as a list <code class="highlighter-rouge">[width, height]</code>.
</p>
<p>
<div><strong style="text-decoration:underline">conio.setcolor</strong></div>
<div style="margin-bottom:1em"><code>conio.setcolor(fg:symbol:nil, bg?:symbol):map:void {block?}</code></div>
Sets foreground and background color of text by specifying a color symbol. Available color symbols are listed below:
</p>
<ul>
<li><code class="highlighter-rouge">`black</code></li>
<li><code class="highlighter-rouge">`blue</code></li>
<li><code class="highlighter-rouge">`green</code></li>
<li><code class="highlighter-rouge">`aqua</code></li>
<li><code class="highlighter-rouge">`cyan</code></li>
<li><code class="highlighter-rouge">`red</code></li>
<li><code class="highlighter-rouge">`purple</code></li>
<li><code class="highlighter-rouge">`magenta</code></li>
<li><code class="highlighter-rouge">`yellow</code></li>
<li><code class="highlighter-rouge">`white</code></li>
<li><code class="highlighter-rouge">`gray</code></li>
<li><code class="highlighter-rouge">`bright_blue</code></li>
<li><code class="highlighter-rouge">`bright_green</code></li>
<li><code class="highlighter-rouge">`bright_aqua</code></li>
<li><code class="highlighter-rouge">`bright_cyan</code></li>
<li><code class="highlighter-rouge">`bright_red</code></li>
<li><code class="highlighter-rouge">`bright_purple</code></li>
<li><code class="highlighter-rouge">`bright_magenta</code></li>
<li><code class="highlighter-rouge">`bright_yellow</code></li>
<li><code class="highlighter-rouge">`bright_white</code></li>
</ul>
<p>
If <code class="highlighter-rouge">fg</code> is set to nil, the foreground color remains unchanged. If <code class="highlighter-rouge">bg</code> is omitted or set to nil, the background color remains unchanged.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, the color is changed before evaluating the block, and then gets back to what has been set when done.
</p>
<p>
<div><strong style="text-decoration:underline">conio.moveto</strong></div>
<div style="margin-bottom:1em"><code>conio.moveto(x:number, y:number):map:void {block?}</code></div>
Moves cursor to the specified position. The most top-left position on the screen is represented as <code class="highlighter-rouge">0, 0</code>.
</p>
<p>
If <code class="highlighter-rouge">block</code> is specified, the cursor is moved before evaluating the block, and then gets back to where it has been when done.
</p>
<p>
<div><strong style="text-decoration:underline">conio.waitkey</strong></div>
<div style="margin-bottom:1em"><code>conio.waitkey():[raise]</code></div>
Waits for a keyboard input and returns a character code number associated with the key.
</p>
<p>
If <code class="highlighter-rouge">:raise</code> attribute is specified, hitting <code class="highlighter-rouge">Ctrl-C</code> issues a terminating signal that causes the program done.
</p>
<p>
Character code numbers of some of the special keys are defined as below:
</p>
<ul>
<li><code class="highlighter-rouge">conio.K_BACKSPACE</code></li>
<li><code class="highlighter-rouge">conio.K_TAB</code></li>
<li><code class="highlighter-rouge">conio.K_RETURN</code></li>
<li><code class="highlighter-rouge">conio.K_ESCAPE</code></li>
<li><code class="highlighter-rouge">conio.K_SPACE</code></li>
<li><code class="highlighter-rouge">conio.K_UP</code></li>
<li><code class="highlighter-rouge">conio.K_DOWN</code></li>
<li><code class="highlighter-rouge">conio.K_RIGHT</code></li>
<li><code class="highlighter-rouge">conio.K_LEFT</code></li>
<li><code class="highlighter-rouge">conio.K_INSERT</code></li>
<li><code class="highlighter-rouge">conio.K_HOME</code></li>
<li><code class="highlighter-rouge">conio.K_END</code></li>
<li><code class="highlighter-rouge">conio.K_PAGEUP</code></li>
<li><code class="highlighter-rouge">conio.K_PAGEDOWN</code></li>
<li><code class="highlighter-rouge">conio.K_DELETE</code></li>
</ul>
{% endraw %}
