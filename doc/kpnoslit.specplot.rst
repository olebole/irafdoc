specplot — Stack and plot multiple spectra
==========================================

**Package: kpnoslit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>specplot (Jan96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>specplot (Jan96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>specplot</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  specplot -- stack and plot multiple spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  specplot spectra
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_spectra">spectra</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='spectra' Line='spectra'>
  <DD>List of spectra to plot.  The spectra are assigned index numbers increasing
  from one in the order of the list.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures to plot.  An empty list selects all apertures.
  An aperture list consists of a comma separated list of aperture numbers or
  hyphen separated range of numbers.  A step size may also be specified preceded
  by <TT>'x'</TT>.  See <B>ranges</B> for more.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bands">bands = "<TT>1</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bands' Line='bands = "1"'>
  <DD>List of bands to plot if the image is three dimensional.  The list has
  the same syntax as for the apertures.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dispaxis">dispaxis = 1, nsum = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dispaxis' Line='dispaxis = 1, nsum = 1'>
  <DD>Parameters for defining vectors in 2D images.  The
  dispersion axis is 1 for line vectors and 2 for column vectors.
  A DISPAXIS parameter in the image header has precedence over the
  <I>dispaxis</I> parameter.  These may be changed interactively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_autolayout">autolayout = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='autolayout' Line='autolayout = yes'>
  <DD>Automatically layout the spectra by shifting or scaling to a common mean
  and determining a separation step which does overlaps the spectra
  by the specified fraction?  The algorithm uses the following parameters.
  <DL>
  <DT><B><A NAME="l_autoscale">autoscale = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='autoscale' Line='autoscale = yes'>
  <DD>Scale the spectra to a common mean?  If no then the spectra are shifted
  to a common mean and if yes they are scaled to a common mean.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fraction">fraction = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fraction' Line='fraction = 1.'>
  <DD>The separation step which just avoids overlapping the spectra is multiplied
  by this number.  Numbers greater than 1 increase the separation while numbers
  less than 1 decrease the separation and provide some amount of overlap.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_units">units = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='units' Line='units = ""'>
  <DD>Dispersion coordinate units.  If the spectra have known units, currently
  this is generally Angstroms, the plotted units may be converted
  for plotting to other units as specified by this parameter.
  If this parameter is the null string then the units specified by the
  world coordinate system attribute "<TT>units_display</TT>" is used.  If neither
  is specified than the units of the coordinate system are used.
  The units
  may also be changed interactively.  See the units section of the
  <B>onedspec</B> help for a further description and available units.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_transform">transform = "<TT>none</TT>" (none|log)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transform' Line='transform = "none" (none|log)'>
  <DD>Transform for the input pixel values.  Currently only "<TT>log</TT>" is implemented.
  If all pixels are negative the spectrum values will be unchanged and if
  some pixels are negative they are mapped to the lowest non-negative value in
  the spectrum.  Note that this cannot be changed interactively or applied
  independently for each spectrum.  To change the setting one must exit
  the task and execute it with the new value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_scale">scale = 1., offset = 0. (value, @file, keyword)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = 1., offset = 0. (value, @file, keyword)'>
  <DD>The scale and offset to apply to each spectrum.  The value of the parameter
  may be a constant value applying to all spectra, a file containing the
  values specified as @&lt;file&gt; where &lt;file&gt; is the filename, or an image
  header keyword whose value is to be used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_step">step = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='step' Line='step = 0'>
  <DD>The step separating spectra when not using the autolayout option.
  The value of this parameter depends on the range of the data.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ptype">ptype = "<TT>1</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ptype' Line='ptype = "1"'>
  <DD>Default plotting type for the spectra.  A numeric value selects line plots
  while marker type strings select marker plots.  The sign of the line type
  number selects histogram style lines when negative or connected pixel
  values when positive.  The absolute value selects the line type with 0
  being an invisible line, 1 being a solid line, and higher integers
  different types of lines depending on the capabilities of the graphics
  device.  The marker type strings are "<TT>point</TT>", "<TT>box</TT>", "<TT>plus</TT>", "<TT>cross</TT>",
  "<TT>diamond</TT>", "<TT>hline</TT>", "<TT>vline</TT>", "<TT>hebar</TT>", "<TT>vebar</TT>", and "<TT>circle</TT>".
  The types for individual spectra may be changed interactively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_labels">labels = "<TT>user</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='labels' Line='labels = "user"'>
  <DD>Spectrum labels to be used.  If the null string or the word "<TT>none</TT>" is
  given then the spectra are not labeled.  The word "<TT>imname</TT>" labels the
  spectra with the image name, the word "<TT>imtitle</TT>" labels them wih the
  image title, the word "<TT>index</TT>" labels them with the index number, and
  the word "<TT>user</TT>" labels them with user defined labels.  The user labels
  may be given in the file specified by the parameter <I>ulabels</I>, which
  are matched with the list of spectra, and also added interactively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ulabels">ulabels = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ulabels' Line='ulabels = ""'>
  <DD>File containing user labels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xlpos">xlpos = 1.02, ylpos = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xlpos' Line='xlpos = 1.02, ylpos = 0.0'>
  <DD>The starting position for the spectrum labels in fractions of the
  graph limits.  The horizontal (x) position is measured from the left
  edge while the vertical position is measured from the mean value of the
  spectrum.  For vertical positions a negative value may be used to label
  below the spectrum.  The default is off the right edge of the graph at
  the mean level of the spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sysid">sysid = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sysid' Line='sysid = yes'>
  <DD>Include system banner and separation step label?  This may be changed
  interactively using ":/sysid"<TT>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_yscale">yscale = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='yscale' Line='yscale = no'>
  <DD>Draw a Y axis scale?  Since stacked plots are relative labeling the Y
  axes may not be useful.  This parameter allows adding the Y axis scale
  if desired.  The default is to not have a Y axis scale.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_title">title = </TT>""<TT>, xlabel = </TT>""<TT>, ylabel = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "", xlabel = "", ylabel = ""'>
  <DD>Title, x axis label, and y axis label for graphs.  These may be changed
  interactively using ":/title</TT>", ":/xlabel"<TT>, and ":/ylabel</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmin">xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmin' Line='xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF'>
  <DD>The default limits for the initial graph.  If INDEF then the limit is
  determined from the range of the data (autoscaling).  These values can
  be changed with <TT>'w'</TT> cursor key or the cursor commands ":/xwindow"<TT> and
  ":/ywindow</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfile">logfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = ""'>
  <DD>Logfile to record the final set of spectra and scale factors displayed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Output graphics device.  One of "<TT>stdgraph</TT>", "<TT>stdplot</TT>", "<TT>stdvdm</TT>",
  @(enviroment variable), or actual device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Graphics cursor input.  When null the standard cursor is used otherwise
  the specified file is used.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Specplot</B> plots multiple spectra with provisions for scaling them,
  separating them vertically, shifting them horizontally, and labeling them.
  The layout can be defined by an automatic algorithm or explicitly and
  adjusted noninteractively (with some limitations) or interactively.  The
  plotting units can be selected and the vertical axis scale can be shown or
  not as desired.  This task is used for compressing many spectra to a page
  for review, intercomparison of spectra, classification against standards,
  and final display.
  <P>
  The input list of spectra consists of one, two, or three dimensional images.
  The set of spectra may be restricted to specific apertures using the
  <I>apertures</I> parameter.  Note that for true 2D images, such as long slit
  spectra, the aperture number corresponds to the line or column to be plotted
  and the dispersion axis and nsum parameter are determined either from the
  image header or the package parameters.  Spectra extracted
  with the <B>apextract</B> package may be three dimensional where the 3rd
  dimension corresponds to related data.  The higher dimensional data is
  also plotted though it may be restricted with the <I>bands</I>
  parameter.
  <P>
  Each spectrum has a number of associated parameters which are initially
  assigned default values but which may be changed interactively.  First each
  spectrum is assigned an index number.  This is generally sequential
  starting from 1.  Spectra added interactively are assigned the next higher
  or lower index relative to the spectrum being appended or inserted.  The
  index is used for refering to parameters of a particular spectrum and for
  separating the spectra vertically.  The spectra are scaled and shifted by
  the equation
  <P>
  	I = value * scale + offset + (index - 1) * step
  <P>
  where "<TT>I</TT>" is the final plotted value, "<TT>value</TT>" is the pixel value, "<TT>scale</TT>"
  is a multiplicative scaling, "<TT>offset</TT>" is a additive offset, and "<TT>step</TT>" is
  an additive separation step used to stack spectra vertically.
  <P>
  The default values of the vertical scaling parameters may be set by an
  automatic layout algorithm or with explicit constants (the same for all
  spectra).  The automatic mode is selected with the parameter
  <I>autolayout</I> and works as follows.  All spectra are scaled or shifted
  to a common mean (depending on the parameter <I>autoscale</I>) relative to
  the lowest indexed spectrum.  A step size is then computed to just avoid
  overlapping of the minimum of one spectrum with the maximum of another.
  Note that this may not yield a good layout if the spectra have large
  continuum slopes.  Finally, to add some extra space between the spectra or
  to allow some overlap, the minimum step is multiplied by a specified
  overlap factor, <I>fraction</I>.
  <P>
  In nonautomatic mode the user specifies the intensity scale, offset,
  and separation step explicitly with the parameters, <I>scale, offset</I>
  and <I>step</I>.  If the step is zero then spectra will be directly
  overplotted while a positive or negative value will separate the
  spectra either upward or downward with the index 1 spectrum having no
  offset.  The scale and offset parameters may be specified as either
  constant values, the name of file containing the values (one per line)
  preceded by the <TT>'@'</TT> character, or the name of an image header keyword.
  This parameter as well as the scale and offset may be set or
  changed interactively via colon commands and the "<TT>offset</TT>" may also be
  set using the cursor to shift a spectrum vertically.
  <P>
  In addition to shifting spectra vertically they may also be shifted
  horizontally as a velocity/redshift or a zero point change with either
  cursor or colon commands.  The dispersion, inteval per pixel, may be
  modified, either with the <TT>'t'</TT> key or the "<TT>wpc</TT>" command, in which case if
  the dispersion is nonlinear the spectra will be linearized.
  <P>
  Each spectrum may have a label associated with it.  The label type may
  be the image name, the image title, the index number, or a user defined
  label.  The default label type is specified by the parameter
  <I>labels</I>.  For user labels the initial labels may be specified in a
  file.  Interactively the label type may be changed using the "<TT>:labels</TT>"
  command and the user assigned labels may be defined by a colon command
  or by using the cursor to mark the position for the label.  The label
  position is given relative to the range of the graph and the mean
  intensity.  The default values are set by the parameters <I>xlpos</I>
  and <I>ylpos</I>.  The positions may be changed interactively for all
  the spectra or individually.  The latter may be done using the cursor
  to mark exactly where the label is to go.
  <P>
  Each spectrum has an associated plotting type.  The default type which
  applies to all spectra initially is specified by the parameter
  <I>ptype</I>.  This parameter specifies both whether line mode or
  marker mode is used and the line type, line style, or marker type to use.
  The line
  mode and types are given by a small integers with the style, connected
  pixel centers or histogram style, chosed by the sign of the integer.
  The type of lines produced depend on the capabilities of the terminal.  In most
  cases a zero line type is invisible.  (This may be used interactively
  to temporarily eliminate a spectrum from a plot instead of deleting the
  spectrum from the list of spectra).  A line type of 1 is a solid line
  and additional line types are specified by higher numbers.
  The marker types are given by name as described in the parameter
  section.  There is currently no combination of line and marker (such as
  connected points with vertical bars) or histogram type plotting.  The
  plotting type may be changed interactively for individual spectra or
  for all spectra using colon commands.
  <P>
  The cursor and colon commands generally apply to the spectrum nearest
  the cursor.  This is determined by finding the nearest data point to
  the cursor.  For the colon commands the spectrum may also be specified
  explicitly by the index number using an optional suffix "<TT>[index]</TT>", where
  index is the index number for the spectrum.  Also the special index "<TT>*</TT>"
  may be specified to apply to all spectra.
  <P>
  The operations of adding, deleting, moving, or shifting spectra affect
  the index numbers of the other spectra.  When deleting a spectrum the
  index numbers of all spectra with greater index numbers are decreased
  by one resulting in the plotted spectra moving down (positive step).
  When adding a spectrum the index numbers above the inserted spectrum
  are increased by one resulting in the spectra moving up.  Moving a
  spectrum to a new index number is equivalent to deleting the spectrum
  and then inserting it at the new index position.  Spectra may be
  shifted to insert gaps in the plotted spectra.  The specified value is
  added to all spectra above and including the one indicated if the value
  is positive to all spectra below and including the one indicated if the
  value is negative.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursor_commands">CURSOR COMMANDS</A></H2>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The indicated spectrum is the one with a point closest to the cursor position.
  <PRE>
  <P>
  ? - Print help summary
  a - Append a new spectrum following the indicated spectrum
  i - Insert a new spectrum before the indicated spectrum
  d - Delete the indicated spectrum
  e - Insert last deleted spectrum before indicated spectrum
  f - Toggle between world coordinates and logical pixel coordinates
  l - Define the user label at the indicated position
  p - Define the label position at the indicated position
  o - Reorder the spectra to eliminate gaps
  q - Quit
  r - Redraw the plot
  s - Repeatedly shift the indicated spectrum position with the cursor
       q - Quit shift                      x - Shift horizontally in velocity
       s - Shift vertically in scale       y - Shift vertically in offset
       t - Shift horizontally in velocity  z - Shift horizontally in velocity
           and vertically in scale             and vertically in offset
  t - Set a wavelength scale using the cursor
  u - Set a wavelength point using the cursor
  v - Set velocity plot with zero point at cursor
  w - Window the plot
  x - Cancel all scales and offsets
  y - Automatically layout the spectra with offsets to common mean
  z - Automatically layout the spectra scaled to common mean
  </PRE>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H2><A NAME="s_colon_commands">COLON COMMANDS</A></H2>
  <! BeginSection: 'COLON COMMANDS'>
  <UL>
  <P>
  A command without a value generally shows the current value of the
  parameter while with a value it sets the value of the parameter.  The show
  commands print to the terminal unless a file is given.  For the spectrum
  parameters the index specification, "<TT>[index]</TT>", is optional.  If absent the
  nearest spectrum to the cursor when the command is given is selected except
  for the "<TT>units</TT>" command which selects all spectra.  The index is either a
  number or the character *.  The latter applies the command to all the
  spectra.
  <P>
  <PRE>
  :show &lt;file&gt;		   Show spectrum parameters (file optional)
  :vshow &lt;file&gt;		   Show verbose parameters (file optional)
  :step &lt;value&gt;		   Set or show step
  :fraction &lt;value&gt;	   Set or show autolayout fraction
  :label &lt;value&gt;		   Set or show label type
  				(none|imtitle|imname|index|user)
  <P>
  :move[index] &lt;to_index&gt;	   Move spectrum to new index position
  :shift[index|*] &lt;value&gt;	   Shift spectra by adding to index
  :w0[index|*] &lt;value&gt;	   Set or show zero point wavelength
  :wpc[index|*] &lt;value&gt;	   Set or show wavelength per channel
  :velocity[index|*] &lt;value&gt; Set or show radial velocity (km/s)
  :redshift[index|*] &lt;value&gt; Set or show redshift
  :offset[index|*] &lt;value&gt;   Set or show intensity offset
  :scale[index|*] &lt;value&gt;	   Set or show intensity scale
  :xlpos[index|*] &lt;value&gt;	   Set or show X label position
  :ylpos[index|*] &lt;value&gt;	   Set or show Y label position
  :ptype[index|*] &lt;value&gt;	   Set or show plotting type
  :color[index|*] &lt;value&gt;    Set or show color (1-9)
  :ulabel[index|*] &lt;value&gt;   Set or show user labels
  :units[index|*] &lt;value&gt;	   Change coordinate units
  <P>
  :/title &lt;value&gt;		   Set the title of the graph
  :/xlabel &lt;value&gt;	   Set the X label of the graph
  :/ylabel &lt;value&gt;	   Set the Y label of the graph
  :/xwindow &lt;min max&gt;	   Set the X graph range
  				(use INDEF for autoscaling)
  :/ywindow &lt;min max&gt;	   Set the X graph range
  				(use INDEF for autoscaling)
   
  <P>
  Examples:
      w0		  Print value of wavelength zero point
      w0 4010	  Set wavelength zero point of spectrum nearest the cursor
      w0[3] 4010	  Set wavelength zero point of spectrum with index 3
      w0[*] 4010	  Set wavelength zero point of all spectra
  </PRE>
  </UL>
  <! EndSection:   'COLON COMMANDS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To make a nice plot of a set of spectra with the default layout:
  <P>
  	cl&gt; specplot spec*
  <P>
  2.  To set the colors or line types for multiple spectra in a batch
  mode application create a cursor file like:
  <P>
  	cl&gt; type cursor.dat
  	:color[1] 2
  	:color[2] 3
  	:color[3] 4
  	r
  	cl&gt; specplot im1,im2,im3 cursor=cursor.dat
  <P>
  Note that the <TT>'r'</TT> key is necessary redraw the graph with the changed
  attributes.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_SPECPLOT">SPECPLOT V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SPECPLOT' Line='SPECPLOT V2.11'>
  <DD>The scale and offset parameters may now be a value, a filename, or
  and image header keyword.
  <P>
  The <TT>'f'</TT> key was added to toggle between world and logical pixel coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_SPECPLOT">SPECPLOT V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SPECPLOT' Line='SPECPLOT V2.10.3'>
  <DD>A color parameter was added for graphics terminals supporting color.
  <P>
  The :units command was extended to have an optional spectrum specifier.
  This is primarily intended to plot different (or the same) spectra in
  velocity but with different velocity zeros.
  <P>
  The default task units parameter has been changed to "<TT></TT>" to allow picking
  up a "<TT>units_display</TT>" WCS attribute if defined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_SPECPLOT">SPECPLOT V2.10</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SPECPLOT' Line='SPECPLOT V2.10'>
  <DD>New parameters were added to select apertures and bands, plot
  additional dimensions (for example the additional output from the extras
  option in <B>apextract</B>), suppress the system ID banner, suppress the Y
  axis scale, output a logfile, and specify the plotting units.  The <I>ptype</I>
  parameter now allows negative numbers to select histogram style lines.
  Interactively, the plotting units may be changed and the <TT>'v'</TT> key allows
  setting a velocity scale zero point with the cursor.  The new version
  supports the new spectral WCS features including nonlinear dispersion
  functions.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_notes">NOTES</A></H2>
  <! BeginSection: 'NOTES'>
  <UL>
  The automatic layout algorithm is relatively simple and may not
  provide visually satisfactory results in all cases.  The fonts and Y axis
  scale capabilities are not as good as might be desired for publication
  quality plots.
  </UL>
  <! EndSection:   'NOTES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  bplot, splot, onedspec, gtools, ranges
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'COLON COMMANDS' 'EXAMPLES' 'REVISIONS' 'NOTES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>