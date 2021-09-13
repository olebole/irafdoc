.. _identify:

identify — Identify arc lines and determine a dispersion function
=================================================================

**Package: kpnocoude**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  identify -- Identify features in one dimensional image vectors
  </UL>
  <! EndSection:   'NAME'>
  <H3>Summary</H3>
  <! BeginSection: 'SUMMARY'>
  <UL>
  Features are interactively marked in one dimensional image vectors.
  The features may be spectral lines when the vector is a spectrum
  or profile positions when the vector is a spatial cut.  A function
  may be fit to the user coordinates as a function of pixel coordinates.
  This is primarily used to find dispersion functions for spectra
  such as arc-line calibration spectra.  The profile position measurements
  are generally used for geometric calibrations.
  </UL>
  <! EndSection:   'SUMMARY'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  identify images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images in which to identify features and fit coordinate functions.
  </DD>
  </DL>
  <DL>
  <DT><B>section = "<TT>middle line</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='section' Line='section = "middle line"'>
  <DD>If an image is not one dimensional or specified as a one dimensional image
  section then the image section given by this parameter is used.  The
  section defines a one dimensional vector.  The image is still considered to
  be two or three dimensional.  It is possible to change the data vector
  within the program.
  <P>
  The section parameter may be specified directly as an image section or
  in one of the following forms
  <P>
  <PRE>
  line|column|x|y|z first|middle|last|# [first|middle|last|#]]
  first|middle|last|# [first|middle|last|#] line|column|x|y|z
  </PRE>
  <P>
  where each field can be one of the strings separated by | except for #
  which is an integer number.  The field in [] is a second designator
  which is used with three dimensional data.  See the example section for
  examples of this syntax.  Abbreviations are allowed though beware that <TT>'l'</TT>
  is not a sufficient abbreviation.
  </DD>
  </DL>
  <DL>
  <DT><B>database = "<TT>database</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "database"'>
  <DD>Database in which the feature data and coordinate functions are recorded.
  </DD>
  </DL>
  <DL>
  <DT><B>coordlist = "<TT>linelists$idhenear.dat</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coordlist' Line='coordlist = "linelists$idhenear.dat"'>
  <DD>User coordinate list consisting of an list of line coordinates.  A
  comment line of the form "<TT># units &lt;units&gt;</TT>", where &lt;units&gt; is one of the
  understood units names, defines the units of the line list.  If no units
  are specified then Angstroms are assumed.  Some standard line lists are
  available in the directory "<TT>linelists$</TT>".  The standard line lists are
  described under the topic <I>linelists</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>units = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='units' Line='units = ""'>
  <DD>The units to use if no database entry exists.  The units are specified as
  described in
  <P>
  <PRE>
      cl&gt; help onedspec.package section=units
  </PRE>
  <P>
  If no units are specified and a coordinate list is used then the units of
  the coordinate list are selected.  If a database entry exists then the
  units defined there override both this parameter and the coordinate list.
  </DD>
  </DL>
  <DL>
  <DT><B>nsum = "<TT>10</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsum' Line='nsum = "10"'>
  <DD>Number of lines, columns, or bands across the designated vector axis to be
  summed when the image is a two or three dimensional spatial spectrum.
  It does not apply to multispec format spectra.  If the image is three
  dimensional an optional second number can be specified for the higher
  dimensional axis  (the first number applies to the lower axis number and
  the second to the higher axis number).  If a second number is not specified
  the first number is used for both axes.
  </DD>
  </DL>
  <DL>
  <DT><B>match = -3.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='match' Line='match = -3.'>
  <DD>The maximum difference for a match between the feature coordinate function
  value and a coordinate in the coordinate list.  Positive values
  are in user coordinate units and negative values are in units of pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>maxfeatures = 50</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxfeatures' Line='maxfeatures = 50'>
  <DD>Maximum number of the strongest features to be selected automatically from
  the coordinate list (function <TT>'l'</TT>) or from the image data (function <TT>'y'</TT>).
  </DD>
  </DL>
  <DL>
  <DT><B>zwidth = 100.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zwidth' Line='zwidth = 100.'>
  <DD>Width of graphs, in user coordinates, when in zoom mode (function <TT>'z'</TT>).
  </DD>
  </DL>
  <P>
  The following parameters are used in determining feature positions.
  <DL>
  <DT><B>ftype = "<TT>emission</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ftype' Line='ftype = "emission"'>
  <DD>Type of features to be identified.  The possibly abbreviated choices are
  "<TT>emission</TT>" and "<TT>absorption</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>fwidth = 4.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fwidth' Line='fwidth = 4.'>
  <DD>Full-width at the base (in pixels) of features to be identified.
  </DD>
  </DL>
  <DL>
  <DT><B>cradius = 5.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cradius' Line='cradius = 5.'>
  <DD>The maximum distance, in pixels, allowed between a feature position
  and the initial estimate when defining a new feature.
  </DD>
  </DL>
  <DL>
  <DT><B>threshold = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 0.'>
  <DD>In order for a feature center to be determined the range of pixel intensities
  around the feature must exceed this threshold.
  </DD>
  </DL>
  <DL>
  <DT><B>minsep = 2.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minsep' Line='minsep = 2.'>
  <DD>The minimum separation, in pixels, allowed between feature positions
  when defining a new feature.
  </DD>
  </DL>
  <P>
  The following parameters are used to fit a function to the user coordinates.
  The <B>icfit</B> package is used and further descriptions about these parameters
  may be found under that package.
  <DL>
  <DT><B>function = "<TT>spline3</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "spline3"'>
  <DD>The function to be fit to the user coordinates as a function of the pixel
  coordinate.  The choices are "<TT>chebyshev</TT>", "<TT>legendre</TT>", "<TT>spline1</TT>", or "<TT>spline3</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>order = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>Order of the fitting function.  The order is the number of polynomial terms
  or number of spline pieces.
  </DD>
  </DL>
  <DL>
  <DT><B>sample = "<TT>*</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Sample regions for fitting. This is in pixel coordinates and not the user
  coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>niterate = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 0'>
  <DD>Number of rejection iterations.
  </DD>
  </DL>
  <DL>
  <DT><B>low_reject = 3.0, high_reject = 3.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 3.0, high_reject = 3.0'>
  <DD>Lower and upper residual rejection in terms of the RMS of the fit.
  </DD>
  </DL>
  <DL>
  <DT><B>grow = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0'>
  <DD>Distance from a rejected point in which additional points are automatically
  rejected regardless of their residuals.
  </DD>
  </DL>
  <P>
  The following parameters control the input and output.
  <DL>
  <DT><B>autowrite = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='autowrite' Line='autowrite = no'>
  <DD>Automatically write or update the database?  If "<TT>no</TT>" then when exiting the
  program a query is given if the feature data and fit have been modified.
  The query is answered with "<TT>yes</TT>" or "<TT>no</TT>" to save or not save the results.
  If <I>autowrite</I> is "<TT>yes</TT>" exiting the program automatically updates the
  database.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics device.  The default is the standard graphics device which is
  generally a graphics terminal.
  </DD>
  </DL>
  <DL>
  <DT><B>cursor = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Cursor input file.  If a cursor file is not given then the standard graphics
  cursor is read.
  </DD>
  </DL>
  <P>
  The following parameters are queried when the <TT>'b'</TT> key is used.
  <DL>
  <DT><B>crval, cdelt</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='crval' Line='crval, cdelt'>
  <DD>These parameters specify an approximate coordinate value and coordinate
  interval per pixel when the automatic line identification
  algorithm (<TT>'b'</TT> key) is used.  The coordinate value is for the
  pixel specified by the <I>crpix</I> parameter in the <B>aidpars</B>
  parameter set.  The default value of <I>crpix</I> is INDEF which then
  refers the coordinate value to the middle of the spectrum.  By default
  only the magnitude of the coordinate interval is used.  Either value
  may be given as INDEF.  In this case the search for a solution will
  be slower and more likely to fail.  The values may also be given as
  keywords in the image header whose values are to be used.
  </DD>
  </DL>
  <DL>
  <DT><B>aidpars = "<TT></TT>" (parameter set)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aidpars' Line='aidpars = "" (parameter set)'>
  <DD>This parameter points to a parameter set for the automatic line
  identification algorithm.  See <I>aidpars</I> for further information.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Cursor keys</H3>
  <! BeginSection: 'CURSOR KEYS'>
  <UL>
  <DL>
  <DT><B>?</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line='?'>
  <DD>Clear the screen and print a menu of options.
  </DD>
  </DL>
  <DL>
  <DT><B>a</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='a' Line='a'>
  <DD>Apply next (c)enter or (d)elete operation to (a)ll features
  </DD>
  </DL>
  <DL>
  <DT><B>b</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='b' Line='b'>
  <DD>Identify features and find a dispersion function automatically using
  the coordinate line list and approximate values for the dispersion.
  </DD>
  </DL>
  <DL>
  <DT><B>c</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='c' Line='c'>
  <DD>(C)enter the feature nearest the cursor.  Used when changing the position
  finding parameters or when features are defined from a previous feature list.
  </DD>
  </DL>
  <DL>
  <DT><B>d</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='d' Line='d'>
  <DD>(D)elete the feature nearest the cursor.  (D)elete all features when preceded
  by the (a)ll key.  This does not affect the dispersion function.
  </DD>
  </DL>
  <DL>
  <DT><B>e</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='e' Line='e'>
  <DD>Find features from a coordinate list without doing any fitting.  This is
  like the <TT>'l'</TT> key without any fitting.
  </DD>
  </DL>
  <DL>
  <DT><B>f</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='f' Line='f'>
  <DD>(F)it a function of the pixel coordinates to the user coordinates.  This enters
  the interactive function fitting package.
  </DD>
  </DL>
  <DL>
  <DT><B>g</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='g' Line='g'>
  <DD>Fit a zero point shift to the user coordinates by minimizing the difference
  between the user and fitted coordinates.  The coordinate function is
  not changed.
  </DD>
  </DL>
  <DL>
  <DT><B>i</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='i' Line='i'>
  <DD>(I)nitialize (delete features and coordinate fit).
  </DD>
  </DL>
  <DL>
  <DT><B>j</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='j' Line='j'>
  <DD>Go to the preceding line, column, or band in a 2D/3D or multispec image.
  </DD>
  </DL>
  <DL>
  <DT><B>k</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='k' Line='k'>
  <DD>Go to the next line, column, or band in a 2D/3D or multispec image.
  </DD>
  </DL>
  <DL>
  <DT><B>l</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='l' Line='l'>
  <DD>(L)ocate features in the coordinate list.  A coordinate function must be
  defined or at least two features must have user coordinates from which a
  coordinate function can be determined.  If there are features an
  initial fit is done, then features are added from the coordinate list,
  and then a final fit is done.
  </DD>
  </DL>
  <DL>
  <DT><B>m</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='m' Line='m'>
  <DD>(M)ark a new feature using the cursor position as the initial position
  estimate.
  </DD>
  </DL>
  <DL>
  <DT><B>n</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='n' Line='n'>
  <DD>Move the cursor or zoom window to the (n)ext feature (same as +).
  </DD>
  </DL>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='o' Line='o'>
  <DD>Go to the specified line, column, or band in a 2D/3D or multispec image.
  For 3D images two numbers are specified.
  </DD>
  </DL>
  <DL>
  <DT><B>p</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='p' Line='p'>
  <DD>(P)an to the original window after (z)ooming on a feature.
  </DD>
  </DL>
  <DL>
  <DT><B>q</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='q' Line='q'>
  <DD>(Q)uit and continue with next image.
  </DD>
  </DL>
  <DL>
  <DT><B>r</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='r' Line='r'>
  <DD>(R)edraw the graph.
  </DD>
  </DL>
  <DL>
  <DT><B>s</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='s' Line='s'>
  <DD>(S)hift the fit coordinates relative to the pixel coordinates.  The
  user specifies the desired fit coordinate at the position of the cursor
  and a zero point shift to the fit coordinates is applied.  If features
  are defined then they are recentered and the shift is the average shift.
  The shift in pixels, user coordinates, and z (fractional shift) is printed.
  </DD>
  </DL>
  <DL>
  <DT><B>t</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='t' Line='t'>
  <DD>Reset the current feature to the position of the cursor.  The feature
  is <I>not</I> recentered.  This is used to mark an arbitrary position.
  </DD>
  </DL>
  <DL>
  <DT><B>u</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='u' Line='u'>
  <DD>Enter a new (u)ser coordinate for the current feature.
  When (m)arking a new feature the user coordinate is also requested.
  </DD>
  </DL>
  <DL>
  <DT><B>v</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='v' Line='v'>
  <DD>Modify the fitting weight of the current feature.  The weights are
  integers with the lowest weight being the default of 1.
  </DD>
  </DL>
  <DL>
  <DT><B>w</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='w' Line='w'>
  <DD>(W)indow the graph.  A window prompt is given and a number of windowing
  options may be given.  For more help type <TT>'?'</TT> to the window prompt or
  see help under <I>gtools</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>x</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='x' Line='x'>
  <DD>Find a zero point shift for the current dispersion function.  This is used
  by starting with the dispersion solution and features from a different
  spectrum.  The mean shift in user coordinates, mean shift in pixels, and
  the fractional shift in user coordinates is printed.
  </DD>
  </DL>
  <DL>
  <DT><B>y</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='y' Line='y'>
  <DD>Up to <I>maxfeatures</I> emission peaks are found automatically (in order of
  peak intensity) and, if a dispersion solution is defined, the peaks are
  identified from the coordinate list.
  </DD>
  </DL>
  <DL>
  <DT><B>z</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='z' Line='z'>
  <DD>(Z)oom on the feature nearest the cursor.  The width of the zoom window
  is determined by the parameter <I>zwidth</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>.</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line='.'>
  <DD>Move the cursor or zoom window to the feature nearest the cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>+</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line='+'>
  <DD>Move the cursor or zoom window to the (n)ext feature.
  </DD>
  </DL>
  <DL>
  <DT><B>-</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line='-'>
  <DD>Move the cursor or zoom window to the previous feature.
  </DD>
  </DL>
  <P>
  Parameters are shown or set with the following "<TT>colon commands</TT>", which may be
  abbreviated.  To show the value of a parameter type the parameter name alone
  and to set a new value follow the parameter name by the value.
  <DL>
  <DT><B>:show file</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':show file'>
  <DD>Show the values of all the parameters.  If a file name is given then the
  output is appended to that file.  If no file is given then the terminal
  is cleared and the output is sent to the terminal.
  </DD>
  </DL>
  <DL>
  <DT><B>:features file</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':features file'>
  <DD>Print the feature list and the fit rms.  If a file name is given then the
  output is appended to that file.  If no file is given then the terminal
  is cleared and the output is sent to the terminal.
  </DD>
  </DL>
  <DL>
  <DT><B>:coordlist file</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':coordlist file'>
  <DD>Set or show the coordinate list file.
  </DD>
  </DL>
  <DL>
  <DT><B>:cradius value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':cradius value'>
  <DD>Set or show the centering radius in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>:threshold value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':threshold value'>
  <DD>Set or show the detection threshold for centering.
  </DD>
  </DL>
  <DL>
  <DT><B>:database name</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':database name'>
  <DD>Set or show the database for recording feature records.
  </DD>
  </DL>
  <DL>
  <DT><B>:ftype value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':ftype value'>
  <DD>Set or show the feature type (emission or absorption).
  </DD>
  </DL>
  <DL>
  <DT><B>:fwidth value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':fwidth value'>
  <DD>Set or show the feature width in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>:image imagename</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':image imagename'>
  <DD>Set a new image or show the current image.
  </DD>
  </DL>
  <DL>
  <DT><B>:labels value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':labels value'>
  <DD>Set or show the feature label type (none, index, pixel, coord, user, or both).
  None produces no labeling, index labels the features sequentially in order
  of pixel position, pixel labels the features by their pixel coordinates,
  coord labels the features by their user coordinates (such as wavelength),
  user labels the features by the user or line list supplied string, and
  both labels the features by both the user coordinates and user strings.
  </DD>
  </DL>
  <DL>
  <DT><B>:match value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':match value'>
  <DD>Set or show the coordinate list matching distance.
  </DD>
  </DL>
  <DL>
  <DT><B>:maxfeatures value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':maxfeatures value'>
  <DD>Set or show the maximum number of features automatically found.
  </DD>
  </DL>
  <DL>
  <DT><B>:minsep value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':minsep value'>
  <DD>Set or show the minimum separation allowed between features.
  </DD>
  </DL>
  <DL>
  <DT><B>:read name ap</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':read name ap'>
  <DD>Read a record from the database.  The record name defaults to the image name
  and, for 1D spectra, the aperture number defaults to aperture of
  the current image.
  </DD>
  </DL>
  <DL>
  <DT><B>:write name ap</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':write name ap'>
  <DD>Write a record to the database.  The record name defaults to the image name
  and, for 1D spectra, the aperture number defaults to aperture of
  the current image.
  </DD>
  </DL>
  <DL>
  <DT><B>:add name ap</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':add name ap'>
  <DD>Add features from a database record.  The record name defaults to the image name
  and, for 1D spectra, the aperture number defaults to aperture of
  the current image.  Only the features are added to any existing list
  of features.  The dispersion function is not read.
  </DD>
  </DL>
  <DL>
  <DT><B>:zwidth value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':zwidth value'>
  <DD>Set or show the zoom width in user units.
  </DD>
  </DL>
  <DL>
  <DT><B>:/help</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':/help'>
  <DD>Print additional help for formatting graphs.  See help under "<TT>gtools</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'CURSOR KEYS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Features in the input images are identified interactively and assigned
  user coordinates.  A "<TT>coordinate function</TT>" mapping pixel coordinates to
  user coordinates may be determined from the identified features.  A
  user coordinate list may be defined to automatically identify additional
  features.  This task is used to measure positions of features,
  determine dispersion solutions for spectra, and to identify features in
  two and three dimensional images for mapping a two or three dimensional
  coordinate transformation.  Because of this dual use the terms vector
  and feature are used rather than spectrum and spectral line.
  <P>
  Each image in the input list is considered in turn.  If the image is
  not one dimensional or a one dimensional section of an image
  then the image section given by the parameter
  <I>section</I> is used.  This parameter may be specified in several ways as
  described in the PARAMETERS and EXAMPLES sections.  The image section is used
  to select a starting vector and image axis.
  <P>
  If the image is not one dimensional or in multispec format then the number
  of lines, columns, or bands given by the parameter <I>nsum</I> are summed.
  The one dimensional image vector is graphed.  The initial feature list and
  coordinate function are read from the database if an entry exists.  The
  features are marked on the graph.  The image coordinates are in pixels
  unless a coordinate function is defined, in which case they are in user
  coordinate units.  The pixel coordinate, coordinate function value, and
  user coordinate for the current feature are printed.
  <P>
  The graphics cursor is used to select features and perform various
  functions.  A menu of the keystroke options and functions is printed
  with the key <TT>'?'</TT>.  The cursor keys and their functions are defined in
  the CURSOR KEYS section and described further below.  The standard
  cursor mode keys are also available to window and redraw the graph and
  to produce hardcopy "<TT>snaps</TT>".
  <P>
  There are a number of ways of defining features.  They fall into
  two categories; interactively defining features with the cursor
  and using automatic algorithms.
  <P>
  The <TT>'m'</TT> key is the principle interactive feature marking method.  Typing
  <TT>'m'</TT> near the position of a feature applies a feature centering algorithm
  (see <B>center1d</B>) and, if a center is found, the feature is entered in
  the feature list and marked on the spectrum.  If the new position is within
  a distance given by the parameter <I>minsep</I> of a previous feature it is
  considered to be the same feature and replaces the old feature.  Normally
  the position of a new feature will be exactly the same as the original
  feature.  The coordinate list is searched for a match between the
  coordinate function value (when defined) and a user coordinate in the
  list.  If a match is found it becomes the default user coordinate which the
  user may override.  The new feature is marked on the graph and it becomes
  the current feature.  The redefinition of a feature which is within the
  minimum separation may be used to set the user coordinate from the
  coordinate list.  The <TT>'t'</TT> key allows setting the position of a feature to
  other than that found by the centering algorithm.
  <P>
  The principle automatic feature identification algorithm is executed
  with the <TT>'b'</TT> key.  The user is queried for an approximate coordinate
  value and coordinate interval per pixel.  The coordinate value
  is for the center of the spectrum by default though this may be changed
  with the <B>aidpars</B> parameters.  Only the magnitude of the
  coordinate interval per pixel is used by default though this also
  may be changed.  Either value may be given as INDEF to do an unconstrained
  search, however, this will be much slower and more likely to fail.
  The algorithm searches for matches between the strong lines in the
  spectrum and lines in the coordinate list.  The algorithm is described
  in the documentation for <B>aidpars</B>.
  <P>
  The <TT>'b'</TT> key works with no predefined dispersion solution or features.  If
  two or more features are identified, with <TT>'m'</TT>, spanning the range of the
  data or if a coordinate function is defined, from a previous solution, then
  the <TT>'e'</TT>, <TT>'l'</TT>, and <TT>'y'</TT> keys may be used to identify additional features from
  a coordinate list.  The <TT>'e'</TT> key only adds features at the coordinates of
  the line lists if the centering algorithm finds a feature at that
  wavelength (as described below).  The <TT>'y'</TT> key works in reverse by finding
  the prominent features using a peak finding algorithm and then looking in
  the coordinate list for entries near the estimated position.  Up to a
  maximum number of features (<I>maxfeatures</I>) will be selected.  If there
  are more peaks only the strongest are kept.  In either of these cases there
  is no automatic fitting and refitting of the dispersion function.
  <P>
  The <TT>'l'</TT> key combines automatic fits with locating lines from the coordinate
  list.  If two or more features are defined an initial fit is made.  Then
  for each coordinate value in the coordinate list the pixel coordinate is
  determined and a search for a feature at that point is made.  If a feature
  is found (based on the parameters <I>ftype, fwidth</I>, <I>cradius</I>, and
  <B>threshold</B>) its user coordinate value based on the coordinate function
  is determined.  If the coordinate function value matches the user
  coordinate from the coordinate list within the error limit set by the
  parameter <I>match</I> then the new feature is entered in the feature list.
  Up to a maximum number of features, set by the parameter <I>maxfeatures</I>,
  may be defined in this way.  A new user coordinate function is fit to all
  the located features.  Finally, the graph is redrawn in user coordinates
  with the additional features found from the coordinate list marked.
  <P>
  A minimum of two features must be defined for the <TT>'l'</TT> key algorithm to
  work.  However, three or more features are preferable to determine changes
  in the dispersion as a function of position.
  <P>
  The <TT>'f'</TT> key fits a function of the pixel coordinates to the user
  coordinates.  The type of function, order and other fitting parameters
  are initially set with the parameters <I>function, order, sample,
  niterate, low_reject, high_reject</I> and <I>grow</I>..  The value of the
  function for a particular pixel coordinate is called the function
  coordinate and each feature in the feature list has a function
  coordinate value.  The fitted function also is used to convert pixel
  coordinates to user coordinates in the graph.  The fitting is done
  within the interactive curve fitting package which has its own set of
  interactive commands.  For further information on this package see the
  help material under <B>icfit</B>.
  <P>
  If a zero point shift is desired without changing the coordinate function
  the user may specify the coordinate of a point in the spectrum with
  the <TT>'s'</TT> key from which a shift is determined.  The <TT>'g'</TT> key also
  determines a shift by minimizing the difference between the user
  coordinates and the fitted coordinates.  This is used when a previously
  determined coordinate function is applied to a new spectrum having
  fewer or poorer lines and only a zero point shift can reasonably be
  determined.  Note that the zero point shift is in user coordinates.
  This is only an approximate correction for shifts in the raw spectra
  since these shifts are in pixels and the coordinate function should
  also be appropriately shifted.
  <P>
  One a set of features is defined one may select features for various
  operations.  To select feature as the current feature the keys <TT>'.'</TT>, <TT>'n'</TT>,
  <TT>'+'</TT>, and <TT>'-'</TT> are used.  The <TT>'.'</TT> selects the feature nearest the cursor, the
  <TT>'n'</TT> and <TT>'+'</TT> select the next feature, and the <TT>'-'</TT> selects the previous
  feature relative to the current feature in the feature list as ordered by
  pixel coordinate.  These keys are useful when redefining the user
  coordinate with the <TT>'u'</TT> key, changing the fitting weight of a feature with
  <TT>'v'</TT>, and when examining features in zoom mode.
  <P>
  Features may be deleted with the key <TT>'d'</TT>.  All features are deleted
  when the <TT>'a'</TT> key immediately precedes the delete key.  Deleting the
  features does not delete the coordinate function.  Features deleted in the
  curve fitting package also are removed from the feature list upon
  exiting the curve fitting package.
  <P>
  It is common to transfer the feature identifications and coordinate function
  from one image to another.  When a new image without a database entry
  is examined, such as when going to the next image in the input list,
  changing image lines or columns with <TT>'j'</TT>, <TT>'k'</TT> and <TT>'o'</TT>, or selecting
  a new image with the "<TT>:image</TT>" command, the current feature list and coordinate
  function are kept.  Alternatively, a database record from a different
  image may be read with the "<TT>:read</TT>" command.  When transferring feature
  identifications between images the feature coordinates will not agree exactly
  with the new image feature positions and several options are available to
  reregister the feature positions.  The key <TT>'c'</TT> centers the feature nearest
  the cursor using the current position as the starting point.  When preceded
  with the <TT>'a'</TT> key all the features are recentered (the user must refit
  the coordinate function if desired).  As an aside, the recentering
  function is also useful when the parameters governing the feature
  centering algorithm are changed.  An additional options is the "<TT>:add</TT>"
  command to add features from a database record.  This does not overwrite
  previous features (or the fitting functions) as does "<TT>:read</TT>".
  <P>
  The (c)entering function is applicable when the shift between the current
  and true feature positions is small.  Larger shifts may be determined
  automatically with the <TT>'s'</TT> or <TT>'x'</TT> keys.
  <P>
  A zero point shift is specified interactively with the <TT>'s'</TT> key by using the
  cursor to indicate the coordinate of a point in the spectrum.  If there are
  no features then the shift is exactly as marked by the cursor.  If there
  are features the specified shift is applied, the features are recentered,
  and the mean shift for all the features is determined.
  <P>
  The <TT>'x'</TT> key uses the automatic line identification algorithm (see
  <B>aidpars</B>) with the constraint that the dispersion is nearly the
  same and the is primarily a shift in the coordinate zero point.  If
  features are defined, normally by inheritance from another spectrum, then a
  first pass is done to identify those features in the spectrum.  Since this
  only works when the shifts are significantly less than the dispersion range
  of the spectrum (i.e. a significant number of features are in common) a
  second pass using the full coordinate line list is performed if a shift
  based on the features is not found.  After a shift is found any features
  remaining from the original list are recentered and a mean shift is
  computed.
  <P>
  In addition to the single keystroke commands there are commands initiated
  by the key <TT>':'</TT> (colon commands).  As with the keystroke commands there are
  a number of standard graphics features available beginning with "<TT>:.</TT>"
  (type "<TT>:.help</TT>" for these commands).  The identify colon commands
  allow the task parameter values to be listed and to be reset
  within the task.  A parameter is listed by typing its name.  The colon command
  "<TT>:show</TT>" lists all the parameters.  A parameter value is reset by
  typing the parameter name followed by the new value; for example
  "<TT>:match 10</TT>".  Other colon commands display the feature list (:features),
  control reading and writing records to the database (:read and :write),
  and set the graph display format.
  <P>
  The feature identification process for an image is completed by typing
  <TT>'q'</TT> to quit.  Attempting to quit an image without explicitly
  recording changes in the feature database produces a warning message
  unless the <I>autowrite</I> parameter is set.  If this parameter is
  not set a prompt is given asking whether to save the results otherwise
  the results are automatically saved.  Also
  the reference spectrum keyword REFSPEC is added to the image header at
  this time.  This is used by <B>refspectra</B> and <B>dispcor</B>.
  As an immediate exit the <TT>'I'</TT> interrupt key may be used.  This does not save
  the feature information and may leave the graphics in a confused state.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Database records</H3>
  <! BeginSection: 'DATABASE RECORDS'>
  <UL>
  The database specified by the parameter <I>database</I> is a directory of
  simple text files.  The text files have names beginning with 'id' followed
  by the entry name, usually the name of the image.  The database text files
  consist of a number of records.  A record begins with a line starting with the
  keyword "<TT>begin</TT>".  The rest of the line is the record identifier.  Records
  read and written by <B>identify</B> have "<TT>identify</TT>" as the first word of the
  identifier.  Following this is a name which may be specified following the
  "<TT>:read</TT>" or "<TT>:write</TT>" commands.  If no name is specified then the image name
  is used.  For 1D spectra the database entry includes the aperture number
  and so to read a solution from a aperture different than the current image
  and aperture number must be specified.  For 2D/3D images the entry name
  has the 1D image section which is what is specified to read the entry.
  The lines following the record identifier contain
  the feature information and dispersion function coefficients.
  <P>
  The dispersion function is saved in the database as a series of
  coefficients.  The section containing the coefficients starts with the
  keyword "<TT>coefficients</TT>" and the number of coefficients.
  <P>
  The first four coefficients define the type of function, the order
  or number of spline pieces, and the range of the independent variable
  (the line or column coordinate along the dispersion).  The first
  coefficient is the function type code with values:
  <P>
  <PRE>
  	Code	Type
  	   1	Chebyshev polynomial
  	   2	Legendre polynomial
  	   3	Cubic spline
  	   4	Linear spline
  </PRE>
  <P>
  The second coefficient is the order (actually the number of terms) of
  the polynomial or the number of pieces in the spline.
  <P>
  The next two coefficients are the range of the independent variable over
  which the function is defined.  These values are used to normalize the
  input variable to the range -1 to 1 in the polynomial functions.  If the
  independent variable is x and the normalized variable is n, then
  <P>
  <PRE>
  	n = (2 * x - (xmax + xmin)) / (xmax - xmin)
  </PRE>
  <P>
  where xmin and xmax are the two coefficients.
  <P>
  The spline functions divide the range into the specified number of
  pieces.  A spline coordinate s and the nearest integer below s,
  denoted as j, are defined by
  <P>
  <PRE>
  	s = (x - xmin) / (xmax - xmin) * npieces
  	j = integer part of s
  </PRE>
  <P>
  where npieces are the number of pieces.
  <P>
  The remaining coefficients are those for the appropriate function.
  The number of coefficients is either the same as the function order
  for the polynomials, npieces+1 for the linear spline, or npieces + 3
  for the cubic spline.
  <P>
  1. Chebyshev Polynomial
  <P>
  The polynomial can be expressed as the sum
  <P>
  <PRE>
  	y = sum from i=1 to order {c_i * z_i}
  </PRE>
  <P>
  where the c_i are the coefficients and the z_i are defined
  interactively as:
  <P>
  <PRE>
  	z_1 = 1
  	z_2 = n
  	z_i = 2 * n * z_{i-1} - z_{i-2}
  </PRE>
  <P>
  2. Legendre Polynomial
  <P>
  The polynomial can be expressed as the sum
  <P>
  <PRE>
  	y = sum from i=1 to order {c_i * z_i}
  </PRE>
  <P>
  where the c_i are the coefficients and the z_i are defined
  interactively as:
  <P>
  <PRE>
  	z_1 = 1
  	z_2 = n
  	z_i = ((2*i-3) * n * z_{i-1} - (i-2) * z_{i-2}) / (i-1)
  </PRE>
  <P>
  3. Linear Spline
  <P>
  The linear spline is evaluated as
  <P>
  <PRE>
  	y = c_j * a + c_{j+1} * b
  </PRE>
  <P>
  where j is as defined earlier and a and b are fractional difference
  between s and the nearest integers above and below
  <P>
  <PRE>
  	a = (j + 1) - s
  	b = s - j
  </PRE>
  <P>
  4.  Cubic Spline
  <P>
  The cubic spline is evaluated as
  <P>
  <PRE>
  	y = sum from i=0 to 3 {c_{i+j} * z_i}
  </PRE>
  <P>
  where j is as defined earlier.  The term z_i are computed from
  a and b, as defined earlier, as follows
  <P>
  <PRE>
  	z_0 = a**3
  	z_1 = 1 + 3 * a * (1 + a * b)
  	z_2 = 1 + 3 * b * (1 + a * b)
  	z_3 = b**3
  </PRE>
  </UL>
  <! EndSection:   'DATABASE RECORDS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Because this task is interactive and has many possible applications
  it is difficult to provide actual examples.  Instead some uses of the task
  are described.
  <P>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='o' Line='o'>
  <DD>For defining distortions in the slit dimension as a function of
  wavelength the positions of objects are marked at some wavelength.
  The task <B>reidentify</B> is then used to trace the features to other
  wavelengths.
  </DD>
  </DL>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='o' Line='o'>
  <DD>For determining dispersion solutions in a one dimensional
  spectrum an arc calibration is used.  Three emission features are marked
  and the (l)ocate key is used to find additional features from a
  coordinate list of arc lines.  The dispersion solution is fit interactively
  and badly determined or misidentified lines are deleted.  The
  solution may be written to the database or transferred to the object
  spectrum by reading the object image and deleting all the features.
  Deleting the features does not delete the coordinate function.
  </DD>
  </DL>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='o' Line='o'>
  <DD>For determining a two or three dimensional coordinate transformation a
  dispersion solution is determined at one slit position in a long slit arc
  spectrum or one spatial position in a Fabry-Perot spectrum as in the
  previous example.  The features are then traced to other positions with the
  task <B>reidentify</B>.
  </DD>
  </DL>
  <P>
  2.  For images which are two or three dimensional it is necessary to
  specify the image axis for the data vector and the number of pixels at each
  point across the vector direction to sum.  One way specify a vector is to
  use an image section to define a vector.  For example, to select column
  20:
  <P>
  <PRE>
      cl&gt; identify obj[20,*]
  </PRE>
  <P>
  The alternative is to use the section parameter.  Below are some examples
  of the section parameter syntax for an image "<TT>im2d</TT>" which is 100x200
  and "<TT>im3d</TT>" which is 100x200x50.  On the left is the section string syntax
  and on the right is the image section
  <P>
  <PRE>
      Section parameter |  Image section      |  Description
      ------------------|---------------------|---------------------
      first line        |  im2d[*,1]          |  First image line
      middle column     |  im2d[50,*]         |  Middle image column
      last z            |  im3d[100,200,*]    |  Last image z vector
      middle last y     |  im3d[50,*,50]      |  Image y vector
      line 20           |  im2d[*,20]         |  Line 20
      column 20         |  im2d[20,*]         |  Column 20
      x 20              |  im2d[*,20]         |  Line 20
      y 20              |  im2d[20,*]         |  Column 20
      y 20 30           |  im2d[20,*,30]      |  Column 20
      z 20 30	      |  im3d[20,30,*]      |  Image z vector
      x middle          |  im3d[*,100,25]     |  Middle of image
      y middle          |  im3d[50,*,25]      |  Middle of image
      z middle          |  im3d[50,100,*]     |  Middle of image
  </PRE>
  <P>
  The most common usage should be "<TT>middle line</TT>", "<TT>middle column</TT>" or "<TT>middle z</TT>".
  <P>
  The summing factors apply to the axes across the specified vector.  For
  3D images there may be one or two values.  The following shows which axes
  are summed, the second and third columns, when the vector axis is that shown
  in the first column.
  <P>
  <PRE>
      Vector axis       |   Sum axis in 2D    |  Sum axes in 3D
      ------------------|---------------------|--------------------
           1            |         2           |      2 3                 
           2            |         1           |      1 3                 
           3            |         -           |      1 2                 
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>IDENTIFY V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IDENTIFY' Line='IDENTIFY V2.11'>
  <DD>The dispersion units are now determined from a user parameter,
  the coordinate list, or the database entry.
  <P>
  A new key, <TT>'e'</TT>, has been added to add features from a line list without
  doing any fits.  This is like the <TT>'l'</TT> but without the automatic
  fitting before and after adding new features.
  <P>
  A new key, <TT>'b'</TT>, has been added to apply an automatic line identification
  algorithm.
  <P>
  The <TT>'x'</TT> key has been changed to use the automatic line identification
  algorithm.  The allows finding much larger shifts.
  <P>
  The match parameter may now be specified either in user coordinates or
  in pixels.  The default is now 3 pixels.
  <P>
  The default threshold value has been changed to 0.
  </DD>
  </DL>
  <DL>
  <DT><B>IDENTIFY V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IDENTIFY' Line='IDENTIFY V2.10.3'>
  <DD>The section and nsum parameter syntax was extended to apply to 3D
  images.  The previous values and defaults may still be used.
  <P>
  The <TT>'v'</TT> key was added to allow assigning weights to features.
  </DD>
  </DL>
  <DL>
  <DT><B>IDENTIFY V2.10</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IDENTIFY' Line='IDENTIFY V2.10'>
  <DD>The principle revision is to allow multiple aperture images and long slit
  spectra to be treated as a unit.  New keystrokes allow jumping or scrolling
  within multiple spectra in a single image.  For aperture spectra the
  database entries are referenced by image name and aperture number and not
  with image sections.  Thus, IDENTIFY solutions are not tied to specific
  image lines in this case.  There is a new autowrite parameter which may
  be set to eliminate the save to database query upon exiting.  The new
  colon command "<TT>add</TT>" may be used to add features based on some other
  spectrum or arc type and then apply the fit to the combined set of features.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  autoidentify, reidentify, aidpars, center1d, linelists, fitcoords, icfit,
  gtools
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SUMMARY' 'USAGE' 'PARAMETERS' 'CURSOR KEYS' 'DESCRIPTION' 'DATABASE RECORDS' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
