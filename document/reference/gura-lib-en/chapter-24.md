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
<div class="mb-2"><code>glut.glutInit(argv[]:string) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutInit</code> is used to initialize the GLUT library.
</p>
</div>
<div class="mb-2"><code>glut.glutInitDisplayMode(mode:number):map:void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutInitDisplayMode</code> sets the <em>initial display mode</em>.
</p>
</div>
<div class="mb-2"><code>glut.glutInitDisplayString(string:string):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutInitWindowPosition(x:number, y:number):map:void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutInitWindowPosition</code> sets the initial window position.	
</p>
</div>
<div class="mb-2"><code>glut.glutInitWindowSize(width:number, height:number):map:void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutInitWindowSize</code> sets the initial window size.	
</p>
</div>
<div class="mb-2"><code>glut.glutMainLoop():void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutMainLoop</code> enters the GLUT event processing loop.
</p>
</div>
<div class="mb-2"><code>glut.glutCreateWindow(title:string):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutCreateWindow</code> creates a top-level window.
</p>
</div>
<div class="mb-2"><code>glut.glutCreateSubWindow(win:number, x:number, y:number, width:number, height:number):map {block?}</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutCreateSubWindow</code> creates a subwindow.
</p>
</div>
<div class="mb-2"><code>glut.glutDestroyWindow(win:number):map:void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutDestroyWindow</code> destroys the specified window.
</p>
</div>
<div class="mb-2"><code>glut.glutPostRedisplay():void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutPostRedisplay marks the *current window* as needing to be redisplayed.</code>
</p>
</div>
<div class="mb-2"><code>glut.glutPostWindowRedisplay(win:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSwapBuffers():void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutSwapBuffers</code> swaps the buffers of the <em>current window</em> if double buffered.
</p>
</div>
<div class="mb-2"><code>glut.glutGetWindow() {block?}</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutGetWindow</code> returns the identifier of the <em>current window</em>.
</p>
</div>
<div class="mb-2"><code>glut.glutSetWindow(win:number):map:void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutSetWindow</code> sets the <em>current window</em>.
</p>
</div>
<div class="mb-2"><code>glut.glutSetWindowTitle(title:string):map:void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutSetWindowTitle</code> changes the window title of the current top-level window.
</p>
</div>
<div class="mb-2"><code>glut.glutSetIconTitle(title:string):map:void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutSetIconTitle</code> changes the icon title of the current top-level window.
</p>
</div>
<div class="mb-2"><code>glut.glutPositionWindow(x:number, y:number):map:void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutPositionWindow</code> requests a change to the position of the <em>current window</em>.
</p>
</div>
<div class="mb-2"><code>glut.glutReshapeWindow(width:number, height:number):map:void</code></div>
<div class="mb-2 ml-4">
<p>
<code class="highlighter-rouge">glutReshapeWindow</code> requests a change to the size of the <em>current window</em>.
</p>
</div>
<div class="mb-2"><code>glut.glutPopWindow():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutPushWindow():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutIconifyWindow():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutShowWindow():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutHideWindow():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutFullScreen():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSetCursor(cursor:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutWarpPointer(x:number, y:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutEstablishOverlay():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutRemoveOverlay():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutUseLayer(layer:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutPostOverlayRedisplay():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutPostWindowOverlayRedisplay(win:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutShowOverlay():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutHideOverlay():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutCreateMenu(func:function) {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutDestroyMenu(menu:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutGetMenu() {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSetMenu(menu:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutAddMenuEntry(label:string, value:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutAddSubMenu(label:string, submenu:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutChangeToMenuEntry(item:number, label:string, value:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutChangeToSubMenu(item:number, label:string, submenu:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutRemoveMenuItem(item:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutAttachMenu(button:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutDetachMenu(button:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutDisplayFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutReshapeFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutKeyboardFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutMouseFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutMotionFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutPassiveMotionFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutEntryFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutVisibilityFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutIdleFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutTimerFunc(millis:number, func:function:nil, value:number):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutMenuStateFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSpecialFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSpaceballMotionFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSpaceballRotateFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSpaceballButtonFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutButtonBoxFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutDialsFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutTabletMotionFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutTabletButtonFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutMenuStatusFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutOverlayDisplayFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutWindowStatusFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutKeyboardUpFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSpecialUpFunc(func:function:nil):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutJoystickFunc(func:function:nil, pollInterval:number):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSetColor(ndx:number, red:number, green:number, blue:number):void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutGetColor(ndx:number, component:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutCopyColormap(win:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutGet(type:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutDeviceGet(type:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutExtensionSupported(name:string):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutGetModifiers() {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutLayerGet(type:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutGetProcAddress(procName:string):map:void {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutBitmapCharacter(font:glut.Font, character:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutBitmapWidth(font:glut.Font, character:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutStrokeCharacter(font:glut.Font, character:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutStrokeWidth(font:glut.Font, character:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutBitmapLength(font:glut.Font, string:string):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutStrokeLength(font:glut.Font, string:string):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutWireSphere(radius:number, slices:number, stacks:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSolidSphere(radius:number, slices:number, stacks:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutWireCone(base:number, height:number, slices:number, stacks:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSolidCone(base:number, height:number, slices:number, stacks:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutWireCube(size:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSolidCube(size:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutWireTorus(innerRadius:number, outerRadius:number, sides:number, rings:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSolidTorus(innerRadius:number, outerRadius:number, sides:number, rings:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutWireDodecahedron():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSolidDodecahedron():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutWireTeapot(size:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSolidTeapot(size:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutWireOctahedron():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSolidOctahedron():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutWireTetrahedron():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSolidTetrahedron():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutWireIcosahedron():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSolidIcosahedron():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutVideoResizeGet(param:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSetupVideoResizing():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutStopVideoResizing():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutVideoResize(x:number, y:number, width:number, height:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutVideoPan(x:number, y:number, width:number, height:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutReportErrors():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutIgnoreKeyRepeat(ignore:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutSetKeyRepeat(repeatMode:number):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutForceJoystickFunc():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutGameModeString(string:string):map:void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutEnterGameMode() {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutLeaveGameMode():void</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>glut.glutGameModeGet(mode:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<h2><span class="caption-index-2">24.3</span><a name="anchor-24-3"></a>Thanks</h2>
<p>
This module uses freeglut which official site is:
</p>
<p>
<a href="http://freeglut.sourceforge.net/">http://freeglut.sourceforge.net/</a>
</p>
{% endraw %}
