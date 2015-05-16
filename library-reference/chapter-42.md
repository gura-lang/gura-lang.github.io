---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">42</span><a name="anchor-42"></a>sdl2 Module</h1>
<p>
The <code>sdl2</code> module provices functions of SDL2 library.
</p>
<h2><span class="caption-index-2">42.1</span><a name="anchor-42-1"></a>Module Function</h2>
<p>
<strong>sdl2.Init</strong>
</p>
<p>
<code>sdl2.Init(flags:number):void</code>
</p>
<p>
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
<strong>sdl2.InitSubSystem</strong>
</p>
<p>
<code>sdl2.InitSubSystem(flags:number):void</code>
</p>
<p>
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
<strong>sdl2.Quit</strong>
</p>
<p>
<code>sdl2.Quit():void</code>
</p>
<p>
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
<strong>sdl2.QuitSubSystem</strong>
</p>
<p>
<code>sdl2.QuitSubSystem(flags:number):void</code>
</p>
<p>
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
<strong>sdl2.SetMainReady</strong>
</p>
<p>
<code>sdl2.SetMainReady():void</code>
</p>
<p>
Use this function to circumvent failure of <code>SDL_Init()</code> when not using <code>SDL_main()</code> as an entry point.
</p>
<p>
This function is defined in SDL_main.h, along with the preprocessor rule to redefine <code>main()</code> as <code>SDL_main()</code>. Thus to ensure that your <code>main()</code> function will not be changed it is necessary to define <code>SDL_MAIN_HANDLED</code> before including SDL.h.
</p>
<p>
<strong>sdl2.WasInit</strong>
</p>
<p>
<code>sdl2.WasInit(flags:number) {block?}</code>
</p>
<p>
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
<strong>sdl2.AddHintCallback</strong>
</p>
<p>
<code>sdl2.AddHintCallback():void</code>
</p>
<p>
<strong>sdl2.ClearHints</strong>
</p>
<p>
<code>sdl2.ClearHints():void</code>
</p>
<p>
<strong>sdl2.DelhintCallback</strong>
</p>
<p>
<code>sdl2.DelhintCallback():void</code>
</p>
<p>
<strong>sdl2.GetHint</strong>
</p>
<p>
<code>sdl2.GetHint():void</code>
</p>
<p>
<strong>sdl2.SetHint</strong>
</p>
<p>
<code>sdl2.SetHint():void</code>
</p>
<p>
<strong>sdl2.SetHintWithPriority</strong>
</p>
<p>
<code>sdl2.SetHintWithPriority():void</code>
</p>
<p>
<strong>sdl2.ClearError</strong>
</p>
<p>
<code>sdl2.ClearError():void</code>
</p>
<p>
Use this function to clear any previous error message.
</p>
<p>
<strong>sdl2.GetError</strong>
</p>
<p>
<code>sdl2.GetError() {block?}</code>
</p>
<p>
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
<strong>sdl2.SetError</strong>
</p>
<p>
<code>sdl2.SetError():void</code>
</p>
<p>
<strong>sdl2.Log</strong>
</p>
<p>
<code>sdl2.Log():void</code>
</p>
<p>
<strong>sdl2.LogCritical</strong>
</p>
<p>
<code>sdl2.LogCritical():void</code>
</p>
<p>
<strong>sdl2.LogDebug</strong>
</p>
<p>
<code>sdl2.LogDebug():void</code>
</p>
<p>
<strong>sdl2.LogError</strong>
</p>
<p>
<code>sdl2.LogError():void</code>
</p>
<p>
<strong>sdl2.LogGetOutputFunction</strong>
</p>
<p>
<code>sdl2.LogGetOutputFunction():void</code>
</p>
<p>
<strong>sdl2.LogGetPriority</strong>
</p>
<p>
<code>sdl2.LogGetPriority():void</code>
</p>
<p>
<strong>sdl2.LogInfo</strong>
</p>
<p>
<code>sdl2.LogInfo():void</code>
</p>
<p>
<strong>sdl2.LogMessage</strong>
</p>
<p>
<code>sdl2.LogMessage():void</code>
</p>
<p>
<strong>sdl2.LogMessageV</strong>
</p>
<p>
<code>sdl2.LogMessageV():void</code>
</p>
<p>
<strong>sdl2.LogResetPriorities</strong>
</p>
<p>
<code>sdl2.LogResetPriorities():void</code>
</p>
<p>
<strong>sdl2.LogSetAllPriority</strong>
</p>
<p>
<code>sdl2.LogSetAllPriority():void</code>
</p>
<p>
<strong>sdl2.LogSetOutputFunction</strong>
</p>
<p>
<code>sdl2.LogSetOutputFunction():void</code>
</p>
<p>
<strong>sdl2.LogSetPriority</strong>
</p>
<p>
<code>sdl2.LogSetPriority():void</code>
</p>
<p>
<strong>sdl2.LogVerbose</strong>
</p>
<p>
<code>sdl2.LogVerbose():void</code>
</p>
<p>
<strong>sdl2.LogWarn</strong>
</p>
<p>
<code>sdl2.LogWarn():void</code>
</p>
<p>
<strong>sdl2.GetAssertionHandler</strong>
</p>
<p>
<code>sdl2.GetAssertionHandler():void</code>
</p>
<p>
<strong>sdl2.GetAssertionReport</strong>
</p>
<p>
<code>sdl2.GetAssertionReport():void</code>
</p>
<p>
<strong>sdl2.GetDefaultAssertionHandler</strong>
</p>
<p>
<code>sdl2.GetDefaultAssertionHandler():void</code>
</p>
<p>
<strong>sdl2.ResetAssertionReport</strong>
</p>
<p>
<code>sdl2.ResetAssertionReport():void</code>
</p>
<p>
<strong>sdl2.SetAssertionHandler</strong>
</p>
<p>
<code>sdl2.SetAssertionHandler():void</code>
</p>
<p>
<strong>sdl2.TriggerBreakpoint</strong>
</p>
<p>
<code>sdl2.TriggerBreakpoint():void</code>
</p>
<p>
<strong>sdl2.assert</strong>
</p>
<p>
<code>sdl2.assert():void</code>
</p>
<p>
<strong>sdl2.assert_paranoid</strong>
</p>
<p>
<code>sdl2.assert_paranoid():void</code>
</p>
<p>
<strong>sdl2.assert_release</strong>
</p>
<p>
<code>sdl2.assert_release():void</code>
</p>
<p>
<strong>sdl2.GetRevision</strong>
</p>
<p>
<code>sdl2.GetRevision() {block?}</code>
</p>
<p>
<strong>sdl2.GetRevisionNumber</strong>
</p>
<p>
<code>sdl2.GetRevisionNumber() {block?}</code>
</p>
<p>
<strong>sdl2.GetVersion</strong>
</p>
<p>
<code>sdl2.GetVersion() {block?}</code>
</p>
<p>
<strong>sdl2.VERSION</strong>
</p>
<p>
<code>sdl2.VERSION() {block?}</code>
</p>
<p>
<strong>sdl2.VERSION_ATLEAST</strong>
</p>
<p>
<code>sdl2.VERSION_ATLEAST(X:number, Y:number, Z:number) {block?}</code>
</p>
<p>
<strong>sdl2.CreateWindow</strong>
</p>
<p>
<code>sdl2.CreateWindow(title:string, x:number, y:number, w:number, h:number, flags:number) {block?}</code>
</p>
<p>
<strong>sdl2.CreateWindowAndRenderer</strong>
</p>
<p>
<code>sdl2.CreateWindowAndRenderer(width:number, height:number, window_flags:number) {block?}</code>
</p>
<p>
<strong>sdl2.CreateWindowFrom</strong>
</p>
<p>
<code>sdl2.CreateWindowFrom():void</code>
</p>
<p>
<strong>sdl2.DestroyWindow</strong>
</p>
<p>
<code>sdl2.DestroyWindow(window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.DisableScreenSaver</strong>
</p>
<p>
<code>sdl2.DisableScreenSaver():void</code>
</p>
<p>
<strong>sdl2.EnableScreenSaver</strong>
</p>
<p>
<code>sdl2.EnableScreenSaver():void</code>
</p>
<p>
<strong>sdl2.GL_CreateContext</strong>
</p>
<p>
<code>sdl2.GL_CreateContext(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GL_DeleteContext</strong>
</p>
<p>
<code>sdl2.GL_DeleteContext(context:sdl2.GLContext):void</code>
</p>
<p>
<strong>sdl2.GL_ExtensionSupported</strong>
</p>
<p>
<code>sdl2.GL_ExtensionSupported(extension:string) {block?}</code>
</p>
<p>
<strong>sdl2.GL_GetAttribute</strong>
</p>
<p>
<code>sdl2.GL_GetAttribute(attr:number) {block?}</code>
</p>
<p>
<strong>sdl2.GL_GetCurrentContext</strong>
</p>
<p>
<code>sdl2.GL_GetCurrentContext() {block?}</code>
</p>
<p>
<strong>sdl2.GL_GetCurrentWindow</strong>
</p>
<p>
<code>sdl2.GL_GetCurrentWindow() {block?}</code>
</p>
<p>
<strong>sdl2.GL_GetDrawableSize</strong>
</p>
<p>
<code>sdl2.GL_GetDrawableSize(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GL_GetProcAddress</strong>
</p>
<p>
<code>sdl2.GL_GetProcAddress():void</code>
</p>
<p>
<strong>sdl2.GL_GetSwapInterval</strong>
</p>
<p>
<code>sdl2.GL_GetSwapInterval() {block?}</code>
</p>
<p>
<strong>sdl2.GL_LoadLibrary</strong>
</p>
<p>
<code>sdl2.GL_LoadLibrary(path:string):void</code>
</p>
<p>
<strong>sdl2.GL_MakeCurrent</strong>
</p>
<p>
<code>sdl2.GL_MakeCurrent(window:sdl2.Window, context:sdl2.GLContext):void</code>
</p>
<p>
<strong>sdl2.GL_ResetAttributes</strong>
</p>
<p>
<code>sdl2.GL_ResetAttributes():void</code>
</p>
<p>
<strong>sdl2.GL_SetAttribute</strong>
</p>
<p>
<code>sdl2.GL_SetAttribute(attr:number, value:number):void</code>
</p>
<p>
<strong>sdl2.GL_SetSwapInterval</strong>
</p>
<p>
<code>sdl2.GL_SetSwapInterval(interval:number):void</code>
</p>
<p>
<strong>sdl2.GL_SwapWindow</strong>
</p>
<p>
<code>sdl2.GL_SwapWindow(window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.GL_UnloadLibrary</strong>
</p>
<p>
<code>sdl2.GL_UnloadLibrary():void</code>
</p>
<p>
<strong>sdl2.GetClosestDisplayMode</strong>
</p>
<p>
<code>sdl2.GetClosestDisplayMode(displayIndex:number, mode:sdl2.DisplayMode) {block?}</code>
</p>
<p>
<strong>sdl2.GetCurrentDisplayMode</strong>
</p>
<p>
<code>sdl2.GetCurrentDisplayMode(displayIndex:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetCurrentVideoDriver</strong>
</p>
<p>
<code>sdl2.GetCurrentVideoDriver() {block?}</code>
</p>
<p>
<strong>sdl2.GetDesktopDisplayMode</strong>
</p>
<p>
<code>sdl2.GetDesktopDisplayMode(displayIndex:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetDisplayBounds</strong>
</p>
<p>
<code>sdl2.GetDisplayBounds(displayIndex:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetDisplayMode</strong>
</p>
<p>
<code>sdl2.GetDisplayMode(displayIndex:number, modeIndex:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetDisplayName</strong>
</p>
<p>
<code>sdl2.GetDisplayName(dipslayIndex:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetNumDisplayModes</strong>
</p>
<p>
<code>sdl2.GetNumDisplayModes(displayIndex:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetNumVideoDisplays</strong>
</p>
<p>
<code>sdl2.GetNumVideoDisplays() {block?}</code>
</p>
<p>
<strong>sdl2.GetNumVideoDrivers</strong>
</p>
<p>
<code>sdl2.GetNumVideoDrivers() {block?}</code>
</p>
<p>
<strong>sdl2.GetVideoDriver</strong>
</p>
<p>
<code>sdl2.GetVideoDriver(index:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowBrightness</strong>
</p>
<p>
<code>sdl2.GetWindowBrightness(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowData</strong>
</p>
<p>
<code>sdl2.GetWindowData(window:sdl2.Window, name:string):void</code>
</p>
<p>
<strong>sdl2.GetWindowDisplayIndex</strong>
</p>
<p>
<code>sdl2.GetWindowDisplayIndex(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowDisplayMode</strong>
</p>
<p>
<code>sdl2.GetWindowDisplayMode(window:sdl2.Window, mode:sdl2.DisplayMode):void</code>
</p>
<p>
<strong>sdl2.GetWindowFlags</strong>
</p>
<p>
<code>sdl2.GetWindowFlags(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowFromID</strong>
</p>
<p>
<code>sdl2.GetWindowFromID(id:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowGammaRamp</strong>
</p>
<p>
<code>sdl2.GetWindowGammaRamp(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowGrab</strong>
</p>
<p>
<code>sdl2.GetWindowGrab(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowID</strong>
</p>
<p>
<code>sdl2.GetWindowID(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowMaximumSize</strong>
</p>
<p>
<code>sdl2.GetWindowMaximumSize(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowMinimumSize</strong>
</p>
<p>
<code>sdl2.GetWindowMinimumSize(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowPixelFormat</strong>
</p>
<p>
<code>sdl2.GetWindowPixelFormat(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowPosition</strong>
</p>
<p>
<code>sdl2.GetWindowPosition(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowSize</strong>
</p>
<p>
<code>sdl2.GetWindowSize(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowSurface</strong>
</p>
<p>
<code>sdl2.GetWindowSurface(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowTitle</strong>
</p>
<p>
<code>sdl2.GetWindowTitle(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetWindowWMInfo</strong>
</p>
<p>
<code>sdl2.GetWindowWMInfo(window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.HideWindow</strong>
</p>
<p>
<code>sdl2.HideWindow(window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.IsScreenSaverEnabled</strong>
</p>
<p>
<code>sdl2.IsScreenSaverEnabled() {block?}</code>
</p>
<p>
<strong>sdl2.MaximizeWindow</strong>
</p>
<p>
<code>sdl2.MaximizeWindow(window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.MinimizeWindow</strong>
</p>
<p>
<code>sdl2.MinimizeWindow(window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.RaiseWindow</strong>
</p>
<p>
<code>sdl2.RaiseWindow(window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.RestoreWindow</strong>
</p>
<p>
<code>sdl2.RestoreWindow(window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.SetWindowBordered</strong>
</p>
<p>
<code>sdl2.SetWindowBordered(window:sdl2.Window, bordered:boolean):void</code>
</p>
<p>
<strong>sdl2.SetWindowBrightness</strong>
</p>
<p>
<code>sdl2.SetWindowBrightness(window:sdl2.Window, brightness:number):void</code>
</p>
<p>
<strong>sdl2.SetWindowData</strong>
</p>
<p>
<code>sdl2.SetWindowData(window:sdl2.Window, name:string):void</code>
</p>
<p>
<strong>sdl2.SetWindowDisplayMode</strong>
</p>
<p>
<code>sdl2.SetWindowDisplayMode(window:sdl2.Window, mode:sdl2.DisplayMode):void</code>
</p>
<p>
<strong>sdl2.SetWindowFullscreen</strong>
</p>
<p>
<code>sdl2.SetWindowFullscreen(window:sdl2.Window, flags:number):void</code>
</p>
<p>
<strong>sdl2.SetWindowGammaRamp</strong>
</p>
<p>
<code>sdl2.SetWindowGammaRamp(window:sdl2.Window, red[]:number, green[]:number, blue[]:number):void</code>
</p>
<p>
<strong>sdl2.SetWindowGrab</strong>
</p>
<p>
<code>sdl2.SetWindowGrab(window:sdl2.Window, grabbed:boolean):void</code>
</p>
<p>
<strong>sdl2.SetWindowHitTest</strong>
</p>
<p>
<code>sdl2.SetWindowHitTest(window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.SetWindowIcon</strong>
</p>
<p>
<code>sdl2.SetWindowIcon(window:sdl2.Window, icon:sdl2.Surface):void</code>
</p>
<p>
<strong>sdl2.SetWindowMaximumSize</strong>
</p>
<p>
<code>sdl2.SetWindowMaximumSize(window:sdl2.Window, max_w:number, max_h:number):void</code>
</p>
<p>
<strong>sdl2.SetWindowMinimumSize</strong>
</p>
<p>
<code>sdl2.SetWindowMinimumSize(window:sdl2.Window, min_w:number, min_h:number):void</code>
</p>
<p>
<strong>sdl2.SetWindowPosition</strong>
</p>
<p>
<code>sdl2.SetWindowPosition(window:sdl2.Window, x:number, y:number):void</code>
</p>
<p>
<strong>sdl2.SetWindowSize</strong>
</p>
<p>
<code>sdl2.SetWindowSize(window:sdl2.Window, w:number, h:number):void</code>
</p>
<p>
<strong>sdl2.SetWindowTitle</strong>
</p>
<p>
<code>sdl2.SetWindowTitle(window:sdl2.Window, title:string):void</code>
</p>
<p>
<strong>sdl2.ShowMessageBox</strong>
</p>
<p>
<code>sdl2.ShowMessageBox():void</code>
</p>
<p>
<strong>sdl2.ShowSimpleMessageBox</strong>
</p>
<p>
<code>sdl2.ShowSimpleMessageBox(flags:number, title:string, message:string, window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.ShowWindow</strong>
</p>
<p>
<code>sdl2.ShowWindow(window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.UpdateWindowSurface</strong>
</p>
<p>
<code>sdl2.UpdateWindowSurface(window:sdl2.Window):void</code>
</p>
<p>
<strong>sdl2.UpdateWindowSurfaceRects</strong>
</p>
<p>
<code>sdl2.UpdateWindowSurfaceRects(window:sdl2.Window, rects[]:sdl2.Rect):void</code>
</p>
<p>
<strong>sdl2.VideoInit</strong>
</p>
<p>
<code>sdl2.VideoInit(driver_name:string):void</code>
</p>
<p>
<strong>sdl2.VideoQuit</strong>
</p>
<p>
<code>sdl2.VideoQuit():void</code>
</p>
<p>
<strong>sdl2.CreateRenderer</strong>
</p>
<p>
<code>sdl2.CreateRenderer(window:sdl2.Window, index:number, flags:number) {block?}</code>
</p>
<p>
<strong>sdl2.CreateSoftwareRenderer</strong>
</p>
<p>
<code>sdl2.CreateSoftwareRenderer(surface:sdl2.Surface) {block?}</code>
</p>
<p>
<strong>sdl2.CreateTexture</strong>
</p>
<p>
<code>sdl2.CreateTexture(renderer:sdl2.Renderer, format:number, access:number, w:number, h:number) {block?}</code>
</p>
<p>
<strong>sdl2.CreateTextureFromSurface</strong>
</p>
<p>
<code>sdl2.CreateTextureFromSurface(renderer:sdl2.Renderer, surface:sdl2.Surface) {block?}</code>
</p>
<p>
<strong>sdl2.DestroyRenderer</strong>
</p>
<p>
<code>sdl2.DestroyRenderer(renderer:sdl2.Renderer):void</code>
</p>
<p>
<strong>sdl2.DestroyTexture</strong>
</p>
<p>
<code>sdl2.DestroyTexture(texture:sdl2.Texture):void</code>
</p>
<p>
<strong>sdl2.GL_BindTexture</strong>
</p>
<p>
<code>sdl2.GL_BindTexture(texture:sdl2.Texture) {block?}</code>
</p>
<p>
<strong>sdl2.GL_UnbindTexture</strong>
</p>
<p>
<code>sdl2.GL_UnbindTexture(texture:sdl2.Texture):void</code>
</p>
<p>
<strong>sdl2.GetNumRenderDrivers</strong>
</p>
<p>
<code>sdl2.GetNumRenderDrivers() {block?}</code>
</p>
<p>
<strong>sdl2.GetRenderDrawBlendMode</strong>
</p>
<p>
<code>sdl2.GetRenderDrawBlendMode(renderer:sdl2.Renderer) {block?}</code>
</p>
<p>
<strong>sdl2.GetRenderDrawColor</strong>
</p>
<p>
<code>sdl2.GetRenderDrawColor(renderer:sdl2.Renderer) {block?}</code>
</p>
<p>
<strong>sdl2.GetRenderDriverInfo</strong>
</p>
<p>
<code>sdl2.GetRenderDriverInfo(index:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetRenderTarget</strong>
</p>
<p>
<code>sdl2.GetRenderTarget(renderer:sdl2.Renderer) {block?}</code>
</p>
<p>
<strong>sdl2.GetRenderer</strong>
</p>
<p>
<code>sdl2.GetRenderer(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.GetRendererInfo</strong>
</p>
<p>
<code>sdl2.GetRendererInfo(renderer:sdl2.Renderer) {block?}</code>
</p>
<p>
<strong>sdl2.GetRenderOutputSize</strong>
</p>
<p>
<code>sdl2.GetRenderOutputSize(renderer:sdl2.Renderer) {block?}</code>
</p>
<p>
<strong>sdl2.GetTextureAlphaMod</strong>
</p>
<p>
<code>sdl2.GetTextureAlphaMod(texture:sdl2.Texture) {block?}</code>
</p>
<p>
<strong>sdl2.GetTextureBlendMode</strong>
</p>
<p>
<code>sdl2.GetTextureBlendMode(texture:sdl2.Texture) {block?}</code>
</p>
<p>
<strong>sdl2.GetTextureColorMod</strong>
</p>
<p>
<code>sdl2.GetTextureColorMod(texture:sdl2.Texture) {block?}</code>
</p>
<p>
<strong>sdl2.LockTexture</strong>
</p>
<p>
<code>sdl2.LockTexture(texture:sdl2.Texture, rect:sdl2.Rect):void</code>
</p>
<p>
<strong>sdl2.QueryTexture</strong>
</p>
<p>
<code>sdl2.QueryTexture(texture:sdl2.Texture) {block?}</code>
</p>
<p>
<strong>sdl2.RenderClear</strong>
</p>
<p>
<code>sdl2.RenderClear(renderer:sdl2.Renderer):void</code>
</p>
<p>
<strong>sdl2.RenderCopy</strong>
</p>
<p>
<code>sdl2.RenderCopy(renderer:sdl2.Renderer, texture:sdl2.Texture, srcrect:sdl2.Rect:nil, dstrect:sdl2.Rect:nil):void</code>
</p>
<p>
<strong>sdl2.RenderCopyEx</strong>
</p>
<p>
<code>sdl2.RenderCopyEx(renderer:sdl2.Renderer, texture:sdl2.Texture, srcrect:sdl2.Rect:nil, dstrect:sdl2.Rect:nil, angle:number, center:sdl2.Point:nil, flip:number):void</code>
</p>
<p>
<strong>sdl2.RenderDrawLine</strong>
</p>
<p>
<code>sdl2.RenderDrawLine(renderer:sdl2.Renderer, x1:number, y1:number, x2:number, y2:number):void</code>
</p>
<p>
<strong>sdl2.RenderDrawLines</strong>
</p>
<p>
<code>sdl2.RenderDrawLines(renderer:sdl2.Renderer, points[]:sdl2.Point):void</code>
</p>
<p>
<strong>sdl2.RenderDrawPoint</strong>
</p>
<p>
<code>sdl2.RenderDrawPoint(renderer:sdl2.Renderer, x:number, y:number):void</code>
</p>
<p>
<strong>sdl2.RenderDrawPoints</strong>
</p>
<p>
<code>sdl2.RenderDrawPoints(renderer:sdl2.Renderer, points[]:sdl2.Point):void</code>
</p>
<p>
<strong>sdl2.RenderDrawRect</strong>
</p>
<p>
<code>sdl2.RenderDrawRect(renderer:sdl2.Renderer, rect:sdl2.Rect:nil):void</code>
</p>
<p>
<strong>sdl2.RenderDrawRects</strong>
</p>
<p>
<code>sdl2.RenderDrawRects(renderer:sdl2.Renderer, rects[]:sdl2.Rect):void</code>
</p>
<p>
<strong>sdl2.RenderFillRect</strong>
</p>
<p>
<code>sdl2.RenderFillRect(renderer:sdl2.Renderer, rect:sdl2.Rect:nil):void</code>
</p>
<p>
<strong>sdl2.RenderFillRects</strong>
</p>
<p>
<code>sdl2.RenderFillRects(renderer:sdl2.Renderer, rects[]:sdl2.Rect):void</code>
</p>
<p>
<strong>sdl2.RenderGetClipRect</strong>
</p>
<p>
<code>sdl2.RenderGetClipRect(renderer:sdl2.Renderer) {block?}</code>
</p>
<p>
<strong>sdl2.RenderGetLogicalSize</strong>
</p>
<p>
<code>sdl2.RenderGetLogicalSize(renderer:sdl2.Renderer) {block?}</code>
</p>
<p>
<strong>sdl2.RenderGetScale</strong>
</p>
<p>
<code>sdl2.RenderGetScale(renderer:sdl2.Renderer) {block?}</code>
</p>
<p>
<strong>sdl2.RenderGetViewport</strong>
</p>
<p>
<code>sdl2.RenderGetViewport(renderer:sdl2.Renderer) {block?}</code>
</p>
<p>
<strong>sdl2.RenderIsClipEnabled</strong>
</p>
<p>
<code>sdl2.RenderIsClipEnabled(renderer:sdl2.Renderer)</code>
</p>
<p>
<strong>sdl2.RenderPresent</strong>
</p>
<p>
<code>sdl2.RenderPresent(renderer:sdl2.Renderer):void</code>
</p>
<p>
<strong>sdl2.RenderReadPixels</strong>
</p>
<p>
<code>sdl2.RenderReadPixels(renderer:sdl2.Renderer, rect:sdl2.Rect:nil, format:symbol) {block?}</code>
</p>
<p>
<strong>sdl2.RenderSetClipRect</strong>
</p>
<p>
<code>sdl2.RenderSetClipRect(renderer:sdl2.Renderer, rect:sdl2.Rect:nil):void</code>
</p>
<p>
<strong>sdl2.RenderSetLogicalSize</strong>
</p>
<p>
<code>sdl2.RenderSetLogicalSize(renderer:sdl2.Renderer, w:number, h:number):void</code>
</p>
<p>
<strong>sdl2.RenderSetScale</strong>
</p>
<p>
<code>sdl2.RenderSetScale(renderer:sdl2.Renderer, scaleX:number, scaleY:number):void</code>
</p>
<p>
<strong>sdl2.RenderSetViewport</strong>
</p>
<p>
<code>sdl2.RenderSetViewport(renderer:sdl2.Renderer, rect:sdl2.Rect:nil):void</code>
</p>
<p>
<strong>sdl2.RenderTargetSupported</strong>
</p>
<p>
<code>sdl2.RenderTargetSupported(renderer:sdl2.Renderer) {block?}</code>
</p>
<p>
<strong>sdl2.SetRenderDrawBlendMode</strong>
</p>
<p>
<code>sdl2.SetRenderDrawBlendMode(renderer:sdl2.Renderer, blendMode:number):void</code>
</p>
<p>
<strong>sdl2.SetRenderDrawColor</strong>
</p>
<p>
<code>sdl2.SetRenderDrawColor(renderer:sdl2.Renderer, r:number, g:number, b:number, a:number):void</code>
</p>
<p>
<strong>sdl2.SetRenderTarget</strong>
</p>
<p>
<code>sdl2.SetRenderTarget(renderer:sdl2.Renderer, texture:sdl2.Texture:nil):void</code>
</p>
<p>
<strong>sdl2.SetTextureAlphaMod</strong>
</p>
<p>
<code>sdl2.SetTextureAlphaMod(texture:sdl2.Texture, alpha:number):void</code>
</p>
<p>
<strong>sdl2.SetTextureBlendMode</strong>
</p>
<p>
<code>sdl2.SetTextureBlendMode(texture:sdl2.Texture, blendMode:number):void</code>
</p>
<p>
<strong>sdl2.SetTextureColorMod</strong>
</p>
<p>
<code>sdl2.SetTextureColorMod(texture:sdl2.Texture, r:number, g:number, b:number):void</code>
</p>
<p>
<strong>sdl2.UnlockTexture</strong>
</p>
<p>
<code>sdl2.UnlockTexture(texture:sdl2.Texture):void</code>
</p>
<p>
<strong>sdl2.UpdateTexture</strong>
</p>
<p>
<code>sdl2.UpdateTexture(texture:sdl2.Texture, rect:sdl2.Rect:nil, pitch:number):void</code>
</p>
<p>
<strong>sdl2.UpdateYUVTexture</strong>
</p>
<p>
<code>sdl2.UpdateYUVTexture():void</code>
</p>
<p>
<strong>sdl2.AllocFormat</strong>
</p>
<p>
<code>sdl2.AllocFormat(pixel_format:number) {block?}</code>
</p>
<p>
<strong>sdl2.AllocPalette</strong>
</p>
<p>
<code>sdl2.AllocPalette(ncolors:number) {block?}</code>
</p>
<p>
<strong>sdl2.CalculateGammaRamp</strong>
</p>
<p>
<code>sdl2.CalculateGammaRamp(gamma:number) {block?}</code>
</p>
<p>
<strong>sdl2.FreeFormat</strong>
</p>
<p>
<code>sdl2.FreeFormat(format:sdl2.PixelFormat):void</code>
</p>
<p>
<strong>sdl2.FreePalette</strong>
</p>
<p>
<code>sdl2.FreePalette(palette:sdl2.Palette):void</code>
</p>
<p>
<strong>sdl2.GetPixelFormatName</strong>
</p>
<p>
<code>sdl2.GetPixelFormatName(format:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetRGB</strong>
</p>
<p>
<code>sdl2.GetRGB(pixel:number, format:sdl2.PixelFormat) {block?}</code>
</p>
<p>
<strong>sdl2.GetRGBA</strong>
</p>
<p>
<code>sdl2.GetRGBA(pixel:number, format:sdl2.PixelFormat) {block?}</code>
</p>
<p>
<strong>sdl2.MapRGB</strong>
</p>
<p>
<code>sdl2.MapRGB(format:sdl2.PixelFormat, r:number, g:number, b:number) {block?}</code>
</p>
<p>
<strong>sdl2.MapRGBA</strong>
</p>
<p>
<code>sdl2.MapRGBA(format:sdl2.PixelFormat, r:number, g:number, b:number, a:number) {block?}</code>
</p>
<p>
<strong>sdl2.MasksToPixelFormatEnum</strong>
</p>
<p>
<code>sdl2.MasksToPixelFormatEnum(bpp:number, Rmask:number, Gmask:number, Bmask:number, Amask:number) {block?}</code>
</p>
<p>
<strong>sdl2.PixelFormatEnumToMasks</strong>
</p>
<p>
<code>sdl2.PixelFormatEnumToMasks(format:number) {block?}</code>
</p>
<p>
<strong>sdl2.SetPaletteColors</strong>
</p>
<p>
<code>sdl2.SetPaletteColors(palette:sdl2.Palette, colors[]:sdl2.Color, firstcolor:number, ncolors:number):void</code>
</p>
<p>
<strong>sdl2.SetPixelFormatPalette</strong>
</p>
<p>
<code>sdl2.SetPixelFormatPalette(format:sdl2.PixelFormat, palette:sdl2.Palette):void</code>
</p>
<p>
<strong>sdl2.EnclosePoints</strong>
</p>
<p>
<code>sdl2.EnclosePoints(points[]:sdl2.Point, clip:sdl2.Rect) {block?}</code>
</p>
<p>
<strong>sdl2.HasIntersection</strong>
</p>
<p>
<code>sdl2.HasIntersection(A:sdl2.Rect, B:sdl2.Rect) {block?}</code>
</p>
<p>
<strong>sdl2.IntersectRect</strong>
</p>
<p>
<code>sdl2.IntersectRect(A:sdl2.Rect, B:sdl2.Rect) {block?}</code>
</p>
<p>
<strong>sdl2.IntersectRectAndLine</strong>
</p>
<p>
<code>sdl2.IntersectRectAndLine(rect:sdl2.Rect, X1:number, Y1:number, X2:number, Y2:number)</code>
</p>
<p>
<strong>sdl2.PointInRect</strong>
</p>
<p>
<code>sdl2.PointInRect(p:sdl2.Point, r:sdl2.Rect)</code>
</p>
<p>
<strong>sdl2.RectEmpty</strong>
</p>
<p>
<code>sdl2.RectEmpty(r:sdl2.Rect) {block?}</code>
</p>
<p>
<strong>sdl2.RectEquals</strong>
</p>
<p>
<code>sdl2.RectEquals(a:sdl2.Rect, b:sdl2.Rect) {block?}</code>
</p>
<p>
<strong>sdl2.UnionRect</strong>
</p>
<p>
<code>sdl2.UnionRect(A:sdl2.Rect, B:sdl2.Rect) {block?}</code>
</p>
<p>
<strong>sdl2.BlitScaled</strong>
</p>
<p>
<code>sdl2.BlitScaled(src:sdl2.Surface, srcrect:sdl2.Rect:nil, dst:sdl2.Surface, dstrect:sdl2.Rect:nil):void</code>
</p>
<p>
<strong>sdl2.BlitSurface</strong>
</p>
<p>
<code>sdl2.BlitSurface(src:sdl2.Surface, srcrect:sdl2.Rect:nil, dst:sdl2.Surface, dstrect:sdl2.Rect:nil):void</code>
</p>
<p>
<strong>sdl2.ConvertPixels</strong>
</p>
<p>
<code>sdl2.ConvertPixels(width:number, height:number, src_format:number, dst_format:number):void</code>
</p>
<p>
<strong>sdl2.ConvertSurface</strong>
</p>
<p>
<code>sdl2.ConvertSurface(src:sdl2.Surface, fmt:sdl2.PixelFormat, flags:number) {block?}</code>
</p>
<p>
<strong>sdl2.ConvertSurfaceFormat</strong>
</p>
<p>
<code>sdl2.ConvertSurfaceFormat(src:sdl2.Surface, pixel_format:number, flags:number) {block?}</code>
</p>
<p>
<strong>sdl2.CreateRGBSurface</strong>
</p>
<p>
<code>sdl2.CreateRGBSurface(flags:number, width:number, height:number, depth:number, Rmask:number, Gmask:number, Bmask:number, Amask:number) {block?}</code>
</p>
<p>
<strong>sdl2.CreateRGBSurfaceFrom</strong>
</p>
<p>
<code>sdl2.CreateRGBSurfaceFrom(pixels, width:number, height:number, depth:number, pitch:number, Rmask:number, Gmask:number, Bmask:number, Amask:number) {block?}</code>
</p>
<p>
<strong>sdl2.CreateRGBSurfaceFromImage</strong>
</p>
<p>
<code>sdl2.CreateRGBSurfaceFromImage(image:image) {block?}</code>
</p>
<p>
<strong>sdl2.FillRect</strong>
</p>
<p>
<code>sdl2.FillRect(dst:sdl2.Surface, rect:sdl2.Rect:nil, color:number):void</code>
</p>
<p>
<strong>sdl2.FillRects</strong>
</p>
<p>
<code>sdl2.FillRects(dst:sdl2.Surface, rects[]:sdl2.Rect, color:number):void</code>
</p>
<p>
<strong>sdl2.FreeSurface</strong>
</p>
<p>
<code>sdl2.FreeSurface(surface:sdl2.Surface):void</code>
</p>
<p>
<strong>sdl2.GetClipRect</strong>
</p>
<p>
<code>sdl2.GetClipRect(surface:sdl2.Surface) {block?}</code>
</p>
<p>
<strong>sdl2.GetColorKey</strong>
</p>
<p>
<code>sdl2.GetColorKey(surface:sdl2.Surface) {block?}</code>
</p>
<p>
<strong>sdl2.GetSurfaceAlphaMod</strong>
</p>
<p>
<code>sdl2.GetSurfaceAlphaMod(surface:sdl2.Surface) {block?}</code>
</p>
<p>
<strong>sdl2.GetSurfaceBlendMode</strong>
</p>
<p>
<code>sdl2.GetSurfaceBlendMode(surface:sdl2.Surface) {block?}</code>
</p>
<p>
<strong>sdl2.GetSurfaceColorMod</strong>
</p>
<p>
<code>sdl2.GetSurfaceColorMod(surface:sdl2.Surface) {block?}</code>
</p>
<p>
<strong>sdl2.LoadBMP</strong>
</p>
<p>
<code>sdl2.LoadBMP(src:stream) {block?}</code>
</p>
<p>
<strong>sdl2.LoadBMP_RW</strong>
</p>
<p>
<code>sdl2.LoadBMP_RW():void</code>
</p>
<p>
<strong>sdl2.LockSurface</strong>
</p>
<p>
<code>sdl2.LockSurface(surface:sdl2.Surface):void</code>
</p>
<p>
<strong>sdl2.LowerBlit</strong>
</p>
<p>
<code>sdl2.LowerBlit(src:sdl2.Surface, srcrect:sdl2.Rect:nil, dst:sdl2.Surface, dstrect:sdl2.Rect:nil):void</code>
</p>
<p>
<strong>sdl2.LowerBlitScaled</strong>
</p>
<p>
<code>sdl2.LowerBlitScaled(src:sdl2.Surface, srcrect:sdl2.Rect:nil, dst:sdl2.Surface, dstrect:sdl2.Rect:nil):void</code>
</p>
<p>
<strong>sdl2.MUSTLOCK</strong>
</p>
<p>
<code>sdl2.MUSTLOCK(surface:sdl2.Surface) {block?}</code>
</p>
<p>
<strong>sdl2.SaveBMP</strong>
</p>
<p>
<code>sdl2.SaveBMP(surface:sdl2.Surface, dst:stream) {block?}</code>
</p>
<p>
<strong>sdl2.SaveBMP_RW</strong>
</p>
<p>
<code>sdl2.SaveBMP_RW():void</code>
</p>
<p>
<strong>sdl2.SetClipRect</strong>
</p>
<p>
<code>sdl2.SetClipRect(surface:sdl2.Surface, rect:sdl2.Rect) {block?}</code>
</p>
<p>
<strong>sdl2.SetColorKey</strong>
</p>
<p>
<code>sdl2.SetColorKey(surface:sdl2.Surface, flag:number, key:number):void</code>
</p>
<p>
<strong>sdl2.SetSurfaceAlphaMod</strong>
</p>
<p>
<code>sdl2.SetSurfaceAlphaMod(surface:sdl2.Surface, alpha:number):void</code>
</p>
<p>
<strong>sdl2.SetSurfaceBlendMode</strong>
</p>
<p>
<code>sdl2.SetSurfaceBlendMode(surface:sdl2.Surface, blendMode:number):void</code>
</p>
<p>
<strong>sdl2.SetSurfaceColorMod</strong>
</p>
<p>
<code>sdl2.SetSurfaceColorMod(surface:sdl2.Surface, r:number, g:number, b:number):void</code>
</p>
<p>
<strong>sdl2.SetSurfacePalette</strong>
</p>
<p>
<code>sdl2.SetSurfacePalette(surface:sdl2.Surface, palette:sdl2.Palette):void</code>
</p>
<p>
<strong>sdl2.SetSurfaceRLE</strong>
</p>
<p>
<code>sdl2.SetSurfaceRLE(surface:sdl2.Surface, flag:number):void</code>
</p>
<p>
<strong>sdl2.UnlockSurface</strong>
</p>
<p>
<code>sdl2.UnlockSurface(surface:sdl2.Surface):void</code>
</p>
<p>
<strong>sdl2.GetClipboardText</strong>
</p>
<p>
<code>sdl2.GetClipboardText() {block?}</code>
</p>
<p>
<strong>sdl2.HasClipboardText</strong>
</p>
<p>
<code>sdl2.HasClipboardText() {block?}</code>
</p>
<p>
<strong>sdl2.SetClipboardText</strong>
</p>
<p>
<code>sdl2.SetClipboardText(text:string):void</code>
</p>
<p>
<strong>sdl2.AddEventWatch</strong>
</p>
<p>
<code>sdl2.AddEventWatch():void</code>
</p>
<p>
<strong>sdl2.DelEventWatch</strong>
</p>
<p>
<code>sdl2.DelEventWatch():void</code>
</p>
<p>
<strong>sdl2.EventState</strong>
</p>
<p>
<code>sdl2.EventState(type:number, state:number) {block?}</code>
</p>
<p>
<strong>sdl2.FilterEvents</strong>
</p>
<p>
<code>sdl2.FilterEvents():void</code>
</p>
<p>
<strong>sdl2.FlushEvent</strong>
</p>
<p>
<code>sdl2.FlushEvent(type:number):void</code>
</p>
<p>
<strong>sdl2.FlushEvents</strong>
</p>
<p>
<code>sdl2.FlushEvents(minType:number, maxType:number):void</code>
</p>
<p>
<strong>sdl2.GetEventFilter</strong>
</p>
<p>
<code>sdl2.GetEventFilter():void</code>
</p>
<p>
<strong>sdl2.GetNumTouchDevices</strong>
</p>
<p>
<code>sdl2.GetNumTouchDevices() {block?}</code>
</p>
<p>
<strong>sdl2.GetNumTouchFingers</strong>
</p>
<p>
<code>sdl2.GetNumTouchFingers(touchId:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetTouchDevice</strong>
</p>
<p>
<code>sdl2.GetTouchDevice(index:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetTouchFinger</strong>
</p>
<p>
<code>sdl2.GetTouchFinger(touchId:number, index:number) {block?}</code>
</p>
<p>
<strong>sdl2.HasEvent</strong>
</p>
<p>
<code>sdl2.HasEvent(type:number) {block?}</code>
</p>
<p>
<strong>sdl2.HasEvents</strong>
</p>
<p>
<code>sdl2.HasEvents(minType:number, maxType:number) {block?}</code>
</p>
<p>
<strong>sdl2.LoadDollarTemplates</strong>
</p>
<p>
<code>sdl2.LoadDollarTemplates(touchId:number, src:stream) {block?}</code>
</p>
<p>
<strong>sdl2.AddEvents</strong>
</p>
<p>
<code>sdl2.AddEvents(events[]:sdl2.Event) {block?}</code>
</p>
<p>
<strong>sdl2.PeekEvents</strong>
</p>
<p>
<code>sdl2.PeekEvents(numevents:number, minType:number, maxType:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetEvents</strong>
</p>
<p>
<code>sdl2.GetEvents(numevents:number, minType:number, maxType:number) {block?}</code>
</p>
<p>
<strong>sdl2.PollEvent</strong>
</p>
<p>
<code>sdl2.PollEvent() {block?}</code>
</p>
<p>
<strong>sdl2.PumpEvents</strong>
</p>
<p>
<code>sdl2.PumpEvents():void</code>
</p>
<p>
<strong>sdl2.PushEvent</strong>
</p>
<p>
<code>sdl2.PushEvent(event:sdl2.Event) {block?}</code>
</p>
<p>
<strong>sdl2.QuitRequested</strong>
</p>
<p>
<code>sdl2.QuitRequested() {block?}</code>
</p>
<p>
<strong>sdl2.RecordGesture</strong>
</p>
<p>
<code>sdl2.RecordGesture(touchId:number) {block?}</code>
</p>
<p>
<strong>sdl2.RegisterEvents</strong>
</p>
<p>
<code>sdl2.RegisterEvents(numevents:number) {block?}</code>
</p>
<p>
<strong>sdl2.SaveAllDollarTemplates</strong>
</p>
<p>
<code>sdl2.SaveAllDollarTemplates(dst:stream) {block?}</code>
</p>
<p>
<strong>sdl2.SaveDollarTemplate</strong>
</p>
<p>
<code>sdl2.SaveDollarTemplate(gestureId:number, dst:stream):void</code>
</p>
<p>
<strong>sdl2.SetEventFilter</strong>
</p>
<p>
<code>sdl2.SetEventFilter():void</code>
</p>
<p>
<strong>sdl2.WaitEvent</strong>
</p>
<p>
<code>sdl2.WaitEvent() {block?}</code>
</p>
<p>
<strong>sdl2.WaitEventTimeout</strong>
</p>
<p>
<code>sdl2.WaitEventTimeout(timeout:number) {block?}</code>
</p>
<p>
<strong>sdl2.CheckKeyboardState</strong>
</p>
<p>
<code>sdl2.CheckKeyboardState(scancode:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetKeyFromName</strong>
</p>
<p>
<code>sdl2.GetKeyFromName(name:string) {block?}</code>
</p>
<p>
<strong>sdl2.GetKeyFromScancode</strong>
</p>
<p>
<code>sdl2.GetKeyFromScancode(scancode:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetKeyName</strong>
</p>
<p>
<code>sdl2.GetKeyName(key:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetKeyboardFocus</strong>
</p>
<p>
<code>sdl2.GetKeyboardFocus() {block?}</code>
</p>
<p>
<strong>sdl2.GetKeyboardState</strong>
</p>
<p>
<code>sdl2.GetKeyboardState() {block?}</code>
</p>
<p>
<strong>sdl2.GetModState</strong>
</p>
<p>
<code>sdl2.GetModState() {block?}</code>
</p>
<p>
<strong>sdl2.GetScancodeFromKey</strong>
</p>
<p>
<code>sdl2.GetScancodeFromKey(key:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetScancodeFromName</strong>
</p>
<p>
<code>sdl2.GetScancodeFromName(name:string) {block?}</code>
</p>
<p>
<strong>sdl2.GetScancodeName</strong>
</p>
<p>
<code>sdl2.GetScancodeName(scancode:number) {block?}</code>
</p>
<p>
<strong>sdl2.HasScreenKeyboardSupport</strong>
</p>
<p>
<code>sdl2.HasScreenKeyboardSupport() {block?}</code>
</p>
<p>
<strong>sdl2.IsScreenKeyboardShown</strong>
</p>
<p>
<code>sdl2.IsScreenKeyboardShown(window:sdl2.Window) {block?}</code>
</p>
<p>
<strong>sdl2.IsTextInputActive</strong>
</p>
<p>
<code>sdl2.IsTextInputActive() {block?}</code>
</p>
<p>
<strong>sdl2.SetModState</strong>
</p>
<p>
<code>sdl2.SetModState(modstate:number):void</code>
</p>
<p>
<strong>sdl2.SetTextInputRect</strong>
</p>
<p>
<code>sdl2.SetTextInputRect(rect:sdl2.Rect):void</code>
</p>
<p>
<strong>sdl2.StartTextInput</strong>
</p>
<p>
<code>sdl2.StartTextInput():void</code>
</p>
<p>
<strong>sdl2.StopTextInput</strong>
</p>
<p>
<code>sdl2.StopTextInput():void</code>
</p>
<p>
<strong>sdl2.CaptureMouse</strong>
</p>
<p>
<code>sdl2.CaptureMouse(enalbed:boolean):void</code>
</p>
<p>
<strong>sdl2.CreateColorCursor</strong>
</p>
<p>
<code>sdl2.CreateColorCursor(surface:sdl2.Surface, hot_x:number, hot_y:number) {block?}</code>
</p>
<p>
<strong>sdl2.CreateCursor</strong>
</p>
<p>
<code>sdl2.CreateCursor(data:array@uchar:nomap, mask:array@uchar:nomap, w:number, h:number, hot_x:number, hot_y:number) {block?}</code>
</p>
<p>
<strong>sdl2.CreateSystemCursor</strong>
</p>
<p>
<code>sdl2.CreateSystemCursor(id:number) {block?}</code>
</p>
<p>
<strong>sdl2.FreeCursor</strong>
</p>
<p>
<code>sdl2.FreeCursor(cursor:sdl2.Cursor):void</code>
</p>
<p>
<strong>sdl2.GetCursor</strong>
</p>
<p>
<code>sdl2.GetCursor() {block?}</code>
</p>
<p>
<strong>sdl2.GetDefaultCursor</strong>
</p>
<p>
<code>sdl2.GetDefaultCursor() {block?}</code>
</p>
<p>
<strong>sdl2.GetGlobalMouseState</strong>
</p>
<p>
<code>sdl2.GetGlobalMouseState():void</code>
</p>
<p>
<strong>sdl2.GetMouseFocus</strong>
</p>
<p>
<code>sdl2.GetMouseFocus() {block?}</code>
</p>
<p>
<strong>sdl2.GetMouseState</strong>
</p>
<p>
<code>sdl2.GetMouseState() {block?}</code>
</p>
<p>
<strong>sdl2.GetRelativeMouseMode</strong>
</p>
<p>
<code>sdl2.GetRelativeMouseMode() {block?}</code>
</p>
<p>
<strong>sdl2.GetRelativeMouseState</strong>
</p>
<p>
<code>sdl2.GetRelativeMouseState() {block?}</code>
</p>
<p>
<strong>sdl2.SetCursor</strong>
</p>
<p>
<code>sdl2.SetCursor(cursor:sdl2.Cursor):void</code>
</p>
<p>
<strong>sdl2.SetRelativeMouseMode</strong>
</p>
<p>
<code>sdl2.SetRelativeMouseMode(enabled:boolean):void</code>
</p>
<p>
<strong>sdl2.ShowCursor</strong>
</p>
<p>
<code>sdl2.ShowCursor(toggle:number):void</code>
</p>
<p>
<strong>sdl2.WarpMouseGlobal</strong>
</p>
<p>
<code>sdl2.WarpMouseGlobal(x:number, y:number):void</code>
</p>
<p>
<strong>sdl2.WarpMouseInWindow</strong>
</p>
<p>
<code>sdl2.WarpMouseInWindow(window:sdl2.Window, x:number, y:number):void</code>
</p>
<p>
<strong>sdl2.JoystickClose</strong>
</p>
<p>
<code>sdl2.JoystickClose(joystick:sdl2.Joystick):void</code>
</p>
<p>
<strong>sdl2.JoystickEventState</strong>
</p>
<p>
<code>sdl2.JoystickEventState(state:number) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickGetAttached</strong>
</p>
<p>
<code>sdl2.JoystickGetAttached(joystick:sdl2.Joystick) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickGetAxis</strong>
</p>
<p>
<code>sdl2.JoystickGetAxis(joystick:sdl2.Joystick, axis:number) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickGetBall</strong>
</p>
<p>
<code>sdl2.JoystickGetBall(joystick:sdl2.Joystick, ball:number) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickGetButton</strong>
</p>
<p>
<code>sdl2.JoystickGetButton(joystick:sdl2.Joystick, button:number) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickGetDeviceGUID</strong>
</p>
<p>
<code>sdl2.JoystickGetDeviceGUID(device_index:number) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickGetGUID</strong>
</p>
<p>
<code>sdl2.JoystickGetGUID(joystick:sdl2.Joystick) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickGetGUIDFromString</strong>
</p>
<p>
<code>sdl2.JoystickGetGUIDFromString(pchGUID:string) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickGetGUIDString</strong>
</p>
<p>
<code>sdl2.JoystickGetGUIDString(guid:sdl2.JoystickGUID) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickGetHat</strong>
</p>
<p>
<code>sdl2.JoystickGetHat(joystick:sdl2.Joystick, hat:number) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickInstanceID</strong>
</p>
<p>
<code>sdl2.JoystickInstanceID(joystick:sdl2.Joystick) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickName</strong>
</p>
<p>
<code>sdl2.JoystickName(joystick:sdl2.Joystick) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickNameForIndex</strong>
</p>
<p>
<code>sdl2.JoystickNameForIndex(device_index:number) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickNumAxes</strong>
</p>
<p>
<code>sdl2.JoystickNumAxes(joystick:sdl2.Joystick) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickNumBalls</strong>
</p>
<p>
<code>sdl2.JoystickNumBalls(joystick:sdl2.Joystick) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickNumButtons</strong>
</p>
<p>
<code>sdl2.JoystickNumButtons(joystick:sdl2.Joystick) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickNumHats</strong>
</p>
<p>
<code>sdl2.JoystickNumHats(joystick:sdl2.Joystick) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickOpen</strong>
</p>
<p>
<code>sdl2.JoystickOpen(device_index:number) {block?}</code>
</p>
<p>
<strong>sdl2.JoystickUpdate</strong>
</p>
<p>
<code>sdl2.JoystickUpdate():void</code>
</p>
<p>
<strong>sdl2.NumJoysticks</strong>
</p>
<p>
<code>sdl2.NumJoysticks() {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerAddMapping</strong>
</p>
<p>
<code>sdl2.GameControllerAddMapping(mappingString:string) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerAddMappingsFromFile</strong>
</p>
<p>
<code>sdl2.GameControllerAddMappingsFromFile(file:stream) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerAddMappingsFromRW</strong>
</p>
<p>
<code>sdl2.GameControllerAddMappingsFromRW():void</code>
</p>
<p>
<strong>sdl2.GameControllerClose</strong>
</p>
<p>
<code>sdl2.GameControllerClose(gamecontroller:sdl2.GameController):void</code>
</p>
<p>
<strong>sdl2.GameControllerEventState</strong>
</p>
<p>
<code>sdl2.GameControllerEventState(state:number) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerGetAttached</strong>
</p>
<p>
<code>sdl2.GameControllerGetAttached(gamecontroller:sdl2.GameController) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerGetAxis</strong>
</p>
<p>
<code>sdl2.GameControllerGetAxis(gamecontroller:sdl2.GameController, axis:number) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerGetAxisFromString</strong>
</p>
<p>
<code>sdl2.GameControllerGetAxisFromString(pchString:string) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerGetBindForAxis</strong>
</p>
<p>
<code>sdl2.GameControllerGetBindForAxis(gamecontroller:sdl2.GameController, axis:number) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerGetBindForButton</strong>
</p>
<p>
<code>sdl2.GameControllerGetBindForButton(gamecontroller:sdl2.GameController, button:number) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerGetButton</strong>
</p>
<p>
<code>sdl2.GameControllerGetButton(gamecontroller:sdl2.GameController, button:number) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerGetButtonFromString</strong>
</p>
<p>
<code>sdl2.GameControllerGetButtonFromString(pchString:string) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerGetJoystick</strong>
</p>
<p>
<code>sdl2.GameControllerGetJoystick(gamecontroller:sdl2.GameController) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerGetStringForAxis</strong>
</p>
<p>
<code>sdl2.GameControllerGetStringForAxis(axis:number) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerGetStringForButton</strong>
</p>
<p>
<code>sdl2.GameControllerGetStringForButton(button:number) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerMapping</strong>
</p>
<p>
<code>sdl2.GameControllerMapping(gamecontroller:sdl2.GameController) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerMappingForGUID</strong>
</p>
<p>
<code>sdl2.GameControllerMappingForGUID(guid:sdl2.JoystickGUID) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerName</strong>
</p>
<p>
<code>sdl2.GameControllerName(gamecontroller:sdl2.GameController) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerNameForIndex</strong>
</p>
<p>
<code>sdl2.GameControllerNameForIndex(joystick_index:number) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerOpen</strong>
</p>
<p>
<code>sdl2.GameControllerOpen(joystick_index:number) {block?}</code>
</p>
<p>
<strong>sdl2.GameControllerUpdate</strong>
</p>
<p>
<code>sdl2.GameControllerUpdate():void</code>
</p>
<p>
<strong>sdl2.IsGameController</strong>
</p>
<p>
<code>sdl2.IsGameController(joystick_index:number) {block?}</code>
</p>
<p>
<strong>sdl2.HapticClose</strong>
</p>
<p>
<code>sdl2.HapticClose(haptic:sdl2.Haptic):void</code>
</p>
<p>
<strong>sdl2.HapticDestroyEffect</strong>
</p>
<p>
<code>sdl2.HapticDestroyEffect(haptic:sdl2.Haptic, effect:number):void</code>
</p>
<p>
<strong>sdl2.HapticEffectSupported</strong>
</p>
<p>
<code>sdl2.HapticEffectSupported(haptic:sdl2.Haptic, effect:sdl2.HapticEffect) {block?}</code>
</p>
<p>
<strong>sdl2.HapticGetEffectStatus</strong>
</p>
<p>
<code>sdl2.HapticGetEffectStatus(haptic:sdl2.Haptic, effect:number) {block?}</code>
</p>
<p>
<strong>sdl2.HapticIndex</strong>
</p>
<p>
<code>sdl2.HapticIndex(haptic:sdl2.Haptic) {block?}</code>
</p>
<p>
<strong>sdl2.HapticName</strong>
</p>
<p>
<code>sdl2.HapticName(device_index:number) {block?}</code>
</p>
<p>
<strong>sdl2.HapticNewEffect</strong>
</p>
<p>
<code>sdl2.HapticNewEffect(haptic:sdl2.Haptic, effect:sdl2.HapticEffect) {block?}</code>
</p>
<p>
<strong>sdl2.HapticNumAxes</strong>
</p>
<p>
<code>sdl2.HapticNumAxes(haptic:sdl2.Haptic) {block?}</code>
</p>
<p>
<strong>sdl2.HapticNumEffects</strong>
</p>
<p>
<code>sdl2.HapticNumEffects(haptic:sdl2.Haptic) {block?}</code>
</p>
<p>
<strong>sdl2.HapticNumEffectsPlaying</strong>
</p>
<p>
<code>sdl2.HapticNumEffectsPlaying(haptic:sdl2.Haptic) {block?}</code>
</p>
<p>
<strong>sdl2.HapticOpen</strong>
</p>
<p>
<code>sdl2.HapticOpen(device_index:number) {block?}</code>
</p>
<p>
<strong>sdl2.HapticOpenFromJoystick</strong>
</p>
<p>
<code>sdl2.HapticOpenFromJoystick(joystick:sdl2.Joystick) {block?}</code>
</p>
<p>
<strong>sdl2.HapticOpenFromMouse</strong>
</p>
<p>
<code>sdl2.HapticOpenFromMouse() {block?}</code>
</p>
<p>
<strong>sdl2.HapticOpened</strong>
</p>
<p>
<code>sdl2.HapticOpened(device_index:number) {block?}</code>
</p>
<p>
<strong>sdl2.HapticPause</strong>
</p>
<p>
<code>sdl2.HapticPause(haptic:sdl2.Haptic):void</code>
</p>
<p>
<strong>sdl2.HapticQuery</strong>
</p>
<p>
<code>sdl2.HapticQuery(haptic:sdl2.Haptic) {block?}</code>
</p>
<p>
<strong>sdl2.HapticRumbleInit</strong>
</p>
<p>
<code>sdl2.HapticRumbleInit(haptic:sdl2.Haptic):void</code>
</p>
<p>
<strong>sdl2.HapticRumblePlay</strong>
</p>
<p>
<code>sdl2.HapticRumblePlay(haptic:sdl2.Haptic, strength:number, length:number):void</code>
</p>
<p>
<strong>sdl2.HapticRumbleStop</strong>
</p>
<p>
<code>sdl2.HapticRumbleStop(haptic:sdl2.Haptic):void</code>
</p>
<p>
<strong>sdl2.HapticRumbleSupported</strong>
</p>
<p>
<code>sdl2.HapticRumbleSupported(haptic:sdl2.Haptic) {block?}</code>
</p>
<p>
<strong>sdl2.HapticRunEffect</strong>
</p>
<p>
<code>sdl2.HapticRunEffect(haptic:sdl2.Haptic, effect:number, iterations:number):void</code>
</p>
<p>
<strong>sdl2.HapticSetAutocenter</strong>
</p>
<p>
<code>sdl2.HapticSetAutocenter(haptic:sdl2.Haptic, autocenter:number):void</code>
</p>
<p>
<strong>sdl2.HapticSetGain</strong>
</p>
<p>
<code>sdl2.HapticSetGain(haptic:sdl2.Haptic, gain:number):void</code>
</p>
<p>
<strong>sdl2.HapticStopAll</strong>
</p>
<p>
<code>sdl2.HapticStopAll(haptic:sdl2.Haptic):void</code>
</p>
<p>
<strong>sdl2.HapticStopEffect</strong>
</p>
<p>
<code>sdl2.HapticStopEffect(haptic:sdl2.Haptic, effect:number):void</code>
</p>
<p>
<strong>sdl2.HapticUnpause</strong>
</p>
<p>
<code>sdl2.HapticUnpause(haptic:sdl2.Haptic):void</code>
</p>
<p>
<strong>sdl2.HapticUpdateEffect</strong>
</p>
<p>
<code>sdl2.HapticUpdateEffect(haptic:sdl2.Haptic, effect:number, data:sdl2.HapticEffect):void</code>
</p>
<p>
<strong>sdl2.JoystickIsHaptic</strong>
</p>
<p>
<code>sdl2.JoystickIsHaptic(joystick:sdl2.Joystick) {block?}</code>
</p>
<p>
<strong>sdl2.MouseIsHaptic</strong>
</p>
<p>
<code>sdl2.MouseIsHaptic() {block?}</code>
</p>
<p>
<strong>sdl2.NumHaptics</strong>
</p>
<p>
<code>sdl2.NumHaptics() {block?}</code>
</p>
<p>
<strong>sdl2.AudioInit</strong>
</p>
<p>
<code>sdl2.AudioInit(driver_name:string):void</code>
</p>
<p>
<strong>sdl2.AudioQuit</strong>
</p>
<p>
<code>sdl2.AudioQuit():void</code>
</p>
<p>
<strong>sdl2.BuildAudioCVT</strong>
</p>
<p>
<code>sdl2.BuildAudioCVT(cvt:sdl2.AudioCVT, src_format:number, src_channels:number, src_rate:number, dst_format:number, dst_channels:number, dst_rate:number) {block?}</code>
</p>
<p>
<strong>sdl2.ClearQueuedAudio</strong>
</p>
<p>
<code>sdl2.ClearQueuedAudio(dev:number):void</code>
</p>
<p>
<strong>sdl2.CloseAudio</strong>
</p>
<p>
<code>sdl2.CloseAudio():void</code>
</p>
<p>
<strong>sdl2.CloseAudioDevice</strong>
</p>
<p>
<code>sdl2.CloseAudioDevice(dev:number):void</code>
</p>
<p>
<strong>sdl2.ConvertAudio</strong>
</p>
<p>
<code>sdl2.ConvertAudio(cvt:sdl2.AudioCVT):void</code>
</p>
<p>
<strong>sdl2.FreeWAV</strong>
</p>
<p>
<code>sdl2.FreeWAV(wav:sdl2.Wav):void</code>
</p>
<p>
<strong>sdl2.GetAudioDeviceName</strong>
</p>
<p>
<code>sdl2.GetAudioDeviceName(index:number, iscapture:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetAudioDeviceStatus</strong>
</p>
<p>
<code>sdl2.GetAudioDeviceStatus(dev:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetAudioDriver</strong>
</p>
<p>
<code>sdl2.GetAudioDriver(index:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetAudioStatus</strong>
</p>
<p>
<code>sdl2.GetAudioStatus() {block?}</code>
</p>
<p>
<strong>sdl2.GetCurrentAudioDriver</strong>
</p>
<p>
<code>sdl2.GetCurrentAudioDriver() {block?}</code>
</p>
<p>
<strong>sdl2.GetNumAudioDevices</strong>
</p>
<p>
<code>sdl2.GetNumAudioDevices(iscapture:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetNumAudioDrivers</strong>
</p>
<p>
<code>sdl2.GetNumAudioDrivers() {block?}</code>
</p>
<p>
<strong>sdl2.GetQueuedAudioSize</strong>
</p>
<p>
<code>sdl2.GetQueuedAudioSize(dev:number)</code>
</p>
<p>
<strong>sdl2.LoadWAV</strong>
</p>
<p>
<code>sdl2.LoadWAV(file:stream) {block?}</code>
</p>
<p>
<strong>sdl2.LoadWAV_RW</strong>
</p>
<p>
<code>sdl2.LoadWAV_RW():void</code>
</p>
<p>
<strong>sdl2.LockAudio</strong>
</p>
<p>
<code>sdl2.LockAudio():void</code>
</p>
<p>
<strong>sdl2.LockAudioDevice</strong>
</p>
<p>
<code>sdl2.LockAudioDevice(dev:number):void</code>
</p>
<p>
<strong>sdl2.MixAudio</strong>
</p>
<p>
<code>sdl2.MixAudio(volume:number):void</code>
</p>
<p>
<strong>sdl2.MixAudioFormat</strong>
</p>
<p>
<code>sdl2.MixAudioFormat(format:number, volume:number):void</code>
</p>
<p>
<strong>sdl2.OpenAudio</strong>
</p>
<p>
<code>sdl2.OpenAudio(desired:sdl2.AudioSpec) {block?}</code>
</p>
<p>
<strong>sdl2.OpenAudioDevice</strong>
</p>
<p>
<code>sdl2.OpenAudioDevice(device:string, iscapture:number, desired:sdl2.AudioSpec, allowed_changes:number)</code>
</p>
<p>
<strong>sdl2.PauseAudio</strong>
</p>
<p>
<code>sdl2.PauseAudio(pause_on:number):void</code>
</p>
<p>
<strong>sdl2.PauseAudioDevice</strong>
</p>
<p>
<code>sdl2.PauseAudioDevice(dev:number, pause_on:number):void</code>
</p>
<p>
<strong>sdl2.QueueAudio</strong>
</p>
<p>
<code>sdl2.QueueAudio(dev:number):void</code>
</p>
<p>
<strong>sdl2.UnlockAudio</strong>
</p>
<p>
<code>sdl2.UnlockAudio():void</code>
</p>
<p>
<strong>sdl2.UnlockAudioDevice</strong>
</p>
<p>
<code>sdl2.UnlockAudioDevice(dev:number):void</code>
</p>
<p>
<strong>sdl2.AUDIO_BITSIZE</strong>
</p>
<p>
<code>sdl2.AUDIO_BITSIZE(x:number) {block?}</code>
</p>
<p>
<strong>sdl2.AUDIO_ISFLOAT</strong>
</p>
<p>
<code>sdl2.AUDIO_ISFLOAT(x:number) {block?}</code>
</p>
<p>
<strong>sdl2.AUDIO_ISBIGENDIAN</strong>
</p>
<p>
<code>sdl2.AUDIO_ISBIGENDIAN(x:number) {block?}</code>
</p>
<p>
<strong>sdl2.AUDIO_ISSIGNED</strong>
</p>
<p>
<code>sdl2.AUDIO_ISSIGNED(x:number) {block?}</code>
</p>
<p>
<strong>sdl2.AUDIO_ISINT</strong>
</p>
<p>
<code>sdl2.AUDIO_ISINT(x:number) {block?}</code>
</p>
<p>
<strong>sdl2.AUDIO_ISLITTLEENDIAN</strong>
</p>
<p>
<code>sdl2.AUDIO_ISLITTLEENDIAN(x:number) {block?}</code>
</p>
<p>
<strong>sdl2.AUDIO_ISUNSIGNED</strong>
</p>
<p>
<code>sdl2.AUDIO_ISUNSIGNED(x:number) {block?}</code>
</p>
<p>
<strong>sdl2.CreateThread</strong>
</p>
<p>
<code>sdl2.CreateThread():void</code>
</p>
<p>
<strong>sdl2.DetachThread</strong>
</p>
<p>
<code>sdl2.DetachThread():void</code>
</p>
<p>
<strong>sdl2.GetThreadID</strong>
</p>
<p>
<code>sdl2.GetThreadID():void</code>
</p>
<p>
<strong>sdl2.GetThreadName</strong>
</p>
<p>
<code>sdl2.GetThreadName():void</code>
</p>
<p>
<strong>sdl2.GetThreadPriority</strong>
</p>
<p>
<code>sdl2.GetThreadPriority():void</code>
</p>
<p>
<strong>sdl2.TLSCreate</strong>
</p>
<p>
<code>sdl2.TLSCreate():void</code>
</p>
<p>
<strong>sdl2.TLSGet</strong>
</p>
<p>
<code>sdl2.TLSGet():void</code>
</p>
<p>
<strong>sdl2.TLSSet</strong>
</p>
<p>
<code>sdl2.TLSSet():void</code>
</p>
<p>
<strong>sdl2.ThreadID</strong>
</p>
<p>
<code>sdl2.ThreadID():void</code>
</p>
<p>
<strong>sdl2.WaitThread</strong>
</p>
<p>
<code>sdl2.WaitThread():void</code>
</p>
<p>
<strong>sdl2.CondBroadcast</strong>
</p>
<p>
<code>sdl2.CondBroadcast():void</code>
</p>
<p>
<strong>sdl2.CondSignal</strong>
</p>
<p>
<code>sdl2.CondSignal():void</code>
</p>
<p>
<strong>sdl2.CondWait</strong>
</p>
<p>
<code>sdl2.CondWait():void</code>
</p>
<p>
<strong>sdl2.CondWaitTimeout</strong>
</p>
<p>
<code>sdl2.CondWaitTimeout():void</code>
</p>
<p>
<strong>sdl2.CreateCond</strong>
</p>
<p>
<code>sdl2.CreateCond():void</code>
</p>
<p>
<strong>sdl2.CreateMutex</strong>
</p>
<p>
<code>sdl2.CreateMutex():void</code>
</p>
<p>
<strong>sdl2.CreateSemaphore</strong>
</p>
<p>
<code>sdl2.CreateSemaphore():void</code>
</p>
<p>
<strong>sdl2.DestroyCond</strong>
</p>
<p>
<code>sdl2.DestroyCond():void</code>
</p>
<p>
<strong>sdl2.DestroyMutex</strong>
</p>
<p>
<code>sdl2.DestroyMutex():void</code>
</p>
<p>
<strong>sdl2.DestroySemaphore</strong>
</p>
<p>
<code>sdl2.DestroySemaphore():void</code>
</p>
<p>
<strong>sdl2.LockMutex</strong>
</p>
<p>
<code>sdl2.LockMutex():void</code>
</p>
<p>
<strong>sdl2.SemPost</strong>
</p>
<p>
<code>sdl2.SemPost():void</code>
</p>
<p>
<strong>sdl2.SemTryWait</strong>
</p>
<p>
<code>sdl2.SemTryWait():void</code>
</p>
<p>
<strong>sdl2.SemValue</strong>
</p>
<p>
<code>sdl2.SemValue():void</code>
</p>
<p>
<strong>sdl2.SemWait</strong>
</p>
<p>
<code>sdl2.SemWait():void</code>
</p>
<p>
<strong>sdl2.SemWaitTimeout</strong>
</p>
<p>
<code>sdl2.SemWaitTimeout():void</code>
</p>
<p>
<strong>sdl2.TryLockMutex</strong>
</p>
<p>
<code>sdl2.TryLockMutex():void</code>
</p>
<p>
<strong>sdl2.UnlockMutex</strong>
</p>
<p>
<code>sdl2.UnlockMutex():void</code>
</p>
<p>
<strong>sdl2.AtomicAdd</strong>
</p>
<p>
<code>sdl2.AtomicAdd():void</code>
</p>
<p>
<strong>sdl2.AtomicCAS</strong>
</p>
<p>
<code>sdl2.AtomicCAS():void</code>
</p>
<p>
<strong>sdl2.AtomicCASPtr</strong>
</p>
<p>
<code>sdl2.AtomicCASPtr():void</code>
</p>
<p>
<strong>sdl2.AtomicDecRef</strong>
</p>
<p>
<code>sdl2.AtomicDecRef():void</code>
</p>
<p>
<strong>sdl2.AtomicGet</strong>
</p>
<p>
<code>sdl2.AtomicGet():void</code>
</p>
<p>
<strong>sdl2.AtomicGetPtr</strong>
</p>
<p>
<code>sdl2.AtomicGetPtr():void</code>
</p>
<p>
<strong>sdl2.AtomicIncRef</strong>
</p>
<p>
<code>sdl2.AtomicIncRef():void</code>
</p>
<p>
<strong>sdl2.AtomicLock</strong>
</p>
<p>
<code>sdl2.AtomicLock():void</code>
</p>
<p>
<strong>sdl2.AtomicSet</strong>
</p>
<p>
<code>sdl2.AtomicSet():void</code>
</p>
<p>
<strong>sdl2.AtomicSetPtr</strong>
</p>
<p>
<code>sdl2.AtomicSetPtr():void</code>
</p>
<p>
<strong>sdl2.AtomicTryLock</strong>
</p>
<p>
<code>sdl2.AtomicTryLock():void</code>
</p>
<p>
<strong>sdl2.AtomicUnlock</strong>
</p>
<p>
<code>sdl2.AtomicUnlock():void</code>
</p>
<p>
<strong>sdl2.CompilerBarrier</strong>
</p>
<p>
<code>sdl2.CompilerBarrier():void</code>
</p>
<p>
<strong>sdl2.AddTimer</strong>
</p>
<p>
<code>sdl2.AddTimer(interval:number)</code>
</p>
<p>
<strong>sdl2.Delay</strong>
</p>
<p>
<code>sdl2.Delay(ms:number):void</code>
</p>
<p>
<strong>sdl2.GetPerformanceCounter</strong>
</p>
<p>
<code>sdl2.GetPerformanceCounter() {block?}</code>
</p>
<p>
<strong>sdl2.GetPerformanceFrequency</strong>
</p>
<p>
<code>sdl2.GetPerformanceFrequency() {block?}</code>
</p>
<p>
<strong>sdl2.GetTicks</strong>
</p>
<p>
<code>sdl2.GetTicks() {block?}</code>
</p>
<p>
<strong>sdl2.RemoveTimer</strong>
</p>
<p>
<code>sdl2.RemoveTimer(id:number) {block?}</code>
</p>
<p>
<strong>sdl2.TICKS_PASSED</strong>
</p>
<p>
<code>sdl2.TICKS_PASSED(A:number, B:number) {block?}</code>
</p>
<p>
<strong>sdl2.GetBasePath</strong>
</p>
<p>
<code>sdl2.GetBasePath()</code>
</p>
<p>
<strong>sdl2.GetPrefPath</strong>
</p>
<p>
<code>sdl2.GetPrefPath(org:string, app:string)</code>
</p>
<p>
<strong>sdl2.AllocRW</strong>
</p>
<p>
<code>sdl2.AllocRW():void</code>
</p>
<p>
<strong>sdl2.FreeRW</strong>
</p>
<p>
<code>sdl2.FreeRW():void</code>
</p>
<p>
<strong>sdl2.RWFromConstMem</strong>
</p>
<p>
<code>sdl2.RWFromConstMem():void</code>
</p>
<p>
<strong>sdl2.RWFromFP</strong>
</p>
<p>
<code>sdl2.RWFromFP():void</code>
</p>
<p>
<strong>sdl2.RWFromFile</strong>
</p>
<p>
<code>sdl2.RWFromFile():void</code>
</p>
<p>
<strong>sdl2.RWFromMem</strong>
</p>
<p>
<code>sdl2.RWFromMem():void</code>
</p>
<p>
<strong>sdl2.RWclose</strong>
</p>
<p>
<code>sdl2.RWclose():void</code>
</p>
<p>
<strong>sdl2.RWread</strong>
</p>
<p>
<code>sdl2.RWread():void</code>
</p>
<p>
<strong>sdl2.RWseek</strong>
</p>
<p>
<code>sdl2.RWseek():void</code>
</p>
<p>
<strong>sdl2.RWtell</strong>
</p>
<p>
<code>sdl2.RWtell():void</code>
</p>
<p>
<strong>sdl2.RWwrite</strong>
</p>
<p>
<code>sdl2.RWwrite():void</code>
</p>
<p>
<strong>sdl2.ReadBE16</strong>
</p>
<p>
<code>sdl2.ReadBE16():void</code>
</p>
<p>
<strong>sdl2.ReadBE32</strong>
</p>
<p>
<code>sdl2.ReadBE32():void</code>
</p>
<p>
<strong>sdl2.ReadBE64</strong>
</p>
<p>
<code>sdl2.ReadBE64():void</code>
</p>
<p>
<strong>sdl2.ReadLE16</strong>
</p>
<p>
<code>sdl2.ReadLE16():void</code>
</p>
<p>
<strong>sdl2.ReadLE32</strong>
</p>
<p>
<code>sdl2.ReadLE32():void</code>
</p>
<p>
<strong>sdl2.ReadLE64</strong>
</p>
<p>
<code>sdl2.ReadLE64():void</code>
</p>
<p>
<strong>sdl2.WriteBE16</strong>
</p>
<p>
<code>sdl2.WriteBE16():void</code>
</p>
<p>
<strong>sdl2.WriteBE32</strong>
</p>
<p>
<code>sdl2.WriteBE32():void</code>
</p>
<p>
<strong>sdl2.WriteBE64</strong>
</p>
<p>
<code>sdl2.WriteBE64():void</code>
</p>
<p>
<strong>sdl2.WriteLE16</strong>
</p>
<p>
<code>sdl2.WriteLE16():void</code>
</p>
<p>
<strong>sdl2.WriteLE32</strong>
</p>
<p>
<code>sdl2.WriteLE32():void</code>
</p>
<p>
<strong>sdl2.WriteLE64</strong>
</p>
<p>
<code>sdl2.WriteLE64():void</code>
</p>
<p>
<strong>sdl2.GetPlatform</strong>
</p>
<p>
<code>sdl2.GetPlatform() {block?}</code>
</p>
<p>
<strong>sdl2.GetCPUCacheLineSize</strong>
</p>
<p>
<code>sdl2.GetCPUCacheLineSize() {block?}</code>
</p>
<p>
<strong>sdl2.GetCPUCount</strong>
</p>
<p>
<code>sdl2.GetCPUCount() {block?}</code>
</p>
<p>
<strong>sdl2.GetSystemRAM</strong>
</p>
<p>
<code>sdl2.GetSystemRAM() {block?}</code>
</p>
<p>
<strong>sdl2.Has3DNow</strong>
</p>
<p>
<code>sdl2.Has3DNow() {block?}</code>
</p>
<p>
<strong>sdl2.HasAVX</strong>
</p>
<p>
<code>sdl2.HasAVX() {block?}</code>
</p>
<p>
<strong>sdl2.HasAVX2</strong>
</p>
<p>
<code>sdl2.HasAVX2()</code>
</p>
<p>
<strong>sdl2.HasAltiVec</strong>
</p>
<p>
<code>sdl2.HasAltiVec() {block?}</code>
</p>
<p>
<strong>sdl2.HasMMX</strong>
</p>
<p>
<code>sdl2.HasMMX() {block?}</code>
</p>
<p>
<strong>sdl2.HasRDTSC</strong>
</p>
<p>
<code>sdl2.HasRDTSC() {block?}</code>
</p>
<p>
<strong>sdl2.HasSSE</strong>
</p>
<p>
<code>sdl2.HasSSE() {block?}</code>
</p>
<p>
<strong>sdl2.HasSSE2</strong>
</p>
<p>
<code>sdl2.HasSSE2() {block?}</code>
</p>
<p>
<strong>sdl2.HasSSE3</strong>
</p>
<p>
<code>sdl2.HasSSE3() {block?}</code>
</p>
<p>
<strong>sdl2.HasSSE41</strong>
</p>
<p>
<code>sdl2.HasSSE41() {block?}</code>
</p>
<p>
<strong>sdl2.HasSSE42</strong>
</p>
<p>
<code>sdl2.HasSSE42() {block?}</code>
</p>
<p>
<strong>sdl2.Swap16</strong>
</p>
<p>
<code>sdl2.Swap16():void</code>
</p>
<p>
<strong>sdl2.Swap32</strong>
</p>
<p>
<code>sdl2.Swap32():void</code>
</p>
<p>
<strong>sdl2.Swap64</strong>
</p>
<p>
<code>sdl2.Swap64():void</code>
</p>
<p>
<strong>sdl2.SwapBE16</strong>
</p>
<p>
<code>sdl2.SwapBE16():void</code>
</p>
<p>
<strong>sdl2.SwapBE32</strong>
</p>
<p>
<code>sdl2.SwapBE32():void</code>
</p>
<p>
<strong>sdl2.SwapBE64</strong>
</p>
<p>
<code>sdl2.SwapBE64():void</code>
</p>
<p>
<strong>sdl2.SwapFloat</strong>
</p>
<p>
<code>sdl2.SwapFloat():void</code>
</p>
<p>
<strong>sdl2.SwapFloatBE</strong>
</p>
<p>
<code>sdl2.SwapFloatBE():void</code>
</p>
<p>
<strong>sdl2.SwapFloatLE</strong>
</p>
<p>
<code>sdl2.SwapFloatLE():void</code>
</p>
<p>
<strong>sdl2.SwapLE16</strong>
</p>
<p>
<code>sdl2.SwapLE16():void</code>
</p>
<p>
<strong>sdl2.SwapLE32</strong>
</p>
<p>
<code>sdl2.SwapLE32():void</code>
</p>
<p>
<strong>sdl2.SwapLE64</strong>
</p>
<p>
<code>sdl2.SwapLE64():void</code>
</p>
<p>
<strong>sdl2.MostSignificantBitIndex32</strong>
</p>
<p>
<code>sdl2.MostSignificantBitIndex32(x:number)</code>
</p>
<p>
<strong>sdl2.GetPowerInfo</strong>
</p>
<p>
<code>sdl2.GetPowerInfo() {block?}</code>
</p>
<p>
<strong>sdl2.AndroidGetActivity</strong>
</p>
<p>
<code>sdl2.AndroidGetActivity():void</code>
</p>
<p>
<strong>sdl2.AndroidGetExternalStoragePath</strong>
</p>
<p>
<code>sdl2.AndroidGetExternalStoragePath():void</code>
</p>
<p>
<strong>sdl2.AndroidGetExternalStorageState</strong>
</p>
<p>
<code>sdl2.AndroidGetExternalStorageState():void</code>
</p>
<p>
<strong>sdl2.AndroidGetInternalStoragePath</strong>
</p>
<p>
<code>sdl2.AndroidGetInternalStoragePath():void</code>
</p>
<p>
<strong>sdl2.AndroidGetJNIEnv</strong>
</p>
<p>
<code>sdl2.AndroidGetJNIEnv():void</code>
</p>
<p>
<strong>sdl2.acos</strong>
</p>
<p>
<code>sdl2.acos(x:number) {block?}</code>
</p>
<h2><span class="caption-index-2">42.2</span><a name="anchor-42-2"></a>sdl2.Window Class</h2>
<h2><span class="caption-index-2">42.3</span><a name="anchor-42-3"></a>sdl2.Renderer Class</h2>
<h2><span class="caption-index-2">42.4</span><a name="anchor-42-4"></a>sdl2.Texture Class</h2>
<h2><span class="caption-index-2">42.5</span><a name="anchor-42-5"></a>sdl2.Event Class</h2>
<h2><span class="caption-index-2">42.6</span><a name="anchor-42-6"></a>sdl2.Point Class</h2>
<h2><span class="caption-index-2">42.7</span><a name="anchor-42-7"></a>sdl2.Rect Class</h2>
<h2><span class="caption-index-2">42.8</span><a name="anchor-42-8"></a>sdl2.Color Class</h2>
<h2><span class="caption-index-2">42.9</span><a name="anchor-42-9"></a>sdl2.Palette Class</h2>
<h2><span class="caption-index-2">42.10</span><a name="anchor-42-10"></a>sdl2.PixelFormat Class</h2>
<h2><span class="caption-index-2">42.11</span><a name="anchor-42-11"></a>sdl2.Keysym Class</h2>
<h2><span class="caption-index-2">42.12</span><a name="anchor-42-12"></a>sdl2.Cursor Class</h2>
<h2><span class="caption-index-2">42.13</span><a name="anchor-42-13"></a>sdl2.Joystick Class</h2>
<h2><span class="caption-index-2">42.14</span><a name="anchor-42-14"></a>sdl2.JoystickGUID Class</h2>
<h2><span class="caption-index-2">42.15</span><a name="anchor-42-15"></a>sdl2.GameController Class</h2>
<h2><span class="caption-index-2">42.16</span><a name="anchor-42-16"></a>sdl2.GameControllerButtonBind Class</h2>
<h2><span class="caption-index-2">42.17</span><a name="anchor-42-17"></a>sdl2.AudioCVT Class</h2>
<h2><span class="caption-index-2">42.18</span><a name="anchor-42-18"></a>sdl2.AudioSpec Class</h2>
<h2><span class="caption-index-2">42.19</span><a name="anchor-42-19"></a>sdl2.Wav Class</h2>
<h2><span class="caption-index-2">42.20</span><a name="anchor-42-20"></a>sdl2.RendererInfo Class</h2>
<h2><span class="caption-index-2">42.21</span><a name="anchor-42-21"></a>sdl2.DisplayMode Class</h2>
<h2><span class="caption-index-2">42.22</span><a name="anchor-42-22"></a>sdl2.GLContext Class</h2>
<h2><span class="caption-index-2">42.23</span><a name="anchor-42-23"></a>sdl2.HapticEffect Class</h2>
<h2><span class="caption-index-2">42.24</span><a name="anchor-42-24"></a>sdl2.Surface Class</h2>
<h2><span class="caption-index-2">42.25</span><a name="anchor-42-25"></a>sdl2.Finger Class</h2>
<h2><span class="caption-index-2">42.26</span><a name="anchor-42-26"></a>Thanks</h2>
<p>
This module uses SDL2 library which is distributed in the following site:
</p>
<p>
<a href="http://www.libsdl.org/">http://www.libsdl.org/</a>
</p>
<p />

{% endraw %}
