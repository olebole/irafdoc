fceval — Evaluate coordinates using the FITSCOORDS solutions
============================================================

**Package: longslit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>fceval (Aug03)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.twodspec.longslit</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>fceval (Aug03)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>fceval</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  fceval -- Evaluate coordinates using the FITCOORDS solutions
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  fceval input output fitnames
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input text file of pixel coordinates.  This may be "<TT>STDIN</TT>" to read
  coordinates from the terminal or pipe.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output text file of pixel coordinates and fitted coordinates.  This may
  be "<TT>STDOUT</TT>" to write coordinates to the terminal or pipe.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fitnames">fitnames  </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitnames' Line='fitnames  '>
  <DD>Names of the user coordinate maps to evaluate.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database = "<TT>database</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "database"'>
  <DD>Database containing the coordinate maps.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task transforms pixel coordinates to the world coordinates fit with
  FITCOORDS.  When there is no map for an axis the identify transform is
  used.  If there are more the one map for an axis the average of the mapped
  coordinates is output.  This is the same behavior as TRANSFORM.
  <P>
  The input file consists of two columns giving the x and y pixel values
  in the frame of the untransformed image data.  The output is a file
  with four columns giving the input x any y pixel values and the
  user coordinates fit by FITCOORDS.
  <P>
  Two typical uses for this task are to look up world coordinates for
  points in the untransformed data and to generate transformations using
  GEOMAP and GEOTRAN.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Evaluate a wavelength and slit position fit where the input pixel coordinates
  are entered interactively and the output is written to the terminal.
  <P>
  <PRE>
      cl&gt; fceval STDIN STDOUT arcfit,std
      1 1
      1. 1. 20.60425149463117 4202.47202514205
      60 1
      60. 1. 79.60425149463118 4203.316616448186
      1 512
      1. 512. 19.15606081299484 7356.089801036373
      60 512
      60. 512. 78.15606081299485 7355.042495319318
  </PRE>
  <P>
  In this case the first axis corresponds to the spatial dimension and
  the second to the dispersion dimension.  The arcfit was created using
  Angstroms and so the units of the last column is Angstroms.
  <P>
  2. One use of this task is to generate the inverse transformation from
  that produced by TRANSFORM.  The steps are: 1) produce a grid of
  coordinates using LISTPIX and FCEVAL, 2) convert the user coordinates to
  pixel coordinates in the transformed data using WCSCTRAN, 3) fit a
  transformation using GEOMAP, and 4) transform the data with GEOTRAN.
  <P>
  <PRE>
      cl&gt; listpix orig[*:5,*:5] wcs=physical verb- |
      &gt;&gt;&gt; fceval STDIN STDOUT arcfit,std |
      &gt;&gt;&gt; wcsctran STDIN coords trans world logical columns="3 4"
      cl&gt; geomap coords geomap.db 1 61 1 512
      cl&gt; geotran trans origNEW geomap.db coords flux+
  </PRE>
  <P>
  This example uses pipes to eliminate intermediate files.  But these
  files can be useful for understanding the process.  LIXTPIX is used to
  generate a grid of points with some subsampling.  Be sure to use "<TT>physical</TT>"
  for the coordinate system otherwise the grid of x and y values will be
  for the subsection.  The order of the columns will be appropriate for
  GEOMAP to compute the inverse transformation.  By reversing the order
  of the columns one could generate a transformation similar to that
  produced by TRANSFORM in order to use features in GEOTRAN not provided
  by TRANSFORM.  However, the world coordinate system information will
  not be automatically set.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fitcoords, transform, geomap, geotran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>