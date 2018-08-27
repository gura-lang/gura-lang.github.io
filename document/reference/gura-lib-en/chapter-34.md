---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-33.html#naviitem-selected
nextpage: chapter-35.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">34</span>midi Module</h1>
<h2><span class="caption-index-2">34.1</span><a name="anchor-34-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">midi</code> module provides measures to read/write MIDI files. To utilize it, import the <code class="highlighter-rouge">midi</code> module using <code class="highlighter-rouge">import</code> function.
</p>
<h2><span class="caption-index-2">34.2</span><a name="anchor-34-2"></a>Module Function</h2>
<h2><span class="caption-index-2">34.3</span><a name="anchor-34-3"></a>midi.event Class</h2>
<h2><span class="caption-index-2">34.4</span><a name="anchor-34-4"></a>midi.track Class</h2>
<div class="mb-2"><code>midi.track#seek(offset:number, origin?:symbol):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Moves the insertion point in the track at which the next event is inserted. If <code class="highlighter-rouge">origin</code> is omitted or set to <code class="highlighter-rouge">`set</code>, the insertion point will be set to absolute offset from the beginning. If <code class="highlighter-rouge">origin</code> is set to <code class="highlighter-rouge">`cur</code>, the insertion point will be moved by offset from the current position.
</p>
</div>
<div class="mb-2"><code>midi.track#tell()</code></div>
<div class="mb-2 ml-4">
<p>
Returns the current insertion point in the track.
</p>
</div>
<div class="mb-2"><code>midi.track#erase(n?:number):reduce</code></div>
<div class="mb-2 ml-4">
<p>
Deletes an event at the current insertion point in the track. The argument <code class="highlighter-rouge">n</code> specifies the number of events to be deleted. If <code class="highlighter-rouge">n</code> is omitted, one event will be deleted.
</p>
</div>
<div class="mb-2"><code>midi.track#mml(str:string, max_velocity?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
<p>
Parses MML in the string <code class="highlighter-rouge">str</code> and inserts resulted MIDI events at the current insertion point in the track.
</p>
<p>
The argument <code class="highlighter-rouge">max_velocity</code> specifies the maximum number of velocity in the MML. If omitted, it will be set to 127.
</p>
</div>
<div class="mb-2"><code>midi.track#note_off(channel:number, note:number, velocity:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#note_on(channel:number, note:number, velocity:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#poly_pressure(channel:number, note:number, value:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#control_change(channel:number, controller, value:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#program_change(channel:number, program, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#channel_pressure(channel:number, pressure:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#pitch_bend(channel:number, value:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#sequence_number(number:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#text_event(text:string, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#copyright_notice(text:string, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#sequence_or_track_name(text:string, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#instrument_name(text:string, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#lyric_text(text:string, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#marker_text(text:string, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#cue_point(text:string, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#midi_channel_prefix_assignment(channel:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#end_of_track(deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#tempo_setting(mpqn:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#smpte_offset(hour:number, minute:number, second:number, frame:number, subFrame:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#time_signature(numerator:number, denominator:number, metronome:number, cnt32nd:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#key_signature(key:number, scale:number, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.track#sequencer_specific_event(binary:binary, deltaTime?:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<h2><span class="caption-index-2">34.5</span><a name="anchor-34-5"></a>midi.sequence Class</h2>
<div class="mb-2"><code>midi.sequence(stream?:stream) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
It creates an instance that contains SMF information.
</p>
</div>
<div class="mb-2"><code>midi.sequence#read(stream:stream:r):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.sequence#write(stream:stream:w):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.sequence#play(port:midi.port, speed?:number, repeat:number:nil =&gt; 1):[background,player]</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.sequence#track(index:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.sequence#mml(str:string, max_velocity?:number):reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.sequence#readmml(stream:stream, max_velocity?:number):reduce</code></div>
<div class="mb-2 ml-4">
</div>
<h2><span class="caption-index-2">34.6</span><a name="anchor-34-6"></a>midi.port Class</h2>
<div class="mb-2"><code>midi.port#send(msg+:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.port#play(sequence:midi.sequence, speed?:number, repeat:number:nil =&gt; 1):map:[background,player]</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.port#mml(str:string, max_velocity?:number):[background,player]</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.port#readmml(stream:stream, max_velocity?:number):[background,player]</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.port#note_off(channel:number, note:number, velocity:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.port#note_on(channel:number, note:number, velocity:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.port#poly_pressure(channel:number, note:number, value:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.port#control_change(channel:number, controller:number, value:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.port#program_change(channel:number, program:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.port#channel_pressure(channel:number, pressure:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.port#pitch_bend(channel:number, value:number):map:reduce</code></div>
<div class="mb-2 ml-4">
</div>
<h2><span class="caption-index-2">34.7</span><a name="anchor-34-7"></a>midi.controller Class</h2>
<h2><span class="caption-index-2">34.8</span><a name="anchor-34-8"></a>midi.program Class</h2>
<h2><span class="caption-index-2">34.9</span><a name="anchor-34-9"></a>midi.soundfont Class</h2>
<div class="mb-2"><code>midi.soundfont(stream:stream) {block?}</code></div>
<div class="mb-2 ml-4">
<p>
It creates an instance to access data in SoundFont file.
</p>
</div>
<div class="mb-2"><code>midi.soundfont#synthesizer(preset:number, bank:number, key:number, velocity:number):map {block?}</code></div>
<div class="mb-2 ml-4">
</div>
<div class="mb-2"><code>midi.soundfont#print():void</code></div>
<div class="mb-2 ml-4">
</div>
<h2><span class="caption-index-2">34.10</span><a name="anchor-34-10"></a>midi.synthesizer Class</h2>
{% endraw %}
