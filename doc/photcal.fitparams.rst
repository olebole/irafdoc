fitparams — Compute the parameters of the transformation equations
==================================================================

**Package: photcal**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>fitparams (Aug91)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.photcal</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>fitparams (Aug91)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>fitparams</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  fitparams -- solve for the parameters of the transformation equations
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  fitparams observations catalogs config parameters
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_observations">observations</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observations' Line='observations'>
  <DD>The list of files containing the observational data.  Observations files are
  multi-column text files whose columns are delimited by whitespace, and
  whose first column is usually reserved for the object id.
  All observations files in the list must have the same format.
  The format of legal observations files is described in further detail in
  the description section.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_catalogs">catalogs</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catalogs' Line='catalogs'>
  <DD>The list of files containing the catalog data.  Catalog files are
  multi-column text files whose columns are delimited by whitespace,
  and whose first column is always reserved for the object id.
  If more than one entry with the same id exists in the list of catalogs,
  only the first entry is used.
  All catalog files in the list must have the same format.
  The format of legal catalog files is described in further detail in
  the description section.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_config">config</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='config' Line='config'>
  <DD>The name of the configuration file. The configuration file is a text file
  specifying the format of the input catalog and observations files, and the
  form of the transformation
  equations. A brief description of the syntax and grammar of this file
  is given in the configuration file section.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_parameters">parameters</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='parameters' Line='parameters'>
  <DD>The name of the output database file.
  Parameters is a text database file to which the error analysis of the fit
  and the parameter values and errors for each transformation equation are
  written. 
  The output of fitparams is appended to parameters as a set of new records,
  one for each of the transformation equations. 
  If more than one record exists with the same record name, the 
  last record written takes precedence.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_weighting">weighting = "<TT>uniform</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weighting' Line='weighting = "uniform"'>
  <DD>The following weighting schemes are supported.
  <DL>
  <DT><B><A NAME="l_uniform">uniform</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='uniform' Line='uniform'>
  <DD>The data points are all assigned a weight of one.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_photometric">photometric</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='photometric' Line='photometric'>
  <DD>The total error squared for each data point is set to the total error in the
  catalog variables squared plus the total error in the observations variables
  squared and the weight for each data point is set to 1.0 / error ** 2.
  This option assumes that all the sources of error are in the photometric
  indices (magnitudes and colors), that error columns (see the description
  of the configuration file below) have been declared for at least one
  photometric index, and that the contribution of each catalog or observations
  variable to the total error is weighted by the number of times it occurs
  in the transformation equation.
  If <I>addscatter</I> is "<TT>yes</TT>" then an additional "<TT>scatter</TT>" term is fit and
  added to the weights.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_equations">equations</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='equations' Line='equations'>
  <DD>The weight equation (see the description of the configuration file below)
  is evaluated for each point and the weight for that point is set to that
  value.  If there is no weight equation the weights are all set to one.
  If <I>addscatter</I> is "<TT>yes</TT>" then an additional "<TT>scatter</TT>" term is fit and
  added to the weights.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_addscatter">addscatter = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='addscatter' Line='addscatter = yes'>
  <DD>Add an additional scatter term to the weights if the average error in the fit
  is much greater than the average error in the measurements? <I>Addscatter</I>
  has no effect if <I>weighting</I> is "<TT>uniform</TT>". <I>Addscatter</I> is recommended
  if <I>weighting</I> is "<TT>photometric</TT>" as the intrinsic error in the
  transformations is often much greater than the formal errors of
  measurement and the scatter term stabilizes the fit.
  Users of the <I>weighting</I> equals "<TT>equations</TT>" option
  may wish to turn off <I>addscatter</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tolerance">tolerance = 3.0e-5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tolerance' Line='tolerance = 3.0e-5'>
  <DD>The convergence tolerance for the non-linear least squares fit.
  The fit will stop iterating 
  when the fractional change in the reduced chi-square of the residuals from 
  iteration to iteration is less than <I>tolerance</I>. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxiter">maxiter = 15</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxiter' Line='maxiter = 15'>
  <DD>The maximum number of iterations for the non-linear least squares fit.
  When this number is reached the fitting process will terminate even
  if the fit has not converged.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nreject">nreject = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nreject' Line='nreject = 0'>
  <DD>The maximum number of bad data rejection iterations. If <I>nreject</I> is
  greater than zero the initial fit is used
  to detect and reject deviant points before performing the final fit.
  No rejection is performed if <I>nreject</I> is less than or equal
  to zero.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_low_reject">low_reject = 3.0, high_reject = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 3.0, high_reject = 3.0'>
  <DD>The lower and upper rejection limits in units of the rms of the fit.
  Points deviating from the initial fit by more than this amount are rejected
  before performing the final fit.  No rejection is done if both limits
  are zero.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_grow">grow = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0.0'>
  <DD>The default rejection growing radius. Points within a distance given
  by this parameter of any rejected point are also rejected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Fit equations interactively ? When this parameter is <I>yes</I>, the user will 
  be presented with plots of the data and can interact with the fitting 
  process.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfile">logfile = "<TT>STDOUT</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "STDOUT"'>
  <DD>The name of the output text file to which selected detailed results of the
  fitting process are written.  By default logfile is the standard output.
  If logfile is "<TT></TT>", logging is turned off altogether. Otherwise new
  output is appended to logfile which can therefor become quite large.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_log_unmatched">log_unmatched = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='log_unmatched' Line='log_unmatched = yes'>
  <DD>Write the list of observations with no corresponding catalog entries to
  logfile? This option is useful for checking for errors in the observed
  object id names and for users who like to run fitparams in non-interactive
  mode.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_log_fit">log_fit = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='log_fit' Line='log_fit = no'>
  <DD>Write the error analysis of the final fit in logfile? This option is
  useful for users who like to run fitparams in non-interactive mode.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_log_results">log_results = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='log_results' Line='log_results = no'>
  <DD>Write the results of the current fit to logfile? This option is
  useful for users who like to run fitparams in non-interactive mode.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_catdir">catdir = "<TT>)_.catdir</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catdir' Line='catdir = ")_.catdir"'>
  <DD>The directory containing the supported standard star catalogs.
  The default parameter value  redirects <I>catdir</I>
  to a package parameter of the same name. A list of standard
  catalogs may be obtained by printing the file "<TT>photcal$catalogs/README</TT>".
  Alternatively the user may create their own standard star catalogs 
  and standard star catalog directory.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>The default graphics device. 
  This parameter is used only if <B>interactive=yes</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Graphics cursor input. When null the standard graphics cursor is used.
  Otherwise the specified cursor command file is used.
  This parameter is used only if <B>interactive=yes</B>.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  FITPARAMS parses the configuration file <I>config</I> checking for
  grammar and syntax errors.  FITPARAMS attempts to recover from any
  errors and to finish parsing the configuration
  file, but it will not process the input data if errors are present.
  The configuration file is described briefly in the configuration file
  section and in detail in the help page for the configuration file.
  <P>
  Once the configuration file is successfully parsed, FITPARAMS reads the list
  of catalog files and loads the values of the catalog variables
  declared in <I>config</I> into memory.
  If no catalog section is declared in <I>config</I>, if the catalog section
  is empty, or if catalogs is "<TT></TT>", no catalog data is read
  and all the required input data is assumed to be in <I>observations</I>.
  After the catalog data is read, FITPARAMS reads the observations files
  <I>observations</I>, matches the object ids of the observations with the
  corresponding catalog object ids, and loads all the observations
  variables declared in <I>config</I> into memory. Id matching is disabled
  if no catalog
  data is read, otherwise only those observations which have a matching catalog
  entry will be used in the fit. If a catalog section declaration was made
  in <I>config</I>, even an empty one, FITPARAMS assumes that the object ids
  are in column 1 of <I>observations</I>.
  <P>
  Legal <I>catalog</I> and <I>observations</I> files are multi-column text
  files whose columns are delimited by whitespace.
  The first column of a catalog file is <I>always</I> reserved for an object id.
  The first column of an observations file is <I>usually</I> reserved for an
  object id which can be
  used to match the observational data with the corresponding catalog data.
  All other columns may contain any quantity which can be
  expressed as an integer or real number.  Sexagesimal format numbers
  (hh:mm:ss) are interpreted internally as real numbers. The constant
  INDEF can be used to represent data that is missing or undefined.
  Double precision and complex data are
  not supported. Lines beginning with "<TT>#</TT>" are treated as comment lines.
  <P>
  FITPARAMS solves the fit
  for each equation in the configuration file either interactively 
  or non-interactively depending on the value of <I>interactive</I>,
  and writes the solution in the output file <I>parameters</I> for later
  use by the evaluation routines EVALFIT or INVERTFIT.
  Selected results can also be written to <I>logfile</I> if
  any of the switches <I>log_unmatched</I>, <I>log_fit</I>, or <I>log_results</I>
  are enabled.
  In interactive mode the user can use all the interactive capabilities
  of the interactive non-linear least squares package INLFIT.
  INLFIT is described more fully below. 
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_the_configuration_file">THE CONFIGURATION FILE</A></H2>
  <! BeginSection: 'THE CONFIGURATION FILE'>
  <UL>
  <P>
  The configuration file is a text file which specifies how the data is
  organized in the input files and how the transformation
  equations are to be fit.
  <P>
  The input data are assumed to come from two different sources that may
  be either in the same input file or in different input files.
  These sources are known as the <I>catalog</I> and the <I>observations</I>
  respectively.
  <P>
  The <I>catalog</I> contains values indexed by a name called the
  matching name. This name must be in the first column of the
  catalog and is also assumed to be unique, i.e, each catalog
  entry is assumed to be unique.
  <P>
  The <I>observations</I> are values that may be either indexed by a matching
  name if a catalog section is specified in the configuration file, or a
  stream of input values in an ordinary text file.
  If a catalog section is specified and non-empty, each observation is
  matched against the
  catalog entries, and only observations whose matching names are found in the
  catalog are used to compute the transformation equations.
  Otherwise all values are used.
  <P>
  The configuration file is divided in three sections: the <I>catalog
  section</I> which describes the format of the catalog files, the
  <I>observations section</I> which describes the format of the observation 
  files, and the <I>transformation section</I> which defines the
  transformation equations in that order.
  <P>
  The catalog and observations sections permit the user to assign
  names to the input file 
  columns. These columns can later be referenced by name in the configuration
  file by using these assigned names
  as if they were variables in a programming language.
  <P>
  The transformation section is used to define the equations to solve,
  and assign initial values to the fitting parameters.
  The user may also optionally define equations for the derivatives of
  the transformation equations with respect to the parameters,
  the weights to be used in the fit, 
  the errors of the fit and the default equations to be
  plotted in the interactive fitting process.
  It is possible to specify any number of transformation equations in
  this section.
  <P>
  SAMPLE CONFIGURATION FILES
  <P>
  Example 1. Configuration file for reducing UBV photoelectric photometry.
  <P>
  <PRE>
  # Configuration file for reducing UBV photoelectric photometry.
  <P>
  catalog
  <P>
  V	2		# V magnitude
  BV	3		# B - V color
  UB	4		# U - B color
  <P>
  observation
  <P>
  v	2		# v instrumental magnitude
  b 	3		# b instrumental magnitude
  u 	4		# u instrumental magnitude
  ev	5		# error in v instrumental magnitude
  eb 	6		# error in b instrumental magnitude
  eu 	7		# error in u instrumental magnitude
  X       8		# airmass		
  <P>
  transformation
  <P>
  fit   v1 = 0.0, v2=0.16, v3=-0.043
  VFIT: V = v1 + v - v2 * X + v3 * (b - v)
        weight(VFIT) = 1.0 / ev ** 2
        plot(VFIT) = V, V - (v1 + v - v2 * X + v3 * (b - v))
  <P>
  fit    b1 = 0.0, b2=0.09, b3=1.21
  BVFIT: BV = b1 - b2 * X + b3 * (b - v)
         weight (BVFIT) = 1.0 / (eb ** 2 + ev ** 2)
         plot(BVFIT) = BV, BV - (b1 - b2 * X + b3 * (b - v))
  <P>
  fit    u1 = 0.0, u2=0.300, u3=0.861
  UBFIT: UB = u1 - u2 * X + u3 * (u - b)
         weight (UBFIT) = 1.0 / (eu ** 2 + eb ** 2)
         plot(UBFIT) = UB, UB - (u1 - u2 * X + u3 * (u - b))
  </PRE>
  <P>
  Example 2. Configuration file for reducing UBV CCD photometry.
  <P>
  <PRE>
  catalog
  <P>
  V		2	# V magnitude
  BV		3	# B - V color
  UB		4	# U - B color
  error(V)	5	# error in V magnitude
  error(BV)	6	# error in B-V color
  error(UB)	7	# error in U-B color
  <P>
  observation
  <P>
  m1		2	# filter 1 instrumental magnitude
  error(m1)	3	# error in filter 1 instrumental magnitude
  Xm1		4	# airmass of filter 1  observation
  m2	 	6	# filter 2 instrumental magnitude
  error(m2) 	7	# error in filter 2 instrumental magnitude
  Xm2		8	# airmass of filter 2 observation
  m3	 	10	# filter 3 instrumental magnitude
  error(m3) 	11	# error in filter 3 instrumental magnitude
  Xm3	        12	# airmass of filter 3 observation		
  <P>
  <P>
  transformation
  <P>
  fit   u1 = 27.0, u2=0.68, u3=0.05
  UFIT: m3 = u1 + V + BV + UB + u2 * Xm3 + u3 * UB
  <P>
  fit   b1 = 26.0, b2=0.30, b3=0.18
  BFIT: m2 = b1 + V + BV + b2 * Xm2 + b3 * BV
  <P>
  fit   v1 = 25.0, v2=0.17, v3=-0.02
  VFIT: m1 = v1 + V + v2 * Xm1 + v3 * BV
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'THE CONFIGURATION FILE'>
  <H2><A NAME="s_the_non_linear_interactive_fitting_package">THE NON-LINEAR INTERACTIVE FITTING PACKAGE</A></H2>
  <! BeginSection: 'THE NON-LINEAR INTERACTIVE FITTING PACKAGE'>
  <UL>
  <P>
  DESCRIPTION
  <P>
  INLFIT fits an n-dimensional function to a set data
  points, iterating until the reduced chi-squared changes
  by less than <I>tolerance</I> percent between successive iterations, or
  machine precision is reached and the fit converges, or until the maximum number
  of iterations <I>maxiter</I> is reached.  If the maximum number
  of iterations is reached before convergence a status flag
  is set.
  <P>
  After computing an initial fit, INLFIT presents the user with a plot of
  the fit and activates the graphics cursor.
  At this point the user may examine and/or interact with the fit by,
  for example, reprogramming the default graph keys,
  editing the default convergence or bad data rejection parameters,
  deleting and undeleting points, 
  altering which parameters in the fitting function are actually to be
  fit and which are to be held constant, and refitting the data.
  <P>
  If <I>nreject</I> is greater than zero the RMS of the residuals is computed
  and points whose residuals are less than <I>low_reject</I> * RMS
  or <I>high_reject</I> * RMS value are excluded from the fit. Points within
  a distance <I>grow</I> of a rejected point are also excluded from
  the fit. The function is then refit without the rejected points.
  The rejection algorithm is executed until the number of rejection
  iterations reaches <I>nreject</I> or no more points are rejected.
  <P>
  ALGORITHMS
  <P>
  INLFIT uses the standard Levenberg-Marquardt non-linear least squares
  algorithm to fit the data. Detailed descriptions of the algorithm can
  be found in the following two references.
  <PRE>
  <P>
  1. Bevington, P.R., 1969, Data Reduction and Error Analysis for the
     Physical Sciences, Chapter 11, page 235.
  <P>
  2. Press, W.H. et al., 1986, Numerical Recipes: The Art of Scientific
     Computing, Chapter 14, page 523.
  <P>
  </PRE>
  <P>
  CURSOR COMMANDS
  <P>
  The following interactive cursor keystroke commands are available from
  with the INLFIT package.
  <DL>
  <DT><B><A NAME="l_">?</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line='?'>
  <DD>The terminal is cleared and a menu of cursor keystroke and colon commands
  is printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_c">c</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='c' Line='c'>
  <DD>The id, coordinates of the data point nearest the cursor, along with the
  function value, the fitted value and the residual, are printed on the status
  line.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_d">d</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='d' Line='d'>
  <DD>The data point nearest the cursor and not previously deleted is marked with an
  X. It will not be used in further fits until it is undeleted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_f">f</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='f' Line='f'>
  <DD>The function is fit to the data and the fit is graphed using the default
  plot type.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_g">g</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='g' Line='g'>
  <DD>Redefine the graph keys "<TT>h-l</TT>" from their defaults. A prompt is issued for the
  graph key to be redefined. Another prompt is issued for the data to be
  plotted at which point the user must enter the x and y axis data to plot,
  delimited by a comma. The data types are the following (they can be
  abbreviated to up to three characters).
  <PRE>
  <P>
      function    Dependent variable or function
      fit         Fitted value
      residuals   Residuals (function - fit)
      ratio       Ratio (function / fit)
      nonlinear   Nonlinear component
      identifier  Independent variable named "identifier" (if defined)
      var n       Independent variable number "n"
      user n      User defined plot equation "n"  (if defined)
  <P>
  </PRE>
  The application program can define independent variable names and user plot 
  functions, aside from the standard options provided. If variable names are 
  supplied, the user can reference them by their names. Otherwise they can be 
  always referenced by "<TT>var n</TT>", where "<TT>n</TT>" is the variable number (the user has 
  to know the variable order in this case). The "<TT>:variables</TT>" command will
  list the currently defined variables by name and number.
  The application program may
  define any number of plot equations aside from the defaults provided. In this 
  case the user may reference them by "<TT>user n</TT>", where "<TT>n</TT>" is the plot function 
  number (the user must know the equation order in this case). 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_h">h, i, j, k, l</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='h' Line='h, i, j, k, l'>
  <DD>By default each key produces a different graph. The graphs are described by
  the data which is graphed along each axis as defined above. The default graph
  keys,
  which may be redefined by the application program or interactively by using 
  the <TT>'g'</TT> key, are the following.
  <PRE>
  <P>
          h       function, fit
          i       function, residuals
          j       function, ratio
          k       var 1, function
          l       user 1, user 2 (default)
  <P>
  </PRE>
  The initial graph key, if not redefined by the application program is <TT>'h'</TT>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_o">o</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='o' Line='o'>
  <DD>Overplot the next fit provided the graph format has not changed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_q">q</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='q' Line='q'>
  <DD>Exit from the interactive curve fitting package.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_r">r</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='r' Line='r'>
  <DD>Redraw the current graph.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_t">t</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='t' Line='t'>
  <DD>Toggle fit overplotting on and off. If this option is on the data
  and fitted values are overplotted. Otherwise only data points are plotted.
  The fitted values are marked using boxes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_u">u</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='u' Line='u'>
  <DD>Undelete the data point nearest the cursor which has been previously deleted.
  This option does not work over points marked as deleted by the application
  program before calling inlfit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_w">w [key]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='w' Line='w [key]'>
  <DD>Set the graph window or data range along each axis to be graphed.. This is a 
  <B>gtools</B> option which prints the prompt "<TT>window:</TT>". The available cursor
  keystroke commands are printed with <TT>'?'</TT> and on-line help is available by
  typing "<TT>help gtools</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_I">I</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='I' Line='I'>
  <DD>Interrupt the task immediately without saving the current fit.
  </DD>
  </DL>
  <P>
  Colon commands are used to show or set the values of parameters.
  The application program calling <B>inlfit</B> can add more commands.
  Parameter names can be abbreviated. The following commands are supported. 
  <DL>
  <DT><B><A NAME="l_">:show [file]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':show [file]'>
  <DD>Show the current values of the fitting parameters high_reject, 
  low_reject, niterate, grow, tol, itmax. The default output device
  is the terminal (STDOUT) and the screen is cleared before the information
  is output. If a file is specified then the information is appended
  to the named file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:variables [file]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':variables [file]'>
  <DD>List the currently loaded variables. The number, id, minimum value and maximum
  value of each variable is printed. The default output device is the terminal
  (STDOUT) and the screen is cleared before the information is output.
  If a file is specified then the information is appended to the named file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:data [file]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':data [file]'>
  <DD>List the raw data. The value of each standard catalog and observations
  catalog variable  for each data point is printed. The default output device
  is the terminal (STDOUT) and the screen is cleared before the information
  is output.  If a file is specified then the information is appended to
  the named file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:errors [file]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':errors [file]'>
  <DD>Show the error analysis of the current fit.  The number of iterations,
  total number of points, the number of rejected and deleted points,
  the standard deviation, the reduced chi, average error (always = 1.0 if
  weight = 1.0,  otherwise = 1.0 / &lt;weight&gt;),
  average scatter (always = 0.0 if no weights scatter term is fit) 
  and the rms value are
  printed on the screen.
  The fitted parameters and their errors are also printed. The default output is 
  the terminal (STDOUT) and the screen is cleared before the information is 
  output. If a file is specified then the information is appended to
  the named file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:results [file]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':results [file]'>
  <DD>List the results of the current fit. The function value, the fitted value,
  the residual, and the weight are printed for each data point. The default
  output device is the terminal (STDOUT) and the screen is cleared before
  the information is output. If a file is specified then the information is
  appended to the named file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:vshow [file]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':vshow [file]'>
  <DD>A verbose version of "<TT>:show</TT>" which is equivalent to a "<TT>:show</TT>" plus a "<TT>:errors</TT>"
  plus a "<TT>:results</TT>". The default output device is the terminal (STDOUT)
  and the screen is cleared before the information is output.
  If a file is specified then the information is appended to the named file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:page file</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':page file'>
  <DD>Page through the named file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:tolerance [value]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':tolerance [value]'>
  <DD>Show or set the value of the fitting tolerance. Tolerance is the maximum
  fraction by which the reduced chi-squared can change from one iteration to the
  next for the fit to meet the convergence criteria.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:maxiter [value]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':maxiter [value]'>
  <DD>Show or set the maximum number of fitting iterations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:nreject [value]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':nreject [value]'>
  <DD>Show or set the maximum number of rejection iterations. A value of zero
  means that automatic bad data rejection is turned off. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:low_reject [value], :high_reject [value]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':low_reject [value], :high_reject [value]'>
  <DD>Show or set the values of the bad data rejection limits.
  If both low_reject and high_reject are zero then automatic bad data
  rejection is turned off.
  If either of the high or low rejection limits are greater than zero,
  and nreject is greater than zero, the rms of the initial fit is computed.
  Points with residuals
  more than low_reject * rms below zero and high_reject * rms above zero
  are removed before the final fit. Rejected points are marked on the 
  graphs with diamonds. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:grow [value]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':grow [value]'>
  <DD>Show or set the value of the rejection growing radius. Any points
  within this distance of a rejected point are also rejected. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:fit [parameter] [value]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':fit [parameter] [value]'>
  <DD>Set the starting guess value for the named coefficient and allow the 
  parameter value to change (converge) during the fit.
  If the value is not specified inlfit will use the last starting guess.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:const [parameter] [value]</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':const [parameter] [value]'>
  <DD>Set the named parameter to be a constant with the specified value, i.e,
  its value won't change during the fit.
  If the value is not specified inlfit will use its last starting value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:/help</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':/help'>
  <DD>Print help for the graph formatting options (the w key).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:.help</A></B></DT>
  <! Sec='THE NON-LINEAR INTERACTIVE FITTING PACKAGE' Level=0 Label='' Line=':.help'>
  <DD>Print help for the general IRAF graphics options.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'THE NON-LINEAR INTERACTIVE FITTING PACKAGE'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Fit a set of UBV standard star data non-interactively using the automatic
  bad data rejection algorithm and the configuration file shown in example
  2 under the configuration file section.
  <P>
  <PRE>
      ph&gt; fitparams m92.obs m92.cat m92.config m92.fit nreject=10 inter-
  <P>
  	... compute valued for the parameters in all the transformation
  	    equations
  <P>
      ph&gt; page m92.fit
  <P>
  	... check that the fitted parameter values are reasonable
  <P>
      ph&gt; invertfit m92.obs m92.cat m92.config m92.fit m92.out
  <P>
  	... evaluate the transformation equations for all the standard
  	    stars
  </PRE>
  <P>
  2. Fit the same set of data interactively but deleting bad points by
  eye instead of using the automatic rejection algorithm.
  <P>
  <PRE>
      ph&gt; fitparams m92.obs m92.cat m92.config m92.fit 
  <P>
  	... a default plot of the UFIT equation comes up on the screen
  	    (the fit or right-hand side of the equation is plotted
  	    versus the function or left-hand side of the equation)
  <P>
  	... type <TT>'?'</TT> to show the available commands
  <P>
  	... type <TT>'i'</TT> to plot the residuals versus the function (LHS of
  	    the equation)
  <P>
  	... delete bad points with the <TT>'d'</TT> key and refit using the <TT>'f'</TT>
  	    key
  <P>
  	... check for any dependencies of the residuals on the color
  	    term by reprogramming the graph key <TT>'l'</TT> using the <TT>'g'</TT> key 
  	    (type <TT>'g'</TT> to enter the reprogramming menu, <TT>'l'</TT> after the
  	    prompt to reprogram the <TT>'l'</TT> key, and "UB, residuals" in
  	    response to the question of which axes to plot
  <P>
  	... list the plot windowing menu by typing <TT>'w'</TT> followed by <TT>'?'</TT>
  	    after the "window:" prompt
  <P>
  	... type <TT>'w'</TT> followed by <TT>'z'</TT> after the ":window" prompt to zoom
  	    up on an interesting area in the plot, a <TT>'w'</TT> followed by <TT>'a'</TT>
  	    will return to normal scaling
  <P>
  	... type <TT>'q'</TT> to quit the fit for this equation 
  <P>
  	... answer "yes" to the question about saving the fit
  <P>
  	... proceed to the next fit by typing "next" in response to the
  	    prompt
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  chkconfig,mkconfig,gtools,inlfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'THE CONFIGURATION FILE' 'THE NON-LINEAR INTERACTIVE FITTING PACKAGE' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>