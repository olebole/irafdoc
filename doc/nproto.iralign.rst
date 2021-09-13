.. _iralign:

iralign — Align the mosaiced image produced by irmosaic
=======================================================

**Package: nproto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  iralign -- align the elements of the mosaiced image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  iralign input output database coords
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The mosaiced image written by IRMOSAIC.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The output aligned image.
  </DD>
  </DL>
  <DL>
  <DT><B>database</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The database file written by IRMOSAIC.
  </DD>
  </DL>
  <DL>
  <DT><B>coords</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords'>
  <DD>If <I>alignment</I> = "<TT>coords</TT>", then <B>coords</B> is
  a text file containing the x and y coordinates, measured in the input
  mosaiced image, of reference objects common
  to adjacent subrasters in the input mosaiced
  image. The reference coordinates are written with the following format:
  line 1) the x and y coordinates of an object in the any subraster,
  line 2) the x and y coordinates of the same object in any adjacent subraster,
  line 3) the x and y coordinates of another object in the any subraster,
  line 4) the x and y coordinates of the same object in any adjacent subraster,
  etc.
  If <I>alignment</I> = "<TT>file</TT>", then <B>coords</B> is a text file containing
  the x and y shifts in columns 1 and 2 respectively,
  of each subraster relative to the reference subraster, in the order
  in which the subrasters were written into the mosaiced input image.
  This option can be used to make fine adjustments to the output aligned image
  by manually editing the computed shifts and rerunning
  IRALIGN with the new shifts.
  </DD>
  </DL>
  <DL>
  <DT><B>xshift</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xshift' Line='xshift'>
  <DD>The x shift in pixels used if <I>alignment</I> = "<TT>shifts</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>yshift</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='yshift' Line='yshift'>
  <DD>The y shift in pixels used if <I>alignment</I> = "<TT>shifts</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>alignment = "<TT>coords</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='alignment' Line='alignment = "coords"'>
  <DD>The method of aligning the subraster.
  <DL>
  <DT><B>coords</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='coords' Line='coords'>
  <DD>The x and y positions of the reference points common to adjacent subrasters
  in the input mosaiced image are listed in a text file as described
  under the help for the  <I>coords</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>shifts</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='shifts' Line='shifts'>
  <DD>The x and y shifts of each subraster with respect to its neighbour are
  set to <I>xshift</I> and <I>yshift</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>file</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='file' Line='file'>
  <DD>The x and y  shifts of each input subraster with respect to the
  reference subraster image are listed in a text file as described
  under the help for the <I>coords</I> parameter.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>nxrsub = INDEF, ls nyrsub = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxrsub' Line='nxrsub = INDEF, ls nyrsub = INDEF'>
  <DD>The column and row index of the reference subraster.
  The default reference subraster is the central subraster.
  </DD>
  </DL>
  <DL>
  <DT><B>xref = 0, yref = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xref' Line='xref = 0, yref = 0'>
  <DD>The x and y offset of the reference
  subraster in the output aligned image.
  By default the reference subraster occupies the same position in
  the output image that it does in the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>trimlimits = "<TT>[1:1,1:1]</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trimlimits' Line='trimlimits = "[1:1,1:1]"'>
  <DD>The number of columns or rows to trim off each edge of each input subraster
  before inserting it in the output image, specified in image section notation.
  The default action is to trim 1 column or line at each edge of the subraster.
  </DD>
  </DL>
  <DL>
  <DT><B>nimcols = INDEF, nimlines = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nimcols' Line='nimcols = INDEF, nimlines = INDEF'>
  <DD>The number of columns and lines in the output image. The defaults are  the
  number of columns and lines in the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>oval = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oval' Line='oval = INDEF'>
  <DD>The value of undefined pixels in the output image. The default is the value
  stored in the database file written by IRMOSAIC.
  </DD>
  </DL>
  <DL>
  <DT><B>interpolant = linear</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interpolant' Line='interpolant = linear'>
  <DD>The type of interpolant used to shift the subrasters. The options are:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Nearest neighbour interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B>linear</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Bilinear interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B>poly3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly3' Line='poly3'>
  <DD>Bicubic polynomial interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B>poly5</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly5' Line='poly5'>
  <DD>Biquintic polynomial interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B>spline3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD>Bicubic spline interpolation.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages on the terminal describing the progress of the task?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  IRALIGN takes the mosaiced image <I>input</I> and database
  <I>database</I> files
  written by IRMOSAIC, and a list of reference object
  coordinates <I>coords</I> created by the user, and writes
  an output image <I>output</I> in which all the subrasters are aligned
  with respect to a reference subraster.
  <P>
  If <I>alignment</I> = "<TT>coords</TT>", IRALIGN accumulates the relative shifts
  between adjacent subrasters defined by the data in <I>coords</I>,
  into a total shift for each subraster with respect to the reference subraster.
  Relative shifts defined for non-adjacent subrasters are ignored.
  For those subrasters which have no relative shift information,
  IRALIGN makes a best guess at the relative x and y shifts
  based on the relative x andy shifts of nearby subrasters
  which do have relative shift information.  If the x and y shifts
  are sufficiently uniform over the whole input image the user may set
  <I>alignment</I> to  "<TT>shifts</TT>" and supply values for
  <I>xshift</I> and <I>yshift</I>.
  Alternatively the total shifts may be read directly from the  file <I>coords</I>
  if <I>alignment</I> = "<TT>file</TT>".
  <P>
  Coordinate lists for the <I>alignment</I> = "<TT>coords</TT>" option,
  may be generated interactively using the RIMCURSOR, 
  or APPHOT package CENTER and APSELECT tasks. For example a coordinate list
  written by RIMCURSOR for a 
  4 by 4 mosaic of 51 by 51 pixel square images containing a single
  reference object common to all the subrasters might look like the following.
  <P>
  <PRE>
  41.3   42.6     1 \40 	# coordinates of ref object in subraster 1
  62.0   38.5	1 \40   # coordinates of ref object in subraster 2
  41.3   42.6     1 \40   # coordinates of ref object in subraster 1
  38.1   95.8     1 \40   # coordinates of ref object in subraster 3
  62.0   38.5     1 \40   # coordinates of ref object in subraster 2
  70.3   89.0     1 \40   # coordinates of ref object in subraster 4
  38.1   95.8     1 \40   # coordinates of ref object in subraster 3
  70.3   89.0     1 \40   # coordinates of ref object in subraster 4
  </PRE>
  <P>
  In this example subrasters 1 and 2 are in the lower-left and
  lower-right hand corners of
  the mosaiced image respectively, while subrasters 3 and 4 are in the
  upper-left and upper- right hand corner of the mosaiced image.
  Any number of reference objects may be used.
  <P>
  The subrasters are inserted into the output image using the
  interpolation scheme defined by
  <I>interpolant</I>, and aligned with reference to the subraster defined
  by <I>nxrsub</I> and <I>nyrsub</I>, using the shifts defined by
  the data in the file <I>coords</I> or defined by <I>xshift</I> and
  <I>yshift</I>. Subrasters are inserted into the output image in the order
  they were placed in the original mosaic with pixels in the most recently
  placed subrasters replacing those in earlier placed ones in the overlap regions.
  Undefined pixels in the output image
  are assigned the value <I>oval</I>. The position of the reference subraster
  in the output image may be adjusted by setting the offset parameters
  <I>xref</I> and <I>yref</I>. The edges of each subraster may be trimmed
  before insertion into the output image by setting the <I>trimlimits</I>
  parameter.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Align an 8 by 8 mosaic with respect to subraster 6, 5.
  <P>
  <PRE>
      pr&gt; iralign mosaic mosaic.al mosaic.db coords nxrsub=6 \<BR>
  	nyrsub=5
  </PRE>
  <P>
  2. Align an 8 by 8 mosaic as in example 1 above but shift the position of the
  reference subraster in the output image by 2 pixels in x and 3 pixels
  in y.
  <P>
  <PRE>
      pr&gt; iralign mosaic mosaic.al mosaic.db coords nxrsub=6 \<BR>
  	nyrsub=5 xref=2 yref=3
  </PRE>
  <P>
  3. Align an 8 by 8 mosaic as 1 above but trim 2 rows and columns off
  of each input subraster before inserting it into the output image.
  <P>
  <PRE>
      pr&gt; iralign mosaic mosaic.al mosaic.db coords nxrsub=6 \<BR>
  	nyrsub=5 trimlimits="[2:2,2:2]"
  </PRE>
  <P>
  4. Rerun the above example saving the verbose output in a file. Use the 
  PROTO package FIELDS task to select the xshift, yshift and intensity
  shift fields, edit the shifts manually and rerun IRALIGN with the
  new shifts.
  <P>
  <PRE>
      pr&gt; iralign mosaic mosaic.al mosaic.db coords nxrsub=6 \<BR>
  	nyrsub=5 trimlimits="[2:2,2:2]" &gt; shifts1
  <P>
      pr&gt; fields shifts1 3,4,6 &gt; shifts2
  <P>
      pr&gt; edit shifts2
  <P>
  	... make whatever changes are desired
  <P>
      pr&gt; iralign mosaic mosaic.al.2 mosaic.db shifts2 align=file \<BR>
  	nxrsub=6 nyrsub=5 trimlimits="[2:2,2:2]"
  </PRE>
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
  irmosaic, apphot.center, apphot.apselect, irmatch1d, irmatch2d
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
