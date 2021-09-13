.. _calcomp:

calcomp — Plot metacode on a Calcomp pen plotter
================================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  calcomp -- plot a GKI metacode file on a Calcomp pen plotter
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  calcomp input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Name of input GKI metacode file, file template, or list of files.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>calcomp</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "calcomp"'>
  <DD>Name of the destination plotter (as referenced in graphcap).
  </DD>
  </DL>
  <DL>
  <DT><B>generic = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no'>
  <DD>Ignore remaining kernel dependent parameters -- if yes, then none of the
  following parameters will be used; this is automatically the case, for
  instance, when using "<TT>:.snap calcomp</TT>" from cursor mode.
  </DD>
  </DL>
  <DL>
  <DT><B>debug = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='debug' Line='debug = no'>
  <DD>Print decoded graphics instructions during processing -- print each GKI 
  metacode instruction on standard output.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print elements of polylines, etc. in debug mode -- if yes, this is essentially
  all of the information present in the input metacode file.
  </DD>
  </DL>
  <DL>
  <DT><B>gkiunits = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gkiunits' Line='gkiunits = no'>
  <DD>Print coordinates in GKI rather than NDC units if in debug mode.
  </DD>
  </DL>
  <DL>
  <DT><B>xscale = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xscale' Line='xscale = INDEF'>
  <DD>X scale in device units per GKI unit; e.g. 0.0003 is 3 ten-thousandths of an
  inch per GKI unit on a plotter calibrated in inches; normally a plot is 32767
  GKI units wide.  If the plotting task that generated the metacode file generated
  a scale, this will be used if xscale is INDEF.  Specify xscale only if you wish
  to override the scale in the metacode.
  </DD>
  </DL>
  <DL>
  <DT><B>yscale = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='yscale' Line='yscale = INDEF'>
  <DD>Y scale in device units per GKI unit -- see xscale.
  </DD>
  </DL>
  <DL>
  <DT><B>txquality = "<TT>normal</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='txquality' Line='txquality = "normal"'>
  <DD>Text quality; "<TT>normal</TT>" means use the text quality specified in the metacode
  file.  "<TT>Low</TT>" means override the metacode font with the Calcomp symbol font,
  while "<TT>medium</TT>" and "<TT>high</TT>" use IRAF fonts.  There is little difference in speed
  with the different fonts, except if the text is bold, in which case "<TT>high</TT>"
  takes twice as long as "<TT>low</TT>" or "<TT>medium</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>lwtype = "<TT>ntracing</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lwtype' Line='lwtype = "ntracing"'>
  <DD>Type of line and text width implementation.  "<TT>Ntracing</TT>" causes the pen plotter
  to draw each line or character several times with slight offsets to simulate 
  boldness.  "<TT>Penchange</TT>", if implemented in the local Calcomp library, would
  cause the plotter to pause for an operator to change the pen when bold lines
  or text are requested.
  </DD>
  </DL>
  <DL>
  <DT><B>ltover = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ltover' Line='ltover = no'>
  <DD>Line type override, if yes, causes the pen plotter to draw all lines solidly,
  rather than as dashed or dotted lines if these are specified in the metacode.
  This may be desired for previewing a plot quickly.
  </DD>
  </DL>
  <DL>
  <DT><B>lwover = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lwover' Line='lwover = yes'>
  <DD>Line width override; causes all lines and text to come out with single width
  in order to speed up plotting.  If bold text, axes, etc. are desired and
  present in the parent plot, then set lwover = no.
  </DD>
  </DL>
  <DL>
  <DT><B>lcover = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lcover' Line='lcover = no'>
  <DD>Line color override, if yes, causes the pen plotter to ignore any requests in
  the metacode for a colored pen change.  Pen change is not implemented at all
  sites with Calcomp plotters.
  </DD>
  </DL>
  <DL>
  <DT><B>dashlen = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dashlen' Line='dashlen = INDEF'>
  <DD>Length of the dash in dashed lines in device units, usually inches.  Shorter
  dashes usually take longer to plot but may look nicer.  If left INDEF, a
  local default from dev$graphcap will be used; a good range is 0.1 to 0.5 inches.
  </DD>
  </DL>
  <DL>
  <DT><B>gaplen = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gaplen' Line='gaplen = INDEF'>
  <DD>Length of the gap in dashed or dotted lines, in device units.  Longer gaps 
  result in faster plotting at the expense of clarity.  If left INDEF, a local
  default from dev$graphcap will be used.  A good range is 0.05 to 0.2 inches.
  </DD>
  </DL>
  <DL>
  <DT><B>plwsep = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plwsep' Line='plwsep = INDEF'>
  <DD>Parallel line width separation -- if bold lines are implemented with "<TT>lwtype
  = ntracing</TT>", this is the right-angle distance between adjacent traces.  If
  INDEF, a local default is used from the device table dev$graphcap.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <B>calcomp</B> is an IRAF graphics kernel.  It may be run standalone to
  plot a GKI metacode file, or from cursor mode via "<TT>:.snap calcomp</TT>".
  <P>
  <B>Calcomp</B> may be used to draw any IRAF plot on a Calcomp pen plotter.  It is
  only available if the local site has a Calcomp library.  Task <B>calcomp</B>
  is an exact-scaling graphics kernel, unlike the NSPP, or STDPLOT kernel.
  This means that if the task that generated the metacode input file passed an
  exact scale into the metacode, data can be plotted to a desired precise scale.
  <P>
  The metacode scale may be overridden, or metacode files generated by tasks that
  do not implement exact scales may be plotted to a precise scale, by specifying
  xscale or yscale.  Note, however, that the only coordinates in a metacode file
  are GKI coordinates, usually running from 1 - 32767.  This means that to use
  xscale and yscale, the user must calculate the number of inches per GKI unit,
  not the number of world or data units per inch.
  <P>
  <B>Calcomp</B> also implements dashed and dotted lines and bold lines and text.
  Thus high-quality plots may be produced, at the expense of requiring more time.
  If "<TT>lwtype=ntracing</TT>" and "<TT>lwover=no</TT>", any bold text or lines in the metacode
  file, such as are produced for axes, tickmarks, titles and axis labels by many
  IRAF plotting tasks, will appear bold on the Calcomp.  If txquality="<TT>low</TT>" or
  "<TT>medium</TT>", and bold text is requested, each character will be drawn 5 times --
  once in the center position and once to the right, top, left, and bottom of
  the original position.  Each of the side positions is drawn "<TT>plwsep</TT>" inches
  from the center.  If txquality="<TT>high</TT>", bold text is implemented with the same
  five tracings plus the four corners upper right, upper left, etc.  For most
  applications txquality="<TT>normal</TT>" or "<TT>medium</TT>" is adequate for nice-looking
  plots.
  <P>
  When drawing data lines bold (only possible if the task originating the 
  metacode specifically requested it, not the case for most IRAF plotting
  tasks), the bounding parallel line traces are constructed to meet at sharp
  points.  This looks fine for line intersections that are not too acute.  If
  the intersection angle between two lines is very acute, say less than 5
  degrees, the vertex of the parallel lines bounding to the outside may lie
  quite a distance away from the actual vertex.  In the limit, if the 
  intersection angle is zero, the outer vertex will lie at infinity.  For
  this reason, all intersection angles less than 5 degrees are treated as
  though they were exactly 5 degrees.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Plot a metacode file exactly as is:
  <P>
      cl&gt; calcomp metacodefile
  <P>
  2. Get the fastest plot you can -- no bold lines or text, no dashed or dotted
  lines:
  <P>
      cl&gt; calcomp metacodefile lwover+ ltover+ txquality=low
  <P>
  3. Get a plot half the size of the original; suppose the original plot had
  metacode scales = 0.0003 inches / GKI unit:
  <P>
      cl&gt; calcomp metacodefile xscale=0.00015 yscale=0.00015
  <P>
  4. Get the highest quality plot you can without having to change pens:
  <P>
      cl&gt; calcomp metacodefile txqual=high 
  <P>
  5. Get a high-quality plot where you have to change the pen each time the
  metacode switches from bold to single-width lines or text:
  <P>
      cl&gt; calcomp metacodefile txqual=high lwtype=penchange
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  Pen plotters vary considerably in their plotting rates.  At NOAO, plotting a
  metacode file from a 1024-pixel image generated by <B>longplot</B>, overriding
  bold lines and text, takes a couple of minutes.  The same plot with txquality
  = "<TT>medium</TT>" can take over twice as long due to bold text, axes, and tick labels.
  With txquality = "<TT>high</TT>", it may take 4 or 5 times as long to plot.
  <P>
  Plots with dashed and dotted, or both, lines may take 2-5 times as long to 
  plot as single-width lines.  The slowest of all is to produce plots with
  a lot of bold text, or with dashed and dotted AND bold data lines.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  When using multiple tracing to simulate bold lines that intersect at very
  acute angles, i.e. less than 5 degrees, each bold line will thin slightly
  as it approaches the obtuse vertex.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  See task <B>longplot</B>, also in the plot package, for a task designed to
  use the <B>calcomp</B> graphics kernel for exact scaling and/or long, e.g.
  spectral, plots.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
