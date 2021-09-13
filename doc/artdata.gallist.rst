gallist — Make an artificial galaxies list
==========================================

**Package: artdata**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>gallist (Feb90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.artdata</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>gallist (Feb90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>gallist</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_task">TASK</A></H2>
  <! BeginSection: 'TASK'>
  <UL>
  gallist -- make an artificial galaxies list
  </UL>
  <! EndSection:   'TASK'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  gallist gallist ngals
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_gallist">gallist</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gallist' Line='gallist'>
  <DD>The name of the output text file for the x and y coordinates,
  magnitudes, profile types, half-flux radii, axial ratios, and position
  angles of the artificial galaxies.  Output will be appended to this
  file if it exists.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ngals">ngals = 100</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ngals' Line='ngals = 100'>
  <DD>The number of galaxies in the output galaxies list.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Examine plots and change the parameters of the spatial, luminosity, and
  morphology distributions interactively.
  </DD>
  </DL>
  <P>
  			SPATIAL DISTRIBUTION
  <DL>
  <DT><B><A NAME="l_spatial">spatial = "<TT>uniform</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='spatial' Line='spatial = "uniform"'>
  <DD>Type of spatial distribution for the galaxies.  The types are:
  <DL>
  <DT><B><A NAME="l_uniform">uniform</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='uniform' Line='uniform'>
  <DD>The galaxies are uniformly distributed between <I>xmin</I>, <I>xmax</I>,
  <I>ymin</I>, and <I>ymax</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_hubble">hubble</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='hubble' Line='hubble'>
  <DD>The galaxies are distributed around the center of symmetry <I>xcenter</I> and
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
  <DD>The range of the output coordinates in pixels.
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
  <DT><B><A NAME="l_core_radius">core_radius = 50</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='core_radius' Line='core_radius = 50'>
  <DD>The core radius of the Hubble density distribution in pixels.
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
  <DT><B><A NAME="l_sseed">sseed = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sseed' Line='sseed = 2'>
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
  <DD>Type of luminosity distribution for the galaxies.  The types are:
  <DL>
  <DT><B><A NAME="l_uniform">uniform</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='uniform' Line='uniform'>
  <DD>The galaxies are uniformly distributed between <I>minmag</I> and
  <I>maxmag</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_powlaw">powlaw</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='powlaw' Line='powlaw'>
  <DD>The galaxies are distributed according to a power law with coefficient
  <I>power</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_schecter">schecter</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='schecter' Line='schecter'>
  <DD>The galaxies are distributed according to a Schecter luminosity
  function with characteristic magnitude <I>mstar</I> and power law exponent
  <I>alpha</I> between <I>minmag</I> and <I>maxmag</I>.
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
  <DD>The range of output relative magnitudes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mzero">mzero = 15.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mzero' Line='mzero = 15.'>
  <DD>Magnitude zero point for Schecter luminosity function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_power">power = 0.6</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='power' Line='power = 0.6'>
  <DD>Coefficient for the power law magnitude distribution The default value
  of 0.6 is the Euclidean value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_alpha">alpha = -1.24</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='alpha' Line='alpha = -1.24'>
  <DD>The power law exponent of the Schecter luminosity function.
  The default value is that determined by Schecter from nearby galaxies.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mstar">mstar = -21.41</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mstar' Line='mstar = -21.41'>
  <DD>The characteristic magnitude of the Schecter luminosity function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lseed">lseed = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lseed' Line='lseed = 2'>
  <DD>The initial value supplied to the random number generator used to
  generate the output magnitudes.
  If a value of "<TT>INDEF</TT>" is given then the clock
  time (integer seconds since 1980) is used as the seed yielding
  different random numbers for each execution.
  </DD>
  </DL>
  <P>
  			MORPHOLOGY DISTRIBUTION
  <DL>
  <DT><B><A NAME="l_egalmix">egalmix = 0.4</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='egalmix' Line='egalmix = 0.4'>
  <DD>The fraction of the galaxies that are "<TT>ellipticals</TT>" represented
  by a de Vaucouleurs surface brightness law as opposed to "<TT>spirals</TT>"
  represented by an exponential disk surface brightness law.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ar">ar = 0.3</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ar' Line='ar = 0.3'>
  <DD>Minimum elliptical galaxy axial ratio (major/minor ratio).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_eradius">eradius = 20.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='eradius' Line='eradius = 20.0'>
  <DD>The maximum elliptical galaxy half-flux semi-major scale radius.  This is
  the radius of an elliptical galaxy with magnitude <I>minmag</I>
  before a random factor is added.  Spiral galaxies and fainter galaxies
  are scaled from this value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sradius">sradius = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sradius' Line='sradius = 1.0'>
  <DD>Ratio between half-flux scale radii of spiral and elliptical models at the
  same magnitude.  For example an elliptical galaxy with magnitude
  <I>minmag</I> will have radius <I>eradius</I> while a spiral galaxy
  of the same magnitude with have radius <I>sradius</I> * <I>eradius</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_absorption">absorption = 1.2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='absorption' Line='absorption = 1.2'>
  <DD>Absorption correction for edge on spirals in magnitudes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_z">z = 0.05</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z' Line='z = 0.05'>
  <DD>Minimum redshift for power law distributed galaxies.  This is the
  redshift assigned galaxies of magnitude <I>minmag</I>.  The redshifts
  are assumed proportional to the square root of the apparent luminosity;
  i.e the luminosity distance proportional to redshift.  The redshift is used
  for computing the mean apparent sizes of the galaxies
  according to (1+z)**2 / z.
  </DD>
  </DL>
  <P>
  			USER FUNCTIONS
  <DL>
  <DT><B><A NAME="l_sfile">sfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sfile' Line='sfile = ""'>
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
  <DD>The number of points at which the spatial density function is 
  sampled. If the spatial density function is analytic or approximated
  analytically (the "<TT>hubble</TT>" option) the function is sampled
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
  <DT><B><A NAME="l_lfile">lfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lfile' Line='lfile = ""'>
  <DD>The name of the input text file containing the sampled luminosity
  function, one sample point per line, with the magnitude and relative
  probability in columns one and two respectively. The sample points need
  not be uniformly spaced or normalized.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nlsample">nlsample = 100</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlsample' Line='nlsample = 100'>
  <DD>The number of points at which the luminosity function is 
  sampled. If the luminosity function is analytic or approximated
  analytically (the "<TT>uniform</TT>", "<TT>powlaw</TT>" and "<TT>schecter</TT>" options) the
  function is sampled directly.  If it is read from a file
  (the "<TT>file</TT>" option) an initial smoothing step is performed before sampling.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lorder">lorder = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lorder' Line='lorder = 10'>
  <DD>The order of the spline fits used to evaluate the integrated
  luminosity function.
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
  <DT><B><A NAME="l_dbinsize">dbinsize = 0.5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dbinsize' Line='dbinsize = 0.5'>
  <DD>The bin size in pixels of the plotted histogram of the half-power semi-major
  axis distribution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ebinsize">ebinsize = 0.1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ebinsize' Line='ebinsize = 0.1'>
  <DD>The bin size of the plotted histogram of the axial ratio distribution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pbinsize">pbinsize = 20.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pbinsize' Line='pbinsize = 20.'>
  <DD>The bin size in degrees of the plotted histogram of the position angle
  distribution.
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
  <B>Gallist</B> generates a list of x and y coordinates, magnitudes,
  morphological types, half-power radii, axial ratios, and position
  angles for a sample of <I>ngals</I> galaxies based on a user selected
  spatial density function <I>spatial</I>  and luminosity function
  <I>luminosity</I> and writes (appends) the results to the text file
  <I>gallist</I>. If the <I>interactive</I> parameter is "<TT>yes</TT>" the user can
  interactively examine plots of the spatial density function, the
  radial density function,  the luminosity function, radii, axial ratios,
  and position angle distributions and alter the parameters of the task
  until a satisfactory artificial field is generated.
  <P>
  The spatial density function generates x and y values around a center
  of symmetry defined by <I>xcenter</I> and <I>ycenter</I> within the x and
  y limits <I>xmin</I>, <I>xmax</I>, <I>ymin</I> and <I>ymax</I> according to
  the spatial density function specified by <I>spatial</I>.  The three
  supported spatial density functions are listed below where R is the
  radial distance in pixels, P is the relative spatial density, C is a
  constant, and f is the best fitting cubic spline function to the spatial
  density function R(user), P(user) supplied by the user in the text file
  <I>sfile</I>.
  <P>
  <PRE>
    uniform:  P = C
    hubble:   P = 1.0 / (1 + R / core_radius) ** 2 + base
    file:     P = f (R(user), P(user))
  </PRE>
  <P>
  The Hubble and user spatial density functions are sampled at
  <I>nssample</I> equally spaced points, and integrated to give the
  spatial density probability function at each sampled point. The
  integrated probability function is normalized and approximated by a
  cubic spline of order <I>sorder</I>.  The x and y coordinates are
  computed by randomly sampling the integrated probability function until
  <I>ngals</I> galaxies which satisfy the x and y coordinate limits
  <I>xmin</I>, <I>xmax</I>, <I>ymin</I> and <I>ymax</I> are generated.
  <P>
  The luminosity function generates relative magnitude values between
  <I>minmag</I> and <I>maxmag</I> (before absorption effects are added)
  according to the luminosity function specified by <I>luminosity</I>.
  The four supported luminosity functions are listed below where M is the
  magnitude, P is the relative luminosity function, C is a constant and f
  is the best fitting cubic spline function to the luminosity function
  M(user), P(user) supplied by the user in the text file <I>lfile</I>.
  <P>
  <PRE>
    uniform:   P = C
    powlaw:    P = C * 10. ** (power * M)
    schecter:  P = C * 10. ** (alpha * dM) * exp (-10. ** dM)
    file:      P = f (M(user), P(user))
  <P>
    where      dM = 0.4 * (mstar - M + mzero)
  </PRE>
  <P>
  The uniform distribution is not very physical but may be useful for
  testing.  The power law distribution is that expected for a homogeneous
  and isotropic distribution of galaxies.  The default value of 0.6 is
  that which can be calculated simply from Euclidean geometry.  Observations
  of faint galaxies generally show a smaller value.  The Schecter
  function provides a good approximation to a galaxy cluster when
  used in conjunction with the Hubble spatial distribution (though there
  is no mass segregation applied).  The "<TT>best fit</TT>" values for the
  parameters <I>mstar</I> and <I>alpha</I> are taken from the paper by
  Schecter (Ap.J 203, 297, 1976).  The <I>mzero</I> parameter is used
  to convert to absolute magnitudes.  Note that it is equivalent to
  set <I>mzero</I> to zero and adjust the characteristic magnitude
  to the same relative magnitude scale or to use absolute magnitudes
  directly.
  <P>
  The Schecter and user file distributions are sampled at <I>nlsample</I>
  equally spaced points, and integrated to give the luminosity
  probability function at each sampled point. The probability function is
  normalized and approximated by a cubic spline of order <I>lorder</I>.
  The magnitudes are computed by randomly sampling the integrated
  probability function until <I>ngals</I> objects which satisfy the
  magnitude limits <I>minmag</I> and <I>maxmag</I> are generated.
  <P>
  The artificial galaxies have one of two morphological types,
  "<TT>ellipticals</TT>" with a de Vaucouleurs surface brightness law and
  "<TT>spirals</TT>" with an exponential surface brightness law. The fraction
  of elliptical galaxies is set by the parameter <I>egalmix</I>.  The
  position angles of the major axis are distributed uniformly between 0.0
  and 360.0 degrees.  The axial ratio (major to minor) of the elliptical
  models is allowed to range uniformly between 1 and <I>ar</I>
  (that is E0 - E7).
  <P>
  The spiral models have inclinations, i, ranging uniformly between 0 and
  90 degrees.  The axial ratio is then given by
  <P>
  	a/b = sqrt (sin(i)**2 * .99 + .01)
  <P>
  which is taken from Holmberg in Galaxies and the Universe (which
  references the work of Hubble).  Note the axial ratio is limited to
  0.1 by this formula.  An internal absorption correction is then
  made based on the inclination using the relation
  <P>
  	dM = A * (min (10, cosecant (i)) - 1) / 9
  <P>
  where is the absorption of an edge on galaxy relative to face on and
  the cosecant is limited to 10.  Note that this correction changes
  allows galaxies with magnitudes less than <I>maxmag</I> and alters
  the luminosity function somewhat.  Or in other words, the luminosity
  function is based on absorption corrected magnitudes.
  <P>
  The sizes of the galaxy images are scaled from the maximum half-flux
  radius of an elliptical galaxy given by the parameter <I>eradius</I>.
  This is the radius given to an elliptical galaxy of magnitude
  <I>minmag</I> (prior to adding a random factor described below).  The
  ratio between the half-flux radii of the exponential disk and de
  Vaucouleurs models at a given total magnitude is set by the parameter
  <I>sradius</I> (note this is a fraction of <I>eradius</I> and not an
  actual radius).  This allows adjusting the relative surface brightness
  of elliptical and spiral models.
  <P>
  The distribution of sizes is based on the apparent
  magnitude of the galaxies.  For the power law magnitude distribution
  the cosmological redshift factor for angular diameters is used.  The
  redshift/magnitude relation is assumed to be such that the redshift is
  proportional to the luminosity distance (the square root of the
  apparent luminosity).  Thus,
  <P>
  <P>
  <PRE>
                  Z = z * 10. ** (0.2 * (M - minmag))
                  Zfactor = ((1+Z)**2 / Z) / ((1+z)**2 / z)
    ellipticals:  r = eradisus * Zfactor
    spirals:      r = sradius * eradius * Zfactor
  </PRE>
  <P>
  where z is the reference redshift at the minimum magnitude, and Z is the
  redshift at magnitude M.  For very small z the size varies as the
  luminosity distance but at larger z the images appear more extended with
  lower surface brightness.  For very deep simulations a pure luminosity
  distance relation gives faint galaxies which are too small and compact
  compared to actual observations.
  <P>
  For the other magnitude distributions, the Schecter cluster function
  in particular where all galaxies are at the same distance, the scale radius
  obeys the following relation.
  <P>
  <PRE>
    ellipticals:  r = eradius * 10. ** ((minmag - M) / 6)
    spirals:      r = sradius * eradius * 10. ** ((minmag - M) / 6)
  </PRE>
  <P>
  This relation gives the size decreasing slightly less rapidly than that
  giving a constant surface brightness.  This relation is taken from
  Holmberg (Galaxies and the Universe).
  <P>
  A uniform random factor of 50% is added to the sizes computed for
  the power law magnitude distribution and 20% for the other distributions.
  <P>
  The interactive spatial plot shows the positions of the galaxies, the
  galaxy type (circles are de Vaucouleurs profiles and other types are
  diamonds), and rough size.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursors">CURSORS</A></H2>
  <! BeginSection: 'CURSORS'>
  <UL>
  The following interactive keystroke commands are available from within the
  GALLIST task.
  <P>
  <PRE>
  	Gallist Keystroke Commands
  <P>
  ?	Print options
  f	Fit one or more of following 
  	    Spatial density function (SDF)
              Luminosity  function (LF)
  	    Distribution of morphological type
  	    Diameter distribution
  	    Roundness distribution
  	    Position angle distribution 
  x	Plot the x-y spatial density function
  r	Plot the histogram of the radial density function
  m	Plot the histogram of the luminosity function
  d	Plot the histogram of the diameter values
  e	Plot the histogram of the roundness values 
  p	Plot the histogram of the position angle values
  :	Colon escape commands (see below)
  q	Exit program
  </PRE>
  <P>
  The following parameters can be shown or set from within the GALLIST task.
  <P>
  <PRE>
  		Gallist Colon Commands
  <P>
  :show			Show gallist parameters
  :ngal       [value]	Number of galaxies
  <P>
  :spatial    [string]	Spatial density function (SDF) (uniform|hubble|file) 
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
  			(uniform|powlaw|schecter|file)
  :minmag     [value]	Minimum magnitude
  :maxmag     [value]	Maximum magnitude
  :mzero      [value]	Magnitude zero-point of schecter LF
  :power      [value]     Power law coefficient for powlaw LF
  :alpha      [value]	Schecter parameter
  :mstar      [value]	Characteristic mag for Schecter LF
  <P>
  :egalmix    [value]	Elliptical/Spiral galaxy ratio
  :ar         [value]     Minimum elliptical galaxy axial ratio
  :eradius    [value]     Maximum elliptical half flux radius
  :sradius    [value]     Spiral/elliptical radius at same magnitude
  :z          [value]     Minimum redshift
  :absorption [value]     Absorption correction for spirals
  <P>
  :lfile      [string]    Name of the LF file
  :sfile	    [string]    Name of the SDF file
  :nlsample   [value]	Number of LF sample points 
  :lorder	    [value]	Order of spline approximation to the integrated LF
  :nssample   [value]	Number of SDF sample points
  :sorder	    [value]	Order of spline approximation to the integrated SDF
  <P>
  :rbinsize   [value]	Resolution of radial SDF histogram in pixels
  :mbinsize   [value]	Resolution of magnitude histogram in magnitudes
  :dbinsize   [value]	Resolution of diameter histogram in pixels
  :ebinsize   [value]	Resolution of roundness histogram in pixels
  :pbinsize   [value]     Resolution of position angle histogram in degrees
  </PRE>
  </UL>
  <! EndSection:   'CURSORS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create a galaxy cluster with a power law distribution of field galaxies
  and stars as background/foreground.
  <P>
  <PRE>
      ar&gt; gallist galaxies.dat 100 spatial=hubble lum=schecter egal=.8
      ar&gt; gallist galaxies.dat 500
      ar&gt; starlist galaxies.dat 100
      ar&gt; mkobjects galaxies obj=galaxies.dat gain=3 rdnoise=10 poisson+
  </PRE>
  <P>
  Note that the objects are appended to the same file.  Actually making
  the image with <B>mkobjects</B> takes about 5 minutes (2.5 min cpu) on a
  SPARCstation 1.
  <P>
  2. Examine the distributions for a uniform spatial distribution
  and power law magnitude distribution using 1000 galaxies without
  creating a data file.
  <P>
  <PRE>
      ar&gt; gallist dev$null 1000 inter+
  	    ... an x-y plot will appear on the screen
  	    ... type r to examine the radial density function
  	    ... type m to examine the luminosity function
  	    ... type d to examine the half-flux radii distribution
  	    ... type e to examine the axial ratio distribution
  	    ... type = to make a copy of any of the plots
  	    ... type q to quit
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_GALLIST">GALLIST V2.11+</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='GALLIST' Line='GALLIST V2.11+'>
  <DD>The random number seeds can be set from the clock time by using the value
  "<TT>INDEF</TT>" to yield different random numbers for each execution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_GALLIST">GALLIST V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='GALLIST' Line='GALLIST V2.11'>
  <DD>The default value for the minimum elliptical galaxy axial ratio was
  change to 0.3 to cover the range E0-E7 uniformly.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  This is a first version and is not intended to produce a full model
  of galaxy fields.  Some of the relations used are empirical and
  simple minded with the aim being to produce reasonably realistic images.
  <P>
  The spline approximation to the spatial density and luminosity
  probability functions can cause wiggles in the output spatial density
  and luminosity functions. Users can examine the results interactively
  and experiment with the spline order and number of sample points if
  they are not satisfied with the results of GALLIST. The default setup
  of 10 sample points per spline piece is generally satisfactory for the
  spatial density and luminosity functions supplied here.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  starlist mkobjects
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'TASK' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSORS' 'EXAMPLES' 'REVISIONS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>