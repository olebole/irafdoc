.. _cursors:

cursors: Graphics and image display cursors
===========================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  cursors -- cursor control for graphics and image display devices
  </p>
  <!-- EndSection:   'NAME' -->
  <span id="s_introduction">1. Introduction</span>
  <!-- BeginSection: 'Introduction' -->
  <p>
      In IRAF, all cursor input is via the graphics cursor interface in the CL.
  The CL supports two types of cursors, the graphics cursor and the image
  display cursor, represented in the CL by the two parameter datatypes <i>gcur</i>
  and <i>imcur</i>.  To read either cursor from a task, the programmer declares
  one of the parameters of their task to be of type gcur or imcur, and then
  reads the value of the parameter.  The act of reading a cursor type parameter
  causes the physical device cursor to be read.  To make it possible for the
  user to read either cursor at any time, the CL provides two predefined global
  parameters also called <i>gcur</i> and <i>imcur</i> (or to be more precise,
  <tt>"cl.gcur"</tt> and <tt>"cl.imcur"</tt>, since both parameters are local parameters of the
  <i>cl</i> task).
  </p>
  <p>
  Since the graphics cursors are interfaced as CL parameters, a cursor read is
  implied whenever a cursor type parameter is referenced in a CL expression.
  The simplest way to read a cursor is to use the <tt>"inspect"</tt> statement to print
  the value of the parameter, as in the following example.  Exactly the same
  thing happens when a program like <i>implot</i> or <i>splot</i> reads the cursor.
  </p>
  <pre>
  	cl&gt; = gcur
  	0.5005035 0.4980621 1 k 
  </pre>
  <p>
  More complex accesses are occasionally useful, e.g.:
  </p>
  <p>
  	cl&gt; print (gcur, &gt; <tt>"curpos"</tt>)
  </p>
  <p>
  writes the cursor value into a file, and
  </p>
  <p>
  	cl&gt; = fscan (gcur, x, y)
  </p>
  <p>
  leaves the X and Y coordinates of the cursor in parameters X and Y.
  </p>
  <p>
  A cursor read returns a string value, as can be seen in the above example.
  The fields of the cursor value string are (from the left) the X and Y position
  of the cursor in world coordinates, the number of the world coordinate system
  to which the coordinates refer, and the key value, or character typed to
  terminate the cursor read.  If the key is a colon (<tt>":"</tt>), a fourth field
  will be added, namely a character string entered by the user after typing the
  colon key.  This feature is useful for passing arbitrary commands to programs
  via the cursor interface.
  </p>
  <p>
  A cursor read is not instantaneous.  A cursor read is initiated by reading a
  cursor type parameter, and terminated by typing any lower case or
  non-alphanumeric character on the keyboard.  The keyboard is used to
  terminate cursor reads from the image display as well as from a graphics
  terminal.  While the cursor read is in progress, i.e., while the CL is
  waiting for a key to be typed on the terminal, the CL is said to be in
  <i>cursor mode</i>.  Cursor mode reserves all of the upper case characters
  and digits for cursor mode commands.  Since the cursor mode commands are
  intercepted by cursor mode, they do not terminate a cursor read and are never
  seen by the program reading the cursor.
  </p>
  <p>
  The cursor mode commands are the major topic of discussion in the remainder
  of this document.  In brief, the cursor mode commands are used to zoom in
  on some portion of the graphics frame (e.g., to get a more accurate cursor
  position measurement), to roam about at high magnification, to replot the frame,
  to make a hardcopy on a batch plotter device, to save or restore the frame in
  a file, and so on.  In reading the rest of this document, take care not to get
  lost in the complexities of cursor mode, forgetting the essential simplicity
  of the cursor interface, namely that we are reading the cursor and returning
  the cursor coordinates to the caller.
  </p>
  <p>
  In the remainder of this document the discussion will focus on the graphics
  cursor to minimize confusion.  The same interface is however used to access
  both types of cursor, hence the discussion is relevant for the image display
  interface as well.
  </p>
  <!-- EndSection:   'Introduction' -->
  <span id="s_overview">2. Overview</span>
  <!-- BeginSection: 'Overview' -->
  <!-- EndSection:   'Overview' -->
  <span id="s_invoking_cursor_mode">2.1 Invoking Cursor Mode</span>
  <!-- BeginSection: 'Invoking Cursor Mode' -->
  <p>
      Many IRAF tasks produce a plot of some sort and then bring up a graphics
  cursor (e.g. a crosshair) and automatically leave the terminal in cursor mode.
  Alternatively, the user can invoke cursor mode from the CL by typing:
  </p>
  <p>
  	cl&gt; = gcur
  </p>
  <p>
  If the CL environment variable <b>cminit</b> is defined when
  cursor mode is first entered, the string value will be interpreted as
  a cursor mode command and used for initialization.  For example, to
  speed up drawing time you could set text quality to low and the
  graphics resolution to 200 points in X and 100 points in Y by adding
  the following <b>set</b> declaration to one's <tt>"login.cl"</tt> file:
  </p>
  <p>
  	set cminit = <tt>"xres=200; yres=150; txqual=low"</tt>
  </p>
  <p>
  An additional environment variable is provided for applications which generate
  very complex plots.  There is a fixed upper limit on the size of the cursor
  mode frame buffer, used to retain all the graphics instructions used to
  generate a plot.  If the buffer overflows the plot will come out correctly
  the first time, but part of the instructions used to generate the plot will be
  discarded, hence it will not be possible to regenerate the full plot in cursor
  mode.  If this happens the size of the cursor mode frame buffer may be
  increased, e.g.,
  </p>
  <p>
  	set cmbuflen = 512000
  </p>
  <p>
  would set the size of the frame buffer to 512K words, or 1 megabyte.
  This would be large enough to hold almost any plot.  A call to <b>gflush</b>
  may be required before the new buffer size takes effect.
  </p>
  <!-- EndSection:   'Invoking Cursor Mode' -->
  <span id="s_cursor_mode_help">2.2 Cursor Mode Help</span>
  <!-- BeginSection: 'Cursor Mode Help' -->
  <p>
      While in cursor mode, help text may be obtained in at least two ways.
  Help on the cursor mode commands themselves, i.e. the topic of this
  document, is available with the command <tt>":.help"</tt> or just <tt>":."</tt>.  By convention
  help on an application task running cursor mode, e.g. <b>implot</b>, is 
  available with the command <tt>"?"</tt>.  All interactive IRAF graphics tasks are
  required to respond to the ? key with a summary of the keystrokes recognized
  by that task.
  </p>
  <!-- EndSection:   'Cursor Mode Help' -->
  <span id="s_cursor_mode_commands_and_options">2.3 Cursor Mode Commands and Options</span>
  <!-- BeginSection: 'Cursor Mode Commands and Options' -->
  <p>
      While in cursor mode, whether invoked by an IRAF task or interactively
  via the command <tt>"=gcur"</tt>, three classes of commands are available.
  First, single, upper-case letters take actions such as roaming and zooming,
  redrawing axes after a zoom, and prompting for text annotation.
  Second, cursor mode options and more complicated commands may be entered
  after a <tt>":."</tt>, for example sending a screen snapshot to a hardcopy plotter
  and changing text quality and orientation.  Third, all other commands,
  namely the lower case letters and most non-alphanumeric characters,
  are interpreted by the controlling task and will terminate a cursor read.
  Thus, if any keystroke is entered that is not shown below or handled by
  the governing application program, cursor mode exits and the keystroke and
  cursor coordinates are reported.
  </p>
  <p>
  Minimum match abbreviations are permitted for the cursor mode <tt>":."</tt>
  command names.  Multiple commands may be given on one line, delimited by
  semicolons.
  </p>
  <p>
  The following upper-case commands are interpreted by the graphics system
  and may therefore be entered from the keyboard either in task mode or from
  <tt>"=gcur"</tt> (this is the same help panel you get from cursor mode by
  typing <tt>":.help"</tt>):
  </p>
  <pre>
      A 			draw and label the axes of current viewport
      B			backup over last instruction in frame buffer
      C			print the cursor position
      D 			draw a line by marking the endpoints
      E			expand plot by setting window corners
      F			set fast cursor (for HJKL)
      H			step cursor left
      J			step cursor down
      K			step cursor up
      L			step cursor right
      M			move point under cursor to center of screen
      P			zoom out (restore previous expansion)
      R			redraw the screen
      T 			draw a text string
      U 			undo last frame buffer edit
      V			set slow cursor (for HJKL)
      W 			select WCS at current position of cursor
      X			zoom in, X only
      Y			zoom in, Y only
      Z			zoom in, both X and Y
      &lt;			set lower limit of plot to the cursor y value
      &gt;			set upper limit of plot to the cursor y value
      \ 			escape next character
      :			set cursor mode options
      :!			send a command to the host system
      =			short for ":.snap"
      0			reset and redraw
     1-9			roam
  </pre>
  <p>
  If the character : is typed while in cursor mode the alpha cursor will appear
  at the bottom of the screen, allowing a command line to be entered.  Command
  lines which begin with a period, e.g., <tt>":."</tt> are interpreted by the graphics
  system; any other command will terminate the cursor read.  If not running an
  IRAF task which interprets that other command, cursor mode will be
  terminated and the cursor value reported.
  </p>
  <pre>
      :.axes[+-]		    draw axes of viewport whenever screen is redrawn
      :.case[+-]		    enable case sensitivity for keystrokes
      :.clear		    clear alpha memory (e.g, this text)
      :.cursor n		    select cursor
      :.gflush		    flush plotter output
      :.help		    print help text for cursor mode
      :.init		    initialize the graphics system
      :.markcur[+-]	    mark cursor position after each cursor read
      :.off [keys]	    disable selected cursor mode keys
      :.on [keys]		    enable selected cursor mode keys
      :.page[+-]		    enable screen clear before printing help text
      :.read file		    fill frame buffer from a file
      :.show		    print cursor mode and graphics kernel status
      :.snap [device]	    make hardcopy of graphics display
      :.txqual qual	    set character generator quality (normal,l,m,h)
      :.txset format	    set text drawing parameters (size,up,hj,vj,etc)
      :.xres=value	    set X resolution (stdgraph only)
      :.yres=value	    set Y resolution (stdgraph only)
      :.viewport x1 x2 y1 y2  set workstation viewport in world coordinates
      :.write[!][+] file	    save frame buffer in a spool file
      :.zero		    reset viewport and redraw frame
  </pre>
  <!-- EndSection:   'Cursor Mode Commands and Options' -->
  <span id="s_advanced_usage">3. Advanced Usage</span>
  <!-- BeginSection: 'Advanced Usage' -->
  <!-- EndSection:   'Advanced Usage' -->
  <span id="s_the_frame_buffer">3.1 The Frame Buffer</span>
  <!-- BeginSection: 'The Frame Buffer' -->
  <p>
      
      The concept of the <i>frame buffer</i> is essential to an understanding of
  cursor mode.  IRAF tasks output all graphics in the form of GKI 
  metacode instructions.  These instructions may be stored in a file if
  desired, or, if the task is run from the CL, they will usually be 
  stored automatically in the frame buffer.  This is a large storage area internal
  to the CL process, and is transparent to the user.  What is important is
  that after producing a plot on the screen, all or part of the information
  in the plot is still present in the frame buffer.  That means that it is
  possible to enter an interactive session with the plot, whether as a part of
  the task that produced the plot in the first place or after the task
  exits by typing <tt>"=gcur"</tt> from the CL.
  </p>
  <p>
  If one wishes to recall the last plot after the task which created it has
  exited, and the screen has since been cleared, the plot will still be in
  the frame buffer and can be redrawn by entering cursor mode and typing 0
  (the digit zero).  If the desired plot was not the last one plotted,
  hence is no longer in the frame buffer, it can still be recalled if it
  was saved earlier in a metacode file on disk.  The command <tt>":.read fname"</tt>
  will refill the frame buffer from file <tt>"fname"</tt>, and redraw the plot.
  </p>
  <p>
  All graphics instructions output since the last time the device screen was
  cleared reside in the frame buffer unless there is an extremely large amount
  of information in the plot, in which case only the last part of the plot
  will be saved (the frame buffer dynamically sizes itself to fit the frame,
  but there is a fixed upper limit on its size of about 100 Kb).
  </p>
  <!-- EndSection:   'The Frame Buffer' -->
  <span id="s_filling_and_writing_the_frame_buffer">3.2 Filling and Writing the Frame Buffer</span>
  <!-- BeginSection: 'Filling and Writing the Frame Buffer' -->
  <p>
      The graphics system will automatically clear the frame buffer whenever
  the screen is cleared when plotting.  For example, in a heavy interactive
  graphics session, the frame buffer will be filled and cleared many times,
  and at the end only the last screenfull will be left in the frame buffer.
  When reading a metacode file containing several frames with <tt>":.read"</tt>,
  all frames will be plotted in sequence, but only the last one will remain
  in the buffer when the sequence finishes.
  </p>
  <p>
  Some tasks have application-specific functions that append to, rather than
  overwrite the frame buffer.  For example, the <tt>"j"</tt> function in <b>implot</b>
  plots another line from the image.  On the screen the previous data vectors
  are erased and the new ones drawn over.  However, if you then do a zoom or
  a reset screen, you will see EACH of the sets of data vectors drawn in
  succession (some people unfairly consider this to be a bug, but actually it
  is a highly desirable feature which we are justifiably proud of).  
  </p>
  <p>
  The contents of the frame buffer may be written to a metacode file
  with <tt>":.write file"</tt>.  By default the frame buffer is appended to the
  file if it already exists.  If you wish to <tt>"clobber"</tt> an existing file,
  use <tt>":.write! file"</tt>.  Also by default, the frame that is written is what
  you currently see on the screen, i.e., if you have zoomed in on a feature
  only what you see on the screen will be saved.  To write the full frame
  (the one you would see if you first did a <tt>"0"</tt>), use <tt>":.write+ file"</tt>.
  To overwrite an existing metacode file in full-frame mode, use <tt>":.write!+ file"</tt>.
  </p>
  <!-- EndSection:   'Filling and Writing the Frame Buffer' -->
  <span id="s_moving_the_cursor_and_modifying_the_display_area">3.3 Moving the Cursor and Modifying the Display Area</span>
  <!-- BeginSection: 'Moving the Cursor and Modifying the Display Area' -->
  <p>
      A number of special keystrokes are recognized for interactive
  display control.  These keystrokes may be used to redraw all or
  any portion of the spooled graphics; e.g., one may zoom in on
  a portion of the plot and then roam about on the plot at high
  magnification.  Since the spooled graphics vectors often contain
  more information than can be displayed at normal magnification, zooming
  in on a feature may bring out additional detail (the maximum resolution
  is 32768 points in either axis).  Increasing the magnification will
  increase the precision of a cursor read by the same factor.
  </p>
  <p>
  If the graphics frame is a typical vector plot with drawn and labeled
  axes, magnifying a portion of the plot may cause the axes to be lost.
  If this is not what is desired a keystroke (<tt>"A"</tt>) is provided to draw and label
  the axes of the displayed window.  The axes will be overplotted on the
  current display and will not be saved in the frame buffer, hence they
  will be lost when the frame is redrawn.  New axes may optionally be drawn
  every time the viewport changes after entry of the command <tt>":.axes+"</tt>.
  In cursor mode the viewport is the full display area of the output device,
  hence the tick mark labels of the drawn axes are drawn inside the viewport,
  on top of the data.
  </p>
  <p>
  By default the cursor mode keystrokes are all upper case letters, reserving
  lower case for applications programs.  The terminal shift lock key may be
  used to simplify typing in lengthy interactive cursor mode sessions.
  Most of the upper-case commands involve moving the graphics cursor
  and/or re-displaying a different part of the plot.  Special keystrokes
  are provided for stepwise cursor motions to increase the speed of cursor
  setting on terminals that do not have fast cursor motions (e.g., the
  Retro-Graphics enhanced VT100).  These keystrokes will only work if the terminal
  you are using permits positioning of the cursor under software control.
  </p>
  <p>
  The commands H, J, K, and L (upper case!) move the cursor left, down, up,
  and right (as in the VI text editor and in Forth/Camera graphics).
  The step size of each cursor motion can change in one of three ways.
  <tt>"F"</tt> increases the step size by a factor over the current step size each
  time it is used; <tt>"V"</tt> decreases it similarly.
  </p>
  <p>
  In practice the F/V speed keys are rarely used because the cursor positioning
  algorithm will automatically adjust the step size as you move the cursor.
  A large step size is used to cross the screen, then the step size is
  automatically decreased as you get close to the desired feature.
  Some practice is required to become adept at this, but soon it becomes
  natural and fast.
  </p>
  <p>
  Arrow keys, thumbwheels, etc., if present on a keyboard, may also be used
  for cursor motions.  However, moving the cursor this way does not
  automatically report the position to the graphics system, thus if the
  command <tt>"C"</tt> is given, you will not get a position report after each motion.  
  </p>
  <p>
  The numeric keypad of the terminal (if it has one) is used to roam about
  when the zoom factor is greater than one.  A numeric key must be escaped
  to use it to exit cursor mode, i.e., if the applications program reading
  the cursor recognizes the digit characters as commands.
  The directional significance of the numeric keys in roam mode is obvious
  if the terminal has a keypad, and is illustrated below.
  </p>
  <pre>
  	7   8   9	135 090 045
  
  	4   5   6	180 000 000
  
  	1   2   3      -135 -90 -45
  </pre>
  <p>
  Even if the terminal has a keypad, it may not be possible to use it for
  roam on some terminals.  If the keypad does not work, the normal numeric
  keys at the top of the keyboard will, after a glance at the keypad to
  see which digit to use.
  </p>
  <!-- EndSection:   'Moving the Cursor and Modifying the Display Area' -->
  <span id="s_reporting_and_marking_the_cursor_position">3.4 Reporting and Marking the Cursor Position</span>
  <!-- BeginSection: 'Reporting and Marking the Cursor Position' -->
  <p>
      To print the current cursor position in world coordinates without
  exiting cursor mode use the <tt>`C'</tt> keystroke.
  </p>
  <p>
  If the cursor mode option <tt>":.markcur+"</tt> is set, the position of the cursor
  will be marked with a small plus sign when time cursor mode exits,
  returning the cursor position to the calling program.  This is useful
  when marking the positions of a large number of objects, to keep track
  of the objects already marked.  The cursor position will not be marked until
  cursor mode exits, i.e., no cursor mode command will cause the mark to be
  drawn.  The mark cursor option remains in effect until you explicitly turn
  it off with <tt>":.markcur-"</tt> or by typing <i>gflush</i>.  The marks are drawn
  in the frame buffer, hence they will survive zoom and roam or screen reset
  (they can be erased with repeated B commands if desired).
  </p>
  <p>
  Some plots have more than one world coordinate system (WCS, the third value
  in the cursor value string).  Suppose you are in cursor mode and the frame
  contains two separate plots, or there is only one plot but the lower x-axis
  is in Angstroms while the upper one is in inverse centimeters.  By default
  the graphics system will automatically select the WCS (viewport) closest to
  the position of the cursor, returning a cursor position in that coordinate
  system.  If this is not what is desired, move the cursor to a position
  that belongs unambiguously to one of the coordinate systems and type <tt>"W"</tt>.
  Subsequent cursor reads will refer to the coordinate system you have
  specified, regardless of the position of the cursor on the screen.
  When the frame is cleared the WCS <tt>"lock"</tt> will be cleared as well.
  </p>
  <!-- EndSection:   'Reporting and Marking the Cursor Position' -->
  <span id="s_annotating_plots">3.5 Annotating Plots</span>
  <!-- BeginSection: 'Annotating Plots' -->
  <p>
      The <tt>"T"</tt> command will prompt you for a text string to be entered from the
  keyboard, followed by a RETURN.  The text will appear on the screen (and get
  stored in the frame buffer), normally located with its lower left corner at
  the current cursor position.  This command may be used in conjunction with
  the <tt>"D"</tt> command to draw a line from the text annotation to a feature of
  interest in the plot.  Notice that the text size is constant in cursor
  mode regardless of the current magnification.  In order that text entered
  with <tt>"T"</tt> will look as nearly the same as possible on a hardcopy snapshot
  as it does on the screen, you should set text quality to high.
  </p>
  <p>
  Text attributes are controlled by two command options.  Use <tt>":.txqual"</tt> to
  set text quality to <tt>"normal"</tt> (the default), <tt>"low"</tt>, <tt>"medium"</tt>, or <tt>"high"</tt>.
  Low-quality text plots the fastest, high-quality the slowest.  On terminals
  with hardware text generation such as the Retro-Graphics Enhanced VT100,
  low-quality characters may always come out 
  upright, even if the whole text string's up-vector is not at 90 degrees.
  </p>
  <p>
  Low-quality text sizes are also fixed on most devices, so in a hardcopy
  snapshot of a plot the text will not necessarily look the same as it did
  on the screen (in particular it may overwrite data vectors).
  With low-quality text other options such
  as <tt>"font=italic"</tt> will not work on most terminals (although they may come
  out correctly on a hardcopy device).  In general, set <tt>":.txqual=h"</tt> if you are
  planning to get hardcopy output from a plot you are annotating.  Changing
  the text quality only applies to text entered with <tt>"T"</tt> AFTER the change;
  you cannot automatically set all text to high quality after you have 
  entered it.
  </p>
  <p>
  There are several ways to change the position of text relative to the
  cursor, its size, font, and orientation.  Use <tt>":.txset"</tt> to change the
  text drawing parameters as follows:
  </p>
  <pre>
  
      keyword	values					default
  
      up		degrees counterclockwise, zero = +x	90
      size	character size scale factor		1.0
      path	left, right, up, down			right
      hjustify	normal, center, left, right		left
      vjustify	normal, center, top, bottom		bottom
      font	roman, greek, italic, bold		roman
      quality	normal, low, medium, high		normal
      color	integers greater than one		1
  
  </pre>
  <p>
  The <tt>"up"</tt> keyword controls the orientation of the character and the whole
  text string.  A text string oriented at +45 degrees to the horizontal, 
  from left to right, would have <tt>"up=135"</tt>.
  </p>
  <p>
  Character sizes are all specified relative to a base size characteristic
  of each plotting device.  The size is a linear magnification factor, so
  <tt>"size=2.0"</tt> results in a character with four times the area.
  </p>
  <p>
  Path is relative to the up vector; a string of characters consecutively
  underneath each other with the normal upright orientation would have 
  <tt>"up=90;path=down"</tt>.
  </p>
  <p>
  The justify parameters refer to the placement of the entire text string
  relative to the current cursor position.  To center a text string horizontally
  over a spike in a plot, position the cursor to just above the spike and
  set <tt>"h=c;v=b"</tt>.
  </p>
  <p>
  Font and quality were discussed above.  Setting the color will only have
  an effect on devices supporting it; if you have a color pen plotter, you
  must remember the current color setting, because there you cannot see it
  on the screen (<tt>":.show"</tt> will reveal it however).
  </p>
  <p>
  If you make a mistake or don't like the appearance of the text you entered,
  all is not lost.  Use the command <tt>"B"</tt> to back up over the last instruction
  and redraw (e.g. with <tt>"0"</tt>) until you're ready to reenter the text.  If you
  back up one instruction too far (you lose some of the data vectors for
  instance) just type <tt>"U"</tt> to undo the last frame buffer edit, i.e. the backup.
  </p>
  <p>
  For example, to annotate a spectral line with <tt>"H-alpha"</tt>, written sideways
  up the screen from the current position in italics:
  </p>
  <pre>
  
  	:.txqual high
  	:.txset up=180;font=italic
  	T
  	text: H-alpha
  
  </pre>
  <p>
  On the last line, cursor mode provided the <tt>"text: "</tt> prompt.  The
  format could have been shortened to <tt>"u=180;f=i"</tt>.
  </p>
  <!-- EndSection:   'Annotating Plots' -->
  <span id="s_hardcopy_snapshots">3.6 Hardcopy Snapshots</span>
  <!-- BeginSection: 'Hardcopy Snapshots' -->
  <p>
      There are two main ways to get a hardcopy of the frame buffer.  To 
  get a copy of what you see on the screen directly on a hardcopy plotter,
  simply use <tt>":.snap plottername"</tt>.  When you do so, you are actually sending
  the output down a buffered stream.  That is, you can do several <tt>":.snap"</tt>'s
  before anything actually comes out on the plotter.  This is because many
  plotters use several pages worth of blank paper before and after the actual
  plot.  If you are planning to make a number of snapshots in succession,
  even if they are from different <tt>"=gcur"</tt> sessions, simply use <tt>":.snap"</tt> for
  each one until you are done, then issue <tt>":.gflush"</tt>.  You can also flush
  graphics output to a plotter from the CL using the Language Package task
  <b>gflush</b>:
  </p>
  <pre>
  	cl&gt; =gcur
  	...
  	:.snap versatec
  	...
  	:.snap versatec
  	&lt;RETURN&gt;
  	cl&gt;
  	cl&gt; gflush
  
  </pre>
  <p>
  Alternatively, you can use <tt>":.write mcodefile"</tt> as discussed above, appending
  as many different frames as you wish, then later from the CL, send the
  metacode file to a plotter with one of the graphics kernels:
  </p>
  <pre>
  	cl&gt; implot
  	...				(interactive session)
  	:.write file1.mc
  	&lt;RETURN&gt;
  	cl&gt; stdplot file1.mc
  
  		or
  
  	cl&gt; calcomp file1.mc		(etc.)
  
  </pre>
  <!-- EndSection:   'Hardcopy Snapshots' -->
  <span id="s_alternate_cursor_input">3.7 Alternate Cursor Input</span>
  <!-- BeginSection: 'Alternate Cursor Input' -->
  <p>
      Any program which uses cursor input may be run non-interactively as well
  as in batch mode.  For example, suppose the task has a cursor type parameter
  called <tt>"coords"</tt>.  In normal interactive use a hardware cursor read will
  occur every time the program reads the value of the <tt>"coords"</tt> parameter.
  To run the program in batch mode we must first prepare a list of cursor
  values in a text file, e.g., with the <i>rgcursor</i> or <i>rimcursor</i> tasks
  in the <i>lists</i> package.  We then run the task assigning the name of the
  cursor list file to the parameter <tt>"coords"</tt>.  For example, to run the
  <i>apphot</i> task in batch, with the cursor list in the file <tt>"starlist"</tt>:
  </p>
  <p>
  	cl&gt; apphot arg1 arg2 ... argN coords=starlist &amp;
  </p>
  <p>
  The program will then read successive cursor values from the starlist file,
  not knowing that the cursor values are coming from a text file rather than
  from actual cursor reads.
  </p>
  <p>
  A second mechanism is available for redirecting cursor input to the
  terminal.  This is most useful when working from a terminal that does not
  have graphics, or when debugging software.  To work this way one must
  first set the value of the environment variable <i>stdgcur</i> (for the
  graphics cursor) or <i>stdimcur</i> (for the image cursor).  Set the value
  to <tt>"text"</tt> to direct cursor reads to the terminal, e.g.:
  </p>
  <p>
  	cl&gt; set stdgcur = text
  </p>
  <p>
  The cursor value will then be a line of text read from the user terminal.
  In this mode the user enters at least two of the fields defining a cursor
  value.  Missing fields are assigned the value zero (the user presumably
  will know that the program does not use the extra fields).
  </p>
  <pre>
  	cl&gt; = gcur
  	gcur: 345.33 23.22 1 c
  	345.33 23.22 1 c
  	cl&gt;
  </pre>
  <p>
  An example of a cursor read request entered interactively by the user,
  taking input from the terminal and sending output to the terminal,
  is shown above (the CL typed the <tt>"gcur: "</tt> query and the user entered the
  remainder of that line).  If the cursor device were <tt>"stdgraph"</tt> a real
  cursor read would occur and the equivalent interaction might appear as
  shown below.  The cursor position is returned in world coordinates,
  where the world coordinate system was defined by the last plot output to
  the device.  For an imaging device the world coordinates will typically
  be the pixel coordinates of the image section being displayed.
  </p>
  <pre>
  	cl&gt; = gcur
  	345.33 23.22 1 c
  	cl&gt;
  </pre>
  <p>
  Redirecting cursor input to the terminal is useful when working from a
  non-graphics workstation and when debugging programs.  ASCII cursor queries
  are the only type supported when running an IRAF program outside the CL.
  Cursor input may also be taken from a list file by assigning a filename
  to a cursor parameter, i.e., by assigning a list file to a list structured
  parameter and overriding query mode:
  </p>
  <pre>
  	cl&gt; gcur = filename
  	cl&gt; = gcur
  	345.33 23.22 1 c
  	cl&gt;
  </pre>
  <!-- EndSection:   'Alternate Cursor Input' -->
  <span id="s_examining_the_status_of_the_graphics_system">3.8 Examining the Status of the Graphics System</span>
  <!-- BeginSection: 'Examining the Status of the Graphics System' -->
  <p>
      The command <tt>":.show"</tt> writes out a page of information concerning the
  state of the graphics system.  This is an example of such a status report:
  </p>
  <pre>
      Cursor Mode Parameters:
  
  	case	= YES
  	markcur = YES
  	page	= YES
  	axes	= NO
  	view	= full screen
  	keys	= ABCDEFGHIJKLMNOPQRSTUVWXYZ&lt;&gt;0123456789?:
  		-&gt;ABCDEFGHIJKLMNOPQRSTUVWXYZ&lt;&gt;0123456789?:
  
  
      Graphics Kernel Status:
  
  	STDGRAPH: kernel=cl, device=vt640
  	    memory=9472 (8192fb+256sb+1024fio), frame=1114+0 words
  	    spool=yes, nopen=0, pid=0, in=0, out=0, redir=-6, wcs=0
  	    text size = 1., up=90, path=right, hj=left, vj=bottom, color=1
  
  	STDIMAGE:	disconnected
  	STDPLOT:	disconnected
  </pre>
  <p>
  The cursor mode parameters report the current values of the <tt>":."</tt> command
  options; these options are in effect for all of three the standard graphics
  streams, i.e., STDGRAPH (the graphics terminal), STDIMAGE (the image display),
  and STDPLOT (batch plotters).
  </p>
  <p>
  The graphics kernel status reports the status of each of the three graphics
  streams.  These streams are independent and in principle any graphics device
  may be connected to any stream.  The <i>kernel</i> field gives the name of
  the kernel connected to that stream, if any.  The value <tt>"cl"</tt> refers to the
  <i>stdgraph</i> kernel, which is built into the CL, and which can only talk
  to graphics terminals.  Any other value is the filename of an external graphics
  kernel, running as a subprocess of the CL process.  The <i>device</i> field
  gives the name of the device named in the last <tt>"open workstation"</tt> command
  on that stream.  This is the device the stream is currently writing plots to.
  </p>
  <p>
  The significance of the remaining kernel status fields is described below.
  </p>
  <pre>
  	memory		- total memory used, chars
  	fb		- size of primary frame buffer, chars
  	sb		- size of scratch frame buffer (used by A)
  	fio		- size of the FIO buffer for the stream
  	frame		- amount of data in the frame + data in SB
  
  	spool		- enable spooling of graphics in frame buffer?
  	nopen		- open count (should be zero)
  	pid		- process id of kernel subprocess
  	in		- fd of process in, if subkernel
  	out		- fd of process out, if subkernel
  	redir		- redirection information for pseudofile i/o
  	wcs		- current WCS, zero if not locked with W
  
  	text size	- current text size relative to device's base size
  	up		- text up vector
  	path		- text character drawing path
  	hj		- horizontal justification
  	vj		- vertical justification
  	color		- index of current color attribute
  </pre>
  <p>
  This status report reflects only the information known to the CL.  The graphics
  subkernels, which are subprocesses of the CL, may themselves have subprocesses,
  sometimes on different nodes in the local network.
  </p>
  <!-- EndSection:   'Examining the Status of the Graphics System' -->
  <span id="s_initializing_the_graphics_system">3.9 Initializing the Graphics System</span>
  <!-- BeginSection: 'Initializing the Graphics System' -->
  <p>
      The graphics system can normally be initialized by typing <i>gflush</i>.
  This will clear the frame buffer and disconnect all kernels, freeing memory
  and file descriptors, and reducing the subprocess count.  Shutting down a
  graphics subkernel automatically flushes any buffered graphics output.
  The CL automatically calls <i>gflush</i> during logout to shutdown the
  graphics system in an orderly fashion.
  </p>
  <!-- EndSection:   'Initializing the Graphics System' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Despite the fact that the CL has graphics and image cursor access capabilities,
  there is no guarantee that one can access the cursor on a particular device.
  A <i>graphcap</i> entry for the device is also required, as is a graphics kernel
  if the device is not a conventional graphics terminal (e.g., an image display).
  If all of these pieces are not in place, the system will abort the cursor
  read, complaining that it cannot find a termcap or graphcap entry for the
  device, or that it cannot open a connected subprocess (the subkernel).
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  The GIO Reference Manual
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'Introduction' 'Overview' 'Invoking Cursor Mode' 'Cursor Mode Help' 'Cursor Mode Commands and Options' 'Advanced Usage' 'The Frame Buffer' 'Filling and Writing the Frame Buffer' 'Moving the Cursor and Modifying the Display Area' 'Reporting and Marking the Cursor Position' 'Annotating Plots' 'Hardcopy Snapshots' 'Alternate Cursor Input' 'Examining the Status of the Graphics System' 'Initializing the Graphics System' 'BUGS' 'SEE ALSO'  -->
  
