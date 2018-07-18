---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">34</span><a name="anchor-34"></a>midi Module</h1>
<h2><span class="caption-index-2">34.1</span><a name="anchor-34-1"></a>Overview</h2>
<p>
The <code>midi</code> module provides measures to read/write MIDI files. To utilize it, import the <code>midi</code> module using <code>import</code> function.
</p>
<h2><span class="caption-index-2">34.2</span><a name="anchor-34-2"></a>Module Function</h2>
<h2><span class="caption-index-2">34.3</span><a name="anchor-34-3"></a>midi.event Class</h2>
<h2><span class="caption-index-2">34.4</span><a name="anchor-34-4"></a>midi.track Class</h2>
<p>
<div><strong style="text-decoration:underline">midi.track#seek</strong></div>
<div style="margin-bottom:1em"><code>midi.track#seek(offset:number, origin?:symbol):reduce</code></div>
Moves the insertion point in the track at which the next event is inserted. If <code>origin</code> is omitted or set to <code>`set</code>, the insertion point will be set to absolute offset from the beginning. If <code>origin</code> is set to <code>`cur</code>, the insertion point will be moved by offset from the current position.
</p>
<p>
<div><strong style="text-decoration:underline">midi.track#tell</strong></div>
<div style="margin-bottom:1em"><code>midi.track#tell()</code></div>
Returns the current insertion point in the track.
</p>
<p>
<div><strong style="text-decoration:underline">midi.track#erase</strong></div>
<div style="margin-bottom:1em"><code>midi.track#erase(n?:number):reduce</code></div>
Deletes an event at the current insertion point in the track. The argument <code>n</code> specifies the number of events to be deleted. If <code>n</code> is omitted, one event will be deleted.
</p>
<p>
<div><strong style="text-decoration:underline">midi.track#mml</strong></div>
<div style="margin-bottom:1em"><code>midi.track#mml(str:string, max_velocity?:number):map:reduce</code></div>
Parses MML in the string <code>str</code> and inserts resulted MIDI events at the current insertion point in the track.
</p>
<p>
The argument <code>max_velocity</code> specifies the maximum number of velocity in the MML. If omitted, it will be set to 127.
</p>
<p>
<div><strong style="text-decoration:underline">midi.track#note_off</strong></div>
<div style="margin-bottom:1em"><code>midi.track#note_off(channel:number, note:number, velocity:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#note_on</strong></div>
<div style="margin-bottom:1em"><code>midi.track#note_on(channel:number, note:number, velocity:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#poly_pressure</strong></div>
<div style="margin-bottom:1em"><code>midi.track#poly_pressure(channel:number, note:number, value:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#control_change</strong></div>
<div style="margin-bottom:1em"><code>midi.track#control_change(channel:number, controller, value:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#program_change</strong></div>
<div style="margin-bottom:1em"><code>midi.track#program_change(channel:number, program, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#channel_pressure</strong></div>
<div style="margin-bottom:1em"><code>midi.track#channel_pressure(channel:number, pressure:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#pitch_bend</strong></div>
<div style="margin-bottom:1em"><code>midi.track#pitch_bend(channel:number, value:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#sequence_number</strong></div>
<div style="margin-bottom:1em"><code>midi.track#sequence_number(number:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#text_event</strong></div>
<div style="margin-bottom:1em"><code>midi.track#text_event(text:string, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#copyright_notice</strong></div>
<div style="margin-bottom:1em"><code>midi.track#copyright_notice(text:string, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#sequence_or_track_name</strong></div>
<div style="margin-bottom:1em"><code>midi.track#sequence_or_track_name(text:string, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#instrument_name</strong></div>
<div style="margin-bottom:1em"><code>midi.track#instrument_name(text:string, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#lyric_text</strong></div>
<div style="margin-bottom:1em"><code>midi.track#lyric_text(text:string, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#marker_text</strong></div>
<div style="margin-bottom:1em"><code>midi.track#marker_text(text:string, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#cue_point</strong></div>
<div style="margin-bottom:1em"><code>midi.track#cue_point(text:string, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#midi_channel_prefix_assignment</strong></div>
<div style="margin-bottom:1em"><code>midi.track#midi_channel_prefix_assignment(channel:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#end_of_track</strong></div>
<div style="margin-bottom:1em"><code>midi.track#end_of_track(deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#tempo_setting</strong></div>
<div style="margin-bottom:1em"><code>midi.track#tempo_setting(mpqn:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#smpte_offset</strong></div>
<div style="margin-bottom:1em"><code>midi.track#smpte_offset(hour:number, minute:number, second:number, frame:number, subFrame:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#time_signature</strong></div>
<div style="margin-bottom:1em"><code>midi.track#time_signature(numerator:number, denominator:number, metronome:number, cnt32nd:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#key_signature</strong></div>
<div style="margin-bottom:1em"><code>midi.track#key_signature(key:number, scale:number, deltaTime?:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.track#sequencer_specific_event</strong></div>
<div style="margin-bottom:1em"><code>midi.track#sequencer_specific_event(binary:binary, deltaTime?:number):map:reduce</code></div>

</p>
<h2><span class="caption-index-2">34.5</span><a name="anchor-34-5"></a>midi.sequence Class</h2>
<p>
<div><strong style="text-decoration:underline">midi.sequence</strong></div>
<div style="margin-bottom:1em"><code>midi.sequence(stream?:stream) {block?}</code></div>
It creates an instance that contains SMF information.
</p>
<p>
<div><strong style="text-decoration:underline">midi.sequence#read</strong></div>
<div style="margin-bottom:1em"><code>midi.sequence#read(stream:stream:r):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.sequence#write</strong></div>
<div style="margin-bottom:1em"><code>midi.sequence#write(stream:stream:w):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.sequence#play</strong></div>
<div style="margin-bottom:1em"><code>midi.sequence#play(port:midi.port, speed?:number, repeat:number:nil =&gt; 1):[background,player]</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.sequence#track</strong></div>
<div style="margin-bottom:1em"><code>midi.sequence#track(index:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.sequence#mml</strong></div>
<div style="margin-bottom:1em"><code>midi.sequence#mml(str:string, max_velocity?:number):reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.sequence#readmml</strong></div>
<div style="margin-bottom:1em"><code>midi.sequence#readmml(stream:stream, max_velocity?:number):reduce</code></div>

</p>
<h2><span class="caption-index-2">34.6</span><a name="anchor-34-6"></a>midi.port Class</h2>
<p>
<div><strong style="text-decoration:underline">midi.port#send</strong></div>
<div style="margin-bottom:1em"><code>midi.port#send(msg+:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.port#play</strong></div>
<div style="margin-bottom:1em"><code>midi.port#play(sequence:midi.sequence, speed?:number, repeat:number:nil =&gt; 1):map:[background,player]</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.port#mml</strong></div>
<div style="margin-bottom:1em"><code>midi.port#mml(str:string, max_velocity?:number):[background,player]</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.port#readmml</strong></div>
<div style="margin-bottom:1em"><code>midi.port#readmml(stream:stream, max_velocity?:number):[background,player]</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.port#note_off</strong></div>
<div style="margin-bottom:1em"><code>midi.port#note_off(channel:number, note:number, velocity:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.port#note_on</strong></div>
<div style="margin-bottom:1em"><code>midi.port#note_on(channel:number, note:number, velocity:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.port#poly_pressure</strong></div>
<div style="margin-bottom:1em"><code>midi.port#poly_pressure(channel:number, note:number, value:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.port#control_change</strong></div>
<div style="margin-bottom:1em"><code>midi.port#control_change(channel:number, controller:number, value:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.port#program_change</strong></div>
<div style="margin-bottom:1em"><code>midi.port#program_change(channel:number, program:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.port#channel_pressure</strong></div>
<div style="margin-bottom:1em"><code>midi.port#channel_pressure(channel:number, pressure:number):map:reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.port#pitch_bend</strong></div>
<div style="margin-bottom:1em"><code>midi.port#pitch_bend(channel:number, value:number):map:reduce</code></div>

</p>
<h2><span class="caption-index-2">34.7</span><a name="anchor-34-7"></a>midi.controller Class</h2>
<h2><span class="caption-index-2">34.8</span><a name="anchor-34-8"></a>midi.program Class</h2>
<h2><span class="caption-index-2">34.9</span><a name="anchor-34-9"></a>midi.soundfont Class</h2>
<p>
<div><strong style="text-decoration:underline">midi.soundfont</strong></div>
<div style="margin-bottom:1em"><code>midi.soundfont(stream:stream) {block?}</code></div>
It creates an instance to access data in SoundFont file.
</p>
<p>
<div><strong style="text-decoration:underline">midi.soundfont#synthesizer</strong></div>
<div style="margin-bottom:1em"><code>midi.soundfont#synthesizer(preset:number, bank:number, key:number, velocity:number):map {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">midi.soundfont#print</strong></div>
<div style="margin-bottom:1em"><code>midi.soundfont#print():void</code></div>

</p>
<h2><span class="caption-index-2">34.10</span><a name="anchor-34-10"></a>midi.synthesizer Class</h2>
<p />

{% endraw %}
