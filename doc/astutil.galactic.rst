.. _galactic:

galactic — Convert ra, dec to galactic coordinates
==================================================

**Package: astutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  galactic -- convert between equatorial and galactic coordinates
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  galactic files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>The name of a file (or a file list or template) containing the coordinates
  to be converted.
  </DD>
  </DL>
  <DL>
  <DT><B>in_coords = "<TT>equatorial</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='in_coords' Line='in_coords = "equatorial"'>
  <DD>Type of input coordinates.  May be either "<TT>equatorial</TT>" (RA and DEC) or
  "<TT>galactic</TT>" (l and b).
  </DD>
  </DL>
  <DL>
  <DT><B>print_coords = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='print_coords' Line='print_coords = yes'>
  <DD>If <B>print_coords</B> = yes, the RA, DEC and epoch (as well as lII and bII) 
  will be listed on the output file.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Program <B>galactic</B> is used to convert between equatorial and
  galactic coordinates.  It converts in either direction based on the
  specified input coordinates.  Coordinates are read from the input file
  as RA and DEC or galactic longitude and latitude pairs, one pair per
  input line.  Each coordinate pair may optionally be followed by the
  epoch of the equatorial coordinates, in which case the coordinates are
  precessed to 1950.0 (the epoch of definition for the galactic center)
  before conversion for equatorial to galactic or to the specified epoch
  for galactic to equatorial.  Coordinates may be entered in either
  decimal or sexagesimal notation.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Convert the given RA and DEC coordinates to galactic coordinates.  When
  the epoch is specified as other than 1950.0, precess before converting.
  The lines input by the user are marked:
  <P>
  <PRE>
  	cl&gt; galactic STDIN 	         		[input]
  	12:30:10.12 10:18:27.5 1930.			[input]
    	12:30:10.12   10:18:27.5  1930.00     288.4695   72.2884
  	12:30 10:18					[input]
    	12:30:00.00   10:18:00.0  1950.00     287.4598   72.3202
  	12.5  10:18                                     [input]
    	12:30:00.00   10:18:00.0  1950.00     287.4598   72.3202
  	(eof=&lt;ctrl/z&gt;)					[input]
  </PRE>
  <P>
  2. The following is equivalent, except that coordinate input is taken from
  the file "<TT>coords</TT>", rather than from the terminal:
  <P>
  <PRE>
  	cl&gt; galactic coords 				[input]
    	12:30:10.12   10:18:27.5  1930.00     288.4695   72.2884
    	12:30:00.00   10:18:00.0  1950.00     287.4598   72.3202
    	12:30:00.00   10:18:00.0  1950.00     287.4598   72.3202
  </PRE>
  <P>
  3. If image headers contain the coordinates, in this case RA, DEC, and EPOCH,
  then one can get the galactic coordinates for the image by:
  <P>
  	cl&gt; hselect *.imh ra,dec,epoch yes | galactic STDIN
  <P>
  (Consult the help for the task <B>hselect</B> for information about selecting
  fields from image headers.)
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
