---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">24</span><a name="anchor-24"></a>glut Module</h1>
<h2><span class="caption-index-2">24.1</span><a name="anchor-24-1"></a>Overview</h2>
<p>
The <code>glut</code> module provides functions of GLUT library.
</p>
<h2><span class="caption-index-2">24.2</span><a name="anchor-24-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">glut.glutInit</strong></div>
<div style="margin-bottom:1em"><code>glut.glutInit(argv[]:string) {block?}</code></div>
<code>glutInit</code> is used to initialize the GLUT library.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutInitDisplayMode</strong></div>
<div style="margin-bottom:1em"><code>glut.glutInitDisplayMode(mode:number):map:void</code></div>
<code>glutInitDisplayMode</code> sets the <em>initial display mode</em>.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutInitDisplayString</strong></div>
<div style="margin-bottom:1em"><code>glut.glutInitDisplayString(string:string):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutInitWindowPosition</strong></div>
<div style="margin-bottom:1em"><code>glut.glutInitWindowPosition(x:number, y:number):map:void</code></div>
<code>glutInitWindowPosition</code> sets the initial window position.	
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutInitWindowSize</strong></div>
<div style="margin-bottom:1em"><code>glut.glutInitWindowSize(width:number, height:number):map:void</code></div>
<code>glutInitWindowSize</code> sets the initial window size.	
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutMainLoop</strong></div>
<div style="margin-bottom:1em"><code>glut.glutMainLoop():void</code></div>
<code>glutMainLoop</code> enters the GLUT event processing loop.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutCreateWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutCreateWindow(title:string):map {block?}</code></div>
<code>glutCreateWindow</code> creates a top-level window.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutCreateSubWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutCreateSubWindow(win:number, x:number, y:number, width:number, height:number):map {block?}</code></div>
<code>glutCreateSubWindow</code> creates a subwindow.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutDestroyWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutDestroyWindow(win:number):map:void</code></div>
<code>glutDestroyWindow</code> destroys the specified window.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutPostRedisplay</strong></div>
<div style="margin-bottom:1em"><code>glut.glutPostRedisplay():void</code></div>
<code>glutPostRedisplay marks the *current window* as needing to be redisplayed.</code>
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutPostWindowRedisplay</strong></div>
<div style="margin-bottom:1em"><code>glut.glutPostWindowRedisplay(win:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSwapBuffers</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSwapBuffers():void</code></div>
<code>glutSwapBuffers</code> swaps the buffers of the <em>current window</em> if double buffered.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutGetWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutGetWindow() {block?}</code></div>
<code>glutGetWindow</code> returns the identifier of the <em>current window</em>.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSetWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSetWindow(win:number):map:void</code></div>
<code>glutSetWindow</code> sets the <em>current window</em>.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSetWindowTitle</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSetWindowTitle(title:string):map:void</code></div>
<code>glutSetWindowTitle</code> changes the window title of the current top-level window.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSetIconTitle</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSetIconTitle(title:string):map:void</code></div>
<code>glutSetIconTitle</code> changes the icon title of the current top-level window.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutPositionWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutPositionWindow(x:number, y:number):map:void</code></div>
<code>glutPositionWindow</code> requests a change to the position of the <em>current window</em>.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutReshapeWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutReshapeWindow(width:number, height:number):map:void</code></div>
<code>glutReshapeWindow</code> requests a change to the size of the <em>current window</em>.
</p>
<p>
<div><strong style="text-decoration:underline">glut.glutPopWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutPopWindow():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutPushWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutPushWindow():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutIconifyWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutIconifyWindow():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutShowWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutShowWindow():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutHideWindow</strong></div>
<div style="margin-bottom:1em"><code>glut.glutHideWindow():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutFullScreen</strong></div>
<div style="margin-bottom:1em"><code>glut.glutFullScreen():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSetCursor</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSetCursor(cursor:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutWarpPointer</strong></div>
<div style="margin-bottom:1em"><code>glut.glutWarpPointer(x:number, y:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutEstablishOverlay</strong></div>
<div style="margin-bottom:1em"><code>glut.glutEstablishOverlay():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutRemoveOverlay</strong></div>
<div style="margin-bottom:1em"><code>glut.glutRemoveOverlay():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutUseLayer</strong></div>
<div style="margin-bottom:1em"><code>glut.glutUseLayer(layer:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutPostOverlayRedisplay</strong></div>
<div style="margin-bottom:1em"><code>glut.glutPostOverlayRedisplay():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutPostWindowOverlayRedisplay</strong></div>
<div style="margin-bottom:1em"><code>glut.glutPostWindowOverlayRedisplay(win:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutShowOverlay</strong></div>
<div style="margin-bottom:1em"><code>glut.glutShowOverlay():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutHideOverlay</strong></div>
<div style="margin-bottom:1em"><code>glut.glutHideOverlay():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutCreateMenu</strong></div>
<div style="margin-bottom:1em"><code>glut.glutCreateMenu(func:function) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutDestroyMenu</strong></div>
<div style="margin-bottom:1em"><code>glut.glutDestroyMenu(menu:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutGetMenu</strong></div>
<div style="margin-bottom:1em"><code>glut.glutGetMenu() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSetMenu</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSetMenu(menu:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutAddMenuEntry</strong></div>
<div style="margin-bottom:1em"><code>glut.glutAddMenuEntry(label:string, value:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutAddSubMenu</strong></div>
<div style="margin-bottom:1em"><code>glut.glutAddSubMenu(label:string, submenu:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutChangeToMenuEntry</strong></div>
<div style="margin-bottom:1em"><code>glut.glutChangeToMenuEntry(item:number, label:string, value:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutChangeToSubMenu</strong></div>
<div style="margin-bottom:1em"><code>glut.glutChangeToSubMenu(item:number, label:string, submenu:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutRemoveMenuItem</strong></div>
<div style="margin-bottom:1em"><code>glut.glutRemoveMenuItem(item:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutAttachMenu</strong></div>
<div style="margin-bottom:1em"><code>glut.glutAttachMenu(button:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutDetachMenu</strong></div>
<div style="margin-bottom:1em"><code>glut.glutDetachMenu(button:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutDisplayFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutDisplayFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutReshapeFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutReshapeFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutKeyboardFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutKeyboardFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutMouseFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutMouseFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutMotionFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutMotionFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutPassiveMotionFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutPassiveMotionFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutEntryFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutEntryFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutVisibilityFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutVisibilityFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutIdleFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutIdleFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutTimerFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutTimerFunc(millis:number, func:function:nil, value:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutMenuStateFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutMenuStateFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSpecialFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSpecialFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSpaceballMotionFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSpaceballMotionFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSpaceballRotateFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSpaceballRotateFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSpaceballButtonFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSpaceballButtonFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutButtonBoxFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutButtonBoxFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutDialsFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutDialsFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutTabletMotionFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutTabletMotionFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutTabletButtonFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutTabletButtonFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutMenuStatusFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutMenuStatusFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutOverlayDisplayFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutOverlayDisplayFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutWindowStatusFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutWindowStatusFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutKeyboardUpFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutKeyboardUpFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSpecialUpFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSpecialUpFunc(func:function:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutJoystickFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutJoystickFunc(func:function:nil, pollInterval:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSetColor</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSetColor(ndx:number, red:number, green:number, blue:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutGetColor</strong></div>
<div style="margin-bottom:1em"><code>glut.glutGetColor(ndx:number, component:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutCopyColormap</strong></div>
<div style="margin-bottom:1em"><code>glut.glutCopyColormap(win:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutGet</strong></div>
<div style="margin-bottom:1em"><code>glut.glutGet(type:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutDeviceGet</strong></div>
<div style="margin-bottom:1em"><code>glut.glutDeviceGet(type:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutExtensionSupported</strong></div>
<div style="margin-bottom:1em"><code>glut.glutExtensionSupported(name:string):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutGetModifiers</strong></div>
<div style="margin-bottom:1em"><code>glut.glutGetModifiers() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutLayerGet</strong></div>
<div style="margin-bottom:1em"><code>glut.glutLayerGet(type:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutGetProcAddress</strong></div>
<div style="margin-bottom:1em"><code>glut.glutGetProcAddress(procName:string):map:void {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutBitmapCharacter</strong></div>
<div style="margin-bottom:1em"><code>glut.glutBitmapCharacter(font:glut.Font, character:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutBitmapWidth</strong></div>
<div style="margin-bottom:1em"><code>glut.glutBitmapWidth(font:glut.Font, character:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutStrokeCharacter</strong></div>
<div style="margin-bottom:1em"><code>glut.glutStrokeCharacter(font:glut.Font, character:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutStrokeWidth</strong></div>
<div style="margin-bottom:1em"><code>glut.glutStrokeWidth(font:glut.Font, character:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutBitmapLength</strong></div>
<div style="margin-bottom:1em"><code>glut.glutBitmapLength(font:glut.Font, string:string):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutStrokeLength</strong></div>
<div style="margin-bottom:1em"><code>glut.glutStrokeLength(font:glut.Font, string:string):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutWireSphere</strong></div>
<div style="margin-bottom:1em"><code>glut.glutWireSphere(radius:number, slices:number, stacks:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSolidSphere</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSolidSphere(radius:number, slices:number, stacks:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutWireCone</strong></div>
<div style="margin-bottom:1em"><code>glut.glutWireCone(base:number, height:number, slices:number, stacks:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSolidCone</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSolidCone(base:number, height:number, slices:number, stacks:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutWireCube</strong></div>
<div style="margin-bottom:1em"><code>glut.glutWireCube(size:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSolidCube</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSolidCube(size:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutWireTorus</strong></div>
<div style="margin-bottom:1em"><code>glut.glutWireTorus(innerRadius:number, outerRadius:number, sides:number, rings:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSolidTorus</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSolidTorus(innerRadius:number, outerRadius:number, sides:number, rings:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutWireDodecahedron</strong></div>
<div style="margin-bottom:1em"><code>glut.glutWireDodecahedron():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSolidDodecahedron</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSolidDodecahedron():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutWireTeapot</strong></div>
<div style="margin-bottom:1em"><code>glut.glutWireTeapot(size:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSolidTeapot</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSolidTeapot(size:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutWireOctahedron</strong></div>
<div style="margin-bottom:1em"><code>glut.glutWireOctahedron():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSolidOctahedron</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSolidOctahedron():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutWireTetrahedron</strong></div>
<div style="margin-bottom:1em"><code>glut.glutWireTetrahedron():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSolidTetrahedron</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSolidTetrahedron():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutWireIcosahedron</strong></div>
<div style="margin-bottom:1em"><code>glut.glutWireIcosahedron():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSolidIcosahedron</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSolidIcosahedron():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutVideoResizeGet</strong></div>
<div style="margin-bottom:1em"><code>glut.glutVideoResizeGet(param:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSetupVideoResizing</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSetupVideoResizing():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutStopVideoResizing</strong></div>
<div style="margin-bottom:1em"><code>glut.glutStopVideoResizing():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutVideoResize</strong></div>
<div style="margin-bottom:1em"><code>glut.glutVideoResize(x:number, y:number, width:number, height:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutVideoPan</strong></div>
<div style="margin-bottom:1em"><code>glut.glutVideoPan(x:number, y:number, width:number, height:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutReportErrors</strong></div>
<div style="margin-bottom:1em"><code>glut.glutReportErrors():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutIgnoreKeyRepeat</strong></div>
<div style="margin-bottom:1em"><code>glut.glutIgnoreKeyRepeat(ignore:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutSetKeyRepeat</strong></div>
<div style="margin-bottom:1em"><code>glut.glutSetKeyRepeat(repeatMode:number):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutForceJoystickFunc</strong></div>
<div style="margin-bottom:1em"><code>glut.glutForceJoystickFunc():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutGameModeString</strong></div>
<div style="margin-bottom:1em"><code>glut.glutGameModeString(string:string):map:void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutEnterGameMode</strong></div>
<div style="margin-bottom:1em"><code>glut.glutEnterGameMode() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutLeaveGameMode</strong></div>
<div style="margin-bottom:1em"><code>glut.glutLeaveGameMode():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">glut.glutGameModeGet</strong></div>
<div style="margin-bottom:1em"><code>glut.glutGameModeGet(mode:number):map {block?}</code></div>

</p>
<h2><span class="caption-index-2">24.3</span><a name="anchor-24-3"></a>Thanks</h2>
<p>
This module uses freeglut which official site is:
</p>
<p>
<a href="http://freeglut.sourceforge.net/">http://freeglut.sourceforge.net/</a>
</p>
<p />

{% endraw %}
