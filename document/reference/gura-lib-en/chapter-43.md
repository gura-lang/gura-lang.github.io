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
<p>
<div class="h5">opengl.glAccum</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glAccum(op:number, value:number):map:void</code></div>
operate on the accumulation buffer
</p>
<p>
<div class="h5">opengl.glAlphaFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glAlphaFunc(func:number, ref:number):map:void</code></div>
specify the alpha test function
</p>
<p>
<div class="h5">opengl.glAreTexturesResident</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glAreTexturesResident(textures:array@uint32:nomap):map {block?}</code></div>
determine if textures are loaded in texture memory
</p>
<p>
<div class="h5">opengl.glArrayElement</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glArrayElement(i:number):map:void</code></div>
render a vertex using the specified vertex array element
</p>
<p>
<div class="h5">opengl.glBegin</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glBegin(mode:number):map:void {block?}</code></div>
delimit the vertices of a primitive or a group of like primitives
</p>
<p>
<div class="h5">opengl.glBindTexture</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glBindTexture(target:number, texture:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glBitmap</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glBitmap(width:number, height:number, xorig:number, yorig:number, xmove:number, ymove:number, bitmap:array@uint8:nil:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glBlendFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glBlendFunc(sfactor:number, dfactor:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glCallList</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glCallList(list:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glCallLists</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glCallLists(type:number, lists[]:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glClear</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glClear(mask:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glClearAccum</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glClearAccum(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glClearColor</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glClearColor(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glClearDepth</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glClearDepth(depth:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glClearIndex</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glClearIndex(c:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glClearStencil</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glClearStencil(s:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glClipPlane</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glClipPlane(plane:number, equation:array@double:nomap):map:void {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glColor3b</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3b(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3bv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3bv(v:array@int8:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3d(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3f(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3i(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3s(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3ub</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3ub(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3ubv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3ubv(v:array@uint8:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3ui</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3ui(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3uiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3uiv(v:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3us</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3us(red:number, green:number, blue:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor3usv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor3usv(v:array@uint16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4b</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4b(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4bv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4bv(v:array@int8:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4d(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4f(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4i(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4s(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4ub</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4ub(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4ubv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4ubv(v:array@uint8:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4ui</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4ui(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4uiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4uiv(v:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4us</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4us(red:number, green:number, blue:number, alpha:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColor4usv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColor4usv(v:array@uint16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColorMask</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColorMask(red:boolean, green:boolean, blue:boolean, alpha:boolean):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glColorMaterial</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glColorMaterial(face:number, mode:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glCopyPixels</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glCopyPixels(x:number, y:number, width:number, height:number, type:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glCopyTexImage1D</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glCopyTexImage1D(target:number, level:number, internalformat:number, x:number, y:number, width:number, border:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glCopyTexImage2D</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glCopyTexImage2D(target:number, level:number, internalformat:number, x:number, y:number, width:number, height:number, border:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glCopyTexSubImage1D</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glCopyTexSubImage1D(target:number, level:number, xoffset:number, x:number, y:number, width:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glCopyTexSubImage2D</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glCopyTexSubImage2D(target:number, level:number, xoffset:number, yoffset:number, x:number, y:number, width:number, height:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glCullFace</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glCullFace(mode:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glDeleteLists</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glDeleteLists(list:number, range:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glDeleteTextures</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glDeleteTextures(textures:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glDepthFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glDepthFunc(func:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glDepthMask</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glDepthMask(flag:boolean):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glDepthRange</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glDepthRange(zNear:number, zFar:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glDisable</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glDisable(cap:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glDisableClientState</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glDisableClientState(array:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glDrawArrays</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glDrawArrays(mode:number, first:number, count:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glDrawBuffer</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glDrawBuffer(mode:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glDrawPixels</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glDrawPixels(width:number, height:number, format:number, type:number, pixels:array:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glDrawPixelsFromImage</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glDrawPixelsFromImage(image:image):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEdgeFlag</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEdgeFlag(flag:boolean):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEdgeFlagv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEdgeFlagv(flag[]:boolean):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEnable</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEnable(cap:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEnableClientState</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEnableClientState(array:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEnd</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEnd():void</code></div>

</p>
<p>
<div class="h5">opengl.glEndList</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEndList():void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalCoord1d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalCoord1d(u:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalCoord1dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalCoord1dv(u:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalCoord1f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalCoord1f(u:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalCoord1fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalCoord1fv(u:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalCoord2d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalCoord2d(u:number, v:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalCoord2dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalCoord2dv(u:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalCoord2f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalCoord2f(u:number, v:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalCoord2fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalCoord2fv(u:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalMesh1</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalMesh1(mode:number, i1:number, i2:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalMesh2</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalMesh2(mode:number, i1:number, i2:number, j1:number, j2:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalPoint1</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalPoint1(i:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glEvalPoint2</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glEvalPoint2(i:number, j:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glFeedbackBuffer</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glFeedbackBuffer(type:number, buffer:array@float:nil:nomap):void</code></div>

</p>
<p>
<div class="h5">opengl.glFinish</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glFinish():void</code></div>

</p>
<p>
<div class="h5">opengl.glFlush</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glFlush():void</code></div>

</p>
<p>
<div class="h5">opengl.glFogf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glFogf(pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glFogfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glFogfv(pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glFogi</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glFogi(pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glFogiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glFogiv(pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glFrontFace</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glFrontFace(mode:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glFrustum</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glFrustum(left:number, right:number, bottom:number, top:number, zNear:number, zFar:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGenLists</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGenLists(range:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGenTextures</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGenTextures(n:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetBooleanv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetBooleanv(pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetClipPlane</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetClipPlane(plane:number):map</code></div>

</p>
<p>
<div class="h5">opengl.glGetDoublev</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetDoublev(pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetError</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetError() {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetFloatv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetFloatv(pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetIntegerv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetIntegerv(pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetLightfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetLightfv(light:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetLightiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetLightiv(light:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetMapdv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetMapdv(target:number, query:number, v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGetMapfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetMapfv(target:number, query:number, v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGetMapiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetMapiv(target:number, query:number, v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGetMaterialfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetMaterialfv(face:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetMaterialiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetMaterialiv(face:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetPixelMapfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetPixelMapfv(map:number, values:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGetPixelMapuiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetPixelMapuiv(map:number, values:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGetPixelMapusv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetPixelMapusv(map:number, values:array@uint16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGetPolygonStipple</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetPolygonStipple():map</code></div>

</p>
<p>
<div class="h5">opengl.glGetString</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetString(name:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetTexEnvfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetTexEnvfv(target:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetTexEnviv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetTexEnviv(target:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetTexGendv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetTexGendv(coord:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetTexGenfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetTexGenfv(coord:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetTexGeniv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetTexGeniv(coord:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetTexLevelParameterfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetTexLevelParameterfv(target:number, level:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetTexLevelParameteriv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetTexLevelParameteriv(target:number, level:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetTexParameterfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetTexParameterfv(target:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetTexParameteriv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetTexParameteriv(target:number, pname:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glHint</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glHint(target:number, mode:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glIndexMask</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIndexMask(mask:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glIndexd</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIndexd(c:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glIndexdv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIndexdv(c:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glIndexf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIndexf(c:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glIndexfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIndexfv(c:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glIndexi</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIndexi(c:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glIndexiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIndexiv(c:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glIndexs</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIndexs(c:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glIndexsv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIndexsv(c:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glIndexub</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIndexub(c:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glIndexubv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIndexubv(c:array@uint8:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glInitNames</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glInitNames():void</code></div>

</p>
<p>
<div class="h5">opengl.glIsEnabled</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIsEnabled(cap:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glIsList</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIsList(list:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glIsTexture</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glIsTexture(texture:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glLightModelf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLightModelf(pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glLightModelfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLightModelfv(pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glLightModeli</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLightModeli(pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glLightModeliv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLightModeliv(pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glLightf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLightf(light:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glLightfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLightfv(light:number, pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glLighti</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLighti(light:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glLightiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLightiv(light:number, pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glLineStipple</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLineStipple(factor:number, pattern:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glLineWidth</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLineWidth(width:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glListBase</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glListBase(base:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glLoadIdentity</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLoadIdentity():void</code></div>

</p>
<p>
<div class="h5">opengl.glLoadMatrixd</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLoadMatrixd(m):void</code></div>

</p>
<p>
<div class="h5">opengl.glLoadMatrixf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLoadMatrixf(m):void</code></div>

</p>
<p>
<div class="h5">opengl.glLoadName</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLoadName(name:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glLogicOp</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glLogicOp(opcode:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMap1d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMap1d(target:number, u1:number, u2:number, stride:number, order:number, points:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMap1f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMap1f(target:number, u1:number, u2:number, stride:number, order:number, points:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMap2d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMap2d(target:number, u1:number, u2:number, ustride:number, uorder:number, v1:number, v2:number, vstride:number, vorder:number, points:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMap2f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMap2f(target:number, u1:number, u2:number, ustride:number, uorder:number, v1:number, v2:number, vstride:number, vorder:number, points:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMapGrid1d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMapGrid1d(un:number, u1:number, u2:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMapGrid1f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMapGrid1f(un:number, u1:number, u2:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMapGrid2d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMapGrid2d(un:number, u1:number, u2:number, vn:number, v1:number, v2:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMapGrid2f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMapGrid2f(un:number, u1:number, u2:number, vn:number, v1:number, v2:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMaterialf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMaterialf(face:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMaterialfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMaterialfv(face:number, pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMateriali</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMateriali(face:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMaterialiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMaterialiv(face:number, pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMatrixMode</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMatrixMode(mode:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glMultMatrixd</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMultMatrixd(m):void</code></div>

</p>
<p>
<div class="h5">opengl.glMultMatrixf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glMultMatrixf(m):void</code></div>

</p>
<p>
<div class="h5">opengl.glNewList</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glNewList(list:number, mode:number):map:void {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glNormal3b</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glNormal3b(nx:number, ny:number, nz:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glNormal3bv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glNormal3bv(v:array@int8:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glNormal3d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glNormal3d(nx:number, ny:number, nz:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glNormal3dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glNormal3dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glNormal3f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glNormal3f(nx:number, ny:number, nz:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glNormal3fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glNormal3fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glNormal3i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glNormal3i(nx:number, ny:number, nz:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glNormal3iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glNormal3iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glNormal3s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glNormal3s(nx:number, ny:number, nz:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glNormal3sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glNormal3sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glOrtho</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glOrtho(left:number, right:number, bottom:number, top:number, zNear:number, zFar:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPassThrough</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPassThrough(token:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPixelMapfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPixelMapfv(map:number, mapsize:number, values:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPixelMapuiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPixelMapuiv(map:number, mapsize:number, values:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPixelMapusv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPixelMapusv(map:number, mapsize:number, values:array@uint16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPixelStoref</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPixelStoref(pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPixelStorei</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPixelStorei(pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPixelTransferf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPixelTransferf(pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPixelTransferi</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPixelTransferi(pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPixelZoom</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPixelZoom(xfactor:number, yfactor:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPointSize</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPointSize(size:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPolygonMode</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPolygonMode(face:number, mode:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPolygonOffset</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPolygonOffset(factor:number, units:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPolygonStipple</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPolygonStipple(mask:array@uint8:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPopAttrib</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPopAttrib():void</code></div>

</p>
<p>
<div class="h5">opengl.glPopClientAttrib</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPopClientAttrib():void</code></div>

</p>
<p>
<div class="h5">opengl.glPopMatrix</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPopMatrix():void</code></div>

</p>
<p>
<div class="h5">opengl.glPopName</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPopName():void</code></div>

</p>
<p>
<div class="h5">opengl.glPrioritizeTextures</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPrioritizeTextures(textures:array@uint32:nomap, priorities:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glPushAttrib</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPushAttrib(mask:number):map:void {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glPushClientAttrib</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPushClientAttrib(mask:number):map:void {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glPushMatrix</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPushMatrix():void {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glPushName</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glPushName(name:number):map:void {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos2d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos2d(x:number, y:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos2dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos2dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos2f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos2f(x:number, y:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos2fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos2fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos2i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos2i(x:number, y:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos2iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos2iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos2s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos2s(x:number, y:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos2sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos2sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos3d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos3d(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos3dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos3dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos3f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos3f(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos3fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos3fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos3i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos3i(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos3iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos3iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos3s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos3s(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos3sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos3sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos4d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos4d(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos4dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos4dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos4f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos4f(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos4fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos4fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos4i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos4i(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos4iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos4iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos4s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos4s(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRasterPos4sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRasterPos4sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glReadBuffer</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glReadBuffer(mode:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glReadPixels</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glReadPixels(x:number, y:number, width:number, height:number, format:symbol):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glRectd</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRectd(x1:number, y1:number, x2:number, y2:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRectdv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRectdv(v1:array@double:nomap, v2:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRectf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRectf(x1:number, y1:number, x2:number, y2:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRectfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRectfv(v1:array@float:nomap, v2:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRecti</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRecti(x1:number, y1:number, x2:number, y2:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRectiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRectiv(v1:array@int32:nomap, v2:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRects</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRects(x1:number, y1:number, x2:number, y2:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRectsv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRectsv(v1:array@int16:nomap, v2:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRenderMode</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRenderMode(mode:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glRotated</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRotated(angle:number, x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glRotatef</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glRotatef(angle:number, x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glScaled</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glScaled(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glScalef</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glScalef(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glScissor</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glScissor(x:number, y:number, width:number, height:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glSelectBuffer</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glSelectBuffer(buffer:array@uint32:nil:nomap):void</code></div>

</p>
<p>
<div class="h5">opengl.glShadeModel</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glShadeModel(mode:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glStencilFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glStencilFunc(func:number, ref:number, mask:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glStencilMask</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glStencilMask(mask:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glStencilOp</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glStencilOp(fail:number, zfail:number, zpass:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord1d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord1d(s:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord1dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord1dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord1f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord1f(s:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord1fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord1fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord1i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord1i(s:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord1iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord1iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord1s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord1s(s:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord1sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord1sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord2d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord2d(s:number, t:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord2dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord2dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord2f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord2f(s:number, t:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord2fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord2fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord2i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord2i(s:number, t:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord2iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord2iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord2s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord2s(s:number, t:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord2sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord2sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord3d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord3d(s:number, t:number, r:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord3dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord3dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord3f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord3f(s:number, t:number, r:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord3fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord3fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord3i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord3i(s:number, t:number, r:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord3iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord3iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord3s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord3s(s:number, t:number, r:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord3sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord3sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord4d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord4d(s:number, t:number, r:number, q:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord4dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord4dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord4f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord4f(s:number, t:number, r:number, q:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord4fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord4fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord4i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord4i(s:number, t:number, r:number, q:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord4iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord4iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord4s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord4s(s:number, t:number, r:number, q:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexCoord4sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexCoord4sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexEnvf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexEnvf(target:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexEnvfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexEnvfv(target:number, pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexEnvi</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexEnvi(target:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexEnviv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexEnviv(target:number, pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexGend</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexGend(coord:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexGendv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexGendv(coord:number, pname:number, params:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexGenf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexGenf(coord:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexGenfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexGenfv(coord:number, pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexGeni</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexGeni(coord:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexGeniv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexGeniv(coord:number, pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexImage1D</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexImage1D(target:number, level:number, internalformat:number, width:number, border:number, format:number, type:number, pixels:array:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexImage1DFromImage</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexImage1DFromImage(target:number, level:number, internalformat:number, border:number, image:image):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexImage2D</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexImage2D(target:number, level:number, internalformat:number, width:number, height:number, border:number, format:number, type:number, pixels:array:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexImage2DFromImage</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexImage2DFromImage(target:number, level:number, internalformat:number, border:number, image:image):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexParameterf</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexParameterf(target:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexParameterfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexParameterfv(target:number, pname:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexParameteri</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexParameteri(target:number, pname:number, param:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexParameteriv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexParameteriv(target:number, pname:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexSubImage1D</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexSubImage1D(target:number, level:number, xoffset:number, width:number, format:number, type:number, pixels:array:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexSubImage1DFromImage</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexSubImage1DFromImage(target:number, level:number, xoffset:number, image:image):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexSubImage2D</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexSubImage2D(target:number, level:number, xoffset:number, yoffset:number, width:number, height:number, format:number, type:number, pixels:array:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTexSubImage2DFromImage</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTexSubImage2DFromImage(target:number, level:number, xoffset:number, yoffset:number, image:image):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTranslated</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTranslated(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glTranslatef</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glTranslatef(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex2d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex2d(x:number, y:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex2dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex2dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex2f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex2f(x:number, y:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex2fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex2fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex2i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex2i(x:number, y:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex2iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex2iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex2s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex2s(x:number, y:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex2sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex2sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex3d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex3d(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex3dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex3dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex3f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex3f(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex3fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex3fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex3i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex3i(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex3iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex3iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex3s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex3s(x:number, y:number, z:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex3sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex3sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex4d</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex4d(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex4dv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex4dv(v:array@double:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex4f</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex4f(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex4fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex4fv(v:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex4i</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex4i(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex4iv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex4iv(v:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex4s</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex4s(x:number, y:number, z:number, w:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glVertex4sv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glVertex4sv(v:array@int16:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glViewport</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glViewport(x:number, y:number, width:number, height:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGetAttachedShaders</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetAttachedShaders(program:number, maxCount:number, count[]:number, shaders:array@uint32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGetShaderInfoLog</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetShaderInfoLog(shader:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetProgramInfoLog</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetProgramInfoLog(program:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetUniformLocation</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetUniformLocation(program:number, name:string):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetActiveUniform</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetActiveUniform(program:number, index:number):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glGetUniformfv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetUniformfv(program:number, location:number, params:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGetUniformiv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetUniformiv(program:number, location:number, params:array@int32:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGetShaderSource</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetShaderSource(shader:number):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glBindAttribLocation</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glBindAttribLocation(program:number, index:number, name:string):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glGetActiveAttrib</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetActiveAttrib(program:number, index:number):map</code></div>

</p>
<p>
<div class="h5">opengl.glGetAttribLocation</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glGetAttribLocation(program:number, name:string):map {block?}</code></div>

</p>
<p>
<div class="h5">opengl.glUniformMatrix2x3fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glUniformMatrix2x3fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glUniformMatrix3x2fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glUniformMatrix3x2fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glUniformMatrix2x4fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glUniformMatrix2x4fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glUniformMatrix4x2fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glUniformMatrix4x2fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glUniformMatrix3x4fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glUniformMatrix3x4fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
<p>
<div class="h5">opengl.glUniformMatrix4x3fv</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>opengl.glUniformMatrix4x3fv(location:number, count:number, transpose:boolean, value:array@float:nomap):map:void</code></div>

</p>
{% endraw %}
