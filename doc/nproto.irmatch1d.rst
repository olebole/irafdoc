irmatch1d — Align and intensity match image produced by irmosaic (1D)
=====================================================================

**Package: nproto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>irmatch1d (Jan90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.nproto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>irmatch1d (Jan90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>irmatch1d</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  irmatch1d -- align and match the elements of the mosaiced image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  irmatch1d input output database coords
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The mosaiced image to be aligned. This image must have been produced by
  the IRMOSAIC task and have an accompanying database file specified by
  <I>database</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The aligned image produced by IRMATCH1D.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The database file from the IRMOSAIC task.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_coords">coords</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords'>
  <DD>If <I>alignment</I> = "<TT>coords</TT>", then <B>coords</B> is
  a text file listing the coordinates of objects in the input
  image one object per line in the following
  format: 1) the x and y coordinates of the object in the first subraster
  2) the x and y coordinates of the same object in the second subraster
  3) the x and y coordinates of the next object in the first subraster
  etc.
  If <I>alignment</I> = "<TT>file</TT>", then <B>coords</B> is a text file listing
  the x, y and intensity shifts in columns 1, 2 and 3 respectively,
  of each input subraster relative to the reference subraster. The
  most common use of this option is to make fine adjustments by hand
  to the output of IRMATCH1D by editing the computed shifts slightly and
  rerunning IRMATCH1D with the new shifts.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xshift">xshift</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xshift' Line='xshift'>
  <DD>The x shift in pixel units if <I>alignment</I> = "<TT>shifts</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_yshift">yshift</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='yshift' Line='yshift'>
  <DD>The y shift in pixel units if <I>alignment</I> = "<TT>shifts</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_alignment">alignment = "<TT>coords</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='alignment' Line='alignment = "coords"'>
  <DD>The method of aligning the subraster.
  <DL>
  <DT><B><A NAME="l_coords">coords</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='coords' Line='coords'>
  <DD>The x and y positions of the marker points are listed in a file in the
  format specified by the <I>coords</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_shifts">shifts</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='shifts' Line='shifts'>
  <DD>The x and y shifts of a subraster with respect to its neighbour are
  set to <I>xshift</I> and <I>yshift</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_file">file</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='file' Line='file'>
  <DD>The x,  y  and intensity shifts of each input subraster with respect to the
  reference subraster image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_match">match = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='match' Line='match = "*"'>
  <DD>Match intensities using the overlap region between adjacent subrasters. The
  median intensity is computed in the overlap region
  and the intensity scale of the current subraster is scaled to that of
  the previous subraster. Intensities are matched in one dimension in the order
  in which they
  are placed in the output image. The default is match everything.
  Those subrasters to be matched must be listed by number. For example to
  match intensities for subrasters 1 to 5 and 10 to 20 set match = "<TT>1-5,10-20</TT>".
  To match all the subrasters set match = "<TT>1-999</TT>" or match="<TT>*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nxrsub">nxrsub = INDEF, ls nyrsub = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxrsub' Line='nxrsub = INDEF, ls nyrsub = INDEF'>
  <DD>The column and line index of the reference subraster.
  This will default to the central subraster.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xref">xref = 0, yref = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xref' Line='xref = 0, yref = 0'>
  <DD>The x and y offset of the position of the reference subraster in the
  output image. The default action is to place the reference subraster
  in the same position in the output image as it has in the input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_trimlimits">trimlimits = "<TT>[1:1,1:1]</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trimlimits' Line='trimlimits = "[1:1,1:1]"'>
  <DD>The number of columns and rows to be trimmed off each edge of the
  input subraster before it is inserted in the output image in section
  notation. The default is to trim 1 column or row in each direction.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nimcols">nimcols = INDEF, ls nimlines = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nimcols' Line='nimcols = INDEF, ls nimlines = INDEF'>
  <DD>The number of columns and rows in the output image. The default is the
  number of columns and rows in the input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_oval">oval = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oval' Line='oval = INDEF'>
  <DD>The value of undefined pixels in the output image. The default is the value
  in the database file from IRMOSAIC.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interpolant">interpolant = linear</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interpolant' Line='interpolant = linear'>
  <DD>The type of interpolant used to shift the subrasters. The options are:
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Nearest neighbour interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_linear">linear</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Bilinear interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_poly3">poly3</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly3' Line='poly3'>
  <DD>Bicubic polynomial interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_poly5">poly5</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly5' Line='poly5'>
  <DD>Biquintic polynomial interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_spline3">spline3</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD>Bicubic spline interpolation.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print messages on the terminal describing the progress of the task.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  IRMATCH1D takes the mosaiced image <I>input</I>, the database file <I>database</I>
  generated by IRMOSAIC and a list of coordinates <I>coords</I> and computes
  an output image <I>output</I> in which all the individual subrasters are aligned.
  If <I>alignment</I> = "<TT>coords</TT>", IRMATCH1D accumulates the relative shifts
  between adjacent subrasters
  into a total shift with respect to the reference subraster. Shifts which
  do not correspond to adjacent subrasters are ignored.
  For subrasters which have no direct shift information, IRMATCH1D makes a best
  guess at the x and y shift based on the shifts of nearby subrasters which
  do have direct shift information.
  If the x and y shifts are sufficiently uniform over the whole input image
  the user may set <I>alignment</I>
  = shifts and input values of <I>xshift</I> and <I>yshift</I>.
  Alternatively the shifts may be read from the file <I>coords</I> if
  <I>alignment</I> = "<TT>file</TT>".
  <P>
  Coordinate lists may be generated interactively on the Sun workstations
  using the IRAF imtool facility and centered using the APPHOT CENTER
  and APSELECT tasks.
  <P>
  The subrasters are inserted into the output image
  using the interpolation scheme defined by
  <I>interpolant</I> and is made with reference to the subraster defined
  by <I>nxrsub</I> and <I>nyrsub</I>, using the shifts defined by
  the coordinates in the file <I>coords</I> or defined by <I>xshift</I> and
  <I>yshift</I>. Subrasters are placed in the output image in the order
  they were inserted into the original mosaic with pixels in the most
  recently placed subrasters replacing those placed earlier in the overlap
  regions. Undefined pixels in the output image
  are given the value <I>oval</I>. The position of the reference image in the
  output image can be adjusted by setting the parameters <I>xref</I> and
  <I>yref</I>. The edges of each subraster may be trimmed before
  insertion into the output image by setting the <I>trimlimits</I> parameter.
  <P>
  Intensities of adjacent subrasters can be matched using the <I>match</I>
  parameters. At present matching is done by computing the median in the
  overlap region between adjacent subrasters and applying difference in
  these two numbers to the subraster in question. Intensity matching is
  done in one dimension  only with the direction of matching following
  the order that the individual subrasters were inserted into the mosaic.
  For example if IRMOSAIC was run with <I>corner</I> = "<TT>ll</TT>", <I>direction</I>
  ="<TT>row</TT>" and <I>raster</I> = "<TT>no</TT>", then the matching would start in the
  lower-left corner, proceed along the first row, move to the star of the
  second row and so on.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Align an 8 by 8 mosaic with respect to subraster 6, 5.
  <P>
  <PRE>
      pr&gt; irmatch1d mosaic mosaic.al mosaic.db coords nxrsub=6 \<BR>
  	nyrsub=5
  </PRE>
  <P>
  2. Align an 8 by 8 mosaic as 1 above but shift the position of the
  reference subraster in the output image by 2 pixels in x and 3 pixels
  in y.
  <P>
  <PRE>
      pr&gt; irmatch1d mosaic mosaic.al mosaic.db coords nxrsub=6 \<BR>
  	nyrsub=5 xref=2 yref=3
  </PRE>
  <P>
  3. Align an 8 by 8 mosaic as 1 above but trim 2 rows and columns off
  of each input image before inserting into the output image.
  <P>
  <PRE>
      pr&gt; irmatch1d mosaic mosaic.al mosaic.db coords nxrsub=6 \<BR>
  	nyrsub=5 trimlimits="[2:2,2:2]"
  </PRE>
  <P>
  4. Rerun the above example saving the verbose output in a file. Use the 
  PROTO package fields task to select the xshift, yshift and intensity
  shift fields, edit the shifts slightly and rerun irmatch1d with the
  new shifts.
  <P>
  <PRE>
      pr&gt; irmatch1d mosaic mosaic.al mosaic.db coords nxrsub=6 \<BR>
  	nyrsub=5 trimlimits="[2:2,2:2]" &gt; shifts1
  <P>
      pr&gt; fields shifts1 3,4,6 &gt; shifts2
  <P>
      pr&gt; edit shifts2
  <P>
  	... make whatever changes are desired
  <P>
      pr&gt; irmatch1d mosaic mosaic.al mosaic.db shifts2 align=file \<BR>
  	nxrsub=6 nyrsub=5 trimlimits="[2:2,2:2]"
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
  irmosaic, iralign, irmatch2d, apphot.center, apphot.apselect
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>