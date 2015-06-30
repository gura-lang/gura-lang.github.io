---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">7</span><a name="anchor-7"></a>argopt Module</h1>
<p>
The <code>argopt</code> module provides measure to parse option strings in an argument list given through the command line.
</p>
<p>
Below is an example:
</p>
<pre><code>import(argopt)

argopt.Parser {|p|
    p.addParam('text', 't')
    p.addFlag('test')
    p.addFlag('bold', 'b')
    try {
        [cfg, argv] = p.parse(sys.argv)
    } catch {|e|
        println(e.text)
        sys.exit(1)
    }
}
</code></pre>
<h2><span class="caption-index-2">7.1</span><a name="anchor-7-1"></a>argopt.Parser Class</h2>
<h3><span class="caption-index-3">7.1.1</span><a name="anchor-7-1-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">argopt.Parser.Parser</strong></div>
<div style="margin-bottom:1em"><code>argopt.Parser.Parser() {block?}</code></div>

</p>
<h3><span class="caption-index-3">7.1.2</span><a name="anchor-7-1-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">argopt.Parser#parse</strong></div>
<div style="margin-bottom:1em"><code>argopt.Parser#parse(argv[]:string)</code></div>
Parses an argument list which is usually the value of <code>sys.argv</code> given by <code>sys</code> module.
</p>
<p>
It returns the result in a format <code>[cfg, argv]</code> where <code>cfg</code> is a <code>dict</code> instance containing parameter values and <code>argv</code> a list of arguments that have not been parsed as options.
</p>
<p>
<div><strong style="text-decoration:underline">argopt.Parser#addParam</strong></div>
<div style="margin-bottom:1em"><code>argopt.Parser#addParam(longName:string, shortName?:string, help?:string, helpValue?:string, defValue?:string)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">argopt.Parser#addFlag</strong></div>
<div style="margin-bottom:1em"><code>argopt.Parser#addFlag(longName:string, shortName?:string, help?:string)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">argopt.Parser#formatHelp</strong></div>
<div style="margin-bottom:1em"><code>argopt.Parser#formatHelp(longNameFlag:boolean =&gt; true, shortNameFlag:boolean =&gt; true):[linefeed]</code></div>

</p>
<p />

{% endraw %}
