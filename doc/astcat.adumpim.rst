adumpim — Image survey access debugging task
============================================

**Package: astcat**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>adumpim (Mar00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>astcat</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>adumpim (Mar00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>adumpim</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  adumpim -- query an image survey and capture the results in a fits file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  adumpim imsurvey output ra dec size
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_imsurvey">imsurvey</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imsurvey' Line='imsurvey'>
  <DD>The name of the image survey to be queried. Image survey names have the form
  survey@site, e.g. "<TT>dss2@cadc</TT>". The image survey address and query format are
  stored in a record called imsurvey in the image survey configuration file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The name of the output query results file. The query results are written
  to the output file without modification, but at present they are implicitly
  assumed to be in fits format. Users should append a "<TT>.fits</TT>" extension to
  the output file name if they wish the output file to be visible to IRAF
  as a FITS image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ra">ra  </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra' Line='ra  '>
  <DD>The right ascension of the field center in the units expected by the image
  survey query. The value of ra replaces the default value of the ra query
  parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dec">dec  </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dec' Line='dec  '>
  <DD>The declination of the field center in the units expected by the image
  survey query.  The value of dec replaces the default value of the dec query
  parameters. It may be necessary to add or remove a leading + sign from
  in order to make the query function correctly.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_size">size</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='size' Line='size'>
  <DD>The field size in units expected by the image survey query. The value of size
  replaces the default value of the width, xwidth, ywidth, hwidth, hxwidth,
  and hywidth query
  parameters as appropriate.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imdb">imdb = "<TT>)_.imdb</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imdb' Line='imdb = ")_.imdb"'>
  <DD>The image survey configuration file. The name of the image survey configuration
  file defaults to the value of the imdb package parameter.  The default
  configuration file is "<TT>astcat$lib/imdb.dat</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Adumpim is a simple image survey access debugging task which queries the
  image survey <I>imsurvey</I>, captures the results, and writes them
  to the file <I>output</I> without modification.
  <P>
  The user must supply values for the query parameters ra, dec, and one or
  more of the size query parameters width, xwidth, ywidth, hwidth, xhwidth,
  or yhwidth, by
  specifying appropriate values for the <I>ra</I>, <I>dec</I>, and <I>size</I>
  parameters in the units expected by the image survey query. These values are
  treated as strings and passed directly to the image survey query without
  coordinate transformations or units conversions.
  <P>
  The image survey configuration file <I>imdb</I> contains a record for each
  supported <I>imsurvey</I>. This record contains the image survey address,
  the query format, and the output format. The default image survey configuration
  file is "<TT>astcat$lib/imdb.dat</TT>".
  <P>
  The output of adumpim can be used to refine the image survey record in the
  image survey configuration file.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List the supported image surveys, select an image survey to query, make
  the query and capture the results. The aslist task is used  to list
  the supported image surveys and the query and output formats for the selected
  image survey as shown below. The query format tells the user that the input
  ra and dec must be in sexagesimal hours and degrees and in the J2000
  coordinate system that the size parameter is a radius in minutes.
  <P>
  <PRE>
  cl&gt; aslist *
  dss2@cadc
  <P>
  cl&gt; aslist dss2@cadc verb+
  Scanning image surveys database astcat$lib/imdb.dat
  Listing the supported image surveys
  dss2@cadc
  wcs dss
  nwcs 10
        wxref INDEF INDEF d pixels
        wyref INDEF INDEF d pixels
        wxmag INDEF 1.009 d arcsec/pixel
        wymag INDEF 1.009 d arcsec/pixel
        wxrot INDEF 180.0 d degrees
        wyrot INDEF 0.0 d degrees
       wraref OBJCTRA INDEF d hms
      wdecref OBJCTDEC INDEF d dms
        wproj INDEF tan c INDEF
      wsystem INDEF J2000 c INDEF
  nkeys 13
      observat INDEF Palomar c INDEF
      esitelng INDEF +116:51:46.80 d degrees
      esitelat INDEF +33:21:21.6 d degrees 
      esitealt INDEF 1706 r meters
       esitetz INDEF 8 r INDEF
       emjdobs INDEF INDEF c INDEF
      edatamin INDEF INDEF r ADU
      edatamax INDEF INDEF r ADU
         egain INDEF INDEF r e-/ADU
      erdnoise INDEF INDEF r e-
       ewavlen INDEF INDEF r angstroms
         etemp INDEF INDEF r degrees
        epress INDEF INDEF r mbars
  <P>
  cl&gt; adumpim dss2@cadc m51.fits 13:29:53.27 +47:11:48.4 10.0
  <P>
  cl&gt; imheader m51.fits
  <P>
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
  aslist, agetim
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>