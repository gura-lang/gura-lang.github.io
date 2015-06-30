---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">19</span><a name="anchor-19"></a>freetype Module</h1>
<p>
The <code>freetype</code> module provices measures to access vectorized font data using freetype library. To utilize it, import the <code>freetype</code> module using <code>import</code> function.
</p>
<h2><span class="caption-index-2">19.1</span><a name="anchor-19-1"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">freetype.sysfontpath</strong></div>
<div style="margin-bottom:1em"><code>freetype.sysfontpath(name?:string):map</code></div>

</p>
<h2><span class="caption-index-2">19.2</span><a name="anchor-19-2"></a>freetype.BBox Class</h2>
<h2><span class="caption-index-2">19.3</span><a name="anchor-19-3"></a>freetype.BDF_Property Class</h2>
<h2><span class="caption-index-2">19.4</span><a name="anchor-19-4"></a>freetype.Bitmap Class</h2>
<h3><span class="caption-index-3">19.4.1</span><a name="anchor-19-4-1"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">freetype.Bitmap#Embolden</strong></div>
<div style="margin-bottom:1em"><code>freetype.Bitmap#Embolden(strength:number):reduce</code></div>

</p>
<h2><span class="caption-index-2">19.5</span><a name="anchor-19-5"></a>freetype.CharMap Class</h2>
<h3><span class="caption-index-3">19.5.1</span><a name="anchor-19-5-1"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">freetype.CharMap#Get_Index</strong></div>
<div style="margin-bottom:1em"><code>freetype.CharMap#Get_Index()</code></div>

</p>
<h2><span class="caption-index-2">19.6</span><a name="anchor-19-6"></a>freetype.FTC_CMapCache Class</h2>
<h2><span class="caption-index-2">19.7</span><a name="anchor-19-7"></a>freetype.FTC_ImageCache Class</h2>
<h2><span class="caption-index-2">19.8</span><a name="anchor-19-8"></a>freetype.FTC_ImageType Class</h2>
<h2><span class="caption-index-2">19.9</span><a name="anchor-19-9"></a>freetype.FTC_Manager Class</h2>
<h2><span class="caption-index-2">19.10</span><a name="anchor-19-10"></a>freetype.FTC_Node Class</h2>
<h2><span class="caption-index-2">19.11</span><a name="anchor-19-11"></a>freetype.FTC_SBit Class</h2>
<h2><span class="caption-index-2">19.12</span><a name="anchor-19-12"></a>freetype.FTC_SBitCache Class</h2>
<h2><span class="caption-index-2">19.13</span><a name="anchor-19-13"></a>freetype.FTC_Scaler Class</h2>
<h2><span class="caption-index-2">19.14</span><a name="anchor-19-14"></a>freetype.Face Class</h2>
<h3><span class="caption-index-3">19.14.1</span><a name="anchor-19-14-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">freetype.Face</strong></div>
<div style="margin-bottom:1em"><code>freetype.Face(stream:stream, face_index:number =&gt; 0):map {block?}</code></div>

</p>
<h3><span class="caption-index-3">19.14.2</span><a name="anchor-19-14-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">freetype.Face#CheckTrueTypePatents</strong></div>
<div style="margin-bottom:1em"><code>freetype.Face#CheckTrueTypePatents()</code></div>
<div><strong style="text-decoration:underline">freetype.Face#Get_Advance</strong></div>
<div style="margin-bottom:1em"><code>freetype.Face#Get_Advance(glyph_index:number, load_flags:number)</code></div>
<div><strong style="text-decoration:underline">freetype.Face#Get_Advances</strong></div>
<div style="margin-bottom:1em"><code>freetype.Face#Get_Advances(glyph_index_start:number, count:number, load_flags:number)</code></div>
<div><strong style="text-decoration:underline">freetype.Face#Get_Glyph_Name</strong></div>
<div style="margin-bottom:1em"><code>freetype.Face#Get_Glyph_Name(glyph_index:number)</code></div>
<div><strong style="text-decoration:underline">freetype.Face#Get_Postscript_Name</strong></div>
<div style="margin-bottom:1em"><code>freetype.Face#Get_Postscript_Name()</code></div>
<div><strong style="text-decoration:underline">freetype.Face#Get_Kerning</strong></div>
<div style="margin-bottom:1em"><code>freetype.Face#Get_Kerning(left_glyph:number, right_glyph:number, kern_mode:number)</code></div>
<div><strong style="text-decoration:underline">freetype.Face#Load_Char</strong></div>
<div style="margin-bottom:1em"><code>freetype.Face#Load_Char(char_code:number, load_flags:number):reduce</code></div>
<div><strong style="text-decoration:underline">freetype.Face#Load_Glyph</strong></div>
<div style="margin-bottom:1em"><code>freetype.Face#Load_Glyph(glyph_index:number, load_flags:number):reduce</code></div>
<div><strong style="text-decoration:underline">freetype.Face#Set_Charmap</strong></div>
<div style="margin-bottom:1em"><code>freetype.Face#Set_Charmap(charmap:freetype.CharMap):reduce</code></div>
<div><strong style="text-decoration:underline">freetype.Face#Set_Pixel_Sizes</strong></div>
<div style="margin-bottom:1em"><code>freetype.Face#Set_Pixel_Sizes(pixel_width:number, pixel_height:number):reduce</code></div>

</p>
<h2><span class="caption-index-2">19.15</span><a name="anchor-19-15"></a>freetype.Glyph Class</h2>
<h3><span class="caption-index-3">19.15.1</span><a name="anchor-19-15-1"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">freetype.Glyph#Copy</strong></div>
<div style="margin-bottom:1em"><code>freetype.Glyph#Copy()</code></div>
<div><strong style="text-decoration:underline">freetype.Glyph#Stroke</strong></div>
<div style="margin-bottom:1em"><code>freetype.Glyph#Stroke(stroker:freetype.Stroker):reduce</code></div>
<div><strong style="text-decoration:underline">freetype.Glyph#StrokeBorder</strong></div>
<div style="margin-bottom:1em"><code>freetype.Glyph#StrokeBorder(stroker:freetype.Stroker, inside:boolean):reduce</code></div>

</p>
<h2><span class="caption-index-2">19.16</span><a name="anchor-19-16"></a>freetype.GlyphSlot Class</h2>
<h3><span class="caption-index-3">19.16.1</span><a name="anchor-19-16-1"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">freetype.GlyphSlot#Get_Glyph</strong></div>
<div style="margin-bottom:1em"><code>freetype.GlyphSlot#Get_Glyph()</code></div>
<div><strong style="text-decoration:underline">freetype.GlyphSlot#Render</strong></div>
<div style="margin-bottom:1em"><code>freetype.GlyphSlot#Render(render_mode:number):reduce</code></div>

</p>
<h2><span class="caption-index-2">19.17</span><a name="anchor-19-17"></a>freetype.Matrix Class</h2>
<h3><span class="caption-index-3">19.17.1</span><a name="anchor-19-17-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">freetype.Matrix</strong></div>
<div style="margin-bottom:1em"><code>freetype.Matrix(matrix:matrix):map {block?}</code></div>

</p>
<h3><span class="caption-index-3">19.17.2</span><a name="anchor-19-17-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">freetype.Matrix#Multiply</strong></div>
<div style="margin-bottom:1em"><code>freetype.Matrix#Multiply(matrix:freetype.Matrix):reduce</code></div>
<div><strong style="text-decoration:underline">freetype.Matrix#Invert</strong></div>
<div style="margin-bottom:1em"><code>freetype.Matrix#Invert():reduce</code></div>

</p>
<h2><span class="caption-index-2">19.18</span><a name="anchor-19-18"></a>freetype.Outline Class</h2>
<h3><span class="caption-index-3">19.18.1</span><a name="anchor-19-18-1"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">freetype.Outline#Translate</strong></div>
<div style="margin-bottom:1em"><code>freetype.Outline#Translate(xOffset:freetype.Matrix, yOffset:freetype.Matrix):reduce</code></div>
<div><strong style="text-decoration:underline">freetype.Outline#Transform</strong></div>
<div style="margin-bottom:1em"><code>freetype.Outline#Transform(matrix:freetype.Matrix):reduce</code></div>
<div><strong style="text-decoration:underline">freetype.Outline#Embolden</strong></div>
<div style="margin-bottom:1em"><code>freetype.Outline#Embolden(strength:number):reduce</code></div>
<div><strong style="text-decoration:underline">freetype.Outline#Reverse</strong></div>
<div style="margin-bottom:1em"><code>freetype.Outline#Reverse():reduce</code></div>

</p>
<h2><span class="caption-index-2">19.19</span><a name="anchor-19-19"></a>freetype.Raster Class</h2>
<h2><span class="caption-index-2">19.20</span><a name="anchor-19-20"></a>freetype.Span Class</h2>
<h2><span class="caption-index-2">19.21</span><a name="anchor-19-21"></a>freetype.Stroker Class</h2>
<h3><span class="caption-index-3">19.21.1</span><a name="anchor-19-21-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">freetype.Stroker</strong></div>
<div style="margin-bottom:1em"><code>freetype.Stroker():map {block?}</code></div>

</p>
<h3><span class="caption-index-3">19.21.2</span><a name="anchor-19-21-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">freetype.Stroker#BeginSubPath</strong></div>
<div style="margin-bottom:1em"><code>freetype.Stroker#BeginSubPath(to:freetype.Vector, open:boolean):reduce</code></div>

</p>
<h2><span class="caption-index-2">19.22</span><a name="anchor-19-22"></a>freetype.Vector Class</h2>
<h3><span class="caption-index-3">19.22.1</span><a name="anchor-19-22-1"></a>Constructor</h3>
<p>
<div><strong style="text-decoration:underline">freetype.Vector</strong></div>
<div style="margin-bottom:1em"><code>freetype.Vector(x:number, y:number):map {block?}</code></div>

</p>
<h3><span class="caption-index-3">19.22.2</span><a name="anchor-19-22-2"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">freetype.Vector#Length</strong></div>
<div style="margin-bottom:1em"><code>freetype.Vector#Length()</code></div>
<div><strong style="text-decoration:underline">freetype.Vector#Transform</strong></div>
<div style="margin-bottom:1em"><code>freetype.Vector#Transform(matrix:freetype.Matrix):reduce</code></div>

</p>
<h2><span class="caption-index-2">19.23</span><a name="anchor-19-23"></a>freetype.font Class</h2>
<h2><span class="caption-index-2">19.24</span><a name="anchor-19-24"></a>Constructor</h2>
<p>
<div><strong style="text-decoration:underline">freetype.font</strong></div>
<div style="margin-bottom:1em"><code>freetype.font(face:freetype.Face):map {block?}</code></div>

</p>
<h3><span class="caption-index-3">19.24.1</span><a name="anchor-19-24-1"></a>Method</h3>
<p>
<div><strong style="text-decoration:underline">freetype.font#cleardeco</strong></div>
<div style="margin-bottom:1em"><code>freetype.font#cleardeco():reduce</code></div>
<div><strong style="text-decoration:underline">freetype.font#drawtext</strong></div>
<div style="margin-bottom:1em"><code>freetype.font#drawtext(image:image, x:number, y:number, str:string):map:reduce {block?}</code></div>
Draws a text on the image.
</p>
<p>
<div><strong style="text-decoration:underline">freetype.font#calcsize</strong></div>
<div style="margin-bottom:1em"><code>freetype.font#calcsize(str:string):map</code></div>
<div><strong style="text-decoration:underline">freetype.font#calcbbox</strong></div>
<div style="margin-bottom:1em"><code>freetype.font#calcbbox(x:number, y:number, str:string):map</code></div>

</p>
<h2><span class="caption-index-2">19.25</span><a name="anchor-19-25"></a>Extension to image Class</h2>
<p>
This module extends the <code>image</code> class with methods described here.
</p>
<p>
<div><strong style="text-decoration:underline">image#drawtext</strong></div>
<div style="margin-bottom:1em"><code>image#drawtext(font:freetype.font, x:number, y:number, str:string):map:reduce {block?}</code></div>
Draws a text on the image.
</p>
<h2><span class="caption-index-2">19.26</span><a name="anchor-19-26"></a>Thanks</h2>
<p>
This module uses FreeType library which is distributed in the following site:
</p>
<p>
<a href="http://www.freetype.org/">http://www.freetype.org/</a>
</p>
<p />

{% endraw %}
