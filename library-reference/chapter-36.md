---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">36</span><a name="anchor-36"></a>opengl Module</h1>
<p>
The <code>opengl</code> module provides functions of OpenGL library.
</p>
<h2><span class="caption-index-2">36.1</span><a name="anchor-36-1"></a>Module Function</h2>
<p>
<strong>opengl.glAccum</strong>
</p>
<p>
<code>opengl.glAccum(op:number, value:number):map:void</code>
</p>
<p>
operate on the accumulation buffer
</p>
<p>
<strong>opengl.glAlphaFunc</strong>
</p>
<p>
<code>opengl.glAlphaFunc(func:number, ref:number):map:void</code>
</p>
<p>
specify the alpha test function
</p>
<p>
<strong>opengl.glAreTexturesResident</strong>
</p>
<p>
<code>opengl.glAreTexturesResident(textures:array@uint:nomap):map {block?}</code>
</p>
<p>
determine if textures are loaded in texture memory
</p>
<p>
<strong>opengl.glArrayElement</strong>
</p>
<p>
<code>opengl.glArrayElement(i:number):map:void</code>
</p>
<p>
render a vertex using the specified vertex array element
</p>
<p>
<strong>opengl.glBegin</strong>
</p>
<p>
<code>opengl.glBegin(mode:number):map:void {block?}</code>
</p>
<p>
delimit the vertices of a primitive or a group of like primitives
</p>
<p>
<strong>opengl.glBindTexture</strong>
</p>
<p>
<code>opengl.glBindTexture(target:number, texture:number):map:void</code>
</p>
<p>
<strong>opengl.glBitmap</strong>
</p>
<p>
<code>opengl.glBitmap(width:number, height:number, xorig:number, yorig:number, xmove:number, ymove:number, bitmap:array@uchar:nomap:nil):map:void</code>
</p>
<p>
<strong>opengl.glBlendFunc</strong>
</p>
<p>
<code>opengl.glBlendFunc(sfactor:number, dfactor:number):map:void</code>
</p>
<p>
<strong>opengl.glCallList</strong>
</p>
<p>
<code>opengl.glCallList(list:number):map:void</code>
</p>
<p>
<strong>opengl.glCallLists</strong>
</p>
<p>
<code>opengl.glCallLists(type:number, lists[]:number):map:void</code>
</p>
<p>
<strong>opengl.glClear</strong>
</p>
<p>
<code>opengl.glClear(mask:number):map:void</code>
</p>
<p>
<strong>opengl.glClearAccum</strong>
</p>
<p>
<code>opengl.glClearAccum(red:number, green:number, blue:number, alpha:number):map:void</code>
</p>
<p>
<strong>opengl.glClearColor</strong>
</p>
<p>
<code>opengl.glClearColor(red:number, green:number, blue:number, alpha:number):map:void</code>
</p>
<p>
<strong>opengl.glClearDepth</strong>
</p>
<p>
<code>opengl.glClearDepth(depth:number):map:void</code>
</p>
<p>
<strong>opengl.glClearIndex</strong>
</p>
<p>
<code>opengl.glClearIndex(c:number):map:void</code>
</p>
<p>
<strong>opengl.glClearStencil</strong>
</p>
<p>
<code>opengl.glClearStencil(s:number):map:void</code>
</p>
<p>
<strong>opengl.glClipPlane</strong>
</p>
<p>
<code>opengl.glClipPlane(plane:number, equation:array@double:nomap):map {block?}</code>
</p>
<p>
<strong>opengl.glColor3b</strong>
</p>
<p>
<code>opengl.glColor3b(red:number, green:number, blue:number):map:void</code>
</p>
<p>
<strong>opengl.glColor3bv</strong>
</p>
<p>
<code>opengl.glColor3bv(v:array@char:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor3d</strong>
</p>
<p>
<code>opengl.glColor3d(red:number, green:number, blue:number):map:void</code>
</p>
<p>
<strong>opengl.glColor3dv</strong>
</p>
<p>
<code>opengl.glColor3dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor3f</strong>
</p>
<p>
<code>opengl.glColor3f(red:number, green:number, blue:number):map:void</code>
</p>
<p>
<strong>opengl.glColor3fv</strong>
</p>
<p>
<code>opengl.glColor3fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor3i</strong>
</p>
<p>
<code>opengl.glColor3i(red:number, green:number, blue:number):map:void</code>
</p>
<p>
<strong>opengl.glColor3iv</strong>
</p>
<p>
<code>opengl.glColor3iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor3s</strong>
</p>
<p>
<code>opengl.glColor3s(red:number, green:number, blue:number):map:void</code>
</p>
<p>
<strong>opengl.glColor3sv</strong>
</p>
<p>
<code>opengl.glColor3sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor3ub</strong>
</p>
<p>
<code>opengl.glColor3ub(red:number, green:number, blue:number):map:void</code>
</p>
<p>
<strong>opengl.glColor3ubv</strong>
</p>
<p>
<code>opengl.glColor3ubv(v:array@uchar:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor3ui</strong>
</p>
<p>
<code>opengl.glColor3ui(red:number, green:number, blue:number):map:void</code>
</p>
<p>
<strong>opengl.glColor3uiv</strong>
</p>
<p>
<code>opengl.glColor3uiv(v:array@uint:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor3us</strong>
</p>
<p>
<code>opengl.glColor3us(red:number, green:number, blue:number):map:void</code>
</p>
<p>
<strong>opengl.glColor3usv</strong>
</p>
<p>
<code>opengl.glColor3usv(v:array@ushort:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor4b</strong>
</p>
<p>
<code>opengl.glColor4b(red:number, green:number, blue:number, alpha:number):map:void</code>
</p>
<p>
<strong>opengl.glColor4bv</strong>
</p>
<p>
<code>opengl.glColor4bv(v:array@char:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor4d</strong>
</p>
<p>
<code>opengl.glColor4d(red:number, green:number, blue:number, alpha:number):map:void</code>
</p>
<p>
<strong>opengl.glColor4dv</strong>
</p>
<p>
<code>opengl.glColor4dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor4f</strong>
</p>
<p>
<code>opengl.glColor4f(red:number, green:number, blue:number, alpha:number):map:void</code>
</p>
<p>
<strong>opengl.glColor4fv</strong>
</p>
<p>
<code>opengl.glColor4fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor4i</strong>
</p>
<p>
<code>opengl.glColor4i(red:number, green:number, blue:number, alpha:number):map:void</code>
</p>
<p>
<strong>opengl.glColor4iv</strong>
</p>
<p>
<code>opengl.glColor4iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor4s</strong>
</p>
<p>
<code>opengl.glColor4s(red:number, green:number, blue:number, alpha:number):map:void</code>
</p>
<p>
<strong>opengl.glColor4sv</strong>
</p>
<p>
<code>opengl.glColor4sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor4ub</strong>
</p>
<p>
<code>opengl.glColor4ub(red:number, green:number, blue:number, alpha:number):map:void</code>
</p>
<p>
<strong>opengl.glColor4ubv</strong>
</p>
<p>
<code>opengl.glColor4ubv(v:array@uchar:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor4ui</strong>
</p>
<p>
<code>opengl.glColor4ui(red:number, green:number, blue:number, alpha:number):map:void</code>
</p>
<p>
<strong>opengl.glColor4uiv</strong>
</p>
<p>
<code>opengl.glColor4uiv(v:array@uint:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColor4us</strong>
</p>
<p>
<code>opengl.glColor4us(red:number, green:number, blue:number, alpha:number):map:void</code>
</p>
<p>
<strong>opengl.glColor4usv</strong>
</p>
<p>
<code>opengl.glColor4usv(v:array@ushort:nomap):map:void</code>
</p>
<p>
<strong>opengl.glColorMask</strong>
</p>
<p>
<code>opengl.glColorMask(red:boolean, green:boolean, blue:boolean, alpha:boolean):map:void</code>
</p>
<p>
<strong>opengl.glColorMaterial</strong>
</p>
<p>
<code>opengl.glColorMaterial(face:number, mode:number):map:void</code>
</p>
<p>
<strong>opengl.glCopyPixels</strong>
</p>
<p>
<code>opengl.glCopyPixels(x:number, y:number, width:number, height:number, type:number):map:void</code>
</p>
<p>
<strong>opengl.glCopyTexImage1D</strong>
</p>
<p>
<code>opengl.glCopyTexImage1D(target:number, level:number, internalformat:number, x:number, y:number, width:number, border:number):map:void</code>
</p>
<p>
<strong>opengl.glCopyTexImage2D</strong>
</p>
<p>
<code>opengl.glCopyTexImage2D(target:number, level:number, internalformat:number, x:number, y:number, width:number, height:number, border:number):map:void</code>
</p>
<p>
<strong>opengl.glCopyTexSubImage1D</strong>
</p>
<p>
<code>opengl.glCopyTexSubImage1D(target:number, level:number, xoffset:number, x:number, y:number, width:number):map:void</code>
</p>
<p>
<strong>opengl.glCopyTexSubImage2D</strong>
</p>
<p>
<code>opengl.glCopyTexSubImage2D(target:number, level:number, xoffset:number, yoffset:number, x:number, y:number, width:number, height:number):map:void</code>
</p>
<p>
<strong>opengl.glCullFace</strong>
</p>
<p>
<code>opengl.glCullFace(mode:number):map:void</code>
</p>
<p>
<strong>opengl.glDeleteLists</strong>
</p>
<p>
<code>opengl.glDeleteLists(list:number, range:number):map:void</code>
</p>
<p>
<strong>opengl.glDeleteTextures</strong>
</p>
<p>
<code>opengl.glDeleteTextures(textures:array@uint:nomap):map:void</code>
</p>
<p>
<strong>opengl.glDepthFunc</strong>
</p>
<p>
<code>opengl.glDepthFunc(func:number):map:void</code>
</p>
<p>
<strong>opengl.glDepthMask</strong>
</p>
<p>
<code>opengl.glDepthMask(flag:boolean):map:void</code>
</p>
<p>
<strong>opengl.glDepthRange</strong>
</p>
<p>
<code>opengl.glDepthRange(zNear:number, zFar:number):map:void</code>
</p>
<p>
<strong>opengl.glDisable</strong>
</p>
<p>
<code>opengl.glDisable(cap:number):map:void</code>
</p>
<p>
<strong>opengl.glDisableClientState</strong>
</p>
<p>
<code>opengl.glDisableClientState(array:number):map:void</code>
</p>
<p>
<strong>opengl.glDrawArrays</strong>
</p>
<p>
<code>opengl.glDrawArrays(mode:number, first:number, count:number):map:void</code>
</p>
<p>
<strong>opengl.glDrawBuffer</strong>
</p>
<p>
<code>opengl.glDrawBuffer(mode:number):map:void</code>
</p>
<p>
<strong>opengl.glDrawPixels</strong>
</p>
<p>
<code>opengl.glDrawPixels(width:number, height:number, format:number, type:number, pixels):map:void</code>
</p>
<p>
<strong>opengl.glDrawPixelsFromImage</strong>
</p>
<p>
<code>opengl.glDrawPixelsFromImage(image:image):map:void</code>
</p>
<p>
<strong>opengl.glEdgeFlag</strong>
</p>
<p>
<code>opengl.glEdgeFlag(flag:boolean):map:void</code>
</p>
<p>
<strong>opengl.glEdgeFlagv</strong>
</p>
<p>
<code>opengl.glEdgeFlagv(flag[]:boolean):map:void</code>
</p>
<p>
<strong>opengl.glEnable</strong>
</p>
<p>
<code>opengl.glEnable(cap:number):map:void</code>
</p>
<p>
<strong>opengl.glEnableClientState</strong>
</p>
<p>
<code>opengl.glEnableClientState(array:number):map:void</code>
</p>
<p>
<strong>opengl.glEnd</strong>
</p>
<p>
<code>opengl.glEnd():void</code>
</p>
<p>
<strong>opengl.glEndList</strong>
</p>
<p>
<code>opengl.glEndList():void</code>
</p>
<p>
<strong>opengl.glEvalCoord1d</strong>
</p>
<p>
<code>opengl.glEvalCoord1d(u:number):map:void</code>
</p>
<p>
<strong>opengl.glEvalCoord1dv</strong>
</p>
<p>
<code>opengl.glEvalCoord1dv(u:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glEvalCoord1f</strong>
</p>
<p>
<code>opengl.glEvalCoord1f(u:number):map:void</code>
</p>
<p>
<strong>opengl.glEvalCoord1fv</strong>
</p>
<p>
<code>opengl.glEvalCoord1fv(u:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glEvalCoord2d</strong>
</p>
<p>
<code>opengl.glEvalCoord2d(u:number, v:number):map:void</code>
</p>
<p>
<strong>opengl.glEvalCoord2dv</strong>
</p>
<p>
<code>opengl.glEvalCoord2dv(u:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glEvalCoord2f</strong>
</p>
<p>
<code>opengl.glEvalCoord2f(u:number, v:number):map:void</code>
</p>
<p>
<strong>opengl.glEvalCoord2fv</strong>
</p>
<p>
<code>opengl.glEvalCoord2fv(u:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glEvalMesh1</strong>
</p>
<p>
<code>opengl.glEvalMesh1(mode:number, i1:number, i2:number):map:void</code>
</p>
<p>
<strong>opengl.glEvalMesh2</strong>
</p>
<p>
<code>opengl.glEvalMesh2(mode:number, i1:number, i2:number, j1:number, j2:number):map:void</code>
</p>
<p>
<strong>opengl.glEvalPoint1</strong>
</p>
<p>
<code>opengl.glEvalPoint1(i:number):map:void</code>
</p>
<p>
<strong>opengl.glEvalPoint2</strong>
</p>
<p>
<code>opengl.glEvalPoint2(i:number, j:number):map:void</code>
</p>
<p>
<strong>opengl.glFeedbackBuffer</strong>
</p>
<p>
<code>opengl.glFeedbackBuffer(type:number, buffer:array@float:nomap:nil):void</code>
</p>
<p>
<strong>opengl.glFinish</strong>
</p>
<p>
<code>opengl.glFinish():void</code>
</p>
<p>
<strong>opengl.glFlush</strong>
</p>
<p>
<code>opengl.glFlush():void</code>
</p>
<p>
<strong>opengl.glFogf</strong>
</p>
<p>
<code>opengl.glFogf(pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glFogfv</strong>
</p>
<p>
<code>opengl.glFogfv(pname:number, params:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glFogi</strong>
</p>
<p>
<code>opengl.glFogi(pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glFogiv</strong>
</p>
<p>
<code>opengl.glFogiv(pname:number, params:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glFrontFace</strong>
</p>
<p>
<code>opengl.glFrontFace(mode:number):map:void</code>
</p>
<p>
<strong>opengl.glFrustum</strong>
</p>
<p>
<code>opengl.glFrustum(left:number, right:number, bottom:number, top:number, zNear:number, zFar:number):map:void</code>
</p>
<p>
<strong>opengl.glGenLists</strong>
</p>
<p>
<code>opengl.glGenLists(range:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGenTextures</strong>
</p>
<p>
<code>opengl.glGenTextures(n:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetBooleanv</strong>
</p>
<p>
<code>opengl.glGetBooleanv(pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetClipPlane</strong>
</p>
<p>
<code>opengl.glGetClipPlane(plane:number):map</code>
</p>
<p>
<strong>opengl.glGetDoublev</strong>
</p>
<p>
<code>opengl.glGetDoublev(pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetError</strong>
</p>
<p>
<code>opengl.glGetError() {block?}</code>
</p>
<p>
<strong>opengl.glGetFloatv</strong>
</p>
<p>
<code>opengl.glGetFloatv(pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetIntegerv</strong>
</p>
<p>
<code>opengl.glGetIntegerv(pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetLightfv</strong>
</p>
<p>
<code>opengl.glGetLightfv(light:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetLightiv</strong>
</p>
<p>
<code>opengl.glGetLightiv(light:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetMapdv</strong>
</p>
<p>
<code>opengl.glGetMapdv(target:number, query:number, v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetMapfv</strong>
</p>
<p>
<code>opengl.glGetMapfv(target:number, query:number, v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetMapiv</strong>
</p>
<p>
<code>opengl.glGetMapiv(target:number, query:number, v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetMaterialfv</strong>
</p>
<p>
<code>opengl.glGetMaterialfv(face:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetMaterialiv</strong>
</p>
<p>
<code>opengl.glGetMaterialiv(face:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetPixelMapfv</strong>
</p>
<p>
<code>opengl.glGetPixelMapfv(map:number, values:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetPixelMapuiv</strong>
</p>
<p>
<code>opengl.glGetPixelMapuiv(map:number, values:array@uint:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetPixelMapusv</strong>
</p>
<p>
<code>opengl.glGetPixelMapusv(map:number, values:array@ushort:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetPolygonStipple</strong>
</p>
<p>
<code>opengl.glGetPolygonStipple(mask:array@uchar:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetString</strong>
</p>
<p>
<code>opengl.glGetString(name:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetTexEnvfv</strong>
</p>
<p>
<code>opengl.glGetTexEnvfv(target:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetTexEnviv</strong>
</p>
<p>
<code>opengl.glGetTexEnviv(target:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetTexGendv</strong>
</p>
<p>
<code>opengl.glGetTexGendv(coord:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetTexGenfv</strong>
</p>
<p>
<code>opengl.glGetTexGenfv(coord:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetTexGeniv</strong>
</p>
<p>
<code>opengl.glGetTexGeniv(coord:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetTexLevelParameterfv</strong>
</p>
<p>
<code>opengl.glGetTexLevelParameterfv(target:number, level:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetTexLevelParameteriv</strong>
</p>
<p>
<code>opengl.glGetTexLevelParameteriv(target:number, level:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetTexParameterfv</strong>
</p>
<p>
<code>opengl.glGetTexParameterfv(target:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glGetTexParameteriv</strong>
</p>
<p>
<code>opengl.glGetTexParameteriv(target:number, pname:number):map {block?}</code>
</p>
<p>
<strong>opengl.glHint</strong>
</p>
<p>
<code>opengl.glHint(target:number, mode:number):map:void</code>
</p>
<p>
<strong>opengl.glIndexMask</strong>
</p>
<p>
<code>opengl.glIndexMask(mask:number):map:void</code>
</p>
<p>
<strong>opengl.glIndexd</strong>
</p>
<p>
<code>opengl.glIndexd(c:number):map:void</code>
</p>
<p>
<strong>opengl.glIndexdv</strong>
</p>
<p>
<code>opengl.glIndexdv(c:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glIndexf</strong>
</p>
<p>
<code>opengl.glIndexf(c:number):map:void</code>
</p>
<p>
<strong>opengl.glIndexfv</strong>
</p>
<p>
<code>opengl.glIndexfv(c:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glIndexi</strong>
</p>
<p>
<code>opengl.glIndexi(c:number):map:void</code>
</p>
<p>
<strong>opengl.glIndexiv</strong>
</p>
<p>
<code>opengl.glIndexiv(c:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glIndexs</strong>
</p>
<p>
<code>opengl.glIndexs(c:number):map:void</code>
</p>
<p>
<strong>opengl.glIndexsv</strong>
</p>
<p>
<code>opengl.glIndexsv(c:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glIndexub</strong>
</p>
<p>
<code>opengl.glIndexub(c:number):map:void</code>
</p>
<p>
<strong>opengl.glIndexubv</strong>
</p>
<p>
<code>opengl.glIndexubv(c:array@uchar:nomap):map:void</code>
</p>
<p>
<strong>opengl.glInitNames</strong>
</p>
<p>
<code>opengl.glInitNames():void</code>
</p>
<p>
<strong>opengl.glIsEnabled</strong>
</p>
<p>
<code>opengl.glIsEnabled(cap:number):map {block?}</code>
</p>
<p>
<strong>opengl.glIsList</strong>
</p>
<p>
<code>opengl.glIsList(list:number):map {block?}</code>
</p>
<p>
<strong>opengl.glIsTexture</strong>
</p>
<p>
<code>opengl.glIsTexture(texture:number):map {block?}</code>
</p>
<p>
<strong>opengl.glLightModelf</strong>
</p>
<p>
<code>opengl.glLightModelf(pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glLightModelfv</strong>
</p>
<p>
<code>opengl.glLightModelfv(pname:number, params:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glLightModeli</strong>
</p>
<p>
<code>opengl.glLightModeli(pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glLightModeliv</strong>
</p>
<p>
<code>opengl.glLightModeliv(pname:number, params:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glLightf</strong>
</p>
<p>
<code>opengl.glLightf(light:number, pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glLightfv</strong>
</p>
<p>
<code>opengl.glLightfv(light:number, pname:number, params:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glLighti</strong>
</p>
<p>
<code>opengl.glLighti(light:number, pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glLightiv</strong>
</p>
<p>
<code>opengl.glLightiv(light:number, pname:number, params:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glLineStipple</strong>
</p>
<p>
<code>opengl.glLineStipple(factor:number, pattern:number):map:void</code>
</p>
<p>
<strong>opengl.glLineWidth</strong>
</p>
<p>
<code>opengl.glLineWidth(width:number):map:void</code>
</p>
<p>
<strong>opengl.glListBase</strong>
</p>
<p>
<code>opengl.glListBase(base:number):map:void</code>
</p>
<p>
<strong>opengl.glLoadIdentity</strong>
</p>
<p>
<code>opengl.glLoadIdentity():void</code>
</p>
<p>
<strong>opengl.glLoadMatrixd</strong>
</p>
<p>
<code>opengl.glLoadMatrixd(m):void</code>
</p>
<p>
<strong>opengl.glLoadMatrixf</strong>
</p>
<p>
<code>opengl.glLoadMatrixf(m):void</code>
</p>
<p>
<strong>opengl.glLoadName</strong>
</p>
<p>
<code>opengl.glLoadName(name:number):map:void</code>
</p>
<p>
<strong>opengl.glLogicOp</strong>
</p>
<p>
<code>opengl.glLogicOp(opcode:number):map:void</code>
</p>
<p>
<strong>opengl.glMap1d</strong>
</p>
<p>
<code>opengl.glMap1d(target:number, u1:number, u2:number, stride:number, order:number, points:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glMap1f</strong>
</p>
<p>
<code>opengl.glMap1f(target:number, u1:number, u2:number, stride:number, order:number, points:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glMap2d</strong>
</p>
<p>
<code>opengl.glMap2d(target:number, u1:number, u2:number, ustride:number, uorder:number, v1:number, v2:number, vstride:number, vorder:number, points:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glMap2f</strong>
</p>
<p>
<code>opengl.glMap2f(target:number, u1:number, u2:number, ustride:number, uorder:number, v1:number, v2:number, vstride:number, vorder:number, points:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glMapGrid1d</strong>
</p>
<p>
<code>opengl.glMapGrid1d(un:number, u1:number, u2:number):map:void</code>
</p>
<p>
<strong>opengl.glMapGrid1f</strong>
</p>
<p>
<code>opengl.glMapGrid1f(un:number, u1:number, u2:number):map:void</code>
</p>
<p>
<strong>opengl.glMapGrid2d</strong>
</p>
<p>
<code>opengl.glMapGrid2d(un:number, u1:number, u2:number, vn:number, v1:number, v2:number):map:void</code>
</p>
<p>
<strong>opengl.glMapGrid2f</strong>
</p>
<p>
<code>opengl.glMapGrid2f(un:number, u1:number, u2:number, vn:number, v1:number, v2:number):map:void</code>
</p>
<p>
<strong>opengl.glMaterialf</strong>
</p>
<p>
<code>opengl.glMaterialf(face:number, pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glMaterialfv</strong>
</p>
<p>
<code>opengl.glMaterialfv(face:number, pname:number, params:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glMateriali</strong>
</p>
<p>
<code>opengl.glMateriali(face:number, pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glMaterialiv</strong>
</p>
<p>
<code>opengl.glMaterialiv(face:number, pname:number, params:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glMatrixMode</strong>
</p>
<p>
<code>opengl.glMatrixMode(mode:number):map:void</code>
</p>
<p>
<strong>opengl.glMultMatrixd</strong>
</p>
<p>
<code>opengl.glMultMatrixd(m):void</code>
</p>
<p>
<strong>opengl.glMultMatrixf</strong>
</p>
<p>
<code>opengl.glMultMatrixf(m):void</code>
</p>
<p>
<strong>opengl.glNewList</strong>
</p>
<p>
<code>opengl.glNewList(list:number, mode:number):map:void {block?}</code>
</p>
<p>
<strong>opengl.glNormal3b</strong>
</p>
<p>
<code>opengl.glNormal3b(nx:number, ny:number, nz:number):map:void</code>
</p>
<p>
<strong>opengl.glNormal3bv</strong>
</p>
<p>
<code>opengl.glNormal3bv(v:array@char:nomap):map:void</code>
</p>
<p>
<strong>opengl.glNormal3d</strong>
</p>
<p>
<code>opengl.glNormal3d(nx:number, ny:number, nz:number):map:void</code>
</p>
<p>
<strong>opengl.glNormal3dv</strong>
</p>
<p>
<code>opengl.glNormal3dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glNormal3f</strong>
</p>
<p>
<code>opengl.glNormal3f(nx:number, ny:number, nz:number):map:void</code>
</p>
<p>
<strong>opengl.glNormal3fv</strong>
</p>
<p>
<code>opengl.glNormal3fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glNormal3i</strong>
</p>
<p>
<code>opengl.glNormal3i(nx:number, ny:number, nz:number):map:void</code>
</p>
<p>
<strong>opengl.glNormal3iv</strong>
</p>
<p>
<code>opengl.glNormal3iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glNormal3s</strong>
</p>
<p>
<code>opengl.glNormal3s(nx:number, ny:number, nz:number):map:void</code>
</p>
<p>
<strong>opengl.glNormal3sv</strong>
</p>
<p>
<code>opengl.glNormal3sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glOrtho</strong>
</p>
<p>
<code>opengl.glOrtho(left:number, right:number, bottom:number, top:number, zNear:number, zFar:number):map:void</code>
</p>
<p>
<strong>opengl.glPassThrough</strong>
</p>
<p>
<code>opengl.glPassThrough(token:number):map:void</code>
</p>
<p>
<strong>opengl.glPixelMapfv</strong>
</p>
<p>
<code>opengl.glPixelMapfv(map:number, mapsize:number, values:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glPixelMapuiv</strong>
</p>
<p>
<code>opengl.glPixelMapuiv(map:number, mapsize:number, values:array@uint:nomap):map:void</code>
</p>
<p>
<strong>opengl.glPixelMapusv</strong>
</p>
<p>
<code>opengl.glPixelMapusv(map:number, mapsize:number, values:array@ushort:nomap):map:void</code>
</p>
<p>
<strong>opengl.glPixelStoref</strong>
</p>
<p>
<code>opengl.glPixelStoref(pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glPixelStorei</strong>
</p>
<p>
<code>opengl.glPixelStorei(pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glPixelTransferf</strong>
</p>
<p>
<code>opengl.glPixelTransferf(pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glPixelTransferi</strong>
</p>
<p>
<code>opengl.glPixelTransferi(pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glPixelZoom</strong>
</p>
<p>
<code>opengl.glPixelZoom(xfactor:number, yfactor:number):map:void</code>
</p>
<p>
<strong>opengl.glPointSize</strong>
</p>
<p>
<code>opengl.glPointSize(size:number):map:void</code>
</p>
<p>
<strong>opengl.glPolygonMode</strong>
</p>
<p>
<code>opengl.glPolygonMode(face:number, mode:number):map:void</code>
</p>
<p>
<strong>opengl.glPolygonOffset</strong>
</p>
<p>
<code>opengl.glPolygonOffset(factor:number, units:number):map:void</code>
</p>
<p>
<strong>opengl.glPolygonStipple</strong>
</p>
<p>
<code>opengl.glPolygonStipple(mask:array@uchar:nomap):map:void</code>
</p>
<p>
<strong>opengl.glPopAttrib</strong>
</p>
<p>
<code>opengl.glPopAttrib():void</code>
</p>
<p>
<strong>opengl.glPopClientAttrib</strong>
</p>
<p>
<code>opengl.glPopClientAttrib():void</code>
</p>
<p>
<strong>opengl.glPopMatrix</strong>
</p>
<p>
<code>opengl.glPopMatrix():void</code>
</p>
<p>
<strong>opengl.glPopName</strong>
</p>
<p>
<code>opengl.glPopName():void</code>
</p>
<p>
<strong>opengl.glPrioritizeTextures</strong>
</p>
<p>
<code>opengl.glPrioritizeTextures(textures:array@uint:nomap, priorities:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glPushAttrib</strong>
</p>
<p>
<code>opengl.glPushAttrib(mask:number):map:void {block?}</code>
</p>
<p>
<strong>opengl.glPushClientAttrib</strong>
</p>
<p>
<code>opengl.glPushClientAttrib(mask:number):map:void {block?}</code>
</p>
<p>
<strong>opengl.glPushMatrix</strong>
</p>
<p>
<code>opengl.glPushMatrix():void {block?}</code>
</p>
<p>
<strong>opengl.glPushName</strong>
</p>
<p>
<code>opengl.glPushName(name:number):map:void {block?}</code>
</p>
<p>
<strong>opengl.glRasterPos2d</strong>
</p>
<p>
<code>opengl.glRasterPos2d(x:number, y:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos2dv</strong>
</p>
<p>
<code>opengl.glRasterPos2dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos2f</strong>
</p>
<p>
<code>opengl.glRasterPos2f(x:number, y:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos2fv</strong>
</p>
<p>
<code>opengl.glRasterPos2fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos2i</strong>
</p>
<p>
<code>opengl.glRasterPos2i(x:number, y:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos2iv</strong>
</p>
<p>
<code>opengl.glRasterPos2iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos2s</strong>
</p>
<p>
<code>opengl.glRasterPos2s(x:number, y:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos2sv</strong>
</p>
<p>
<code>opengl.glRasterPos2sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos3d</strong>
</p>
<p>
<code>opengl.glRasterPos3d(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos3dv</strong>
</p>
<p>
<code>opengl.glRasterPos3dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos3f</strong>
</p>
<p>
<code>opengl.glRasterPos3f(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos3fv</strong>
</p>
<p>
<code>opengl.glRasterPos3fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos3i</strong>
</p>
<p>
<code>opengl.glRasterPos3i(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos3iv</strong>
</p>
<p>
<code>opengl.glRasterPos3iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos3s</strong>
</p>
<p>
<code>opengl.glRasterPos3s(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos3sv</strong>
</p>
<p>
<code>opengl.glRasterPos3sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos4d</strong>
</p>
<p>
<code>opengl.glRasterPos4d(x:number, y:number, z:number, w:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos4dv</strong>
</p>
<p>
<code>opengl.glRasterPos4dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos4f</strong>
</p>
<p>
<code>opengl.glRasterPos4f(x:number, y:number, z:number, w:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos4fv</strong>
</p>
<p>
<code>opengl.glRasterPos4fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos4i</strong>
</p>
<p>
<code>opengl.glRasterPos4i(x:number, y:number, z:number, w:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos4iv</strong>
</p>
<p>
<code>opengl.glRasterPos4iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos4s</strong>
</p>
<p>
<code>opengl.glRasterPos4s(x:number, y:number, z:number, w:number):map:void</code>
</p>
<p>
<strong>opengl.glRasterPos4sv</strong>
</p>
<p>
<code>opengl.glRasterPos4sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glReadBuffer</strong>
</p>
<p>
<code>opengl.glReadBuffer(mode:number):map:void</code>
</p>
<p>
<strong>opengl.glReadPixels</strong>
</p>
<p>
<code>opengl.glReadPixels(x:number, y:number, width:number, height:number, format:symbol):map {block?}</code>
</p>
<p>
<strong>opengl.glRectd</strong>
</p>
<p>
<code>opengl.glRectd(x1:number, y1:number, x2:number, y2:number):map:void</code>
</p>
<p>
<strong>opengl.glRectdv</strong>
</p>
<p>
<code>opengl.glRectdv(v1:array@double:nomap, v2:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRectf</strong>
</p>
<p>
<code>opengl.glRectf(x1:number, y1:number, x2:number, y2:number):map:void</code>
</p>
<p>
<strong>opengl.glRectfv</strong>
</p>
<p>
<code>opengl.glRectfv(v1:array@float:nomap, v2:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRecti</strong>
</p>
<p>
<code>opengl.glRecti(x1:number, y1:number, x2:number, y2:number):map:void</code>
</p>
<p>
<strong>opengl.glRectiv</strong>
</p>
<p>
<code>opengl.glRectiv(v1:array@int:nomap, v2:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRects</strong>
</p>
<p>
<code>opengl.glRects(x1:number, y1:number, x2:number, y2:number):map:void</code>
</p>
<p>
<strong>opengl.glRectsv</strong>
</p>
<p>
<code>opengl.glRectsv(v1:array@short:nomap, v2:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glRenderMode</strong>
</p>
<p>
<code>opengl.glRenderMode(mode:number):map {block?}</code>
</p>
<p>
<strong>opengl.glRotated</strong>
</p>
<p>
<code>opengl.glRotated(angle:number, x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glRotatef</strong>
</p>
<p>
<code>opengl.glRotatef(angle:number, x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glScaled</strong>
</p>
<p>
<code>opengl.glScaled(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glScalef</strong>
</p>
<p>
<code>opengl.glScalef(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glScissor</strong>
</p>
<p>
<code>opengl.glScissor(x:number, y:number, width:number, height:number):map:void</code>
</p>
<p>
<strong>opengl.glSelectBuffer</strong>
</p>
<p>
<code>opengl.glSelectBuffer(buffer:array@uint:nomap:nil):void</code>
</p>
<p>
<strong>opengl.glShadeModel</strong>
</p>
<p>
<code>opengl.glShadeModel(mode:number):map:void</code>
</p>
<p>
<strong>opengl.glStencilFunc</strong>
</p>
<p>
<code>opengl.glStencilFunc(func:number, ref:number, mask:number):map:void</code>
</p>
<p>
<strong>opengl.glStencilMask</strong>
</p>
<p>
<code>opengl.glStencilMask(mask:number):map:void</code>
</p>
<p>
<strong>opengl.glStencilOp</strong>
</p>
<p>
<code>opengl.glStencilOp(fail:number, zfail:number, zpass:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord1d</strong>
</p>
<p>
<code>opengl.glTexCoord1d(s:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord1dv</strong>
</p>
<p>
<code>opengl.glTexCoord1dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord1f</strong>
</p>
<p>
<code>opengl.glTexCoord1f(s:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord1fv</strong>
</p>
<p>
<code>opengl.glTexCoord1fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord1i</strong>
</p>
<p>
<code>opengl.glTexCoord1i(s:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord1iv</strong>
</p>
<p>
<code>opengl.glTexCoord1iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord1s</strong>
</p>
<p>
<code>opengl.glTexCoord1s(s:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord1sv</strong>
</p>
<p>
<code>opengl.glTexCoord1sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord2d</strong>
</p>
<p>
<code>opengl.glTexCoord2d(s:number, t:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord2dv</strong>
</p>
<p>
<code>opengl.glTexCoord2dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord2f</strong>
</p>
<p>
<code>opengl.glTexCoord2f(s:number, t:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord2fv</strong>
</p>
<p>
<code>opengl.glTexCoord2fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord2i</strong>
</p>
<p>
<code>opengl.glTexCoord2i(s:number, t:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord2iv</strong>
</p>
<p>
<code>opengl.glTexCoord2iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord2s</strong>
</p>
<p>
<code>opengl.glTexCoord2s(s:number, t:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord2sv</strong>
</p>
<p>
<code>opengl.glTexCoord2sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord3d</strong>
</p>
<p>
<code>opengl.glTexCoord3d(s:number, t:number, r:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord3dv</strong>
</p>
<p>
<code>opengl.glTexCoord3dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord3f</strong>
</p>
<p>
<code>opengl.glTexCoord3f(s:number, t:number, r:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord3fv</strong>
</p>
<p>
<code>opengl.glTexCoord3fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord3i</strong>
</p>
<p>
<code>opengl.glTexCoord3i(s:number, t:number, r:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord3iv</strong>
</p>
<p>
<code>opengl.glTexCoord3iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord3s</strong>
</p>
<p>
<code>opengl.glTexCoord3s(s:number, t:number, r:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord3sv</strong>
</p>
<p>
<code>opengl.glTexCoord3sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord4d</strong>
</p>
<p>
<code>opengl.glTexCoord4d(s:number, t:number, r:number, q:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord4dv</strong>
</p>
<p>
<code>opengl.glTexCoord4dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord4f</strong>
</p>
<p>
<code>opengl.glTexCoord4f(s:number, t:number, r:number, q:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord4fv</strong>
</p>
<p>
<code>opengl.glTexCoord4fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord4i</strong>
</p>
<p>
<code>opengl.glTexCoord4i(s:number, t:number, r:number, q:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord4iv</strong>
</p>
<p>
<code>opengl.glTexCoord4iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord4s</strong>
</p>
<p>
<code>opengl.glTexCoord4s(s:number, t:number, r:number, q:number):map:void</code>
</p>
<p>
<strong>opengl.glTexCoord4sv</strong>
</p>
<p>
<code>opengl.glTexCoord4sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexEnvf</strong>
</p>
<p>
<code>opengl.glTexEnvf(target:number, pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glTexEnvfv</strong>
</p>
<p>
<code>opengl.glTexEnvfv(target:number, pname:number, params:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexEnvi</strong>
</p>
<p>
<code>opengl.glTexEnvi(target:number, pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glTexEnviv</strong>
</p>
<p>
<code>opengl.glTexEnviv(target:number, pname:number, params:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexGend</strong>
</p>
<p>
<code>opengl.glTexGend(coord:number, pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glTexGendv</strong>
</p>
<p>
<code>opengl.glTexGendv(coord:number, pname:number, params:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexGenf</strong>
</p>
<p>
<code>opengl.glTexGenf(coord:number, pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glTexGenfv</strong>
</p>
<p>
<code>opengl.glTexGenfv(coord:number, pname:number, params:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexGeni</strong>
</p>
<p>
<code>opengl.glTexGeni(coord:number, pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glTexGeniv</strong>
</p>
<p>
<code>opengl.glTexGeniv(coord:number, pname:number, params:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexImage1D</strong>
</p>
<p>
<code>opengl.glTexImage1D(target:number, level:number, internalformat:number, width:number, border:number, format:number, type:number, pixels):map:void</code>
</p>
<p>
<strong>opengl.glTexImage1DFromImage</strong>
</p>
<p>
<code>opengl.glTexImage1DFromImage(target:number, level:number, internalformat:number, border:number, image:image):map:void</code>
</p>
<p>
<strong>opengl.glTexImage2D</strong>
</p>
<p>
<code>opengl.glTexImage2D(target:number, level:number, internalformat:number, width:number, height:number, border:number, format:number, type:number, pixels):map:void</code>
</p>
<p>
<strong>opengl.glTexImage2DFromImage</strong>
</p>
<p>
<code>opengl.glTexImage2DFromImage(target:number, level:number, internalformat:number, border:number, image:image):map:void</code>
</p>
<p>
<strong>opengl.glTexParameterf</strong>
</p>
<p>
<code>opengl.glTexParameterf(target:number, pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glTexParameterfv</strong>
</p>
<p>
<code>opengl.glTexParameterfv(target:number, pname:number, params:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexParameteri</strong>
</p>
<p>
<code>opengl.glTexParameteri(target:number, pname:number, param:number):map:void</code>
</p>
<p>
<strong>opengl.glTexParameteriv</strong>
</p>
<p>
<code>opengl.glTexParameteriv(target:number, pname:number, params:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glTexSubImage1D</strong>
</p>
<p>
<code>opengl.glTexSubImage1D(target:number, level:number, xoffset:number, width:number, format:number, type:number, pixels):map:void</code>
</p>
<p>
<strong>opengl.glTexSubImage1DFromImage</strong>
</p>
<p>
<code>opengl.glTexSubImage1DFromImage(target:number, level:number, xoffset:number, image:image):map:void</code>
</p>
<p>
<strong>opengl.glTexSubImage2D</strong>
</p>
<p>
<code>opengl.glTexSubImage2D(target:number, level:number, xoffset:number, yoffset:number, width:number, height:number, format:number, type:number, pixels):map:void</code>
</p>
<p>
<strong>opengl.glTexSubImage2DFromImage</strong>
</p>
<p>
<code>opengl.glTexSubImage2DFromImage(target:number, level:number, xoffset:number, yoffset:number, image:image):map:void</code>
</p>
<p>
<strong>opengl.glTranslated</strong>
</p>
<p>
<code>opengl.glTranslated(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glTranslatef</strong>
</p>
<p>
<code>opengl.glTranslatef(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex2d</strong>
</p>
<p>
<code>opengl.glVertex2d(x:number, y:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex2dv</strong>
</p>
<p>
<code>opengl.glVertex2dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glVertex2f</strong>
</p>
<p>
<code>opengl.glVertex2f(x:number, y:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex2fv</strong>
</p>
<p>
<code>opengl.glVertex2fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glVertex2i</strong>
</p>
<p>
<code>opengl.glVertex2i(x:number, y:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex2iv</strong>
</p>
<p>
<code>opengl.glVertex2iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glVertex2s</strong>
</p>
<p>
<code>opengl.glVertex2s(x:number, y:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex2sv</strong>
</p>
<p>
<code>opengl.glVertex2sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glVertex3d</strong>
</p>
<p>
<code>opengl.glVertex3d(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex3dv</strong>
</p>
<p>
<code>opengl.glVertex3dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glVertex3f</strong>
</p>
<p>
<code>opengl.glVertex3f(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex3fv</strong>
</p>
<p>
<code>opengl.glVertex3fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glVertex3i</strong>
</p>
<p>
<code>opengl.glVertex3i(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex3iv</strong>
</p>
<p>
<code>opengl.glVertex3iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glVertex3s</strong>
</p>
<p>
<code>opengl.glVertex3s(x:number, y:number, z:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex3sv</strong>
</p>
<p>
<code>opengl.glVertex3sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glVertex4d</strong>
</p>
<p>
<code>opengl.glVertex4d(x:number, y:number, z:number, w:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex4dv</strong>
</p>
<p>
<code>opengl.glVertex4dv(v:array@double:nomap):map:void</code>
</p>
<p>
<strong>opengl.glVertex4f</strong>
</p>
<p>
<code>opengl.glVertex4f(x:number, y:number, z:number, w:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex4fv</strong>
</p>
<p>
<code>opengl.glVertex4fv(v:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glVertex4i</strong>
</p>
<p>
<code>opengl.glVertex4i(x:number, y:number, z:number, w:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex4iv</strong>
</p>
<p>
<code>opengl.glVertex4iv(v:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glVertex4s</strong>
</p>
<p>
<code>opengl.glVertex4s(x:number, y:number, z:number, w:number):map:void</code>
</p>
<p>
<strong>opengl.glVertex4sv</strong>
</p>
<p>
<code>opengl.glVertex4sv(v:array@short:nomap):map:void</code>
</p>
<p>
<strong>opengl.glViewport</strong>
</p>
<p>
<code>opengl.glViewport(x:number, y:number, width:number, height:number):map:void</code>
</p>
<p>
<strong>opengl.glGetAttachedShaders</strong>
</p>
<p>
<code>opengl.glGetAttachedShaders(program:number, maxCount:number, count[]:number, shaders:array@uint:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetShaderInfoLog</strong>
</p>
<p>
<code>opengl.glGetShaderInfoLog(shader:number, bufSize:number, length[]:number, infoLog:array@char:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetProgramInfoLog</strong>
</p>
<p>
<code>opengl.glGetProgramInfoLog(program:number, bufSize:number, length[]:number, infoLog:array@char:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetUniformLocation</strong>
</p>
<p>
<code>opengl.glGetUniformLocation(program:number, name:array@char:nomap):map {block?}</code>
</p>
<p>
<strong>opengl.glGetActiveUniform</strong>
</p>
<p>
<code>opengl.glGetActiveUniform(program:number, index:number, bufSize:number, length[]:number, size:array@int:nomap, type[]:number, name:array@char:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetUniformfv</strong>
</p>
<p>
<code>opengl.glGetUniformfv(program:number, location:number, params:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetUniformiv</strong>
</p>
<p>
<code>opengl.glGetUniformiv(program:number, location:number, params:array@int:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetShaderSource</strong>
</p>
<p>
<code>opengl.glGetShaderSource(shader:number, bufSize:number, length[]:number, source:array@char:nomap):map:void</code>
</p>
<p>
<strong>opengl.glBindAttribLocation</strong>
</p>
<p>
<code>opengl.glBindAttribLocation(program:number, index:number, name:array@char:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetActiveAttrib</strong>
</p>
<p>
<code>opengl.glGetActiveAttrib(program:number, index:number, bufSize:number, length[]:number, size:array@int:nomap, type[]:number, name:array@char:nomap):map:void</code>
</p>
<p>
<strong>opengl.glGetAttribLocation</strong>
</p>
<p>
<code>opengl.glGetAttribLocation(program:number, name:array@char:nomap):map {block?}</code>
</p>
<p>
<strong>opengl.glUniformMatrix2x3fv</strong>
</p>
<p>
<code>opengl.glUniformMatrix2x3fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glUniformMatrix3x2fv</strong>
</p>
<p>
<code>opengl.glUniformMatrix3x2fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glUniformMatrix2x4fv</strong>
</p>
<p>
<code>opengl.glUniformMatrix2x4fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glUniformMatrix4x2fv</strong>
</p>
<p>
<code>opengl.glUniformMatrix4x2fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glUniformMatrix3x4fv</strong>
</p>
<p>
<code>opengl.glUniformMatrix3x4fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code>
</p>
<p>
<strong>opengl.glUniformMatrix4x3fv</strong>
</p>
<p>
<code>opengl.glUniformMatrix4x3fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code>
</p>
<p />

{% endraw %}
