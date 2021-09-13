.. _rtar:

rtar — Read a TAR format archive file
=====================================

**Package: softools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rtar -- read TAR format archive file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rtar [ flags ] [ archive ] [ after ] [ files ]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>-a</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-a'>
  <DD>Advance to the archive file named by the <I>after</I> argument before
  performing the main operation.  The extract or list operation will begin with
  the file <I>after</I> and continue to the end of the archive.
  </DD>
  </DL>
  <DL>
  <DT><B>-b</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-b'>
  <DD>Output only binary byte stream files.  By default, <I>rtar</I> outputs text
  files in the host system textfile format.  The conversion from the byte stream
  <I>tar</I> format to host textfile format may involve modification of the
  file, e.g., conversion from ASCII to EBCDIC.  A binary extraction copies
  the file to disk without modification.
  </DD>
  </DL>
  <DL>
  <DT><B>-d</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-d'>
  <DD>Print detailed information about what <I>rtar</I> is doing.
  </DD>
  </DL>
  <DL>
  <DT><B>-e</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-e'>
  <DD>Extract the entire contents of the tape <I>excluding</I> the files or directories
  listed in <I>files</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>-f filename</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-f filename'>
  <DD><I>Rtar</I> uses the first filename argument as the host filename of the
  archive instead of reading from <I>stdin</I>.   Magtape devices should be
  specified using the host device name, e.g., "/dev/nrmt8"<TT> or </TT>"MSA0"<TT>.
  Since <I>rtar</I> is a host level program and does not read the IRAF tapecap
  file, IRAF device names such as "<TT>mta</TT>" cannot be used.
  </DD>
  </DL>
  <DL>
  <DT><B>-l</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-l'>
  <DD>Do not try to resolve file links by a disk to disk file copy.  By default,
  if file A appears in the archive as a link to file B,
  <I>rtar</I> trys to resolve the link by performing a disk to disk copy of
  file B to A.  This is valid providing file B was present in the archive and
  has already been extracted.  If the <B>l</B> flag is present linked files
  will not be extracted.
  </DD>
  </DL>
  <DL>
  <DT><B>-m</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-m'>
  <DD>Do not restore the file modify time.
  </DD>
  </DL>
  <DL>
  <DT><B>-n</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-n'>
  <DD>Do not strip trailing blank lines from text files read from the tape.
  The default is to strip any blank lines at the ends of files.
  This is necessary when the file was written by <I>wtar</I> on a system
  like VMS, where the size of the file is not known before it has been
  read.  The <I>wtar</I> utility must guess at the final size and pad the
  file at the end with spaces to ensure that the size of the file actually
  written agrees with the file header.
  </DD>
  </DL>
  <DL>
  <DT><B>-o</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-o'>
  <DD>Omit binary files when performing the extraction.  A binary file is any
  file containing ASCII values other than 040 through 0176 (the printable
  ASCII characters), tab, or newline in the first 512 byte block of the file.
  </DD>
  </DL>
  <DL>
  <DT><B>-p pathprefix</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-p pathprefix'>
  <DD>When creating directories and files from the pathnames recorded in the archive,
  omit the given path prefix if it matches the pathname given in the archive.
  This feature is used to relocate directories, or to read tar archives
  containing absolute pathnames.  For example, given "<TT>-p /usr/</TT>", the archive
  pathname "/usr/me/file"<TT> would be written to the file </TT>"me/file"<TT>.
  </DD>
  </DL>
  <DL>
  <DT><B>-r</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-r'>
  <DD>The extracted file replaces any existing file of the same name, i.e.,
  <I>rtar</I> performs a delete before creating the extracted file.
  </DD>
  </DL>
  <DL>
  <DT><B>-t</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-t'>
  <DD>The names of the specified files are listed each time they occur on
  the tape.  If no <I>files</I> argument is given, all of the names on the tape
  are listed.
  </DD>
  </DL>
  <DL>
  <DT><B>-u</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-u'>
  <DD>Do not attempt to restore the owner and group identification of each file.
  </DD>
  </DL>
  <DL>
  <DT><B>-v</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-v'>
  <DD>Print more information about the tape entries than just their names.
  The verbose file list format gives the file permissions, the link flag
  (zero if there were no links to the file), the owner and group identification
  numbers of the file on the system that wrote the archive, the file size in
  bytes, the date of last modification of the file, and the file name.
  </DD>
  </DL>
  <DL>
  <DT><B>-x</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-x'>
  <DD>The named files are extracted from the tape.  If the named file
  matches a directory whose contents had been written onto the tape, this
  directory is (recursively) extracted.  The owner, modification time, and mode
  are restored (if possible).  If no file argument is given, the entire content
  of the tape is extracted.  Note that if multiple entries specifying the same
  file are on the tape, the last one overwrites all earlier.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Rtar</I> reads multiple files from a UNIX <I>tar</I> format file,
  restoring the files to disk on the local host machine.
  Output filenames are mapped according to the IRAF filenaming conventions
  of the local host operating system.
  <P>
  <I>Rtar</I>'s actions are controlled by the <I>flags</I> argument. 
  <I>Flags</I> consists of a minus sign followed by a string of characters
  containing any combination of the function flags described below.
  Other arguments to <I>rtar</I> are the name of the archive file to be read,
  the name of the file on the archive at which reading is to begin,
  and the names of the files or directories to be read or to be excluded
  from the read.  In all cases, appearance of a directory name refers to
  the files and (recursively) subdirectories of that directory.
  <P>
  All <I>rtar</I> filename arguments are IRAF virtual filenames (or host
  filenames), except the prefix strings, which pertain to the tape format and
  hence are UNIX pathnames.  Magtape devices must be specified using a host
  physical or logical device name (i.e., IRAF device names like "<TT>mta</TT>" will not
  work).
  <P>
  If the input archive file is a tape the blocksize must be a multiple
  of 512 bytes, with a maximum blocksize of 10240 bytes.  Each archived file
  occupies an integral number of 512 byte blocks in the archive (this is
  required by the <I>tar</I> format).
  <P>
  Filenames appearing in the file list are interpreted as prefix strings,
  i.e., a match occurs if the given string is a prefix of an actual filename
  in the archive.  If the last character in the <I>files</I> filename is
  a <B>$</B> then an exact match is required (excluding the $ meta-character).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Diagnostics</H3>
  <! BeginSection: 'DIAGNOSTICS'>
  <UL>
  A file read error occurring while reading the archive file is fatal unless
  caught and corrected by the host system.
  File header checksum errors result in skipping of the archive file
  currently being read, with execution continuing with the next archive
  file if possible.
  File write errors on the output file are reported but do not cause
  termination of <I>rtar</I>.  The output file being written will be corrupted.
  </UL>
  <! EndSection:   'DIAGNOSTICS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Since <I>rtar</I> is a bootstrap utility implemented as a foreign task in
  the CL, it may be called either from within the CL (as in the examples),
  or at the host system level.  The command syntax is identical on both cases.
  <P>
  1. List the contents of the disk archive file "<TT>foo.tar</TT>".
  <P>
  	cl&gt; rtar -tvf foo.tar
  <P>
  2. Unpack the tape archive on unix device /dev/nrmt8 in the current
  directory.
  <P>
  	cl&gt; rtar -xf /dev/nrmt8
  <P>
  3. Unpack the tape archive on the VMS device MSA0: in the current
  directory.
  <P>
  	cl&gt; rtar -xf msa0
  <P>
  When working within the CL, commands such as <I>rewind</I> may be used
  with <I>rtar</I>, but switching between IRAF and host device names may be
  confusing.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The current limit on file name length is 100 characters (this restriction
  is imposed by the standard UNIX <I>tar</I> format).
  File links are not recreated.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  wtar, rmbin
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'DIAGNOSTICS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
