---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">50</span><a name="anchor-50"></a>sdl2 Module</h1>
<h2><span class="caption-index-2">50.1</span><a name="anchor-50-1"></a>Overview</h2>
<p>
The <code>sdl2</code> module provices functions of SDL2 library.
</p>
<h2><span class="caption-index-2">50.2</span><a name="anchor-50-2"></a>Module Function</h2>
<p>
<div><strong style="text-decoration:underline">sdl2.Init</strong></div>
<div style="margin-bottom:1em"><code>sdl2.Init(flags:number):void</code></div>
Use this function to initialize the SDL library. This must be called before using any other SDL function.
</p>
<p>
The Event Handling, File I/O, and Threading subsystems are initialized by default. You must specifically initialize other subsystems if you use them in your application.
</p>
<p>
<code>flags</code> may be any of the following OR'd together:
</p>
<ul>
<li><code>sdl2.INIT_TIMER</code> .. timer subsystem</li>
<li><code>sdl2.INIT_AUDIO</code> .. audio subsystem</li>
<li><code>sdl2.INIT_VIDEO</code> .. video subsystem</li>
<li><code>sdl2.INIT_JOYSTICK</code> .. joystick subsystem</li>
<li><code>sdl2.INIT_HAPTIC</code> .. haptic (force feedback) subsystem</li>
<li><code>sdl2.INIT_GAMECONTROLLER</code> .. controller subsystem</li>
<li><code>sdl2.INIT_EVENTS</code> .. events subsystem</li>
<li><code>sdl2.INIT_EVERYTHING</code> .. all of the above subsystems</li>
<li><code>sdl2.INIT_NOPARACHUTE</code> .. compatibility; this flag is ignored</li>
</ul>
<p>
If you want to initialize subsystems separately you would call <code>SDL_Init(0)</code> followed by <code>SDL_InitSubSystem()</code> with the desired subsystem flag.
</p>
<p>
<div><strong style="text-decoration:underline">sdl2.InitSubSystem</strong></div>
<div style="margin-bottom:1em"><code>sdl2.InitSubSystem(flags:number):void</code></div>
Use this function to initialize specific SDL subsystems.
</p>
<p>
After SDL has been initialized with <code>SDL_Init()</code> you may initialize uninitialized subsystems with <code>SDL_InitSubSystem()</code>.
</p>
<p>
These are the flags which may be passed to <code>SDL_InitSubSystem()</code> and may be OR'd together to initialize multiple subsystems simultaneously.
</p>
<ul>
<li><code>sdl2.INIT_TIMER</code> .. timer subsystem</li>
<li><code>sdl2.INIT_AUDIO</code> .. audio subsystem</li>
<li><code>sdl2.INIT_VIDEO</code> .. video subsystem</li>
<li><code>sdl2.INIT_JOYSTICK</code> .. joystick subsystem</li>
<li><code>sdl2.INIT_HAPTIC</code> .. haptic (force feedback) subsystem</li>
<li><code>sdl2.INIT_GAMECONTROLLER</code> .. controller subsystem</li>
<li><code>sdl2.INIT_EVENTS</code> .. events subsystem</li>
<li><code>sdl2.INIT_EVERYTHING</code> .. all of the above subsystems</li>
<li><code>sdl2.INIT_NOPARACHUTE</code> .. compatibility; this flag is ignored</li>
</ul>
<p>
If you want to initialize subsystems separately you would call <code>SDL_Init(0)</code> followed by <code>SDL_InitSubSystem()</code> with the desired subsystem flag.
</p>
<p>
<div><strong style="text-decoration:underline">sdl2.Quit</strong></div>
<div style="margin-bottom:1em"><code>sdl2.Quit():void</code></div>
Use this function to clean up all initialized subsystems. You should call it upon all exit conditions.
</p>
<p>
You should call this function even if you have already shutdown each initialized subsystem with <code>SDL_QuitSubSystem()</code>.
</p>
<p>
If you start a subsystem using a call to that subsystem's init function (for example <code>SDL_VideoInit()</code>) instead of <code>SDL_Init()</code> or <code>SDL_InitSubSystem()</code>, then you must use that subsystem's quit function (<code>SDL_VideoQuit()</code>) to shut it down before calling <code>SDL_Quit()</code>.
</p>
<p>
You can use this function with <code>atexit()</code> to ensure that it is run when your application is shutdown, but it is not wise to do this from a library or other dynamically loaded code.
</p>
<p>
<div><strong style="text-decoration:underline">sdl2.QuitSubSystem</strong></div>
<div style="margin-bottom:1em"><code>sdl2.QuitSubSystem(flags:number):void</code></div>
Use this function to shut down specific SDL subsystems.
</p>
<p>
These are the flags which may be passed to <code>SDL_QuitSubSystem()</code> and may be OR'd together to quit multiple subsystems simultaneously.
</p>
<ul>
<li><code>sdl2.INIT_TIMER</code> .. timer subsystem</li>
<li><code>sdl2.INIT_AUDIO</code> .. audio subsystem</li>
<li><code>sdl2.INIT_VIDEO</code> .. video subsystem</li>
<li><code>sdl2.INIT_JOYSTICK</code> .. joystick subsystem</li>
<li><code>sdl2.INIT_HAPTIC</code> .. haptic (force feedback) subsystem</li>
<li><code>sdl2.INIT_GAMECONTROLLER</code> .. controller subsystem</li>
<li><code>sdl2.INIT_EVENTS</code> .. events subsystem</li>
<li><code>sdl2.INIT_EVERYTHING</code> .. all of the above subsystems</li>
<li><code>sdl2.INIT_NOPARACHUTE</code> .. compatibility; this flag is ignored</li>
</ul>
<p>
If you want to initialize subsystems separately you would call <code>SDL_Init(0)</code> followed by <code>SDL_InitSubSystem()</code> with the desired subsystem flag.
</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetMainReady</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetMainReady():void</code></div>
Use this function to circumvent failure of <code>SDL_Init()</code> when not using <code>SDL_main()</code> as an entry point.
</p>
<p>
This function is defined in SDL_main.h, along with the preprocessor rule to redefine <code>main()</code> as <code>SDL_main()</code>. Thus to ensure that your <code>main()</code> function will not be changed it is necessary to define <code>SDL_MAIN_HANDLED</code> before including SDL.h.
</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WasInit</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WasInit(flags:number) {block?}</code></div>
Use this function to return a mask of the specified subsystems which have previously been initialized.
</p>
<p>
These are the flags which may be passed to <code>SDL_WasInit()</code> and may be OR'd together to query multiple subsystems simultaneously.
</p>
<ul>
<li><code>sdl2.INIT_TIMER</code> .. timer subsystem</li>
<li><code>sdl2.INIT_AUDIO</code> .. audio subsystem</li>
<li><code>sdl2.INIT_VIDEO</code> .. video subsystem</li>
<li><code>sdl2.INIT_JOYSTICK</code> .. joystick subsystem</li>
<li><code>sdl2.INIT_HAPTIC</code> .. haptic (force feedback) subsystem</li>
<li><code>sdl2.INIT_GAMECONTROLLER</code> .. controller subsystem</li>
<li><code>sdl2.INIT_EVENTS</code> .. events subsystem</li>
<li><code>sdl2.INIT_EVERYTHING</code> .. all of the above subsystems</li>
<li><code>sdl2.INIT_NOPARACHUTE</code> .. compatibility; this flag is ignored</li>
</ul>
<p>
If you want to initialize subsystems separately you would call <code>SDL_Init(0)</code> followed by <code>SDL_InitSubSystem()</code> with the desired subsystem flag.
</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AddHintCallback</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AddHintCallback():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ClearHints</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ClearHints():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.DelhintCallback</strong></div>
<div style="margin-bottom:1em"><code>sdl2.DelhintCallback():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetHint</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetHint():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetHint</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetHint():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetHintWithPriority</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetHintWithPriority():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ClearError</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ClearError():void</code></div>
Use this function to clear any previous error message.
</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetError</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetError() {block?}</code></div>
Use this function to retrieve a message about the last error that occurred.
</p>
<p>
Returns a message with information about the specific error that occurred, or an empty string if there hasn't been an error since the last call to <code>SDL_ClearError()</code>. Without calling <code>SDL_ClearError()</code>, the message is only applicable when an SDL function has signaled an error. You must check the return values of SDL function calls to determine when to appropriately call <code>SDL_GetError()</code>.
</p>
<p>
This string is statically allocated and must not be freed by the application.
</p>
<p>
It is possible for multiple errors to occur before calling <code>SDL_GetError()</code>. Only the last error is returned.
</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetError</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetError():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.Log</strong></div>
<div style="margin-bottom:1em"><code>sdl2.Log():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogCritical</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogCritical():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogDebug</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogDebug():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogError</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogError():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogGetOutputFunction</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogGetOutputFunction():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogGetPriority</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogGetPriority():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogInfo</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogInfo():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogMessage</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogMessage():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogMessageV</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogMessageV():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogResetPriorities</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogResetPriorities():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogSetAllPriority</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogSetAllPriority():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogSetOutputFunction</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogSetOutputFunction():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogSetPriority</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogSetPriority():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogVerbose</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogVerbose():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LogWarn</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LogWarn():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetAssertionHandler</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetAssertionHandler():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetAssertionReport</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetAssertionReport():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetDefaultAssertionHandler</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetDefaultAssertionHandler():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ResetAssertionReport</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ResetAssertionReport():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetAssertionHandler</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetAssertionHandler():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.TriggerBreakpoint</strong></div>
<div style="margin-bottom:1em"><code>sdl2.TriggerBreakpoint():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.assert</strong></div>
<div style="margin-bottom:1em"><code>sdl2.assert():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.assert_paranoid</strong></div>
<div style="margin-bottom:1em"><code>sdl2.assert_paranoid():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.assert_release</strong></div>
<div style="margin-bottom:1em"><code>sdl2.assert_release():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRevision</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRevision() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRevisionNumber</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRevisionNumber() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetVersion</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetVersion() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.VERSION</strong></div>
<div style="margin-bottom:1em"><code>sdl2.VERSION() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.VERSION_ATLEAST</strong></div>
<div style="margin-bottom:1em"><code>sdl2.VERSION_ATLEAST(X:number, Y:number, Z:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateWindow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateWindow(title:string, x:number, y:number, w:number, h:number, flags:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateWindowAndRenderer</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateWindowAndRenderer(width:number, height:number, window_flags:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateWindowFrom</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateWindowFrom():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.DestroyWindow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.DestroyWindow(window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.DisableScreenSaver</strong></div>
<div style="margin-bottom:1em"><code>sdl2.DisableScreenSaver():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.EnableScreenSaver</strong></div>
<div style="margin-bottom:1em"><code>sdl2.EnableScreenSaver():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_CreateContext</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_CreateContext(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_DeleteContext</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_DeleteContext(context:sdl2.GLContext):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_ExtensionSupported</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_ExtensionSupported(extension:string) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_GetAttribute</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_GetAttribute(attr:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_GetCurrentContext</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_GetCurrentContext() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_GetCurrentWindow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_GetCurrentWindow() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_GetDrawableSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_GetDrawableSize(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_GetProcAddress</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_GetProcAddress():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_GetSwapInterval</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_GetSwapInterval() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_LoadLibrary</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_LoadLibrary(path:string):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_MakeCurrent</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_MakeCurrent(window:sdl2.Window, context:sdl2.GLContext):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_ResetAttributes</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_ResetAttributes():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_SetAttribute</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_SetAttribute(attr:number, value:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_SetSwapInterval</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_SetSwapInterval(interval:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_SwapWindow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_SwapWindow(window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_UnloadLibrary</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_UnloadLibrary():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetClosestDisplayMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetClosestDisplayMode(displayIndex:number, mode:sdl2.DisplayMode) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetCurrentDisplayMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetCurrentDisplayMode(displayIndex:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetCurrentVideoDriver</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetCurrentVideoDriver() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetDesktopDisplayMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetDesktopDisplayMode(displayIndex:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetDisplayBounds</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetDisplayBounds(displayIndex:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetDisplayMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetDisplayMode(displayIndex:number, modeIndex:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetDisplayName</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetDisplayName(dipslayIndex:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetNumDisplayModes</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetNumDisplayModes(displayIndex:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetNumVideoDisplays</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetNumVideoDisplays() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetNumVideoDrivers</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetNumVideoDrivers() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetVideoDriver</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetVideoDriver(index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowBrightness</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowBrightness(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowData</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowData(window:sdl2.Window, name:string):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowDisplayIndex</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowDisplayIndex(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowDisplayMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowDisplayMode(window:sdl2.Window, mode:sdl2.DisplayMode):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowFlags</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowFlags(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowFromID</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowFromID(id:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowGammaRamp</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowGammaRamp(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowGrab</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowGrab(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowID</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowID(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowMaximumSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowMaximumSize(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowMinimumSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowMinimumSize(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowPixelFormat</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowPixelFormat(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowPosition</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowPosition(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowSize(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowSurface</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowSurface(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowTitle</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowTitle(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetWindowWMInfo</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetWindowWMInfo(window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HideWindow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HideWindow(window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.IsScreenSaverEnabled</strong></div>
<div style="margin-bottom:1em"><code>sdl2.IsScreenSaverEnabled() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.MaximizeWindow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.MaximizeWindow(window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.MinimizeWindow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.MinimizeWindow(window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RaiseWindow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RaiseWindow(window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RestoreWindow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RestoreWindow(window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowBordered</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowBordered(window:sdl2.Window, bordered:boolean):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowBrightness</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowBrightness(window:sdl2.Window, brightness:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowData</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowData(window:sdl2.Window, name:string):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowDisplayMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowDisplayMode(window:sdl2.Window, mode:sdl2.DisplayMode):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowFullscreen</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowFullscreen(window:sdl2.Window, flags:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowGammaRamp</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowGammaRamp(window:sdl2.Window, red[]:number, green[]:number, blue[]:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowGrab</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowGrab(window:sdl2.Window, grabbed:boolean):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowHitTest</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowHitTest(window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowIcon</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowIcon(window:sdl2.Window, icon:sdl2.Surface):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowMaximumSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowMaximumSize(window:sdl2.Window, max_w:number, max_h:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowMinimumSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowMinimumSize(window:sdl2.Window, min_w:number, min_h:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowPosition</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowPosition(window:sdl2.Window, x:number, y:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowSize(window:sdl2.Window, w:number, h:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetWindowTitle</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetWindowTitle(window:sdl2.Window, title:string):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ShowMessageBox</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ShowMessageBox():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ShowSimpleMessageBox</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ShowSimpleMessageBox(flags:number, title:string, message:string, window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ShowWindow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ShowWindow(window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.UpdateWindowSurface</strong></div>
<div style="margin-bottom:1em"><code>sdl2.UpdateWindowSurface(window:sdl2.Window):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.UpdateWindowSurfaceRects</strong></div>
<div style="margin-bottom:1em"><code>sdl2.UpdateWindowSurfaceRects(window:sdl2.Window, rects[]:sdl2.Rect):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.VideoInit</strong></div>
<div style="margin-bottom:1em"><code>sdl2.VideoInit(driver_name:string):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.VideoQuit</strong></div>
<div style="margin-bottom:1em"><code>sdl2.VideoQuit():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateRenderer</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateRenderer(window:sdl2.Window, index:number, flags:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateSoftwareRenderer</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateSoftwareRenderer(surface:sdl2.Surface) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateTexture</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateTexture(renderer:sdl2.Renderer, format:number, access:number, w:number, h:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateTextureFromSurface</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateTextureFromSurface(renderer:sdl2.Renderer, surface:sdl2.Surface) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.DestroyRenderer</strong></div>
<div style="margin-bottom:1em"><code>sdl2.DestroyRenderer(renderer:sdl2.Renderer):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.DestroyTexture</strong></div>
<div style="margin-bottom:1em"><code>sdl2.DestroyTexture(texture:sdl2.Texture):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_BindTexture</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_BindTexture(texture:sdl2.Texture) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GL_UnbindTexture</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GL_UnbindTexture(texture:sdl2.Texture):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetNumRenderDrivers</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetNumRenderDrivers() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRenderDrawBlendMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRenderDrawBlendMode(renderer:sdl2.Renderer) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRenderDrawColor</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRenderDrawColor(renderer:sdl2.Renderer) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRenderDriverInfo</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRenderDriverInfo(index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRenderTarget</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRenderTarget(renderer:sdl2.Renderer) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRenderer</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRenderer(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRendererInfo</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRendererInfo(renderer:sdl2.Renderer) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRenderOutputSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRenderOutputSize(renderer:sdl2.Renderer) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetTextureAlphaMod</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetTextureAlphaMod(texture:sdl2.Texture) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetTextureBlendMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetTextureBlendMode(texture:sdl2.Texture) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetTextureColorMod</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetTextureColorMod(texture:sdl2.Texture) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LockTexture</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LockTexture(texture:sdl2.Texture, rect:sdl2.Rect):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.QueryTexture</strong></div>
<div style="margin-bottom:1em"><code>sdl2.QueryTexture(texture:sdl2.Texture) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderClear</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderClear(renderer:sdl2.Renderer):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderCopy</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderCopy(renderer:sdl2.Renderer, texture:sdl2.Texture, srcrect:sdl2.Rect:nil, dstrect:sdl2.Rect:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderCopyEx</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderCopyEx(renderer:sdl2.Renderer, texture:sdl2.Texture, srcrect:sdl2.Rect:nil, dstrect:sdl2.Rect:nil, angle:number, center:sdl2.Point:nil, flip:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderDrawLine</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderDrawLine(renderer:sdl2.Renderer, x1:number, y1:number, x2:number, y2:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderDrawLines</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderDrawLines(renderer:sdl2.Renderer, points[]:sdl2.Point):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderDrawPoint</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderDrawPoint(renderer:sdl2.Renderer, x:number, y:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderDrawPoints</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderDrawPoints(renderer:sdl2.Renderer, points[]:sdl2.Point):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderDrawRect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderDrawRect(renderer:sdl2.Renderer, rect:sdl2.Rect:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderDrawRects</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderDrawRects(renderer:sdl2.Renderer, rects[]:sdl2.Rect):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderFillRect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderFillRect(renderer:sdl2.Renderer, rect:sdl2.Rect:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderFillRects</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderFillRects(renderer:sdl2.Renderer, rects[]:sdl2.Rect):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderGetClipRect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderGetClipRect(renderer:sdl2.Renderer) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderGetLogicalSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderGetLogicalSize(renderer:sdl2.Renderer) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderGetScale</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderGetScale(renderer:sdl2.Renderer) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderGetViewport</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderGetViewport(renderer:sdl2.Renderer) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderIsClipEnabled</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderIsClipEnabled(renderer:sdl2.Renderer)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderPresent</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderPresent(renderer:sdl2.Renderer):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderReadPixels</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderReadPixels(renderer:sdl2.Renderer, rect:sdl2.Rect:nil, format:symbol) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderSetClipRect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderSetClipRect(renderer:sdl2.Renderer, rect:sdl2.Rect:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderSetLogicalSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderSetLogicalSize(renderer:sdl2.Renderer, w:number, h:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderSetScale</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderSetScale(renderer:sdl2.Renderer, scaleX:number, scaleY:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderSetViewport</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderSetViewport(renderer:sdl2.Renderer, rect:sdl2.Rect:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RenderTargetSupported</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RenderTargetSupported(renderer:sdl2.Renderer) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetRenderDrawBlendMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetRenderDrawBlendMode(renderer:sdl2.Renderer, blendMode:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetRenderDrawColor</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetRenderDrawColor(renderer:sdl2.Renderer, r:number, g:number, b:number, a:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetRenderTarget</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetRenderTarget(renderer:sdl2.Renderer, texture:sdl2.Texture:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetTextureAlphaMod</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetTextureAlphaMod(texture:sdl2.Texture, alpha:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetTextureBlendMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetTextureBlendMode(texture:sdl2.Texture, blendMode:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetTextureColorMod</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetTextureColorMod(texture:sdl2.Texture, r:number, g:number, b:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.UnlockTexture</strong></div>
<div style="margin-bottom:1em"><code>sdl2.UnlockTexture(texture:sdl2.Texture):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.UpdateTexture</strong></div>
<div style="margin-bottom:1em"><code>sdl2.UpdateTexture(texture:sdl2.Texture, rect:sdl2.Rect:nil, pitch:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.UpdateYUVTexture</strong></div>
<div style="margin-bottom:1em"><code>sdl2.UpdateYUVTexture():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AllocFormat</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AllocFormat(pixel_format:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AllocPalette</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AllocPalette(ncolors:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CalculateGammaRamp</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CalculateGammaRamp(gamma:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.FreeFormat</strong></div>
<div style="margin-bottom:1em"><code>sdl2.FreeFormat(format:sdl2.PixelFormat):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.FreePalette</strong></div>
<div style="margin-bottom:1em"><code>sdl2.FreePalette(palette:sdl2.Palette):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetPixelFormatName</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetPixelFormatName(format:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRGB</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRGB(pixel:number, format:sdl2.PixelFormat) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRGBA</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRGBA(pixel:number, format:sdl2.PixelFormat) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.MapRGB</strong></div>
<div style="margin-bottom:1em"><code>sdl2.MapRGB(format:sdl2.PixelFormat, r:number, g:number, b:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.MapRGBA</strong></div>
<div style="margin-bottom:1em"><code>sdl2.MapRGBA(format:sdl2.PixelFormat, r:number, g:number, b:number, a:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.MasksToPixelFormatEnum</strong></div>
<div style="margin-bottom:1em"><code>sdl2.MasksToPixelFormatEnum(bpp:number, Rmask:number, Gmask:number, Bmask:number, Amask:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.PixelFormatEnumToMasks</strong></div>
<div style="margin-bottom:1em"><code>sdl2.PixelFormatEnumToMasks(format:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetPaletteColors</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetPaletteColors(palette:sdl2.Palette, colors[]:sdl2.Color, firstcolor:number, ncolors:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetPixelFormatPalette</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetPixelFormatPalette(format:sdl2.PixelFormat, palette:sdl2.Palette):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.EnclosePoints</strong></div>
<div style="margin-bottom:1em"><code>sdl2.EnclosePoints(points[]:sdl2.Point, clip:sdl2.Rect) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasIntersection</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasIntersection(A:sdl2.Rect, B:sdl2.Rect) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.IntersectRect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.IntersectRect(A:sdl2.Rect, B:sdl2.Rect) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.IntersectRectAndLine</strong></div>
<div style="margin-bottom:1em"><code>sdl2.IntersectRectAndLine(rect:sdl2.Rect, X1:number, Y1:number, X2:number, Y2:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.PointInRect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.PointInRect(p:sdl2.Point, r:sdl2.Rect):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RectEmpty</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RectEmpty(r:sdl2.Rect) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RectEquals</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RectEquals(a:sdl2.Rect, b:sdl2.Rect) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.UnionRect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.UnionRect(A:sdl2.Rect, B:sdl2.Rect) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.BlitScaled</strong></div>
<div style="margin-bottom:1em"><code>sdl2.BlitScaled(src:sdl2.Surface, srcrect:sdl2.Rect:nil, dst:sdl2.Surface, dstrect:sdl2.Rect:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.BlitSurface</strong></div>
<div style="margin-bottom:1em"><code>sdl2.BlitSurface(src:sdl2.Surface, srcrect:sdl2.Rect:nil, dst:sdl2.Surface, dstrect:sdl2.Rect:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ConvertPixels</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ConvertPixels(width:number, height:number, src_format:number, dst_format:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ConvertSurface</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ConvertSurface(src:sdl2.Surface, fmt:sdl2.PixelFormat, flags:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ConvertSurfaceFormat</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ConvertSurfaceFormat(src:sdl2.Surface, pixel_format:number, flags:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateRGBSurface</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateRGBSurface(flags:number, width:number, height:number, depth:number, Rmask:number, Gmask:number, Bmask:number, Amask:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateRGBSurfaceFrom</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateRGBSurfaceFrom(pixels:array:nomap, width:number, height:number, depth:number, pitch:number, Rmask:number, Gmask:number, Bmask:number, Amask:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateRGBSurfaceFromImage</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateRGBSurfaceFromImage(image:image) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.FillRect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.FillRect(dst:sdl2.Surface, rect:sdl2.Rect:nil, color:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.FillRects</strong></div>
<div style="margin-bottom:1em"><code>sdl2.FillRects(dst:sdl2.Surface, rects[]:sdl2.Rect, color:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.FreeSurface</strong></div>
<div style="margin-bottom:1em"><code>sdl2.FreeSurface(surface:sdl2.Surface):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetClipRect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetClipRect(surface:sdl2.Surface) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetColorKey</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetColorKey(surface:sdl2.Surface) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetSurfaceAlphaMod</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetSurfaceAlphaMod(surface:sdl2.Surface) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetSurfaceBlendMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetSurfaceBlendMode(surface:sdl2.Surface) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetSurfaceColorMod</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetSurfaceColorMod(surface:sdl2.Surface) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LoadBMP</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LoadBMP(src:stream) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LoadBMP_RW</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LoadBMP_RW():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LockSurface</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LockSurface(surface:sdl2.Surface):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LowerBlit</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LowerBlit(src:sdl2.Surface, srcrect:sdl2.Rect:nil, dst:sdl2.Surface, dstrect:sdl2.Rect:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LowerBlitScaled</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LowerBlitScaled(src:sdl2.Surface, srcrect:sdl2.Rect:nil, dst:sdl2.Surface, dstrect:sdl2.Rect:nil):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.MUSTLOCK</strong></div>
<div style="margin-bottom:1em"><code>sdl2.MUSTLOCK(surface:sdl2.Surface) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SaveBMP</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SaveBMP(surface:sdl2.Surface, dst:stream) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SaveBMP_RW</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SaveBMP_RW():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetClipRect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetClipRect(surface:sdl2.Surface, rect:sdl2.Rect) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetColorKey</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetColorKey(surface:sdl2.Surface, flag:number, key:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetSurfaceAlphaMod</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetSurfaceAlphaMod(surface:sdl2.Surface, alpha:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetSurfaceBlendMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetSurfaceBlendMode(surface:sdl2.Surface, blendMode:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetSurfaceColorMod</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetSurfaceColorMod(surface:sdl2.Surface, r:number, g:number, b:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetSurfacePalette</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetSurfacePalette(surface:sdl2.Surface, palette:sdl2.Palette):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetSurfaceRLE</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetSurfaceRLE(surface:sdl2.Surface, flag:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.UnlockSurface</strong></div>
<div style="margin-bottom:1em"><code>sdl2.UnlockSurface(surface:sdl2.Surface):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetClipboardText</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetClipboardText() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasClipboardText</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasClipboardText() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetClipboardText</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetClipboardText(text:string):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AddEventWatch</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AddEventWatch():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.DelEventWatch</strong></div>
<div style="margin-bottom:1em"><code>sdl2.DelEventWatch():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.EventState</strong></div>
<div style="margin-bottom:1em"><code>sdl2.EventState(type:number, state:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.FilterEvents</strong></div>
<div style="margin-bottom:1em"><code>sdl2.FilterEvents():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.FlushEvent</strong></div>
<div style="margin-bottom:1em"><code>sdl2.FlushEvent(type:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.FlushEvents</strong></div>
<div style="margin-bottom:1em"><code>sdl2.FlushEvents(minType:number, maxType:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetEventFilter</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetEventFilter():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetNumTouchDevices</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetNumTouchDevices() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetNumTouchFingers</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetNumTouchFingers(touchId:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetTouchDevice</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetTouchDevice(index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetTouchFinger</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetTouchFinger(touchId:number, index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasEvent</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasEvent(type:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasEvents</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasEvents(minType:number, maxType:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LoadDollarTemplates</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LoadDollarTemplates(touchId:number, src:stream) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AddEvents</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AddEvents(events[]:sdl2.Event) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.PeekEvents</strong></div>
<div style="margin-bottom:1em"><code>sdl2.PeekEvents(numevents:number, minType:number, maxType:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetEvents</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetEvents(numevents:number, minType:number, maxType:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.PollEvent</strong></div>
<div style="margin-bottom:1em"><code>sdl2.PollEvent() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.PumpEvents</strong></div>
<div style="margin-bottom:1em"><code>sdl2.PumpEvents():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.PushEvent</strong></div>
<div style="margin-bottom:1em"><code>sdl2.PushEvent(event:sdl2.Event) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.QuitRequested</strong></div>
<div style="margin-bottom:1em"><code>sdl2.QuitRequested() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RecordGesture</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RecordGesture(touchId:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RegisterEvents</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RegisterEvents(numevents:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SaveAllDollarTemplates</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SaveAllDollarTemplates(dst:stream) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SaveDollarTemplate</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SaveDollarTemplate(gestureId:number, dst:stream):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetEventFilter</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetEventFilter():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WaitEvent</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WaitEvent() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WaitEventTimeout</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WaitEventTimeout(timeout:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CheckKeyboardState</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CheckKeyboardState(scancode:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetKeyFromName</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetKeyFromName(name:string) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetKeyFromScancode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetKeyFromScancode(scancode:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetKeyName</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetKeyName(key:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetKeyboardFocus</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetKeyboardFocus() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetKeyboardState</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetKeyboardState() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetModState</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetModState() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetScancodeFromKey</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetScancodeFromKey(key:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetScancodeFromName</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetScancodeFromName(name:string) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetScancodeName</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetScancodeName(scancode:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasScreenKeyboardSupport</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasScreenKeyboardSupport() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.IsScreenKeyboardShown</strong></div>
<div style="margin-bottom:1em"><code>sdl2.IsScreenKeyboardShown(window:sdl2.Window) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.IsTextInputActive</strong></div>
<div style="margin-bottom:1em"><code>sdl2.IsTextInputActive() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetModState</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetModState(modstate:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetTextInputRect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetTextInputRect(rect:sdl2.Rect):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.StartTextInput</strong></div>
<div style="margin-bottom:1em"><code>sdl2.StartTextInput():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.StopTextInput</strong></div>
<div style="margin-bottom:1em"><code>sdl2.StopTextInput():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CaptureMouse</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CaptureMouse(enalbed:boolean):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateColorCursor</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateColorCursor(surface:sdl2.Surface, hot_x:number, hot_y:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateCursor</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateCursor(data:array@uint8:nomap, mask:array@uint8:nomap, w:number, h:number, hot_x:number, hot_y:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateSystemCursor</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateSystemCursor(id:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.FreeCursor</strong></div>
<div style="margin-bottom:1em"><code>sdl2.FreeCursor(cursor:sdl2.Cursor):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetCursor</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetCursor() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetDefaultCursor</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetDefaultCursor() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetGlobalMouseState</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetGlobalMouseState():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetMouseFocus</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetMouseFocus() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetMouseState</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetMouseState() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRelativeMouseMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRelativeMouseMode() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetRelativeMouseState</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetRelativeMouseState() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetCursor</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetCursor(cursor:sdl2.Cursor):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SetRelativeMouseMode</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SetRelativeMouseMode(enabled:boolean):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ShowCursor</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ShowCursor(toggle:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WarpMouseGlobal</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WarpMouseGlobal(x:number, y:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WarpMouseInWindow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WarpMouseInWindow(window:sdl2.Window, x:number, y:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickClose</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickClose(joystick:sdl2.Joystick):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickEventState</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickEventState(state:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickGetAttached</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickGetAttached(joystick:sdl2.Joystick) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickGetAxis</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickGetAxis(joystick:sdl2.Joystick, axis:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickGetBall</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickGetBall(joystick:sdl2.Joystick, ball:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickGetButton</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickGetButton(joystick:sdl2.Joystick, button:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickGetDeviceGUID</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickGetDeviceGUID(device_index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickGetGUID</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickGetGUID(joystick:sdl2.Joystick) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickGetGUIDFromString</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickGetGUIDFromString(pchGUID:string) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickGetGUIDString</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickGetGUIDString(guid:sdl2.JoystickGUID) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickGetHat</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickGetHat(joystick:sdl2.Joystick, hat:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickInstanceID</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickInstanceID(joystick:sdl2.Joystick) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickName</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickName(joystick:sdl2.Joystick) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickNameForIndex</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickNameForIndex(device_index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickNumAxes</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickNumAxes(joystick:sdl2.Joystick) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickNumBalls</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickNumBalls(joystick:sdl2.Joystick) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickNumButtons</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickNumButtons(joystick:sdl2.Joystick) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickNumHats</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickNumHats(joystick:sdl2.Joystick) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickOpen</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickOpen(device_index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickUpdate</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickUpdate():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.NumJoysticks</strong></div>
<div style="margin-bottom:1em"><code>sdl2.NumJoysticks() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerAddMapping</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerAddMapping(mappingString:string) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerAddMappingsFromFile</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerAddMappingsFromFile(file:stream) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerAddMappingsFromRW</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerAddMappingsFromRW():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerClose</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerClose(gamecontroller:sdl2.GameController):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerEventState</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerEventState(state:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerGetAttached</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerGetAttached(gamecontroller:sdl2.GameController) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerGetAxis</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerGetAxis(gamecontroller:sdl2.GameController, axis:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerGetAxisFromString</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerGetAxisFromString(pchString:string) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerGetBindForAxis</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerGetBindForAxis(gamecontroller:sdl2.GameController, axis:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerGetBindForButton</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerGetBindForButton(gamecontroller:sdl2.GameController, button:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerGetButton</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerGetButton(gamecontroller:sdl2.GameController, button:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerGetButtonFromString</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerGetButtonFromString(pchString:string) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerGetJoystick</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerGetJoystick(gamecontroller:sdl2.GameController) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerGetStringForAxis</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerGetStringForAxis(axis:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerGetStringForButton</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerGetStringForButton(button:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerMapping</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerMapping(gamecontroller:sdl2.GameController) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerMappingForGUID</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerMappingForGUID(guid:sdl2.JoystickGUID) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerName</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerName(gamecontroller:sdl2.GameController) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerNameForIndex</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerNameForIndex(joystick_index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerOpen</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerOpen(joystick_index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GameControllerUpdate</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GameControllerUpdate():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.IsGameController</strong></div>
<div style="margin-bottom:1em"><code>sdl2.IsGameController(joystick_index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticClose</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticClose(haptic:sdl2.Haptic):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticDestroyEffect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticDestroyEffect(haptic:sdl2.Haptic, effect:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticEffectSupported</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticEffectSupported(haptic:sdl2.Haptic, effect:sdl2.HapticEffect) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticGetEffectStatus</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticGetEffectStatus(haptic:sdl2.Haptic, effect:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticIndex</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticIndex(haptic:sdl2.Haptic) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticName</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticName(device_index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticNewEffect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticNewEffect(haptic:sdl2.Haptic, effect:sdl2.HapticEffect) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticNumAxes</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticNumAxes(haptic:sdl2.Haptic) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticNumEffects</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticNumEffects(haptic:sdl2.Haptic) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticNumEffectsPlaying</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticNumEffectsPlaying(haptic:sdl2.Haptic) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticOpen</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticOpen(device_index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticOpenFromJoystick</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticOpenFromJoystick(joystick:sdl2.Joystick) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticOpenFromMouse</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticOpenFromMouse() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticOpened</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticOpened(device_index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticPause</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticPause(haptic:sdl2.Haptic):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticQuery</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticQuery(haptic:sdl2.Haptic) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticRumbleInit</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticRumbleInit(haptic:sdl2.Haptic):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticRumblePlay</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticRumblePlay(haptic:sdl2.Haptic, strength:number, length:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticRumbleStop</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticRumbleStop(haptic:sdl2.Haptic):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticRumbleSupported</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticRumbleSupported(haptic:sdl2.Haptic) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticRunEffect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticRunEffect(haptic:sdl2.Haptic, effect:number, iterations:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticSetAutocenter</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticSetAutocenter(haptic:sdl2.Haptic, autocenter:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticSetGain</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticSetGain(haptic:sdl2.Haptic, gain:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticStopAll</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticStopAll(haptic:sdl2.Haptic):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticStopEffect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticStopEffect(haptic:sdl2.Haptic, effect:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticUnpause</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticUnpause(haptic:sdl2.Haptic):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HapticUpdateEffect</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HapticUpdateEffect(haptic:sdl2.Haptic, effect:number, data:sdl2.HapticEffect):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.JoystickIsHaptic</strong></div>
<div style="margin-bottom:1em"><code>sdl2.JoystickIsHaptic(joystick:sdl2.Joystick) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.MouseIsHaptic</strong></div>
<div style="margin-bottom:1em"><code>sdl2.MouseIsHaptic() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.NumHaptics</strong></div>
<div style="margin-bottom:1em"><code>sdl2.NumHaptics() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AudioInit</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AudioInit(driver_name:string):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AudioQuit</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AudioQuit():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.BuildAudioCVT</strong></div>
<div style="margin-bottom:1em"><code>sdl2.BuildAudioCVT(cvt:sdl2.AudioCVT, src_format:number, src_channels:number, src_rate:number, dst_format:number, dst_channels:number, dst_rate:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ClearQueuedAudio</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ClearQueuedAudio(dev:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CloseAudio</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CloseAudio():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CloseAudioDevice</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CloseAudioDevice(dev:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ConvertAudio</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ConvertAudio(cvt:sdl2.AudioCVT):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.FreeWAV</strong></div>
<div style="margin-bottom:1em"><code>sdl2.FreeWAV(wav:sdl2.Wav):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetAudioDeviceName</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetAudioDeviceName(index:number, iscapture:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetAudioDeviceStatus</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetAudioDeviceStatus(dev:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetAudioDriver</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetAudioDriver(index:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetAudioStatus</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetAudioStatus() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetCurrentAudioDriver</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetCurrentAudioDriver() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetNumAudioDevices</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetNumAudioDevices(iscapture:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetNumAudioDrivers</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetNumAudioDrivers() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetQueuedAudioSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetQueuedAudioSize(dev:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LoadWAV</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LoadWAV(file:stream) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LoadWAV_RW</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LoadWAV_RW():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LockAudio</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LockAudio():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LockAudioDevice</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LockAudioDevice(dev:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.MixAudio</strong></div>
<div style="margin-bottom:1em"><code>sdl2.MixAudio(volume:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.MixAudioFormat</strong></div>
<div style="margin-bottom:1em"><code>sdl2.MixAudioFormat(format:number, volume:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.OpenAudio</strong></div>
<div style="margin-bottom:1em"><code>sdl2.OpenAudio(desired:sdl2.AudioSpec) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.OpenAudioDevice</strong></div>
<div style="margin-bottom:1em"><code>sdl2.OpenAudioDevice(device:string, iscapture:number, desired:sdl2.AudioSpec, allowed_changes:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.PauseAudio</strong></div>
<div style="margin-bottom:1em"><code>sdl2.PauseAudio(pause_on:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.PauseAudioDevice</strong></div>
<div style="margin-bottom:1em"><code>sdl2.PauseAudioDevice(dev:number, pause_on:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.QueueAudio</strong></div>
<div style="margin-bottom:1em"><code>sdl2.QueueAudio(dev:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.UnlockAudio</strong></div>
<div style="margin-bottom:1em"><code>sdl2.UnlockAudio():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.UnlockAudioDevice</strong></div>
<div style="margin-bottom:1em"><code>sdl2.UnlockAudioDevice(dev:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AUDIO_BITSIZE</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AUDIO_BITSIZE(x:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AUDIO_ISFLOAT</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AUDIO_ISFLOAT(x:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AUDIO_ISBIGENDIAN</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AUDIO_ISBIGENDIAN(x:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AUDIO_ISSIGNED</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AUDIO_ISSIGNED(x:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AUDIO_ISINT</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AUDIO_ISINT(x:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AUDIO_ISLITTLEENDIAN</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AUDIO_ISLITTLEENDIAN(x:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AUDIO_ISUNSIGNED</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AUDIO_ISUNSIGNED(x:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateThread</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateThread():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.DetachThread</strong></div>
<div style="margin-bottom:1em"><code>sdl2.DetachThread():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetThreadID</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetThreadID():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetThreadName</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetThreadName():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetThreadPriority</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetThreadPriority():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.TLSCreate</strong></div>
<div style="margin-bottom:1em"><code>sdl2.TLSCreate():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.TLSGet</strong></div>
<div style="margin-bottom:1em"><code>sdl2.TLSGet():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.TLSSet</strong></div>
<div style="margin-bottom:1em"><code>sdl2.TLSSet():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ThreadID</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ThreadID():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WaitThread</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WaitThread():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CondBroadcast</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CondBroadcast():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CondSignal</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CondSignal():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CondWait</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CondWait():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CondWaitTimeout</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CondWaitTimeout():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateCond</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateCond():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateMutex</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateMutex():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CreateSemaphore</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CreateSemaphore():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.DestroyCond</strong></div>
<div style="margin-bottom:1em"><code>sdl2.DestroyCond():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.DestroyMutex</strong></div>
<div style="margin-bottom:1em"><code>sdl2.DestroyMutex():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.DestroySemaphore</strong></div>
<div style="margin-bottom:1em"><code>sdl2.DestroySemaphore():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.LockMutex</strong></div>
<div style="margin-bottom:1em"><code>sdl2.LockMutex():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SemPost</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SemPost():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SemTryWait</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SemTryWait():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SemValue</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SemValue():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SemWait</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SemWait():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SemWaitTimeout</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SemWaitTimeout():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.TryLockMutex</strong></div>
<div style="margin-bottom:1em"><code>sdl2.TryLockMutex():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.UnlockMutex</strong></div>
<div style="margin-bottom:1em"><code>sdl2.UnlockMutex():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicAdd</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicAdd():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicCAS</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicCAS():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicCASPtr</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicCASPtr():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicDecRef</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicDecRef():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicGet</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicGet():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicGetPtr</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicGetPtr():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicIncRef</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicIncRef():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicLock</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicLock():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicSet</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicSet():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicSetPtr</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicSetPtr():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicTryLock</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicTryLock():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AtomicUnlock</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AtomicUnlock():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.CompilerBarrier</strong></div>
<div style="margin-bottom:1em"><code>sdl2.CompilerBarrier():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AddTimer</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AddTimer(interval:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.Delay</strong></div>
<div style="margin-bottom:1em"><code>sdl2.Delay(ms:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetPerformanceCounter</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetPerformanceCounter() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetPerformanceFrequency</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetPerformanceFrequency() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetTicks</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetTicks() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RemoveTimer</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RemoveTimer(id:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.TICKS_PASSED</strong></div>
<div style="margin-bottom:1em"><code>sdl2.TICKS_PASSED(A:number, B:number) {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetBasePath</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetBasePath():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetPrefPath</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetPrefPath(org:string, app:string):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AllocRW</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AllocRW():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.FreeRW</strong></div>
<div style="margin-bottom:1em"><code>sdl2.FreeRW():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RWFromConstMem</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RWFromConstMem():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RWFromFP</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RWFromFP():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RWFromFile</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RWFromFile():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RWFromMem</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RWFromMem():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RWclose</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RWclose():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RWread</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RWread():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RWseek</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RWseek():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RWtell</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RWtell():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.RWwrite</strong></div>
<div style="margin-bottom:1em"><code>sdl2.RWwrite():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ReadBE16</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ReadBE16():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ReadBE32</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ReadBE32():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ReadBE64</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ReadBE64():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ReadLE16</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ReadLE16():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ReadLE32</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ReadLE32():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.ReadLE64</strong></div>
<div style="margin-bottom:1em"><code>sdl2.ReadLE64():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WriteBE16</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WriteBE16():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WriteBE32</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WriteBE32():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WriteBE64</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WriteBE64():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WriteLE16</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WriteLE16():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WriteLE32</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WriteLE32():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.WriteLE64</strong></div>
<div style="margin-bottom:1em"><code>sdl2.WriteLE64():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetPlatform</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetPlatform() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetCPUCacheLineSize</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetCPUCacheLineSize() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetCPUCount</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetCPUCount() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetSystemRAM</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetSystemRAM() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.Has3DNow</strong></div>
<div style="margin-bottom:1em"><code>sdl2.Has3DNow() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasAVX</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasAVX() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasAVX2</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasAVX2():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasAltiVec</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasAltiVec() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasMMX</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasMMX() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasRDTSC</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasRDTSC() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasSSE</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasSSE() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasSSE2</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasSSE2() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasSSE3</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasSSE3() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasSSE41</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasSSE41() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.HasSSE42</strong></div>
<div style="margin-bottom:1em"><code>sdl2.HasSSE42() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.Swap16</strong></div>
<div style="margin-bottom:1em"><code>sdl2.Swap16():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.Swap32</strong></div>
<div style="margin-bottom:1em"><code>sdl2.Swap32():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.Swap64</strong></div>
<div style="margin-bottom:1em"><code>sdl2.Swap64():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SwapBE16</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SwapBE16():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SwapBE32</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SwapBE32():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SwapBE64</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SwapBE64():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SwapFloat</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SwapFloat():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SwapFloatBE</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SwapFloatBE():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SwapFloatLE</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SwapFloatLE():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SwapLE16</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SwapLE16():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SwapLE32</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SwapLE32():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.SwapLE64</strong></div>
<div style="margin-bottom:1em"><code>sdl2.SwapLE64():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.MostSignificantBitIndex32</strong></div>
<div style="margin-bottom:1em"><code>sdl2.MostSignificantBitIndex32(x:number):void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.GetPowerInfo</strong></div>
<div style="margin-bottom:1em"><code>sdl2.GetPowerInfo() {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AndroidGetActivity</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AndroidGetActivity():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AndroidGetExternalStoragePath</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AndroidGetExternalStoragePath():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AndroidGetExternalStorageState</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AndroidGetExternalStorageState():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AndroidGetInternalStoragePath</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AndroidGetInternalStoragePath():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.AndroidGetJNIEnv</strong></div>
<div style="margin-bottom:1em"><code>sdl2.AndroidGetJNIEnv():void</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">sdl2.acos</strong></div>
<div style="margin-bottom:1em"><code>sdl2.acos(x:number) {block?}</code></div>

</p>
<h2><span class="caption-index-2">50.3</span><a name="anchor-50-3"></a>sdl2.Window Class</h2>
<h2><span class="caption-index-2">50.4</span><a name="anchor-50-4"></a>sdl2.Renderer Class</h2>
<h2><span class="caption-index-2">50.5</span><a name="anchor-50-5"></a>sdl2.Texture Class</h2>
<h2><span class="caption-index-2">50.6</span><a name="anchor-50-6"></a>sdl2.Event Class</h2>
<h2><span class="caption-index-2">50.7</span><a name="anchor-50-7"></a>sdl2.Point Class</h2>
<h2><span class="caption-index-2">50.8</span><a name="anchor-50-8"></a>sdl2.Rect Class</h2>
<h2><span class="caption-index-2">50.9</span><a name="anchor-50-9"></a>sdl2.Color Class</h2>
<h2><span class="caption-index-2">50.10</span><a name="anchor-50-10"></a>sdl2.Palette Class</h2>
<h2><span class="caption-index-2">50.11</span><a name="anchor-50-11"></a>sdl2.PixelFormat Class</h2>
<h2><span class="caption-index-2">50.12</span><a name="anchor-50-12"></a>sdl2.Keysym Class</h2>
<h2><span class="caption-index-2">50.13</span><a name="anchor-50-13"></a>sdl2.Cursor Class</h2>
<h2><span class="caption-index-2">50.14</span><a name="anchor-50-14"></a>sdl2.Joystick Class</h2>
<h2><span class="caption-index-2">50.15</span><a name="anchor-50-15"></a>sdl2.JoystickGUID Class</h2>
<h2><span class="caption-index-2">50.16</span><a name="anchor-50-16"></a>sdl2.GameController Class</h2>
<h2><span class="caption-index-2">50.17</span><a name="anchor-50-17"></a>sdl2.GameControllerButtonBind Class</h2>
<h2><span class="caption-index-2">50.18</span><a name="anchor-50-18"></a>sdl2.AudioCVT Class</h2>
<h2><span class="caption-index-2">50.19</span><a name="anchor-50-19"></a>sdl2.AudioSpec Class</h2>
<h2><span class="caption-index-2">50.20</span><a name="anchor-50-20"></a>sdl2.Wav Class</h2>
<h2><span class="caption-index-2">50.21</span><a name="anchor-50-21"></a>sdl2.RendererInfo Class</h2>
<h2><span class="caption-index-2">50.22</span><a name="anchor-50-22"></a>sdl2.DisplayMode Class</h2>
<h2><span class="caption-index-2">50.23</span><a name="anchor-50-23"></a>sdl2.GLContext Class</h2>
<h2><span class="caption-index-2">50.24</span><a name="anchor-50-24"></a>sdl2.HapticEffect Class</h2>
<h2><span class="caption-index-2">50.25</span><a name="anchor-50-25"></a>sdl2.Surface Class</h2>
<h2><span class="caption-index-2">50.26</span><a name="anchor-50-26"></a>sdl2.Finger Class</h2>
<h2><span class="caption-index-2">50.27</span><a name="anchor-50-27"></a>Thanks</h2>
<p>
This module uses SDL2 library which is distributed in the following site:
</p>
<p>
<a href="http://www.libsdl.org/">http://www.libsdl.org/</a>
</p>
<p />

{% endraw %}
