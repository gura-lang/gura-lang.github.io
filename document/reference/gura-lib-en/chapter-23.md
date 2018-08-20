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
<div><strong style="text-decoration:underline">glu.gluBeginCurve</strong></div>
<div style="margin-bottom:1em"><code>glu.gluBeginCurve(nurb:glu.Nurbs):void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluBeginPolygon</strong></div>
<div style="margin-bottom:1em"><code>glu.gluBeginPolygon(tess:glu.Tesselator):void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluBeginSurface</strong></div>
<div style="margin-bottom:1em"><code>glu.gluBeginSurface(nurb:glu.Nurbs):void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluBeginTrim</strong></div>
<div style="margin-bottom:1em"><code>glu.gluBeginTrim(nurb:glu.Nurbs):void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluBuild1DMipmaps</strong></div>
<div style="margin-bottom:1em"><code>glu.gluBuild1DMipmaps(target:number, internalFormat:number, width:number, format:number, type:number, data:array:nomap)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluBuild1DMipmapsFromImage</strong></div>
<div style="margin-bottom:1em"><code>glu.gluBuild1DMipmapsFromImage(target:number, internalFormat:number, image:image)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluBuild2DMipmaps</strong></div>
<div style="margin-bottom:1em"><code>glu.gluBuild2DMipmaps(target:number, internalFormat:number, width:number, height:number, format:number, type:number, data:array:nomap)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluBuild2DMipmapsFromImage</strong></div>
<div style="margin-bottom:1em"><code>glu.gluBuild2DMipmapsFromImage(target:number, internalFormat:number, image:image)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluCylinder</strong></div>
<div style="margin-bottom:1em"><code>glu.gluCylinder(quad:glu.Quadric, base:number, top:number, height:number, slices:number, stacks:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluDeleteNurbsRenderer</strong></div>
<div style="margin-bottom:1em"><code>glu.gluDeleteNurbsRenderer(nurb:glu.Nurbs):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluDeleteQuadric</strong></div>
<div style="margin-bottom:1em"><code>glu.gluDeleteQuadric(quad:glu.Quadric):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluDeleteTess</strong></div>
<div style="margin-bottom:1em"><code>glu.gluDeleteTess(tess:glu.Tesselator):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluDisk</strong></div>
<div style="margin-bottom:1em"><code>glu.gluDisk(quad:glu.Quadric, inner:number, outer:number, slices:number, loops:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluEndCurve</strong></div>
<div style="margin-bottom:1em"><code>glu.gluEndCurve(nurb:glu.Nurbs):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluEndPolygon</strong></div>
<div style="margin-bottom:1em"><code>glu.gluEndPolygon(tess:glu.Tesselator):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluEndSurface</strong></div>
<div style="margin-bottom:1em"><code>glu.gluEndSurface(nurb:glu.Nurbs):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluEndTrim</strong></div>
<div style="margin-bottom:1em"><code>glu.gluEndTrim(nurb:glu.Nurbs):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluErrorString</strong></div>
<div style="margin-bottom:1em"><code>glu.gluErrorString(error:number)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluGetNurbsProperty</strong></div>
<div style="margin-bottom:1em"><code>glu.gluGetNurbsProperty(nurb:glu.Nurbs, property:number, data:array@float:nomap):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluGetString</strong></div>
<div style="margin-bottom:1em"><code>glu.gluGetString(name:number)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluGetTessProperty</strong></div>
<div style="margin-bottom:1em"><code>glu.gluGetTessProperty(tess:glu.Tesselator, which:number, data:array@double:nomap):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluLoadSamplingMatrices</strong></div>
<div style="margin-bottom:1em"><code>glu.gluLoadSamplingMatrices(nurb:glu.Nurbs, model:array@float:nomap, perspective:array@float:nomap, view:array@int32:nomap):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluLookAt</strong></div>
<div style="margin-bottom:1em"><code>glu.gluLookAt(eyeX:number, eyeY:number, eyeZ:number, centerX:number, centerY:number, centerZ:number, upX:number, upY:number, upZ:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluNewNurbsRenderer</strong></div>
<div style="margin-bottom:1em"><code>glu.gluNewNurbsRenderer()</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluNewQuadric</strong></div>
<div style="margin-bottom:1em"><code>glu.gluNewQuadric()</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluNewTess</strong></div>
<div style="margin-bottom:1em"><code>glu.gluNewTess()</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluNextContour</strong></div>
<div style="margin-bottom:1em"><code>glu.gluNextContour(tess:glu.Tesselator, type:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluNurbsCallback</strong></div>
<div style="margin-bottom:1em"><code>glu.gluNurbsCallback(nurbs:glu.Nurbs, which:number, func:function)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluNurbsCallbackData</strong></div>
<div style="margin-bottom:1em"><code>glu.gluNurbsCallbackData(nurb:glu.Nurbs, userData):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluNurbsCallbackDataEXT</strong></div>
<div style="margin-bottom:1em"><code>glu.gluNurbsCallbackDataEXT(nurb:glu.Nurbs, userData):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluNurbsCurve</strong></div>
<div style="margin-bottom:1em"><code>glu.gluNurbsCurve(nurb:glu.Nurbs, knots:array@float:nomap, stride:number, control:array@float:nomap, order:number, type:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluNurbsProperty</strong></div>
<div style="margin-bottom:1em"><code>glu.gluNurbsProperty(nurb:glu.Nurbs, property:number, value:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluNurbsSurface</strong></div>
<div style="margin-bottom:1em"><code>glu.gluNurbsSurface(nurb:glu.Nurbs, sKnots:array@float:nomap, tKnots:array@float:nomap, sStride:number, tStride:number, control:array@float:nomap, sOrder:number, tOrder:number, type:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluOrtho2D</strong></div>
<div style="margin-bottom:1em"><code>glu.gluOrtho2D(left:number, right:number, bottom:number, top:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluPartialDisk</strong></div>
<div style="margin-bottom:1em"><code>glu.gluPartialDisk(quad:glu.Quadric, inner:number, outer:number, slices:number, loops:number, start:number, sweep:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluPerspective</strong></div>
<div style="margin-bottom:1em"><code>glu.gluPerspective(fovy:number, aspect:number, zNear:number, zFar:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluPickMatrix</strong></div>
<div style="margin-bottom:1em"><code>glu.gluPickMatrix(x:number, y:number, delX:number, delY:number, viewport:array@int32:nomap):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluProject</strong></div>
<div style="margin-bottom:1em"><code>glu.gluProject(objX:number, objY:number, objZ:number, model:array@double:nomap, proj:array@double:nomap, view:array@int32:nomap, winX:array@double:nomap, winY:array@double:nomap, winZ:array@double:nomap)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluPwlCurve</strong></div>
<div style="margin-bottom:1em"><code>glu.gluPwlCurve(nurb:glu.Nurbs, data:array@float:nomap, stride:number, type:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluQuadricCallback</strong></div>
<div style="margin-bottom:1em"><code>glu.gluQuadricCallback(quad:glu.Quadric, which:number, func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluQuadricDrawStyle</strong></div>
<div style="margin-bottom:1em"><code>glu.gluQuadricDrawStyle(quad:glu.Quadric, draw:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluQuadricNormals</strong></div>
<div style="margin-bottom:1em"><code>glu.gluQuadricNormals(quad:glu.Quadric, normal:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluQuadricOrientation</strong></div>
<div style="margin-bottom:1em"><code>glu.gluQuadricOrientation(quad:glu.Quadric, orientation:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluQuadricTexture</strong></div>
<div style="margin-bottom:1em"><code>glu.gluQuadricTexture(quad:glu.Quadric, texture:boolean):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluScaleImage</strong></div>
<div style="margin-bottom:1em"><code>glu.gluScaleImage(imageIn:image, wOut:number, hOut:number)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluSphere</strong></div>
<div style="margin-bottom:1em"><code>glu.gluSphere(quad:glu.Quadric, radius:number, slices:number, stacks:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluTessBeginContour</strong></div>
<div style="margin-bottom:1em"><code>glu.gluTessBeginContour(tess:glu.Tesselator):void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluTessBeginPolygon</strong></div>
<div style="margin-bottom:1em"><code>glu.gluTessBeginPolygon(tess:glu.Tesselator, polygon_data):void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluTessCallback</strong></div>
<div style="margin-bottom:1em"><code>glu.gluTessCallback(tess:glu.Tesselator, which:number, func:function):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluTessEndContour</strong></div>
<div style="margin-bottom:1em"><code>glu.gluTessEndContour(tess:glu.Tesselator):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluTessEndPolygon</strong></div>
<div style="margin-bottom:1em"><code>glu.gluTessEndPolygon(tess:glu.Tesselator):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluTessNormal</strong></div>
<div style="margin-bottom:1em"><code>glu.gluTessNormal(tess:glu.Tesselator, valueX:number, valueY:number, valueZ:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluTessProperty</strong></div>
<div style="margin-bottom:1em"><code>glu.gluTessProperty(tess:glu.Tesselator, which:number, data:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluTessVertex</strong></div>
<div style="margin-bottom:1em"><code>glu.gluTessVertex(tess:glu.Tesselator, location:array@double:nomap, vertex_data):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glu.gluUnProject</strong></div>
<div style="margin-bottom:1em"><code>glu.gluUnProject(winX:number, winY:number, winZ:number, model:array@double:nomap, proj:array@double:nomap, view:array@int32:nomap, objX:array@double:nomap, objY:array@double:nomap, objZ:array@double:nomap)</code></div>

</p>
{% endraw %}
