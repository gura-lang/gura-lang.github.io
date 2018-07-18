---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">43</span><a name="anchor-43"></a>opengl Module</h1>
<h2><span class="caption-index-2">43.1</span><a name="anchor-43-1"></a>Overview</h2>
<p>
The <code>opengl</code> module provides functions of OpenGL library.
</p>
<h2><span class="caption-index-2">43.2</span><a name="anchor-43-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">opengl.glAccum</strong></div>
<div style="margin-bottom:1em"><code>opengl.glAccum(op:number, value:number):map:void</code></div>
operate on the accumulation buffer
</p>
<p>
<div><strong style="text-decoration:underline">opengl.glAlphaFunc</strong></div>
<div style="margin-bottom:1em"><code>opengl.glAlphaFunc(func:number, ref:number):map:void</code></div>
specify the alpha test function
</p>
<p>
<div><strong style="text-decoration:underline">opengl.glAreTexturesResident</strong></div>
<div style="margin-bottom:1em"><code>opengl.glAreTexturesResident(textures:array@uint32:nomap):map {block?}</code></div>
determine if textures are loaded in texture memory
</p>
<p>
<div><strong style="text-decoration:underline">opengl.glArrayElement</strong></div>
<div style="margin-bottom:1em"><code>opengl.glArrayElement(i:number):map:void</code></div>
render a vertex using the specified vertex array element
</p>
<p>
<div><strong style="text-decoration:underline">opengl.glBegin</strong></div>
<div style="margin-bottom:1em"><code>opengl.glBegin(mode:number):map:void {block?}</code></div>
delimit the vertices of a primitive or a group of like primitives
</p>
<p>
<div><strong style="text-decoration:underline">opengl.glBindTexture</strong></div>
<div style="margin-bottom:1em"><code>opengl.glBindTexture(target:number, texture:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glBitmap</strong></div>
<div style="margin-bottom:1em"><code>opengl.glBitmap(width:number, height:number, xorig:number, yorig:number, xmove:number, ymove:number, bitmap:array@uint8:nil:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glBlendFunc</strong></div>
<div style="margin-bottom:1em"><code>opengl.glBlendFunc(sfactor:number, dfactor:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glCallList</strong></div>
<div style="margin-bottom:1em"><code>opengl.glCallList(list:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glCallLists</strong></div>
<div style="margin-bottom:1em"><code>opengl.glCallLists(type:number, lists[]:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glClear</strong></div>
<div style="margin-bottom:1em"><code>opengl.glClear(mask:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glClearAccum</strong></div>
<div style="margin-bottom:1em"><code>opengl.glClearAccum(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glClearColor</strong></div>
<div style="margin-bottom:1em"><code>opengl.glClearColor(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glClearDepth</strong></div>
<div style="margin-bottom:1em"><code>opengl.glClearDepth(depth:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glClearIndex</strong></div>
<div style="margin-bottom:1em"><code>opengl.glClearIndex(c:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glClearStencil</strong></div>
<div style="margin-bottom:1em"><code>opengl.glClearStencil(s:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glClipPlane</strong></div>
<div style="margin-bottom:1em"><code>opengl.glClipPlane(plane:number, equation:array@double:nomap):map:void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3b</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3b(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3bv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3bv(v:array@int8:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3d(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3f(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3i(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3s(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3ub</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3ub(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3ubv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3ubv(v:array@uint8:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3ui</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3ui(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3uiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3uiv(v:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3us</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3us(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor3usv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor3usv(v:array@uint16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4b</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4b(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4bv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4bv(v:array@int8:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4d(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4f(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4i(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4s(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4ub</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4ub(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4ubv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4ubv(v:array@uint8:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4ui</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4ui(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4uiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4uiv(v:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4us</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4us(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColor4usv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColor4usv(v:array@uint16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColorMask</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColorMask(red:boolean, green:boolean, blue:boolean, alpha:boolean):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glColorMaterial</strong></div>
<div style="margin-bottom:1em"><code>opengl.glColorMaterial(face:number, mode:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glCopyPixels</strong></div>
<div style="margin-bottom:1em"><code>opengl.glCopyPixels(x:number, y:number, width:number, height:number, type:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glCopyTexImage1D</strong></div>
<div style="margin-bottom:1em"><code>opengl.glCopyTexImage1D(target:number, level:number, internalformat:number, x:number, y:number, width:number, border:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glCopyTexImage2D</strong></div>
<div style="margin-bottom:1em"><code>opengl.glCopyTexImage2D(target:number, level:number, internalformat:number, x:number, y:number, width:number, height:number, border:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glCopyTexSubImage1D</strong></div>
<div style="margin-bottom:1em"><code>opengl.glCopyTexSubImage1D(target:number, level:number, xoffset:number, x:number, y:number, width:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glCopyTexSubImage2D</strong></div>
<div style="margin-bottom:1em"><code>opengl.glCopyTexSubImage2D(target:number, level:number, xoffset:number, yoffset:number, x:number, y:number, width:number, height:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glCullFace</strong></div>
<div style="margin-bottom:1em"><code>opengl.glCullFace(mode:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glDeleteLists</strong></div>
<div style="margin-bottom:1em"><code>opengl.glDeleteLists(list:number, range:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glDeleteTextures</strong></div>
<div style="margin-bottom:1em"><code>opengl.glDeleteTextures(textures:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glDepthFunc</strong></div>
<div style="margin-bottom:1em"><code>opengl.glDepthFunc(func:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glDepthMask</strong></div>
<div style="margin-bottom:1em"><code>opengl.glDepthMask(flag:boolean):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glDepthRange</strong></div>
<div style="margin-bottom:1em"><code>opengl.glDepthRange(zNear:number, zFar:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glDisable</strong></div>
<div style="margin-bottom:1em"><code>opengl.glDisable(cap:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glDisableClientState</strong></div>
<div style="margin-bottom:1em"><code>opengl.glDisableClientState(array:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glDrawArrays</strong></div>
<div style="margin-bottom:1em"><code>opengl.glDrawArrays(mode:number, first:number, count:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glDrawBuffer</strong></div>
<div style="margin-bottom:1em"><code>opengl.glDrawBuffer(mode:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glDrawPixels</strong></div>
<div style="margin-bottom:1em"><code>opengl.glDrawPixels(width:number, height:number, format:number, type:number, pixels:array:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glDrawPixelsFromImage</strong></div>
<div style="margin-bottom:1em"><code>opengl.glDrawPixelsFromImage(image:image):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEdgeFlag</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEdgeFlag(flag:boolean):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEdgeFlagv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEdgeFlagv(flag[]:boolean):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEnable</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEnable(cap:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEnableClientState</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEnableClientState(array:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEnd</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEnd():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEndList</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEndList():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalCoord1d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalCoord1d(u:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalCoord1dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalCoord1dv(u:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalCoord1f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalCoord1f(u:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalCoord1fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalCoord1fv(u:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalCoord2d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalCoord2d(u:number, v:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalCoord2dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalCoord2dv(u:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalCoord2f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalCoord2f(u:number, v:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalCoord2fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalCoord2fv(u:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalMesh1</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalMesh1(mode:number, i1:number, i2:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalMesh2</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalMesh2(mode:number, i1:number, i2:number, j1:number, j2:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalPoint1</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalPoint1(i:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glEvalPoint2</strong></div>
<div style="margin-bottom:1em"><code>opengl.glEvalPoint2(i:number, j:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glFeedbackBuffer</strong></div>
<div style="margin-bottom:1em"><code>opengl.glFeedbackBuffer(type:number, buffer:array@float:nil:nomap):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glFinish</strong></div>
<div style="margin-bottom:1em"><code>opengl.glFinish():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glFlush</strong></div>
<div style="margin-bottom:1em"><code>opengl.glFlush():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glFogf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glFogf(pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glFogfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glFogfv(pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glFogi</strong></div>
<div style="margin-bottom:1em"><code>opengl.glFogi(pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glFogiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glFogiv(pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glFrontFace</strong></div>
<div style="margin-bottom:1em"><code>opengl.glFrontFace(mode:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glFrustum</strong></div>
<div style="margin-bottom:1em"><code>opengl.glFrustum(left:number, right:number, bottom:number, top:number, zNear:number, zFar:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGenLists</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGenLists(range:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGenTextures</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGenTextures(n:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetBooleanv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetBooleanv(pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetClipPlane</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetClipPlane(plane:number):map</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetDoublev</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetDoublev(pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetError</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetError() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetFloatv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetFloatv(pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetIntegerv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetIntegerv(pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetLightfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetLightfv(light:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetLightiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetLightiv(light:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetMapdv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetMapdv(target:number, query:number, v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetMapfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetMapfv(target:number, query:number, v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetMapiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetMapiv(target:number, query:number, v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetMaterialfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetMaterialfv(face:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetMaterialiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetMaterialiv(face:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetPixelMapfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetPixelMapfv(map:number, values:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetPixelMapuiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetPixelMapuiv(map:number, values:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetPixelMapusv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetPixelMapusv(map:number, values:array@uint16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetPolygonStipple</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetPolygonStipple():map</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetString</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetString(name:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetTexEnvfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetTexEnvfv(target:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetTexEnviv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetTexEnviv(target:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetTexGendv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetTexGendv(coord:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetTexGenfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetTexGenfv(coord:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetTexGeniv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetTexGeniv(coord:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetTexLevelParameterfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetTexLevelParameterfv(target:number, level:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetTexLevelParameteriv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetTexLevelParameteriv(target:number, level:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetTexParameterfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetTexParameterfv(target:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetTexParameteriv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetTexParameteriv(target:number, pname:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glHint</strong></div>
<div style="margin-bottom:1em"><code>opengl.glHint(target:number, mode:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIndexMask</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIndexMask(mask:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIndexd</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIndexd(c:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIndexdv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIndexdv(c:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIndexf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIndexf(c:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIndexfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIndexfv(c:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIndexi</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIndexi(c:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIndexiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIndexiv(c:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIndexs</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIndexs(c:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIndexsv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIndexsv(c:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIndexub</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIndexub(c:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIndexubv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIndexubv(c:array@uint8:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glInitNames</strong></div>
<div style="margin-bottom:1em"><code>opengl.glInitNames():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIsEnabled</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIsEnabled(cap:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIsList</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIsList(list:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glIsTexture</strong></div>
<div style="margin-bottom:1em"><code>opengl.glIsTexture(texture:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLightModelf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLightModelf(pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLightModelfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLightModelfv(pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLightModeli</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLightModeli(pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLightModeliv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLightModeliv(pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLightf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLightf(light:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLightfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLightfv(light:number, pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLighti</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLighti(light:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLightiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLightiv(light:number, pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLineStipple</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLineStipple(factor:number, pattern:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLineWidth</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLineWidth(width:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glListBase</strong></div>
<div style="margin-bottom:1em"><code>opengl.glListBase(base:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLoadIdentity</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLoadIdentity():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLoadMatrixd</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLoadMatrixd(m):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLoadMatrixf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLoadMatrixf(m):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLoadName</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLoadName(name:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glLogicOp</strong></div>
<div style="margin-bottom:1em"><code>opengl.glLogicOp(opcode:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMap1d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMap1d(target:number, u1:number, u2:number, stride:number, order:number, points:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMap1f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMap1f(target:number, u1:number, u2:number, stride:number, order:number, points:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMap2d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMap2d(target:number, u1:number, u2:number, ustride:number, uorder:number, v1:number, v2:number, vstride:number, vorder:number, points:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMap2f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMap2f(target:number, u1:number, u2:number, ustride:number, uorder:number, v1:number, v2:number, vstride:number, vorder:number, points:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMapGrid1d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMapGrid1d(un:number, u1:number, u2:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMapGrid1f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMapGrid1f(un:number, u1:number, u2:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMapGrid2d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMapGrid2d(un:number, u1:number, u2:number, vn:number, v1:number, v2:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMapGrid2f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMapGrid2f(un:number, u1:number, u2:number, vn:number, v1:number, v2:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMaterialf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMaterialf(face:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMaterialfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMaterialfv(face:number, pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMateriali</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMateriali(face:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMaterialiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMaterialiv(face:number, pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMatrixMode</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMatrixMode(mode:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMultMatrixd</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMultMatrixd(m):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glMultMatrixf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glMultMatrixf(m):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glNewList</strong></div>
<div style="margin-bottom:1em"><code>opengl.glNewList(list:number, mode:number):map:void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glNormal3b</strong></div>
<div style="margin-bottom:1em"><code>opengl.glNormal3b(nx:number, ny:number, nz:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glNormal3bv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glNormal3bv(v:array@int8:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glNormal3d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glNormal3d(nx:number, ny:number, nz:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glNormal3dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glNormal3dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glNormal3f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glNormal3f(nx:number, ny:number, nz:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glNormal3fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glNormal3fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glNormal3i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glNormal3i(nx:number, ny:number, nz:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glNormal3iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glNormal3iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glNormal3s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glNormal3s(nx:number, ny:number, nz:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glNormal3sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glNormal3sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glOrtho</strong></div>
<div style="margin-bottom:1em"><code>opengl.glOrtho(left:number, right:number, bottom:number, top:number, zNear:number, zFar:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPassThrough</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPassThrough(token:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPixelMapfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPixelMapfv(map:number, mapsize:number, values:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPixelMapuiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPixelMapuiv(map:number, mapsize:number, values:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPixelMapusv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPixelMapusv(map:number, mapsize:number, values:array@uint16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPixelStoref</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPixelStoref(pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPixelStorei</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPixelStorei(pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPixelTransferf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPixelTransferf(pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPixelTransferi</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPixelTransferi(pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPixelZoom</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPixelZoom(xfactor:number, yfactor:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPointSize</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPointSize(size:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPolygonMode</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPolygonMode(face:number, mode:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPolygonOffset</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPolygonOffset(factor:number, units:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPolygonStipple</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPolygonStipple(mask:array@uint8:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPopAttrib</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPopAttrib():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPopClientAttrib</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPopClientAttrib():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPopMatrix</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPopMatrix():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPopName</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPopName():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPrioritizeTextures</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPrioritizeTextures(textures:array@uint32:nomap, priorities:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPushAttrib</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPushAttrib(mask:number):map:void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPushClientAttrib</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPushClientAttrib(mask:number):map:void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPushMatrix</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPushMatrix():void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glPushName</strong></div>
<div style="margin-bottom:1em"><code>opengl.glPushName(name:number):map:void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos2d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos2d(x:number, y:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos2dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos2dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos2f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos2f(x:number, y:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos2fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos2fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos2i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos2i(x:number, y:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos2iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos2iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos2s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos2s(x:number, y:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos2sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos2sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos3d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos3d(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos3dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos3dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos3f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos3f(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos3fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos3fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos3i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos3i(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos3iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos3iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos3s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos3s(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos3sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos3sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos4d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos4d(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos4dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos4dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos4f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos4f(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos4fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos4fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos4i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos4i(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos4iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos4iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos4s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos4s(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRasterPos4sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRasterPos4sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glReadBuffer</strong></div>
<div style="margin-bottom:1em"><code>opengl.glReadBuffer(mode:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glReadPixels</strong></div>
<div style="margin-bottom:1em"><code>opengl.glReadPixels(x:number, y:number, width:number, height:number, format:symbol):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRectd</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRectd(x1:number, y1:number, x2:number, y2:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRectdv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRectdv(v1:array@double:nomap, v2:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRectf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRectf(x1:number, y1:number, x2:number, y2:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRectfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRectfv(v1:array@float:nomap, v2:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRecti</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRecti(x1:number, y1:number, x2:number, y2:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRectiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRectiv(v1:array@int32:nomap, v2:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRects</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRects(x1:number, y1:number, x2:number, y2:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRectsv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRectsv(v1:array@int16:nomap, v2:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRenderMode</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRenderMode(mode:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRotated</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRotated(angle:number, x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glRotatef</strong></div>
<div style="margin-bottom:1em"><code>opengl.glRotatef(angle:number, x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glScaled</strong></div>
<div style="margin-bottom:1em"><code>opengl.glScaled(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glScalef</strong></div>
<div style="margin-bottom:1em"><code>opengl.glScalef(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glScissor</strong></div>
<div style="margin-bottom:1em"><code>opengl.glScissor(x:number, y:number, width:number, height:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glSelectBuffer</strong></div>
<div style="margin-bottom:1em"><code>opengl.glSelectBuffer(buffer:array@uint32:nil:nomap):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glShadeModel</strong></div>
<div style="margin-bottom:1em"><code>opengl.glShadeModel(mode:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glStencilFunc</strong></div>
<div style="margin-bottom:1em"><code>opengl.glStencilFunc(func:number, ref:number, mask:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glStencilMask</strong></div>
<div style="margin-bottom:1em"><code>opengl.glStencilMask(mask:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glStencilOp</strong></div>
<div style="margin-bottom:1em"><code>opengl.glStencilOp(fail:number, zfail:number, zpass:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord1d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord1d(s:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord1dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord1dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord1f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord1f(s:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord1fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord1fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord1i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord1i(s:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord1iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord1iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord1s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord1s(s:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord1sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord1sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord2d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord2d(s:number, t:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord2dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord2dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord2f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord2f(s:number, t:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord2fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord2fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord2i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord2i(s:number, t:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord2iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord2iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord2s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord2s(s:number, t:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord2sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord2sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord3d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord3d(s:number, t:number, r:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord3dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord3dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord3f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord3f(s:number, t:number, r:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord3fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord3fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord3i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord3i(s:number, t:number, r:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord3iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord3iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord3s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord3s(s:number, t:number, r:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord3sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord3sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord4d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord4d(s:number, t:number, r:number, q:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord4dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord4dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord4f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord4f(s:number, t:number, r:number, q:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord4fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord4fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord4i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord4i(s:number, t:number, r:number, q:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord4iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord4iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord4s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord4s(s:number, t:number, r:number, q:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexCoord4sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexCoord4sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexEnvf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexEnvf(target:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexEnvfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexEnvfv(target:number, pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexEnvi</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexEnvi(target:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexEnviv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexEnviv(target:number, pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexGend</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexGend(coord:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexGendv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexGendv(coord:number, pname:number, params:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexGenf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexGenf(coord:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexGenfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexGenfv(coord:number, pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexGeni</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexGeni(coord:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexGeniv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexGeniv(coord:number, pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexImage1D</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexImage1D(target:number, level:number, internalformat:number, width:number, border:number, format:number, type:number, pixels:array:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexImage1DFromImage</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexImage1DFromImage(target:number, level:number, internalformat:number, border:number, image:image):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexImage2D</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexImage2D(target:number, level:number, internalformat:number, width:number, height:number, border:number, format:number, type:number, pixels:array:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexImage2DFromImage</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexImage2DFromImage(target:number, level:number, internalformat:number, border:number, image:image):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexParameterf</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexParameterf(target:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexParameterfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexParameterfv(target:number, pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexParameteri</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexParameteri(target:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexParameteriv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexParameteriv(target:number, pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexSubImage1D</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexSubImage1D(target:number, level:number, xoffset:number, width:number, format:number, type:number, pixels:array:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexSubImage1DFromImage</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexSubImage1DFromImage(target:number, level:number, xoffset:number, image:image):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexSubImage2D</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexSubImage2D(target:number, level:number, xoffset:number, yoffset:number, width:number, height:number, format:number, type:number, pixels:array:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTexSubImage2DFromImage</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTexSubImage2DFromImage(target:number, level:number, xoffset:number, yoffset:number, image:image):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTranslated</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTranslated(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glTranslatef</strong></div>
<div style="margin-bottom:1em"><code>opengl.glTranslatef(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex2d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex2d(x:number, y:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex2dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex2dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex2f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex2f(x:number, y:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex2fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex2fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex2i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex2i(x:number, y:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex2iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex2iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex2s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex2s(x:number, y:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex2sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex2sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex3d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex3d(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex3dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex3dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex3f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex3f(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex3fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex3fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex3i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex3i(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex3iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex3iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex3s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex3s(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex3sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex3sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex4d</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex4d(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex4dv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex4dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex4f</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex4f(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex4fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex4fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex4i</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex4i(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex4iv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex4iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex4s</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex4s(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glVertex4sv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glVertex4sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glViewport</strong></div>
<div style="margin-bottom:1em"><code>opengl.glViewport(x:number, y:number, width:number, height:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetAttachedShaders</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetAttachedShaders(program:number, maxCount:number, count[]:number, shaders:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetShaderInfoLog</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetShaderInfoLog(shader:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetProgramInfoLog</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetProgramInfoLog(program:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetUniformLocation</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetUniformLocation(program:number, name:string):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetActiveUniform</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetActiveUniform(program:number, index:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetUniformfv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetUniformfv(program:number, location:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetUniformiv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetUniformiv(program:number, location:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetShaderSource</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetShaderSource(shader:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glBindAttribLocation</strong></div>
<div style="margin-bottom:1em"><code>opengl.glBindAttribLocation(program:number, index:number, name:string):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetActiveAttrib</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetActiveAttrib(program:number, index:number):map</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glGetAttribLocation</strong></div>
<div style="margin-bottom:1em"><code>opengl.glGetAttribLocation(program:number, name:string):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glUniformMatrix2x3fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glUniformMatrix2x3fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glUniformMatrix3x2fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glUniformMatrix3x2fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glUniformMatrix2x4fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glUniformMatrix2x4fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glUniformMatrix4x2fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glUniformMatrix4x2fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glUniformMatrix3x4fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glUniformMatrix3x4fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">opengl.glUniformMatrix4x3fv</strong></div>
<div style="margin-bottom:1em"><code>opengl.glUniformMatrix4x3fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
<p />

{% endraw %}
