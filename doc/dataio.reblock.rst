.. _reblock:

reblock — Copy a binary file, optionally reblocking
===================================================

**Package: dataio**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  reblock -- copy a file to tape or disk with optional reblocking
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  reblock infiles outfiles file_list
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>infiles  </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='infiles' Line='infiles  '>
  <DD>The input file list or device name, e.g. "<TT>mta1600[2]</TT>" or "<TT>mta800</TT>", "<TT>file1</TT>",
  "<TT>file1,file2</TT>", or "<TT>@infiles</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>outfiles  </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outfiles' Line='outfiles  '>
  <DD>The list of output files or device name, e.g. "<TT>gemini!mtb</TT>", "<TT>out1</TT>",
  "<TT>out1,out2</TT>", or "<TT>@outfiles</TT>".
  If multiple file output to disk is requested,  and the specified number
  of output files is 1, the output file names will be generated
  by concatenating the tape file number (the input files are on tape) or
  a sequence number (the input files are on disk) onto the output file
  name.
  </DD>
  </DL>
  <DL>
  <DT><B>file_list</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list'>
  <DD>List of tape file numbers or ranges delimited by commas,
  e.g. "<TT>1-3,5_8</TT>".
  File_list is requested only if the magtape input device is specified.
  Files will be read in ascending order regardless of the ordering of the list.
  Reading will terminate silently if EOT is reached, thus a list such as
  "<TT>1-999</TT>" may be used to read all files on the tape.
  </DD>
  </DL>
  <DL>
  <DT><B>newtape  </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newtape' Line='newtape  '>
  <DD>If the output device is magtape, newtape specifies whether the tape is
  blank or contains data.
  Newtape is requested only if no tape file number is specified, e.g. "<TT>mta1600</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>outblock = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outblock' Line='outblock = INDEF'>
  <DD>Size of the output block  bytes.
  In the  default case and for disk output, the output block size is set to the
  file i/o disk default buffer size.
  </DD>
  </DL>
  <DL>
  <DT><B>inrecord = INDEF, outrecord = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='inrecord' Line='inrecord = INDEF, outrecord = INDEF'>
  <DD>The sizes of the input and output logical records in bytes.
  The default input and output record sizes are set equal to
  the input and output block sizes respectively. If inrecord &gt; outrecord,
  records are trimmed; if inrecord &lt; outrecord, records are padded; if
  inrecord = outrecord, records are simply counted. If only one of inrecord or
  outrecord is set, the undefined parameter defaults to the value of the
  other.
  </DD>
  </DL>
  <DL>
  <DT><B>skipn = 0    </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skipn' Line='skipn = 0    '>
  <DD>The number of input blocks (tape input) or records (disk input, size inrecord)
  to be skipped.
  </DD>
  </DL>
  <DL>
  <DT><B>copyn = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='copyn' Line='copyn = INDEF'>
  <DD>The number of input blocks (tape input) or records
  (disk input, size inrecord) to be copied. Copyn defaults to a very large number.
  </DD>
  </DL>
  <DL>
  <DT><B>byteswap = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='byteswap' Line='byteswap = no'>
  <DD>Swap every other byte. For example if byteswap is enabled, bytes 1 2 3 4 5 6
  would become bytes 2 1 4 3 6 5 on output.
  </DD>
  </DL>
  <DL>
  <DT><B>wordswap = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wordswap' Line='wordswap = no'>
  <DD>Swap every 4 bytes. For example if byteswap is enabled, bytes 1 2 3 4 5 6 7 8
  would become 4 3 2 1 8 7 6 5 on output.
  </DD>
  </DL>
  <DL>
  <DT><B>pad_block = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pad_block' Line='pad_block = no'>
  <DD>If pad_block is set, reblock pads trailing blocks until they are outblock
  bytes long, otherwise trailing blocks may be short.
  </DD>
  </DL>
  <DL>
  <DT><B>padchar  = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='padchar' Line='padchar  = 0'>
  <DD>Single character used to pad blocks or records.
  Padchar is only requested if pad_record or pad_block
  is set. If padchar equals one of the digits 0 through nine, records and
  blocks are padded with the face value of the character, otherwise the
  ASCII value is used.
  </DD>
  </DL>
  <DL>
  <DT><B>offset = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='offset' Line='offset = 0'>
  <DD>The number which added to the tape file number is appended to <I>outfiles</I>
  to produce the output file name. For example if file_list = "<TT>1-3</TT>", outfiles =
  "<TT>out</TT>" and offset = 100, the three files out101, out102, out103 would
  be produced rather than out001, out002 and out003.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes  </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes  '>
  <DD>Print messages about files, blocks copied etc.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  REBLOCK is a procedure to copy disk or tape resident files to
  disk or tape. Multiple input tape or disk files may be specified.
  If multiple files are output to disk, and only one output file name is
  specified, the output file names will be
  generated by concatenating the tape file number (the input files are on tape)
  or a sequence number (the input files are on disk) onto the output file name.
  The user may request magnetic tape output to begin at a specific file on
  tape, e.g. mta1600[5] in which case file five will be overwritten if it
  exists, or at BOT or EOT. If no file number is specified REBLOCK asks
  whether the tape is new or old and begin writing at BOT or EOT as
  appropriate.
  <P>
  Before beginning the copy, the user may request reblock to skip
  n (default 0) blocks (tape input) or logical records (disk input).
  The user can also specify that
  only n (default all) blocks (tape input) or records (disk input)
  are to be copied. Before the copy the data may be optionally word-swapped
  (default no) and/or byte-swapped (default no). If verbose is specified
  (default yes) reblock prints the input and output file names,
  the number of blocks read and written and the number of records read and
  written.
  <P>
  Reblock
  uses the default buffer sizes supplied by mtio and file i/o to determine the 
  maximum number of bytes which can be read in a single read call. For tapes
  this corresponds to the maximum number of bytes per block permitted by the
  device. Mtio will not read more than one block per read call. Therefore the
  actual number of bytes read will be less than or equal to the mtio buffer size.
  For disk files the default buffer size set by IRAF is a multiple of the
  disk block size. If the disk file is smaller than one block
  or the last block is partially full, the number of bytes read
  will be less than the default buffer size. All magtape and disk reads are
  done with the file i/o read procedure and a call to fstati determines the number
  of bytes actually read.
  <P>
  If all the defaults are set, a binary copy is performed.
  In tape to tape copies the block and record sizes are preserved,
  but the density may
  be changed by specifying the appropriate output file name e.g. mta800 or
  mta1600.
  Reblocking occurs in tape to disk transfers, if records, are trimmed,
  padded or counted, or if blocks are padded.
  If a disk to tape transfer is requested
  the output block size will be the default file i/o  buffer size.
  The last block in a file may be short. If uniform sized blocks are
  desired, pad_block must be set, in which case trailing partially filled
  blocks will be padded with padchar.
  <P>
  Logical records are distinguished from blocks (physical records).
  The input and output record sizes default to
  the size of the input and output blocks respectively.
  Logical records may be shorter or longer than the  block sizes.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Copy a magnetic tape preserving the record sizes but changing
  the density from 800 bpi to 1600 bpi.
  <P>
  <PRE>
  	cl&gt; reblock mtb800 mta1600[1] 1-999
  </PRE>
  <P>
  2. Reblock a magnetic tape changing the block size from 4000 bytes to 8000
  bytes and padding the last block.
  <P>
  <PRE>
  	cl&gt; reblock mtb1600 mta1600[1] 1-999 outb=8000 padb+
  </PRE>
  <P>
  3. Copy a series of disk fits files to tape
  <P>
  <PRE>
  	cl&gt; reblock @fitsfiles mta[1] outb=28800
  </PRE>
  <P>
  4. Trim the records of a disk file.
  <P>
  <PRE>
  	cl&gt; reblock infile outfile inrec=80 outrec=72
  </PRE>
  <P>
  5. Pad the records of a disk file with blanks.
  <P>
  <PRE>
  	cl&gt; reblock input output inrec=81 outrec=82 padchar=" "
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  t2d
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
