starlist — Make an artificial star list
=======================================

**Package: artdata**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>starlist (Feb90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.artdata</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>starlist (Feb90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>starlist</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_task">TASK</A></H2>
  <! BeginSection: 'TASK'>
  <UL>
  starlist -- make an artificial star list
  </UL>
  <! EndSection:   'TASK'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  starlist starlist nstars
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_starlist">starlist</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='starlist' Line='starlist'>
  <DD>The name of the output text file for the x and y coordinates
  and magnitudes of the artificial stars.  Output will be appended to this
  file is it exists.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nstars">nstars = 5000</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nstars' Line='nstars = 5000'>
  <DD>The number of stars in the output star list.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Examine plots and change the parameters of the spatial luminosity
  distributions interactively.
  </DD>
  </DL>
  <P>
  			SPATIAL DISTRIBUTION
  <DL>
  <DT><B><A NAME="l_spatial">spatial = "<TT>uniform</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='spatial' Line='spatial = "uniform"'>
  <DD>Type of spatial distribution.  The types are:
  <DL>
  <DT><B><A NAME="l_uniform">uniform</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='uniform' Line='uniform'>
  <DD>The stars are uniformly distributed between <I>xmin</I>, <I>xmax</I>, <I>ymin</I>,
  and <I>ymax</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_hubble">hubble</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='hubble' Line='hubble'>
  <DD>The stars are distributed around the center of symmetry <I>xcenter</I> and
  <I>ycenter</I> according to a Hubble density law of core radius
  <I>core_radius</I> and background density <I>base</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_file">file</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='file' Line='file'>
  <DD>The radial density function is contained in the text file <I>sfile</I>.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmin">xmin = 1., xmax = 512., ymin = 1., ymax = 512.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmin' Line='xmin = 1., xmax = 512., ymin = 1., ymax = 512.'>
  <DD>The range of output coordinates in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xcenter">xcenter = INDEF, ycenter = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcenter' Line='xcenter = INDEF, ycenter = INDEF'>
  <DD>The coordinate of the center of symmetry for the "<TT>hubble</TT>"
  and "<TT>file</TT>" radial density functions. The default is the
  midpoint of the coordinate limits.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_core_radius">core_radius = 30</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='core_radius' Line='core_radius = 30'>
  <DD>The core radius of the Hubble spatial distribution in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_base">base = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='base' Line='base = 0.0'>
  <DD>The background density relative to the central density of the Hubble
  density distribution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sseed">sseed = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sseed' Line='sseed = 1'>
  <DD>The initial value supplied to the random number generator used to
  generate the output x and y coordinates.
  If a value of "<TT>INDEF</TT>" is given then the clock
  time (integer seconds since 1980) is used as the seed yielding
  different random numbers for each execution.
  </DD>
  </DL>
  <P>
  			MAGNITUDE DISTRIBUTION
  <DL>
  <DT><B><A NAME="l_luminosity">luminosity = "<TT>powlaw</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='luminosity' Line='luminosity = "powlaw"'>
  <DD>Type of luminosity distribution.  The types are:
  <DL>
  <DT><B><A NAME="l_uniform">uniform</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='uniform' Line='uniform'>
  <DD>The stars are uniformly distributed between <I>minmag</I> and <I>maxmag</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_powlaw">powlaw</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='powlaw' Line='powlaw'>
  <DD>The stars are distributed according to a power law with coefficient
  <I>power</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_salpeter">salpeter</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='salpeter' Line='salpeter'>
  <DD>The stars are distributed with a Salpeter luminosity function between
  <I>minmag</I> and <I>maxmag</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bands">bands</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='bands' Line='bands'>
  <DD>The stars are distributed with a Bahcall and Soneira luminosity function
  between <I>minmag</I> and <I>maxmag</I>.  The function is described
  by the parameters <I>alpha</I>, <I>beta</I>, <I>delta</I> and <I>mstar</I>
  whose default values give a best fit to the observed main sequence in several
  nearby globular clusters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_file">file</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='file' Line='file'>
  <DD>The luminosity function is contained in the text file <I>lfile</I>.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_minmag">minmag = -7., maxmag = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minmag' Line='minmag = -7., maxmag = 0.'>
  <DD>The range of output magnitudes.  The "<TT>salpeter</TT>" luminosity function
  imposes limits of -4 and 16 and the "<TT>bands</TT>" luminosity function
  imposes limits of -7 and 17 relative to the zero point given by
  <I>mzero</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mzero">mzero = -4.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mzero' Line='mzero = -4.'>
  <DD>The zero point for converting the output relative magnitudes
  to absolute magnitudes for the Salpeter and Bahcall and Soneira
  luminosity functions.  For example the default values give an
  absolute magnitude range of -3 to +4.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_power">power = 0.6</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='power' Line='power = 0.6'>
  <DD>Coefficient for the power law magnitude distribution.
  The default value of 0.6 is the value for a homogeneous
  and isotropic distribution with no cutoff in distance.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_alpha">alpha = 0.74, beta = 0.04, delta = 0.294, mstar = 1.28</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='alpha' Line='alpha = 0.74, beta = 0.04, delta = 0.294, mstar = 1.28'>
  <DD>The parameters of the Bahcall and Soneira luminosity function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lseed">lseed = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lseed' Line='lseed = 1'>
  <DD>The initial value supplied to the random number generator used to
  generate the output magnitudes.
  If a value of "<TT>INDEF</TT>" is given then the clock
  time (integer seconds since 1980) is used as the seed yielding
  different random numbers for each execution.
  </DD>
  </DL>
  <P>
  			USER FUNCTIONS
  <DL>
  <DT><B><A NAME="l_sfile">sfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sfile' Line='sfile'>
  <DD>The name of the input text file containing the sampled spatial radial
  density
  function, one sample point per line, with the radius and relative probability
  in columns one and two respectively. The sample points need not be
  uniformly spaced or normalized.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nssample">nssample = 100</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nssample' Line='nssample = 100'>
  <DD>The number of points at which the <I>spatial</I> density function is 
  sampled. If the <I>spatial</I> density function is analytic or approximated
  analytically (the "<TT>uniform</TT>" and "<TT>hubble</TT>" options) the function is sampled
  directly. If the function is read from a file  (the "<TT>file</TT>" option) an
  initial smoothing step is performed before sampling.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sorder">sorder = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sorder' Line='sorder = 10'>
  <DD>The order of the spline fits used to evaluate the integrated spatial
  density function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lfile">lfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lfile' Line='lfile'>
  <DD>The name of the input text file containing the sampled luminosity
  function, one sample point per line, with the magnitude and relative probability
  in columns one and two respectively. The sample points need not be
  uniformly spaced or normalized.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nlsample">nlsample = 100</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlsample' Line='nlsample = 100'>
  <DD>The number of points at which the luminosity function is sampled. If
  the luminosity function is analytic or approximated analytically (the
  "<TT>salpeter</TT>" and "<TT>bands</TT>" options) the function is sampled directly.  If
  it is read from a file  (the "<TT>file</TT>" option) an initial smoothing step
  is performed before sampling.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lorder">lorder = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lorder' Line='lorder = 10'>
  <DD>The order of the spline fits used to evaluate the integrated
  <I>luminosity</I> function.
  </DD>
  </DL>
  <P>
  			INTERACTIVE PARAMETERS
  <DL>
  <DT><B><A NAME="l_rbinsize">rbinsize = 10.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rbinsize' Line='rbinsize = 10.'>
  <DD>The bin size in pixels of the plotted histogram of the radial density
  distribution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mbinsize">mbinsize = 0.5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mbinsize' Line='mbinsize = 0.5'>
  <DD>The bin size in magnitudes of the plotted histogram of the luminosity function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = stdgraph</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = stdgraph'>
  <DD>The default graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>The graphics cursor.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Starlist</B> generates a list of x and y coordinates and magnitudes
  for a sample of <I>nstars</I> stars based on a user selected spatial
  density function <I>spatial</I>  and luminosity function
  <I>luminosity</I> and writes (appends) the results to the text file
  <I>starlist</I>. If the <I>interactive</I> parameter is "<TT>yes</TT>" the user
  can interactively examine plots of the spatial density function,
  the radial density function, and the luminosity function, and alter the
  parameters of the task until a satisfactory artificial field is
  generated.
  <P>
  The spatial density function generates x and y values around a center
  of symmetry defined by <I>xcenter</I> and <I>ycenter</I> within the x and
  y limits <I>xmin</I>, <I>xmax</I>, <I>ymin</I> and <I>ymax</I> according to
  the spatial density function specified by <I>spatial</I>.  The three
  supported spatial density functions are listed below where R is the
  radial distance in pixels, P is the relative spatial density, C is a
  constant and f is the best fitting cubic spline function to the spatial
  density function R(user), P(user) supplied by the user in the text file
  <I>sfile</I>.
  <P>
  <PRE>
      uniform:  P = C
      hubble:   P = 1.0 / (1 + R / core_radius) ** 2 + base
      file:     P = f (R(user), P(user))
  </PRE>
  <P>
  The Hubble and user file spatial density function are sampled at
  <I>nssample</I> equally spaced points, and integrated to give the
  spatial density probability function at each sampled point. The
  integrated probability function is normalized and approximated by a
  cubic spline of order <I>sorder</I>.  The x and y coordinates are
  computed by randomly sampling the integrated probability function until
  <I>nstars</I> stars which satisfy the x and y coordinate limits
  <I>xmin</I>, <I>xmax</I>, <I>ymin</I> and <I>ymax</I> are generated.
  <P>
  The luminosity function generates relative magnitude values between
  <I>minmag</I> and <I>maxmag</I> according to the luminosity function
  specified by <I>luminosity</I>.  The four supported luminosity functions
  are defined below where M is the magnitude, P is the relative luminosity
  function, C is a constant and f is the best fitting cubic spline
  function to the luminosity function M(user), P(user) supplied by the
  in the text file <I>lfile</I>.
  <P>
  <PRE>
    uniform:  P = C
  <P>
    powlaw:   P = C * 10. ** (power * M)
  <P>
    salpeter: P = C * 10. ** (-3.158 + 1.551e-1*dM - 5.194e-3*dM**2)
  <P>
              dM = M - mzero
  <P>
                               C * 10. ** (beta * dM)
    bands:   P =  --------------------------------------------------
                 (1. + 10. ** ((beta-alpha)*delta*dM))) ** 1. /delta
  <P>
             dM = M - mstar - mzero
  <P>
    file:    P = f (M(user), P(user))
  </PRE>
  <P>
  The Salpeter and "<TT>bands</TT>" functions are defined in terms of absolute
  magnitudes so the parameter <I>mzero</I> is used to convert from
  relative magnitudes.  Equivalently, one could use absolute magnitudes
  for the magnitude limits while setting the zero point to 0.
  <P>
  The luminosity function is sampled at <I>nlsample</I> equally spaced
  points, and integrated to give the luminosity probability function at
  each sampled point. The probablity function is normalized and
  approximated by a cubic spline of order <I>lorder</I>. The magnitudes
  are computed by randomly sampling the integrated probability function
  until <I>nstars</I> objects which satisfy the magnitude limits
  <I>minmag</I> and <I>maxmag</I> are generated.  The Salpeter luminosity
  is a best fit function to the data of McCuskey (McCuskey, 1966, Vistas
  Astr. 7, 141). The Bahcall and Soneira function and the default values
  of the parameters are discussed by Bahcall and Soneira (Ap.J.  Supp. 44, 73).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursors">CURSORS</A></H2>
  <! BeginSection: 'CURSORS'>
  <UL>
  The following interactive keystroke commands are available from within the
  STARLIST task.
  <P>
  <PRE>
  	Starlist Keystroke Commands
  <P>
  ?	Print options
  f	Fit  one or more of the following
  	    Spatial density function (SDF)
  	    Luminosity functions (LF)
  x	Plot the x-y spatial density function
  r	Plot the histogram of the radial density function
  m	Plot the histogram of the luminosity function
  :	Colon escape commands (see below)
  q	Exit program
  </PRE>
  <P>
  The following parameters can be shown or set from within the STARLIST task.
  <P>
  <P>
  <PRE>
  		Starlist Colon Commands
  <P>
  :show			Show starlist parameters
  :nstars     [value]	Number of stars
  <P>
  :spatial    [string]	Spatial density function (SDF)
  			(uniform|hubble|file) 
  :xmin       [value]	Minimum X value
  :xmax       [value]	Maximum X value
  :ymin       [value]	Minimum Y value
  :ymax       [value]	Maximum Y value
  :xcenter    [value]	X center for SDF
  :ycenter    [value]	Y center for SDF
  :core       [value]	Core radius for Hubble density function
  :base       [value]	Background density for Hubble density function
  <P>
  :luminosity [string]	Luminosity function (LF)
  			(uniform|powlaw|salpeter|bands|file)
  :minmag     [value]	Minimum magnitude
  :maxmag     [value]	Maximum magnitude
  :mzero	    [value]	Magnitude zero-point for salpeter and bands LF
  :power	    [value]	Exponent for powlaw LF
  :alpha      [value]	Alpha parameter for bands LF
  :beta       [value]	Beta parameter for bands LF
  :delta      [value]	Delta parameter for bands LF
  :mstar      [value]	Mstar parameter for bands LF
  <P>
  :sfile	    [string]    File containing the user SDF
  :nssample   [value]	Number of SDF sample points
  :sorder	    [value]	Order of spline fit to integrated SDF
  :lfile	    [string]    File containing the user LF
  :nlsample   [value]	Number of LF sample points 
  :lorder	    [value]	Order of spline fit to the integrated LF
  <P>
  :rbinsize   [value]	Resolution of radial profile histogram (pixels)
  :mbinsize   [value]	Resolution of magnitude histogram (mag)
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSORS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create a uniform artificial starfield of 5000 stars for a 512 square image.
  <P>
  <PRE>
      ar&gt; starlist starfield.dat 5000
      ar&gt; mkobjects starfield obj=starfield.dat gain=2 rdnoise=10 poisson+
  </PRE>
  <P>
  This example takes about a minute on a SPARCstation 1.
  <P>
  2. Create a globular cluster field of 5000 stars for a 512 square image.
  <P>
  <PRE>
      ar&gt; starlist gc.dat 5000 spat=hubble lum=bands
      ar&gt; mkobjects starfield obj=gc.dat gain=2 rdnoise=10 poisson+
  </PRE>
  <P>
  This example takes about a minute on a SPARCstation 1.
  <P>
  3. Examine the distributions for a Hubble spatial distribution
  and Salpeter magnitude distribution using 1000 stars without
  creating a data file.
  <P>
  <PRE>
      ar&gt; starlist dev$null 1000 inter+ spat=hubble lum=salpeter
  	    ... an x-y plot will appear on the screen
  	    ... type r to examine the radial density function
  	    ... type m to examine the luminosity function
  	    ... type = to make a copy of any of the plots
  	    ... type q to quit
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_STARLIST">STARLIST V2.11+</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='STARLIST' Line='STARLIST V2.11+'>
  <DD>The random number seeds can be set from the clock time by using the value
  "<TT>INDEF</TT>" to yield different random numbers for each execution.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The spline approximation to the spatial density and luminosity
  probability functions can  cause wiggles in the output spatial density
  and luminosity functions. Users can examine the results interactively
  and experiment with the spline order and number of sample points if
  they are not satisfied with the results of STARLIST. The default setup
  of 10 sample points per spline piece is generally satisfactory for the
  spatial density and luminosity functions supplied here.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  gallist mkobjects
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'TASK' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSORS' 'EXAMPLES' 'REVISIONS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>