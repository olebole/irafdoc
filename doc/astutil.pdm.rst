.. _pdm:

pdm — Find periods in light curves by Phase Dispersion Minimization
===================================================================

**Package: astutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  pdm -- Find periods in lightcurve data.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  pdm infile
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <P>
  <DL>
  <DT><B>infiles</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='infiles' Line='infiles'>
  <DD>Input file template.  If more than one file matches the template, data
  from all the files will be concatenated to produce the working data set.
  </DD>
  </DL>
  <DL>
  <DT><B>metafile = "<TT>pdmmeta</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='metafile' Line='metafile = "pdmmeta"'>
  <DD>File in which to store metacode when running in batch mode.  All of the
  plots saved will be put here with formfeeds between them.
  </DD>
  </DL>
  <DL>
  <DT><B>batchfile = "<TT>pdmbatch</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='batchfile' Line='batchfile = "pdmbatch"'>
  <DD>File in which to store information about the period, amplitude, epoch
  and fit function when running in batch mode.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>The output device for interactive graphics.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Interactive flag.  If set to no, the analysis is done in batch mode with output
  to a file and no interactive graphics.  Metacode will be saved for the data
  plot, the theta plot, and the phase plot.  If set to yes, various types of
  plots can be made on the user's terminal and cursor commands are available.
  </DD>
  </DL>
  <DL>
  <DT><B>flip = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flip' Line='flip = no'>
  <DD>Flag to tell the program to flip the y-axis.  This is useful when the y-scale
  is in magnitudes (decreasing numbers mean increasing brightness).
  </DD>
  </DL>
  <DL>
  <DT><B>minp = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minp' Line='minp = 0'>
  <DD>Minimum period to be searched.  This parameter, if set, tells the program
  the bottom end of the period window to be searched.   If not set, the
  program uses as a value the smallest chronological distance between
  any two adjacent data points.  When the program is run, it writes a value
  into this parameter as stored in the uparm directory.  This means the
  next time the program is run, the default minp will be the value assigned
  or calculated the last time the program was run by this user.  We say the
  program 'remembers' the last value used.
  </DD>
  </DL>
  <DL>
  <DT><B>maxp = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxp' Line='maxp = 0'>
  <DD>Maximum period to be searched.  This parameter, if set, tells the program
  the top end of the period window to be searched.  If not set, the program
  uses as a value 4 times the distance between the first and last data
  point.  This parameter is remembered as minp is.
  </DD>
  </DL>
  <DL>
  <DT><B>ntheta = 200</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ntheta' Line='ntheta = 200'>
  <DD>Resolution of the theta plot.  This parameter tells how many points in
  the period window should have their theta statistic calculated.  The points
  are spaced equidistant from one another in frequency space.
  </DD>
  </DL>
  <DL>
  <DT><B>pluspoint = 50</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pluspoint' Line='pluspoint = 50'>
  <DD>Maximum number of data points for which to use plus symbols.  If there
  are more data points then points are plotted.
  </DD>
  </DL>
  <DL>
  <DT><B>autoranges = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='autoranges' Line='autoranges = no'>
  <DD>This flag, when set, instructs the program to look for gaps in
  the data and, if large gaps are found, divide the data up into ranges
  discarding the gaps and doing the analysis only on the ranges.  This
  helps remove side lobes from the spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>nsigma = 3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsigma' Line='nsigma = 3'>
  <DD>Number of standard deviations for autorange break.  If ranges are to 
  be automatically calculated, this parameter tells how large a gap in
  the data should constitute a division between ranges.  The mean
  and standard deviation of the distribution of chronological spacing
  of input points are calculated.  Then the points are scanned in
  increasing order and if an inter-data gap bigger than nsigma
  standard deviations is found, a new range is started.
  </DD>
  </DL>
  <DL>
  <DT><B>cursor = "<TT>stdgcur</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = "stdgcur"'>
  <DD>The source of graphics cursor input.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Pdm applies a phase dispersion minimization algorithm (R. F. Stellingwerf,
  "<TT>Period Determination by Phase Dispersion Minimization</TT>", ApJ 224, 1978,
  953) to lightcurve data to determine periodicities in the data.  It also
  calculates amplitude and epoch information.
  <P>
  Pdm can be used in batch or interactive mode.  In batch
  mode the
  output is period, amplitude, and epoch for the minimum found within
  the period window.  Metacode will be produced for the data plot,
  the theta statistic plot, and the phasecurve plot.
  The metacode will be saved in the metafile.  In interactive mode the user
  can plot the data at different stages in the analysis, fit and remove
  curves from the data, reject points, set data ranges, plot and fit
  phasecurves, etc.
  <P>
  Pdm guesses at the period/frequency window to be searched unless
  the minimum
  and maximum period for the window are specified using minp and maxp.  The
  minimum period is taken as twice the chronological distance between the closest
  two points in the data.  The maximum period is taken as 4 times the distance
  between the first and last data points.
  <P>
  Pdm will work on one object at a time and the input data may
  be contained in multiple input files if desired.  The program will
  concatenate data in all the files which match the input template.
  The input files are text files containing one (x,y) pair per line or
  just a (y) value per line.  If only one value per line is found the
  program will number x sequentially (1,2,3,4,...).  If a third value
  is included on each line it will be read as the error in that
  measurement.   (The <TT>'e'</TT> key is used to toggle error bars on the phase
  plot.)
  <P>
  At startup, if the interactive flag is set, the user will be presented
  with a plot of the data and the cursor will be turned on.
  <P>
  When the user plots a phasecurve, points that are deleted or undeleted from
  the phasecurve plot will be deleted or undeleted from the working data set.
  <P>
  The ICFIT keystrokes are described elsewhere. (see help for icfit)
  <P>
  <P>
  Phase Dispersion Minimization User Interface (keystrokes)
  <P>
  When the program starts up it reads the data file(s) and displays
  the data on the screen as a standard mark plot.  The user is
  then placed in a graphics cursor loop with the following options
  available in addition to the standard graphics commands:
  <P>
  Note:
  The remembered period is for the last minimum found.  This
  minimum calculation is done whenever a new theta plot is graphed
  and whenever the "<TT>m</TT>" key is used.
  <P>
  <DL>
  <DT><B>? -- list options</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='? -- list options'>
  <DD><P>
  Print out the menu.
  </DD>
  </DL>
  <DL>
  <DT><B>h -- graph data</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='h' Line='h -- graph data'>
  <DD><P>
  Make a plot on the screen, using marks, of observation time vs observed
  value. If there are more than 50 points, use dots, else use pluses.  If
  points have been deleted, draw an x through them on the plot.  If ranges
  are in effect, draw range bars along the abscissa of the plot marking
  the ranges.
  </DD>
  </DL>
  <DL>
  <DT><B>e -- toggle error bars on or off</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='e' Line='e -- toggle error bars on or off'>
  <DD><P>
  When the phase plot is on the screen and error data has been supplied,
  this key will toggle the drawing of error bars on the phase plot so that
  the user can determine how well the period found works with the data
  including this error information.
  </DD>
  </DL>
  <DL>
  <DT><B>i,k -- graph frequency or period respectively versus theta</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='i' Line='i,k -- graph frequency or period respectively versus theta'>
  <DD><P>
  Calculate the theta statistic in the period/frequency range specified
  previously.  If no period/frequency range has been specified,
  pdm guesses one.  The minimum period is taken as twice the chronological
  distance between the closest two points in the data.  The maximum
  period is taken as 4 times the distance between the first and last
  data points.  The number of theta points in this range is also a
  parameter which can be specified.
  <P>
  Next, plot theta on the screen using line drawing mode.  Plot
  either period vs theta or frequency vs theta.  Calculate the minimum
  value of theta displayed, turn the cursor back on (clgcur) and put
  the cursor x position at that minimum.
  </DD>
  </DL>
  <DL>
  <DT><B>p -- graph phase curve for period/frequency at cursor position</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='p' Line='p -- graph phase curve for period/frequency at cursor position'>
  <DD><P>
  Calculate the phase curve for the period/frequency under the
  cursor.  This assumes the user has a theta plot on the screen and
  an error message will be given otherwise.
  <P>
  The phase curve will be plotted in mark mode with two copies displayed
  and placed end to end to clarify the plot by providing continuity at
  all phases.  The amplitude and epoch values for this period are calculated
  and the phases are plotted relative to this epoch.
  </DD>
  </DL>
  <DL>
  <DT><B>d,u -- delete/undelete respectively point nearest the cursor</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='d' Line='d,u -- delete/undelete respectively point nearest the cursor'>
  <DD><P>
  Points deleted will have an x drawn through them.  The x will be
  erased when the point is undeleted.
  </DD>
  </DL>
  <DL>
  <DT><B>f -- call ICFIT on displayed data</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='f' Line='f -- call ICFIT on displayed data'>
  <DD><P>
  ICFIT is used for interactive curve fitting.
  It is called with either the data values or the phase values,
  depending on which type of plot is on the screen at the time.
  Any point deleted in ICFIT will be removed from consideration in
  all subsequent calculations until restored.
  <P>
  The fit curve is retained by PDM after the return from ICFIT and
  may be subsequently subtracted from the data using the j command.
  <P>
  Note: The user must exit ICFIT using the q key before he is placed
  back into PDM.
  </DD>
  </DL>
  <DL>
  <DT><B>j -- subtract fit from data, use residuals</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='j' Line='j -- subtract fit from data, use residuals'>
  <DD><P>
  Just as it says. The original data is retained and can be reinstated
  with the :origdata command.  This command only applies to the data.
  The user cannot subtract a fit from the phase plot.
  </DD>
  </DL>
  <DL>
  <DT><B>s -- set sample range for calculations</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='s' Line='s -- set sample range for calculations'>
  <DD><P>
  This command is used to set ranges of data to be used.  The cursor is
  first positioned to the beginning of the range of interest, an s is
  struck, the program prints the prompt again:, the cursor is
  repositioned to the end of the range and a second s is struck
  completing the command.  Multiple ranges may be set and all the data
  inside the union of the ranges will be used.  Data points outside the
  ranges will be ignored until the data is reset with an :alldata
  or an :origdata command.
  <P>
  This also forces the boolean flag segments to be set true.
  </DD>
  </DL>
  <DL>
  <DT><B>,, -- Set minp or minf to cursor x position</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=',, -- Set minp or minf to cursor x position'>
  <DD><P>
  When the theta plot is on the screen, this keystroke can be used
  to set the minimum period (frequency) to the current cursor position.
  </DD>
  </DL>
  <DL>
  <DT><B>. -- Set maxp or maxf to cursor x position</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='. -- Set maxp or maxf to cursor x position'>
  <DD><P>
  When the theta plot is on the screen, this keystroke can be used
  to set the maximum period (frequency) to the current cursor position.
  </DD>
  </DL>
  <DL>
  <DT><B>g -- significance of theta at cursor x position</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='g' Line='g -- significance of theta at cursor x position'>
  <DD><P>
  The statistical significance of the period/frequency under the
  cursor is calculated by Fisher's method of randomization.
  This value is printed at the bottom of the screen.
  <P>
  This assumes that a theta plot is on the screen.
  </DD>
  </DL>
  <DL>
  <DT><B>a -- amplitude and epoch at cursor x position</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='a' Line='a -- amplitude and epoch at cursor x position'>
  <DD><P>
  For the period/frequency under the cursor or of the plot, the amplitude
  and epoch are calculated and returned to the user.
  <P>
  This assumes that a theta plot is on the screen.
  </DD>
  </DL>
  <DL>
  <DT><B>m -- mark range and find minimum in this range</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='m' Line='m -- mark range and find minimum in this range'>
  <DD><P>
  This command is used exactly like the s command but has a different
  effect.  After the user has positioned the cursor and struck the m
  key twice, defining the range, the minimum value of theta is found
  in this range and its associated period/frequency is returned.
  </DD>
  </DL>
  <DL>
  <DT><B>r -- replot</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='r' Line='r -- replot'>
  <DD><P>
  Redraw the plot on the screen.
  </DD>
  </DL>
  <DL>
  <DT><B>x -- remove a trend from the data by removing a bestfit line</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='x' Line='x -- remove a trend from the data by removing a bestfit line'>
  <DD><P>
  This command calls the curfit package to fit a straight line to the
  data and then subtracts it point by point from the data.
  </DD>
  </DL>
  <DL>
  <DT><B>z -- flip the y-axis scale</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='z' Line='z -- flip the y-axis scale'>
  <DD><P>
  This command toggles a y-axis flip for the plots.  This is useful when
  the user is plotting magnitudes where the smaller the ordinate value the
  larger the intensity.
  </DD>
  </DL>
  <DL>
  <DT><B>q -- quit</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='q' Line='q -- quit'>
  <DD><P>
  Exit PDM.
  <P>
  </DD>
  </DL>
  The following commands may be abbreviated.  If entered without an
  argument; :minp, :maxp, :minf, :maxf, and :ntheta will display the named
  parameter; :show, :vshow will print to STDOUT; :signif, :ampep, and :phase,
  will do the calculation at the remembered period.
  <P>
  <DL>
  <DT><B>:show [file]		show parameter settings</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':show [file]		show parameter settings'>
  <DD><P>
  Print on the screen the min/max period, the remembered minimum,
  the range if it is in effect, the start and end of the ranges
  if they are defined, the mean and variance of the data in each
  range. If file is specified, the output will go there.
  </DD>
  </DL>
  <DL>
  <DT><B>:vshow [file]		show verbose information</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':vshow [file]		show verbose information'>
  <DD><P>
  This command will display all the information displayed by the :show
  command plus curfit information if the any curves have been fit.  Also,
  the residual data will be shown if residuals have been calculated. If
  file is specified, the output will go there.
  </DD>
  </DL>
  <PRE>
  <P>
  :minp :maxp [period]		set min/max search period
  :minf :maxf [frequency]		set min/max search frequency
  </PRE>
  <DL>
  <DT><B></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=' '>
  <DD>These commands are self explanatory.  Whichever value is set,
  period or frequency, the corresponding frequency or period is
  automatically calculated and remembered.
  </DD>
  </DL>
  <DL>
  <DT><B>:ntheta [num]		set number of points for theta</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':ntheta [num]		set number of points for theta'>
  <DD><P>
  Set the number of equally spaced points in the period window for
  which theta should be calculated.  This is really a setting of
  the resolution of the theta plot and defaults to 200 since
  the calculation time for 200 points is only a few seconds.  Very
  large numbers entered here will cause the program to warn the user
  that the theta calculation may take some time.
  </DD>
  </DL>
  <DL>
  <DT><B>:sample [value]		set/show the sample ranges</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':sample [value]		set/show the sample ranges'>
  <DD><P>
  The start and end values for the ranges will be printed on the screen.
  If value is present, it has the form begin:end where begin
  and end are real numbers specifying a new range.
  </DD>
  </DL>
  <DL>
  <DT><B>:signif [period]		find theta significance</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':signif [period]		find theta significance'>
  <DD><P>
  Same as the g key.  The colon command allows the user to 
  set the period exactly, instead of using the cursor.  If no period
  is entered, the calculation will be done using the remembered period.
  </DD>
  </DL>
  <DL>
  <DT><B>:ampep [period]		amplitude and epoch</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':ampep [period]		amplitude and epoch'>
  <DD><P>
  Same as the e key.  Without an argument, use remembered minima.
  </DD>
  </DL>
  <DL>
  <DT><B>:phase [period]		graph phase curve</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':phase [period]		graph phase curve'>
  <DD><P>
  Same as the h key.  Without an argument, use remembered minima.
  </DD>
  </DL>
  <DL>
  <DT><B>:unreject			unreject all points</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':unreject			unreject all points'>
  <DD><P>
  This tells the program to use all of the data points. If a fit
  has been subtracted from a subset of the data points then this command
  causes the original data set to be restored since, otherwise, we would
  restore a mixture of data and residuals.
  </DD>
  </DL>
  <DL>
  <DT><B>:alldata			reset range to entire dataset</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':alldata			reset range to entire dataset'>
  <DD><P>
  The effect of this command is to turn off the range settings.  All
  of the data will be used if the ranges settings are off.  Rejected
  points remain rejected though.  Again, if these data are residuals,
  the original data are restored.
  </DD>
  </DL>
  <DL>
  <DT><B>:origdata			reset data to original dataset</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':origdata			reset data to original dataset'>
  <DD><P>
  Copy the original data vector into the working data vector.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To find the main period in the data contained in the file 'vstar645',
  whose period is within the bounds (200., 800.) interactively
  the command might be:
  <P>
  	cl&gt; pdm vstar645 minp=200. maxp=800.
  <P>
  2. To do the same thing in batch mode, allowing the program to guess the 
  period window, with no lightcurve analysis, and saving the metacode
  in vstar645.m, the command might be:
  <P>
  	cl&gt; pdm vstar645 inter=no meta="<TT>vstar645.m</TT>"
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Pdm has some problems with data sets containing a small number (&lt;20)
  points.  Generally, it will do fairly well but the theta curve may look
  strange.
  <P>
  The amplitude and epoch calculation might be improved by fitting a parabola
  to the phase curve near the minimum and near the maximum and using points
  on these parabolas for the min and max points instead of actual data points.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  icfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
