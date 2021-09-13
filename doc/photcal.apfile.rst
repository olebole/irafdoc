apfile — Prepare an aperture corrections file from a text file
==============================================================

**Package: photcal**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>apfile (Apr93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>photcal</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>apfile (Apr93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>apfile</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  apfile -- prepare an aperture corrections file from a list of photometry
  files using the daogrow algorithm
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  apfile photfiles incolumns naperts apercors
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_photfiles">photfiles</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photfiles' Line='photfiles'>
  <DD>A list of text files containing the images names or image ids, x and y
  coordinates, filter ids, exposure times, airmasses, aperture radii,
  magnitudes, and magnitude errors
  of all the objects to be used to compute the aperture corrections.
  <I>Photfiles</I> are assumed to be the output of the user's own digital
  photometry program. All the files in <I>photfiles</I> must have the format
  specified by <I>incolumns</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_incolumns">incolumns</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='incolumns' Line='incolumns'>
  <DD>A list of ten numbers separated by commas or whitespace specifying
  which columns in <I>photfiles</I> contain the following quantities: the
  image name or image id, x coordinate, y coordinate, filter id, exposure time,
  airmass, time of observation, first aperture radius, magnitude measured
  inside the first aperture radius, magnitude error measured inside the
  first aperture radius respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_naperts">naperts</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='naperts' Line='naperts'>
  <DD>The number of aperture radii for which aperture radii, magnitudes, and
  magnitude errors are to be extracted from <I>photfiles</I>. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apercors">apercors</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apercors' Line='apercors'>
  <DD>The name of the output text file containing the aperture
  corrections computed between <I>smallap</I> and <I>largeap</I>
  for each image in <I>photfiles</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_smallap">smallap = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='smallap' Line='smallap = 1'>
  <DD>The index of the smallest extracted aperture for which the aperture 
  correction is to be computed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_largeap">largeap = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='largeap' Line='largeap = 0'>
  <DD>The index of the largest extracted aperture for which the aperture 
  correction is to be computed. If <I>largeap</I> is 0, then
  the largest aperture is <I>naperts</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_magfile">magfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='magfile' Line='magfile = ""'>
  <DD>The name of an optional output text file containing the magnitudes
  of all the stars in <I>photfiles</I>, corrected to the aperture <I>largeap</I>
  by using the measured magnitude and computed aperture correction at
  which the estimated error is a minimum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfile">logfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = ""'>
  <DD>The name of an optional output text file containing details of the curve
  of growth model fit for each image in <I>photfiles</I>. If <I>logfile</I> is
  "<TT></TT>", no file is written.  If <I>append</I> = "<TT>no</TT>" a new logfile is written, if
  "<TT>yes</TT>" output is appended to an existing logfile.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_plotfile">plotfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile = ""'>
  <DD>The name of an optional output plot file containing plots of the
  curve of growth model fit, the fit residuals versus aperture radius,
  magnitude inside the first aperture, x coordinate, and y coordinate,
  and the aperture correction versus aperture radius for each image
  in <I>photfiles</I>. If <I>plotfile</I> is "<TT></TT>", no file is written.
  If <I>append</I> = "<TT>no</TT>" a new plotfile is written, if
  "<TT>yes</TT>" output is appended to an existing plotfile.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_append">append = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Open <I>logfile</I> and/or <I>plotfile</I> in append mode ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_obsparams">obsparams = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='obsparams' Line='obsparams = ""'>
  <DD>The name of an optional input text file containing the correct filter ids,
  exposure times, airmasses, and times of observation for each image
  whose values are either
  undefined or incorrectly stored in <I>photfiles</I>. The observing parameters
  for each image are listed in <I>obsparams</I>,
  1 image per line with the image name in column 1 and the filter id,
  exposure time, airmass, and time of exposure in
  <I>obscolumns</I>. The image names must match those in <I>photfiles</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_obscolumns">obscolumns = "<TT>2 3 4 5</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='obscolumns' Line='obscolumns = "2 3 4 5"'>
  <DD>The list of numbers separated by commas or whitespace specifying which
  columns in the text file <I>obsparams</I> contain the correct filter ids,
  exposure times, airmasses, and times of observation respectively. The
  number 0 can be used as
  a place holder in the obscolumns string. For example to correct only
  the <I>photfiles</I> airmass values, <I>obscolumns</I> should be set to
  "<TT>0 0 column 0</TT>", where column is the airmass column number.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maglim">maglim = 0.10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maglim' Line='maglim = 0.10'>
  <DD>The maximum magnitude error permitted in the input magnitude measurements.
  Data at and following the first aperture radius whose associated magnitude
  measurement has an error greater than <I>magerr</I> is rejected on input.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nparams">nparams = 3</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nparams' Line='nparams = 3'>
  <DD>The of number parameters in the five parameter curve of growth model to be fit.
  The remaining parameters 5 - nparams parameters are held constant.
  For <I>nparams</I> = 3, the parameters <I>swings</I>,
  <I>pwings</I>, and <I>pgauss</I> are fit, and <I>rgescale</I> and 
  and <I>xwings</I> maintain their default values.
  <I>Nparams</I> must be greater than or equal to one.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_swings">swings = 1.2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='swings' Line='swings = 1.2'>
  <DD>The slope of the power law component of the analytic curve of growth model
  describing the seeing independent part of the stellar profile. For a
  physically reasonable profile <I>swings</I> must be greater than 1.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pwings">pwings = 0.1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pwings' Line='pwings = 0.1'>
  <DD>The fraction of the total power in the seeing independent
  part of the stellar profile, if <I>xwings</I> is 0.0.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pgauss">pgauss = 0.5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pgauss' Line='pgauss = 0.5'>
  <DD>The fraction of the total power in the seeing dependent part of the
  profile contained in the gaussian rather than the exponential component
  of the analytic curve of growth function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rgescale">rgescale = 0.9</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rgescale' Line='rgescale = 0.9'>
  <DD>The ratio of the exponential to the gaussian radial scale
  lengths in the seeing dependent part of the profile.
  In practice the curve of growth model fits for most data do not depend
  significantly on this parameter and it can be left at its default value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xwings">xwings = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xwings' Line='xwings = 0.0'>
  <DD>A parameter describing the effect of airmass on the total power 
  in the seeing independent part of the stellar profile, where this quantity
  is defined as defined as <I>pwings</I> + <I>xwings</I> * <I>airmass</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Fit the curve of growth interactively ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verify">verify = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no'>
  <DD>Verify interactive user input ? This option is used only if <I>obsparams</I>
  is set to the standard input STDIN.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gcommands">gcommands = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The interactive graphics cursor.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>The default graphics device.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  APFILE takes a list of user generated text files <I>photfiles</I>, 
  containing image names or ids, x and y coordinates, filter ids, exposure times,
  airmasses, times of observation, aperture radii, measured magnitudes,
  and magnitude errors for
  one or more stars in one or more images, computes the aperture correction
  between the apertures <I>smallap</I> and <I>largeap</I> for each image using
  a weighted average of the computed model curve of growth and the observed
  curve of growth, and writes the results to <I>apercors</I>.
  <P>
  APFILE computes the aperture corrections by performing the following steps:
  1) extracts the image names or ids,  x and y coordinates, filter ids, exposure
  times, airmasses, times of observation
  and <I>naperts</I> aperture radii, measured magnitudes,
  and magnitude errors for all the objects in <I>photfiles</I>, 2) rejects data
  for all aperture radii greater than any aperture radius for which the magnitude
  or magnitude error is INDEF, the magnitude error is &gt; <I>maglim</I>,
  or the number of apertures left containing good data is &lt; 2, 
  3) adds in quadrature a magnitude error of 0.001 magnitudes to the extracted
  magnitude errors, 4) edits any incorrect or undefined values of
  the filter id, exposure time, airmass, and time of observation
  in <I>photfiles</I> using the values
  in <I>obsparams</I> if defined, or default values of INDEF, 1.0, 1.25, and INDEF
  respectively, 5) computes the theoretical and observed curve of growth
  curve for each image, 6) computes the adopted curve of growth for each
  image by combining the theoretical and observed curves with weights that
  favor the observed curve at smaller aperture radii and the theoretical curve
  at larger aperture radii, 7) integrates the adopted growth curve between
  the <I>smallap</I> and <I>largeap</I> apertures to
  compute the final aperture correction, 8) writes the results for each image
  to <I>apercors</I>, 9) optionally computes magnitudes for all the stars
  in <I>photfiles</I> corrected to <I>largeap</I> using the observed magnitude
  and computed correction for which the signal to noise is highest,
  10) optionally writes a <I>logfile</I> containing the details of the
  fit for all the individual images, 11) optionally writes a file of
  plots of the fit, the residuals, and the curve of growth for all the
  images.
  <P>
  The parameter <I>incolumns</I> describes the format of <I>photfiles</I>.
  <I>Incolumns</I> is a list of 9 numbers separated by commas or
  whitespace which specify the columns containing the following quantities:
  the image name or id, , the x coordinate, the y coordinate, the filter
  id, the exposure time, the airmass, the time of observation,
  the first aperture radius extracted,
  the first measured magnitude extracted,
  and the first magnitude error extracted. The number of aperture radii,
  magnitudes, and magnitude errors extracted are specified by <I>naperts</I>.
  For example if <I>incolumns</I> is "<TT>1,3,4,0,0,2,5,0,20,35</TT>" and <I>naperts</I>
  is 15, then the image name is assumed to be in column 1,
  the x and y coordinates in columns 3 and 4, the filter id, exposure time,
  and time of exposure
  are missing and will be assigned values of INDEF, 1.0, and INDEF respectively,
  the airmass is in column 2, the aperture
  radii in columns 5-19, the magnitudes in columns 20-34, and the magnitude
  errors in columns 35-49.  The aperture radii must be written in
  <I>photfiles</I> in increasing order of size. The columns image name,
  x coordinate, y coordinate, aperture radii, magnitude, and magnitude error
  are mandatory and must be present in <I>photfiles</I>. The filter id,
  exposure time, and airmass columns are optional in which case they
  may be represented by a "<TT>0</TT>" in the appropriate place in <I>incolumns</I>.
  <P>
  Values of the filter ids, exposure times, airmasses, and times of observation
  which are undefined
  or incorrect in <I>photfiles</I>, can be entered or corrected by reading values
  from the file <I>obsparams</I> a simple multi-column text file with a
  format specified by <I>obscolumns</I>.
  If no values are read from <I>photfiles</I> or <I>obsparams</I> default values
  for the filter id, exposure time, airmass, and time of observation
  of "<TT>INDEF</TT>", 1.0, 1.25, "<TT>INDEF</TT>" respectively will be assigned.
  It must be emphasized that the airmass is actually used in the curve of
  growth analysis only if <I>nparams</I> is equal to
  5, and that the quantities filter id and exposure time are not used in
  the analysis at all. However if the user should wish to use the corrected
  magnitudes optionally computed and written to <I>magfile</I> in any subsequent
  analysis it is important to include the correct values of
  these quantities in <I>magfile</I>. 
  <P>
  If <I>interactive</I> is "<TT>yes</TT>", the user can interact with the curve of
  growth fitting process by examining plots of the model fit, the residuals
  versus aperture radius, magnitude in the first aperture, x and y coordinates,
  and the aperture correction
  as a function of radius, by changing the number of parameters to be fit and
  their initial values, deleting and undeleting points with the graphics
  cursor, refitting the model curve of growth and reexamining the results
  until satisfied. Users must realize that when deleting and undeleting
  points with the graphics cursor data for all the apertures above
  the one being deleted or undeleted will also be deleted.
  <P>
  The output aperture corrections file <I>apercors</I> is a simple text
  file containing the image name in column 1, the aperture correction
  computed from <I>smallap</I> to <I>largeap</I> in column 2, and the
  estimated error in the aperture correction in column 3.
  The sign of the aperture correction is such that the
  correction must be added to the observed magnitude to compute the corrected
  magnitude. <I>Apercors</I> is written in a form suitable for input to
  the MKNOBSILE, MKOBSFILE, or OBSFILE tasks.
  <P>
  If <I>magfile</I> is not "<TT></TT>", a file containing the image name or id, x and y
  position, filter id, exposure time, airmass, magnitude corrected to
  <I>largeap</I> using the observed magnitude and computed correction at the
  aperture radius with the highest signal-to-noise ratio, and the associated
  magnitude error, for all the stars in all the images in <I>photfiles</I>.
  <I>Magfile</I> is written in a form suitable for input to the OBSFILE task.
  <P>
  If <I>logfile</I> is not "<TT></TT>", all the details and diagnostics of the
  curve of growth fit are logged either to a new file, if <I>append</I> = "<TT>no</TT>"
  or to a previously existing file, <I>append</I> = "<TT>yes</TT>". The output
  consists of: 1) a banner listing
  the date, time, and <I>apercors</I> for which the entry is relevant, 2)
  a listing of the number of parameters <I>nparams</I> in the five parameter
  curve of growth model to be fit, the initial values of all the parameters, and
  the small and large aperture numbers, 3) the fitted values of the
  curve of growth model parameters and their errors where parameters which
  were not fit have zero-valued errors, 4) the computed seeing radius
  for each image,
  5) the theoretical, observed, and adopted curves of growth and
  their associated errors, 6) the aperture correction to  largeap,
  the estimated total aperture correction to an
  aperture radius twice the largest aperture radius, and the estimated error
  in the aperture correction, 7) the aperture
  correction from <I>smallap</I> to <I>largeap</I>, 8) for each star
  in the image the observed magnitudes, magnitude corrected to the largest
  aperture, and magnitude corrected to twice the largest aperture, and
  finally, 9) a summary of the mean adopted curve of growth, the mean residual,
  and the mean residual squared for all the data for all the images
  as a function of aperture radius.
  <P>
  If <I>plotfile</I> is not "<TT></TT>", plots of the final curve of growth model fit,
  residuals as a function of aperture radius, magnitude, x, y, and the
  aperture correction to the largest aperture <I>largeap</I>
  for each image in <I>photfiles</I> are saved in the plot metacode file
  <I>plotfile</I>..
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursor_commands">CURSOR COMMANDS</A></H2>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The following commands are available in interactive graphics cursor mode.
  <P>
  <PRE>
  	Keystroke Commands 
  <P>
  ?	Print help
  w	Print computed aperture correction
  c	Print coordinates of star nearest cursor
  f	Compute a new fit
  d	Delete point(s) nearest the cursor
  u	Undelete point(s) nearest the cursor
  m	Plot the observed and model cog versus radius
  r	Plot the cog fit residuals versus radius
  b	Plot the cog fit residuals versus magnitude
  x	Plot the cog residuals versus the x coordinate
  y	Plot the cog residuals versus the y coordinate
  a	Plot the aperture correction versus radius
  g	Redraw the current plot
  n	Move to the next image
  p	Move to the previous image
  q	Quit task
  <P>
  	Colon commands
  <P>
  :show   parameters   Show the initial cog model parameter values
  :show   model	     Show the fitted cog model parameters
  :show   seeing       Show the computed seeing radii for all images
  :image  [value]      Show/set the image to be analyzed
  <P>
  	Colon Parameter Editing Commands
  <P>
  :smallap   [value]  Show/set the index of the smallest aperture
  :largeap   [value]  Show/set the index of the largest aperture
  :nparams   [value]  Show/set the number of cog model parameters to fit 
  :swings	   [value]  Show/set initial power law slope of stellar wings
  :pwings	   [value]  Show/set fraction of total power in stellar wings 
  :pgauss	   [value]  Show/set fraction of total core power in gaussian 
  :rgescale  [value]  Show/set ratio of exp to gauss radial scales
  :xwings	   [value]  Show/set the extinction coefficient
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H2><A NAME="s_algorithms">ALGORITHMS</A></H2>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  The algorithm used to compute the aperture correction is the DAOGROW
  algorithm developed by Peter Stetson (1990).
  <P>
  In this algorithm the stellar profile is approximated by the following
  3 component model where P, G, E denote the power law, gaussian, and
  exponential analytic components of the model respectively. The subscript i
  denotes quantities that are a function of each image. 
  <P>
  <PRE>
  <P>
      I[r,X[i];RO[i],swings,pwings,pgauss,regscale,xwings] =
  	(pwings + X[i] * xwings) * P[r;swings] + (1 - pwings - X[i] *
  	xwings) * (pgauss * G[r;RO[i]] + (1 - pgauss) *
  	E[r;rgescale,RO[i]])
  <P>
      P[r;swings] = mnorm * (1 + r ** 2) ** swings
            mnorm = (swings - 1) / PI
  <P>
      G[r;RO[i]] = gnorm * exp (-0.5 * r ** 2 / RO[i] ** 2)
           gnorm = 1 / (2 * PI * RO[i] ** 2)
  <P>
      E[r;RO[i]] = hnorm  * exp (-r / (rgescale * RO[i]))
           hnorm = 1 /  (2 * PI * (rgescale * RO[i]) ** 2) 
  <P>
  </PRE>
  <P>
  This equation is actually applied to the magnitude differences between
  apertures where the observed magnitude differences are computed as follows
  for image i, star j, and aperture k.
  <P>
  <PRE>
  <P>
      mdiff[i,j,k] = m[i,j,k] - m[i,j,k-1]           k=2,..,naperts
  <P>
  </PRE>
  <P>
  <P>
  The observed differences are fit by least-squares techniques to 
  to the theoretical model differences represented by the following equation.
  <P>
  <PRE>
  <P>
  diff[i,j,k] = -2.5 * log10 (integral (2 * PI * r * I) from 0 to r[k] /
            integral (2 * PI * r * I) from 0 to r[k-1])
  <P>
  </PRE>
  <P>
  The integrals of the three model components P, G, and E are the following.
  <P>
  <PRE>
  <P>
      integral (2 * PI * r * P) = 1 - (1 + r ** 2) ** -swings
  <P>
      integral (2 * PI * r * G) = 1 - exp (-r ** 2 / (2 * RO[i] ** 2))
  <P>
      integral (2 * PI * r * H) = 1 + (1 + r / (rgescale * RO[i]) *
                            exp (-r / (rgescale * RO[i]))
  <P>
  </PRE>
  <P>
  In a given run of APFILE the seeing radius
  RO[i] is fit separately for each image, but the parameters swings, pwings,
  pgauss, rgescale, and xwings are fit to the entire data set. Therefore
  the RO[i] values define a family curves, each differing from the other
  by the seeing radius RO[i] alone. It turns out that for most data the
  fits do not depend significantly on the <I>rgescale</I> and <I>xwings</I>
  parameters.  Therefore by default <I>nparams</I> is set to 3 and
  <I>rgescale</I> and <I>xwings</I> are set to default values of 0.9 and 0.0
  respectively.
  <P>
  After the theoretical and observed growth curves are computed for
  each image, they are combined to produce an adopted growth curve. The
  weighting scheme used in the combining process is such that at small radii
  where the observed magnitude differences have the smallest errors,
  the observed values,
  are favored, and at large radii  the theoretical curve is favored. At
  all points in the computation of the theoretical curve, the observed curve,
  and the adopted curve, tests are made for deviant data points and these
  are down-weighted. The adopted curve is integrated between <I>smallap
  and fIlargeap</I> to produce the aperture correction for each image.
  <P>
  Because the error in the observed magnitudes grows rapidly toward
  larger radii, while the error in the aperture correction grows
  rapidly toward smaller radii, the combined error for the star will
  have some minimum value, usually at an intermediate aperture. If
  <I>magfile</I> is not "<TT></TT>", the magnitudes corrected to <I>largeap</I>
  using the observed magnitude and correction where the  error
  is lowest are written to <I>magfile</I>, along with the image id, x and y
  coordinates, filter ids, exposure times, airmasses, and errors in the
  magnitude. This file can be read into the OBSFILE program so as to
  create a photometry catalog suitable for input into PHOTCAL.
  <P>
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  A full description of the DAOGROW algorithm used by APFILE can be
  found in the article "<TT>On the Growth-Curve Method for Calibrating
  Stellar Photometry with CCDs</TT>" by Peter Stetson in PASP 102, 932
  (1990).
  <P>
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Prepare an aperture corrections file from a set of observations
  from 5 different data frames taken in a single night. The input
  photometry files contain the image ids in column 1, the x and y positions
  in columns 3 and 4, the airmass in column 2, and the 15 aperture radii,
  magnitudes, and magnitude errors in columns 5-19,20-34,35-49 respectively.
  <P>
  <PRE>
  	ph&gt; apfile photfiles "1,3,4,0,0,2,0,5,20,35" 15 apercor
  <P>
  	    ... plot of the cog for the first image will appear
  <P>
  	    ... type r to examine fit residuals versus radius
  <P>
  	    ... type a to examine the aperture correction curve
  		versus radius
  <P>
  	    ... type n to look at results for next image
  <P>
  	    ... type d to remove a discrepant point
  <P>
  	    ... type f to refit the cog
  <P>
  	    ... type r to examine the residuals for this image
  <P>
  	    ... type p to recheck the residuals for the first image
  <P>
  	    ... step through the remaining image deleting points and
  		refitting as necessary
  <P>
  	    ... type q to quit
  <P>
  	    ... the compute aperture corrections will appear in apercor
  </PRE>
  <P>
  2. Repeat the previous example in non-interactive mode saving all the
  details and plots of the fit in the log and plot file respectively.
  <P>
  <PRE>
  	ph&gt; apfile photfiles "1,3,4,0,0,2,0,5,20,35" 15 apercor \<BR>
  	    inter- logfile=apercor.log plotfile=apercor.plot
  <P>
  	ph&gt; page apercor.log
  <P>
  	    ... page through the log file
  <P>
  	ph&gt; gkiextract apercor.plot "1-25" | stdplot
  <P>
  	    ... send all the plots of the fit to the default plotter
  </PRE>
  <P>
  3. Compute the magnitudes corrected to largeap, of all the standard
  stars observed in a night using the observed magnitude and computed magnitude
  correction at the aperture radius with the lowest error. Assume that the
  format of the input photometry files is the same as in the two previous
  examples and the filter ids (U,B,V), exposure times, and airmasses were
  all present and correct in the photometry files.
  <P>
  <PRE>
  	ph&gt; apfile stdfiles "1,3,4,0,0,2,0,5,20,35" 15 apercor inter-\<BR>
  	    magfile="stdfiles.ap" logfile=apercor.log\<BR>
  	    plotfile=apercor.plot
  <P>
  	ph&gt; obsfile stdfiles.ap "1,2,3,4,5,6,7,8,9" "U,B,V" imsets stdobs 
  <P>
  	    ... create a standard star observations file suitable for
  		input to the photcal package
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkapfile, mknobsfile,mkobsfile,obsfile
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'ALGORITHMS' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>