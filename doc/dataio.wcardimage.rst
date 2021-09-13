.. _wcardimage:

wcardimage — Convert text files to cardimage files
==================================================

**Package: dataio**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  wcardimage -- convert IRAF text files to card image files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  wcardimage infiles outfiles
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>textfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='textfile' Line='textfile'>
  <DD>A character string identifying the file (s) on disk to be processed.
  The string acts as a "<TT>template</TT>" so that multiple files can be pro-
  cessed.
  </DD>
  </DL>
  <DL>
  <DT><B>cardfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cardfile' Line='cardfile'>
  <DD>Name of the output tape device of the form "<TT>mta800</TT>" or "<TT>mta800[#]</TT>"
  or name of disk file (s). EOT and BOT are acceptable tape file numbers.
  The file number will be appended to
  the output file name in the case of multiple file disk output.
  </DD>
  </DL>
  <DL>
  <DT><B>new_tape</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='new_tape' Line='new_tape'>
  <DD>Specifies whether the output tape is blank or contains data.
  </DD>
  </DL>
  <DL>
  <DT><B>contn_string = "<TT>&gt;&gt;</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='contn_string' Line='contn_string = "&gt;&gt;"'>
  <DD>Character string which will be inserted at the beginning of
  card image lines which have been split from a single text line.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages of actions performed?
  </DD>
  </DL>
  <DL>
  <DT><B>detab = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='detab' Line='detab = yes'>
  <DD>Remove tabs?
  </DD>
  </DL>
  <DL>
  <DT><B>card_length = 80</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='card_length' Line='card_length = 80'>
  <DD>Number of columns per card.
  </DD>
  </DL>
  <DL>
  <DT><B>cards_per_blk = 50</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cards_per_blk' Line='cards_per_blk = 50'>
  <DD>Number of card images per physical record.
  </DD>
  </DL>
  <DL>
  <DT><B>ebcdic = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ebcdic' Line='ebcdic = no'>
  <DD>Translate ascii characters to ebcdic?
  </DD>
  </DL>
  <DL>
  <DT><B>ibm = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ibm' Line='ibm = no'>
  <DD>Translate ascii characters to ibm ebcdic?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  If multiple file disk output is requested, "<TT>.crd</TT>" is appended to the input
  file name. Oversize lines are split and prefixed by the string "<TT>&gt;&gt;</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Convert a set of IRAF text files to a set of blocked ASCII cardimage files
  on tape, replacing tabs with blanks and prefixing the leftover portions
  of oversize lines with "<TT>&gt;&gt;</TT>".
  <P>
  <PRE>
  <P>
  	cl&gt; wcardimage files* mtb1600[1]
  </PRE>
  <P>
  2. Convert a set of IRAF text files to a set of blocked EBCDIC cardimage files
  on tape, replacing tabs with blanks and prefixing the leftover portions
  of oversize lines with "<TT>&gt;&gt;</TT>".
  <P>
  	cl&gt; wcardimage files* mtb1600[1] eb+
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The card_length in bytes must be an integral number of chars.
  At present WCARDIMAGE can only handle lines with less than or equal to
  161 characters.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rcardimage
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
