mkphotcors — Prepare the photometric corrections files
======================================================

**Package: photcal**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkphotcors (Apr94)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.photcal</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkphotcors (Apr94)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkphotcors</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkphotcors -- type in and/or check the observing parameters, shifts
  or aperture corrections files for a given image set file.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkphotcors imsets idfilters obsparams shifts apercors
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_imsets">imsets</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imsets' Line='imsets'>
  <DD>The name of the input/output text file of observations, where  a complete
  observation consists of an observation name usually the name of
  the observed star field,
  followed by a list of images of that star field taken through the filters
  <I>idfilters</I>.
  If <I>imsets</I> does not exist, MKPHOTCORS prompts the user for
  input and writes the results to a new image set file <I>imsets</I>.
  If <I>imsets</I> does exist, MKPHOTCORS reads the file and prints messages
  about any errors or inconsistencies it finds in it. If <I>imsets</I> is "<TT></TT>",
  MKPHOTCORS prompts the user for input, but does not create a new <I>imsets</I>
  file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_idfilters">idfilters</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='idfilters' Line='idfilters'>
  <DD>The list of filters separated by whitespace or commas which define a complete
  observation. If <I>imsets</I> is entered interactively by the user,
  <I>idfilters</I> defines the number of images in an
  observation. If <I>imsets</I> is an existing file, MKPHOTCORS uses
  the number of filters specified by <I>idfilters</I> to
  check that there are the correct number of images in each observation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_obsparams">obsparams</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='obsparams' Line='obsparams'>
  <DD>The name of the input/output text file containing the quantities filter id,
  exposure time, airmass, and time of observation, for each image in <I>imsets</I>.
  If <I>obsparams</I> does not exist, MKPHOTCORS prompts the user for input
  and writes the results to the new observing parameters file <I>obsparams</I>.
  If <I>obsparams</I> already exists, MKPHOTCORS reads the file using the format
  specified by <I>obscolumns</I>, and prints out messages about any
  errors and inconsistencies it finds.
  If <I>obsparams</I>
  is "<TT></TT>", the user is not prompted for input and no output file is created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_shifts">shifts</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shifts' Line='shifts'>
  <DD>The name of the input/output text file containing the x-y shifts to be applied
  to the measured x-y coordinates of each object in each image in <I>imsets</I>.
  If <I>shifts</I> does not exist, MKPHOTCORS prompts the user for input
  and writes the results to the new shifts file <I>shifts</I>.
  If <I>shifts</I> already exists, MKPHOTCORS reads the file and prints out
  messages about any errors and inconsistencies it finds.
  If <I>shifts</I> is "<TT></TT>", the user is not prompted for input and no output
  file is created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apercors">apercors</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apercors' Line='apercors'>
  <DD>The name of the input/output text file containing the aperture corrections
  to be applied
  to the measured magnitudes of each object in each image in <I>imsets</I>.
  If <I>apercors</I> does not exist, MKPHOTCORS prompts the user for input
  and writes the results to the new aperture corrections file <I>apercors</I>.
  If <I>apercors</I> already exists, MKPHOTCORS reads the file and prints out
  messages about any errors and inconsistencies it finds.
  If <I>apercors</I> is "<TT></TT>", the user is not prompted for input and no output
  file is created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_obscolumns">obscolumns = "<TT>2 3 4 5</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='obscolumns' Line='obscolumns = "2 3 4 5"'>
  <DD>The list of numbers separated by commas or whitespace specifying which 
  columns in <I>obsparams</I> contain the filter ids, exposure times,
  airmasses, and times of observation, respectively of the images listed in column 1.
  <I>Obscolumns</I> is only used if <I>obsparams</I> already exists on disk.
  The number 0 may be used as a place holder in the <I>obscolumns</I> string.
  For example to read in only the airmass values, <I>obscolumns</I> should be
  set to "<TT>0 0 column</TT>" if the airmass values are in column.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verify">verify = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no'>
  <DD>Verify all data entered interactively ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions taken by MKPHOTCORS, and any warning or error
  messages generated.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  MKPHOTCORS takes an image set file <I>imsets</I> and a list of filter ids
  <I>idfilters</I> and writes one or more of the photometric corrections files
  <I>obsparams</I>, <I>shifts</I> and <I>apercors</I> required by the
  preprocessor tasks MKNOBSFILE and MKOBSFILE. MKPHOTCORS is intended as
  a simple tool to assist the user in creating and/or checking the input
  required by the MKNOBSFILE and MKOBSFILE tasks.
  <P>
  <I>Imsets</I> is the name of the input/output text file which tells
  MKNOBSFILE or MKOBSFILE which
  observations are to be extracted from the photometry files.
  A complete observation consists of the observation name,
  for example "<TT>M92</TT>", followed by a list of images
  taken through the filters <I>idfilters</I>, for example "<TT>m92u m92b m92v</TT>". 
  Observations are listed in <I>imsets</I>, 1 observation per line, with the
  observation name in column 1, a colon in column 2, followed by, in filter
  order and separated by whitespace, the names of the images belonging
  to that observation. A sample image set file is shown in the next section.
  <P>
  <I>Imsets</I> may be an existing file created with the MKIMSETS task, a file
  typed in by hand by the user, or a new file to be created by MKPHOTCORS.
  If <I>imsets</I> already exists, MKPHOTCORS reads the file and prints warning
  messages if it cannot decode the observations specification, or if the
  number of images in the observation does not match the number specified
  by <I>idfilters</I>. If imsets does not exist, MKPHOTCORS prompts the user
  for input using <I>idfilters</I> to determine the number of images
  there should be in each observation, and writes the results to the new
  image set file <I>imsets</I>. If <I>imsets</I> is "<TT></TT>", MKPHOTCORS prompts
  the user for input but does not save the results.
  <P>
  <I>Obsparams</I> is the name of the input/output text file listing the
  observing parameters filter id, exposure time, airmass, and time of observation,
  for the images in
  <I>imsets</I>. <I>Obsparams</I> is used to correct missing or incorrect
  filter ids, exposure times, airmasses, and times of observation in the photometry files, and
  is not required if all these values are correctly recorded in the photometry
  files. The observing parameters for each image are listed in
  <I>obsparams</I>, 1 image per line, with the image name in column 1, and the
  filter id, exposure time, airmass, and time of observation in the columns <I>obscolumns</I>.
  A sample observing parameters file is shown in the next section.
  <P>
  <I>Obsparams</I> may be an existing file created with the MKIMSETS task,
  a file typed in by hand by the user, or a new file to be created by
  MKPHOTCORS. If <I>obsparams</I> already exists, MKPHOTCORS reads the file
  and prints warning messages if it cannot decode the observing parameters,
  or if the there is an entry which does not correspond to one of the images
  listed in <I>imsets</I>. If <I>obsparams</I> does not exist, MKPHOTCORS
  prompts the user for input for each image in <I>imsets</I> and
  writes the results to a new observing parameters file <I>obsparams</I>.
  If <I>obsparams</I> is "<TT></TT>",  MKPHOTCORS does not prompt for input and no new
  file is written.
  <P>
  <I>Shifts</I> is the name of the text file specifying the x-y shifts, as
  a function of image, to be
  added to the x-y positions of all objects in the images listed in <I>imsets</I>.
  These shifts are
  used to brings frames of the same star field taken through different
  filters into rough alignment before matching individual objects.
  <I>Shifts</I> is not required if the frame to frame shifts are
  small, as is usually the case if the filters are of comparable thickness,
  and the exposures are short or well-guided.  The x-y shifts are listed 1
  per line with the name of the image in column 1, and the x and y shifts in
  columns 2 and 3 respectively.
  A sample shifts file is shown in the next section.
  <P>
  <I>Shifts</I> may be an existing file created with the IMCENTROID task and
  edited by the user,
  a file typed in by hand by the user, or a new file to be created by
  MKPHOTCORS. If <I>shifts</I> already exists, MKPHOTCORS reads the file
  and prints warning messages if it cannot decode the shifts,
  or if the there is an entry which does not correspond to one of the images
  listed in <I>imsets</I>. If <I>shifts</I> does not exist, MKPHOTCORS
  prompts the user for input for each of the images in <I>imsets</I> and
  writes the results to a new shifts file <I>shifts</I>.
  If <I>shifts</I> is "<TT></TT>",  MKPHOTCORS does not prompt for input and no new
  file is written.
  <P>
  <I>Apercors</I> is the name of the text file specifying the aperture
  corrections, as a function of image,  to be added to the magnitudes of all
  objects in the images listed in <I>imsets</I>.
  The aperture corrections are most often used to correct the instrumental
  magnitudes of stars
  measured through a small aperture to minimize crowding affects, to the
  instrumental magnitudes of standard stars measured through a larger
  aperture. These aperture corrections will normally be a function of filter
  and of seeing and focus which can change throughout the night.
  Aperture corrections are normally not required for standard star measurements.
  Aperture corrections are listed 1 per line with
  the name of the image in column 1, and the aperture correction in column 2.
  A sample aperture corrections file is shown in the next section.
  <P>
  <I>Apercors</I> may be an existing file
  typed in by hand by the user, or a new file to be created by
  MKPHOTCORS. If <I>apercors</I> already exists, MKPHOTCORS reads the file
  and prints warning messages if it cannot decode the aperture corrections,
  or if the there is an entry which does not correspond to one of the images
  listed in <I>imsets</I>. If <I>apercors</I> does not exist, MKPHOTCORS
  prompts the user for input for each of the images in <I>imsets</I> and
  writes the results to a aperture corrections file <I>apercors</I>.
  If <I>apercors</I> is "<TT></TT>",  MKPHOTCORS does not prompt for input and no new
  file is written.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_output">OUTPUT</A></H2>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  A sample image set file for a set of UBV 100 second, 600 seconds, and 
  1800 second exposure images of the globular cluster m92 is shown below.
  The labels "<TT>M92S</TT>", "<TT>M92M</TT>", and "<TT>M92L</TT>" stand for the  100, 600, 1800 second
  exposure observations sets respectively. The names which follow the labels are
  the names of the actual IRAF images comprising each data set. The image names
  must match those in the photometry files.
  <P>
  <PRE>
  	M92S : m92us  m92bs m92vs
  	M92M : m92um  m92bm m92vm
  	M92L : m92ul  m92bl m92vl
  </PRE>
  <P>
  A sample observing parameters file is shown for the above data set. In this
  example the user forgot to tell the photometry code to pick up the filter ids,
  exposure times, airmasses, and times of observation from the image headers and
  so is obliged to
  correct them after the fact via the observing parameters file. The filters
  U B V are represented by the numbers 1 2 3. 
  <P>
  <PRE>
  	m92us  1  100   1.10 03:10:53
  	m92bs  2  100   1.09 03:14:06
  	m92vs  3  100   1.06 03:18:54
  	m92um  1  600   1.03 04:15:05
  	m92bm  2  600   1.03 04:29:43
  	m92vm  3  600   1.03 04:44:56
  	m92ul  1  1800  1.06 06:10:33
  	m92bl  2  1800  1.12 06:45:32
  	m92vl  3  1800  1.18 07:23:02
  </PRE>
  <P>
  A sample shifts file for the above data set is shown below.
  Only the long exposure frames have significant frame to frame shifts
  so only those images are included in the shifts file.
  The long u frame is used a position reference so its x-y shift is zero.
  <P>
  <PRE>
  	m92ul  0.0  0.0
  	m92bl  5.4  8.4
  	m92vl  9.6  17.1
  </PRE>
  <P>
  A sample aperture corrections file for the above data set is shown below.
  Note that the aperture correction appears to vary in a systematic
  way  with filter.
  <P>
  <PRE>
  	m92us  -.153
  	m92bs  -.110
  	m92vs  -.083
  	m92um  -.149
  	m92bm  -.108
  	m92vm  -.090
  	m92ul  -.160
  	m92bl  -.123
  	m92vl  -.079
  </PRE>
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Type in the image set file and accompanying shifts and aperture corrections
  files  for a set of UBV observations of a crowded field in NGC4147. The filter
  ids "<TT>1 2 3</TT>" stand
  for "<TT>U B V</TT>". The photometry programs picked up the correct values of
  the filter id, exposure time, and airmass from the image headers
  and wrote them to the photometry
  files so the observing parameters file is not required.
  <P>
  <PRE>
  	ph&gt; mkphotcors n4147.imsets "1,2,3" "" n4147.shifts n4147.apcors
  </PRE>
  <P>
  2. Type in the shifts and aperture corrections files for the already
  existing image set file m17.imsets. In this case the filter set is "<TT>J H K</TT>".
  <P>
  <PRE>
  	ph&gt; mkphotcors m17.imsets "J,H,K" "" m17.shifts m17.apcors
  </PRE>
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