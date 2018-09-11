---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-22.html#naviitem-selected
nextpage: chapter-24.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">23</span>glu Module</h1>
<h2><span class="caption-index-2">23.1</span><a name="anchor-23-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">glu</code> module provides functions of GLU library.
</p>
<h2><span class="caption-index-2">23.2</span><a name="anchor-23-2"></a>Module Function</h2>
<p>
The <code class="highlighter-rouge">glu</code> modules provides folloing functions:
</p>
<div class="mb-2"><code>glu.gluBeginCurve(nurb:glu.Nurbs):void {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluBeginPolygon(tess:glu.Tesselator):void {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluBeginSurface(nurb:glu.Nurbs):void {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluBeginTrim(nurb:glu.Nurbs):void {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluBuild1DMipmaps(target:number, internalFormat:number, width:number, format:number, type:number, data:array:nomap)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluBuild1DMipmapsFromImage(target:number, internalFormat:number, image:image)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluBuild2DMipmaps(target:number, internalFormat:number, width:number, height:number, format:number, type:number, data:array:nomap)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluBuild2DMipmapsFromImage(target:number, internalFormat:number, image:image)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluCylinder(quad:glu.Quadric, base:number, top:number, height:number, slices:number, stacks:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluDeleteNurbsRenderer(nurb:glu.Nurbs):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluDeleteQuadric(quad:glu.Quadric):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluDeleteTess(tess:glu.Tesselator):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluDisk(quad:glu.Quadric, inner:number, outer:number, slices:number, loops:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluEndCurve(nurb:glu.Nurbs):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluEndPolygon(tess:glu.Tesselator):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluEndSurface(nurb:glu.Nurbs):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluEndTrim(nurb:glu.Nurbs):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluErrorString(error:number)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluGetNurbsProperty(nurb:glu.Nurbs, property:number, data:array@float:nomap):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluGetString(name:number)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluGetTessProperty(tess:glu.Tesselator, which:number, data:array@double:nomap):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluLoadSamplingMatrices(nurb:glu.Nurbs, model:array@float:nomap, perspective:array@float:nomap, view:array@int32:nomap):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluLookAt(eyeX:number, eyeY:number, eyeZ:number, centerX:number, centerY:number, centerZ:number, upX:number, upY:number, upZ:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluNewNurbsRenderer()</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluNewQuadric()</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluNewTess()</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluNextContour(tess:glu.Tesselator, type:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluNurbsCallback(nurbs:glu.Nurbs, which:number, func:function)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluNurbsCallbackData(nurb:glu.Nurbs, userData):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluNurbsCallbackDataEXT(nurb:glu.Nurbs, userData):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluNurbsCurve(nurb:glu.Nurbs, knots:array@float:nomap, stride:number, control:array@float:nomap, order:number, type:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluNurbsProperty(nurb:glu.Nurbs, property:number, value:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluNurbsSurface(nurb:glu.Nurbs, sKnots:array@float:nomap, tKnots:array@float:nomap, sStride:number, tStride:number, control:array@float:nomap, sOrder:number, tOrder:number, type:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluOrtho2D(left:number, right:number, bottom:number, top:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluPartialDisk(quad:glu.Quadric, inner:number, outer:number, slices:number, loops:number, start:number, sweep:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluPerspective(fovy:number, aspect:number, zNear:number, zFar:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluPickMatrix(x:number, y:number, delX:number, delY:number, viewport:array@int32:nomap):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluProject(objX:number, objY:number, objZ:number, model:array@double:nomap, proj:array@double:nomap, view:array@int32:nomap, winX:array@double:nomap, winY:array@double:nomap, winZ:array@double:nomap)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluPwlCurve(nurb:glu.Nurbs, data:array@float:nomap, stride:number, type:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluQuadricCallback(quad:glu.Quadric, which:number, func:function:nil):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluQuadricDrawStyle(quad:glu.Quadric, draw:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluQuadricNormals(quad:glu.Quadric, normal:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluQuadricOrientation(quad:glu.Quadric, orientation:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluQuadricTexture(quad:glu.Quadric, texture:boolean):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluScaleImage(imageIn:image, wOut:number, hOut:number)</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluSphere(quad:glu.Quadric, radius:number, slices:number, stacks:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluTessBeginContour(tess:glu.Tesselator):void {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluTessBeginPolygon(tess:glu.Tesselator, polygon_data):void {block?}</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluTessCallback(tess:glu.Tesselator, which:number, func:function):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluTessEndContour(tess:glu.Tesselator):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluTessEndPolygon(tess:glu.Tesselator):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluTessNormal(tess:glu.Tesselator, valueX:number, valueY:number, valueZ:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluTessProperty(tess:glu.Tesselator, which:number, data:number):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluTessVertex(tess:glu.Tesselator, location:array@double:nomap, vertex_data):void</code></div>
<div class="mb-2 ml-4">

</div>
<div class="mb-2"><code>glu.gluUnProject(winX:number, winY:number, winZ:number, model:array@double:nomap, proj:array@double:nomap, view:array@int32:nomap, objX:array@double:nomap, objY:array@double:nomap, objZ:array@double:nomap)</code></div>
<div class="mb-2 ml-4">

</div>
{% endraw %}
