obsfile — Prepare an observations file from a text file
=======================================================

**Package: photcal**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>obsfile (Apr94)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.photcal</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>obsfile (Apr94)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>obsfile</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  obsfile -- prepare an observations file from a list of user created 
  photometry files containing observations of objects in one or more fields
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  obsfile photfiles incolumns idfilters imsets observations
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_photfiles">photfiles</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photfiles' Line='photfiles'>
  <DD>A list of text files containing the image names or an image id, x-y positions,
  magnitudes, magnitude errors, airmasses, filter ids, exposure times, and time
  of observation of all the measured objects. <I>Photfiles</I> are assumed to be
  the output of the user's own digital photometry program. All the files in the
  list must have the format specified by <I>incolumns</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_incolumns">incolumns</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='incolumns' Line='incolumns'>
  <DD>A list of ten numbers separated by commas or whitespace specifying which
  columns in <I>photfiles</I> contain the following fields: the image name or id,
  x coordinate, y coordinate, filter id, exposure time, airmass, time of
  observation, instrumental magnitude, magnitude error, and object id
  respectively.  
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_idfilters">idfilters</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='idfilters' Line='idfilters'>
  <DD>The list of filter ids separated by whitespace or commas which define a
  complete observation. The filter ids must correspond to those in
  <I>photfiles</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imsets">imsets</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imsets' Line='imsets'>
  <DD>The name of the text file which lists the observations of each field, assigns a
  name to each field, and tells OBSFILE which images belong to the same
  observation of that field. Only observations corresponding to the images
  specified in <I>imsets</I> will be extracted from <I>photfiles</I>. Observations
  are listed in <I>imsets</I>, 1 observation per line with the field name in
  column 1, a colon in column 2, followed by, in filter order and separated by
  whitespace, the names of the images of that field belonging to that
  observation. The format of <I>imsets</I> is described in detail below.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_observations">observations</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observations' Line='observations'>
  <DD>The output observations file suitable for input to FITPARAMS or
  EVALFIT/INVERTFIT.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wrap">wrap = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wrap' Line='wrap = yes'>
  <DD>Format the output observations file for easy reading ? If wrap = yes then the
  observation in each filter are written on a separate line and the * character
  in column 1 is interpreted as a continuation character. Otherwise all the
  observations for a single filter are written on a single line where the maximum
  length of a line is SZ_LINE characters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_obsparams">obsparams = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='obsparams' Line='obsparams = ""'>
  <DD>The name of an optional text file containing the correct filter ids, exposure
  times, airmasses, and time of observations for each image whose values are
  either undefined or incorrectly stored in <I>photfiles</I>. The observing
  parameters for each image are listed in the file <I>obsparams</I>, 1 image per
  line with the image name in column 1 and the filter ids, exposure times,
  airmasses, and times of observation listed in columns <I>obscolumns</I>. The
  image names must match those in <I>imsets</I>. Images which have no entries in
  <I>obsparams</I> are assigned the values stored in <I>photfiles</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_obscolumns">obscolumns = "<TT>2 3 4 5</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='obscolumns' Line='obscolumns = "2 3 4 5"'>
  <DD>The list of numbers separated by commas or whitespace specifying which columns
  in the text file <I>obsparams</I> contain the correct filter ids, exposure
  times, airmasses, and times of observation respectively. The number 0 can be
  used as a place holder in the <I>obscolumns</I> string. For example, to correct
  only  the <I>photfiles</I> airmass values, <I>obscolumns</I> should be set to
  "<TT>0 0 column 0</TT>", where column is the airmass column number. The default value of
  <I>obscolumns</I> corresponds to the format of the default <I>obsparams</I> file
  produced by MKIMSETS.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_minmagerr">minmagerr = 0.001</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minmagerr' Line='minmagerr = 0.001'>
  <DD>The error that will be assigned to a non-INDEF valued magnitude measurement
  whose recorded error is less than <I>minmagerr</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_shifts">shifts = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shifts' Line='shifts = ""'>
  <DD>The name of the text file specifying the x and y shifts to be ADDED to the x-y
  positions of all objects in an image before position matching (the original x's
  and y's are retained in the output). Shifts are listed for each image, 1 image
  per line with the name of the image in column 1, followed by the x and y shifts
  in columns 2 and 3 respectively. Image names must match those in <I>imsets</I>.
  Images for which no shift is supplied are assigned x and y shifts of zero.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apercors">apercors = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apercors' Line='apercors = ""'>
  <DD>The name of the text file specifying the aperture corrections to be ADDED to
  the extracted magnitudes. Aperture corrections are listed for each image, 1
  image per line with the name of the image in column 1, followed by the aperture
  correction in magnitudes in column 2.  The image names must match those in
  <I>imsets</I>. Images for which no aperture correction is supplied are assigned
  a default value of zero.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_normtime">normtime = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='normtime' Line='normtime = no'>
  <DD>Normalize the magnitudes to an exposure time of one time unit using the
  exposure times in <I>photfiles</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tolerance">tolerance = 5.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tolerance' Line='tolerance = 5.0'>
  <DD>The tolerance in pixels for matching objects in the same observation, but
  different images.  OBSFILE extracts the x and y coordinates of each object
  in each image of a given observation from <I>photfiles</I>, adds the shift for
  that image in <I>shifts</I> to the extracted x-y coordinates, and matches the
  objects to within <I>tolerance</I> pixels. Missing objects are assigned INDEF
  entries in <I>observations</I>. If <I>tolerance</I> is less than or equal to 0
  no coordinate matching is done, and objects are matched in order of occurrence
  with missing objects being assigned INDEF values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_allfilters">allfilters = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='allfilters' Line='allfilters = no'>
  <DD>Output only objects which are successfully matched in all the filters specified
  by <I>idfilters</I>?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verify">verify = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no'>
  <DD>Verify interactive user input? This option is used only if any of <I>imsets</I>,
  <I>obsparams</I>, <I>shifts</I>, or <I> apercors</I> are set to the standard input
  "<TT>STDIN</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions taken by the task or any warnings or errors
  encountered?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  OBSFILE takes a list of user generated text files <I>photfiles</I>, where each
  file contains  observations of one or more objects taken through one or more
  filters, and the image set file <I>imsets</I>, and prepares a single
  observations file <I>observations</I>. OBSFILE is intended for use with any
  user digital stellar photometry program which writes its output in simple text
  files format.
  <P>
  OBSFILE performs the following functions: 1) extracts the quantities
  image name or image id, x and y position, filter id, exposure time, airmass,
  time of observation, magnitude, and magnitude error from
  <I>photfiles</I>, 2) corrects any erroneous or missing values of filter id,
  exposure time, airmass, or time of observation in <I>photfiles</I>,  3) associates each 
  field with one or more sets of images of that
  field taken through different filters 4) matches individual objects within
  a given observation by order of occurrence or x-y position, and
  5) assigns a unique name to each object in each field.
  <P>
  The parameter <I>incolumns</I> describes the format of <I>photfiles</I>.
  <I>Incolumns</I> is a list of ten numbers separated by commas or whitespace
  which specify the columns containing the following fields: the
  image name or id,
  the x coordinate, the y coordinate, the filter id, the exposure time, 
  the airmass, the time of observation the instrumental magnitude, the
  magnitude error, and the object id.
  For example
  if <I>incolumns</I> is "<TT>10 2 3 6 8 7 9 4 5 1</TT>", the object id is assumed to
  be in column 1, the image id in column 10, the x and y positions in columns 2 and 3, the filter id,
  exposure time, airmass, and time of observation in columns 6, 8, 7 and 9,
  and the instrumental
  magnitude and magnitude error in columns 4 and 5. The image names must
  match those in <I>imsets</I> or the corresponding input data is skipped.
  The columns image name, x coordinate, y coordinate, and magnitude
  are mandatory and must be present in <I>photfiles</I>. 
  Other missing columns in the data may be represented by a "<TT>0</TT>" in the
  appropriate place in <I>incolumns</I>.
  For example, if there is no magnitude error
  column in <I>photfiles</I> a value of INDEF will be written in the appropriate
  column in <I>observations</I>. 
  If there is no airmass column in <I>photfiles</I> the value in
  <I>obspararms</I> if any, or the value INDEF will be written to the appropriate
  column in <I>observations</I>. 
  If there is no filter id column in <I>photfiles</I> the value in
  <I>obspararms</I> if any, or one of the values in <I>idfilters</I>
  will be written to the appropriate column in <I>observations</I>. 
  If there is no exposure time column in <I>photfiles</I> the value in
  <I>obspararms</I> if any, or a value of one will be assumed.
  If there is no time of observation time column in <I>photfiles</I> the value in
  <I>obspararms</I> if any, or a value of INDEF will be assumed.
  <P>
  The image set file <I>imsets</I> assigns a name to each field.
  For fields containing only a single standard star this name should
  match the name of the standard star in the standard star catalog.
  For fields containing more than one star, OBSFILE constructs a unique
  name for each object in the field by adding a sequence number to the 
  field name in <I>imsets</I>, which if the star is a standard star, the
  user must later edit. For example the fourth star in the field "<TT>M92</TT>"
  will be assigned the name "<TT>M92-4</TT>" in <I>observations</I>.
  If this star is a standard star and its true name is "<TT>IX-10</TT>" in the
  standard star catalog, then the user must change "<TT>M92-4</TT>" to "<TT>IX-10</TT>"
  in <I>observations</I>.
  <I>Imsets</I> also tells OBSFILE which images
  in <I>photfiles</I> are images of the same region of the sky belonging
  to the same observation.
  The format of <I>imsets</I> is described in detail below.
  If the number of observations is small the user may wish to simply type
  in <I>imsets</I> by hand. If the number of observations is large, a 
  separate task MKIMSETS is available to assist users in preparing
  <I>imsets</I>.
  <P>
  Values of the filter ids, exposure times, airmasses, and times of observation,
  which are undefined or incorrect in <I>photfiles</I>,
  can be corrected by reading values listed in the columns <I>obscolumns</I>
  in the file <I>obsparams</I>. The format of <I>obsparams</I> is described
  in detail below.
  <P>
  OBSFILE matches the objects in different images within the same observation
  either
  by order of occurrence if <I>tolerance</I> is less than or equal to 0.0,
  or by x-y position. Matching by position is done by identifying which objects
  in each of the
  images of a given field and observation set are within <I>tolerance</I>
  pixels of each other.  The user may supply an optional file of x and y
  shifts <I>shifts</I> to be added to the object positions prior to
  matching. The format of <I>shifts</I> is described in detail below.
  If the parameter <I>allfilters</I> is "<TT>yes</TT>", only objects which are matched
  in all the filters <I>idfilters</I> are output to <I>observations</I>.
  <P>
  OBSFILE permits the user to supply 
  an optional file of aperture corrections <I>apercors</I> containing
  magnitude corrections which are added to the instrumental
  magnitudes in <I>photfiles</I>.
  The format of <I>apercors</I> is described in detail below.
  <P>
  Each new observations file created by OBSFILE has an associated format
  description file listing the column names and numbers in <I>observations</I>,
  of the fields extracted from <I>photfiles</I>. This file, referenced 
  by its parent observations file name, can be used as input to the
  MKCONFIG task. The actual name of the format description file on disk is
  constructed by prepending the string "<TT>f</TT>" and appending the string "<TT>.dat</TT>"
  to <I>observations</I>.
  For example if a new observations file called "<TT>nite1</TT>" is created by
  OBSFILE, a format description file called "<TT>fnite1.dat</TT>" will also be
  created. Any pre-existing format description file of that name, which does
  not have an associated observations file, will be deleted.
  <P>
  <P>
  THE IMSETS FILE
  <P>
  The <I>imsets</I> file lists the 
  the observations of each field, assigns a name to each
  field, and informs OBSFILE which images belong to the same
  observation of that field.
  Observations are listed in <I>imsets</I>, 1 observation
  per line with the field name in column 1, a colon in column 2,
  followed by the names of the
  images of that field for that observation separated by whitespace.
  Only data for image names in <I>imsets</I> which match those in
  <I>photfiles</I> will be extracted.
  <P>
  The field name is used to generate the output object name in <I>observations</I>.
  If there is only a single measured object in the field, then the name
  of that object in <I>observations</I> will be the name of the field. If
  the single object is a standard star, the user should edit <I>imsets</I>
  so that the field name is the same as the name of the standard star in
  the standard star catalog. If a stellar field contains more than one
  measured object, OBSFILE generates names of the form "<TT>field-#</TT>" where
  "<TT>field</TT>" is the field name and "<TT>#</TT>" is a sequence number. For example the
  fourth star in the field "<TT>M92</TT>" will be assigned the name "<TT>M92-4</TT>" in
  <I>observations</I>. If the star is a standard star, the user must edit
  the object names in <I>observations</I> to match those in the standard
  star catalog.
  <P>
  Any number of observations may have the same field name. This normally occurs,
  for example, when multiple observations of a single standard star of
  standard star field are made at several airmasses.
  <P>
  If there
  are no filter ids in <I>photfiles</I> or <I>obsparams</I> then the images in
  each image set are assigned the filter ids in <I>idfilters</I> in order
  of occurrence.
  <P>
  The <I>imsets</I> file for a  set of 50 UBV frames of fifteen standard star
  fields is listed below. There is only a single bright star per field.
  The name of star field in column 1 has been edited to be identical
  to the name of the standard in the standard star catalog. Column 2 contains
  a <TT>':'</TT>. The U, B and V
  images for each field are listed in columns 3, 4 and 5 respectively.
  The missing U image for field "<TT>STD7</TT>" is represented by the name "<TT>INDEF</TT>".
  Standard stars "<TT>STD1</TT>" and "<TT>STD2</TT>" were observed twice in the same night
  at different airmasses.
  <P>
  <PRE>
  	STD1 :	nite001   nite002  nite003
  	STD1 :  nite045   nite046  nite047
  	STD2 :	nite004   nite005  nite006
  	STD2 :	nite048   nite049  nite050
  	...
  	STD7 :  INDEF     nite019  nite020
  	...
  	STD14 : nite039   nite040  nite041
  	STD15 : nite042   nite043  nite044
  </PRE>
  <P>
  THE OBSPARAMS FILE
  <P>
  A sample corrections file <I>obsparams</I> for the previous set of
  UBV standards observations is shown below.
  The filter ids, exposure times, airmasses, and times of observation for all the images were
  correctly read
  from the image headers with the exception of the filter id, exposure time,
  and airmass for the first  "<TT>STD2</TT>" V frame.
  The correct filter id, exposure time, airmass, and time of observation, is supplied
  in <I>obsparams</I>  and <I>obscolumns</I> is set to "<TT>2 3 4 5</TT>"
  <P>
  <PRE>
  	nite006    3 8 1.256 14:30:02.3
  </PRE>
  <P>
  Zero can be used as a place holder in <I>obscolumns</I>,
  as in the following example where
  the user only wants to correct the exposure time and the airmass and
  leave the filter id alone. In this case <I>obscolumns</I> is "<TT>0 2 3 0</TT>"
  and <I>obsparams</I> looks as follows.
  <P>
  <PRE>
  	nite006    8 1.256
  </PRE>
  <P>
  Only images listed in <I>imsets</I> can have their observing parameters
  modified by <I>obsparams</I>.
  <P>
  THE SHIFTS FILE
  <P>
  The file <I>shifts</I> lists the shifts for each image, 1 shift per line,
  with the image name in column 1 and the x and y shifts in columns 2 and
  3 respectively.
  The image names in <I>shifts</I> must match those in <I>imsets</I>.
  <P>
  A sample shifts file for the previous set of UBV standards
  observations is shown below. All the standards except for "<TT>STD14</TT>" are assumed
  to have no significant shifts from filter to filter. The B and V frames
  for "<TT>STD14</TT>" are shifted -10 pixels in x and -5 pixels
  in y with respect to the U frame. Therefore +10 and +5 pixels should be
  added to the "<TT>STD14</TT>" B and V frame positions respectively before
  position matching.
  <P>
  <PRE>
  	nite040   10.0   5.0
  	nite041   10.0   5.0
  </PRE>
  <P>
  An alternate way of listing the same observations would be the following.
  <P>
  <PRE>
  	nite039   -10.0 -5.0
  </PRE>
  <P>
  THE APERCORS FILE
  <P>
  The file <I>apercors</I> lists the aperture corrections for each image,
  1 aperture correction per line,
  with the image name in column 1 and the aperture correction in magnitudes
  in column 2 respectively.
  The image names in <I>apercors</I> must match those in <I>imsets</I>.
  <P>
  The <I>apercors</I> file for the previous set of UBV observations is shown
  below.
  The aperture corrections for all the standard stars are assumed to be
  zero except for "<TT>STD14</TT>".
  <P>
  <PRE>
  	nite039    -0.150
  	nite040    -0.100
  	nite041    -0.090
  </PRE>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_output">OUTPUT</A></H2>
  <! BeginSection: 'OUTPUT'>
  <UL>
  For the previous set of UBV observations the output file
  <I>observations</I> produced by OBSFILE will look like the following.
  The filter ids for the U,B,V filters are assumed to be 1,2,3.
  Note that the exposure times are assumed to have been normalized either
  prior to running OBSFILE or by OBSFILE itself,
  and so are not included in <I>observations</I>.
  <P>
  <PRE>
  	# FIELD   FILTER   OTIME  AIRMASS  X     Y     MAG   MERR
  <P>
  	  STD1    1        .      .        .     .     .     .
  	  *       2        .      .        .     .     .     .
  	  *       3        .      .        .     .     .     .
  	  STD1    1        .      .        .     .     .     .
  	  *       2        .      .        .     .     .     .   
  	  *       3        .      .        .     .     .     .
  	  STD2    1        .      .        .     .     .     .
  	  *       2        .      .        .     .     .     .
  	  *       3        .      .        .     .     .     .
  	  STD2    1        .      .        .     .     .     .
  	  *       2        .      .        .     .     .     .
  	  *       3        .      .        .     .     .     .
  	  ........................................................
  	  STD7    INDEF    INDEF  INDEF    INDEF INDEF INDEF INDEF
  	  *       2        .      .        .     .     .     .
  	  *       3        .      .        .     .     .     .
  	  .......................................................
  	  STD14   1        .      .        .     .     .     .
  	  *       2        .      .        .     .     .     .
  	  *       3        .      .        .     .     .     .
  	  STD15   1        .      .        .     .     .     .
  	  *       2        .      .        .     .     .     .
  	  *       3        .      .        .     .     .     .
  </PRE>
  <P>
  The accompanying format description file has the following form.
  <P>
  <PRE>
  # Declare the observations file variables
  <P>
  observations
  <P>
  X1            3              # airmass in filter 1
  T1            4              # time of observation in filter 1
  x1            5              # x coordinate in filter 1
  y1            6              # y coordinate in filter 1
  m1            7              # instrumental magnitude in filter 1
  error(m1)     8              # magnitude error in filter 1
  <P>
  X2            10             # airmass in filter 2
  T2            11             # time of observation in filter 2
  x2            12             # x coordinate in filter 2
  y2            13             # y coordinate in filter 2
  m2            14             # instrumental magnitude in filter 2
  error(m2)     15             # magnitude error in filter 2
  <P>
  X3            16             # airmass in filter 3
  T3            17             # time of observation in filter 3
  x3            18             # x coordinate in filter 3
  y3            19             # y coordinate in filter 3
  m3            20             # instrumental magnitude in filter 3
  error(m3)     21             # magnitude error in filter 3
  </PRE>
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Prepare an observations file, from a set of standard star observations
  in a file output by the user's own digital stellar photometry program,
  for input to FITPARAMS. A sample of the file illustrating the format
  is shown below.
  Since there is only one star per field, position matching is not necessary.
  The magnitudes have already been normalized to unit exposure time by the
  user's program, and the filter ids and airmasses are correct. However the
  observing time column is missing and represented by a zero in the incolumns
  parameters.
  <P>
  <PRE>
  	ph&gt; head magsfile
  <P>
  	    ... print out the first few lines of the photometry file
  <P>
  	    std1u   40.4   50.3   18.059   0.043   U   1.030   1.0
  	    std1b   42.5   53.1   17.089   0.023   B   1.032   1.0
  	    std1v   43.8   56.9   16.023   0.020   V   1.034   1.0
  	    std2u   39.4   55.3   17.029   0.040   U   1.135   1.0
  	    std2b   41.5   57.3   15.905   0.020   B   1.140   1.0
  	    std2v   42.6   58.9   14.899   0.018   V   1.144   1.0
  	    .....   ....   ....   ......   .....   .   .....   ...
  	    .....   ....   ....   ......   .....   .   .....   ...
  <P>
  	ph&gt; type fields
  <P>
  	    ... print out the corresponding image set file
  <P>
  	    std1 : std1u  std1b  std1v
  	    std2 : std2u  std2b  std2v
  	    ..... .....  .....  .....
  	    ..... .....  .....  .....
  <P>
  	ph&gt; obsfile magsfile "1 2 3 6 8 7 0 4 5" "U,B,V" fields standards.obs\<BR>
  	    tol=0.0
  <P>
  	    ... create the observations file
  <P>
  	ph&gt; edit standards.obs
  <P>
  	    ... edit the observations file so that the object names
  		match those in the standard star catalog
  </PRE>
  <P>
  2. Prepare an observations file from a set of program star observations
  of a crowded field in the globular cluster M92 computed by the same
  digital photometry
  program as above, for input to FITPARAMS.  The 3 input files contain UBV
  measurements of over 2000 stars in the M92 field. Since the same stars
  were not measured in all filters position matching is necessary.
  <P>
  <PRE>
  	ph&gt; head m92umags,m92bmags,m92vmags
  <P>
  	    ... print the first few lines of the input files on the
  	        standard output
  <P>
  	    m92u    80.4   42.3   17.046   0.046   U   1.056   1.0
  	    m92u    ....   ....   ......   .....   U   1.056   1.0
  <P>
  	    m92b    62.6   81.1   18.071   0.041   B   1.030   1.0
  	    m92b    ....   ....   ......   .....   B   1.030   1.0
  <P>
  	    m92v    33.8   26.9   16.023   0.022   V   1.034   1.0
  	    m92v    ....   ....   ......   .....   V   1.034   1.0
  <P>
  	ph&gt; type fields
  <P>
  	    ... print out the image set file
  <P>
  	    m92 : m92u  m92b  m92v
  <P>
  	ph&gt; obsfile m92umags,m92bmags,m92vmags "1 2 3 6 8 7 0 4 5" "U,B,V"\<BR>
  	    fields standards.obs tolerance=8.0
  <P>
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
  mkimsets,mknobsfile,mkobsfile
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'OUTPUT' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>