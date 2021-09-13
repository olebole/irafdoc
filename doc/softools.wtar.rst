wtar — Write a TAR format archive file
======================================

**Package: softools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>wtar (Oct92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>softools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>wtar (Oct92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>wtar</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  wtar -- write TAR format archive file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  wtar [-flags] [-f archive] [files]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_arguments">ARGUMENTS</A></H2>
  <! BeginSection: 'ARGUMENTS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_">-d</A></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='-d'>
  <DD>Print debug messages.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">-o</A></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='-o'>
  <DD>Omit binary files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">-t</A></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='-t'>
  <DD>Print the name of each file as it is written or omitted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">-v</A></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='-v'>
  <DD>Verbose mode; print more information about each file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">-f archive</A></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='-f archive'>
  <DD>The tar format file to be written, i.e., "<TT>stdout</TT>", a host magtape device
  name (e.g., "/dev/nrmt8"<TT> or </TT>"MSA0"<TT>), or the IRAF virtual filename of a disk
  file.  The default is the standard output.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_files">files</A></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='files' Line='files'>
  <DD>The names of the files or root directories of directory trees to be written
  to the archive file.  If no files are specified </TT>"."<TT> (the directory tree
  rooted at the current directory) is assumed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'ARGUMENTS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The named files and directories are written to the indicated
  UNIX </TT>"tar"<TT> format output file.  Any directories in the file list are
  recursively descended.  The named directories should be subdirectories of
  the current directory when <I>wtar</I> is called.  Binary files may be
  omitted if desired, e.g., when transporting software to a different host, or
  when making a backup of a large system which would otherwise exceed the
  capacity of a single reel of tape.  All file, directory, and magtape names
  conform to the IRAF standard.
  <P>
  The output file is normally either a disk file (e.g., if the transport
  medium is an electronic network), or a magtape file.  If the output file is
  a magtape multiple files, i.e., wtar archives, may be written on the tape.
  The blocking factor is fixed at 10240 bytes per record.
  <P>
  The TAR format file written by <I>wtar</I> conforms to the UNIX standard except
  that [1] no link information is preserved, [2] the user and group numbers
  may not be preserved (they are preserved in the UNIX version of <I>wtar</I>),
  and [3] some versions of <I>wtar</I> (e.g., VMS) pad text files at the end
  with extra blank lines.
  <P>
  All <I>wtar</I> filename arguments are IRAF virtual filenames (or host
  filenames).  Magtape devices should be specified by their host (not IRAF)
  device name, e.g., "/dev/nrmt8"<TT> or </TT>"MSA0"<TT>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Make a source-only archive of the IRAF system on the UNIX device
  /dev/nrmt8.
  <P>
  <PRE>
  	cl&gt; cd iraf
  	cl&gt; wtar -of /dev/nrmt8
  </PRE>
  <P>
  2. Archive the </TT>"uparm"<TT> directory to the VMS logical device MSA0:.
  <P>
  	cl&gt; wtar -f msa0 uparm
  <P>
  3. Make a disk archive of the LIB and PKG directory trees in your home
  directory.
  <P>
  	cl&gt; wtar -f home$archive.tar lib pkg 
  <P>
  4. Examine the resultant file to make sure everything worked correctly.
  <P>
  	cl&gt; rtar -tvf home$archive.tar
  <P>
  <P>
  5. Make a disk archive, using a host filename for the output file.
  <P>
  	cl&gt; wtar -f /tmp2/arc lib pkg sys
  <P>
  IRAF magtape commands such as <I>rewind</I> may be used with <I>wtar</I>,
  but switching between IRAF and host device names can be confusing.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rtar, rmbin
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'ARGUMENTS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>