mtexamine — Examine the structure of a magnetic tape
====================================================

**Package: dataio**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mtexamine (Apr84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>dataio</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mtexamine (Apr84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mtexamine</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mtexamine -- examine the structure of magtape or a single disk file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mtexamine tape_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_tape_file">tape_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tape_file' Line='tape_file'>
  <DD>Tape or disk file, e.g. "<TT>mta1600[2]</TT>", "<TT>mta1600</TT>" or "<TT>data</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_file_list">file_list = "<TT>1-999</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list = "1-999"'>
  <DD>List of tape file numbers or ranges delimited by commas, e.g. "<TT>1-3,5-8</TT>".
  File_list is used only if no file number is given in tape_file.
  Files will be read in ascending order, regardless of the order of the list.
  Reading will terminate if EOT is reached, thus a list such as "<TT>1-999</TT>"
  may be used to read all the files on the tape. File_list is ignored is input
  is a single disk file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dump_records">dump_records = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dump_records' Line='dump_records = no'>
  <DD>Dump selected records?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rec_list">rec_list = "<TT>1-999</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rec_list' Line='rec_list = "1-999"'>
  <DD>List of tape record numbers or ranges to be dumped delimited by whitespace
  or commas e.g "<TT>1-3,4</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_swapbytes">swapbytes = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='swapbytes' Line='swapbytes = no'>
  <DD>Swap bytes?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_byte_chunk">byte_chunk = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='byte_chunk' Line='byte_chunk = 1'>
  <DD>The number of bytes which are considered as one output element.
  The maximum number of bytes permitted in byte_chunk is the number of
  bytes in a long integer on the host machine.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output_format">output_format = "<TT>o</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output_format' Line='output_format = "o"'>
  <DD>Permitted types are character(c), octal(o), hexadecimal (x), decimal (d)
  or unsigned decimal (u).  Character dumps are only permitted for byte_chunk = 1.
  Unless decimal format is specified, the data are dumped as
  unsigned integers.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  By default mtexamine determines the record structure of all files
  on a magnetic tape or a single disk file.
  Selected files can be dumped by setting the file_list parameter.
  Selected records can be dumped by setting the dump_record switch
  and entering a record list. The user can select the byte chunk
  and the output format for the dump.
  <P>
  Mtexamine can also be used to dump a single disk file. However the concept
  of a block is not well defined for disk files. Mtexamine defines a block
  to be one IRAF file io block which is usually some multiple of the machine
  block size.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Determine the record structure of a magnetic tape and send the result to
  the file tapedump.
  <P>
  <PRE>
  	cl&gt; mtexamine mtb1600 &gt; tapedump
  </PRE>
  <P>
  2. Dump the third tape file in octal bytes on the standard output.
  <P>
  <PRE>
  	cl&gt; mtexamine mtb1600[3] du+
  </PRE>
  <P>
  3. Dump the contents of the fifth record of the third tape file in ASCII
  characters on the standard output.
  <P>
  <PRE>
  	cl&gt; mtexamine mtb1600[3] du+ re=5 ou=c
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The IRAF magtape i/o routines do not permit data beyond a double EOF
  to be accessed. Therefore mtexamine cannot be used to examine tapes with
  embedded double EOFs.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rewind, allocate
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>