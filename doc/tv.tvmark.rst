tvmark — Mark objects on the image display
==========================================

**Package: tv**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tvmark (Dec89)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.tv</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tvmark (Dec89)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tvmark</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tvmark -- mark objects on the image display 
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tvmark frame coords
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_frame">frame</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame' Line='frame'>
  <DD>The frame or image plane number of the display to be marked. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_coords">coords </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords '>
  <DD>The text file containing the coordinates of objects to be
  marked, one object per line with x and y in columns 1 and 2 respectively.
  An optional label may be read out of the third column.
  If <I>coords</I> = "<TT></TT>", the coordinate file is undefined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfile">logfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = ""'>
  <DD>The text file in which image cursor commands typed in interactive mode
  are logged. If <I>logfile</I> = "<TT></TT>" no commands are logged.
  If automatic logging is enabled, all cursor commands
  are logged, otherwise the user must use the interactive keep keystroke
  command to select specific cursor commands for logging.
  Commands are not logged in non-interactive mode.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_autolog">autolog = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='autolog' Line='autolog = no'>
  <DD>Automatically log all cursor commands in interactive mode.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outimage">outimage = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outimage' Line='outimage = ""'>
  <DD>The name of the output snapshot image.
  If tvmark is run in non-interactive mode and no command file is specified,
  a copy of the frame buffer
  is automatically written to the IRAF image <I>outimage</I> after tvmark
  terminates execution.
  If <I>outimage</I> = "<TT></TT>" no output image is written.
  In interactive mode or in non-interactive mode if a command file
  is specified, the user can make snapshots of the frame buffer
  with the interactive colon  write command.  In this case the name of the output
  snapped image will be in order of priority, the name specified
  by the user in the colon write ommand,  "<TT>outimage.snap.version</TT>",  or,
  "<TT>imagename.snap.version</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_deletions">deletions = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='deletions' Line='deletions = ""'>
  <DD>The extension of the output file containing objects which were deleted
  from the coordinate file in interactive or command file mode.
  By default no output deletions file is written.
  If <I>deletions</I> is not equal to the null string ("<TT></TT>"), then deleted
  objects are written to a file called <I>coords.deletions</I>. For
  example if <I>coords</I> = "<TT>nite1</TT>" and <I>deletions</I> = "<TT>del</TT>", then the
  deletions file will be called "<TT>nite1.del</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_commands">commands = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='commands' Line='commands = ""'>
  <DD>The text file containing the marking commands.
  In interactive mode if <I>commands</I> = "<TT></TT>", 
  <I>commands</I> is the image cursor.  In non-interactive mode
  cursor commands may be read from a text file, by setting <I>commands</I> =
  "<TT>textfile</TT>".  This file may be a user
  created command file, or the <I>logfile</I> from a previous run of tvmark.
  If <I>commands</I> = "<TT></TT>" in non-interactive mode, the default mark is drawn
  on the display at the positions of all the objects in <I>coords</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mark">mark = "<TT>point</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mark' Line='mark = "point"'>
  <DD>The default mark type.  The options are:
  <DL>
  <DT><B><A NAME="l_point">point</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='point' Line='point'>
  <DD>A point.  To ensure legibility <I>point</I> is actually a square dot whose
  size is specified by <I>pointsize</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_plus">plus</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='plus' Line='plus'>
  <DD>A plus sign.  The shape of the plus sign is determined by the raster font
  and its size is specified by <I>txsize</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cross">cross</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='cross' Line='cross'>
  <DD>An x.  The shape of the x is determined by the raster font and its size is
  is specified by <I>txsize</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_circle">circle</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='circle' Line='circle'>
  <DD>A set of concentric circles whose radii are specified by the <I>radii</I>
  parameter.  The radii are in image pixel units.  If the magnifications
  used by display are not equal in x and y circles will become ellipses
  when drawn.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rectangle">rectangle</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rectangle' Line='rectangle'>
  <DD>A set of concentric rectangles whose lengths and width/length ratio are
  specified by the <I>lengths</I> parameter.  The lengths are specified in
  image pixel units.  If the magnifications used by the display are not
  equal in x and y then squares will become rectangles when drawn.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radii">radii = "<TT>0</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radii' Line='radii = "0"'>
  <DD>If the default mark type is "<TT>circle</TT>" than concentric circles of radii
  "<TT>r1,r2,...rN</TT>" are drawn around each selected point.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lengths">lengths = "<TT>0</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lengths' Line='lengths = "0"'>
  <DD>if the default mark type is "<TT>rectangle</TT>" then concentric rectangles of
  length and width / length ratio "<TT>l1,l2,...lN ratio</TT>" are drawn around
  each selected point.  If ratio is not supplied, it defaults to 1.0
  and squares are drawn.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_font">font = "<TT>raster</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='font' Line='font = "raster"'>
  <DD>The name of the font.  At present only a simple raster font is supported.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_color">color = 255</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='color' Line='color = 255'>
  <DD>The numerical value or  color of the marks drawn.
  Any number between 0 and 255 may be specified.
  The meaning of the color is device dependent.
  In the current version of the Sun/IRAF IMTOOL numbers between 202
  and 217 may be used to display graphics colors.  The current color
  assignments for IMTOOL are summarized later in this help page.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_label">label = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='label' Line='label = no'>
  <DD>Label the marked coordinates with the string in the third column of
  the text file <I>coords</I>.  <I>label</I> overrides <I>number</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_number">number = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='number' Line='number = no'>
  <DD>Label the marked objects with their sequence number in the coordinate
  list <I>coords</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nxoffset">nxoffset = 0, nyoffset = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxoffset' Line='nxoffset = 0, nyoffset = 0'>
  <DD>The x and y offset in display pixels of the numbers to be drawn.
  Numbers are drawn by default with the lower left corner of the first
  digit at the coordinate list position.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pointsize">pointsize = 3</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pointsize' Line='pointsize = 3'>
  <DD>The size of the default mark type "<TT>point</TT>". Point size will be rounded up
  to the nearest odd number.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_txsize">txsize = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='txsize' Line='txsize = 1'>
  <DD>The size of text, numbers and the plus and cross marks to be written.
  The size is in font units which are 6 display pixels wide and 7 display 
  pixels high.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tolerance">tolerance = 1.5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tolerance' Line='tolerance = 1.5'>
  <DD>Objects marked by the cursor for deletion from the coordinate list
  <I>coords</I> must be less than or equal to <I>tolerance</I> pixels
  from the cursor position to be deleted. If 1 or more objects
  is closer than <I>tolerance</I>, the closest object is deleted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Interactive mode.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  TVMARK marks objects on the display by writing directly into
  the frame buffer specified by <I>frame</I>.  TVMARK can draw on
  any devices supported by the IRAF <I>display</I> program.
  After marking, the
  contents of the frame buffer may be written out to the IRAF image
  <I>outimage</I>.  The output image is equal in size and intensity
  to the contents of the frame buffer displayed at the time of writing.
  <P>
  In interactive mode objects to be marked may be selected interactively
  using the image cursor or read from the text file <I>coords</I>.
  Objects in the coordinate list
  may be selected individually by number,
  in groups by specifying a range of numbers, or the entire list may
  be read.  New objects may be added to the list interactively
  using the append keystroke command.  In batch mode cursor commands
  may be read from a text file by setting <I>commands</I> to the name
  of the text file.  This may be a user created file of cursor
  commands or a log file from a previous interactive run of TVMARK.
  If no command file is specified then all the objects in the coordinate
  list are marked with the default mark type /fImark/fR.
  <P>
  The mark commands entered in interactive mode can be saved in the text
  file <I>logfile</I>.  If <I>autolog</I>
  is enabled and <I>logfile</I> is defined all cursor commands
  are automatically logged.  If <I>autolog</I> is turned off then the user
  can select which commands are to be logged interactively using the
  interactive keep keystroke.
  <P>
  The default mark type are currently "<TT>none</TT>", "<TT>point</TT>", "<TT>plus</TT>", "<TT>cross</TT>",
  "<TT>circle</TT>", a
  list of concentric circles, and "<TT>rectangles</TT>", a list of concentric rectangles.
  The size of the "<TT>point</TT>" mark is set using the parameter <I>pointsize</I>
  while the sizes of the "<TT>plus</TT>" and "<TT>cross</TT>" mark types are set by the
  <I>txsize</I> parameter.  Txsize is in font units which for the simple raster
  font currently implemented is six display pixels in x and seven display 
  pixels in y.
  The <I>radii</I> and <I>lengths</I> parameters
  describe the concentric circles and concentric rectangles to be drawn
  respectively.
  If <I>number=yes</I> then objects in the coordinate list will be automatically
  numbered as well as marked.  The position of the number can be altered
  with the <I>nxoffset</I> and <I>nyoffset</I> parameters.
  <P>
  In interactive mode tvmark maintains a scratch buffer.  The user opens
  the scratch buffer by issuing a save command which saves the current
  contents of the frame buffer in a temporary IRAF image.
  The user can continue marking and if unsatisfied with the results
  restore the last saved copy of the frame buffer with the restore
  command. Subsections of the saved frame buffer can be restored to the
  current frame buffer with the erase keystroke command.
  Finally a snapshot of the frame buffer can be saved permanently by
  using the write command. These snapped images can be redisplayed
  by setting the display task parameter <I>ztrans</I> = "<TT>none</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursor_commands">CURSOR COMMANDS</A></H2>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  <PRE>
                Interactive TVMARK Keystroke/Colon Commands
  <P>
  The following keystroke commands are available.
  <P>
      ?	    Print help
      +       Mark the cursor position with +
      x       Mark the cursor position with x
      .       Mark the cursor position with a dot
      c       Draw defined concentric circles around the cursor position
      r       Draw defined concentric rectangles around the cursor position
      s	    Draw line segments, 2 keystrokes
      v       Draw a circle, 2 keystrokes
      b       Draw a rectangle, 2 keystrokes
      f       Draw filled rectangle, 2 keystrokes
      e	    Mark region to be erased and restored, 2 keystrokes
  <P>
      -       Move to previous object in the coordinate list
      m       Move to next object in the coordinate list
      p	    Mark the previous object in the coordinate list
      n       Mark next object in the coordinate list	
      l	    Mark all the objects in the coordinate list
      o       Rewind the coordinate list
      a       Append object at cursor position to coordinate list and mark
      d	    Delete object nearest the cursor position in the coordinate list
  	    and mark
  <P>
      k       Keep last cursor command
      q       Exit tvmark
  <P>
  The following colon commands are available.
  <P>
     :show		     List the tvmark parameters
     :move N	       	     Move to Nth object in coordinate list
     :next N M                 Mark objects N to M in coordinate list
     :text      [string]       Write text at the cursor position
     :save		     Save the current contents of frame buffer
     :restore                  Restore last saved frame buffer
     :write     [imagename]    Write the contents of frame buffer to an image
  <P>
  The following parameters can be shown or set with colon commands.
  <P>
     :frame             [number]
     :outimage	      [imagename]
     :coords	      [filename]
     :logfile	      [filename]
     :autolog           [yes/no]
     :mark              [point|line|circle|rectangle|cross|plus]
     :radii             [r1,...,rN]
     :lengths           [l1,...,lN] [width]
     :font	      [raster]
     :color             [number]
     :number            [yes/no]
     :label	      [yes/no]
     :txsize	      [1,2,..]
     :pointsize	      [1,3,5...]
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H2><A NAME="s_current_imtool_colors">CURRENT IMTOOL COLORS</A></H2>
  <! BeginSection: 'CURRENT IMTOOL COLORS'>
  <UL>
  <P>
  <PRE>
  	  0 = sunview background color (normally white)
        1-200 = frame buffer data values, windowed
  	201 = cursor color (white)
  <P>
  	202 = black
  	203 = white
  	204 = red
  	205 = green
  	206 = blue
  	207 = yellow
  	208 = cyan
  	209 = magenta
  	210 = coral
  	211 = maroon
  	212 = orange
  	213 = khaki
  	214 = orchid
  	215 = turquoise
  	216 = violet
  	217 = wheat
  <P>
      218-254 = reserved for use by other windows
  	255 = black (sunview foreground color)
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURRENT IMTOOL COLORS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Display an image,  mark all the objects in the coordinate file 
  m92.coo.1 with red dots, and save the contents of the frame buffer
  in the iraf image m92r.snap. Redisplay the marked image.
  <P>
  <PRE>
      cl&gt; display m92r 1
      cl&gt; tvmark 1 m92.coo.1 outimage=m92r.snap col=204
      cl&gt; display m92r.snap 2 ztrans="none"
  </PRE>
  <P>
  2. Execute the same command only number the objects in the coordinate
  list instead of marking them.
  <P>
  <PRE>
      cl&gt; display m92r 1
      cl&gt; tvmark 1 m92.coo.1 outimage=m92r.snap mark=none\<BR>
      &gt;&gt;&gt;   number+ col=204
      cl&gt; display m92r.snap 2 ztrans="none"
  </PRE>
  <P>
  3. Display an image and draw concentric circles with radii of 5, 10 and
  20 pixels corresponding to an aperture radius and inner and outer
  sky annulus around the objects in the coordinate list. 
  <P>
  <PRE>
      cl&gt; display m92r 1
      cl&gt; tvmark 1 m92.coo.1 mark=circle radii="5,10,20" col=204
  </PRE>
  <P>
  4. Display an image, mark objects in a coordinate list with dots
  and append new objects to the coordinate file.
  <P>
  <PRE>
      cl&gt; display m92r 1
  <P>
      cl&gt; tvmark 1 m92.coo.1 interactive+
  	... type q to quit the help menu ...
  	... type :number yes to turn on numbering ...
  	... type l to mark all objects in the coordinate file
  	... move cursor to desired unmarked objects and type a
  	... type :write to take a snap shot of the frame buffer
  	... type q to quit
  </PRE>
  <P>
  5. Make a finder chart of a region containing 10 stars by drawing
  a box around the field, marking each of the 10 stars with a dot,
  labeling each with an id and finally labeling the whole field.
  Save all the keystroke commands in a log file.
  <P>
  <PRE>
      cl&gt; display m92r 1 log=m92r.log auto+
  <P>
      cl&gt; tvmark 1 "" interactive+
  <P>
  	... type q to quit the help menu ...
  <P>
  	... to draw a box around the finder field move the cursor to the
  	    lower left corner of the finder field and type b, move the
  	    cursor the upper right corner of the field and type b again
  <P>
  	... to mark and label each object move to the position of the
  	    object and type ., next move slightly away from the object
  	    and type :text id 
  <P>
  	... to label the chart with a title first type :txsize 2 for
  	    bigger text then move the cursor to the position where
  	    the title should begin and type :text title
  <P>
  	... save the marked image with :write
  <P>
  	... type q to quit the program
  </PRE>
  <P>
  6. Edit the log file created above to remove any undesired commands
  and rerun tvmark redirecting cursor input to the log file.
  <P>
  <PRE>
      cl&gt; display m92r 1
      cl&gt; tvmark 1 "" commands=logfile inter-
  </PRE>
  <P>
  7. Draw a box on the display with a lower left corner of 101,101 and an
  upper right corner of 200,200 using a simple cursor command file.
  Note than in interactive mode the b key is the one that draws a box.
  <P>
  <PRE>
  The command file contains the following 3 lines
  <P>
      101.0 101.0 101 b
      200.0 200.0 101 b
      200.0 200.0 101 q
  <P>
      cl&gt; display m92r 1
      cl&gt; tvmark 1 "" commands=commandfile inter-
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Tvmark is a prototype task which can be expected to undergo considerable
  modification and enhancement in the future. The current version of this
  task does not produce publication quality graphics.
  In particular aliasing is easily visible in the code which draws circles
  and lines.
  <P>
  Input from the coordinate list is sequential. No attempt has been made
  to arrange the objects to be marked in order for efficiency of input and
  output.
  <P>
  Note that the move command does not currently physically move the image
  cursor. However the next mark drawn will be at the current coordinate
  list position.
  <P>
  Users may wish to disable the markcur option in the imtool setup window
  before running tvmark.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  display, imedit, imexamine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'CURRENT IMTOOL COLORS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>