---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-19.html#naviitem-selected
nextpage: chapter-21.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">20</span>freetype Module</h1>
<h2><span class="caption-index-2">20.1</span><a name="anchor-20-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">freetype</code> module provices measures to access vectorized font data using freetype library. To utilize it, import the <code class="highlighter-rouge">freetype</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<h2><span class="caption-index-2">20.2</span><a name="anchor-20-2"></a>Module Function</h2>
<div class="h5">freetype.sysfontpath</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.sysfontpath(name:string):map</code></div>
<h2><span class="caption-index-2">20.3</span><a name="anchor-20-3"></a>freetype.BBox Class</h2>
<h2><span class="caption-index-2">20.4</span><a name="anchor-20-4"></a>freetype.BDF_Property Class</h2>
<h2><span class="caption-index-2">20.5</span><a name="anchor-20-5"></a>freetype.Bitmap Class</h2>
<h3><span class="caption-index-3">20.5.1</span><a name="anchor-20-5-1"></a>Method</h3>
<div class="h5">freetype.Bitmap#Embolden</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Bitmap#Embolden(strength:number):reduce</code></div>
<h2><span class="caption-index-2">20.6</span><a name="anchor-20-6"></a>freetype.CharMap Class</h2>
<h3><span class="caption-index-3">20.6.1</span><a name="anchor-20-6-1"></a>Method</h3>
<div class="h5">freetype.CharMap#Get_Index</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.CharMap#Get_Index()</code></div>
<h2><span class="caption-index-2">20.7</span><a name="anchor-20-7"></a>freetype.FTC_CMapCache Class</h2>
<h2><span class="caption-index-2">20.8</span><a name="anchor-20-8"></a>freetype.FTC_ImageCache Class</h2>
<h2><span class="caption-index-2">20.9</span><a name="anchor-20-9"></a>freetype.FTC_ImageType Class</h2>
<h2><span class="caption-index-2">20.10</span><a name="anchor-20-10"></a>freetype.FTC_Manager Class</h2>
<h2><span class="caption-index-2">20.11</span><a name="anchor-20-11"></a>freetype.FTC_Node Class</h2>
<h2><span class="caption-index-2">20.12</span><a name="anchor-20-12"></a>freetype.FTC_SBit Class</h2>
<h2><span class="caption-index-2">20.13</span><a name="anchor-20-13"></a>freetype.FTC_SBitCache Class</h2>
<h2><span class="caption-index-2">20.14</span><a name="anchor-20-14"></a>freetype.FTC_Scaler Class</h2>
<h2><span class="caption-index-2">20.15</span><a name="anchor-20-15"></a>freetype.Face Class</h2>
<h3><span class="caption-index-3">20.15.1</span><a name="anchor-20-15-1"></a>Constructor</h3>
<div class="h5">freetype.Face</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Face(stream:stream, face_index:number =&gt; 0):map {block?}</code></div>
<h3><span class="caption-index-3">20.15.2</span><a name="anchor-20-15-2"></a>Method</h3>
<div class="h5">freetype.Face#CheckTrueTypePatents</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Face#CheckTrueTypePatents()</code></div>
<div class="h5">freetype.Face#Get_Advance</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Face#Get_Advance(glyph_index:number, load_flags:number)</code></div>
<div class="h5">freetype.Face#Get_Advances</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Face#Get_Advances(glyph_index_start:number, count:number, load_flags:number)</code></div>
<div class="h5">freetype.Face#Get_Glyph_Name</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Face#Get_Glyph_Name(glyph_index:number)</code></div>
<div class="h5">freetype.Face#Get_Postscript_Name</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Face#Get_Postscript_Name()</code></div>
<div class="h5">freetype.Face#Get_Kerning</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Face#Get_Kerning(left_glyph:number, right_glyph:number, kern_mode:number)</code></div>
<div class="h5">freetype.Face#Load_Char</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Face#Load_Char(char_code:number, load_flags:number):reduce</code></div>
<div class="h5">freetype.Face#Load_Glyph</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Face#Load_Glyph(glyph_index:number, load_flags:number):reduce</code></div>
<div class="h5">freetype.Face#Set_Charmap</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Face#Set_Charmap(charmap:freetype.CharMap):reduce</code></div>
<div class="h5">freetype.Face#Set_Pixel_Sizes</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Face#Set_Pixel_Sizes(pixel_width:number, pixel_height:number):reduce</code></div>
<h2><span class="caption-index-2">20.16</span><a name="anchor-20-16"></a>freetype.Glyph Class</h2>
<h3><span class="caption-index-3">20.16.1</span><a name="anchor-20-16-1"></a>Method</h3>
<div class="h5">freetype.Glyph#Copy</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Glyph#Copy()</code></div>
<div class="h5">freetype.Glyph#Stroke</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Glyph#Stroke(stroker:freetype.Stroker):reduce</code></div>
<div class="h5">freetype.Glyph#StrokeBorder</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Glyph#StrokeBorder(stroker:freetype.Stroker, inside:boolean):reduce</code></div>
<h2><span class="caption-index-2">20.17</span><a name="anchor-20-17"></a>freetype.GlyphSlot Class</h2>
<h3><span class="caption-index-3">20.17.1</span><a name="anchor-20-17-1"></a>Method</h3>
<div class="h5">freetype.GlyphSlot#Get_Glyph</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.GlyphSlot#Get_Glyph()</code></div>
<div class="h5">freetype.GlyphSlot#Render</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.GlyphSlot#Render(render_mode:number):reduce</code></div>
<h2><span class="caption-index-2">20.18</span><a name="anchor-20-18"></a>freetype.Matrix Class</h2>
<h3><span class="caption-index-3">20.18.1</span><a name="anchor-20-18-1"></a>Constructor</h3>
<div class="h5">freetype.Matrix</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Matrix(array:array@double):map {block?}</code></div>
<h3><span class="caption-index-3">20.18.2</span><a name="anchor-20-18-2"></a>Method</h3>
<div class="h5">freetype.Matrix#Multiply</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Matrix#Multiply(matrix:freetype.Matrix):reduce</code></div>
<div class="h5">freetype.Matrix#Invert</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Matrix#Invert():reduce</code></div>
<h2><span class="caption-index-2">20.19</span><a name="anchor-20-19"></a>freetype.Outline Class</h2>
<h3><span class="caption-index-3">20.19.1</span><a name="anchor-20-19-1"></a>Method</h3>
<div class="h5">freetype.Outline#Translate</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Outline#Translate(xOffset:freetype.Matrix, yOffset:freetype.Matrix):reduce</code></div>
<div class="h5">freetype.Outline#Transform</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Outline#Transform(matrix:freetype.Matrix):reduce</code></div>
<div class="h5">freetype.Outline#Embolden</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Outline#Embolden(strength:number):reduce</code></div>
<div class="h5">freetype.Outline#Reverse</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Outline#Reverse():reduce</code></div>
<h2><span class="caption-index-2">20.20</span><a name="anchor-20-20"></a>freetype.Raster Class</h2>
<h2><span class="caption-index-2">20.21</span><a name="anchor-20-21"></a>freetype.Span Class</h2>
<h2><span class="caption-index-2">20.22</span><a name="anchor-20-22"></a>freetype.Stroker Class</h2>
<h3><span class="caption-index-3">20.22.1</span><a name="anchor-20-22-1"></a>Constructor</h3>
<div class="h5">freetype.Stroker</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Stroker():map {block?}</code></div>
<h3><span class="caption-index-3">20.22.2</span><a name="anchor-20-22-2"></a>Method</h3>
<div class="h5">freetype.Stroker#BeginSubPath</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Stroker#BeginSubPath(to:freetype.Vector, open:boolean):reduce</code></div>
<h2><span class="caption-index-2">20.23</span><a name="anchor-20-23"></a>freetype.Vector Class</h2>
<h3><span class="caption-index-3">20.23.1</span><a name="anchor-20-23-1"></a>Constructor</h3>
<div class="h5">freetype.Vector</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Vector(x:number, y:number):map {block?}</code></div>
<h3><span class="caption-index-3">20.23.2</span><a name="anchor-20-23-2"></a>Method</h3>
<div class="h5">freetype.Vector#Length</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Vector#Length()</code></div>
<div class="h5">freetype.Vector#Transform</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.Vector#Transform(matrix:freetype.Matrix):reduce</code></div>
<h2><span class="caption-index-2">20.24</span><a name="anchor-20-24"></a>freetype.font Class</h2>
<h2><span class="caption-index-2">20.25</span><a name="anchor-20-25"></a>Constructor</h2>
<div class="h5">freetype.font</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.font(face:freetype.Face):map {block?}</code></div>
<h3><span class="caption-index-3">20.25.1</span><a name="anchor-20-25-1"></a>Method</h3>
<div class="h5">freetype.font#cleardeco</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.font#cleardeco():reduce</code></div>
<div class="h5">freetype.font#drawtext</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.font#drawtext(image:image, x:number, y:number, str:string):map:reduce {block?}</code></div>
<p>
Draws a text on the image.
</p>
<div class="h5">freetype.font#calcsize</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.font#calcsize(str:string):map</code></div>
<div class="h5">freetype.font#calcbbox</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>freetype.font#calcbbox(x:number, y:number, str:string):map</code></div>
<h2><span class="caption-index-2">20.26</span><a name="anchor-20-26"></a>Extension to image Class</h2>
<p>
This module extends the <code class="highlighter-rouge">image</code> class with methods described here.
</p>
<div class="h5">image#drawtext</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>image#drawtext(font:freetype.font, x:number, y:number, str:string):map:reduce {block?}</code></div>
<p>
Draws a text on the image.
</p>
<h2><span class="caption-index-2">20.27</span><a name="anchor-20-27"></a>Thanks</h2>
<p>
This module uses FreeType library which is distributed in the following site:
</p>
<p>
<a href="http://www.freetype.org/">http://www.freetype.org/</a>
</p>
{% endraw %}
