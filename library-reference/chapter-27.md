---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">27</span><a name="anchor-27"></a>midi Module</h1>
<p>
The <code>midi</code> module provides measures to read/write MIDI files. To utilize it, import the <code>midi</code> module using <code>import</code> function.
</p>
<h2><span class="caption-index-2">27.1</span><a name="anchor-27-1"></a>Module Functions</h2>
<h2><span class="caption-index-2">27.2</span><a name="anchor-27-2"></a>midi.event Class</h2>
<h2><span class="caption-index-2">27.3</span><a name="anchor-27-3"></a>midi.track Class</h2>
<p>
<strong>midi.track#seek</strong>
</p>
<p>
<code>midi.track#seek(offset:number, origin?:symbol):reduce</code>
</p>
<p>
Moves the insertion point in the track at which the next event is inserted. If <code>origin</code> is omitted or set to <code>`set</code>, the insertion point will be set to absolute offset from the beginning. If <code>origin</code> is set to <code>`cur</code>, the insertion point will be moved by offset from the current position.
</p>
<p>
<strong>midi.track#tell</strong>
</p>
<p>
<code>midi.track#tell()</code>
</p>
<p>
Returns the current insertion point in the track.
</p>
<p>
<strong>midi.track#erase</strong>
</p>
<p>
<code>midi.track#erase(n?:number):reduce</code>
</p>
<p>
Deletes an event at the current insertion point in the track. The argument <code>n</code> specifies the number of events to be deleted. If <code>n</code> is omitted, one event will be deleted.
</p>
<p>
<strong>midi.track#mml</strong>
</p>
<p>
<code>midi.track#mml(str:string, max_velocity?:number):map:reduce</code>
</p>
<p>
Parses MML in the string <code>str</code> and inserts resulted MIDI events at the current insertion point in the track.
</p>
<p>
The argument <code>max_velocity</code> specifies the maximum number of velocity in the MML. If omitted, it will be set to 127.
</p>
<p>
<strong>midi.track#note_off</strong>
</p>
<p>
<code>midi.track#note_off(channel:number, note:number, velocity:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#note_on</strong>
</p>
<p>
<code>midi.track#note_on(channel:number, note:number, velocity:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#poly_pressure</strong>
</p>
<p>
<code>midi.track#poly_pressure(channel:number, note:number, value:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#control_change</strong>
</p>
<p>
<code>midi.track#control_change(channel:number, controller, value:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#program_change</strong>
</p>
<p>
<code>midi.track#program_change(channel:number, program, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#channel_pressure</strong>
</p>
<p>
<code>midi.track#channel_pressure(channel:number, pressure:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#pitch_bend</strong>
</p>
<p>
<code>midi.track#pitch_bend(channel:number, value:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#sequence_number</strong>
</p>
<p>
<code>midi.track#sequence_number(number:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#text_event</strong>
</p>
<p>
<code>midi.track#text_event(text:string, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#copyright_notice</strong>
</p>
<p>
<code>midi.track#copyright_notice(text:string, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#sequence_or_track_name</strong>
</p>
<p>
<code>midi.track#sequence_or_track_name(text:string, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#instrument_name</strong>
</p>
<p>
<code>midi.track#instrument_name(text:string, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#lyric_text</strong>
</p>
<p>
<code>midi.track#lyric_text(text:string, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#marker_text</strong>
</p>
<p>
<code>midi.track#marker_text(text:string, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#cue_point</strong>
</p>
<p>
<code>midi.track#cue_point(text:string, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#midi_channel_prefix_assignment</strong>
</p>
<p>
<code>midi.track#midi_channel_prefix_assignment(channel:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#end_of_track</strong>
</p>
<p>
<code>midi.track#end_of_track(deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#tempo_setting</strong>
</p>
<p>
<code>midi.track#tempo_setting(mpqn:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#smpte_offset</strong>
</p>
<p>
<code>midi.track#smpte_offset(hour:number, minute:number, second:number, frame:number, subFrame:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#time_signature</strong>
</p>
<p>
<code>midi.track#time_signature(numerator:number, denominator:number, metronome:number, cnt32nd:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#key_signature</strong>
</p>
<p>
<code>midi.track#key_signature(key:number, scale:number, deltaTime?:number):map:reduce</code>
</p>
<p>
<strong>midi.track#sequencer_specific_event</strong>
</p>
<p>
<code>midi.track#sequencer_specific_event(binary:binary, deltaTime?:number):map:reduce</code>
</p>
<h2><span class="caption-index-2">27.4</span><a name="anchor-27-4"></a>midi.sequence Class</h2>
<p>
<strong>midi.sequence</strong>
</p>
<p>
<code>midi.sequence(stream?:stream) {block?}</code>
</p>
<p>
It creates an instance that contains SMF information.
</p>
<p>
<strong>midi.sequence#read</strong>
</p>
<p>
<code>midi.sequence#read(stream:stream:r):map:reduce</code>
</p>
<p>
<strong>midi.sequence#write</strong>
</p>
<p>
<code>midi.sequence#write(stream:stream:w):map:reduce</code>
</p>
<p>
<strong>midi.sequence#play</strong>
</p>
<p>
<code>midi.sequence#play(port:midi.port, speed?:number, repeat:number:nil =&gt; 1):[background,player]</code>
</p>
<p>
<strong>midi.sequence#track</strong>
</p>
<p>
<code>midi.sequence#track(index:number):map {block?}</code>
</p>
<p>
<strong>midi.sequence#mml</strong>
</p>
<p>
<code>midi.sequence#mml(str:string, max_velocity?:number):reduce</code>
</p>
<p>
<strong>midi.sequence#readmml</strong>
</p>
<p>
<code>midi.sequence#readmml(stream:stream, max_velocity?:number):reduce</code>
</p>
<h2><span class="caption-index-2">27.5</span><a name="anchor-27-5"></a>midi.port Class</h2>
<p>
<strong>midi.port#send</strong>
</p>
<p>
<code>midi.port#send(msg+:number):map:reduce</code>
</p>
<p>
<strong>midi.port#play</strong>
</p>
<p>
<code>midi.port#play(sequence:midi.sequence, speed?:number, repeat:number:nil =&gt; 1):map:[background,player]</code>
</p>
<p>
<strong>midi.port#mml</strong>
</p>
<p>
<code>midi.port#mml(str:string, max_velocity?:number):[background,player]</code>
</p>
<p>
<strong>midi.port#readmml</strong>
</p>
<p>
<code>midi.port#readmml(stream:stream, max_velocity?:number):[background,player]</code>
</p>
<p>
<strong>midi.port#note_off</strong>
</p>
<p>
<code>midi.port#note_off(channel:number, note:number, velocity:number):map:reduce</code>
</p>
<p>
<strong>midi.port#note_on</strong>
</p>
<p>
<code>midi.port#note_on(channel:number, note:number, velocity:number):map:reduce</code>
</p>
<p>
<strong>midi.port#poly_pressure</strong>
</p>
<p>
<code>midi.port#poly_pressure(channel:number, note:number, value:number):map:reduce</code>
</p>
<p>
<strong>midi.port#control_change</strong>
</p>
<p>
<code>midi.port#control_change(channel:number, controller:number, value:number):map:reduce</code>
</p>
<p>
<strong>midi.port#program_change</strong>
</p>
<p>
<code>midi.port#program_change(channel:number, program:number):map:reduce</code>
</p>
<p>
<strong>midi.port#channel_pressure</strong>
</p>
<p>
<code>midi.port#channel_pressure(channel:number, pressure:number):map:reduce</code>
</p>
<p>
<strong>midi.port#pitch_bend</strong>
</p>
<p>
<code>midi.port#pitch_bend(channel:number, value:number):map:reduce</code>
</p>
<h2><span class="caption-index-2">27.6</span><a name="anchor-27-6"></a>midi.controller Class</h2>
<h2><span class="caption-index-2">27.7</span><a name="anchor-27-7"></a>midi.program Class</h2>
<h2><span class="caption-index-2">27.8</span><a name="anchor-27-8"></a>midi.soundfont Class</h2>
<p>
<strong>midi.soundfont</strong>
</p>
<p>
<code>midi.soundfont(stream:stream) {block?}</code>
</p>
<p>
It creates an instance to access data in SoundFont file.
</p>
<p>
<strong>midi.soundfont#synthesizer</strong>
</p>
<p>
<code>midi.soundfont#synthesizer(preset:number, bank:number, key:number, velocity:number):map {block?}</code>
</p>
<p>
<strong>midi.soundfont#print</strong>
</p>
<p>
<code>midi.soundfont#print():void</code>
</p>
<h2><span class="caption-index-2">27.9</span><a name="anchor-27-9"></a>midi.synthesizer Class</h2>
<p />

{% endraw %}
