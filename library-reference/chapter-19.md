---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">19</span><a name="anchor-19"></a>glu Module</h1>
<p>
The <code>glu</code> module provides functions of GLU library.
</p>
<h2><span class="caption-index-2">19.1</span><a name="anchor-19-1"></a>Module Functions</h2>
<p>
<strong>glu.gluBeginCurve</strong>
</p>
<p>
<code>glu.gluBeginCurve(nurb:glu.Nurbs):void {block?}</code>
</p>
<p>
<strong>glu.gluBeginPolygon</strong>
</p>
<p>
<code>glu.gluBeginPolygon(tess:glu.Tesselator):void {block?}</code>
</p>
<p>
<strong>glu.gluBeginSurface</strong>
</p>
<p>
<code>glu.gluBeginSurface(nurb:glu.Nurbs):void {block?}</code>
</p>
<p>
<strong>glu.gluBeginTrim</strong>
</p>
<p>
<code>glu.gluBeginTrim(nurb:glu.Nurbs):void {block?}</code>
</p>
<p>
<strong>glu.gluBuild1DMipmaps</strong>
</p>
<p>
<code>glu.gluBuild1DMipmaps(target:number, internalFormat:number, width:number, format:number, type:number, data)</code>
</p>
<p>
<strong>glu.gluBuild1DMipmapsFromImage</strong>
</p>
<p>
<code>glu.gluBuild1DMipmapsFromImage(target:number, internalFormat:number, image:image)</code>
</p>
<p>
<strong>glu.gluBuild2DMipmaps</strong>
</p>
<p>
<code>glu.gluBuild2DMipmaps(target:number, internalFormat:number, width:number, height:number, format:number, type:number, data)</code>
</p>
<p>
<strong>glu.gluBuild2DMipmapsFromImage</strong>
</p>
<p>
<code>glu.gluBuild2DMipmapsFromImage(target:number, internalFormat:number, image:image)</code>
</p>
<p>
<strong>glu.gluCylinder</strong>
</p>
<p>
<code>glu.gluCylinder(quad:glu.Quadric, base:number, top:number, height:number, slices:number, stacks:number):void</code>
</p>
<p>
<strong>glu.gluDeleteNurbsRenderer</strong>
</p>
<p>
<code>glu.gluDeleteNurbsRenderer(nurb:glu.Nurbs):void</code>
</p>
<p>
<strong>glu.gluDeleteQuadric</strong>
</p>
<p>
<code>glu.gluDeleteQuadric(quad:glu.Quadric):void</code>
</p>
<p>
<strong>glu.gluDeleteTess</strong>
</p>
<p>
<code>glu.gluDeleteTess(tess:glu.Tesselator):void</code>
</p>
<p>
<strong>glu.gluDisk</strong>
</p>
<p>
<code>glu.gluDisk(quad:glu.Quadric, inner:number, outer:number, slices:number, loops:number):void</code>
</p>
<p>
<strong>glu.gluEndCurve</strong>
</p>
<p>
<code>glu.gluEndCurve(nurb:glu.Nurbs):void</code>
</p>
<p>
<strong>glu.gluEndPolygon</strong>
</p>
<p>
<code>glu.gluEndPolygon(tess:glu.Tesselator):void</code>
</p>
<p>
<strong>glu.gluEndSurface</strong>
</p>
<p>
<code>glu.gluEndSurface(nurb:glu.Nurbs):void</code>
</p>
<p>
<strong>glu.gluEndTrim</strong>
</p>
<p>
<code>glu.gluEndTrim(nurb:glu.Nurbs):void</code>
</p>
<p>
<strong>glu.gluErrorString</strong>
</p>
<p>
<code>glu.gluErrorString(error:number)</code>
</p>
<p>
<strong>glu.gluGetNurbsProperty</strong>
</p>
<p>
<code>glu.gluGetNurbsProperty(nurb:glu.Nurbs, property:number, data:array@float:nomap):void</code>
</p>
<p>
<strong>glu.gluGetString</strong>
</p>
<p>
<code>glu.gluGetString(name:number)</code>
</p>
<p>
<strong>glu.gluGetTessProperty</strong>
</p>
<p>
<code>glu.gluGetTessProperty(tess:glu.Tesselator, which:number, data:array@double:nomap):void</code>
</p>
<p>
<strong>glu.gluLoadSamplingMatrices</strong>
</p>
<p>
<code>glu.gluLoadSamplingMatrices(nurb:glu.Nurbs, model:array@float:nomap, perspective:array@float:nomap, view:array@int:nomap):void</code>
</p>
<p>
<strong>glu.gluLookAt</strong>
</p>
<p>
<code>glu.gluLookAt(eyeX:number, eyeY:number, eyeZ:number, centerX:number, centerY:number, centerZ:number, upX:number, upY:number, upZ:number):void</code>
</p>
<p>
<strong>glu.gluNewNurbsRenderer</strong>
</p>
<p>
<code>glu.gluNewNurbsRenderer()</code>
</p>
<p>
<strong>glu.gluNewQuadric</strong>
</p>
<p>
<code>glu.gluNewQuadric()</code>
</p>
<p>
<strong>glu.gluNewTess</strong>
</p>
<p>
<code>glu.gluNewTess()</code>
</p>
<p>
<strong>glu.gluNextContour</strong>
</p>
<p>
<code>glu.gluNextContour(tess:glu.Tesselator, type:number):void</code>
</p>
<p>
<strong>glu.gluNurbsCallback</strong>
</p>
<p>
<code>glu.gluNurbsCallback(nurbs:glu.Nurbs, which:number, func:function)</code>
</p>
<p>
<strong>glu.gluNurbsCallbackData</strong>
</p>
<p>
<code>glu.gluNurbsCallbackData(nurb:glu.Nurbs, userData):void</code>
</p>
<p>
<strong>glu.gluNurbsCallbackDataEXT</strong>
</p>
<p>
<code>glu.gluNurbsCallbackDataEXT(nurb:glu.Nurbs, userData):void</code>
</p>
<p>
<strong>glu.gluNurbsCurve</strong>
</p>
<p>
<code>glu.gluNurbsCurve(nurb:glu.Nurbs, knots:array@float:nomap, stride:number, control:array@float:nomap, order:number, type:number):void</code>
</p>
<p>
<strong>glu.gluNurbsProperty</strong>
</p>
<p>
<code>glu.gluNurbsProperty(nurb:glu.Nurbs, property:number, value:number):void</code>
</p>
<p>
<strong>glu.gluNurbsSurface</strong>
</p>
<p>
<code>glu.gluNurbsSurface(nurb:glu.Nurbs, sKnots:array@float:nomap, tKnots:array@float:nomap, sStride:number, tStride:number, control:array@float:nomap, sOrder:number, tOrder:number, type:number):void</code>
</p>
<p>
<strong>glu.gluOrtho2D</strong>
</p>
<p>
<code>glu.gluOrtho2D(left:number, right:number, bottom:number, top:number):void</code>
</p>
<p>
<strong>glu.gluPartialDisk</strong>
</p>
<p>
<code>glu.gluPartialDisk(quad:glu.Quadric, inner:number, outer:number, slices:number, loops:number, start:number, sweep:number):void</code>
</p>
<p>
<strong>glu.gluPerspective</strong>
</p>
<p>
<code>glu.gluPerspective(fovy:number, aspect:number, zNear:number, zFar:number):void</code>
</p>
<p>
<strong>glu.gluPickMatrix</strong>
</p>
<p>
<code>glu.gluPickMatrix(x:number, y:number, delX:number, delY:number, viewport:array@int:nomap):void</code>
</p>
<p>
<strong>glu.gluProject</strong>
</p>
<p>
<code>glu.gluProject(objX:number, objY:number, objZ:number, model:array@double:nomap, proj:array@double:nomap, view:array@int:nomap, winX:array@double:nomap, winY:array@double:nomap, winZ:array@double:nomap)</code>
</p>
<p>
<strong>glu.gluPwlCurve</strong>
</p>
<p>
<code>glu.gluPwlCurve(nurb:glu.Nurbs, data:array@float:nomap, stride:number, type:number):void</code>
</p>
<p>
<strong>glu.gluQuadricCallback</strong>
</p>
<p>
<code>glu.gluQuadricCallback(quad:glu.Quadric, which:number, func:function:nil):void</code>
</p>
<p>
<strong>glu.gluQuadricDrawStyle</strong>
</p>
<p>
<code>glu.gluQuadricDrawStyle(quad:glu.Quadric, draw:number):void</code>
</p>
<p>
<strong>glu.gluQuadricNormals</strong>
</p>
<p>
<code>glu.gluQuadricNormals(quad:glu.Quadric, normal:number):void</code>
</p>
<p>
<strong>glu.gluQuadricOrientation</strong>
</p>
<p>
<code>glu.gluQuadricOrientation(quad:glu.Quadric, orientation:number):void</code>
</p>
<p>
<strong>glu.gluQuadricTexture</strong>
</p>
<p>
<code>glu.gluQuadricTexture(quad:glu.Quadric, texture:boolean):void</code>
</p>
<p>
<strong>glu.gluScaleImage</strong>
</p>
<p>
<code>glu.gluScaleImage(imageIn:image, wOut:number, hOut:number)</code>
</p>
<p>
<strong>glu.gluSphere</strong>
</p>
<p>
<code>glu.gluSphere(quad:glu.Quadric, radius:number, slices:number, stacks:number):void</code>
</p>
<p>
<strong>glu.gluTessBeginContour</strong>
</p>
<p>
<code>glu.gluTessBeginContour(tess:glu.Tesselator):void {block?}</code>
</p>
<p>
<strong>glu.gluTessBeginPolygon</strong>
</p>
<p>
<code>glu.gluTessBeginPolygon(tess:glu.Tesselator, polygon_data):void {block?}</code>
</p>
<p>
<strong>glu.gluTessCallback</strong>
</p>
<p>
<code>glu.gluTessCallback(tess:glu.Tesselator, which:number, func:function):void</code>
</p>
<p>
<strong>glu.gluTessEndContour</strong>
</p>
<p>
<code>glu.gluTessEndContour(tess:glu.Tesselator):void</code>
</p>
<p>
<strong>glu.gluTessEndPolygon</strong>
</p>
<p>
<code>glu.gluTessEndPolygon(tess:glu.Tesselator):void</code>
</p>
<p>
<strong>glu.gluTessNormal</strong>
</p>
<p>
<code>glu.gluTessNormal(tess:glu.Tesselator, valueX:number, valueY:number, valueZ:number):void</code>
</p>
<p>
<strong>glu.gluTessProperty</strong>
</p>
<p>
<code>glu.gluTessProperty(tess:glu.Tesselator, which:number, data:number):void</code>
</p>
<p>
<strong>glu.gluTessVertex</strong>
</p>
<p>
<code>glu.gluTessVertex(tess:glu.Tesselator, location:array@double:nomap, vertex_data):void</code>
</p>
<p>
<strong>glu.gluUnProject</strong>
</p>
<p>
<code>glu.gluUnProject(winX:number, winY:number, winZ:number, model:array@double:nomap, proj:array@double:nomap, view:array@int:nomap, objX:array@double:nomap, objY:array@double:nomap, objZ:array@double:nomap)</code>
</p>
<p />

{% endraw %}
