---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-23.html#naviitem-selected
nextpage: chapter-25.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">24</span>glut Module</h1>
<h2><span class="caption-index-2">24.1</span><a name="anchor-24-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">glut</code> module provides functions of GLUT library.
</p>
<h2><span class="caption-index-2">24.2</span><a name="anchor-24-2"></a>Module Function</h2>
<div class="h5">glut.glutInit</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutInit(argv[]:string) {block?}</code></div>
<p>
<code class="highlighter-rouge">glutInit</code> is used to initialize the GLUT library.
</p>
<div class="h5">glut.glutInitDisplayMode</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutInitDisplayMode(mode:number):map:void</code></div>
<p>
<code class="highlighter-rouge">glutInitDisplayMode</code> sets the <em>initial display mode</em>.
</p>
<div class="h5">glut.glutInitDisplayString</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutInitDisplayString(string:string):map:void</code></div>
<div class="h5">glut.glutInitWindowPosition</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutInitWindowPosition(x:number, y:number):map:void</code></div>
<p>
<code class="highlighter-rouge">glutInitWindowPosition</code> sets the initial window position.	
</p>
<div class="h5">glut.glutInitWindowSize</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutInitWindowSize(width:number, height:number):map:void</code></div>
<p>
<code class="highlighter-rouge">glutInitWindowSize</code> sets the initial window size.	
</p>
<div class="h5">glut.glutMainLoop</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutMainLoop():void</code></div>
<p>
<code class="highlighter-rouge">glutMainLoop</code> enters the GLUT event processing loop.
</p>
<div class="h5">glut.glutCreateWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutCreateWindow(title:string):map {block?}</code></div>
<p>
<code class="highlighter-rouge">glutCreateWindow</code> creates a top-level window.
</p>
<div class="h5">glut.glutCreateSubWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutCreateSubWindow(win:number, x:number, y:number, width:number, height:number):map {block?}</code></div>
<p>
<code class="highlighter-rouge">glutCreateSubWindow</code> creates a subwindow.
</p>
<div class="h5">glut.glutDestroyWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutDestroyWindow(win:number):map:void</code></div>
<p>
<code class="highlighter-rouge">glutDestroyWindow</code> destroys the specified window.
</p>
<div class="h5">glut.glutPostRedisplay</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutPostRedisplay():void</code></div>
<p>
<code class="highlighter-rouge">glutPostRedisplay marks the *current window* as needing to be redisplayed.</code>
</p>
<div class="h5">glut.glutPostWindowRedisplay</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutPostWindowRedisplay(win:number):map:void</code></div>
<div class="h5">glut.glutSwapBuffers</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSwapBuffers():void</code></div>
<p>
<code class="highlighter-rouge">glutSwapBuffers</code> swaps the buffers of the <em>current window</em> if double buffered.
</p>
<div class="h5">glut.glutGetWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutGetWindow() {block?}</code></div>
<p>
<code class="highlighter-rouge">glutGetWindow</code> returns the identifier of the <em>current window</em>.
</p>
<div class="h5">glut.glutSetWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSetWindow(win:number):map:void</code></div>
<p>
<code class="highlighter-rouge">glutSetWindow</code> sets the <em>current window</em>.
</p>
<div class="h5">glut.glutSetWindowTitle</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSetWindowTitle(title:string):map:void</code></div>
<p>
<code class="highlighter-rouge">glutSetWindowTitle</code> changes the window title of the current top-level window.
</p>
<div class="h5">glut.glutSetIconTitle</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSetIconTitle(title:string):map:void</code></div>
<p>
<code class="highlighter-rouge">glutSetIconTitle</code> changes the icon title of the current top-level window.
</p>
<div class="h5">glut.glutPositionWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutPositionWindow(x:number, y:number):map:void</code></div>
<p>
<code class="highlighter-rouge">glutPositionWindow</code> requests a change to the position of the <em>current window</em>.
</p>
<div class="h5">glut.glutReshapeWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutReshapeWindow(width:number, height:number):map:void</code></div>
<p>
<code class="highlighter-rouge">glutReshapeWindow</code> requests a change to the size of the <em>current window</em>.
</p>
<div class="h5">glut.glutPopWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutPopWindow():void</code></div>
<div class="h5">glut.glutPushWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutPushWindow():void</code></div>
<div class="h5">glut.glutIconifyWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutIconifyWindow():void</code></div>
<div class="h5">glut.glutShowWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutShowWindow():void</code></div>
<div class="h5">glut.glutHideWindow</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutHideWindow():void</code></div>
<div class="h5">glut.glutFullScreen</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutFullScreen():void</code></div>
<div class="h5">glut.glutSetCursor</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSetCursor(cursor:number):map:void</code></div>
<div class="h5">glut.glutWarpPointer</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutWarpPointer(x:number, y:number):map:void</code></div>
<div class="h5">glut.glutEstablishOverlay</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutEstablishOverlay():void</code></div>
<div class="h5">glut.glutRemoveOverlay</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutRemoveOverlay():void</code></div>
<div class="h5">glut.glutUseLayer</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutUseLayer(layer:number):map:void</code></div>
<div class="h5">glut.glutPostOverlayRedisplay</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutPostOverlayRedisplay():void</code></div>
<div class="h5">glut.glutPostWindowOverlayRedisplay</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutPostWindowOverlayRedisplay(win:number):map:void</code></div>
<div class="h5">glut.glutShowOverlay</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutShowOverlay():void</code></div>
<div class="h5">glut.glutHideOverlay</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutHideOverlay():void</code></div>
<div class="h5">glut.glutCreateMenu</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutCreateMenu(func:function) {block?}</code></div>
<div class="h5">glut.glutDestroyMenu</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutDestroyMenu(menu:number):map:void</code></div>
<div class="h5">glut.glutGetMenu</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutGetMenu() {block?}</code></div>
<div class="h5">glut.glutSetMenu</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSetMenu(menu:number):map:void</code></div>
<div class="h5">glut.glutAddMenuEntry</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutAddMenuEntry(label:string, value:number):map:void</code></div>
<div class="h5">glut.glutAddSubMenu</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutAddSubMenu(label:string, submenu:number):map:void</code></div>
<div class="h5">glut.glutChangeToMenuEntry</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutChangeToMenuEntry(item:number, label:string, value:number):map:void</code></div>
<div class="h5">glut.glutChangeToSubMenu</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutChangeToSubMenu(item:number, label:string, submenu:number):map:void</code></div>
<div class="h5">glut.glutRemoveMenuItem</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutRemoveMenuItem(item:number):map:void</code></div>
<div class="h5">glut.glutAttachMenu</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutAttachMenu(button:number):map:void</code></div>
<div class="h5">glut.glutDetachMenu</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutDetachMenu(button:number):map:void</code></div>
<div class="h5">glut.glutDisplayFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutDisplayFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutReshapeFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutReshapeFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutKeyboardFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutKeyboardFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutMouseFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutMouseFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutMotionFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutMotionFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutPassiveMotionFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutPassiveMotionFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutEntryFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutEntryFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutVisibilityFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutVisibilityFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutIdleFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutIdleFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutTimerFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutTimerFunc(millis:number, func:function:nil, value:number):void</code></div>
<div class="h5">glut.glutMenuStateFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutMenuStateFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutSpecialFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSpecialFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutSpaceballMotionFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSpaceballMotionFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutSpaceballRotateFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSpaceballRotateFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutSpaceballButtonFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSpaceballButtonFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutButtonBoxFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutButtonBoxFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutDialsFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutDialsFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutTabletMotionFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutTabletMotionFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutTabletButtonFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutTabletButtonFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutMenuStatusFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutMenuStatusFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutOverlayDisplayFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutOverlayDisplayFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutWindowStatusFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutWindowStatusFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutKeyboardUpFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutKeyboardUpFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutSpecialUpFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSpecialUpFunc(func:function:nil):void</code></div>
<div class="h5">glut.glutJoystickFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutJoystickFunc(func:function:nil, pollInterval:number):void</code></div>
<div class="h5">glut.glutSetColor</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSetColor(ndx:number, red:number, green:number, blue:number):void</code></div>
<div class="h5">glut.glutGetColor</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutGetColor(ndx:number, component:number):map {block?}</code></div>
<div class="h5">glut.glutCopyColormap</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutCopyColormap(win:number):map:void</code></div>
<div class="h5">glut.glutGet</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutGet(type:number):map {block?}</code></div>
<div class="h5">glut.glutDeviceGet</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutDeviceGet(type:number):map {block?}</code></div>
<div class="h5">glut.glutExtensionSupported</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutExtensionSupported(name:string):map {block?}</code></div>
<div class="h5">glut.glutGetModifiers</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutGetModifiers() {block?}</code></div>
<div class="h5">glut.glutLayerGet</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutLayerGet(type:number):map {block?}</code></div>
<div class="h5">glut.glutGetProcAddress</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutGetProcAddress(procName:string):map:void {block?}</code></div>
<div class="h5">glut.glutBitmapCharacter</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutBitmapCharacter(font:glut.Font, character:number):map:void</code></div>
<div class="h5">glut.glutBitmapWidth</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutBitmapWidth(font:glut.Font, character:number):map {block?}</code></div>
<div class="h5">glut.glutStrokeCharacter</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutStrokeCharacter(font:glut.Font, character:number):map:void</code></div>
<div class="h5">glut.glutStrokeWidth</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutStrokeWidth(font:glut.Font, character:number):map {block?}</code></div>
<div class="h5">glut.glutBitmapLength</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutBitmapLength(font:glut.Font, string:string):map {block?}</code></div>
<div class="h5">glut.glutStrokeLength</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutStrokeLength(font:glut.Font, string:string):map {block?}</code></div>
<div class="h5">glut.glutWireSphere</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutWireSphere(radius:number, slices:number, stacks:number):map:void</code></div>
<div class="h5">glut.glutSolidSphere</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSolidSphere(radius:number, slices:number, stacks:number):map:void</code></div>
<div class="h5">glut.glutWireCone</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutWireCone(base:number, height:number, slices:number, stacks:number):map:void</code></div>
<div class="h5">glut.glutSolidCone</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSolidCone(base:number, height:number, slices:number, stacks:number):map:void</code></div>
<div class="h5">glut.glutWireCube</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutWireCube(size:number):map:void</code></div>
<div class="h5">glut.glutSolidCube</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSolidCube(size:number):map:void</code></div>
<div class="h5">glut.glutWireTorus</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutWireTorus(innerRadius:number, outerRadius:number, sides:number, rings:number):map:void</code></div>
<div class="h5">glut.glutSolidTorus</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSolidTorus(innerRadius:number, outerRadius:number, sides:number, rings:number):map:void</code></div>
<div class="h5">glut.glutWireDodecahedron</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutWireDodecahedron():void</code></div>
<div class="h5">glut.glutSolidDodecahedron</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSolidDodecahedron():void</code></div>
<div class="h5">glut.glutWireTeapot</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutWireTeapot(size:number):map:void</code></div>
<div class="h5">glut.glutSolidTeapot</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSolidTeapot(size:number):map:void</code></div>
<div class="h5">glut.glutWireOctahedron</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutWireOctahedron():void</code></div>
<div class="h5">glut.glutSolidOctahedron</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSolidOctahedron():void</code></div>
<div class="h5">glut.glutWireTetrahedron</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutWireTetrahedron():void</code></div>
<div class="h5">glut.glutSolidTetrahedron</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSolidTetrahedron():void</code></div>
<div class="h5">glut.glutWireIcosahedron</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutWireIcosahedron():void</code></div>
<div class="h5">glut.glutSolidIcosahedron</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSolidIcosahedron():void</code></div>
<div class="h5">glut.glutVideoResizeGet</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutVideoResizeGet(param:number):map {block?}</code></div>
<div class="h5">glut.glutSetupVideoResizing</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSetupVideoResizing():void</code></div>
<div class="h5">glut.glutStopVideoResizing</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutStopVideoResizing():void</code></div>
<div class="h5">glut.glutVideoResize</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutVideoResize(x:number, y:number, width:number, height:number):map:void</code></div>
<div class="h5">glut.glutVideoPan</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutVideoPan(x:number, y:number, width:number, height:number):map:void</code></div>
<div class="h5">glut.glutReportErrors</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutReportErrors():void</code></div>
<div class="h5">glut.glutIgnoreKeyRepeat</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutIgnoreKeyRepeat(ignore:number):map:void</code></div>
<div class="h5">glut.glutSetKeyRepeat</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutSetKeyRepeat(repeatMode:number):map:void</code></div>
<div class="h5">glut.glutForceJoystickFunc</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutForceJoystickFunc():void</code></div>
<div class="h5">glut.glutGameModeString</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutGameModeString(string:string):map:void</code></div>
<div class="h5">glut.glutEnterGameMode</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutEnterGameMode() {block?}</code></div>
<div class="h5">glut.glutLeaveGameMode</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutLeaveGameMode():void</code></div>
<div class="h5">glut.glutGameModeGet</div>
<div class="mb-2"><i class="fas fa-caret-right mr-2"></i><code>glut.glutGameModeGet(mode:number):map {block?}</code></div>
<h2><span class="caption-index-2">24.3</span><a name="anchor-24-3"></a>Thanks</h2>
<p>
This module uses freeglut which official site is:
</p>
<p>
<a href="http://freeglut.sourceforge.net/">http://freeglut.sourceforge.net/</a>
</p>
{% endraw %}
