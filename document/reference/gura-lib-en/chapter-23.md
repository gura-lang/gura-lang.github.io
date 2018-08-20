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
<div class="h5">glu.gluBeginCurve</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluBeginCurve(nurb:glu.Nurbs):void {block?}</code></div>

</p>
<p>
<div class="h5">glu.gluBeginPolygon</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluBeginPolygon(tess:glu.Tesselator):void {block?}</code></div>

</p>
<p>
<div class="h5">glu.gluBeginSurface</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluBeginSurface(nurb:glu.Nurbs):void {block?}</code></div>

</p>
<p>
<div class="h5">glu.gluBeginTrim</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluBeginTrim(nurb:glu.Nurbs):void {block?}</code></div>

</p>
<p>
<div class="h5">glu.gluBuild1DMipmaps</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluBuild1DMipmaps(target:number, internalFormat:number, width:number, format:number, type:number, data:array:nomap)</code></div>

</p>
<p>
<div class="h5">glu.gluBuild1DMipmapsFromImage</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluBuild1DMipmapsFromImage(target:number, internalFormat:number, image:image)</code></div>

</p>
<p>
<div class="h5">glu.gluBuild2DMipmaps</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluBuild2DMipmaps(target:number, internalFormat:number, width:number, height:number, format:number, type:number, data:array:nomap)</code></div>

</p>
<p>
<div class="h5">glu.gluBuild2DMipmapsFromImage</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluBuild2DMipmapsFromImage(target:number, internalFormat:number, image:image)</code></div>

</p>
<p>
<div class="h5">glu.gluCylinder</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluCylinder(quad:glu.Quadric, base:number, top:number, height:number, slices:number, stacks:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluDeleteNurbsRenderer</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluDeleteNurbsRenderer(nurb:glu.Nurbs):void</code></div>

</p>
<p>
<div class="h5">glu.gluDeleteQuadric</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluDeleteQuadric(quad:glu.Quadric):void</code></div>

</p>
<p>
<div class="h5">glu.gluDeleteTess</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluDeleteTess(tess:glu.Tesselator):void</code></div>

</p>
<p>
<div class="h5">glu.gluDisk</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluDisk(quad:glu.Quadric, inner:number, outer:number, slices:number, loops:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluEndCurve</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluEndCurve(nurb:glu.Nurbs):void</code></div>

</p>
<p>
<div class="h5">glu.gluEndPolygon</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluEndPolygon(tess:glu.Tesselator):void</code></div>

</p>
<p>
<div class="h5">glu.gluEndSurface</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluEndSurface(nurb:glu.Nurbs):void</code></div>

</p>
<p>
<div class="h5">glu.gluEndTrim</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluEndTrim(nurb:glu.Nurbs):void</code></div>

</p>
<p>
<div class="h5">glu.gluErrorString</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluErrorString(error:number)</code></div>

</p>
<p>
<div class="h5">glu.gluGetNurbsProperty</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluGetNurbsProperty(nurb:glu.Nurbs, property:number, data:array@float:nomap):void</code></div>

</p>
<p>
<div class="h5">glu.gluGetString</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluGetString(name:number)</code></div>

</p>
<p>
<div class="h5">glu.gluGetTessProperty</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluGetTessProperty(tess:glu.Tesselator, which:number, data:array@double:nomap):void</code></div>

</p>
<p>
<div class="h5">glu.gluLoadSamplingMatrices</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluLoadSamplingMatrices(nurb:glu.Nurbs, model:array@float:nomap, perspective:array@float:nomap, view:array@int32:nomap):void</code></div>

</p>
<p>
<div class="h5">glu.gluLookAt</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluLookAt(eyeX:number, eyeY:number, eyeZ:number, centerX:number, centerY:number, centerZ:number, upX:number, upY:number, upZ:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluNewNurbsRenderer</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluNewNurbsRenderer()</code></div>

</p>
<p>
<div class="h5">glu.gluNewQuadric</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluNewQuadric()</code></div>

</p>
<p>
<div class="h5">glu.gluNewTess</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluNewTess()</code></div>

</p>
<p>
<div class="h5">glu.gluNextContour</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluNextContour(tess:glu.Tesselator, type:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluNurbsCallback</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluNurbsCallback(nurbs:glu.Nurbs, which:number, func:function)</code></div>

</p>
<p>
<div class="h5">glu.gluNurbsCallbackData</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluNurbsCallbackData(nurb:glu.Nurbs, userData):void</code></div>

</p>
<p>
<div class="h5">glu.gluNurbsCallbackDataEXT</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluNurbsCallbackDataEXT(nurb:glu.Nurbs, userData):void</code></div>

</p>
<p>
<div class="h5">glu.gluNurbsCurve</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluNurbsCurve(nurb:glu.Nurbs, knots:array@float:nomap, stride:number, control:array@float:nomap, order:number, type:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluNurbsProperty</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluNurbsProperty(nurb:glu.Nurbs, property:number, value:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluNurbsSurface</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluNurbsSurface(nurb:glu.Nurbs, sKnots:array@float:nomap, tKnots:array@float:nomap, sStride:number, tStride:number, control:array@float:nomap, sOrder:number, tOrder:number, type:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluOrtho2D</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluOrtho2D(left:number, right:number, bottom:number, top:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluPartialDisk</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluPartialDisk(quad:glu.Quadric, inner:number, outer:number, slices:number, loops:number, start:number, sweep:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluPerspective</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluPerspective(fovy:number, aspect:number, zNear:number, zFar:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluPickMatrix</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluPickMatrix(x:number, y:number, delX:number, delY:number, viewport:array@int32:nomap):void</code></div>

</p>
<p>
<div class="h5">glu.gluProject</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluProject(objX:number, objY:number, objZ:number, model:array@double:nomap, proj:array@double:nomap, view:array@int32:nomap, winX:array@double:nomap, winY:array@double:nomap, winZ:array@double:nomap)</code></div>

</p>
<p>
<div class="h5">glu.gluPwlCurve</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluPwlCurve(nurb:glu.Nurbs, data:array@float:nomap, stride:number, type:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluQuadricCallback</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluQuadricCallback(quad:glu.Quadric, which:number, func:function:nil):void</code></div>

</p>
<p>
<div class="h5">glu.gluQuadricDrawStyle</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluQuadricDrawStyle(quad:glu.Quadric, draw:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluQuadricNormals</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluQuadricNormals(quad:glu.Quadric, normal:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluQuadricOrientation</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluQuadricOrientation(quad:glu.Quadric, orientation:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluQuadricTexture</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluQuadricTexture(quad:glu.Quadric, texture:boolean):void</code></div>

</p>
<p>
<div class="h5">glu.gluScaleImage</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluScaleImage(imageIn:image, wOut:number, hOut:number)</code></div>

</p>
<p>
<div class="h5">glu.gluSphere</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluSphere(quad:glu.Quadric, radius:number, slices:number, stacks:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluTessBeginContour</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluTessBeginContour(tess:glu.Tesselator):void {block?}</code></div>

</p>
<p>
<div class="h5">glu.gluTessBeginPolygon</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluTessBeginPolygon(tess:glu.Tesselator, polygon_data):void {block?}</code></div>

</p>
<p>
<div class="h5">glu.gluTessCallback</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluTessCallback(tess:glu.Tesselator, which:number, func:function):void</code></div>

</p>
<p>
<div class="h5">glu.gluTessEndContour</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluTessEndContour(tess:glu.Tesselator):void</code></div>

</p>
<p>
<div class="h5">glu.gluTessEndPolygon</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluTessEndPolygon(tess:glu.Tesselator):void</code></div>

</p>
<p>
<div class="h5">glu.gluTessNormal</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluTessNormal(tess:glu.Tesselator, valueX:number, valueY:number, valueZ:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluTessProperty</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluTessProperty(tess:glu.Tesselator, which:number, data:number):void</code></div>

</p>
<p>
<div class="h5">glu.gluTessVertex</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluTessVertex(tess:glu.Tesselator, location:array@double:nomap, vertex_data):void</code></div>

</p>
<p>
<div class="h5">glu.gluUnProject</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glu.gluUnProject(winX:number, winY:number, winZ:number, model:array@double:nomap, proj:array@double:nomap, view:array@int32:nomap, objX:array@double:nomap, objY:array@double:nomap, objZ:array@double:nomap)</code></div>

</p>
{% endraw %}
