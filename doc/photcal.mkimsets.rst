.. _mkimsets:

mkimsets — Prepare an image set file for input to (mk)(n)obsfile
================================================================

**Package: photcal**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkimsets -- create an image set file from the observations for input
  to MKNOBSFILE OR OBSFILE
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkimsets imlist idfilters imsets 
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>imlist</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imlist' Line='imlist'>
  <DD>The file(s) containing all the image names and filter ids associated with
  the observations.
  <I>Imlist</I> is a list of APPHOT/DAOPHOT databases if <I>input</I> =
  "<TT>photfiles</TT>", a list of images if <I>input</I> = "<TT>images</TT>", or the name
  of a user text file if <I>input</I> = "<TT>user</TT>".
  The default input is a list of APPHOT/DAOPHOT databases.
  </DD>
  </DL>
  <DL>
  <DT><B>idfilters</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='idfilters' Line='idfilters'>
  <DD>The ids of the filters, separated by whitespace or
  commas, which define a complete observation.
  The order in which the filter ids are listed in the string <I>idfilters</I>
  determines the order in which the image names associated with each observation
  are written in <I>imsets</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>imsets</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imsets' Line='imsets'>
  <DD>The name of the output image set file which lists each observation of
  each star field, assigns a name
  to each observation, and specifies which images belong to the same
  observation of that star field.
  </DD>
  </DL>
  <DL>
  <DT><B>imobsparams = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imobsparams' Line='imobsparams = ""'>
  <DD>The name of the output image list file containing the image name,
  the filter id,
  and the quantities specified by <I>fields</I>, for each
  unique image referenced in <I>imlist</I>.
  <I>Imobsparams</I> includes changes made by the user if <I>edit</I> is
  "<TT>yes</TT>". If <I>imobsparams</I> is "<TT></TT>" the output image list
  is not saved.
  </DD>
  </DL>
  <DL>
  <DT><B>input = photfiles</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input = photfiles'>
  <DD>The source of the information used to create the image set file.
  The options are:
  <DL>
  <DT><B>photfiles</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='photfiles' Line='photfiles'>
  <DD>Extract the image list from the APPHOT/DAOPHOT 
  databases containing
  the photometry. This option uses the PTOOLS task DUMP to extract
  the image name, the filter id, the exposure time, the airmass,  the
  time of observation, and
  other user selected fields <I>fields</I> from the database files.
  </DD>
  </DL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='images' Line='images'>
  <DD>Extract the image list from the headers of the images containing
  the objects measured
  with APPHOT or DAOPHOT. This option uses the IMAGES task HSELECT to extract
  the image name, the filter id <I>filter</I>, and other user selected
  fields <I>fields</I> from the image headers. Useful additional fields
  might be the image title and the time of the observation.
  </DD>
  </DL>
  <DL>
  <DT><B>user</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='user' Line='user'>
  <DD>Extract the image list from a user created file which has the
  image name in the first column, the filter id in the column
  <I>filter</I>, and 
  other useful information in the columns specified by <I>fields</I>.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>filter</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filter' Line='filter'>
  <DD>The filter id keyword.
  <I>Filter</I> is always the APPHOT/DAOPHOT database keyword "<TT>IFILTER</TT>"
  if <I>input</I> is "<TT>photfiles</TT>",
  the image header keyword which defines the filter id if <I>input</I> is
  "<TT>images</TT>", or the number of the column
  containing the filter id, if <I>input</I> is "<TT>user</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>fields = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fields' Line='fields = ""'>
  <DD>The list of additional fields, besides the image name and filter id,
  to be extracted from <I>imlist</I>, separated by whitespace or commas.
  If <I>input</I> is "<TT>photfiles</TT>" <I>fields</I> is a list of APPHOT/DAOPHOT
  keywords including "<TT>itime,xairmass</TT>"; if <I>input</I> is "<TT>images</TT>"
  <I>fields</I> is a list of image
  header keywords; if <I>input</I> is "<TT>user</TT>" <I>fields</I> is a list of the
  column numbers defining the fields to be extracted from the user file.
  <I>Fields</I> may include any quantities, for example airmass, image title, or
  the time of the observation, which aid the user in the interactive
  image name grouping process.
  </DD>
  </DL>
  <DL>
  <DT><B>sort = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sort' Line='sort = ""'>
  <DD>Sort the extracted image list in order of the value of the quantity <I>sort</I>.
  <I>Sort</I> must be one of the fields
  <I>"image"</I>, <I>filter</I>, or <I>fields</I> if <I>input</I>
  is "<TT>images</TT>" or "<TT>photfiles</TT>", or the column number in the user file of the
  field to be sorted on if <I>input</I> is "<TT>user</TT>".
  <I>Sort</I> is used to reorder the image list 
  before entering the editor.
  </DD>
  </DL>
  <DL>
  <DT><B>edit = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='edit' Line='edit = yes'>
  <DD>Edit the extracted image name list interactively, checking that the images
  belonging to a single observation are adjacent to one another in the list,
  and that the filter ids are present and match those in <I>idfilters</I>.
  For each observation there must be an image name for every filter
  in <I>idfilters</I>.
  Missing set members must be assigned the image name "<TT>INDEF</TT>" for undefined
  and the filter id of the missing observation.
  </DD>
  </DL>
  <DL>
  <DT><B>rename = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rename' Line='rename = yes'>
  <DD>Enter new names for each observation of each field interactively.
  If <I>rename</I> is "<TT>no</TT>", default names
  of the form "<TT>OBS1</TT>", "<TT>OBS2</TT>", ..., "<TT>OBSN</TT>" are assigned. If <I>rename</I> is "<TT>yes</TT>",
  MKIMSETS prints each image set
  on the terminal and prompts the user for the new name.
  Images sets containing a single standard star observation should be assigned
  the name of the standard star in the standard star catalog.
  </DD>
  </DL>
  <DL>
  <DT><B>review = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='review' Line='review = yes'>
  <DD>Review and edit <I>imsets</I> to check that the image set names are correct
  and that the images names have been properly grouped into sets.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  MKIMSETS is a script task which takes as input a list of
  the image names and filter ids, <I>imlist</I>, associated
  with objects whose magnitudes have been measured with APPHOT, DAOPHOT,
  or a user program, and produces the image set file <I>imsets</I> 
  required as input by the preprocessor tasks MKNOBSFILE or OBSFILE.
  MKIMSETS is used in conjunction with MKNOBSFILE OR OBSFILE to combine many
  individual digital photometry measurements, for example standard star
  measurements,
  into a single observations file. The source of the input image list is
  a list of IRAF images if <I>input</I> is "<TT>images</TT>",
  a list of APPHOT or DAOPHOT database files if <I>input</I> is "<TT>photfiles</TT>",
  or a user supplied text file if <I>input</I> is "<TT>user</TT>".
  <P>
  The output image set file <I>imsets</I> lists each observation of
  each star field, assigns a name supplied by the user
  to each observation, and specifies which images belong to the same
  observation of that star field.
  In the case of image sets which contain a single standard star measurement,
  the image set name should
  match the name of the standard star in the standard star catalog.
  <P>
  The optional output image observing parameters file <I>imobsparams</I>
  lists each unique image in <I>imlist</I>, its
  filter id <I>filter</I>, and other user specified fields <I>fields</I>.
  <I>Imobsparams</I> may be edited by
  the user, and used by the preprocessor tasks MKNOBSFILE or OBSFILE
  to correct erroneous or undefined values of
  filter id, exposure time, airmass and time of observation in the input
  databases.  By default <I>imobsparams</I> is not written.
  <P>
  After task initialization, MKIMSETS extracts each unique image name,
  the corresponding filter id stored in column <I>filter</I>,
  and the corresponding values of the user defined fields <I>fields</I>,
  from the input list <I>imlist</I>, and writes the resulting image list
  in tabular form to a temporary file.
  The temporary image list file contains the image name in column 1,
  the value of <I>filter</I> in column 2, and the values of
  any additional fields in succeeding columns in the order they were
  specified in <I>fields</I>.
  <P>
  If <I>sort</I> is one of the extracted
  fields "<TT>image</TT>", <I>filter</I>, or <I>fields</I>, MKIMSETS sorts the image
  list based on the values of <I>sort</I>, before writing the results to the
  the temporary image list file.
  <P>
  If <I>edit</I> is "<TT>yes</TT>", the user enters the text editor and edits the
  temporary image list interactively.
  The image list must be arranged so that members of each image set are
  adjacent to each other in the image list.
  Missing images may be represented by
  an INDEF in column 1, the appropriate filter id in column 2, and
  INDEF in any other columns.
  The edit step is necessary if the image names are not in any logical
  order in <I>imlist</I> for <I>input</I> = "<TT>images</TT>",
  do not occur in any logical order in the APPHOT/DAOPHOT 
  databases for <I>input</I> = "<TT>photfiles</TT>", or are not listed logically
  in <I>imlist</I> for <I>input</I> = "<TT>user</TT>".
  At this point MKIMSETS saves the temporary image list in the text file
  <I>imobsparams</I>, if <I>imobsparams</I> is defined.
  <P>
  After the initial edit, MKIMSETS groups the images in the temporary image list,
  by using the filter ids in <I>idfilters</I>, and assuming that the image
  names are in logical order.
  If <I>rename</I> is "<TT>yes</TT>", MKIMSETS prompts the user for the name of each 
  image set. Otherwise the default names OBS1, OBS2, ..., OBSN are
  assigned.
  If <I>review</I> is "<TT>yes</TT>", MKIMSETS enters the editor, permitting the user
  to review <I>imsets</I> and interactively
  correct any mistakes.
  Image sets are written to <I>imsets</I>, 1 set
  per line with the image set name in column 1, a colon in column 2,
  followed by, in filter order and separated by whitespace, the names of the
  images of that field, for that  observation.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Create an image set file from a list of APPHOT databases which
  contain UBV observations of 5 standard stars. The UBV filters are
  identified in the APPHOT databases by the filters ids "<TT>1</TT>","<TT>2</TT>", "<TT>3</TT>" 
  respectively. There is one database file
  for each star measured. Since data for each of the stars was taken
  sequentially and the images were read sequentially off tape, the user
  requests MKIMSETS to sort the extracted data by image name. Note that
  the time of observation field was undefined in the input data sets.
  <P>
  <PRE>
  	ph&gt; mkimsets *.mag.* "1,2,3" jan10.stdim sort="image"
  <P>
  	   ... MKIMSETS constructs the image list and sorts on
  	       the image name
  <P>
  	   ... MKIMSETS enters the editor and lists the first few
  	       lines of the intermediate image list file
  <P>
  	   im001  1  3.0  1.150 INDEF
  	   im002  2  2.0  1.150 INDEF
  	   im003  3  2.0  1.140 INDEF
  	   im004  1  6.0  1.300 INDEF
  	   im005  2  4.0  1.300 INDEF
  	   im006  3  2.0  1.300 INDEF
  	   im007  1  5.0  1.263 INDEF
  	   im008  3  1.0  1.270 INDEF
  	   im009  2  3.0  1.270 INDEF
  	   im010  1  2.0  1.030 INDEF
  	   im011  3  10.0  1.030 INDEF
  	   im012  1  30.0  1.093 INDEF
  	   im013  2  20.0  1.110 INDEF
  	   im014  3  10.0  1.110 INDEF
  <P>
  	   ... the user notices that standard 4 is missing a B
  	       observation and that the observations of standard 3
  	       are out of order and edits the file as follows
  <P>
  	   im001  1  3.0  1.150 INDEF
  	   im002  2  2.0  1.150 INDEF
  	   im003  3  2.0  1.140 INDEF
  	   im004  1  6.0  1.300 INDEF
  	   im005  2  4.0  1.300 INDEF
  	   im006  3  2.0  1.300 INDEF
  	   im007  1  5.0  1.263 INDEF
  	   im009  2  3.0  1.270 INDEF
  	   im008  3  1.0  1.270 INDEF
  	   im010  1  2.0  1.030 INDEF
  	   INDEF  2  INDEF  INDEF INDEF
  	   im011  3  10.0  1.030 INDEF
  	   im012  1  30.0  1.093 INDEF
  	   im013  2  20.0  1.110 INDEF
  	   im014  3  10.0  1.110 INDEF
  <P>
  	   ... the user quits the editor
  <P>
  	   ... MKIMSETS groups the image list prompting for a
  	       name for each image set
  <P>
  	   ... MKIMSETS enters the editor, displays the first few
  	       lines of the imsets file, and allows the user to
  	       correct any mistakes
  <P>
  	   STD1 :    im001  im002  im003
  	   STD2 :    im004  im005  im006
  	   STD3 :    im007  im009  im008
  	   STD4 :    im010  INDEF  im011
  	   STD5 :    im012  im013  im014
  <P>
  	   ... quit the editor
  </PRE>
  <P>
  <P>
  2. Create the image set file from the list of IRAF images associated with
  the APPHOT databases in example 1.  The images contain the image
  header keyword "<TT>f1pos</TT>" which specifies the filter id and which may assume
  the values "<TT>1,2,3</TT>" where "<TT>1,2,3</TT>" stand for "<TT>U,B,V</TT>". 
  Since the data for the individual stars was taken sequentially the user
  requests MKIMSETS to print out value of the sidereal time stored in the
  image header keyword "<TT>ST</TT>", and to sort on that
  parameter. The image title is also printed out as an image grouping
  aid to the user. It is placed last in the fields parameter because  any
  internal blanks in the title would otherwise confuse the sorting routine.
  <P>
  <PRE>
  	ph&gt; mkimsets *.imh "1,2,3" jan10.stdim input="images" \<BR>
  	    filter="f1pos" fields="ST,i_title" sort="ST"
  <P>
  	   ... MKIMSETS constructs the image list and sorts on
  	       the column containing the sidereal time
  <P>
  	   ... MKIMSETS enters the editor and lists the first
  	       few lines of the temporary image list file, the sidereal
  	       time is in column 3 and the image title containing
  	       some blanks is in column 4
  <P>
  	   im001  1  12:30:50.2   STD1 U filter
  	   im002  2  12:35:40.1   STD1 B
  	   im003  3  12:40:16.2   STD1 v filter
  	   im004  1  12:50:50.2   STD2
  	   im005  2  12:55:40.1   STD2 B
  	   im006  3  12:59:58.2   STD2 V
  	   im007  1  13:10:50.2   STD3 U
  	   im008  3  13:15:40.1   STD3 V
  	   im009  2  13:20:16.2   STD3 B
  	   im010  1  13:30:50.2   STD4 u
  	   im011  3  13:40:40.1   STD4 V
  	   im012  1  13:50:50.2   STD5 U
  	   im013  2  13:55:40.1   STD5 B
  	   im014  3  13:59:58.2   STD5 V
  <P>
  	   ... the user notices that standard 4 is missing a B
  	       observation and that the observations of standard 3
  	       are out of order and edits the file as follows
  <P>
  	   im001  1  12:30:50.2   STD1 U filter
  	   im002  2  12:35:40.1   STD1 B
  	   im003  3  12:40:16.2   STD1 v filter
  	   im004  1  12:50:50.2   STD2
  	   im005  2  12:55:40.1   STD2 B
  	   im006  3  12:59:58.2   STD2 V
  	   im007  1  13:10:50.2   STD3 U
  	   im009  2  13:20:16.2   STD3 B
  	   im008  3  13:15:40.1   STD3 V
  	   im010  1  13:30:50.2   STD4 u
  	   INDEF  2  INDEF        INDEF
  	   im011  3  13:40:40.1   STD4 V
  	   im012  1  13:50:50.2   STD5 U
  	   im013  2  13:55:40.1   STD5 B
  	   im014  3  13:59:58.2   STD5 V
  <P>
  	   ... the user quits the editor
  <P>
  	   ... MKIMSETS groups the edited image list prompting for a
  	       name for each image set
  <P>
  	   ... MKIMSETS enters the editor, displays the first few
  	       lines of the image set file and permits the
  	       user to correct any mistakes
  <P>
  	   STD1 :    im001  im002  im003
  	   STD2 :    im004  im005  im006
  	   STD3 :    im007  im009  im008
  	   STD4 :    im010  INDEF  im011
  	   STD5 :    im012  im013  im014
  <P>
  	   ... quit the editor
  <P>
  	   ... note that MKIMSETS did not save the output image list
  <P>
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  images.hselect,ptools.dump,mknobsfile,mkobsfile
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
