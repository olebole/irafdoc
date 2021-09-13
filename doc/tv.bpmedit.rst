bpmedit — examine and edit bad pixel masks associated with images
=================================================================

**Package: tv**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>bpmedit (Aug07)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.tv</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>bpmedit (Aug07)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>bpmedit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  bpmedit -- examine and edit bad pixel masks associated with images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  bpmedit images
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images whose bad pixel masks are to be edit.  The images must
  contain the keyword BPM whose value is an existing bad pixel mask to
  be edit.  If the keyword is missing or the mask does not exit a warning
  is issued and the task proceeds to the next image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bpmkey">bpmkey = "<TT>BPM</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bpmkey' Line='bpmkey = "BPM"'>
  <DD>The mask to be edited is defined by the value of this keyword.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_frame">frame = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame' Line='frame = 1'>
  <DD>The display frame where the image with the mask overlay is shown.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_refframe">refframe = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refframe' Line='refframe = 2'>
  <DD>The display frame with the image without the mask is shown.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_command">command = "<TT>display ...</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='command' Line='command = "display ..."'>
  <DD>Command for displaying and updating the mask overlay.  This is the
  command used with <B>imedit</B>.  This should be changed with care.
  In the string the following changes are made:
  <P>
  <PRE>
      $image -- substitute the image
       $mask -- substitute the mask being edited
      $frame -- substitute the value of the frame parameter
      $erase -- substituted by imedit
  </PRE>
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_display">display = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = yes'>
  <DD>Use the task interactively with the display?  This sets the behavior
  of <B>imedit</B> as described for the parameter of the same name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Image cursor input.  This is normally either a null string for interactive
  display editing or the value of a file with cursor commands to edit
  non-interactively.  See the help for <B>imedit</B> for more information.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_additional_parameters">ADDITIONAL PARAMETERS</A></H2>
  <! BeginSection: 'ADDITIONAL PARAMETERS'>
  <UL>
  <P>
  This task calls <B>display</B> to load the image display and <B>imedit</B>
  to do the editing.  The current default parameters are used from those
  tasks except the image names, frames, and the display command are set by
  this task.  Also the search radius is set to zero (i.e. no centering).
  Also the <I>display</I> and <I>cursor</I> parameters override the
  values of the parameters of the same name in <B>imedit</B>.  Of particular
  note is the default value for imedit.value which defines the mask value to
  be set initially.  This value may be changed interactively in <B>imedit</B>.
  </UL>
  <! EndSection:   'ADDITIONAL PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Bpmedit</B> is a variant of <B>imedit</B>.  It displays the input images
  with the masks overlaid.  The mask is defined
  by the value of the keyword keywords specified by the <I>bpmkey</I>
  parameter.  The editing commands apply to the mask overlay and not the
  image pixels.  In this application the edited values should be integer mask
  values.  In the usual case where zero indicates good pixels and non-zero
  indicates bad pixels one can set and unset values by changing current
  replacement value with "<TT>:value</TT>".  Two useful parameters, "<TT>:minvalue</TT>"
  and "<TT>:maxvalue</TT>", are useful in this context to allow editing only
  specific ranges of mask values.  Note that many of the imedit options are
  not useful for mask editing.  The <TT>'?'</TT> keystroke prints a list of the
  useful cursor and colon commands.  This list is also shown below.
  <P>
  Because it is common to want to see the image pixels to which the
  mask values apply this task loads two image display frames.  In one the
  mask is overlaid and changes to the mask are updated with the
  redisplay options of imedit (note the options to turn on and off
  automatic redisplay).  In the second the image without the mask is
  displayed.  The editing commands may be given in either frame but the
  mask updates will appear only in the mask overlay frame.
  <P>
  This task also provides the parameters <I>display</I> and <I>cursor</I>
  to use <B>imedit</B> in a non-interactive manner as described for that
  task.  Because only the setting and clearing of rectangles, circles,
  or vectors makes sense with this task this may not be of great use.
  Also there are many other tasks that can be used to edit masks
  non-interactively.
  <P>
  Please read the help for <B>imedit</B> for details of the editing
  process.
  <P>
  <PRE>
  		BPMEDIT CURSOR KEYSTROKE COMMANDS
  <P>
      The following are the useful commands for BPMEDIT.  Note all
      the commands for IMEDIT are available but only those shown
      here should be used for editing pixel masks.
       
  	?	Print help
  	:	Colon commands (see below)
  	i	Initialize (start over without saving changes)
  	q	Quit and save changes
  	r	Redraw image display
  	+	Increase radius by one
  	-	Decrease radius by one
  	I	Interrupt task immediately
  	Q	Quit without saving changes
  <P>
      The following editing options are available.  Rectangular
      and vector regions are specified with two positions and
      aperture regions are specified by one position.  The current
      aperture type (circular or square) is used in the latter
      case.  All the following substitute the new value set for
      the "value" parameter (see :value).  Some replace all pixels
      within the mask that have the same pixel value as the value
      at the cursor position.
  <P>
  	d 	Set rectangle to "value"
  	e 	Set aperture to "value"
  	u	Undo last change (see also <TT>'i'</TT>, <TT>'j'</TT>, and <TT>'k'</TT>)
  	v       Set vector to "value"
  	=	Replace pixels = to "cursor value" to "value"
  	&lt;	Replace pixels &lt; or = to "cursor value" to "value"
  	&gt;	Replace pixels &gt; than or = to "cursor value" to "value"
  <P>
  <P>
  		BPMEDIT COLON COMMANDS
  <P>
      The colon either print the current value of a parameter when
      there is no value or set the parameter to the specified
      value.
  <P>
      aperture [type]	 Aperture type (circular|square)
      autodisplay [yes|no] Automatic image display?
      command [string]	 Display command
      display [yes|no]	 Display image?
      eparam		 Edit parameters
      radius [value]	 Aperture radius
      value [value]	 Constant substitution value
      minvalue [value]	 Minimum value for modification (INDEF=minimum)
      maxvalue [value]	 Maximum value for modification (INDEF=maximum)
      write [name]	 Write changes to name
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Interactively edit a mask.
   
  <PRE>
      cl&gt; bpmedit wpix
  </PRE>
   
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imedit, display, badpiximage, text2mask, mskexpr, mskregions, imexpr
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>