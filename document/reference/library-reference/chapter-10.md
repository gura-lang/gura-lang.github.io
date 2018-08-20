---
layout: doc-widenavi
lang: en
title: Gura Library Reference
prevpage: chapter-09.html#naviitem-selected
nextpage: chapter-11.html#naviitem-selected
---
{% raw %}
<h1><span class="caption-index-1">10</span>cairo Module</h1>
<h2><span class="caption-index-2">10.1</span><a name="anchor-10-1"></a>Overview</h2>
<p>
The <code class="highlighter-rouge">cairo</code> module provides methods to draw 2-D graphics using Cairo library. Official site of Cairo is <a href="http://cairographics.org/">http://cairographics.org/</a>.
</p>
<h2><span class="caption-index-2">10.2</span><a name="anchor-10-2"></a>Drawing</h2>
<h3><span class="caption-index-3">10.2.1</span><a name="anchor-10-2-1"></a>cairo.context - The cairo drawing context</h3>
<h4><span class="caption-index-4">10.2.1.1</span><a name="anchor-10-2-1-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.context#status</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#status()</code></div>
Checks whether an error has previously occurred for this context.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#save</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#save():reduce {block?}</code></div>
Makes a copy of the current state of cr and saves it on an internal stack of saved states for cr. When <code class="highlighter-rouge">cairo.context#restore()</code> is called, cr will be restored to the saved state. Multiple calls to <code class="highlighter-rouge">cairo.context#save()</code> and <code class="highlighter-rouge">cairo.context#restore()</code> can be nested; each call to <code class="highlighter-rouge">cairo.context#restore()</code> restores the state from the matching paired <code class="highlighter-rouge">cairo.context#save()</code>.
</p>
<p>
It isn't necessary to clear all saved states before a cairo_t is freed. If the reference count of a cairo_t drops to zero in response to a call to <code class="highlighter-rouge">cairo.context#destroy()</code>, any saved states will be freed along with the <code class="highlighter-rouge">cairo_t</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#restore</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#restore():reduce</code></div>
Restores cr to the state saved by a preceding call to <code class="highlighter-rouge">cairo.context#save()</code> and removes that state from the stack of saved states.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_target</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_target()</code></div>
Gets the target surface for the cairo context as passed to <code class="highlighter-rouge">cairo.context</code> constructor.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#push_group</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#push_group():reduce</code></div>
Temporarily redirects drawing to an intermediate surface known as a group. The redirection lasts until the group is completed by a call to <code class="highlighter-rouge">cairo.context#pop_group()</code> or <code class="highlighter-rouge">cairo.context#pop_group_to_source()</code>. These calls provide the result of any drawing to the group as a pattern, (either as an explicit object, or set as the source pattern).
</p>
<p>
This group functionality can be convenient for performing intermediate compositing. One common use of a group is to render objects as opaque within the group, (so that they occlude each other), and then blend the result with translucence onto the destination.
</p>
<p>
Groups can be nested arbitrarily deep by making balanced calls to <code class="highlighter-rouge">cairo.context#push_group()</code>/<code class="highlighter-rouge">cairo.context#pop_group()</code>. Each call pushes/pops the new target group onto/from a stack.
</p>
<p>
The <code class="highlighter-rouge">cairo.context#push_group()</code> function calls cairo_save() so that any changes to the graphics state will not be visible outside the group, (the pop_group functions call cairo_restore()).
</p>
<p>
By default the intermediate group will have a content type of <code class="highlighter-rouge">cairo.CONTENT_COLOR_ALPHA</code>. Other content types can be chosen for the group by using <code class="highlighter-rouge">cairo.context#push_group_with_content()</code> instead.
</p>
<p>
As an example, here is how one might fill and stroke a path with translucence, but without any portion of the fill being visible under the stroke:
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#push_group_with_content</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#push_group_with_content(content:number):reduce</code></div>
Temporarily redirects drawing to an intermediate surface known as a group. The redirection lasts until the group is completed by a call to <code class="highlighter-rouge">cairo.context#pop_group()</code> or <code class="highlighter-rouge">cairo.context#pop_group_to_source()</code>. These calls provide the result of any drawing to the group as a pattern, (either as an explicit object, or set as the source pattern).
</p>
<p>
The group will have a content type of content. The ability to control this content type is the only distinction between this function and <code class="highlighter-rouge">cairo.context#push_group()</code> which you should see for a more detailed description of group rendering.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#pop_group</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#pop_group() {block?}</code></div>
Terminates the redirection begun by a call to <code class="highlighter-rouge">cairo.context#push_group()</code> or <code class="highlighter-rouge">cairo.context#push_group_with_content()</code> and returns a new pattern containing the results of all drawing operations performed to the group.
</p>
<p>
The <code class="highlighter-rouge">cairo.context#pop_group()</code> function calls cairo_restore(), (balancing a call to <code class="highlighter-rouge">cairo_save()</code> by the <code class="highlighter-rouge">push_group</code> function), so that any changes to the graphics state will not be visible outside the group.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#pop_group_to_source</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#pop_group_to_source():reduce</code></div>
Terminates the redirection begun by a call to <code class="highlighter-rouge">cairo.context#push_group()</code> or <code class="highlighter-rouge">cairo.context#push_group_with_content()</code> and installs the resulting pattern as the source pattern in the given cairo context.
</p>
<p>
The <code class="highlighter-rouge">cairo.context#pop_group()</code> function calls cairo_restore(), (balancing a call to cairo_save() by the push_group function), so that any changes to the graphics state will not be visible outside the group.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_group_target</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_group_target() {block?}</code></div>
Gets the current destination surface for the context. This is either the original target surface as passed to <code class="highlighter-rouge">cairo.context</code> constructor or the target surface for the current group as started by the most recent call to <code class="highlighter-rouge">cairo.context#push_group()</code> or <code class="highlighter-rouge">cairo.context#push_group_with_content()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_source_rgb</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_source_rgb(red:number, green:number, blue:number):reduce</code></div>
Sets the source pattern within cr to an opaque color. This opaque color will then be used for any subsequent drawing operation until a new source pattern is set.
</p>
<p>
The color components are floating point numbers in the range 0 to 1. If the values passed in are outside that range, they will be clamped.
</p>
<p>
The default source pattern is opaque black, (that is, it is equivalent to <code class="highlighter-rouge">cr.set_source_rgb(0.0, 0.0, 0.0))</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_source_rgba</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_source_rgba(red:number, green:number, blue:number, alpha:number):reduce</code></div>
Sets the source pattern within cr to a translucent color. This color will then be used for any subsequent drawing operation until a new source pattern is set.
</p>
<p>
The color and alpha components are floating point numbers in the range 0 to 1. If the values passed in are outside that range, they will be clamped.
</p>
<p>
The default source pattern is opaque black, (that is, it is equivalent to <code class="highlighter-rouge">cr.set_source_rgba(0.0, 0.0, 0.0, 1.0))</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_source</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_source(source:cairo.pattern):reduce</code></div>
Sets the source pattern within cr to source. This pattern will then be used for any subsequent drawing operation until a new source pattern is set.
</p>
<p>
Note: The pattern's transformation matrix will be locked to the user space in effect at the time of <code class="highlighter-rouge">cairo.context#set_source()</code>. This means that further modifications of the current transformation matrix will not affect the source pattern. See <code class="highlighter-rouge">cairo.pattern#set_matrix()</code>.
</p>
<p>
The default source pattern is a solid pattern that is opaque black, (that is, it is equivalent to <code class="highlighter-rouge">cr.set_source_rgb(0.0, 0.0, 0.0))</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_source_surface</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_source_surface(surface:cairo.surface, x:number, y:number):reduce</code></div>
This is a convenience function for creating a pattern from <code class="highlighter-rouge">surface</code> and setting it as the source in <code class="highlighter-rouge">cr</code> with <code class="highlighter-rouge">cairo.context#set_source()</code>.
</p>
<p>
The <code class="highlighter-rouge">x</code> and <code class="highlighter-rouge">y</code> parameters give the user-space coordinate at which the surface origin should appear. (The surface origin is its upper-left corner before any transformation has been applied.) The x and y parameters are negated and then set as translation values in the pattern matrix.
</p>
<p>
Other than the initial translation pattern matrix, as described above, all other pattern attributes, (such as its extend mode), are set to the default values as in <code class="highlighter-rouge">cairo.pattern.create_for_surface()</code>. The resulting pattern can be queried with <code class="highlighter-rouge">cairo.context#get_source()</code> so that these attributes can be modified if desired, (eg. to create a repeating pattern with <code class="highlighter-rouge">cairo.pattern#set_extend()</code>).
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_source</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_source() {block?}</code></div>
Gets the current source pattern for <code class="highlighter-rouge">cr</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_antialias</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_antialias(antialias:number):reduce</code></div>
Set the antialiasing mode of the rasterizer used for drawing shapes. This value is a hint, and a particular backend may or may not support a particular value. At the current time, no backend supports <code class="highlighter-rouge">cairo.ANTIALIAS_SUBPIXEL</code> when drawing shapes.
</p>
<p>
Note that this option does not affect text rendering, instead see <code class="highlighter-rouge">cairo.font_options#set_antialias()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_antialias</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_antialias()</code></div>
Gets the current shape antialiasing mode, as set by <code class="highlighter-rouge">cairo.context#set_antialias()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_dash</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_dash(dashes[]:number, offset:number):reduce</code></div>
Sets the dash pattern to be used by <code class="highlighter-rouge">cairo.context#stroke()</code>. A dash pattern is specified by dashes, an array of positive values. Each value provides the length of alternate "on" and "off" portions of the stroke. The offset specifies an offset into the pattern at which the stroke begins.
</p>
<p>
Each "on" segment will have caps applied as if the segment were a separate sub-path. In particular, it is valid to use an "on" length of 0.0 with <code class="highlighter-rouge">cairo.LINE_CAP_ROUND</code> or <code class="highlighter-rouge">cairo.LINE_CAP_SQUARE</code> in order to distributed dots or squares along a path.
</p>
<p>
Note: The length values are in user-space units as evaluated at the time of stroking. This is not necessarily the same as the user space at the time of <code class="highlighter-rouge">cairo.context#set_dash()</code>.
</p>
<p>
If length of dashes is 0 dashing is disabled.
</p>
<p>
If length of dashes is 1 a symmetric pattern is assumed with alternating on and off portions of the size specified by the single value in dashes.
</p>
<p>
If any value in dashes is negative, or if all values are 0, then cr will be put into an error state with a status of <code class="highlighter-rouge">cairo.STATUS_INVALID_DASH</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_dash</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_dash()</code></div>
Gets the current dash array.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_fill_rule</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_fill_rule(fill_rule:number):reduce</code></div>
Set the current fill rule within the cairo context. The fill rule is used to determine which regions are inside or outside a complex (potentially self-intersecting) path. The current fill rule affects both <code class="highlighter-rouge">cairo.context#fill()</code> and <code class="highlighter-rouge">cairo.context#clip()</code>. See cairo_fill_rule_t for details on the semantics of each available fill rule.
</p>
<p>
The default fill rule is <code class="highlighter-rouge">cairo.FILL_RULE_WINDING</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_fill_rule</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_fill_rule()</code></div>
Gets the current fill rule, as set by <code class="highlighter-rouge">cairo.context#set_fill_rule()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_line_cap</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_line_cap(line_cap:number):reduce</code></div>
Sets the current line cap style within the cairo context. See <code class="highlighter-rouge">cairo_line_cap_t</code> for details about how the available line cap styles are drawn.
</p>
<p>
As with the other stroke parameters, the current line cap style is examined by <code class="highlighter-rouge">cairo.context#stroke()</code>, <code class="highlighter-rouge">cairo.context#stroke_extents()</code>, and <code class="highlighter-rouge">cairo.context#stroke_to_path()</code>, but does not have any effect during path construction.
</p>
<p>
The default line cap style is <code class="highlighter-rouge">cairo.LINE_CAP_BUTT</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_line_cap</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_line_cap()</code></div>
Gets the current line cap style, as set by <code class="highlighter-rouge">cairo.context#set_line_cap()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_line_join</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_line_join(line_join:number):reduce</code></div>
Sets the current line join style within the cairo context. See <code class="highlighter-rouge">cairo_line_join_t</code> for details about how the available line join styles are drawn.
</p>
<p>
As with the other stroke parameters, the current line join style is examined by <code class="highlighter-rouge">cairo.context#stroke()</code>, <code class="highlighter-rouge">cairo.context#stroke_extents()</code>, and <code class="highlighter-rouge">cairo.context#stroke_to_path()</code>, but does not have any effect during path construction.
</p>
<p>
The default line join style is <code class="highlighter-rouge">cairo.LINE_JOIN_MITER</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_line_join</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_line_join()</code></div>
Gets the current line join style, as set by <code class="highlighter-rouge">cairo.context#set_line_join()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_line_width</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_line_width(width:number):reduce</code></div>
Sets the current line width within the cairo context. The line width value specifies the diameter of a pen that is circular in user space, (though device-space pen may be an ellipse in general due to scaling/shear/rotation of the CTM).
</p>
<p>
Note: When the description above refers to user space and CTM it refers to the user space and CTM in effect at the time of the stroking operation, not the user space and CTM in effect at the time of the call to <code class="highlighter-rouge">cairo.context#set_line_width()</code>. The simplest usage makes both of these spaces identical. That is, if there is no change to the CTM between a call to <code class="highlighter-rouge">cairo.context#set_line_width()</code> and the stroking operation, then one can just pass user-space values to <code class="highlighter-rouge">cairo.context#set_line_width()</code> and ignore this note.
</p>
<p>
As with the other stroke parameters, the current line width is examined by <code class="highlighter-rouge">cairo.context#stroke()</code>, <code class="highlighter-rouge">cairo.context#stroke_extents()</code>, and <code class="highlighter-rouge">cairo.context#stroke_to_path()</code>, but does not have any effect during path construction.
</p>
<p>
The default line width value is 2.0.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_line_width</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_line_width()</code></div>
This function returns the current line width value exactly as set by <code class="highlighter-rouge">cairo.context#set_line_width()</code>. Note that the value is unchanged even if the CTM has changed between the calls to <code class="highlighter-rouge">cairo.context#set_line_width()</code> and <code class="highlighter-rouge">cairo.context#get_line_width()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_miter_limit</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_miter_limit(limit:number):reduce</code></div>
Sets the current miter limit within the cairo context.
</p>
<p>
If the current line join style is set to <code class="highlighter-rouge">cairo.LINE_JOIN_MITER</code> (see <code class="highlighter-rouge">cairo.context#set_line_join()</code>), the miter limit is used to determine whether the lines should be joined with a bevel instead of a miter. Cairo divides the length of the miter by the line width. If the result is greater than the miter limit, the style is converted to a bevel.
</p>
<p>
As with the other stroke parameters, the current line miter limit is examined by <code class="highlighter-rouge">cairo.context#stroke()</code>, <code class="highlighter-rouge">cairo.context#stroke_extents()</code>, and <code class="highlighter-rouge">cairo.context#stroke_to_path()</code>, but does not have any effect during path construction.
</p>
<p>
The default miter limit value is 10.0, which will convert joins with interior angles less than 11 degrees to bevels instead of miters. For reference, a miter limit of 2.0 makes the miter cutoff at 60 degrees, and a miter limit of 1.414 makes the cutoff at 90 degrees.
</p>
<p>
A miter limit for a desired angle can be computed as: miter limit = 1/sin(angle/2)
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_miter_limit</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_miter_limit()</code></div>
Gets the current miter limit, as set by cairo.context#set_miter_limit().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_operator</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_operator(op:number):reduce</code></div>
Sets the compositing operator to be used for all drawing operations. See <code class="highlighter-rouge">cairo_operator_t</code> for details on the semantics of each available compositing operator.
</p>
<p>
The default operator is <code class="highlighter-rouge">cairo.OPERATOR_OVER</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_operator</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_operator()</code></div>
Gets the current compositing operator for a cairo context.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_tolerance</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_tolerance(tolerance:number):reduce</code></div>
Sets the tolerance used when converting paths into trapezoids. Curved segments of the path will be subdivided until the maximum deviation between the original path and the polygonal approximation is less than tolerance. The default value is 0.1. A larger value will give better performance, a smaller value, better appearance. (Reducing the value from the default value of 0.1 is unlikely to improve appearance significantly.) The accuracy of paths within Cairo is limited by the precision of its internal arithmetic, and the prescribed tolerance is restricted to the smallest representable internal value.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_tolerance</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_tolerance()</code></div>
Gets the current tolerance value, as set by <code class="highlighter-rouge">cairo.context#set_tolerance()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#clip</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#clip():reduce</code></div>
Establishes a new clip region by intersecting the current clip region with the current path as it would be filled by <code class="highlighter-rouge">cairo.context#fill()</code> and according to the current fill rule (see <code class="highlighter-rouge">cairo.context#set_fill_rule()</code>).
</p>
<p>
After <code class="highlighter-rouge">cairo.context#clip()</code>, the current path will be cleared from the cairo context.
</p>
<p>
The current clip region affects all drawing operations by effectively masking out any changes to the surface that are outside the current clip region.
</p>
<p>
Calling <code class="highlighter-rouge">cairo.context#clip()</code> can only make the clip region smaller, never larger. But the current clip is part of the graphics state, so a temporary restriction of the clip region can be achieved by calling <code class="highlighter-rouge">cairo.context#clip()</code> within a <code class="highlighter-rouge">cairo.context#save()</code>/<code class="highlighter-rouge">cairo.context#restore()</code> pair. The only other means of increasing the size of the clip region is <code class="highlighter-rouge">cairo.context#reset_clip()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#clip_preserve</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#clip_preserve():reduce</code></div>
Establishes a new clip region by intersecting the current clip region with the current path as it would be filled by <code class="highlighter-rouge">cairo.context#fill()</code> and according to the current fill rule (see <code class="highlighter-rouge">cairo.context#set_fill_rule()</code>). Unlike <code class="highlighter-rouge">cairo.context#clip()</code>, <code class="highlighter-rouge">cairo.context#clip_preserve()</code> preserves the path within the cairo context.
</p>
<p>
The current clip region affects all drawing operations by effectively masking out any changes to the surface that are outside the current clip region.
</p>
<p>
Calling <code class="highlighter-rouge">cairo.context#clip_preserve()</code> can only make the clip region smaller, never larger. But the current clip is part of the graphics state, so a temporary restriction of the clip region can be achieved by calling <code class="highlighter-rouge">cairo.context#clip_preserve()</code> within a <code class="highlighter-rouge">cairo.context#save()</code>/<code class="highlighter-rouge">cairo.context#restore()</code> pair. The only other means of increasing the size of the clip region is <code class="highlighter-rouge">cairo.context#reset_clip()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#clip_extents</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#clip_extents()</code></div>
Computes a bounding box in user coordinates covering the area inside the current clip.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#in_clip</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#in_clip(x:number, y:number)</code></div>
Tests whether the given point is inside the area that would be visible through the current clip, i.e. the area that would be filled by a <code class="highlighter-rouge">cairo.context#paint()</code> operation.
</p>
<p>
See <code class="highlighter-rouge">cairo.context#clip()</code>, and <code class="highlighter-rouge">cairo.context#clip_preserve()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#reset_clip</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#reset_clip():reduce</code></div>
Reset the current clip region to its original, unrestricted state. That is, set the clip region to an infinitely large shape containing the target surface. Equivalently, if infinity is too hard to grasp, one can imagine the clip region being reset to the exact bounds of the target surface.
</p>
<p>
Note that code meant to be reusable should not call <code class="highlighter-rouge">cairo.context#reset_clip()</code> as it will cause results unexpected by higher-level code which calls <code class="highlighter-rouge">cairo.context#clip()</code>. Consider using <code class="highlighter-rouge">cairo.context#save()</code> and <code class="highlighter-rouge">cairo.context#restore()</code> around <code class="highlighter-rouge">cairo.context#clip()</code> as a more robust means of temporarily restricting the clip region.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#copy_clip_rectangle_list</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#copy_clip_rectangle_list()</code></div>
Gets the current clip region as a list of rectangles in user coordinates.
</p>
<p>
The status in the list may be <code class="highlighter-rouge">cairo.STATUS_CLIP_NOT_REPRESENTABLE</code> to indicate that the clip region cannot be represented as a list of user-space rectangles. The status may have other values to indicate other errors.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#fill</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#fill():reduce</code></div>
A drawing operator that fills the current path according to the current fill rule, (each sub-path is implicitly closed before being filled). After <code class="highlighter-rouge">cairo.context#fill()</code>, the current path will be cleared from the cairo context. See <code class="highlighter-rouge">cairo.context#set_fill_rule()</code> and <code class="highlighter-rouge">cairo.context#fill_preserve()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#fill_preserve</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#fill_preserve():reduce</code></div>
A drawing operator that fills the current path according to the current fill rule, (each sub-path is implicitly closed before being filled). Unlike <code class="highlighter-rouge">cairo.context#fill()</code>, <code class="highlighter-rouge">cairo.context#fill_preserve()</code> preserves the path within the cairo context.
</p>
<p>
See <code class="highlighter-rouge">cairo.context#set_fill_rule()</code> and <code class="highlighter-rouge">cairo.context#fill()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#fill_extents</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#fill_extents():reduce</code></div>
Computes a bounding box in user coordinates covering the area that would be affected, (the "inked" area), by a <code class="highlighter-rouge">cairo.context#fill()</code> operation given the current path and fill parameters. If the current path is empty, returns an empty rectangle ((0,0), (0,0)). Surface dimensions and clipping are not taken into account.
</p>
<p>
Contrast with <code class="highlighter-rouge">cairo.context#path_extents()</code>, which is similar, but returns non-zero extents for some paths with no inked area, (such as a simple line segment).
</p>
<p>
Note that <code class="highlighter-rouge">cairo.context#fill_extents()</code> must necessarily do more work to compute the precise inked areas in light of the fill rule, so <code class="highlighter-rouge">cairo.context#path_extents()</code> may be more desirable for sake of performance if the non-inked path extents are desired.
</p>
<p>
See <code class="highlighter-rouge">cairo.context#fill()</code>, <code class="highlighter-rouge">cairo.context#set_fill_rule()</code> and <code class="highlighter-rouge">cairo.context#fill_preserve()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#in_fill</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#in_fill(x:number, y:number)</code></div>
Tests whether the given point is inside the area that would be affected by a <code class="highlighter-rouge">cairo.context#fill()</code> operation given the current path and filling parameters. Surface dimensions and clipping are not taken into account.
</p>
<p>
See <code class="highlighter-rouge">cairo.context#fill()</code>, <code class="highlighter-rouge">cairo.context#set_fill_rule()</code> and <code class="highlighter-rouge">cairo.context#fill_preserve()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#mask</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#mask(pattern:cairo.pattern):reduce</code></div>
A drawing operator that paints the current source using the alpha channel of pattern as a mask. (Opaque areas of pattern are painted with the source, transparent areas are not painted.)
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#mask_surface</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#mask_surface(surface:cairo.surface, surface_x:number, surface_y:number):reduce</code></div>
A drawing operator that paints the current source using the alpha channel of surface as a mask. (Opaque areas of surface are painted with the source, transparent areas are not painted.)
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#paint</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#paint():reduce</code></div>
A drawing operator that paints the current source everywhere within the current clip region.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#paint_with_alpha</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#paint_with_alpha(alpha:number):reduce</code></div>
A drawing operator that paints the current source everywhere within the current clip region using a mask of constant alpha value alpha. The effect is similar to cairo.context#paint(), but the drawing is faded out using the alpha value.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#stroke</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#stroke():reduce</code></div>
A drawing operator that strokes the current path according to the current line width, line join, line cap, and dash settings. After <code class="highlighter-rouge">cairo.context#stroke()</code>, the current path will be cleared from the cairo context. See <code class="highlighter-rouge">cairo.context#set_line_width()</code>, <code class="highlighter-rouge">cairo.context#set_line_join()</code>, <code class="highlighter-rouge">cairo.context#set_line_cap()</code>, <code class="highlighter-rouge">cairo.context#set_dash()</code>, and <code class="highlighter-rouge">cairo.context#stroke_preserve()</code>.
</p>
<p>
Note: Degenerate segments and sub-paths are treated specially and provide a useful result. These can result in two different situations:
</p>
<ol>
<li>Zero-length "on" segments set in cairo.context#set_dash(). If the cap style is <code class="highlighter-rouge">cairo.LINE_CAP_ROUND</code> or <code class="highlighter-rouge">cairo.LINE_CAP_SQUARE</code> then these segments will be drawn as circular dots or squares respectively. In the case of <code class="highlighter-rouge">cairo.LINE_CAP_SQUARE</code>, the orientation of the squares is determined by the direction of the underlying path.</li>
<li>A sub-path created by <code class="highlighter-rouge">cairo.context#move_to()</code> followed by either a <code class="highlighter-rouge">cairo.context#close_path()</code> or one or more calls to <code class="highlighter-rouge">cairo.context#line_to()</code> to the same coordinate as the <code class="highlighter-rouge">cairo.context#move_to()</code>. If the cap style is <code class="highlighter-rouge">cairo.LINE_CAP_ROUND</code> then these sub-paths will be drawn as circular dots. Note that in the case of <code class="highlighter-rouge">cairo.LINE_CAP_SQUARE</code> a degenerate sub-path will not be drawn at all, (since the correct orientation is indeterminate).</li>
</ol>
<p>
In no case will a cap style of <code class="highlighter-rouge">cairo.LINE_CAP_BUTT</code> cause anything to be drawn in the case of either degenerate segments or sub-paths.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#stroke_preserve</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#stroke_preserve():reduce</code></div>
A drawing operator that strokes the current path according to the current line width, line join, line cap, and dash settings. Unlike <code class="highlighter-rouge">cairo.context#stroke()</code>, <code class="highlighter-rouge">cairo.context#stroke_preserve()</code> preserves the path within the cairo context.
</p>
<p>
See <code class="highlighter-rouge">cairo.context#set_line_width()</code>, <code class="highlighter-rouge">cairo.context#set_line_join()</code>, <code class="highlighter-rouge">cairo.context#set_line_cap()</code>, <code class="highlighter-rouge">cairo.context#set_dash()</code>, and <code class="highlighter-rouge">cairo.context#stroke_preserve()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#stroke_extents</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#stroke_extents()</code></div>
Computes a bounding box in user coordinates covering the area that would be affected, (the "inked" area), by a cairo.context#stroke() operation given the current path and stroke parameters. If the current path is empty, returns an empty rectangle ((0,0), (0,0)). Surface dimensions and clipping are not taken into account.
</p>
<p>
Note that if the line width is set to exactly zero, then <code class="highlighter-rouge">cairo.context#stroke_extents()</code> will return an empty rectangle. Contrast with <code class="highlighter-rouge">cairo.context#path_extents()</code> which can be used to compute the non-empty bounds as the line width approaches zero.
</p>
<p>
Note that <code class="highlighter-rouge">cairo.context#stroke_extents()</code> must necessarily do more work to compute the precise inked areas in light of the stroke parameters, so <code class="highlighter-rouge">cairo.context#path_extents()</code> may be more desirable for sake of performance if non-inked path extents are desired.
</p>
<p>
See <code class="highlighter-rouge">cairo.context#stroke()</code>, <code class="highlighter-rouge">cairo.context#set_line_width()</code>, <code class="highlighter-rouge">cairo.context#set_line_join()</code>, <code class="highlighter-rouge">cairo.context#set_line_cap()</code>, <code class="highlighter-rouge">cairo.context#set_dash()</code>, and <code class="highlighter-rouge">cairo.context#stroke_preserve()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#in_stroke</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#in_stroke(x:number, y:number)</code></div>
Tests whether the given point is inside the area that would be affected by a <code class="highlighter-rouge">cairo.context#stroke()</code> operation given the current path and stroking parameters. Surface dimensions and clipping are not taken into account. See <code class="highlighter-rouge">cairo.context#stroke()</code>, <code class="highlighter-rouge">cairo.context#set_line_width()</code>, <code class="highlighter-rouge">cairo.context#set_line_join()</code>, <code class="highlighter-rouge">cairo.context#set_line_cap()</code>, <code class="highlighter-rouge">cairo.context#_set_dash()</code>, and <code class="highlighter-rouge">cairo.context#stroke_preserve()</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#copy_page</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#copy_page():reduce</code></div>
Emits the current page for backends that support multiple pages, but doesn't clear it, so, the contents of the current page will be retained for the next page too. Use <code class="highlighter-rouge">cairo.cairo#show_page()</code> if you want to get an empty page after the emission.
</p>
<p>
This is a convenience function that simply calls <code class="highlighter-rouge">cairo.context#surface_copy_page()</code> on cr's target.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#show_page</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#show_page():reduce</code></div>
Emits and clears the current page for backends that support multiple pages. Use <code class="highlighter-rouge">cairo.context#copy_page()</code> if you don't want to clear the page.
</p>
<p>
This is a convenience function that simply calls <code class="highlighter-rouge">cairo.context#surface_show_page()</code> on cr's target.
</p>
<h4><span class="caption-index-4">10.2.1.2</span><a name="anchor-10-2-1-2"></a>Types and Values</h4>
<p>
<code class="highlighter-rouge">cairo.antialias</code>
</p>
<ul>
<li><code class="highlighter-rouge">cairo.ANTIALIAS_DEFAULT</code></li>
<li><code class="highlighter-rouge">cairo.ANTIALIAS_NONE</code></li>
<li><code class="highlighter-rouge">cairo.ANTIALIAS_GRAY</code></li>
<li><code class="highlighter-rouge">cairo.ANTIALIAS_SUBPIXEL</code></li>
<li><code class="highlighter-rouge">cairo.ANTIALIAS_FAST</code></li>
<li><code class="highlighter-rouge">cairo.ANTIALIAS_GOOD</code></li>
<li><code class="highlighter-rouge">cairo.ANTIALIAS_BEST</code></li>
</ul>
<p>
<code class="highlighter-rouge">cairo.fill_fule</code>
</p>
<ul>
<li><code class="highlighter-rouge">cairo.FILL_RULE_WINDING</code></li>
<li><code class="highlighter-rouge">cairo.FILL_RULE_EVEN_ODD</code></li>
</ul>
<p>
<code class="highlighter-rouge">cairo.line_cap</code>
</p>
<ul>
<li><code class="highlighter-rouge">cairo.LINE_CAP_BUTT</code></li>
<li><code class="highlighter-rouge">cairo.LINE_CAP_ROUND</code></li>
<li><code class="highlighter-rouge">cairo.LINE_CAP_SQUARE</code></li>
</ul>
<p>
<code class="highlighter-rouge">cairo.line_join</code>
</p>
<ul>
<li><code class="highlighter-rouge">cairo.LINE_JOIN_MITER</code></li>
<li><code class="highlighter-rouge">cairo.LINE_JOIN_ROUND</code></li>
<li><code class="highlighter-rouge">cairo.LINE_JOIN_BEVEL</code></li>
</ul>
<p>
<code class="highlighter-rouge">cairo.operator</code>
</p>
<ul>
<li><code class="highlighter-rouge">cairo.OPERATOR_CLEAR</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_SOURCE</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_OVER</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_IN</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_OUT</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_ATOP</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_DEST</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_DEST_OVER</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_DEST_IN</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_DEST_OUT</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_DEST_ATOP</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_XOR</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_ADD</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_SATURATE</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_MULTIPLY</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_SCREEN</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_OVERLAY</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_DARKEN</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_LIGHTEN</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_COLOR_DODGE</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_COLOR_BURN</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_HARD_LIGHT</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_SOFT_LIGHT</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_DIFFERENCE</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_EXCLUSION</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_HSL_HUE</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_HSL_SATURATION</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_HSL_COLOR</code></li>
<li><code class="highlighter-rouge">cairo.OPERATOR_HSL_LUMINOSITY</code></li>
</ul>
<h3><span class="caption-index-3">10.2.2</span><a name="anchor-10-2-2"></a>Paths - Creating paths and manipulating path data</h3>
<h4><span class="caption-index-4">10.2.2.1</span><a name="anchor-10-2-2-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.context#copy_path</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#copy_path()</code></div>
Creates a copy of the current path and returns it to the user as a <code class="highlighter-rouge">cairo.path</code>. See <code class="highlighter-rouge">cairo_path_data_t</code> for hints on how to iterate over the returned data structure.
</p>
<p>
The result will have no data (data==nullptr and num_data==0), if either of the following conditions hold:
</p>
<ol>
<li>If there is insufficient memory to copy the path. In this case path-&gt;status will be set to <code class="highlighter-rouge">cairo.STATUS_NO_MEMORY</code>.</li>
<li>If cr is already in an error state. In this case <code class="highlighter-rouge">path.status</code> will contain the same status that would be returned by <code class="highlighter-rouge">cairo.context#status()</code>.</li>
</ol>
<p>
<div><strong style="text-decoration:underline">cairo.context#copy_path_flat</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#copy_path_flat()</code></div>
Gets a flattened copy of the current path and returns it to the user as a cairo.path. See cairo_path_data_t for hints on how to iterate over the returned data structure.
</p>
<p>
This function is like <code class="highlighter-rouge">cairo.context#copy_path()</code> except that any curves in the path will be approximated with piecewise-linear approximations, (accurate to within the current tolerance value). That is, the result is guaranteed to not have any elements of type <code class="highlighter-rouge">cairo.PATH_CURVE_TO</code> which will instead be replaced by a series of <code class="highlighter-rouge">cairo.PATH_LINE_TO</code> elements.
</p>
<p>
The result will have no data (data==nullptr and num_data==0), if either of the following conditions hold:
</p>
<ol>
<li>If there is insufficient memory to copy the path. In this case path.status will be set to <code class="highlighter-rouge">cairo.STATUS_NO_MEMORY</code>.</li>
<li>If cr is already in an error state. In this case path-&gt;status will contain the same status that would be returned by <code class="highlighter-rouge">cairo.context#status()</code>.</li>
</ol>
<p>
<div><strong style="text-decoration:underline">cairo.context#append_path</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#append_path(path:cairo.path):reduce</code></div>
Append the path onto the current path. The path may be either the return value from one of <code class="highlighter-rouge">cairo.context#copy_path()</code> or <code class="highlighter-rouge">cairo.context#copy_path_flat()</code> or it may be constructed manually. See <code class="highlighter-rouge">cairo.path</code> for details on how the path data structure should be initialized, and note that <code class="highlighter-rouge">path.status</code> must be initialized to <code class="highlighter-rouge">cairo.STATUS_SUCCESS</code>.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#has_current_point</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#has_current_point()</code></div>
Returns whether a current point is defined on the current path. See cairo.context#get_current_point() for details on the current point.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_current_point</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_current_point()</code></div>
Gets the current point of the current path, which is conceptually the final point reached by the path so far.
</p>
<p>
The current point is returned in the user-space coordinate system. If there is no defined current point or if cr is in an error status, x and y will both be set to 0.0. It is possible to check this in advance with cairo.context#has_current_point().
</p>
<p>
Most path construction functions alter the current point. See the following for details on how they affect the current point: cairo.context#new_path(), cairo.context#new_sub_path(), cairo.context#append_path(), cairo.context#close_path(), cairo.context#move_to(), cairo.context#line_to(), cairo.context#curve_to(), cairo.context#rel_move_to(), cairo.context#rel_line_to(), cairo.context#rel_curve_to(), cairo.context#arc(), cairo.context#arc_negative(), cairo.context#rectangle(), cairo.context#text_path(), cairo.context#glyph_path(), cairo.context#stroke_to_path().
</p>
<p>
Some functions use and alter the current point but do not otherwise change current path: cairo.context#show_text().
</p>
<p>
Some functions unset the current path and as a result, current point: cairo.context#fill(), cairo.context#stroke().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#new_path</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#new_path():reduce</code></div>
Clears the current path. After this call there will be no path and no current point.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#new_sub_path</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#new_sub_path():reduce</code></div>
Begin a new sub-path. Note that the existing path is not affected. After this call there will be no current point.
</p>
<p>
In many cases, this call is not needed since new sub-paths are frequently started with cairo.context#move_to().
</p>
<p>
A call to cairo.context#new_sub_path() is particularly useful when beginning a new sub-path with one of the cairo.context#arc() calls. This makes things easier as it is no longer necessary to manually compute the arc's initial coordinates for a call to cairo.context#move_to().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#close_path</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#close_path():reduce</code></div>
Adds a line segment to the path from the current point to the beginning of the current sub-path, (the most recent point passed to cairo.context#move_to()), and closes this sub-path. After this call the current point will be at the joined endpoint of the sub-path.
</p>
<p>
The behavior of cairo.context#close_path() is distinct from simply calling cairo.context#line_to() with the equivalent coordinate in the case of stroking. When a closed sub-path is stroked, there are no caps on the ends of the sub-path. Instead, there is a line join connecting the final and initial segments of the sub-path.
</p>
<p>
If there is no current point before the call to cairo.context#close_path(), this function will have no effect.
</p>
<p>
Note: As of cairo version 1.2.4 any call to cairo.context#close_path() will place an explicit MOVE_TO element into the path immediately after the CLOSE_PATH element, (which can be seen in cairo.context#copy_path() for example). This can simplify path processing in some cases as it may not be necessary to save the "last move_to point" during processing as the MOVE_TO immediately after the CLOSE_PATH will provide that point.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#arc</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#arc(xc:number, yc:number, radius:number, angle1?:number, angle2?:number):map:reduce:[deg]</code></div>
Adds a circular arc of the given radius to the current path. The arc is centered at (xc, yc), begins at angle1 and proceeds in the direction of increasing angles to end at angle2. If angle2 is less than angle1 it will be progressively increased by 2*M_PI until it is greater than angle1.
</p>
<p>
If there is a current point, an initial line segment will be added to the path to connect the current point to the beginning of the arc. If this initial line is undesired, it can be avoided by calling cairo.context#new_sub_path() before calling cairo.context#arc().
</p>
<p>
Angles are measured in radians. An angle of 0.0 is in the direction of the positive X axis (in user space). An angle of math.pi/2.0 radians (90 degrees) is in the direction of the positive Y axis (in user space). Angles increase in the direction from the positive X axis toward the positive Y axis. So with the default transformation matrix, angles increase in a clockwise direction.
</p>
<p>
(To convert from degrees to radians, use degrees * (math.pi / 180.).)
</p>
<p>
This function gives the arc in the direction of increasing angles; see cairo.context#arc_negative() to get the arc in the direction of decreasing angles.
</p>
<p>
The arc is circular in user space. To achieve an elliptical arc, you can scale the current transformation matrix by different amounts in the X and Y directions. For example, to draw an ellipse in the box given by x, y, width, height:
</p>
<p>
cr.save() cr.translate(x + width / 2., y + height / 2.) cr.scale(width / 2., height / 2.) cr.arc(0., 0., 1., 0., 2 * math.pi)cr.restore()
</p>
<p>
<em>Gura:</em> If attribute :deg is specified, angle1 and angle2 are represented in degrees instead of radians.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#arc_negative</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#arc_negative(xc:number, yc:number, radius:number, angle1?:number, angle2?:number):map:reduce:[deg]</code></div>
Adds a circular arc of the given radius to the current path. The arc is centered at (xc, yc), begins at angle1 and proceeds in the direction of decreasing angles to end at angle2. If angle2 is greater than angle1 it will be progressively decreased by 2*math.pi until it is less than angle1.
</p>
<p>
See cairo.context#arc() for more details. This function differs only in the direction of the arc between the two angles.
</p>
<p>
<em>Gura:</em> If attribute :deg is specified, angle1 and angle2 are represented in degrees instead of radians.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#curve_to</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#curve_to(x1:number, y1:number, x2:number, y2:number, x3:number, y3:number):map:reduce</code></div>
Adds a cubic Bezier spline to the path from the current point to position (x3, y3) in user-space coordinates, using (x1, y1) and (x2, y2) as the control points. After this call the current point will be (x3, y3).
</p>
<p>
If there is no current point before the call to cairo.context#curve_to() this function will behave as if preceded by a call to cr.move_to(x1, y1).
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#line_to</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#line_to(x:number, y:number):map:reduce</code></div>
Adds a line to the path from the current point to position (x, y) in user-space coordinates. After this call the current point will be (x, y).
</p>
<p>
If there is no current point before the call to cairo.context#line_to() this function will behave as cr.move_to(x, y).
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#move_to</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#move_to(x:number, y:number):map:reduce</code></div>
Begin a new sub-path. After this call the current point will be (x, y).
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#rectangle</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#rectangle(x:number, y:number, width:number, height:number):map:reduce</code></div>
Adds a closed sub-path rectangle of the given size to the current path at position (x, y) in user-space coordinates.
</p>
<p>
This function is logically equivalent to:
</p>
<p>
cr.move_to(x, y) cr.rel_line_to(width, 0) cr.rel_line_to(0, height) cr.rel_line_to(-width, 0) cr.close_path()
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#text_path</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#text_path(text:string):map:reduce</code></div>
Adds closed paths for text to the current path. The generated path if filled, achieves an effect similar to that of cairo.context#show_text().
</p>
<p>
Text conversion and positioning is done similar to cairo.context#show_text().
</p>
<p>
Like cairo.context#show_text(), After this call the current point is moved to the origin of where the next glyph would be placed in this same progression. That is, the current point will be at the origin of the final glyph offset by its advance values. This allows for chaining multiple calls to to cairo.context#text_path() without having to set current point in between.
</p>
<p>
Note: The cairo.context#text_path() function call is part of what the cairo designers call the "toy" text API. It is convenient for short demos and simple programs, but it is not expected to be adequate for serious text-using applications. See cairo.context#glyph_path() for the "real" text path API in cairo.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#rel_curve_to</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#rel_curve_to(dx1:number, dy1:number, dx2:number, dy2:number, dx3:number, dy3:number):map:reduce</code></div>
Relative-coordinate version of cairo.context#curve_to(). All offsets are relative to the current point. Adds a cubic Bezier spline to the path from the current point to a point offset from the current point by (dx3, dy3), using points offset by (dx1, dy1) and (dx2, dy2) as the control points. After this call the current point will be offset by (dx3, dy3).
</p>
<p>
Given a current point of (x, y), cr.rel_curve_to(dx1, dy1, dx2, dy2, dx3, dy3) is logically equivalent to cr.curve_to(x+dx1, y+dy1, x+dx2, y+dy2, x+dx3, y+dy3).
</p>
<p>
It is an error to call this function with no current point. Doing so will cause cr to shutdown with a status of cairo.STATUS_NO_CURRENT_POINT.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#rel_line_to</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#rel_line_to(dx:number, dy:number):map:reduce</code></div>
Relative-coordinate version of cairo.context#line_to(). Adds a line to the path from the current point to a point that is offset from the current point by (dx, dy) in user space. After this call the current point will be offset by (dx, dy).
</p>
<p>
Given a current point of (x, y), cr.rel_line_to(dx, dy) is logically equivalent to cr.line_to(x + dx, y + dy).
</p>
<p>
It is an error to call this function with no current point. Doing so will cause cr to shutdown with a status of cairo.STATUS_NO_CURRENT_POINT.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#rel_move_to</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#rel_move_to(dx:number, dy:number):map:reduce</code></div>
Begin a new sub-path. After this call the current point will offset by (dx, dy).
</p>
<p>
Given a current point of (x, y), cr.rel_move_to(dx, dy) is logically equivalent to cr.move_to(x + dx, y + dy).
</p>
<p>
It is an error to call this function with no current point. Doing so will cause cr to shutdown with a status of cairo.STATUS_NO_CURRENT_POINT.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#path_extents</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#path_extents()</code></div>
Computes a bounding box in user-space coordinates covering the points on the current path. If the current path is empty, returns an empty rectangle ((0,0), (0,0)). Stroke parameters, fill rule, surface dimensions and clipping are not taken into account.
</p>
<p>
Contrast with cairo.context#fill_extents() and cairo.context#stroke_extents() which return the extents of only the area that would be "inked" by the corresponding drawing operations.
</p>
<p>
The result of cairo.context#path_extents() is defined as equivalent to the limit of cairo.context#stroke_extents() with cairo.LINE_CAP_ROUND as the line width approaches 0.0, (but never reaching the empty-rectangle returned by cairo.context#stroke_extents() for a line width of 0.0).
</p>
<p>
Specifically, this means that zero-area sub-paths such as cairo.context#move_to();cairo.context#line_to() segments, (even degenerate cases where the coordinates to both calls are identical), will be considered as contributing to the extents. However, a lone cairo.context#move_to() will not contribute to the results of cairo.context#path_extents().
</p>
<h4><span class="caption-index-4">10.2.2.2</span><a name="anchor-10-2-2-2"></a>Types and Values</h4>
<h3><span class="caption-index-3">10.2.3</span><a name="anchor-10-2-3"></a>cairo.pattern - Sources for drawing</h3>
<h4><span class="caption-index-4">10.2.3.1</span><a name="anchor-10-2-3-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#add_color_stop_rgb</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#add_color_stop_rgb(offset:number, red:number, green:number, blue:number):reduce</code></div>
Adds an opaque color stop to a gradient pattern. The offset specifies the location along the gradient's control vector. For example, a linear gradient's control vector is from (x0,y0) to (x1,y1) while a radial gradient's control vector is from any point on the start circle to the corresponding point on the end circle.
</p>
<p>
The color is specified in the same way as in cairo.context#set_source_rgb().
</p>
<p>
If two (or more) stops are specified with identical offset values, they will be sorted according to the order in which the stops are added, (stops added earlier will compare less than stops added later). This can be useful for reliably making sharp color transitions instead of the typical blend.
</p>
<p>
Note: If the pattern is not a gradient pattern, (eg. a linear or radial pattern), then the pattern will be put into an error status with a status of cairo.STATUS_PATTERN_TYPE_MISMATCH.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#add_color_stop_rgba</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#add_color_stop_rgba(offset:number, red:number, green:number, blue:number, alpha:number):reduce</code></div>
Adds a translucent color stop to a gradient pattern. The offset specifies the location along the gradient's control vector. For example, a linear gradient's control vector is from (x0,y0) to (x1,y1) while a radial gradient's control vector is from any point on the start circle to the corresponding point on the end circle.
</p>
<p>
The color is specified in the same way as in cairo.context#set_source_rgba().
</p>
<p>
If two (or more) stops are specified with identical offset values, they will be sorted according to the order in which the stops are added, (stops added earlier will compare less than stops added later). This can be useful for reliably making sharp color transitions instead of the typical blend.
</p>
<p>
Note: If the pattern is not a gradient pattern, (eg. a linear or radial pattern), then the pattern will be put into an error status with a status of cairo.STATUS_PATTERN_TYPE_MISMATCH.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#get_color_stop_count</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#get_color_stop_count()</code></div>
Gets the number of color stops specified in the given gradient pattern.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#get_color_stop_rgba</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#get_color_stop_rgba(index:number)</code></div>
Gets the color and offset information at the given index for a gradient pattern. Values of index are 0 to 1 less than the number returned by cairo.pattern#get_color_stop_count().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern.create_rgb</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern.create_rgb(red:number, green:number, blue:number):static {block?}</code></div>
Creates a new cairo.pattern corresponding to an opaque color. The color components are floating point numbers in the range 0 to 1. If the values passed in are outside that range, they will be clamped.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern.create_rgba</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern.create_rgba(red:number, green:number, blue:number, alpha:number):static {block?}</code></div>
Creates a new cairo,pattern corresponding to a translucent color. The color components are floating point numbers in the range 0 to 1. If the values passed in are outside that range, they will be clamped.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#get_rgba</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#get_rgba()</code></div>
Gets the solid color for a solid color pattern.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern.create_for_surface</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern.create_for_surface(surface:cairo.surface):static {block?}</code></div>
Create a new cairo.pattern for the given surface.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#get_surface</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#get_surface()</code></div>
Gets the surface of a surface pattern. The reference returned in surface is owned by the pattern; the caller should call cairo_surface_reference() if the surface is to be retained.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern.create_linear</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern.create_linear(x0:number, y0:number, x1:number, y1:number):static {block?}</code></div>
Create a new linear gradient cairo.pattern along the line defined by (x0, y0) and (x1, y1). Before using the gradient pattern, a number of color stops should be defined using cairo.pattern#add_color_stop_rgb() or cairo.pattern#add_color_stop_rgba().
</p>
<p>
Note: The coordinates here are in pattern space. For a new pattern, pattern space is identical to user space, but the relationship between the spaces can be changed with cairo.pattern#set_matrix().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#get_linear_points</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#get_linear_points()</code></div>
Gets the gradient endpoints for a linear gradient.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern.create_radial</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern.create_radial(cx0:number, cy0:number, radius0:number, cx1:number, cy1:number, radius1:number):static {block?}</code></div>
Creates a new radial gradient cairo_pattern_t between the two circles defined by (cx0, cy0, radius0) and (cx1, cy1, radius1). Before using the gradient pattern, a number of color stops should be defined using cairo.pattern#add_color_stop_rgb() or cairo.pattern#add_color_stop_rgba().
</p>
<p>
Note: The coordinates here are in pattern space. For a new pattern, pattern space is identical to user space, but the relationship between the spaces can be changed with cairo.pattern#set_matrix().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#get_radial_circles</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#get_radial_circles()</code></div>
Gets the gradient endpoint circles for a radial gradient, each specified as a center coordinate and a radius.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.mesh_pattern.create</strong></div>
<div style="margin-bottom:1em"><code>cairo.mesh_pattern.create():static {block?}</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.mesh_pattern#begin_patch</strong></div>
<div style="margin-bottom:1em"><code>cairo.mesh_pattern#begin_patch():reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.mesh_pattern#end_patch</strong></div>
<div style="margin-bottom:1em"><code>cairo.mesh_pattern#end_patch():reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.mesh_pattern#move_to</strong></div>
<div style="margin-bottom:1em"><code>cairo.mesh_pattern#move_to(x:number, y:number):reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.mesh_pattern#line_to</strong></div>
<div style="margin-bottom:1em"><code>cairo.mesh_pattern#line_to(x:number, y:number):reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.mesh_pattern#curve_to</strong></div>
<div style="margin-bottom:1em"><code>cairo.mesh_pattern#curve_to(x1:number, y1:number, x2:number, y2:number, x3:number, y3:number):reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.mesh_pattern#set_control_point</strong></div>
<div style="margin-bottom:1em"><code>cairo.mesh_pattern#set_control_point(point_num:number, x:number, y:number):reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.mesh_pattern#set_corner_color_rgb</strong></div>
<div style="margin-bottom:1em"><code>cairo.mesh_pattern#set_corner_color_rgb(corner_num:number, red:number, green:number, blue:number):reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.mesh_pattern#set_corner_color_rgba</strong></div>
<div style="margin-bottom:1em"><code>cairo.mesh_pattern#set_corner_color_rgba(corner_num:number, red:number, green:number, blue:number, alpha:number):reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#status</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#status()</code></div>
Checks whether an error has previously occurred for this pattern.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#set_extend</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#set_extend(extend:number):reduce</code></div>
Sets the mode to be used for drawing outside the area of a pattern. See cairo_extend_t for details on the semantics of each extend strategy.
</p>
<p>
The default extend mode is cairo.EXTEND_NONE for surface patterns and cairo.EXTEND_PAD for gradient patterns.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#get_extend</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#get_extend()</code></div>
Gets the current extend mode for a pattern. See cairo_extend_t for details on the semantics of each extend strategy.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#set_filter</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#set_filter(filter:number):reduce</code></div>
Sets the filter to be used for resizing when using this pattern. See cairo_filter_t for details on each filter.
</p>
<ul>
<li><p>
Note that you might want to control filtering even when you do not have an explicit cairo.pattern object, (for example when using cairo.context#set_source_surface()). In these cases, it is convenient to use cairo.context#get_source() to get access to the pattern that cairo creates implicitly. For example:
</p>
<p>
cr.set_source_surface(image, x, y) cr.get_source().set_filter(cairo.FILTER_NEAREST)
</p>
</li>
</ul>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#get_filter</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#get_filter()</code></div>
Gets the current filter for a pattern. See cairo_filter_t for details on each filter.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#set_matrix</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#set_matrix(array:array@double):reduce</code></div>
Sets the pattern's transformation matrix to matrix. This matrix is a transformation from user space to pattern space.
</p>
<p>
When a pattern is first created it always has the identity matrix for its transformation matrix, which means that pattern space is initially identical to user space.
</p>
<p>
Important: Please note that the direction of this transformation matrix is from user space to pattern space. This means that if you imagine the flow from a pattern to user space (and on to device space), then coordinates in that flow will be transformed by the inverse of the pattern matrix.
</p>
<p>
For example, if you want to make a pattern appear twice as large as it does by default the correct code to use is:
</p>
<p>
cairo_matrix_init_scale (&amp;matrix, 0.5, 0.5); cairo_pattern_set_matrix (pattern, &amp;matrix);
</p>
<p>
Meanwhile, using values of 2.0 rather than 0.5 in the code above would cause the pattern to appear at half of its default size.
</p>
<p>
Also, please note the discussion of the user-space locking semantics of cairo.context#set_source().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#get_matrix</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#get_matrix()</code></div>
Stores the pattern's transformation matrix into matrix.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.pattern#get_type</strong></div>
<div style="margin-bottom:1em"><code>cairo.pattern#get_type()</code></div>
This function returns the type a pattern. See cairo_pattern_type_t for available types.
</p>
<h4><span class="caption-index-4">10.2.3.2</span><a name="anchor-10-2-3-2"></a>Types and Values</h4>
<p>
<code class="highlighter-rouge">cairo.extend</code>
</p>
<ul>
<li><code class="highlighter-rouge">cairo.EXTEND_NONE</code></li>
<li><code class="highlighter-rouge">cairo.EXTEND_REPEAT</code></li>
<li><code class="highlighter-rouge">cairo.EXTEND_REFLECT</code></li>
<li><code class="highlighter-rouge">cairo.EXTEND_PAD</code></li>
</ul>
<p>
<code class="highlighter-rouge">cairo.filter</code>
</p>
<ul>
<li><code class="highlighter-rouge">cairo.FILTER_FAST</code></li>
<li><code class="highlighter-rouge">cairo.FILTER_GOOD</code></li>
<li><code class="highlighter-rouge">cairo.FILTER_BEST</code></li>
<li><code class="highlighter-rouge">cairo.FILTER_NEAREST</code></li>
<li><code class="highlighter-rouge">cairo.FILTER_BILINEAR</code></li>
<li><code class="highlighter-rouge">cairo.FILTER_GAUSSIAN</code></li>
</ul>
<p>
<code class="highlighter-rouge">cairo.pattern_type</code>
</p>
<ul>
<li><code class="highlighter-rouge">cairo.PATTERN_TYPE_SOLID</code></li>
<li><code class="highlighter-rouge">cairo.PATTERN_TYPE_SURFACE</code></li>
<li><code class="highlighter-rouge">cairo.PATTERN_TYPE_LINEAR</code></li>
<li><code class="highlighter-rouge">cairo.PATTERN_TYPE_RADIAL</code></li>
<li><code class="highlighter-rouge">cairo.PATTERN_TYPE_MESH</code></li>
<li><code class="highlighter-rouge">cairo.PATTERN_TYPE_RASTER_SOURCE</code></li>
</ul>
<h3><span class="caption-index-3">10.2.4</span><a name="anchor-10-2-4"></a>Regions - Representing a pixel-aligned area</h3>
<p>
<code class="highlighter-rouge">cairo.region_overlap</code>
</p>
<ul>
<li><code class="highlighter-rouge">cairo.REGION_OVERLAP_IN</code></li>
<li><code class="highlighter-rouge">cairo.REGION_OVERLAP_OUT</code></li>
<li><code class="highlighter-rouge">cairo.REGION_OVERLAP_PART</code></li>
</ul>
<h4><span class="caption-index-4">10.2.4.1</span><a name="anchor-10-2-4-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.region.create</strong></div>
<div style="margin-bottom:1em"><code>cairo.region.create():static {block?}</code></div>
<div><strong style="text-decoration:underline">cairo.region.create_rectangle</strong></div>
<div style="margin-bottom:1em"><code>cairo.region.create_rectangle(rectangle:cairo.rectangle_int):static {block?}</code></div>
<div><strong style="text-decoration:underline">cairo.region.create_rectangles</strong></div>
<div style="margin-bottom:1em"><code>cairo.region.create_rectangles(rects[]:cairo.rectangle_int):static {block?}</code></div>
<div><strong style="text-decoration:underline">cairo.region#copy</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#copy() {block?}</code></div>
<div><strong style="text-decoration:underline">cairo.region#status</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#status()</code></div>
<div><strong style="text-decoration:underline">cairo.region#get_extents</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#get_extents()</code></div>
<div><strong style="text-decoration:underline">cairo.region#get_rectangle</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#get_rectangle(nth:number)</code></div>
<div><strong style="text-decoration:underline">cairo.region#is_empty</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#is_empty()</code></div>
<div><strong style="text-decoration:underline">cairo.region#contains_point</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#contains_point(x:number, y:number)</code></div>
<div><strong style="text-decoration:underline">cairo.region#contains_rectangle</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#contains_rectangle(rectangle:cairo.rectangle_int)</code></div>
<div><strong style="text-decoration:underline">cairo.region#equal</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#equal(region:cairo.region)</code></div>
<div><strong style="text-decoration:underline">cairo.region#translate</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#translate(dx:number, dy:number)</code></div>
<div><strong style="text-decoration:underline">cairo.region#intersect</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#intersect(other:cairo.region)</code></div>
<div><strong style="text-decoration:underline">cairo.region#intersect_rectangle</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#intersect_rectangle(rectangle:cairo.rectangle_int)</code></div>
<div><strong style="text-decoration:underline">cairo.region#union</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#union(other:cairo.region)</code></div>
<div><strong style="text-decoration:underline">cairo.region#union_rectangle</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#union_rectangle(rectangle:cairo.rectangle_int)</code></div>
<div><strong style="text-decoration:underline">cairo.region#xor</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#xor(other:cairo.region)</code></div>
<div><strong style="text-decoration:underline">cairo.region#xor_rectangle</strong></div>
<div style="margin-bottom:1em"><code>cairo.region#xor_rectangle(rectangle:cairo.rectangle_int)</code></div>

</p>
<h4><span class="caption-index-4">10.2.4.2</span><a name="anchor-10-2-4-2"></a>Types and Values</h4>
<h3><span class="caption-index-3">10.2.5</span><a name="anchor-10-2-5"></a>Transformations - Manipulating the current transformation matrix</h3>
<h4><span class="caption-index-4">10.2.5.1</span><a name="anchor-10-2-5-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.context#translate</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#translate(tx:number, ty:number):reduce</code></div>
Modifies the current transformation matrix (CTM) by translating the user-space origin by (tx, ty). This offset is interpreted as a user-space coordinate according to the CTM in place before the new call to cairo.context#translate(). In other words, the translation of the user-space origin takes place after any existing transformation.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#scale</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#scale(sx:number, sy:number):reduce</code></div>
Modifies the current transformation matrix (CTM) by scaling the X and Y user-space axes by sx and sy respectively. The scaling of the axes takes place after any existing transformation of user space.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#rotate</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#rotate(angle:number):reduce:[deg]</code></div>
Modifies the current transformation matrix (CTM) by rotating the user-space axes by angle radians. The rotation of the axes takes places after any existing transformation of user space. The rotation direction for positive angles is from the positive X axis toward the positive Y axis.
</p>
<p>
<em>Gura:</em> If attribute :deg is specified, angle is represented in degrees instead of radians.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#transform</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#transform(array:array@double):reduce</code></div>
Modifies the current transformation matrix (CTM) by applying matrix as an additional transformation. The new transformation of user space takes place after any existing transformation.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_matrix</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_matrix(array:array@double):reduce</code></div>
Modifies the current transformation matrix (CTM) by setting it equal to matrix.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_matrix</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_matrix()</code></div>
Stores the current transformation matrix (CTM) into matrix.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#identity_matrix</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#identity_matrix():reduce</code></div>
Resets the current transformation matrix (CTM) by setting it equal to the identity matrix. That is, the user-space and device-space axes will be aligned and one user-space unit will transform to one device-space unit.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#user_to_device</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#user_to_device(x:number, y:number)</code></div>
Transform a coordinate from user space to device space by multiplying the given point by the current transformation matrix (CTM).
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#user_to_device_distance</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#user_to_device_distance(dx:number, dy:number)</code></div>
Transform a distance vector from user space to device space. This function is similar to cairo.context#user_to_device() except that the translation components of the CTM will be ignored when transforming (dx,dy).
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#device_to_user</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#device_to_user(x:number, y:number)</code></div>
Transform a coordinate from device space to user space by multiplying the given point by the inverse of the current transformation matrix (CTM).
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#device_to_user_distance</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#device_to_user_distance(dx:number, dy:number)</code></div>
Transform a distance vector from device space to user space. This function is similar to cairo.context#device_to_user() except that the translation components of the inverse CTM will be ignored when transforming (dx,dy).
</p>
<h3><span class="caption-index-3">10.2.6</span><a name="anchor-10-2-6"></a>text - Rendering text and glyphs</h3>
<h4><span class="caption-index-4">10.2.6.1</span><a name="anchor-10-2-6-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.context#select_font_face</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#select_font_face(family:string, slant:number, weight:number):reduce</code></div>
Note: The cairo.context#select_font_face() function call is part of what the cairo designers call the "toy" text API. It is convenient for short demos and simple programs, but it is not expected to be adequate for serious text-using applications.
</p>
<p>
Selects a family and style of font from a simplified description as a family name, slant and weight. Cairo provides no operation to list available family names on the system (this is a "toy", remember), but the standard CSS2 generic family names, ("serif", "sans-serif", "cursive", "fantasy", "monospace"), are likely to work as expected.
</p>
<p>
If family starts with the string "cairo:", or if no native font backends are compiled in, cairo will use an internal font family. The internal font family recognizes many modifiers in the family string, most notably, it recognizes the string "monospace". That is, the family name "cairo:monospace" will use the monospace version of the internal font family.
</p>
<p>
For "real" font selection, see the font-backend-specific font_face_create functions for the font backend you are using. (For example, if you are using the freetype-based cairo-ft font backend, see cairo_ft_font_face_create_for_ft_face() or cairo_ft_font_face_create_for_pattern().) The resulting font face could then be used with cairo.scaled_font_create() and cairo.context#set_scaled_font().
</p>
<p>
Similarly, when using the "real" font support, you can call directly into the underlying font system, (such as fontconfig or freetype), for operations such as listing available fonts, etc.
</p>
<p>
It is expected that most applications will need to use a more comprehensive font handling and text layout library, (for example, pango), in conjunction with cairo.
</p>
<p>
If text is drawn without a call to cairo.context#select_font_face(), (nor cairo.context#set_font_face() nor cairo.context#set_scaled_font()), the default family is platform-specific, but is essentially "sans-serif". Default slant is cairo.FONT_SLANT_NORMAL, and default weight is cairo.FONT_WEIGHT_NORMAL.
</p>
<p>
This function is equivalent to a call to cairo.toy_font_face.create() followed by cairo.context#set_font_face().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_font_size</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_font_size(size:number):reduce</code></div>
Sets the current font matrix to a scale by a factor of size, replacing any font matrix previously set with cairo.context#set_font_size() or cairo.context#set_font_matrix(). This results in a font size of size user space units. (More precisely, this matrix will result in the font's em-square being a size by size square in user space.)
</p>
<p>
If text is drawn without a call to cairo.context#set_font_size(), (nor cairo.context#set_font_matrix() nor cairo.context#set_scaled_font()), the default font size is 10.0.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_font_matrix</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_font_matrix(array:array@double):reduce</code></div>
Sets the current font matrix to matrix. The font matrix gives a transformation from the design space of the font (in this space, the em-square is 1 unit by 1 unit) to user space. Normally, a simple scale is used (see cairo_set_font_size()), but a more complex font matrix can be used to shear the font or stretch it unequally along the two axes.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_font_matrix</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_font_matrix()</code></div>
Stores the current font matrix into matrix. See cairo.context#set_font_matrix().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_font_options</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_font_options(options:cairo.font_options):reduce</code></div>
Sets a set of custom font rendering options for the cairo_t. Rendering options are derived by merging these options with the options derived from underlying surface; if the value in options has a default value (like cairo.ANTIALIAS_DEFAULT), then the value from the surface is used.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_font_options</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_font_options() {block?}</code></div>
Retrieves font rendering options set via cairo.context#set_font_options. Note that the returned options do not include any options derived from the underlying surface; they are literally the options passed to cairo.context#set_font_options().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_font_face</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_font_face(font_face:cairo.font_face):reduce</code></div>
Replaces the current cairo_font_face_t object in the cairo_t with font_face. The replaced font face in the cairo_t will be destroyed if there are no other references to it.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_font_face</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_font_face() {block?}</code></div>
Gets the current font face for a cairo_t.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#set_scaled_font</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#set_scaled_font(scaled_font:cairo.scaled_font):reduce</code></div>
Replaces the current font face, font matrix, and font options in the cairo_t with those of the cairo_scaled_font_t. Except for some translation, the current CTM of the cairo_t should be the same as that of the cairo_scaled_font_t, which can be accessed using cairo.context#scaled_font_get_ctm().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#get_scaled_font</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#get_scaled_font() {block?}</code></div>
Gets the current scaled font for a cairo_t.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#show_text</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#show_text(text:string):map:reduce</code></div>
A drawing operator that generates the shape from a string of UTF-8 characters, rendered according to the current font_face, font_size (font_matrix), and font_options.
</p>
<p>
This function first computes a set of glyphs for the string of text. The first glyph is placed so that its origin is at the current point. The origin of each subsequent glyph is offset from that of the previous glyph by the advance values of the previous glyph.
</p>
<p>
After this call the current point is moved to the origin of where the next glyph would be placed in this same progression. That is, the current point will be at the origin of the final glyph offset by its advance values. This allows for easy display of a single logical string with multiple calls to cairo.context#show_text().
</p>
<p>
Note: The cairo.context#show_text() function call is part of what the cairo designers call the "toy" text API. It is convenient for short demos and simple programs, but it is not expected to be adequate for serious text-using applications. See cairo.context#show_glyphs() for the "real" text display API in cairo.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#show_glyphs</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#show_glyphs(glyphs:cairo.glyph):reduce</code></div>
A drawing operator that generates the shape from an array of glyphs, rendered according to the current font face, font size (font matrix), and font options.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#font_extents</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#font_extents() {block?}</code></div>
Gets the font extents for the currently selected font.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#text_extents</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#text_extents(text:string):map {block?}</code></div>
Gets the extents for a string of text. The extents describe a user-space rectangle that encloses the "inked" portion of the text, (as it would be drawn by cairo.context#show_text()). Additionally, the x_advance and y_advance values indicate the amount by which the current point would be advanced by cairo.context#show_text().
</p>
<p>
Note that whitespace characters do not directly contribute to the size of the rectangle (extents.width and extents.height). They do contribute indirectly by changing the position of non-whitespace characters. In particular, trailing whitespace characters are likely to not affect the size of the rectangle, though they will affect the x_advance and y_advance values.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.context#glyph_extents</strong></div>
<div style="margin-bottom:1em"><code>cairo.context#glyph_extents(glyphs:cairo.glyph) {block?}</code></div>
Gets the extents for an array of glyphs. The extents describe a user-space rectangle that encloses the "inked" portion of the glyphs, (as they would be drawn by cairo.context#show_glyphs()). Additionally, the x_advance and y_advance values indicate the amount by which the current point would be advanced by cairo.context#show_glyphs().
</p>
<p>
Note that whitespace glyphs do not contribute to the size of the rectangle (extents.width and extents.height).
</p>
<p>
<div><strong style="text-decoration:underline">cairo.toy_font_face.create</strong></div>
<div style="margin-bottom:1em"><code>cairo.toy_font_face.create(family:string, slant:number, weight:number):static {block?}</code></div>
Creates a font face from a triplet of family, slant, and weight. These font faces are used in implementation of the the cairo_t "toy" font API.
</p>
<p>
If family is the zero-length string "", the platform-specific default family is assumed. The default family then can be queried using cairo.toy_font_face#get_family().
</p>
<p>
The cairo.context#select_font_face() function uses this to create font faces. See that function for limitations and other details of toy font faces.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.toy_font_face#get_family</strong></div>
<div style="margin-bottom:1em"><code>cairo.toy_font_face#get_family()</code></div>
Gets the familly name of a toy font.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.toy_font_face#get_slant</strong></div>
<div style="margin-bottom:1em"><code>cairo.toy_font_face#get_slant()</code></div>
Gets the slant a toy font.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.toy_font_face#get_weight</strong></div>
<div style="margin-bottom:1em"><code>cairo.toy_font_face#get_weight()</code></div>
Gets the weight a toy font.
</p>
<h4><span class="caption-index-4">10.2.6.2</span><a name="anchor-10-2-6-2"></a>Types and Values</h4>
<h3><span class="caption-index-3">10.2.7</span><a name="anchor-10-2-7"></a>Raster Sources - Supplying arbitary image data</h3>
<h4><span class="caption-index-4">10.2.7.1</span><a name="anchor-10-2-7-1"></a>Functions</h4>
<h2><span class="caption-index-2">10.3</span><a name="anchor-10-3"></a>Fonts</h2>
<h3><span class="caption-index-3">10.3.1</span><a name="anchor-10-3-1"></a>cairo.font_face - Base class for font faces</h3>
<h4><span class="caption-index-4">10.3.1.1</span><a name="anchor-10-3-1-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.3.2</span><a name="anchor-10-3-2"></a>cairo.scaled_font - Font face at particular size and options</h3>
<h4><span class="caption-index-4">10.3.2.1</span><a name="anchor-10-3-2-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.scaled_font.create</strong></div>
<div style="margin-bottom:1em"><code>cairo.scaled_font.create(font_face:cairo.font_face, font_matrix:array@double, ctm:array@double, options):static {block?}</code></div>

</p>
<h3><span class="caption-index-3">10.3.3</span><a name="anchor-10-3-3"></a>cairo_font_options_t - How a font should be rendered</h3>
<h4><span class="caption-index-4">10.3.3.1</span><a name="anchor-10-3-3-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.font_options.create</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options.create():static {block?}</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#status</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#status()</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#merge</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#merge(other:cairo.font_options):void</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#hash</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#hash()</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#equal</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#equal(other:cairo.font_options)</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#set_antialias</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#set_antialias(antialias:number):void</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#get_antialias</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#get_antialias()</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#set_subpixel_order</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#set_subpixel_order(subpixel_order:number):void</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#get_subpixel_order</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#get_subpixel_order()</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#set_hint_style</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#set_hint_style(hint_style:number):void</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#get_hint_style</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#get_hint_style()</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#set_hint_metrics</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#set_hint_metrics(hint_metrics:number):void</code></div>
<div><strong style="text-decoration:underline">cairo.font_options#get_hint_metrics</strong></div>
<div style="margin-bottom:1em"><code>cairo.font_options#get_hint_metrics()</code></div>

</p>
<h3><span class="caption-index-3">10.3.4</span><a name="anchor-10-3-4"></a>FreeType Fonts - Font support for FreeType</h3>
<h4><span class="caption-index-4">10.3.4.1</span><a name="anchor-10-3-4-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.3.5</span><a name="anchor-10-3-5"></a>Win32 Fonts - Font support for Microsoft Windows</h3>
<h4><span class="caption-index-4">10.3.5.1</span><a name="anchor-10-3-5-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.3.6</span><a name="anchor-10-3-6"></a>Quartz (CGFont) Fonts - Font support via CGFont on OS X</h3>
<h4><span class="caption-index-4">10.3.6.1</span><a name="anchor-10-3-6-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.3.7</span><a name="anchor-10-3-7"></a>User Fonts - Font support with font data provided by the user</h3>
<h4><span class="caption-index-4">10.3.7.1</span><a name="anchor-10-3-7-1"></a>Functions</h4>
<h2><span class="caption-index-2">10.4</span><a name="anchor-10-4"></a>Surfaces</h2>
<h3><span class="caption-index-3">10.4.1</span><a name="anchor-10-4-1"></a>cairo.device - interface to underlying rendering system</h3>
<h4><span class="caption-index-4">10.4.1.1</span><a name="anchor-10-4-1-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.device#status</strong></div>
<div style="margin-bottom:1em"><code>cairo.device#status()</code></div>
<div><strong style="text-decoration:underline">cairo.device#finish</strong></div>
<div style="margin-bottom:1em"><code>cairo.device#finish():reduce</code></div>
<div><strong style="text-decoration:underline">cairo.device#flush</strong></div>
<div style="margin-bottom:1em"><code>cairo.device#flush():reduce</code></div>
<div><strong style="text-decoration:underline">cairo.device#get_type</strong></div>
<div style="margin-bottom:1em"><code>cairo.device#get_type()</code></div>
<div><strong style="text-decoration:underline">cairo.device#acquire</strong></div>
<div style="margin-bottom:1em"><code>cairo.device#acquire()</code></div>
<div><strong style="text-decoration:underline">cairo.device#release</strong></div>
<div style="margin-bottom:1em"><code>cairo.device#release():void</code></div>

</p>
<h3><span class="caption-index-3">10.4.2</span><a name="anchor-10-4-2"></a>cairo.surface - Base class for surfaces</h3>
<h4><span class="caption-index-4">10.4.2.1</span><a name="anchor-10-4-2-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.surface.create_similar</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface.create_similar(other:cairo.surface, content:number, width:number, height:number):static {block?}</code></div>
Create a new surface that is as compatible as possible with an existing surface. For example the new surface will have the same fallback resolution and font options as other. Generally, the new surface will also use the same backend as other, unless that is not possible for some reason. The type of the returned surface may be examined with cairo.surface#get_type().
</p>
<p>
Initially the surface contents are all 0 (transparent if contents have transparency, black otherwise.)
</p>
<p>
Use cairo.surface.create_similar_image() if you need an image surface which can be painted quickly to the target surface.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface.create_similar_image</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface.create_similar_image(other:cairo.surface, format:number, width:number, height:number):static {block?}</code></div>
Create a new image surface that is as compatible as possible for uploading to and the use in conjunction with an existing surface. However, this surface can still be used like any normal image surface.
</p>
<p>
Initially the surface contents are all 0 (transparent if contents have transparency, black otherwise.)
</p>
<p>
Use cairo.surface.create_similar() if you don't need an image surface.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface.create_for_rectangle</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface.create_for_rectangle(other:cairo.surface, format:number, width:number, height:number):static {block?}</code></div>
Create a new surface that is a rectangle within the target surface. All operations drawn to this surface are then clipped and translated onto the target surface. Nothing drawn via this sub-surface outside of its bounds is drawn onto the target surface, making this a useful method for passing constrained child surfaces to library routines that draw directly onto the parent surface, i.e. with no further backend allocations, double buffering or copies.
</p>
<p>
<em>Note:</em> The semantics of subsurfaces have not been finalized yet unless the rectangle is in full device units, is contained within the extents of the target surface, and the target or subsurface's device transforms are not changed.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#status</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#status()</code></div>
Checks whether an error has previously occurred for this surface.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#finish</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#finish():reduce</code></div>
This function finishes the surface and drops all references to external resources. For example, for the Xlib backend it means that cairo will no longer access the drawable, which can be freed. After calling cairo.surface#finish() the only valid operations on a surface are getting and setting user, referencing and destroying, and flushing and finishing it. Further drawing to the surface will not affect the surface but will instead trigger a cairo.STATUS_SURFACE_FINISHED error.
</p>
<p>
When the last call to cairo_surface_destroy() decreases the reference count to zero, cairo will call cairo_surface_finish() if it hasn't been called already, before freeing the resources associated with the surface.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#flush</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#flush():reduce</code></div>
Do any pending drawing for the surface and also restore any temporary modifications cairo has made to the surface's state. This function must be called before switching from drawing on the surface with cairo to drawing on it directly with native APIs. If the surface doesn't support direct access, then this function does nothing.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#get_device</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#get_device()</code></div>
This function returns the device for a surface. See cairo.device.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#get_font_options</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#get_font_options()</code></div>
Retrieves the default font rendering options for the surface. This allows display surfaces to report the correct subpixel order for rendering on them, print surfaces to disable hinting of metrics and so forth. The result can then be used with cairo.scaled_font.create().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#get_content</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#get_content()</code></div>
This function returns the content type of surface which indicates whether the surface contains color and/or alpha information. See cairo_content_t.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#mark_dirty</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#mark_dirty():reduce</code></div>
Tells cairo that drawing has been done to surface using means other than cairo, and that cairo should reread any cached areas. Note that you must call cairo.surface#flush() before doing such drawing.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#mark_dirty_rectangle</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#mark_dirty_rectangle(x:number, y:number, width:number, height:number):reduce</code></div>
Like cairo.surface#mark_dirty(), but drawing has been done only to the specified rectangle, so that cairo can retain cached contents for other parts of the surface.
</p>
<p>
Any cached clip set on the surface will be reset by this function, to make sure that future cairo calls have the clip set that they expect.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#set_device_offset</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#set_device_offset(x_offset:number, y_offset:number):reduce</code></div>
Sets an offset that is added to the device coordinates determined by the CTM when drawing to surface. One use case for this function is when we want to create a cairo.surface that redirects drawing for a portion of an onscreen surface to an offscreen surface in a way that is completely invisible to the user of the cairo API. Setting a transformation via cairo.context#translate() isn't sufficient to do this, since functions like cairo.context#device_to_user() will expose the hidden offset.
</p>
<p>
Note that the offset affects drawing to the surface as well as using the surface in a source pattern.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#get_device_offset</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#get_device_offset()</code></div>
This function returns the previous device offset set by cairo.surface#set_device_offset().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#set_fallback_resolution</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#set_fallback_resolution(x_pixels_per_inch:number, y_pixels_per_inch:number):reduce</code></div>
Set the horizontal and vertical resolution for image fallbacks.
</p>
<p>
When certain operations aren't supported natively by a backend, cairo will fallback by rendering operations to an image and then overlaying that image onto the output. For backends that are natively vector-oriented, this function can be used to set the resolution used for these image fallbacks, (larger values will result in more detailed images, but also larger file sizes).
</p>
<p>
Some examples of natively vector-oriented backends are the ps, pdf, and svg backends.
</p>
<p>
For backends that are natively raster-oriented, image fallbacks are still possible, but they are always performed at the native device resolution. So this function has no effect on those backends.
</p>
<p>
Note: The fallback resolution only takes effect at the time of completing a page (with cairo.context#show_page() or cairo.context#copy_page()) so there is currently no way to have more than one fallback resolution in effect on a single page.
</p>
<p>
The default fallback resoultion is 300 pixels per inch in both dimensions.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#get_fallback_resolution</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#get_fallback_resolution()</code></div>
This function returns the previous fallback resolution set by cairo.surface#set_fallback_resolution(), or default fallback resolution if never set.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#get_type</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#get_type()</code></div>
This function returns the type of the backend used to create a surface. See cairo_surface_type_t for available types.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#copy_page</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#copy_page():reduce</code></div>
Emits the current page for backends that support multiple pages, but doesn't clear it, so that the contents of the current page will be retained for the next page. Use cairo.surface#show_page() if you want to get an empty page after the emission.
</p>
<p>
There is a convenience function for this that takes a cairo.context, namely cairo.context#copy_page().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#show_page</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#show_page():reduce</code></div>
Emits and clears the current page for backends that support multiple pages. Use cairo.surface#copy_page() if you don't want to clear the page.
</p>
<p>
There is a convenience function for this that takes a cairo.context, namely cairo.context#show_page().
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#has_show_text_glyphs</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#has_show_text_glyphs()</code></div>
Returns whether the surface supports sophisticated cairo.context#show_text_glyphs() operations. That is, whether it actually uses the provided text and cluster data to a cairo.context#show_text_glyphs() call.
</p>
<p>
Note: Even if this function returns false, a cairo.context#show_text_glyphs() operation targeted at surface will still succeed. It just will act like a cairo.context#show_glyphs() operation. Users can use this function to avoid computing UTF-8 text and cluster mapping if the target surface does not use it.
</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#set_mime_data</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#set_mime_data():reduce</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#get_mime_data</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#get_mime_data()</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#supports_mime_type</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#supports_mime_type()</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#map_to_image</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#map_to_image(extents:cairo.rectangle_int)</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#unmap_image</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#unmap_image()</code></div>

</p>
<p>
<div><strong style="text-decoration:underline">cairo.surface#write_to_png</strong></div>
<div style="margin-bottom:1em"><code>cairo.surface#write_to_png(stream:stream:w):reduce</code></div>

</p>
<h3><span class="caption-index-3">10.4.3</span><a name="anchor-10-4-3"></a>Image Surfaces - Rendering to memory buffers</h3>
<h4><span class="caption-index-4">10.4.3.1</span><a name="anchor-10-4-3-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.image_surface.create</strong></div>
<div style="margin-bottom:1em"><code>cairo.image_surface.create(image:image):static {block?}</code></div>
<div><strong style="text-decoration:underline">cairo.image_surface.create_from_png</strong></div>
<div style="margin-bottom:1em"><code>cairo.image_surface.create_from_png(stream:stream:r):static {block?}</code></div>
<div><strong style="text-decoration:underline">cairo.image_surface#get_format</strong></div>
<div style="margin-bottom:1em"><code>cairo.image_surface#get_format()</code></div>
<div><strong style="text-decoration:underline">cairo.image_surface#get_width</strong></div>
<div style="margin-bottom:1em"><code>cairo.image_surface#get_width()</code></div>
<div><strong style="text-decoration:underline">cairo.image_surface#get_height</strong></div>
<div style="margin-bottom:1em"><code>cairo.image_surface#get_height()</code></div>
<div><strong style="text-decoration:underline">cairo.image_surface#get_stride</strong></div>
<div style="margin-bottom:1em"><code>cairo.image_surface#get_stride()</code></div>

</p>
<h3><span class="caption-index-3">10.4.4</span><a name="anchor-10-4-4"></a>PDF Surfaces - Rendering PDF documents</h3>
<h4><span class="caption-index-4">10.4.4.1</span><a name="anchor-10-4-4-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.pdf_surface.create</strong></div>
<div style="margin-bottom:1em"><code>cairo.pdf_surface.create(stream:stream:w, width_in_points:number, height_in_points:number):static {block?}</code></div>
<div><strong style="text-decoration:underline">cairo.pdf_surface#restrict_to_version</strong></div>
<div style="margin-bottom:1em"><code>cairo.pdf_surface#restrict_to_version(version:number):reduce</code></div>
<div><strong style="text-decoration:underline">cairo.pdf_surface#set_size</strong></div>
<div style="margin-bottom:1em"><code>cairo.pdf_surface#set_size(width_in_points:number, height_in_points:number):reduce</code></div>

</p>
<h3><span class="caption-index-3">10.4.5</span><a name="anchor-10-4-5"></a>PNG Support - Reading and writing PNG images</h3>
<h4><span class="caption-index-4">10.4.5.1</span><a name="anchor-10-4-5-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.4.6</span><a name="anchor-10-4-6"></a>PostScript Surfaces - Rendering PostScript documents</h3>
<h4><span class="caption-index-4">10.4.6.1</span><a name="anchor-10-4-6-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.4.7</span><a name="anchor-10-4-7"></a>Recording Surfaces - Records all drawing operations</h3>
<h4><span class="caption-index-4">10.4.7.1</span><a name="anchor-10-4-7-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.4.8</span><a name="anchor-10-4-8"></a>Win32 Surfaces - Microsoft Windows surface support</h3>
<h4><span class="caption-index-4">10.4.8.1</span><a name="anchor-10-4-8-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.4.9</span><a name="anchor-10-4-9"></a>SVG Surfaces - Rendering SVG documents</h3>
<h4><span class="caption-index-4">10.4.9.1</span><a name="anchor-10-4-9-1"></a>Functions</h4>
<p>
<div><strong style="text-decoration:underline">cairo.svg_surface.create</strong></div>
<div style="margin-bottom:1em"><code>cairo.svg_surface.create(stream:stream:w, width_in_points:number, height_in_points:number):static {block?}</code></div>
<div><strong style="text-decoration:underline">cairo.svg_surface#restrict_to_version</strong></div>
<div style="margin-bottom:1em"><code>cairo.svg_surface#restrict_to_version(version:number):reduce</code></div>

</p>
<h3><span class="caption-index-3">10.4.10</span><a name="anchor-10-4-10"></a>Quartz Surfaces - Rendering to Quartz surfaces</h3>
<h4><span class="caption-index-4">10.4.10.1</span><a name="anchor-10-4-10-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.4.11</span><a name="anchor-10-4-11"></a>XCB Surfaces - X Window System rendering using the XCB library</h3>
<h4><span class="caption-index-4">10.4.11.1</span><a name="anchor-10-4-11-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.4.12</span><a name="anchor-10-4-12"></a>XLib Surfaces - X Window System rendering using XLib</h3>
<h4><span class="caption-index-4">10.4.12.1</span><a name="anchor-10-4-12-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.4.13</span><a name="anchor-10-4-13"></a>XLib-XRender Backend - X Window System rendering using XLib and the X Render extension</h3>
<h4><span class="caption-index-4">10.4.13.1</span><a name="anchor-10-4-13-1"></a>Functions</h4>
<h3><span class="caption-index-3">10.4.14</span><a name="anchor-10-4-14"></a>Script Surfaces - Rendering to replayable scripts</h3>
<h4><span class="caption-index-4">10.4.14.1</span><a name="anchor-10-4-14-1"></a>Functions</h4>
<h2><span class="caption-index-2">10.5</span><a name="anchor-10-5"></a>Thanks</h2>
<p>
This module uses Cairo library which is distributed in the following site:
</p>
<p>
<a href="http://cairographics.org/">http://cairographics.org/</a>
</p>
{% endraw %}
