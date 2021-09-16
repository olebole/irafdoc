.. _cursors:

cursors — Graphics and image display cursors
============================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  cursors -- cursor control for graphics and image display devices
  <P>
  </UL>
  <! EndSection:   'NAME'>
  <H3>1. introduction</H3>
  <! BeginSection: 'Introduction'>
  <UL>
  <P>
      In IRAF, all cursor input is via the graphics cursor interface in the CL.
  The CL supports two types of cursors, the graphics cursor and the image
  display cursor, represented in the CL by the two parameter datatypes <I>gcur</I>
  and <I>imcur</I>.  To read either cursor from a task, the programmer declares
  one of the parameters of their task to be of type gcur or imcur, and then
  reads the value of the parameter.  The act of reading a cursor type parameter
  causes the physical device cursor to be read.  To make it possible for the
  user to read either cursor at any time, the CL provides two predefined global
  parameters also called <I>gcur</I> and <I>imcur</I> (or to be more precise,
  "<TT>cl.gcur</TT>" and "<TT>cl.imcur</TT>", since both parameters are local parameters of the
  <I>cl</I> task).
  <P>
  Since the graphics cursors are interfaced as CL parameters, a cursor read is
  implied whenever a cursor type parameter is referenced in a CL expression.
  The simplest way to read a cursor is to use the "<TT>inspect</TT>" statement to print
  the value of the parameter, as in the following example.  Exactly the same
  thing happens when a program like <I>implot</I> or <I>splot</I> reads the cursor.
  <P>
  <PRE>
  	cl&gt; = gcur
  	0.5005035 0.4980621 1 k 
  </PRE>
  <P>
  More complex accesses are occasionally useful, e.g.:
  <P>
  	cl&gt; print (gcur, &gt; "<TT>curpos</TT>")
  <P>
  writes the cursor value into a file, and
  <P>
  	cl&gt; = fscan (gcur, x, y)
  <P>
  leaves the X and Y coordinates of the cursor in parameters X and Y.
  <P>
  A cursor read returns a string value, as can be seen in the above example.
  The fields of the cursor value string are (from the left) the X and Y position
  of the cursor in world coordinates, the number of the world coordinate system
  to which the coordinates refer, and the key value, or character typed to
  terminate the cursor read.  If the key is a colon ("<TT>:</TT>"), a fourth field
  will be added, namely a character string entered by the user after typing the
  colon key.  This feature is useful for passing arbitrary commands to programs
  via the cursor interface.
  <P>
  A cursor read is not instantaneous.  A cursor read is initiated by reading a
  cursor type parameter, and terminated by typing any lower case or
  non-alphanumeric character on the keyboard.  The keyboard is used to
  terminate cursor reads from the image display as well as from a graphics
  terminal.  While the cursor read is in progress, i.e., while the CL is
  waiting for a key to be typed on the terminal, the CL is said to be in
  <I>cursor mode</I>.  Cursor mode reserves all of the upper case characters
  and digits for cursor mode commands.  Since the cursor mode commands are
  intercepted by cursor mode, they do not terminate a cursor read and are never
  seen by the program reading the cursor.
  <P>
  The cursor mode commands are the major topic of discussion in the remainder
  of this document.  In brief, the cursor mode commands are used to zoom in
  on some portion of the graphics frame (e.g., to get a more accurate cursor
  position measurement), to roam about at high magnification, to replot the frame,
  to make a hardcopy on a batch plotter device, to save or restore the frame in
  a file, and so on.  In reading the rest of this document, take care not to get
  lost in the complexities of cursor mode, forgetting the essential simplicity
  of the cursor interface, namely that we are reading the cursor and returning
  the cursor coordinates to the caller.
  <P>
  In the remainder of this document the discussion will focus on the graphics
  cursor to minimize confusion.  The same interface is however used to access
  both types of cursor, hence the discussion is relevant for the image display
  interface as well.
  <P>
  </UL>
  <! EndSection:   'Introduction'>
  <H3>2. overview</H3>
  <! BeginSection: 'Overview'>
  <UL>
  </UL>
  <! EndSection:   'Overview'>
  <H3>2.1 invoking cursor mode</H3>
  <! BeginSection: 'Invoking Cursor Mode'>
  <UL>
  <P>
      Many IRAF tasks produce a plot of some sort and then bring up a graphics
  cursor (e.g. a crosshair) and automatically leave the terminal in cursor mode.
  Alternatively, the user can invoke cursor mode from the CL by typing:
  <P>
  	cl&gt; = gcur
  <P>
  If the CL environment variable <B>cminit</B> is defined when
  cursor mode is first entered, the string value will be interpreted as
  a cursor mode command and used for initialization.  For example, to
  speed up drawing time you could set text quality to low and the
  graphics resolution to 200 points in X and 100 points in Y by adding
  the following <B>set</B> declaration to one's "<TT>login.cl</TT>" file:
  <P>
  	set cminit = "<TT>xres=200; yres=150; txqual=low</TT>"
  <P>
  An additional environment variable is provided for applications which generate
  very complex plots.  There is a fixed upper limit on the size of the cursor
  mode frame buffer, used to retain all the graphics instructions used to
  generate a plot.  If the buffer overflows the plot will come out correctly
  the first time, but part of the instructions used to generate the plot will be
  discarded, hence it will not be possible to regenerate the full plot in cursor
  mode.  If this happens the size of the cursor mode frame buffer may be
  increased, e.g.,
  <P>
  	set cmbuflen = 512000
  <P>
  would set the size of the frame buffer to 512K words, or 1 megabyte.
  This would be large enough to hold almost any plot.  A call to <B>gflush</B>
  may be required before the new buffer size takes effect.
  <P>
  </UL>
  <! EndSection:   'Invoking Cursor Mode'>
  <H3>2.2 cursor mode help</H3>
  <! BeginSection: 'Cursor Mode Help'>
  <UL>
  <P>
      While in cursor mode, help text may be obtained in at least two ways.
  Help on the cursor mode commands themselves, i.e. the topic of this
  document, is available with the command "<TT>:.help</TT>" or just "<TT>:.</TT>".  By convention
  help on an application task running cursor mode, e.g. <B>implot</B>, is 
  available with the command "<TT>?</TT>".  All interactive IRAF graphics tasks are
  required to respond to the ? key with a summary of the keystrokes recognized
  by that task.
  <P>
  </UL>
  <! EndSection:   'Cursor Mode Help'>
  <H3>2.3 cursor mode commands and options</H3>
  <! BeginSection: 'Cursor Mode Commands and Options'>
  <UL>
  <P>
      While in cursor mode, whether invoked by an IRAF task or interactively
  via the command "<TT>=gcur</TT>", three classes of commands are available.
  First, single, upper-case letters take actions such as roaming and zooming,
  redrawing axes after a zoom, and prompting for text annotation.
  Second, cursor mode options and more complicated commands may be entered
  after a "<TT>:.</TT>", for example sending a screen snapshot to a hardcopy plotter
  and changing text quality and orientation.  Third, all other commands,
  namely the lower case letters and most non-alphanumeric characters,
  are interpreted by the controlling task and will terminate a cursor read.
  Thus, if any keystroke is entered that is not shown below or handled by
  the governing application program, cursor mode exits and the keystroke and
  cursor coordinates are reported.
  <P>
  Minimum match abbreviations are permitted for the cursor mode "<TT>:.</TT>"
  command names.  Multiple commands may be given on one line, delimited by
  semicolons.
  <P>
  The following upper-case commands are interpreted by the graphics system
  and may therefore be entered from the keyboard either in task mode or from
  "<TT>=gcur</TT>" (this is the same help panel you get from cursor mode by
  typing "<TT>:.help</TT>"):
  <P>
  <PRE>
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
  </PRE>
  <P>
  If the character : is typed while in cursor mode the alpha cursor will appear
  at the bottom of the screen, allowing a command line to be entered.  Command
  lines which begin with a period, e.g., "<TT>:.</TT>" are interpreted by the graphics
  system; any other command will terminate the cursor read.  If not running an
  IRAF task which interprets that other command, cursor mode will be
  terminated and the cursor value reported.
  <P>
  <PRE>
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
  </PRE>
  <P>
  </UL>
  <! EndSection:   'Cursor Mode Commands and Options'>
  <H3>3. advanced usage</H3>
  <! BeginSection: 'Advanced Usage'>
  <UL>
  </UL>
  <! EndSection:   'Advanced Usage'>
  <H3>3.1 the frame buffer</H3>
  <! BeginSection: 'The Frame Buffer'>
  <UL>
      
      The concept of the <I>frame buffer</I> is essential to an understanding of
  cursor mode.  IRAF tasks output all graphics in the form of GKI 
  metacode instructions.  These instructions may be stored in a file if
  desired, or, if the task is run from the CL, they will usually be 
  stored automatically in the frame buffer.  This is a large storage area internal
  to the CL process, and is transparent to the user.  What is important is
  that after producing a plot on the screen, all or part of the information
  in the plot is still present in the frame buffer.  That means that it is
  possible to enter an interactive session with the plot, whether as a part of
  the task that produced the plot in the first place or after the task
  exits by typing "<TT>=gcur</TT>" from the CL.
  <P>
  If one wishes to recall the last plot after the task which created it has
  exited, and the screen has since been cleared, the plot will still be in
  the frame buffer and can be redrawn by entering cursor mode and typing 0
  (the digit zero).  If the desired plot was not the last one plotted,
  hence is no longer in the frame buffer, it can still be recalled if it
  was saved earlier in a metacode file on disk.  The command "<TT>:.read fname</TT>"
  will refill the frame buffer from file "<TT>fname</TT>", and redraw the plot.
  <P>
  All graphics instructions output since the last time the device screen was
  cleared reside in the frame buffer unless there is an extremely large amount
  of information in the plot, in which case only the last part of the plot
  will be saved (the frame buffer dynamically sizes itself to fit the frame,
  but there is a fixed upper limit on its size of about 100 Kb).
  <P>
  </UL>
  <! EndSection:   'The Frame Buffer'>
  <H3>3.2 filling and writing the frame buffer</H3>
  <! BeginSection: 'Filling and Writing the Frame Buffer'>
  <UL>
  <P>
      The graphics system will automatically clear the frame buffer whenever
  the screen is cleared when plotting.  For example, in a heavy interactive
  graphics session, the frame buffer will be filled and cleared many times,
  and at the end only the last screenfull will be left in the frame buffer.
  When reading a metacode file containing several frames with "<TT>:.read</TT>",
  all frames will be plotted in sequence, but only the last one will remain
  in the buffer when the sequence finishes.
  <P>
  Some tasks have application-specific functions that append to, rather than
  overwrite the frame buffer.  For example, the "<TT>j</TT>" function in <B>implot</B>
  plots another line from the image.  On the screen the previous data vectors
  are erased and the new ones drawn over.  However, if you then do a zoom or
  a reset screen, you will see EACH of the sets of data vectors drawn in
  succession (some people unfairly consider this to be a bug, but actually it
  is a highly desirable feature which we are justifiably proud of).  
  <P>
  The contents of the frame buffer may be written to a metacode file
  with "<TT>:.write file</TT>".  By default the frame buffer is appended to the
  file if it already exists.  If you wish to "<TT>clobber</TT>" an existing file,
  use "<TT>:.write! file</TT>".  Also by default, the frame that is written is what
  you currently see on the screen, i.e., if you have zoomed in on a feature
  only what you see on the screen will be saved.  To write the full frame
  (the one you would see if you first did a "<TT>0</TT>"), use "<TT>:.write+ file</TT>".
  To overwrite an existing metacode file in full-frame mode, use "<TT>:.write!+ file</TT>".
  <P>
  </UL>
  <! EndSection:   'Filling and Writing the Frame Buffer'>
  <H3>3.3 moving the cursor and modifying the display area</H3>
  <! BeginSection: 'Moving the Cursor and Modifying the Display Area'>
  <UL>
  <P>
      A number of special keystrokes are recognized for interactive
  display control.  These keystrokes may be used to redraw all or
  any portion of the spooled graphics; e.g., one may zoom in on
  a portion of the plot and then roam about on the plot at high
  magnification.  Since the spooled graphics vectors often contain
  more information than can be displayed at normal magnification, zooming
  in on a feature may bring out additional detail (the maximum resolution
  is 32768 points in either axis).  Increasing the magnification will
  increase the precision of a cursor read by the same factor.
  <P>
  If the graphics frame is a typical vector plot with drawn and labeled
  axes, magnifying a portion of the plot may cause the axes to be lost.
  If this is not what is desired a keystroke ("<TT>A</TT>") is provided to draw and label
  the axes of the displayed window.  The axes will be overplotted on the
  current display and will not be saved in the frame buffer, hence they
  will be lost when the frame is redrawn.  New axes may optionally be drawn
  every time the viewport changes after entry of the command "<TT>:.axes+</TT>".
  In cursor mode the viewport is the full display area of the output device,
  hence the tick mark labels of the drawn axes are drawn inside the viewport,
  on top of the data.
  <P>
  By default the cursor mode keystrokes are all upper case letters, reserving
  lower case for applications programs.  The terminal shift lock key may be
  used to simplify typing in lengthy interactive cursor mode sessions.
  Most of the upper-case commands involve moving the graphics cursor
  and/or re-displaying a different part of the plot.  Special keystrokes
  are provided for stepwise cursor motions to increase the speed of cursor
  setting on terminals that do not have fast cursor motions (e.g., the
  Retro-Graphics enhanced VT100).  These keystrokes will only work if the terminal
  you are using permits positioning of the cursor under software control.
  <P>
  The commands H, J, K, and L (upper case!) move the cursor left, down, up,
  and right (as in the VI text editor and in Forth/Camera graphics).
  The step size of each cursor motion can change in one of three ways.
  "<TT>F</TT>" increases the step size by a factor over the current step size each
  time it is used; "<TT>V</TT>" decreases it similarly.
  <P>
  In practice the F/V speed keys are rarely used because the cursor positioning
  algorithm will automatically adjust the step size as you move the cursor.
  A large step size is used to cross the screen, then the step size is
  automatically decreased as you get close to the desired feature.
  Some practice is required to become adept at this, but soon it becomes
  natural and fast.
  <P>
  Arrow keys, thumbwheels, etc., if present on a keyboard, may also be used
  for cursor motions.  However, moving the cursor this way does not
  automatically report the position to the graphics system, thus if the
  command "<TT>C</TT>" is given, you will not get a position report after each motion.  
  <P>
  The numeric keypad of the terminal (if it has one) is used to roam about
  when the zoom factor is greater than one.  A numeric key must be escaped
  to use it to exit cursor mode, i.e., if the applications program reading
  the cursor recognizes the digit characters as commands.
  The directional significance of the numeric keys in roam mode is obvious
  if the terminal has a keypad, and is illustrated below.
  <P>
  <P>
  <PRE>
  	7   8   9	135 090 045
  <P>
  	4   5   6	180 000 000
  <P>
  	1   2   3      -135 -90 -45
  </PRE>
  <P>
  <P>
  Even if the terminal has a keypad, it may not be possible to use it for
  roam on some terminals.  If the keypad does not work, the normal numeric
  keys at the top of the keyboard will, after a glance at the keypad to
  see which digit to use.
  <P>
  </UL>
  <! EndSection:   'Moving the Cursor and Modifying the Display Area'>
  <H3>3.4 reporting and marking the cursor position</H3>
  <! BeginSection: 'Reporting and Marking the Cursor Position'>
  <UL>
  <P>
      To print the current cursor position in world coordinates without
  exiting cursor mode use the <TT>`C'</TT> keystroke.
  <P>
  If the cursor mode option "<TT>:.markcur+</TT>" is set, the position of the cursor
  will be marked with a small plus sign when time cursor mode exits,
  returning the cursor position to the calling program.  This is useful
  when marking the positions of a large number of objects, to keep track
  of the objects already marked.  The cursor position will not be marked until
  cursor mode exits, i.e., no cursor mode command will cause the mark to be
  drawn.  The mark cursor option remains in effect until you explicitly turn
  it off with "<TT>:.markcur-</TT>" or by typing <I>gflush</I>.  The marks are drawn
  in the frame buffer, hence they will survive zoom and roam or screen reset
  (they can be erased with repeated B commands if desired).
  <P>
  Some plots have more than one world coordinate system (WCS, the third value
  in the cursor value string).  Suppose you are in cursor mode and the frame
  contains two separate plots, or there is only one plot but the lower x-axis
  is in Angstroms while the upper one is in inverse centimeters.  By default
  the graphics system will automatically select the WCS (viewport) closest to
  the position of the cursor, returning a cursor position in that coordinate
  system.  If this is not what is desired, move the cursor to a position
  that belongs unambiguously to one of the coordinate systems and type "<TT>W</TT>".
  Subsequent cursor reads will refer to the coordinate system you have
  specified, regardless of the position of the cursor on the screen.
  When the frame is cleared the WCS "<TT>lock</TT>" will be cleared as well.
  <P>
  </UL>
  <! EndSection:   'Reporting and Marking the Cursor Position'>
  <H3>3.5 annotating plots</H3>
  <! BeginSection: 'Annotating Plots'>
  <UL>
  <P>
      The "<TT>T</TT>" command will prompt you for a text string to be entered from the
  keyboard, followed by a RETURN.  The text will appear on the screen (and get
  stored in the frame buffer), normally located with its lower left corner at
  the current cursor position.  This command may be used in conjunction with
  the "<TT>D</TT>" command to draw a line from the text annotation to a feature of
  interest in the plot.  Notice that the text size is constant in cursor
  mode regardless of the current magnification.  In order that text entered
  with "<TT>T</TT>" will look as nearly the same as possible on a hardcopy snapshot
  as it does on the screen, you should set text quality to high.
  <P>
  Text attributes are controlled by two command options.  Use "<TT>:.txqual</TT>" to
  set text quality to "<TT>normal</TT>" (the default), "<TT>low</TT>", "<TT>medium</TT>", or "<TT>high</TT>".
  Low-quality text plots the fastest, high-quality the slowest.  On terminals
  with hardware text generation such as the Retro-Graphics Enhanced VT100,
  low-quality characters may always come out 
  upright, even if the whole text string's up-vector is not at 90 degrees.
  <P>
  Low-quality text sizes are also fixed on most devices, so in a hardcopy
  snapshot of a plot the text will not necessarily look the same as it did
  on the screen (in particular it may overwrite data vectors).
  With low-quality text other options such
  as "<TT>font=italic</TT>" will not work on most terminals (although they may come
  out correctly on a hardcopy device).  In general, set "<TT>:.txqual=h</TT>" if you are
  planning to get hardcopy output from a plot you are annotating.  Changing
  the text quality only applies to text entered with "<TT>T</TT>" AFTER the change;
  you cannot automatically set all text to high quality after you have 
  entered it.
  <P>
  There are several ways to change the position of text relative to the
  cursor, its size, font, and orientation.  Use "<TT>:.txset</TT>" to change the
  text drawing parameters as follows:
  <PRE>
  <P>
      keyword	values					default
  <P>
      up		degrees counterclockwise, zero = +x	90
      size	character size scale factor		1.0
      path	left, right, up, down			right
      hjustify	normal, center, left, right		left
      vjustify	normal, center, top, bottom		bottom
      font	roman, greek, italic, bold		roman
      quality	normal, low, medium, high		normal
      color	integers greater than one		1
  <P>
  </PRE>
  The "<TT>up</TT>" keyword controls the orientation of the character and the whole
  text string.  A text string oriented at +45 degrees to the horizontal, 
  from left to right, would have "<TT>up=135</TT>".
  <P>
  Character sizes are all specified relative to a base size characteristic
  of each plotting device.  The size is a linear magnification factor, so
  "<TT>size=2.0</TT>" results in a character with four times the area.
  <P>
  Path is relative to the up vector; a string of characters consecutively
  underneath each other with the normal upright orientation would have 
  "<TT>up=90;path=down</TT>".
  <P>
  The justify parameters refer to the placement of the entire text string
  relative to the current cursor position.  To center a text string horizontally
  over a spike in a plot, position the cursor to just above the spike and
  set "<TT>h=c;v=b</TT>".
  <P>
  Font and quality were discussed above.  Setting the color will only have
  an effect on devices supporting it; if you have a color pen plotter, you
  must remember the current color setting, because there you cannot see it
  on the screen ("<TT>:.show</TT>" will reveal it however).
  <P>
  If you make a mistake or don't like the appearance of the text you entered,
  all is not lost.  Use the command "<TT>B</TT>" to back up over the last instruction
  and redraw (e.g. with "<TT>0</TT>") until you're ready to reenter the text.  If you
  back up one instruction too far (you lose some of the data vectors for
  instance) just type "<TT>U</TT>" to undo the last frame buffer edit, i.e. the backup.
  <P>
  For example, to annotate a spectral line with "<TT>H-alpha</TT>", written sideways
  up the screen from the current position in italics:
  <PRE>
  <P>
  	:.txqual high
  	:.txset up=180;font=italic
  	T
  	text: H-alpha
  <P>
  </PRE>
  On the last line, cursor mode provided the "<TT>text: </TT>" prompt.  The
  format could have been shortened to "<TT>u=180;f=i</TT>".
  <P>
  </UL>
  <! EndSection:   'Annotating Plots'>
  <H3>3.6 hardcopy snapshots</H3>
  <! BeginSection: 'Hardcopy Snapshots'>
  <UL>
  <P>
      There are two main ways to get a hardcopy of the frame buffer.  To 
  get a copy of what you see on the screen directly on a hardcopy plotter,
  simply use "<TT>:.snap plottername</TT>".  When you do so, you are actually sending
  the output down a buffered stream.  That is, you can do several "<TT>:.snap</TT>"'s
  before anything actually comes out on the plotter.  This is because many
  plotters use several pages worth of blank paper before and after the actual
  plot.  If you are planning to make a number of snapshots in succession,
  even if they are from different "<TT>=gcur</TT>" sessions, simply use "<TT>:.snap</TT>" for
  each one until you are done, then issue "<TT>:.gflush</TT>".  You can also flush
  graphics output to a plotter from the CL using the Language Package task
  <B>gflush</B>:
  <P>
  <PRE>
  	cl&gt; =gcur
  	...
  	:.snap versatec
  	...
  	:.snap versatec
  	&lt;RETURN&gt;
  	cl&gt;
  	cl&gt; gflush
  <P>
  </PRE>
  <P>
  Alternatively, you can use "<TT>:.write mcodefile</TT>" as discussed above, appending
  as many different frames as you wish, then later from the CL, send the
  metacode file to a plotter with one of the graphics kernels:
  <P>
  <PRE>
  	cl&gt; implot
  	...				(interactive session)
  	:.write file1.mc
  	&lt;RETURN&gt;
  	cl&gt; stdplot file1.mc
  <P>
  		or
  <P>
  	cl&gt; calcomp file1.mc		(etc.)
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'Hardcopy Snapshots'>
  <H3>3.7 alternate cursor input</H3>
  <! BeginSection: 'Alternate Cursor Input'>
  <UL>
  <P>
      Any program which uses cursor input may be run non-interactively as well
  as in batch mode.  For example, suppose the task has a cursor type parameter
  called "<TT>coords</TT>".  In normal interactive use a hardware cursor read will
  occur every time the program reads the value of the "<TT>coords</TT>" parameter.
  To run the program in batch mode we must first prepare a list of cursor
  values in a text file, e.g., with the <I>rgcursor</I> or <I>rimcursor</I> tasks
  in the <I>lists</I> package.  We then run the task assigning the name of the
  cursor list file to the parameter "<TT>coords</TT>".  For example, to run the
  <I>apphot</I> task in batch, with the cursor list in the file "<TT>starlist</TT>":
  <P>
  	cl&gt; apphot arg1 arg2 ... argN coords=starlist &amp;
  <P>
  The program will then read successive cursor values from the starlist file,
  not knowing that the cursor values are coming from a text file rather than
  from actual cursor reads.
  <P>
  A second mechanism is available for redirecting cursor input to the
  terminal.  This is most useful when working from a terminal that does not
  have graphics, or when debugging software.  To work this way one must
  first set the value of the environment variable <I>stdgcur</I> (for the
  graphics cursor) or <I>stdimcur</I> (for the image cursor).  Set the value
  to "<TT>text</TT>" to direct cursor reads to the terminal, e.g.:
  <P>
  	cl&gt; set stdgcur = text
  <P>
  The cursor value will then be a line of text read from the user terminal.
  In this mode the user enters at least two of the fields defining a cursor
  value.  Missing fields are assigned the value zero (the user presumably
  will know that the program does not use the extra fields).
  <P>
  <PRE>
  	cl&gt; = gcur
  	gcur: 345.33 23.22 1 c
  	345.33 23.22 1 c
  	cl&gt;
  </PRE>
  <P>
  An example of a cursor read request entered interactively by the user,
  taking input from the terminal and sending output to the terminal,
  is shown above (the CL typed the "<TT>gcur: </TT>" query and the user entered the
  remainder of that line).  If the cursor device were "<TT>stdgraph</TT>" a real
  cursor read would occur and the equivalent interaction might appear as
  shown below.  The cursor position is returned in world coordinates,
  where the world coordinate system was defined by the last plot output to
  the device.  For an imaging device the world coordinates will typically
  be the pixel coordinates of the image section being displayed.
  <P>
  <PRE>
  	cl&gt; = gcur
  	345.33 23.22 1 c
  	cl&gt;
  </PRE>
  <P>
  Redirecting cursor input to the terminal is useful when working from a
  non-graphics workstation and when debugging programs.  ASCII cursor queries
  are the only type supported when running an IRAF program outside the CL.
  Cursor input may also be taken from a list file by assigning a filename
  to a cursor parameter, i.e., by assigning a list file to a list structured
  parameter and overriding query mode:
  <P>
  <PRE>
  	cl&gt; gcur = filename
  	cl&gt; = gcur
  	345.33 23.22 1 c
  	cl&gt;
  </PRE>
  <P>
  </UL>
  <! EndSection:   'Alternate Cursor Input'>
  <H3>3.8 examining the status of the graphics system</H3>
  <! BeginSection: 'Examining the Status of the Graphics System'>
  <UL>
  <P>
      The command "<TT>:.show</TT>" writes out a page of information concerning the
  state of the graphics system.  This is an example of such a status report:
  <P>
  <PRE>
      Cursor Mode Parameters:
  <P>
  	case	= YES
  	markcur = YES
  	page	= YES
  	axes	= NO
  	view	= full screen
  	keys	= ABCDEFGHIJKLMNOPQRSTUVWXYZ&lt;&gt;0123456789?:
  		-&gt;ABCDEFGHIJKLMNOPQRSTUVWXYZ&lt;&gt;0123456789?:
  <P>
  <P>
      Graphics Kernel Status:
  <P>
  	STDGRAPH: kernel=cl, device=vt640
  	    memory=9472 (8192fb+256sb+1024fio), frame=1114+0 words
  	    spool=yes, nopen=0, pid=0, in=0, out=0, redir=-6, wcs=0
  	    text size = 1., up=90, path=right, hj=left, vj=bottom, color=1
  <P>
  	STDIMAGE:	disconnected
  	STDPLOT:	disconnected
  </PRE>
  <P>
  The cursor mode parameters report the current values of the "<TT>:.</TT>" command
  options; these options are in effect for all of three the standard graphics
  streams, i.e., STDGRAPH (the graphics terminal), STDIMAGE (the image display),
  and STDPLOT (batch plotters).
  <P>
  The graphics kernel status reports the status of each of the three graphics
  streams.  These streams are independent and in principle any graphics device
  may be connected to any stream.  The <I>kernel</I> field gives the name of
  the kernel connected to that stream, if any.  The value "<TT>cl</TT>" refers to the
  <I>stdgraph</I> kernel, which is built into the CL, and which can only talk
  to graphics terminals.  Any other value is the filename of an external graphics
  kernel, running as a subprocess of the CL process.  The <I>device</I> field
  gives the name of the device named in the last "<TT>open workstation</TT>" command
  on that stream.  This is the device the stream is currently writing plots to.
  <P>
  The significance of the remaining kernel status fields is described below.
  <P>
  <P>
  <PRE>
  	memory		- total memory used, chars
  	fb		- size of primary frame buffer, chars
  	sb		- size of scratch frame buffer (used by A)
  	fio		- size of the FIO buffer for the stream
  	frame		- amount of data in the frame + data in SB
  <P>
  	spool		- enable spooling of graphics in frame buffer?
  	nopen		- open count (should be zero)
  	pid		- process id of kernel subprocess
  	in		- fd of process in, if subkernel
  	out		- fd of process out, if subkernel
  	redir		- redirection information for pseudofile i/o
  	wcs		- current WCS, zero if not locked with W
  <P>
  	text size	- current text size relative to device's base size
  	up		- text up vector
  	path		- text character drawing path
  	hj		- horizontal justification
  	vj		- vertical justification
  	color		- index of current color attribute
  </PRE>
  <P>
  <P>
  This status report reflects only the information known to the CL.  The graphics
  subkernels, which are subprocesses of the CL, may themselves have subprocesses,
  sometimes on different nodes in the local network.
  <P>
  </UL>
  <! EndSection:   'Examining the Status of the Graphics System'>
  <H3>3.9 initializing the graphics system</H3>
  <! BeginSection: 'Initializing the Graphics System'>
  <UL>
  <P>
      The graphics system can normally be initialized by typing <I>gflush</I>.
  This will clear the frame buffer and disconnect all kernels, freeing memory
  and file descriptors, and reducing the subprocess count.  Shutting down a
  graphics subkernel automatically flushes any buffered graphics output.
  The CL automatically calls <I>gflush</I> during logout to shutdown the
  graphics system in an orderly fashion.
  </UL>
  <! EndSection:   'Initializing the Graphics System'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Despite the fact that the CL has graphics and image cursor access capabilities,
  there is no guarantee that one can access the cursor on a particular device.
  A <I>graphcap</I> entry for the device is also required, as is a graphics kernel
  if the device is not a conventional graphics terminal (e.g., an image display).
  If all of these pieces are not in place, the system will abort the cursor
  read, complaining that it cannot find a termcap or graphcap entry for the
  device, or that it cannot open a connected subprocess (the subkernel).
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  The GIO Reference Manual
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'Introduction' 'Overview' 'Invoking Cursor Mode' 'Cursor Mode Help' 'Cursor Mode Commands and Options' 'Advanced Usage' 'The Frame Buffer' 'Filling and Writing the Frame Buffer' 'Moving the Cursor and Modifying the Display Area' 'Reporting and Marking the Cursor Position' 'Annotating Plots' 'Hardcopy Snapshots' 'Alternate Cursor Input' 'Examining the Status of the Graphics System' 'Initializing the Graphics System' 'BUGS' 'SEE ALSO'  >
  
