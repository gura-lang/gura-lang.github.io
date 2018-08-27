---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-42.html#naviitem-selected
nextpage: chapter-44.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">43</span>opengl Module</h1>
<h2><span class="caption-index-2">43.1</span><a name="anchor-43-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">opengl</code> module provides functions of OpenGL library.
</p>
<h2><span class="caption-index-2">43.2</span><a name="anchor-43-2"></a>Module Function</h2>
<div class="mb-2"><code>opengl.glAccum(op:number, value:number):map:void</code></div>
<div class="mb-2 ml-4">
<p>
operate on the accumulation buffer
</p>
</div>
<div class="mb-2"><code>opengl.glAlphaFunc(func:number, ref:number):map:void</code></div>
<div class="mb-2 ml-4">
<p>
specify the alpha test function
</p>
</div>
<div class="mb-2"><code>opengl.glAreTexturesResident(textures:array@uint32:nomap):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
determine if textures are loaded in texture memory
</p>
</div>
<div class="mb-2"><code>opengl.glArrayElement(i:number):map:void</code></div>
<div class="mb-2 ml-4">
<p>
render a vertex using the specified vertex array element
</p>
</div>
<div class="mb-2"><code>opengl.glBegin(mode:number):map:void {block?}</code></div>
<div class="mb-2 ml-4">
<p>
delimit the vertices of a primitive or a group of like primitives
</p>
</div>
<div class="mb-2"><code>opengl.glBindTexture(target:number, texture:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glBitmap(width:number, height:number, xorig:number, yorig:number, xmove:number, ymove:number, bitmap:array@uint8:nil:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glBlendFunc(sfactor:number, dfactor:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glCallList(list:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glCallLists(type:number, lists[]:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glClear(mask:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glClearAccum(red:number, green:number, blue:number, alpha:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glClearColor(red:number, green:number, blue:number, alpha:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glClearDepth(depth:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glClearIndex(c:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glClearStencil(s:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glClipPlane(plane:number, equation:array@double:nomap):map:void {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3b(red:number, green:number, blue:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3bv(v:array@int8:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3d(red:number, green:number, blue:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3f(red:number, green:number, blue:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3i(red:number, green:number, blue:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3s(red:number, green:number, blue:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3ub(red:number, green:number, blue:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3ubv(v:array@uint8:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3ui(red:number, green:number, blue:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3uiv(v:array@uint32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3us(red:number, green:number, blue:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor3usv(v:array@uint16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4b(red:number, green:number, blue:number, alpha:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4bv(v:array@int8:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4d(red:number, green:number, blue:number, alpha:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4f(red:number, green:number, blue:number, alpha:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4i(red:number, green:number, blue:number, alpha:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4s(red:number, green:number, blue:number, alpha:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4ub(red:number, green:number, blue:number, alpha:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4ubv(v:array@uint8:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4ui(red:number, green:number, blue:number, alpha:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4uiv(v:array@uint32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4us(red:number, green:number, blue:number, alpha:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColor4usv(v:array@uint16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColorMask(red:boolean, green:boolean, blue:boolean, alpha:boolean):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glColorMaterial(face:number, mode:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glCopyPixels(x:number, y:number, width:number, height:number, type:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glCopyTexImage1D(target:number, level:number, internalformat:number, x:number, y:number, width:number, border:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glCopyTexImage2D(target:number, level:number, internalformat:number, x:number, y:number, width:number, height:number, border:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glCopyTexSubImage1D(target:number, level:number, xoffset:number, x:number, y:number, width:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glCopyTexSubImage2D(target:number, level:number, xoffset:number, yoffset:number, x:number, y:number, width:number, height:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glCullFace(mode:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glDeleteLists(list:number, range:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glDeleteTextures(textures:array@uint32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glDepthFunc(func:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glDepthMask(flag:boolean):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glDepthRange(zNear:number, zFar:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glDisable(cap:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glDisableClientState(array:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glDrawArrays(mode:number, first:number, count:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glDrawBuffer(mode:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glDrawPixels(width:number, height:number, format:number, type:number, pixels:array:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glDrawPixelsFromImage(image:image):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEdgeFlag(flag:boolean):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEdgeFlagv(flag[]:boolean):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEnable(cap:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEnableClientState(array:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEnd():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEndList():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalCoord1d(u:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalCoord1dv(u:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalCoord1f(u:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalCoord1fv(u:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalCoord2d(u:number, v:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalCoord2dv(u:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalCoord2f(u:number, v:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalCoord2fv(u:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalMesh1(mode:number, i1:number, i2:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalMesh2(mode:number, i1:number, i2:number, j1:number, j2:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalPoint1(i:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glEvalPoint2(i:number, j:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glFeedbackBuffer(type:number, buffer:array@float:nil:nomap):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glFinish():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glFlush():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glFogf(pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glFogfv(pname:number, params:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glFogi(pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glFogiv(pname:number, params:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glFrontFace(mode:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glFrustum(left:number, right:number, bottom:number, top:number, zNear:number, zFar:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGenLists(range:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGenTextures(n:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetBooleanv(pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetClipPlane(plane:number):map</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetDoublev(pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetError() {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetFloatv(pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetIntegerv(pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetLightfv(light:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetLightiv(light:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetMapdv(target:number, query:number, v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetMapfv(target:number, query:number, v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetMapiv(target:number, query:number, v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetMaterialfv(face:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetMaterialiv(face:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetPixelMapfv(map:number, values:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetPixelMapuiv(map:number, values:array@uint32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetPixelMapusv(map:number, values:array@uint16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetPolygonStipple():map</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetString(name:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetTexEnvfv(target:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetTexEnviv(target:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetTexGendv(coord:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetTexGenfv(coord:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetTexGeniv(coord:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetTexLevelParameterfv(target:number, level:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetTexLevelParameteriv(target:number, level:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetTexParameterfv(target:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetTexParameteriv(target:number, pname:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glHint(target:number, mode:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIndexMask(mask:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIndexd(c:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIndexdv(c:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIndexf(c:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIndexfv(c:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIndexi(c:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIndexiv(c:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIndexs(c:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIndexsv(c:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIndexub(c:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIndexubv(c:array@uint8:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glInitNames():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIsEnabled(cap:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIsList(list:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glIsTexture(texture:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLightModelf(pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLightModelfv(pname:number, params:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLightModeli(pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLightModeliv(pname:number, params:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLightf(light:number, pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLightfv(light:number, pname:number, params:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLighti(light:number, pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLightiv(light:number, pname:number, params:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLineStipple(factor:number, pattern:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLineWidth(width:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glListBase(base:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLoadIdentity():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLoadMatrixd(m):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLoadMatrixf(m):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLoadName(name:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glLogicOp(opcode:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMap1d(target:number, u1:number, u2:number, stride:number, order:number, points:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMap1f(target:number, u1:number, u2:number, stride:number, order:number, points:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMap2d(target:number, u1:number, u2:number, ustride:number, uorder:number, v1:number, v2:number, vstride:number, vorder:number, points:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMap2f(target:number, u1:number, u2:number, ustride:number, uorder:number, v1:number, v2:number, vstride:number, vorder:number, points:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMapGrid1d(un:number, u1:number, u2:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMapGrid1f(un:number, u1:number, u2:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMapGrid2d(un:number, u1:number, u2:number, vn:number, v1:number, v2:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMapGrid2f(un:number, u1:number, u2:number, vn:number, v1:number, v2:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMaterialf(face:number, pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMaterialfv(face:number, pname:number, params:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMateriali(face:number, pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMaterialiv(face:number, pname:number, params:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMatrixMode(mode:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMultMatrixd(m):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glMultMatrixf(m):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glNewList(list:number, mode:number):map:void {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glNormal3b(nx:number, ny:number, nz:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glNormal3bv(v:array@int8:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glNormal3d(nx:number, ny:number, nz:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glNormal3dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glNormal3f(nx:number, ny:number, nz:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glNormal3fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glNormal3i(nx:number, ny:number, nz:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glNormal3iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glNormal3s(nx:number, ny:number, nz:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glNormal3sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glOrtho(left:number, right:number, bottom:number, top:number, zNear:number, zFar:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPassThrough(token:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPixelMapfv(map:number, mapsize:number, values:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPixelMapuiv(map:number, mapsize:number, values:array@uint32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPixelMapusv(map:number, mapsize:number, values:array@uint16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPixelStoref(pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPixelStorei(pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPixelTransferf(pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPixelTransferi(pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPixelZoom(xfactor:number, yfactor:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPointSize(size:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPolygonMode(face:number, mode:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPolygonOffset(factor:number, units:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPolygonStipple(mask:array@uint8:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPopAttrib():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPopClientAttrib():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPopMatrix():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPopName():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPrioritizeTextures(textures:array@uint32:nomap, priorities:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPushAttrib(mask:number):map:void {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPushClientAttrib(mask:number):map:void {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPushMatrix():void {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glPushName(name:number):map:void {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos2d(x:number, y:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos2dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos2f(x:number, y:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos2fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos2i(x:number, y:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos2iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos2s(x:number, y:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos2sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos3d(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos3dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos3f(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos3fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos3i(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos3iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos3s(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos3sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos4d(x:number, y:number, z:number, w:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos4dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos4f(x:number, y:number, z:number, w:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos4fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos4i(x:number, y:number, z:number, w:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos4iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos4s(x:number, y:number, z:number, w:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRasterPos4sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glReadBuffer(mode:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glReadPixels(x:number, y:number, width:number, height:number, format:symbol):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRectd(x1:number, y1:number, x2:number, y2:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRectdv(v1:array@double:nomap, v2:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRectf(x1:number, y1:number, x2:number, y2:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRectfv(v1:array@float:nomap, v2:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRecti(x1:number, y1:number, x2:number, y2:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRectiv(v1:array@int32:nomap, v2:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRects(x1:number, y1:number, x2:number, y2:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRectsv(v1:array@int16:nomap, v2:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRenderMode(mode:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRotated(angle:number, x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glRotatef(angle:number, x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glScaled(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glScalef(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glScissor(x:number, y:number, width:number, height:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glSelectBuffer(buffer:array@uint32:nil:nomap):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glShadeModel(mode:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glStencilFunc(func:number, ref:number, mask:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glStencilMask(mask:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glStencilOp(fail:number, zfail:number, zpass:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord1d(s:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord1dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord1f(s:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord1fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord1i(s:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord1iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord1s(s:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord1sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord2d(s:number, t:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord2dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord2f(s:number, t:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord2fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord2i(s:number, t:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord2iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord2s(s:number, t:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord2sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord3d(s:number, t:number, r:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord3dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord3f(s:number, t:number, r:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord3fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord3i(s:number, t:number, r:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord3iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord3s(s:number, t:number, r:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord3sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord4d(s:number, t:number, r:number, q:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord4dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord4f(s:number, t:number, r:number, q:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord4fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord4i(s:number, t:number, r:number, q:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord4iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord4s(s:number, t:number, r:number, q:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexCoord4sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexEnvf(target:number, pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexEnvfv(target:number, pname:number, params:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexEnvi(target:number, pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexEnviv(target:number, pname:number, params:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexGend(coord:number, pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexGendv(coord:number, pname:number, params:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexGenf(coord:number, pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexGenfv(coord:number, pname:number, params:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexGeni(coord:number, pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexGeniv(coord:number, pname:number, params:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexImage1D(target:number, level:number, internalformat:number, width:number, border:number, format:number, type:number, pixels:array:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexImage1DFromImage(target:number, level:number, internalformat:number, border:number, image:image):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexImage2D(target:number, level:number, internalformat:number, width:number, height:number, border:number, format:number, type:number, pixels:array:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexImage2DFromImage(target:number, level:number, internalformat:number, border:number, image:image):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexParameterf(target:number, pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexParameterfv(target:number, pname:number, params:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexParameteri(target:number, pname:number, param:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexParameteriv(target:number, pname:number, params:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexSubImage1D(target:number, level:number, xoffset:number, width:number, format:number, type:number, pixels:array:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexSubImage1DFromImage(target:number, level:number, xoffset:number, image:image):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexSubImage2D(target:number, level:number, xoffset:number, yoffset:number, width:number, height:number, format:number, type:number, pixels:array:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTexSubImage2DFromImage(target:number, level:number, xoffset:number, yoffset:number, image:image):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTranslated(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glTranslatef(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex2d(x:number, y:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex2dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex2f(x:number, y:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex2fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex2i(x:number, y:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex2iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex2s(x:number, y:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex2sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex3d(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex3dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex3f(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex3fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex3i(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex3iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex3s(x:number, y:number, z:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex3sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex4d(x:number, y:number, z:number, w:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex4dv(v:array@double:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex4f(x:number, y:number, z:number, w:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex4fv(v:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex4i(x:number, y:number, z:number, w:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex4iv(v:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex4s(x:number, y:number, z:number, w:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glVertex4sv(v:array@int16:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glViewport(x:number, y:number, width:number, height:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetAttachedShaders(program:number, maxCount:number, count[]:number, shaders:array@uint32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetShaderInfoLog(shader:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetProgramInfoLog(program:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetUniformLocation(program:number, name:string):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetActiveUniform(program:number, index:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetUniformfv(program:number, location:number, params:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetUniformiv(program:number, location:number, params:array@int32:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetShaderSource(shader:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glBindAttribLocation(program:number, index:number, name:string):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetActiveAttrib(program:number, index:number):map</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glGetAttribLocation(program:number, name:string):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glUniformMatrix2x3fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glUniformMatrix3x2fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glUniformMatrix2x4fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glUniformMatrix4x2fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glUniformMatrix3x4fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>opengl.glUniformMatrix4x3fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>
<div class="mb-2 ml-4">
</div>
{% endraw %}
