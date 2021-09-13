precess — Precess a list of astronomical coordinates
====================================================

**Package: astutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>precess (Oct87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.astutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>precess (Oct87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>precess</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  precess -- general astronomical coordinate precession
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  precess files startyear endyear
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>The name of a file (or a file list or template) containing the coordinates
  to be precessed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_startyear">startyear</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='startyear' Line='startyear'>
  <DD>The default equinox of the input coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_endyear">endyear</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='endyear' Line='endyear'>
  <DD>The default target year to which the coordinates will be precessed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_stdepoch">stdepoch = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='stdepoch' Line='stdepoch = 0'>
  <DD>If nonzero, coordinates will be output precessed to both <B>endyear</B>
  and the specified standard epoch.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Coordinates are read from the input file as RA and DEC pairs,
  one pair per input line.  Each coordinate pair may optionally be followed
  by the equinox of the input coordinates (if different from the default)
  and the epoch of the output coordinates.
  Coordinates may be entered in either decimal or sexagesimal notation.
  The given coordinates are rotated according to the
  precession rates to the requested year and printed on the standard output.
  Basic data is taken from the Explanation to the American Ephemeris.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Precess coordinate entered interactively from 1950 to 1990, except where
  the dates are specified otherwise on the command line (lines input by the
  user are marked:
  <P>
  <PRE>
  	cl&gt; precess STDIN 1950 1990			[input]
  	12:30:10.12 10:18:27.5				[input]
  	  12:32:11.79   10:05:13.09  1990.0
  	12:30 10:18					[input]
  	  12:32:01.68   10:04:45.51  1990.0
  	12:30 -20 1900					[input]
  	  12:34:42.89  -20:29:46.29  1990.0
  	12:30 -20 1900 2000				[input]
  	  12:35:14.40  -20:33:04.40  2000.0
  	(eof=&lt;ctrl/z&gt;)					[input]
  </PRE>
  <P>
  The following is equivalent, except that coordinate input is taken from
  the file "<TT>coords</TT>", rather than from the terminal:
  <P>
  <PRE>
  	cl&gt; precess coords 1950 1990			[input]
  	  12:32:11.79   10:05:13.09  1990.0
  	  12:32:01.68   10:04:45.51  1990.0
  	  12:34:42.89  -20:29:46.29  1990.0
  	  12:35:14.40  -20:33:04.40  2000.0
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
  </BODY>
  </HTML>