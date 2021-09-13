widstape — Convert ONEDSPEC spectra to IDSOUT text format
=========================================================

**Package: mtlocal**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>widstape (Mar85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.mtlocal</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>widstape (Mar85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>widstape</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  widstape -- Write a Cyber style IDSOUT tape
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  widstape idsout input records
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_idsout">idsout</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='idsout' Line='idsout'>
  <DD>The output file name to receive the card-image data. This may be a
  magtape specification (e.g. mta, mtb) or disk file name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input root file name for the spectra to be written
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The record string to be appended to the root name to create the image
  names of the spectra to be written.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_new_tape">new_tape = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='new_tape' Line='new_tape = no'>
  <DD>If set to yes, the tape is rewound and output begins at BOT. If no,
  output begins at EOT unless an explicit file specification is given
  as part of the magtape file name for parameter "<TT>idsout</TT>" (e.g. mta[2]).
  If idsout contains a file specification of [1], then writing begins
  at BOT regardless of the value for new_tape.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_block_size">block_size = 3200</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='block_size' Line='block_size = 3200'>
  <DD>The tape block size in bytes. This must be an integral factor of 80.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ebcdic">ebcdic = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ebcdic' Line='ebcdic = no'>
  <DD>The default character code is ASCII, but if this parameter is set to yes,
  the output character will be in EBCDIC.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The specified spectra are copied to the output file in a card-image format
  defined in the IPPS-IIDS/IRS Reduction Manual. Values from the extended
  image header are used to fill in the observational parameters.
  <P>
  The basic format consists of 4 - 80 byte header cards, 128 data cards
  having 8 data elements per card in 1PE10.3 FORTRAN equivalent format,
  and a trailing blank card for a total of 133 cards. 
  Thus spectra up to 1024 points may be contained in the IDSOUT format. 
  The format is outlined below:
  <P>
  <PRE>
   Line	Column	Type
      1	   1-5	Integer	  Record number within IDSOUT text file
  	  6-10	Integer	  Integration time
  	 11-25	Real	  Wavelength of first bin
  	 26-40	Real	  Dispersion
  	 41-45	Integer	  0 (Index of first pixel)
  	 46-50  Integer	  Line length - 1 (Index of last pixel)
  	 71-80	Integer	  UT time
      2	  1-10	Real	  Siderial time
  	 11-25	Real	  Right Ascension
  	 26-40	Real	  Declination
      3	 21-35	Real	  Hour Angle
  	 36-50	Real	  Air mass
  	 51-58	Integer	  UT date
  	 60-76	String	  Image title
  	 78-80	String	  END
      4	  1-64	String	  Record label
  	 78-80	String	  END
  5-132		Real	  1024 pixel values, 8 per line
    133			  Blank line
  </PRE>
  <P>
  The data of type real are in exponent format; i.e FORTRAN <TT>'E'</TT> format (1.234e3).
  <P>
  There are no special marks between spectral images, 
  and when multiple spectra are written with a single command, the first card
  of a subsequent spectrum may be within the same physical tape block
  as the last card of the previous spectrum. This assures that all tape
  blocks (except the very last one in the tape file) are all the same
  length.  A double end-of-mark is written after the last spectrum.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following example writes an IDSOUT format tape starting at the
  beginning of the tape.
  <P>
  	cl&gt; widstape mta nite1 1001-1200 new_tape+
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements__unix_vax_11_750">TIME REQUIREMENTS: UNIX/VAX 11/750</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS: UNIX/VAX 11/750'>
  <UL>
  Each spectrum of 1024 points requires about 2 second.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS: UNIX/VAX 11/750'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rcardimage, ridsout
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS: UNIX/VAX 11/750' 'SEE ALSO'  >
  
  </BODY>
  </HTML>