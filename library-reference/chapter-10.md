---
layout: page
lang: en
title: Gura Library Reference
---

{% raw %}
<h1><span class="caption-index-1">10</span><a name="anchor-10"></a>cairo Module</h1>
<p>
The <code>cairo</code> module provides methods to draw 2-D graphics using Cairo library. Official site of Cairo is <a href="http://cairographics.org/">http://cairographics.org/</a>.
</p>
<h2><span class="caption-index-2">10.1</span><a name="anchor-10-1"></a>Drawing</h2>
<h3><span class="caption-index-3">10.1.1</span><a name="anchor-10-1-1"></a>cairo_t - The cairo drawing context</h3>
<p>
<strong>cairo.context#status</strong>
</p>
<p>
<code>cairo.context#status()</code>
</p>
<p>
Checks whether an error has previously occurred for this context.
</p>
<p>
<strong>cairo.context#save</strong>
</p>
<p>
<code>cairo.context#save():reduce {block?}</code>
</p>
<p>
Makes a copy of the current state of cr and saves it on an internal stack of saved states for cr. When cairo.context#restore() is called, cr will be restored to the saved state. Multiple calls to cairo.context#save() and cairo.context#restore() can be nested; each call to cairo.context#restore() restores the state from the matching paired cairo.context#save().
</p>
<p>
It isn't necessary to clear all saved states before a cairo<em>t is freed.</em>If the reference count of a cairo<em>t drops to zero in response to a call to cairo.context#destroy(),</em>any saved states will be freed along with the cairo<em>t.</em>
</p>
<p>
<strong>cairo.context#restore</strong>
</p>
<p>
<code>cairo.context#restore():reduce</code>
</p>
<p>
Restores cr to the state saved by a preceding call to cairo.context#save() and removes that state from the stack of saved states.
</p>
<p>
<strong>cairo.context#get_target</strong>
</p>
<p>
<code>cairo.context#get_target()</code>
</p>
<p>
Gets the target surface for the cairo context as passed to cairo.context constructor.
</p>
<p>
<strong>cairo.context#push_group</strong>
</p>
<p>
<code>cairo.context#push_group():reduce</code>
</p>
<p>
Temporarily redirects drawing to an intermediate surface known as a group. The redirection lasts until the group is completed by a call to cairo.context#pop<em>group() or cairo.context#pop</em>group<em>to</em>source(). These calls provide the result of any drawing to the group as a pattern, (either as an explicit object, or set as the source pattern).
</p>
<p>
This group functionality can be convenient for performing intermediate compositing. One common use of a group is to render objects as opaque within the group, (so that they occlude each other), and then blend the result with translucence onto the destination.
</p>
<p>
Groups can be nested arbitrarily deep by making balanced calls to cairo.context#push<em>group()/cairo.context#pop</em>group(). Each call pushes/pops the new target group onto/from a stack.
</p>
<p>
The cairo.context#push<em>group() function calls cairo</em>save() so that any changes to the graphics state will not be visible outside the group, (the pop<em>group functions call cairo</em>restore()).
</p>
<p>
By default the intermediate group will have a content type of cairo.CONTENT<em>COLOR</em>ALPHA. Other content types can be chosen for the group by using cairo.context#push<em>group</em>with<em>content() instead.</em>
</p>
<p>
As an example, here is how one might fill and stroke a path with translucence, but without any portion of the fill being visible under the stroke:
</p>
<p>
<strong>cairo.context#push_group_with_content</strong>
</p>
<p>
<code>cairo.context#push_group_with_content(content:number):reduce</code>
</p>
<p>
Temporarily redirects drawing to an intermediate surface known as a group. The redirection lasts until the group is completed by a call to cairo.context#pop<em>group() or cairo.context#pop</em>group<em>to</em>source(). These calls provide the result of any drawing to the group as a pattern, (either as an explicit object, or set as the source pattern).
</p>
<p>
The group will have a content type of content. The ability to control this content type is the only distinction between this function and cairo.context#push<em>group()</em>which you should see for a more detailed description of group rendering.
</p>
<p>
<strong>cairo.context#pop_group</strong>
</p>
<p>
<code>cairo.context#pop_group()</code>
</p>
<p>
Terminates the redirection begun by a call to cairo.context#push<em>group() or cairo.context#push</em>group<em>with</em>content() and returns a new pattern containing the results of all drawing operations performed to the group.
</p>
<p>
The cairo.context#pop<em>group() function calls cairo</em>restore(), (balancing a call to cairo<em>save() by the push</em>group function), so that any changes to the graphics state will not be visible outside the group.
</p>
<p>
<strong>cairo.context#pop_group_to_source</strong>
</p>
<p>
<code>cairo.context#pop_group_to_source():reduce</code>
</p>
<p>
Terminates the redirection begun by a call to cairo.context#push<em>group() or cairo.context#push</em>group<em>with</em>content() and installs the resulting pattern as the source pattern in the given cairo context.
</p>
<p>
The cairo.context#pop<em>group() function calls cairo</em>restore(), (balancing a call to cairo<em>save() by the push</em>group function), so that any changes to the graphics state will not be visible outside the group.
</p>
<p>
<strong>cairo.context#get_group_target</strong>
</p>
<p>
<code>cairo.context#get_group_target()</code>
</p>
<p>
Gets the current destination surface for the context. This is either the original target surface as passed to cairo.context constructor or the target surface for the current group as started by the most recent call to cairo.context#push<em>group() or cairo.context#push</em>group<em>with</em>content().
</p>
<p>
<strong>cairo.context#set_source_rgb</strong>
</p>
<p>
<code>cairo.context#set_source_rgb(red:number, green:number, blue:number):reduce</code>
</p>
<p>
Sets the source pattern within cr to an opaque color. This opaque color will then be used for any subsequent drawing operation until a new source pattern is set.
</p>
<p>
The color components are floating point numbers in the range 0 to 1. If the values passed in are outside that range, they will be clamped.
</p>
<p>
The default source pattern is opaque black, (that is, it is equivalent to cr.set<em>source</em>rgb(0.0, 0.0, 0.0)).
</p>
<p>
<strong>cairo.context#set_source_rgba</strong>
</p>
<p>
<code>cairo.context#set_source_rgba(red:number, green:number, blue:number, alpha:number):reduce</code>
</p>
<p>
Sets the source pattern within cr to a translucent color. This color will then be used for any subsequent drawing operation until a new source pattern is set.
</p>
<p>
The color and alpha components are floating point numbers in the range 0 to 1. If the values passed in are outside that range, they will be clamped.
</p>
<p>
The default source pattern is opaque black, (that is, it is equivalent to cr.set<em>source</em>rgba(0.0, 0.0, 0.0, 1.0)).
</p>
<p>
<strong>cairo.context#set_source</strong>
</p>
<p>
<code>cairo.context#set_source(source:cairo.pattern):reduce</code>
</p>
<p>
Sets the source pattern within cr to source. This pattern will then be used for any subsequent drawing operation until a new source pattern is set.
</p>
<p>
Note: The pattern's transformation matrix will be locked to the user space in effect at the time of cairo.context#set<em>source().</em>This means that further modifications of the current transformation matrix will not affect the source pattern. See cairo.pattern#set<em>matrix().</em>
</p>
<p>
The default source pattern is a solid pattern that is opaque black, (that is, it is equivalent to cr.set<em>source</em>rgb(0.0, 0.0, 0.0)).
</p>
<p>
<strong>cairo.context#set_source_surface</strong>
</p>
<p>
<code>cairo.context#set_source_surface(surface:cairo.surface, x:number, y:number):reduce</code>
</p>
<p>
This is a convenience function for creating a pattern from surface and setting it as the source in cr with cairo.context#set<em>source().</em>
</p>
<p>
The x and y parameters give the user-space coordinate at which the surface origin should appear. (The surface origin is its upper-left corner before any transformation has been applied.) The x and y parameters are negated and then set as translation values in the pattern matrix.
</p>
<p>
Other than the initial translation pattern matrix, as described above, all other pattern attributes, (such as its extend mode), are set to the default values as in cairo.pattern.create<em>for</em>surface(). The resulting pattern can be queried with cairo.context#get<em>source() so that these attributes can be modified if desired,</em>(eg. to create a repeating pattern with cairo.pattern#set<em>extend()).</em>
</p>
<p>
<strong>cairo.context#get_source</strong>
</p>
<p>
<code>cairo.context#get_source()</code>
</p>
<p>
Gets the current source pattern for cr.
</p>
<p>
<strong>cairo.context#set_antialias</strong>
</p>
<p>
<code>cairo.context#set_antialias(antialias:number):reduce</code>
</p>
<p>
Set the antialiasing mode of the rasterizer used for drawing shapes. This value is a hint, and a particular backend may or may not support a particular value. At the current time, no backend supports cairo.ANTIALIAS<em>SUBPIXEL when drawing shapes.</em>
</p>
<p>
Note that this option does not affect text rendering, instead see cairo.font<em>options#set</em>antialias().
</p>
<p>
<strong>cairo.context#get_antialias</strong>
</p>
<p>
<code>cairo.context#get_antialias()</code>
</p>
<p>
Gets the current shape antialiasing mode, as set by cairo.context#set<em>antialias().</em>
</p>
<p>
<strong>cairo.context#set_dash</strong>
</p>
<p>
<code>cairo.context#set_dash(dashes[]:number, offset:number):reduce</code>
</p>
<p>
Sets the dash pattern to be used by cairo.context#stroke(). A dash pattern is specified by dashes, an array of positive values. Each value provides the length of alternate "on" and "off" portions of the stroke. The offset specifies an offset into the pattern at which the stroke begins.
</p>
<p>
Each "on" segment will have caps applied as if the segment were a separate sub-path. In particular, it is valid to use an "on" length of 0.0 with cairo.LINE<em>CAP</em>ROUND or cairo.LINE<em>CAP</em>SQUARE in order to distributed dots or squares along a path.
</p>
<p>
Note: The length values are in user-space units as evaluated at the time of stroking. This is not necessarily the same as the user space at the time of cairo.context#set<em>dash().</em>
</p>
<p>
If length of dashes is 0 dashing is disabled.
</p>
<p>
If length of dashes is 1 a symmetric pattern is assumed with alternating on and off portions of the size specified by the single value in dashes.
</p>
<p>
If any value in dashes is negative, or if all values are 0, then cr will be put into an error state with a status of cairo.STATUS<em>INVALID</em>DASH.
</p>
<p>
<strong>cairo.context#get_dash</strong>
</p>
<p>
<code>cairo.context#get_dash()</code>
</p>
<p>
Gets the current dash array.
</p>
<p>
<strong>cairo.context#set_fill_rule</strong>
</p>
<p>
<code>cairo.context#set_fill_rule(fill_rule:number):reduce</code>
</p>
<p>
Set the current fill rule within the cairo context. The fill rule is used to determine which regions are inside or outside a complex (potentially self-intersecting) path. The current fill rule affects both cairo.context#fill() and cairo.context#clip(). See cairo<em>fill</em>rule<em>t for details on the semantics of each available fill rule.</em>
</p>
<p>
The default fill rule is cairo.FILL<em>RULE</em>WINDING.
</p>
<p>
<strong>cairo.context#get_fill_rule</strong>
</p>
<p>
<code>cairo.context#get_fill_rule()</code>
</p>
<p>
Gets the current fill rule, as set by cairo.context#set<em>fill</em>rule().
</p>
<p>
<strong>cairo.context#set_line_cap</strong>
</p>
<p>
<code>cairo.context#set_line_cap(line_cap:number):reduce</code>
</p>
<p>
Sets the current line cap style within the cairo context. See cairo<em>line</em>cap<em>t for details about how the available line cap styles are drawn.</em>
</p>
<p>
As with the other stroke parameters, the current line cap style is examined by cairo.context#stroke(), cairo.context#stroke<em>extents(),</em>and cairo.context#stroke<em>to</em>path(), but does not have any effect during path construction.
</p>
<p>
The default line cap style is cairo.LINE<em>CAP</em>BUTT.
</p>
<p>
<strong>cairo.context#get_line_cap</strong>
</p>
<p>
<code>cairo.context#get_line_cap()</code>
</p>
<p>
Gets the current line cap style, as set by cairo.context#set<em>line</em>cap().
</p>
<p>
<strong>cairo.context#set_line_join</strong>
</p>
<p>
<code>cairo.context#set_line_join(line_join:number):reduce</code>
</p>
<p>
Sets the current line join style within the cairo context. See cairo<em>line</em>join<em>t for details about how the available line join styles are drawn.</em>
</p>
<p>
As with the other stroke parameters, the current line join style is examined by cairo.context#stroke(), cairo.context#stroke<em>extents(),</em>and cairo.context#stroke<em>to</em>path(), but does not have any effect during path construction.
</p>
<p>
The default line join style is cairo.LINE<em>JOIN</em>MITER.
</p>
<p>
<strong>cairo.context#get_line_join</strong>
</p>
<p>
<code>cairo.context#get_line_join()</code>
</p>
<p>
Gets the current line join style, as set by cairo.context#set<em>line</em>join().
</p>
<p>
<strong>cairo.context#set_line_width</strong>
</p>
<p>
<code>cairo.context#set_line_width(width:number):reduce</code>
</p>
<p>
Sets the current line width within the cairo context. The line width value specifies the diameter of a pen that is circular in user space, (though device-space pen may be an ellipse in general due to scaling/shear/rotation of the CTM).
</p>
<p>
Note: When the description above refers to user space and CTM it refers to the user space and CTM in effect at the time of the stroking operation, not the user space and CTM in effect at the time of the call to cairo.context#set<em>line</em>width(). The simplest usage makes both of these spaces identical. That is, if there is no change to the CTM between a call to cairo.context#set<em>line</em>width() and the stroking operation, then one can just pass user-space values to cairo.context#set<em>line</em>width() and ignore this note.
</p>
<p>
As with the other stroke parameters, the current line width is examined by cairo.context#stroke(), cairo.context#stroke<em>extents(),</em>and cairo.context#stroke<em>to</em>path(), but does not have any effect during path construction.
</p>
<p>
The default line width value is 2.0.
</p>
<p>
<strong>cairo.context#get_line_width</strong>
</p>
<p>
<code>cairo.context#get_line_width()</code>
</p>
<p>
This function returns the current line width value exactly as set by cairo.context#set<em>line</em>width(). Note that the value is unchanged even if the CTM has changed between the calls to cairo.context#set<em>line</em>width() and cairo.context#get<em>line</em>width().
</p>
<p>
<strong>cairo.context#set_miter_limit</strong>
</p>
<p>
<code>cairo.context#set_miter_limit(limit:number):reduce</code>
</p>
<p>
Sets the current miter limit within the cairo context.
</p>
<p>
If the current line join style is set to cairo.LINE<em>JOIN</em>MITER (see cairo<em>set</em>line<em>join()), the miter limit is used to determine whether the lines should be joined with a bevel instead of a miter.</em>Cairo divides the length of the miter by the line width. If the result is greater than the miter limit, the style is converted to a bevel.
</p>
<p>
As with the other stroke parameters, the current line miter limit is examined by cairo.context#stroke(), cairo.context#stroke<em>extents(),</em>and cairo.context#stroke<em>to</em>path(), but does not have any effect during path construction.
</p>
<p>
The default miter limit value is 10.0, which will convert joins with interior angles less than 11 degrees to bevels instead of miters. For reference, a miter limit of 2.0 makes the miter cutoff at 60 degrees, and a miter limit of 1.414 makes the cutoff at 90 degrees.
</p>
<p>
A miter limit for a desired angle can be computed as: miter limit = 1/sin(angle/2)
</p>
<p>
<strong>cairo.context#get_miter_limit</strong>
</p>
<p>
<code>cairo.context#get_miter_limit()</code>
</p>
<p>
Gets the current miter limit, as set by cairo.context#set<em>miter</em>limit().
</p>
<p>
<strong>cairo.context#set_operator</strong>
</p>
<p>
<code>cairo.context#set_operator(op:number):reduce</code>
</p>
<p>
Sets the compositing operator to be used for all drawing operations. See cairo<em>operator</em>t for details on the semantics of each available compositing operator.
</p>
<p>
The default operator is cairo.OPERATOR<em>OVER.</em>
</p>
<p>
<strong>cairo.context#get_operator</strong>
</p>
<p>
<code>cairo.context#get_operator()</code>
</p>
<p>
Gets the current compositing operator for a cairo context.
</p>
<p>
<strong>cairo.context#set_tolerance</strong>
</p>
<p>
<code>cairo.context#set_tolerance(tolerance:number):reduce</code>
</p>
<p>
Sets the tolerance used when converting paths into trapezoids. Curved segments of the path will be subdivided until the maximum deviation between the original path and the polygonal approximation is less than tolerance. The default value is 0.1. A larger value will give better performance, a smaller value, better appearance. (Reducing the value from the default value of 0.1 is unlikely to improve appearance significantly.) The accuracy of paths within Cairo is limited by the precision of its internal arithmetic, and the prescribed tolerance is restricted to the smallest representable internal value.
</p>
<p>
<strong>cairo.context#get_tolerance</strong>
</p>
<p>
<code>cairo.context#get_tolerance()</code>
</p>
<p>
Gets the current tolerance value, as set by cairo.context#set<em>tolerance().</em>
</p>
<p>
<strong>cairo.context#clip</strong>
</p>
<p>
<code>cairo.context#clip():reduce</code>
</p>
<p>
Establishes a new clip region by intersecting the current clip region with the current path as it would be filled by cairo.context#fill() and according to the current fill rule (see cairo.context#set<em>fill</em>rule()).
</p>
<p>
After cairo.context#clip(), the current path will be cleared from the cairo context.
</p>
<p>
The current clip region affects all drawing operations by effectively masking out any changes to the surface that are outside the current clip region.
</p>
<p>
Calling cairo.context#clip() can only make the clip region smaller, never larger. But the current clip is part of the graphics state, so a temporary restriction of the clip region can be achieved by calling cairo.context#clip() within a cairo.context#save()/cairo.context#restore() pair. The only other means of increasing the size of the clip region is cairo.context#reset<em>clip().</em>
</p>
<p>
<strong>cairo.context#clip_preserve</strong>
</p>
<p>
<code>cairo.context#clip_preserve():reduce</code>
</p>
<p>
Establishes a new clip region by intersecting the current clip region with the current path as it would be filled by cairo.context#fill() and according to the current fill rule (see cairo.context#set<em>fill</em>rule()). Unlike cairo.context#clip(), cairo.context#clip<em>preserve() preserves the path within the cairo context.</em>
</p>
<p>
The current clip region affects all drawing operations by effectively masking out any changes to the surface that are outside the current clip region.
</p>
<p>
Calling cairo.context#clip<em>preserve() can only make the clip region smaller, never larger.</em>But the current clip is part of the graphics state, so a temporary restriction of the clip region can be achieved by calling cairo.context#clip<em>preserve()</em>within a cairo.context#save()/cairo.context#restore() pair. The only other means of increasing the size of the clip region is cairo.context#reset<em>clip().</em>
</p>
<p>
<strong>cairo.context#clip_extents</strong>
</p>
<p>
<code>cairo.context#clip_extents()</code>
</p>
<p>
Computes a bounding box in user coordinates covering the area inside the current clip.
</p>
<p>
<strong>cairo.context#in_clip</strong>
</p>
<p>
<code>cairo.context#in_clip(x:number, y:number)</code>
</p>
<p>
Tests whether the given point is inside the area that would be visible through the current clip, i.e. the area that would be filled by a cairo.context#paint() operation.
</p>
<p>
See cairo.context#clip(), and cairo.context#clip<em>preserve().</em>
</p>
<p>
<strong>cairo.context#reset_clip</strong>
</p>
<p>
<code>cairo.context#reset_clip():reduce</code>
</p>
<p>
Reset the current clip region to its original, unrestricted state. That is, set the clip region to an infinitely large shape containing the target surface. Equivalently, if infinity is too hard to grasp, one can imagine the clip region being reset to the exact bounds of the target surface.
</p>
<p>
Note that code meant to be reusable should not call cairo<em>reset</em>clip() as it will cause results unexpected by higher-level code which calls cairo.context#clip(). Consider using cairo.context#save() and cairo.context#restore() around cairo.context#clip() as a more robust means of temporarily restricting the clip region.
</p>
<p>
<strong>cairo.context#copy_clip_rectangle_list</strong>
</p>
<p>
<code>cairo.context#copy_clip_rectangle_list()</code>
</p>
<p>
Gets the current clip region as a list of rectangles in user coordinates.
</p>
<p>
The status in the list may be cairo.STATUS<em>CLIP</em>NOT<em>REPRESENTABLE</em>to indicate that the clip region cannot be represented as a list of user-space rectangles. The status may have other values to indicate other errors.
</p>
<p>
<strong>cairo.context#fill</strong>
</p>
<p>
<code>cairo.context#fill():reduce</code>
</p>
<p>
A drawing operator that fills the current path according to the current fill rule, (each sub-path is implicitly closed before being filled). After cairo.context#fill(), the current path will be cleared from the cairo context. See cairo.context#set<em>fill</em>rule() and cairo.context#fill<em>preserve().</em>
</p>
<p>
<strong>cairo.context#fill_preserve</strong>
</p>
<p>
<code>cairo.context#fill_preserve():reduce</code>
</p>
<p>
A drawing operator that fills the current path according to the current fill rule, (each sub-path is implicitly closed before being filled). Unlike cairo.context#fill(), cairo.context#fill<em>preserve() preserves the path within the cairo context.</em>
</p>
<p>
See cairo.context#set<em>fill</em>rule() and cairo.context#fill().
</p>
<p>
<strong>cairo.context#fill_extents</strong>
</p>
<p>
<code>cairo.context#fill_extents():reduce</code>
</p>
<p>
Computes a bounding box in user coordinates covering the area that would be affected, (the "inked" area), by a cairo.context#fill() operation given the current path and fill parameters. If the current path is empty, returns an empty rectangle ((0,0), (0,0)). Surface dimensions and clipping are not taken into account.
</p>
<p>
Contrast with cairo.context#path<em>extents(), which is similar,</em>but returns non-zero extents for some paths with no inked area, (such as a simple line segment).
</p>
<p>
Note that cairo.context#fill<em>extents() must necessarily do more work to compute the precise inked areas in light of the fill rule,</em>so cairo.context#path<em>extents() may be more desirable for sake of performance if the non-inked path extents are desired.</em>
</p>
<p>
See cairo.context#fill(), cairo.context#set<em>fill</em>rule() and cairo.context#fill<em>preserve().</em>
</p>
<p>
<strong>cairo.context#in_fill</strong>
</p>
<p>
<code>cairo.context#in_fill(x:number, y:number)</code>
</p>
<p>
Tests whether the given point is inside the area that would be affected by a cairo.context#fill() operation given the current path and filling parameters. Surface dimensions and clipping are not taken into account.
</p>
<p>
See cairo.context#fill(), cairo.context#set<em>fill</em>rule() and cairo.context#fill<em>preserve().</em>
</p>
<p>
<strong>cairo.context#mask</strong>
</p>
<p>
<code>cairo.context#mask(pattern:cairo.pattern):reduce</code>
</p>
<p>
A drawing operator that paints the current source using the alpha channel of pattern as a mask. (Opaque areas of pattern are painted with the source, transparent areas are not painted.)
</p>
<p>
<strong>cairo.context#mask_surface</strong>
</p>
<p>
<code>cairo.context#mask_surface(surface:cairo.surface, surface_x:number, surface_y:number):reduce</code>
</p>
<p>
A drawing operator that paints the current source using the alpha channel of surface as a mask. (Opaque areas of surface are painted with the source, transparent areas are not painted.)
</p>
<p>
<strong>cairo.context#paint</strong>
</p>
<p>
<code>cairo.context#paint():reduce</code>
</p>
<p>
A drawing operator that paints the current source everywhere within the current clip region.
</p>
<p>
<strong>cairo.context#paint_with_alpha</strong>
</p>
<p>
<code>cairo.context#paint_with_alpha(alpha:number):reduce</code>
</p>
<p>
A drawing operator that paints the current source everywhere within the current clip region using a mask of constant alpha value alpha. The effect is similar to cairo.context#paint(), but the drawing is faded out using the alpha value.
</p>
<p>
<strong>cairo.context#stroke</strong>
</p>
<p>
<code>cairo.context#stroke():reduce</code>
</p>
<p>
A drawing operator that strokes the current path according to the current line width, line join, line cap, and dash settings. After cairo.context#stroke(), the current path will be cleared from the cairo context. See cairo.context#set<em>line</em>width(), cairo.context#set<em>line</em>join(), cairo.context#set<em>line</em>cap(), cairo.context#set<em>dash(), and cairo.context#stroke</em>preserve().
</p>
<p>
Note: Degenerate segments and sub-paths are treated specially and provide a useful result. These can result in two different situations:
</p>
<ol>
<li>Zero-length "on" segments set in cairo.context#set<em>dash().</em> If the cap style is cairo.LINE<em>CAP</em>ROUND or cairo.LINE<em>CAP</em>SQUARE then these segments will be drawn as circular dots or squares respectively. In the case of cairo.LINE<em>CAP</em>SQUARE, the orientation of the squares is determined by the direction of the underlying path.</li>
<li>A sub-path created by cairo.context#move<em>to() followed by either a cairo.context#close</em>path() or one or more calls to cairo.context#line<em>to() to the same coordinate as the cairo.context#move</em>to(). If the cap style is cairo.LINE<em>CAP</em>ROUND then these sub-paths will be drawn as circular dots. Note that in the case of cairo.LINE<em>CAP</em>SQUARE a degenerate sub-path will not be drawn at all, (since the correct orientation is indeterminate).</li>
</ol>
<p>
In no case will a cap style of cairo.LINE<em>CAP</em>BUTT cause anything to be drawn in the case of either degenerate segments or sub-paths.
</p>
<p>
<strong>cairo.context#stroke_preserve</strong>
</p>
<p>
<code>cairo.context#stroke_preserve():reduce</code>
</p>
<p>
A drawing operator that strokes the current path according to the current line width, line join, line cap, and dash settings. Unlike cairo.context#stroke(), cairo.context#stroke<em>preserve() preserves the path within the cairo context.</em>
</p>
<p>
See cairo.context#set<em>line</em>width(), cairo.context#set<em>line</em>join(), cairo.context#set<em>line</em>cap(), cairo.context#set<em>dash(), and cairo.context#stroke</em>preserve().
</p>
<p>
<strong>cairo.context#stroke_extents</strong>
</p>
<p>
<code>cairo.context#stroke_extents()</code>
</p>
<p>
Computes a bounding box in user coordinates covering the area that would be affected, (the "inked" area), by a cairo.context#stroke() operation given the current path and stroke parameters. If the current path is empty, returns an empty rectangle ((0,0), (0,0)). Surface dimensions and clipping are not taken into account.
</p>
<p>
Note that if the line width is set to exactly zero, then cairo.context#stroke<em>extents() will return an empty rectangle.</em>Contrast with cairo.context#path<em>extents() which can be used to compute the non-empty bounds as the line width approaches zero.</em>
</p>
<p>
Note that cairo.context#stroke<em>extents() must necessarily do more work to compute the precise inked areas in light of the stroke parameters,</em>so cairo.context#path<em>extents() may be more desirable for sake of performance if non-inked path extents are desired.</em>
</p>
<p>
See cairo.context#stroke(), cairo.context#set<em>line</em>width(), cairo.context#set<em>line</em>join(), cairo.context#set<em>line</em>cap(), cairo.context#set<em>dash(), and cairo.context#stroke</em>preserve().
</p>
<p>
<strong>cairo.context#in_stroke</strong>
</p>
<p>
<code>cairo.context#in_stroke(x:number, y:number)</code>
</p>
<p>
Tests whether the given point is inside the area that would be affected by a cairo.context#stroke() operation given the current path and stroking parameters. Surface dimensions and clipping are not taken into account. See cairo.context#stroke(), cairo.context#set<em>line</em>width(), cairo.context#set<em>line</em>join(), cairo.context#set<em>line</em>cap(), cairo.context#<em>set</em>dash(), and cairo.context#stroke<em>preserve().</em>
</p>
<p>
<strong>cairo.context#copy_page</strong>
</p>
<p>
<code>cairo.context#copy_page():reduce</code>
</p>
<p>
Emits the current page for backends that support multiple pages, but doesn't clear it, so, the contents of the current page will be retained for the next page too. Use cairo.cairo#show<em>page() if you want to get an empty page after the emission.</em>
</p>
<p>
This is a convenience function that simply calls cairo.context#surface<em>copy</em>page() on cr's target.
</p>
<p>
<strong>cairo.context#show_page</strong>
</p>
<p>
<code>cairo.context#show_page():reduce</code>
</p>
<p>
Emits and clears the current page for backends that support multiple pages. Use cairo.context#copy<em>page() if you don't want to clear the page.</em>
</p>
<p>
This is a convenience function that simply calls cairo.context#surface<em>show</em>page() on cr's target.
</p>
<h3><span class="caption-index-3">10.1.2</span><a name="anchor-10-1-2"></a>Paths - Creating paths and manipulating path data</h3>
<p>
<strong>cairo.context#copy_path</strong>
</p>
<p>
<code>cairo.context#copy_path()</code>
</p>
<p>
Creates a copy of the current path and returns it to the user as a cairo.path. See cairo<em>path</em>data<em>t for hints on how to iterate over the returned data structure.</em>
</p>
<p>
The result will have no data (data==NULL and num<em>data==0), if either of the following conditions hold:</em>
</p>
<ol>
<li>If there is insufficient memory to copy the path. In this case path-&gt;status will be set to cairo.STATUS<em>NO</em>MEMORY.</li>
<li>If cr is already in an error state. In this case path-&gt;status will contain the same status that would be returned by cairo.context#status().</li>
</ol>
<p>
<strong>cairo.context#copy_path_flat</strong>
</p>
<p>
<code>cairo.context#copy_path_flat()</code>
</p>
<p>
Gets a flattened copy of the current path and returns it to the user as a cairo.path. See cairo<em>path</em>data<em>t for hints on how to iterate over the returned data structure.</em>
</p>
<p>
This function is like cairo.context#copy<em>path() except that any curves in the path will be approximated with piecewise-linear approximations,</em>(accurate to within the current tolerance value). That is, the result is guaranteed to not have any elements of type cairo.PATH<em>CURVE</em>TO which will instead be replaced by a series of cairo.PATH<em>LINE</em>TO elements.
</p>
<p>
The result will have no data (data==NULL and num<em>data==0), if either of the following conditions hold:</em>
</p>
<ol>
<li>If there is insufficient memory to copy the path. In this case path-&gt;status will be set to cairo.STATUS<em>NO</em>MEMORY.</li>
<li>If cr is already in an error state. In this case path-&gt;status will contain the same status that would be returned by cairo.context#status().</li>
</ol>
<p>
<strong>cairo.context#append_path</strong>
</p>
<p>
<code>cairo.context#append_path(path:cairo.path):reduce</code>
</p>
<p>
Append the path onto the current path. The path may be either the return value from one of cairo.context#copy<em>path() or cairo.context#copy</em>path<em>flat() or it may be constructed manually.</em>See cairo<em>path</em>t for details on how the path data structure should be initialized, and note that path-&gt;status must be initialized to cairo.STATUS<em>SUCCESS.</em>
</p>
<p>
<strong>cairo.context#has_current_point</strong>
</p>
<p>
<code>cairo.context#has_current_point()</code>
</p>
<p>
Returns whether a current point is defined on the current path. See cairo.context#get<em>current</em>point() for details on the current point.
</p>
<p>
<strong>cairo.context#get_current_point</strong>
</p>
<p>
<code>cairo.context#get_current_point()</code>
</p>
<p>
Gets the current point of the current path, which is conceptually the final point reached by the path so far.
</p>
<p>
The current point is returned in the user-space coordinate system. If there is no defined current point or if cr is in an error status, x and y will both be set to 0.0. It is possible to check this in advance with cairo.context#has<em>current</em>point().
</p>
<p>
Most path construction functions alter the current point. See the following for details on how they affect the current point: cairo.context#new<em>path(), cairo.context#new</em>sub<em>path(), cairo.context#append</em>path(), cairo.context#close<em>path(), cairo.context#move</em>to(), cairo.context#line<em>to(), cairo.context#curve</em>to(), cairo.context#rel<em>move</em>to(), cairo.context#rel<em>line</em>to(), cairo.context#rel<em>curve</em>to(), cairo.context#arc(), cairo.context#arc<em>negative(), cairo.context#rectangle(), cairo.context#text</em>path(), cairo.context#glyph<em>path(), cairo.context#stroke</em>to<em>path().</em>
</p>
<p>
Some functions use and alter the current point but do not otherwise change current path: cairo.context#show<em>text().</em>
</p>
<p>
Some functions unset the current path and as a result, current point: cairo.context#fill(), cairo.context#stroke().
</p>
<p>
<strong>cairo.context#new_path</strong>
</p>
<p>
<code>cairo.context#new_path():reduce</code>
</p>
<p>
Clears the current path. After this call there will be no path and no current point.
</p>
<p>
<strong>cairo.context#new_sub_path</strong>
</p>
<p>
<code>cairo.context#new_sub_path():reduce</code>
</p>
<p>
Begin a new sub-path. Note that the existing path is not affected. After this call there will be no current point.
</p>
<p>
In many cases, this call is not needed since new sub-paths are frequently started with cairo.context#move<em>to().</em>
</p>
<p>
A call to cairo.context#new<em>sub</em>path() is particularly useful when beginning a new sub-path with one of the cairo.context#arc() calls. This makes things easier as it is no longer necessary to manually compute the arc's initial coordinates for a call to cairo.context#move<em>to().</em>
</p>
<p>
<strong>cairo.context#close_path</strong>
</p>
<p>
<code>cairo.context#close_path():reduce</code>
</p>
<p>
Adds a line segment to the path from the current point to the beginning of the current sub-path, (the most recent point passed to cairo.context#move<em>to()), and closes this sub-path.</em>After this call the current point will be at the joined endpoint of the sub-path.
</p>
<p>
The behavior of cairo.context#close<em>path() is distinct from simply calling cairo.context#line</em>to() with the equivalent coordinate in the case of stroking. When a closed sub-path is stroked, there are no caps on the ends of the sub-path. Instead, there is a line join connecting the final and initial segments of the sub-path.
</p>
<p>
If there is no current point before the call to cairo.context#close<em>path(), this function will have no effect.</em>
</p>
<p>
Note: As of cairo version 1.2.4 any call to cairo.context#close<em>path() will place an explicit MOVE</em>TO element into the path immediately after the CLOSE<em>PATH element,</em>(which can be seen in cairo.context#copy<em>path() for example).</em>This can simplify path processing in some cases as it may not be necessary to save the "last move<em>to point" during processing as the MOVE</em>TO immediately after the CLOSE<em>PATH will provide that point.</em>
</p>
<p>
<strong>cairo.context#arc</strong>
</p>
<p>
<code>cairo.context#arc(xc:number, yc:number, radius:number, angle1?:number, angle2?:number):map:reduce:[deg]</code>
</p>
<p>
Adds a circular arc of the given radius to the current path. The arc is centered at (xc, yc), begins at angle1 and proceeds in the direction of increasing angles to end at angle2. If angle2 is less than angle1 it will be progressively increased by 2<em>M_PI until it is greater than angle1.</em>
</p>
<p>
If there is a current point, an initial line segment will be added to the path to connect the current point to the beginning of the arc. If this initial line is undesired, it can be avoided by calling cairo.context#new<em>sub</em>path() before calling cairo.context#arc().
</p>
<p>
Angles are measured in radians. An angle of 0.0 is in the direction of the positive X axis (in user space). An angle of math.pi/2.0 radians (90 degrees) is in the direction of the positive Y axis (in user space). Angles increase in the direction from the positive X axis toward the positive Y axis. So with the default transformation matrix, angles increase in a clockwise direction.
</p>
<p>
(To convert from degrees to radians, use degrees <em> (math.pi / 180.).)</em>
</p>
<p>
This function gives the arc in the direction of increasing angles; see cairo.context#arc<em>negative() to get the arc in the direction of decreasing angles.</em>
</p>
<p>
The arc is circular in user space. To achieve an elliptical arc, you can scale the current transformation matrix by different amounts in the X and Y directions. For example, to draw an ellipse in the box given by x, y, width, height:
</p>
<p>
cr.save() cr.translate(x + width / 2., y + height / 2.) cr.scale(width / 2., height / 2.) cr.arc(0., 0., 1., 0., 2 <em> math.pi)</em>cr.restore()
</p>
<p>
<em>Gura:</em> If attribute :deg is specified, angle1 and angle2 are represented in degrees instead of radians.
</p>
<p>
<strong>cairo.context#arc_negative</strong>
</p>
<p>
<code>cairo.context#arc_negative(xc:number, yc:number, radius:number, angle1?:number, angle2?:number):map:reduce:[deg]</code>
</p>
<p>
Adds a circular arc of the given radius to the current path. The arc is centered at (xc, yc), begins at angle1 and proceeds in the direction of decreasing angles to end at angle2. If angle2 is greater than angle1 it will be progressively decreased by 2<em>math.pi until it is less than angle1.</em>
</p>
<p>
See cairo.context#arc() for more details. This function differs only in the direction of the arc between the two angles.
</p>
<p>
<em>Gura:</em> If attribute :deg is specified, angle1 and angle2 are represented in degrees instead of radians.
</p>
<p>
<strong>cairo.context#curve_to</strong>
</p>
<p>
<code>cairo.context#curve_to(x1:number, y1:number, x2:number, y2:number, x3:number, y3:number):map:reduce</code>
</p>
<p>
Adds a cubic Bezier spline to the path from the current point to position (x3, y3) in user-space coordinates, using (x1, y1) and (x2, y2) as the control points. After this call the current point will be (x3, y3).
</p>
<p>
If there is no current point before the call to cairo.context#curve<em>to() this function will behave as if preceded by a call to cr.move</em>to(x1, y1).
</p>
<p>
<strong>cairo.context#line_to</strong>
</p>
<p>
<code>cairo.context#line_to(x:number, y:number):map:reduce</code>
</p>
<p>
Adds a line to the path from the current point to position (x, y) in user-space coordinates. After this call the current point will be (x, y).
</p>
<p>
If there is no current point before the call to cairo.context#line<em>to() this function will behave as cr.move</em>to(x, y).
</p>
<p>
<strong>cairo.context#move_to</strong>
</p>
<p>
<code>cairo.context#move_to(x:number, y:number):map:reduce</code>
</p>
<p>
Begin a new sub-path. After this call the current point will be (x, y).
</p>
<p>
<strong>cairo.context#rectangle</strong>
</p>
<p>
<code>cairo.context#rectangle(x:number, y:number, width:number, height:number):map:reduce</code>
</p>
<p>
Adds a closed sub-path rectangle of the given size to the current path at position (x, y) in user-space coordinates.
</p>
<p>
This function is logically equivalent to:
</p>
<p>
cr.move<em>to(x, y)</em>cr.rel<em>line</em>to(width, 0) cr.rel<em>line</em>to(0, height) cr.rel<em>line</em>to(-width, 0) cr.close<em>path()</em>
</p>
<p>
<strong>cairo.context#text_path</strong>
</p>
<p>
<code>cairo.context#text_path(text:string):map:reduce</code>
</p>
<p>
Adds closed paths for text to the current path. The generated path if filled, achieves an effect similar to that of cairo.context#show<em>text().</em>
</p>
<p>
Text conversion and positioning is done similar to cairo.context#show<em>text().</em>
</p>
<p>
Like cairo.context#show<em>text(), After this call the current point is moved to the origin of where the next glyph would be placed in this same progression.</em>That is, the current point will be at the origin of the final glyph offset by its advance values. This allows for chaining multiple calls to to cairo.context#text<em>path() without having to set current point in between.</em>
</p>
<p>
Note: The cairo.context#text<em>path() function call is part of what the cairo designers call the "toy" text API.</em>It is convenient for short demos and simple programs, but it is not expected to be adequate for serious text-using applications. See cairo.context#glyph<em>path() for the "real" text path API in cairo.</em>
</p>
<p>
<strong>cairo.context#rel_curve_to</strong>
</p>
<p>
<code>cairo.context#rel_curve_to(dx1:number, dy1:number, dx2:number, dy2:number, dx3:number, dy3:number):map:reduce</code>
</p>
<p>
Relative-coordinate version of cairo.context#curve<em>to().</em>All offsets are relative to the current point. Adds a cubic Bezier spline to the path from the current point to a point offset from the current point by (dx3, dy3), using points offset by (dx1, dy1) and (dx2, dy2) as the control points. After this call the current point will be offset by (dx3, dy3).
</p>
<p>
Given a current point of (x, y), cr.rel<em>curve</em>to(dx1, dy1, dx2, dy2, dx3, dy3) is logically equivalent to cr.curve<em>to(x+dx1, y+dy1, x+dx2, y+dy2, x+dx3, y+dy3).</em>
</p>
<p>
It is an error to call this function with no current point. Doing so will cause cr to shutdown with a status of cairo.STATUS<em>NO</em>CURRENT<em>POINT.</em>
</p>
<p>
<strong>cairo.context#rel_line_to</strong>
</p>
<p>
<code>cairo.context#rel_line_to(dx:number, dy:number):map:reduce</code>
</p>
<p>
Relative-coordinate version of cairo.context#line<em>to().</em>Adds a line to the path from the current point to a point that is offset from the current point by (dx, dy) in user space. After this call the current point will be offset by (dx, dy).
</p>
<p>
Given a current point of (x, y), cr.rel<em>line</em>to(dx, dy) is logically equivalent to cr.line<em>to(x + dx, y + dy).</em>
</p>
<p>
It is an error to call this function with no current point. Doing so will cause cr to shutdown with a status of cairo.STATUS<em>NO</em>CURRENT<em>POINT.</em>
</p>
<p>
<strong>cairo.context#rel_move_to</strong>
</p>
<p>
<code>cairo.context#rel_move_to(dx:number, dy:number):map:reduce</code>
</p>
<p>
Begin a new sub-path. After this call the current point will offset by (dx, dy).
</p>
<p>
Given a current point of (x, y), cr.rel<em>move</em>to(dx, dy) is logically equivalent to cr.move<em>to(x + dx, y + dy).</em>
</p>
<p>
It is an error to call this function with no current point. Doing so will cause cr to shutdown with a status of cairo.STATUS<em>NO</em>CURRENT<em>POINT.</em>
</p>
<p>
<strong>cairo.context#path_extents</strong>
</p>
<p>
<code>cairo.context#path_extents()</code>
</p>
<p>
Computes a bounding box in user-space coordinates covering the points on the current path. If the current path is empty, returns an empty rectangle ((0,0), (0,0)). Stroke parameters, fill rule, surface dimensions and clipping are not taken into account.
</p>
<p>
Contrast with cairo.context#fill<em>extents() and cairo.context#stroke</em>extents() which return the extents of only the area that would be "inked" by the corresponding drawing operations.
</p>
<p>
The result of cairo.context#path<em>extents() is defined as equivalent to the limit of cairo.context#stroke</em>extents() with cairo.LINE<em>CAP</em>ROUND as the line width approaches 0.0, (but never reaching the empty-rectangle returned by cairo.context#stroke<em>extents() for a line width of 0.0).</em>
</p>
<p>
Specifically, this means that zero-area sub-paths such as cairo.context#move<em>to();cairo.context#line</em>to() segments, (even degenerate cases where the coordinates to both calls are identical), will be considered as contributing to the extents. However, a lone cairo.context#move<em>to() will not contribute to the results of cairo.context#path</em>extents().
</p>
<h3><span class="caption-index-3">10.1.3</span><a name="anchor-10-1-3"></a>cairo_pattern_t - Sources for drawing</h3>
<p>
<strong>cairo.pattern#add_color_stop_rgb</strong>
</p>
<p>
<code>cairo.pattern#add_color_stop_rgb(offset:number, red:number, green:number, blue:number):reduce</code>
</p>
<p>
Adds an opaque color stop to a gradient pattern. The offset specifies the location along the gradient's control vector. For example, a linear gradient's control vector is from (x0,y0) to (x1,y1) while a radial gradient's control vector is from any point on the start circle to the corresponding point on the end circle.
</p>
<p>
The color is specified in the same way as in cairo.context#set<em>source</em>rgb().
</p>
<p>
If two (or more) stops are specified with identical offset values, they will be sorted according to the order in which the stops are added, (stops added earlier will compare less than stops added later). This can be useful for reliably making sharp color transitions instead of the typical blend.
</p>
<p>
Note: If the pattern is not a gradient pattern, (eg. a linear or radial pattern), then the pattern will be put into an error status with a status of cairo.STATUS<em>PATTERN</em>TYPE<em>MISMATCH.</em>
</p>
<p>
<strong>cairo.pattern#add_color_stop_rgba</strong>
</p>
<p>
<code>cairo.pattern#add_color_stop_rgba(offset:number, red:number, green:number, blue:number, alpha:number):reduce</code>
</p>
<p>
Adds a translucent color stop to a gradient pattern. The offset specifies the location along the gradient's control vector. For example, a linear gradient's control vector is from (x0,y0) to (x1,y1) while a radial gradient's control vector is from any point on the start circle to the corresponding point on the end circle.
</p>
<p>
The color is specified in the same way as in cairo.context#set<em>source</em>rgba().
</p>
<p>
If two (or more) stops are specified with identical offset values, they will be sorted according to the order in which the stops are added, (stops added earlier will compare less than stops added later). This can be useful for reliably making sharp color transitions instead of the typical blend.
</p>
<p>
Note: If the pattern is not a gradient pattern, (eg. a linear or radial pattern), then the pattern will be put into an error status with a status of cairo.STATUS<em>PATTERN</em>TYPE<em>MISMATCH.</em>
</p>
<p>
<strong>cairo.pattern#get_color_stop_count</strong>
</p>
<p>
<code>cairo.pattern#get_color_stop_count()</code>
</p>
<p>
Gets the number of color stops specified in the given gradient pattern.
</p>
<p>
<strong>cairo.pattern#get_color_stop_rgba</strong>
</p>
<p>
<code>cairo.pattern#get_color_stop_rgba(index:number)</code>
</p>
<p>
Gets the color and offset information at the given index for a gradient pattern. Values of index are 0 to 1 less than the number returned by cairo.pattern#get<em>color</em>stop<em>count().</em>
</p>
<p>
<strong>cairo.pattern.create_rgb</strong>
</p>
<p>
<code>cairo.pattern.create_rgb(red:number, green:number, blue:number):static {block?}</code>
</p>
<p>
Creates a new cairo.pattern corresponding to an opaque color. The color components are floating point numbers in the range 0 to 1. If the values passed in are outside that range, they will be clamped.
</p>
<p>
<strong>cairo.pattern.create_rgba</strong>
</p>
<p>
<code>cairo.pattern.create_rgba(red:number, green:number, blue:number, alpha:number):static {block?}</code>
</p>
<p>
Creates a new cairo,pattern corresponding to a translucent color. The color components are floating point numbers in the range 0 to 1. If the values passed in are outside that range, they will be clamped.
</p>
<p>
<strong>cairo.pattern#get_rgba</strong>
</p>
<p>
<code>cairo.pattern#get_rgba()</code>
</p>
<p>
Gets the solid color for a solid color pattern.
</p>
<p>
<strong>cairo.pattern.create_for_surface</strong>
</p>
<p>
<code>cairo.pattern.create_for_surface(surface:cairo.surface):static {block?}</code>
</p>
<p>
Create a new cairo.pattern for the given surface.
</p>
<p>
<strong>cairo.pattern#get_surface</strong>
</p>
<p>
<code>cairo.pattern#get_surface()</code>
</p>
<p>
Gets the surface of a surface pattern. The reference returned in surface is owned by the pattern; the caller should call cairo<em>surface</em>reference() if the surface is to be retained.
</p>
<p>
<strong>cairo.pattern.create_linear</strong>
</p>
<p>
<code>cairo.pattern.create_linear(x0:number, y0:number, x1:number, y1:number):static {block?}</code>
</p>
<p>
Create a new linear gradient cairo.pattern along the line defined by (x0, y0) and (x1, y1). Before using the gradient pattern, a number of color stops should be defined using cairo.pattern#add<em>color</em>stop<em>rgb() or cairo.pattern#add</em>color<em>stop</em>rgba().
</p>
<p>
Note: The coordinates here are in pattern space. For a new pattern, pattern space is identical to user space, but the relationship between the spaces can be changed with cairo.pattern#set<em>matrix().</em>
</p>
<p>
<strong>cairo.pattern#get_linear_points</strong>
</p>
<p>
<code>cairo.pattern#get_linear_points()</code>
</p>
<p>
Gets the gradient endpoints for a linear gradient.
</p>
<p>
<strong>cairo.pattern.create_radial</strong>
</p>
<p>
<code>cairo.pattern.create_radial(cx0:number, cy0:number, radius0:number, cx1:number, cy1:number, radius1:number):static {block?}</code>
</p>
<p>
Creates a new radial gradient cairo<em>pattern</em>t between the two circles defined by (cx0, cy0, radius0) and (cx1, cy1, radius1). Before using the gradient pattern, a number of color stops should be defined using cairo.pattern#add<em>color</em>stop<em>rgb() or cairo.pattern#add</em>color<em>stop</em>rgba().
</p>
<p>
Note: The coordinates here are in pattern space. For a new pattern, pattern space is identical to user space, but the relationship between the spaces can be changed with cairo.pattern#set<em>matrix().</em>
</p>
<p>
<strong>cairo.pattern#get_radial_circles</strong>
</p>
<p>
<code>cairo.pattern#get_radial_circles()</code>
</p>
<p>
Gets the gradient endpoint circles for a radial gradient, each specified as a center coordinate and a radius.
</p>
<p>
<strong>cairo.mesh_pattern.create</strong>
</p>
<p>
<code>cairo.mesh_pattern.create():static {block?}</code>
</p>
<p>
<strong>cairo.mesh_pattern#begin_patch</strong>
</p>
<p>
<code>cairo.mesh_pattern#begin_patch():reduce</code>
</p>
<p>
<strong>cairo.mesh_pattern#end_patch</strong>
</p>
<p>
<code>cairo.mesh_pattern#end_patch():reduce</code>
</p>
<p>
<strong>cairo.mesh_pattern#move_to</strong>
</p>
<p>
<code>cairo.mesh_pattern#move_to(x:number, y:number):reduce</code>
</p>
<p>
<strong>cairo.mesh_pattern#line_to</strong>
</p>
<p>
<code>cairo.mesh_pattern#line_to(x:number, y:number):reduce</code>
</p>
<p>
<strong>cairo.mesh_pattern#curve_to</strong>
</p>
<p>
<code>cairo.mesh_pattern#curve_to(x1:number, y1:number, x2:number, y2:number, x3:number, y3:number):reduce</code>
</p>
<p>
<strong>cairo.mesh_pattern#set_control_point</strong>
</p>
<p>
<code>cairo.mesh_pattern#set_control_point(point_num:number, x:number, y:number):reduce</code>
</p>
<p>
<strong>cairo.mesh_pattern#set_corner_color_rgb</strong>
</p>
<p>
<code>cairo.mesh_pattern#set_corner_color_rgb(corner_num:number, red:number, green:number, blue:number):reduce</code>
</p>
<p>
<strong>cairo.mesh_pattern#set_corner_color_rgba</strong>
</p>
<p>
<code>cairo.mesh_pattern#set_corner_color_rgba(corner_num:number, red:number, green:number, blue:number, alpha:number):reduce</code>
</p>
<p>
<strong>cairo.pattern#status</strong>
</p>
<p>
<code>cairo.pattern#status()</code>
</p>
<p>
Checks whether an error has previously occurred for this pattern.
</p>
<p>
<strong>cairo.pattern#set_extend</strong>
</p>
<p>
<code>cairo.pattern#set_extend(extend:number):reduce</code>
</p>
<p>
Sets the mode to be used for drawing outside the area of a pattern. See cairo<em>extend</em>t for details on the semantics of each extend strategy.
</p>
<p>
The default extend mode is cairo.EXTEND<em>NONE for surface patterns and cairo.EXTEND</em>PAD for gradient patterns.
</p>
<p>
<strong>cairo.pattern#get_extend</strong>
</p>
<p>
<code>cairo.pattern#get_extend()</code>
</p>
<p>
Gets the current extend mode for a pattern. See cairo<em>extend</em>t for details on the semantics of each extend strategy.
</p>
<p>
<strong>cairo.pattern#set_filter</strong>
</p>
<p>
<code>cairo.pattern#set_filter(filter:number):reduce</code>
</p>
<p>
Sets the filter to be used for resizing when using this pattern. See cairo<em>filter</em>t for details on each filter.
</p>
<ul>
<li><p>
Note that you might want to control filtering even when you do not have an explicit cairo.pattern object, (for example when using cairo.context#set<em>source</em>surface()). In these cases, it is convenient to use cairo.context#get<em>source() to get access to the pattern that cairo creates implicitly. For example:</em>
</p>
<p>
cr.set<em>source</em>surface(image, x, y) cr.get<em>source().set</em>filter(cairo.FILTER<em>NEAREST)</em>
</p>
</li>
</ul>
<p>
<strong>cairo.pattern#get_filter</strong>
</p>
<p>
<code>cairo.pattern#get_filter()</code>
</p>
<p>
Gets the current filter for a pattern. See cairo<em>filter</em>t for details on each filter.
</p>
<p>
<strong>cairo.pattern#set_matrix</strong>
</p>
<p>
<code>cairo.pattern#set_matrix(matrix:matrix):reduce</code>
</p>
<p>
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
cairo<em>matrix</em>init<em>scale (&amp;matrix, 0.5, 0.5);</em>cairo<em>pattern</em>set<em>matrix (pattern, &amp;matrix);</em>
</p>
<p>
Meanwhile, using values of 2.0 rather than 0.5 in the code above would cause the pattern to appear at half of its default size.
</p>
<p>
Also, please note the discussion of the user-space locking semantics of cairo.context#set<em>source().</em>
</p>
<p>
<strong>cairo.pattern#get_matrix</strong>
</p>
<p>
<code>cairo.pattern#get_matrix()</code>
</p>
<p>
Stores the pattern's transformation matrix into matrix.
</p>
<p>
<strong>cairo.pattern#get_type</strong>
</p>
<p>
<code>cairo.pattern#get_type()</code>
</p>
<p>
This function returns the type a pattern. See cairo<em>pattern</em>type<em>t for available types.</em>
</p>
<h3><span class="caption-index-3">10.1.4</span><a name="anchor-10-1-4"></a>Regions - Representing a pixel-aligned area</h3>
<p>
<strong>cairo.region.create</strong>
</p>
<p>
<code>cairo.region.create():static {block?}</code>
</p>
<p>
<strong>cairo.region.create_rectangle</strong>
</p>
<p>
<code>cairo.region.create_rectangle(rectangle:cairo.rectangle_int):static {block?}</code>
</p>
<p>
<strong>cairo.region.create_rectangles</strong>
</p>
<p>
<code>cairo.region.create_rectangles(rects[]:cairo.rectangle_int):static {block?}</code>
</p>
<p>
<strong>cairo.region#copy</strong>
</p>
<p>
<code>cairo.region#copy() {block?}</code>
</p>
<p>
<strong>cairo.region#status</strong>
</p>
<p>
<code>cairo.region#status()</code>
</p>
<p>
<strong>cairo.region#get_extents</strong>
</p>
<p>
<code>cairo.region#get_extents()</code>
</p>
<p>
<strong>cairo.region#get_rectangle</strong>
</p>
<p>
<code>cairo.region#get_rectangle(nth:number)</code>
</p>
<p>
<strong>cairo.region#is_empty</strong>
</p>
<p>
<code>cairo.region#is_empty()</code>
</p>
<p>
<strong>cairo.region#contains_point</strong>
</p>
<p>
<code>cairo.region#contains_point(x:number, y:number)</code>
</p>
<p>
<strong>cairo.region#contains_rectangle</strong>
</p>
<p>
<code>cairo.region#contains_rectangle(rectangle:cairo.rectangle_int)</code>
</p>
<p>
<strong>cairo.region#equal</strong>
</p>
<p>
<code>cairo.region#equal(region:cairo.region)</code>
</p>
<p>
<strong>cairo.region#translate</strong>
</p>
<p>
<code>cairo.region#translate(dx:number, dy:number)</code>
</p>
<p>
<strong>cairo.region#intersect</strong>
</p>
<p>
<code>cairo.region#intersect(other:cairo.region)</code>
</p>
<p>
<strong>cairo.region#intersect_rectangle</strong>
</p>
<p>
<code>cairo.region#intersect_rectangle(rectangle:cairo.rectangle_int)</code>
</p>
<p>
<strong>cairo.region#union</strong>
</p>
<p>
<code>cairo.region#union(other:cairo.region)</code>
</p>
<p>
<strong>cairo.region#union_rectangle</strong>
</p>
<p>
<code>cairo.region#union_rectangle(rectangle:cairo.rectangle_int)</code>
</p>
<p>
<strong>cairo.region#xor</strong>
</p>
<p>
<code>cairo.region#xor(other:cairo.region)</code>
</p>
<p>
<strong>cairo.region#xor_rectangle</strong>
</p>
<p>
<code>cairo.region#xor_rectangle(rectangle:cairo.rectangle_int)</code>
</p>
<h3><span class="caption-index-3">10.1.5</span><a name="anchor-10-1-5"></a>Transformations - Manipulating the current transformation matrix</h3>
<p>
<strong>cairo.context#translate</strong>
</p>
<p>
<code>cairo.context#translate(tx:number, ty:number):reduce</code>
</p>
<p>
Modifies the current transformation matrix (CTM) by translating the user-space origin by (tx, ty). This offset is interpreted as a user-space coordinate according to the CTM in place before the new call to cairo.context#translate(). In other words, the translation of the user-space origin takes place after any existing transformation.
</p>
<p>
<strong>cairo.context#scale</strong>
</p>
<p>
<code>cairo.context#scale(sx:number, sy:number):reduce</code>
</p>
<p>
Modifies the current transformation matrix (CTM) by scaling the X and Y user-space axes by sx and sy respectively. The scaling of the axes takes place after any existing transformation of user space.
</p>
<p>
<strong>cairo.context#rotate</strong>
</p>
<p>
<code>cairo.context#rotate(angle:number):reduce:[deg]</code>
</p>
<p>
Modifies the current transformation matrix (CTM) by rotating the user-space axes by angle radians. The rotation of the axes takes places after any existing transformation of user space. The rotation direction for positive angles is from the positive X axis toward the positive Y axis.
</p>
<p>
<em>Gura:</em> If attribute :deg is specified, angle is represented in degrees instead of radians.
</p>
<p>
<strong>cairo.context#transform</strong>
</p>
<p>
<code>cairo.context#transform(matrix:matrix):reduce</code>
</p>
<p>
Modifies the current transformation matrix (CTM) by applying matrix as an additional transformation. The new transformation of user space takes place after any existing transformation.
</p>
<p>
<strong>cairo.context#set_matrix</strong>
</p>
<p>
<code>cairo.context#set_matrix(matrix:matrix):reduce</code>
</p>
<p>
Modifies the current transformation matrix (CTM) by setting it equal to matrix.
</p>
<p>
<strong>cairo.context#get_matrix</strong>
</p>
<p>
<code>cairo.context#get_matrix()</code>
</p>
<p>
Stores the current transformation matrix (CTM) into matrix.
</p>
<p>
<strong>cairo.context#identity_matrix</strong>
</p>
<p>
<code>cairo.context#identity_matrix():reduce</code>
</p>
<p>
Resets the current transformation matrix (CTM) by setting it equal to the identity matrix. That is, the user-space and device-space axes will be aligned and one user-space unit will transform to one device-space unit.
</p>
<p>
<strong>cairo.context#user_to_device</strong>
</p>
<p>
<code>cairo.context#user_to_device(x:number, y:number)</code>
</p>
<p>
Transform a coordinate from user space to device space by multiplying the given point by the current transformation matrix (CTM).
</p>
<p>
<strong>cairo.context#user_to_device_distance</strong>
</p>
<p>
<code>cairo.context#user_to_device_distance(dx:number, dy:number)</code>
</p>
<p>
Transform a distance vector from user space to device space. This function is similar to cairo.context#user<em>to</em>device() except that the translation components of the CTM will be ignored when transforming (dx,dy).
</p>
<p>
<strong>cairo.context#device_to_user</strong>
</p>
<p>
<code>cairo.context#device_to_user(x:number, y:number)</code>
</p>
<p>
Transform a coordinate from device space to user space by multiplying the given point by the inverse of the current transformation matrix (CTM).
</p>
<p>
<strong>cairo.context#device_to_user_distance</strong>
</p>
<p>
<code>cairo.context#device_to_user_distance(dx:number, dy:number)</code>
</p>
<p>
Transform a distance vector from device space to user space. This function is similar to cairo.context#device<em>to</em>user() except that the translation components of the inverse CTM will be ignored when transforming (dx,dy).
</p>
<h3><span class="caption-index-3">10.1.6</span><a name="anchor-10-1-6"></a>text - Rendering text and glyphs</h3>
<p>
<strong>cairo.context#select_font_face</strong>
</p>
<p>
<code>cairo.context#select_font_face(family:string, slant:number, weight:number):reduce</code>
</p>
<p>
Note: The cairo.context#select<em>font</em>face() function call is part of what the cairo designers call the "toy" text API. It is convenient for short demos and simple programs, but it is not expected to be adequate for serious text-using applications.
</p>
<p>
Selects a family and style of font from a simplified description as a family name, slant and weight. Cairo provides no operation to list available family names on the system (this is a "toy", remember), but the standard CSS2 generic family names, ("serif", "sans-serif", "cursive", "fantasy", "monospace"), are likely to work as expected.
</p>
<p>
If family starts with the string "cairo:", or if no native font backends are compiled in, cairo will use an internal font family. The internal font family recognizes many modifiers in the family string, most notably, it recognizes the string "monospace". That is, the family name "cairo:monospace" will use the monospace version of the internal font family.
</p>
<p>
For "real" font selection, see the font-backend-specific font<em>face</em>create functions for the font backend you are using. (For example, if you are using the freetype-based cairo-ft font backend, see cairo<em>ft</em>font<em>face</em>create<em>for</em>ft<em>face() or cairo</em>ft<em>font</em>face<em>create</em>for<em>pattern().)</em>The resulting font face could then be used with cairo.scaled<em>font</em>create() and cairo.context#set<em>scaled</em>font().
</p>
<p>
Similarly, when using the "real" font support, you can call directly into the underlying font system, (such as fontconfig or freetype), for operations such as listing available fonts, etc.
</p>
<p>
It is expected that most applications will need to use a more comprehensive font handling and text layout library, (for example, pango), in conjunction with cairo.
</p>
<p>
If text is drawn without a call to cairo.context#select<em>font</em>face(), (nor cairo.context#set<em>font</em>face() nor cairo.context#set<em>scaled</em>font()), the default family is platform-specific, but is essentially "sans-serif". Default slant is cairo.FONT<em>SLANT</em>NORMAL, and default weight is cairo.FONT<em>WEIGHT</em>NORMAL.
</p>
<p>
This function is equivalent to a call to cairo.toy<em>font</em>face.create() followed by cairo.context#set<em>font</em>face().
</p>
<p>
<strong>cairo.context#set_font_size</strong>
</p>
<p>
<code>cairo.context#set_font_size(size:number):reduce</code>
</p>
<p>
Sets the current font matrix to a scale by a factor of size, replacing any font matrix previously set with cairo.context#set<em>font</em>size() or cairo.context#set<em>font</em>matrix(). This results in a font size of size user space units. (More precisely, this matrix will result in the font's em-square being a size by size square in user space.)
</p>
<p>
If text is drawn without a call to cairo.context#set<em>font</em>size(), (nor cairo.context#set<em>font</em>matrix() nor cairo.context#set<em>scaled</em>font()), the default font size is 10.0.
</p>
<p>
<strong>cairo.context#set_font_matrix</strong>
</p>
<p>
<code>cairo.context#set_font_matrix(matrix:matrix):reduce</code>
</p>
<p>
Sets the current font matrix to matrix. The font matrix gives a transformation from the design space of the font (in this space, the em-square is 1 unit by 1 unit) to user space. Normally, a simple scale is used (see cairo<em>set</em>font<em>size()), but a more complex font matrix can be used to shear the font or stretch it unequally along the two axes.</em>
</p>
<p>
<strong>cairo.context#get_font_matrix</strong>
</p>
<p>
<code>cairo.context#get_font_matrix()</code>
</p>
<p>
Stores the current font matrix into matrix. See cairo.context#set<em>font</em>matrix().
</p>
<p>
<strong>cairo.context#set_font_options</strong>
</p>
<p>
<code>cairo.context#set_font_options(options:cairo.font_options):reduce</code>
</p>
<p>
Sets a set of custom font rendering options for the cairo<em>t.</em>Rendering options are derived by merging these options with the options derived from underlying surface; if the value in options has a default value (like cairo.ANTIALIAS<em>DEFAULT), then the value from the surface is used.</em>
</p>
<p>
<strong>cairo.context#get_font_options</strong>
</p>
<p>
<code>cairo.context#get_font_options()</code>
</p>
<p>
Retrieves font rendering options set via cairo.context#set<em>font</em>options. Note that the returned options do not include any options derived from the underlying surface; they are literally the options passed to cairo.context#set<em>font</em>options().
</p>
<p>
<strong>cairo.context#set_font_face</strong>
</p>
<p>
<code>cairo.context#set_font_face(font_face:cairo.font_face):reduce</code>
</p>
<p>
Replaces the current cairo<em>font</em>face<em>t object in the cairo</em>t with font<em>face.</em>The replaced font face in the cairo<em>t will be destroyed if there are no other references to it.</em>
</p>
<p>
<strong>cairo.context#get_font_face</strong>
</p>
<p>
<code>cairo.context#get_font_face()</code>
</p>
<p>
Gets the current font face for a cairo<em>t.</em>
</p>
<p>
<strong>cairo.context#set_scaled_font</strong>
</p>
<p>
<code>cairo.context#set_scaled_font(scaled_font:cairo.scaled_font):reduce</code>
</p>
<p>
Replaces the current font face, font matrix, and font options in the cairo<em>t with those of the cairo</em>scaled<em>font</em>t. Except for some translation, the current CTM of the cairo<em>t should be the same as that of the cairo</em>scaled<em>font</em>t, which can be accessed using cairo.context#scaled<em>font</em>get<em>ctm().</em>
</p>
<p>
<strong>cairo.context#get_scaled_font</strong>
</p>
<p>
<code>cairo.context#get_scaled_font()</code>
</p>
<p>
Gets the current scaled font for a cairo<em>t.</em>
</p>
<p>
<strong>cairo.context#show_text</strong>
</p>
<p>
<code>cairo.context#show_text(text:string):reduce</code>
</p>
<p>
A drawing operator that generates the shape from a string of UTF-8 characters, rendered according to the current font<em>face, font</em>size (font<em>matrix), and font</em>options.
</p>
<p>
This function first computes a set of glyphs for the string of text. The first glyph is placed so that its origin is at the current point. The origin of each subsequent glyph is offset from that of the previous glyph by the advance values of the previous glyph.
</p>
<p>
After this call the current point is moved to the origin of where the next glyph would be placed in this same progression. That is, the current point will be at the origin of the final glyph offset by its advance values. This allows for easy display of a single logical string with multiple calls to cairo.context#show<em>text().</em>
</p>
<p>
Note: The cairo.context#show<em>text() function call is part of what the cairo designers call the "toy" text API.</em>It is convenient for short demos and simple programs, but it is not expected to be adequate for serious text-using applications. See cairo.context#show<em>glyphs() for the "real" text display API in cairo.</em>
</p>
<p>
<strong>cairo.context#show_glyphs</strong>
</p>
<p>
<code>cairo.context#show_glyphs(glyphs:cairo.glyph):reduce</code>
</p>
<p>
A drawing operator that generates the shape from an array of glyphs, rendered according to the current font face, font size (font matrix), and font options.
</p>
<p>
<strong>cairo.context#font_extents</strong>
</p>
<p>
<code>cairo.context#font_extents()</code>
</p>
<p>
Gets the font extents for the currently selected font.
</p>
<p>
<strong>cairo.context#text_extents</strong>
</p>
<p>
<code>cairo.context#text_extents(text:string)</code>
</p>
<p>
Gets the extents for a string of text. The extents describe a user-space rectangle that encloses the "inked" portion of the text, (as it would be drawn by cairo.context#show<em>text()).</em>Additionally, the x<em>advance and y</em>advance values indicate the amount by which the current point would be advanced by cairo.context#show<em>text().</em>
</p>
<p>
Note that whitespace characters do not directly contribute to the size of the rectangle (extents.width and extents.height). They do contribute indirectly by changing the position of non-whitespace characters. In particular, trailing whitespace characters are likely to not affect the size of the rectangle, though they will affect the x<em>advance and y</em>advance values.
</p>
<p>
<strong>cairo.context#glyph_extents</strong>
</p>
<p>
<code>cairo.context#glyph_extents(glyphs:cairo.glyph)</code>
</p>
<p>
Gets the extents for an array of glyphs. The extents describe a user-space rectangle that encloses the "inked" portion of the glyphs, (as they would be drawn by cairo.context#show<em>glyphs()).</em>Additionally, the x<em>advance and y</em>advance values indicate the amount by which the current point would be advanced by cairo.context#show<em>glyphs().</em>
</p>
<p>
Note that whitespace glyphs do not contribute to the size of the rectangle (extents.width and extents.height).
</p>
<p>
<strong>cairo.toy_font_face.create</strong>
</p>
<p>
<code>cairo.toy_font_face.create(family:string, slant:number, weight:number):static {block?}</code>
</p>
<p>
Creates a font face from a triplet of family, slant, and weight. These font faces are used in implementation of the the cairo<em>t "toy" font API.</em>
</p>
<p>
If family is the zero-length string "", the platform-specific default family is assumed. The default family then can be queried using cairo.toy<em>font</em>face#get<em>family().</em>
</p>
<p>
The cairo.context#select<em>font</em>face() function uses this to create font faces. See that function for limitations and other details of toy font faces.
</p>
<p>
<strong>cairo.toy_font_face#get_family</strong>
</p>
<p>
<code>cairo.toy_font_face#get_family()</code>
</p>
<p>
Gets the familly name of a toy font.
</p>
<p>
<strong>cairo.toy_font_face#get_slant</strong>
</p>
<p>
<code>cairo.toy_font_face#get_slant()</code>
</p>
<p>
Gets the slant a toy font.
</p>
<p>
<strong>cairo.toy_font_face#get_weight</strong>
</p>
<p>
<code>cairo.toy_font_face#get_weight()</code>
</p>
<p>
Gets the weight a toy font.
</p>
<h3><span class="caption-index-3">10.1.7</span><a name="anchor-10-1-7"></a>Raster Sources - Supplying arbitary image data</h3>
<h2><span class="caption-index-2">10.2</span><a name="anchor-10-2"></a>Fonts</h2>
<h3><span class="caption-index-3">10.2.1</span><a name="anchor-10-2-1"></a>cairo_font_face_t - Base class for font faces</h3>
<h3><span class="caption-index-3">10.2.2</span><a name="anchor-10-2-2"></a>cairo_scaled_font_t - Font face at particular size and options</h3>
<p>
<strong>cairo.scaled_font.create</strong>
</p>
<p>
<code>cairo.scaled_font.create(font_face:cairo.font_face, font_matrix:matrix, ctm:matrix, options):static {block?}</code>
</p>
<h3><span class="caption-index-3">10.2.3</span><a name="anchor-10-2-3"></a>cairo_font_options_t - How a font should be rendered</h3>
<h3><span class="caption-index-3">10.2.4</span><a name="anchor-10-2-4"></a>FreeType  Fonts - Font support for FreeType</h3>
<h3><span class="caption-index-3">10.2.5</span><a name="anchor-10-2-5"></a>Win32 Fonts - Font support for Microsoft Windows</h3>
<h3><span class="caption-index-3">10.2.6</span><a name="anchor-10-2-6"></a>Quartz (CGFont) Fonts - Font support via CGFont on OS X</h3>
<h3><span class="caption-index-3">10.2.7</span><a name="anchor-10-2-7"></a>User Fonts - Font support with font data provided by the user</h3>
<h2><span class="caption-index-2">10.3</span><a name="anchor-10-3"></a>Surfaces</h2>
<h3><span class="caption-index-3">10.3.1</span><a name="anchor-10-3-1"></a>cairo_device_t - interface to underlying rendering system</h3>
<h3><span class="caption-index-3">10.3.2</span><a name="anchor-10-3-2"></a>cairo_surface_t - Base class for surfaces</h3>
<h3><span class="caption-index-3">10.3.3</span><a name="anchor-10-3-3"></a>Image Surfaces - Rendering to memory buffers</h3>
<h3><span class="caption-index-3">10.3.4</span><a name="anchor-10-3-4"></a>PDF Surfaces - Rendering PDF documents</h3>
<h3><span class="caption-index-3">10.3.5</span><a name="anchor-10-3-5"></a>PNG Support - Reading and writing PNG images</h3>
<h3><span class="caption-index-3">10.3.6</span><a name="anchor-10-3-6"></a>PostScript Surfaces - Rendering PostScript documents</h3>
<h3><span class="caption-index-3">10.3.7</span><a name="anchor-10-3-7"></a>Recording Surfaces - Records all drawing operations</h3>
<h3><span class="caption-index-3">10.3.8</span><a name="anchor-10-3-8"></a>Win32 Surfaces - Microsoft Windows surface support</h3>
<h3><span class="caption-index-3">10.3.9</span><a name="anchor-10-3-9"></a>SVG Surfaces - Rendering SVG documents</h3>
<h3><span class="caption-index-3">10.3.10</span><a name="anchor-10-3-10"></a>Quartz Surfaces - Rendering to Quartz surfaces</h3>
<h3><span class="caption-index-3">10.3.11</span><a name="anchor-10-3-11"></a>XCB Surfaces - X Window System rendering using the XCB library</h3>
<h3><span class="caption-index-3">10.3.12</span><a name="anchor-10-3-12"></a>XLib Surfaces - X Window System rendering using XLib</h3>
<h3><span class="caption-index-3">10.3.13</span><a name="anchor-10-3-13"></a>XLib-XRender Backend - X Window System rendering using XLib and the X Render extension</h3>
<h3><span class="caption-index-3">10.3.14</span><a name="anchor-10-3-14"></a>Script Surfaces - Rendering to replayable scripts</h3>
<h2><span class="caption-index-2">10.4</span><a name="anchor-10-4"></a>Utilities</h2>
<h3><span class="caption-index-3">10.4.1</span><a name="anchor-10-4-1"></a>cairo_matrix_t - Generic matrix operations</h3>
<h2><span class="caption-index-2">10.5</span><a name="anchor-10-5"></a>Thanks</h2>
<p>
This module uses Cairo library which is distributed in the following site:
</p>
<p>
<a href="http://cairographics.org/">http://cairographics.org/</a>
</p>
<p />

{% endraw %}