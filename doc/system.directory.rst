.. _directory:

directory — List the files in a directory
=========================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  directory -- list the contents of a file directory
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  directory [files]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>A file template specifying the files to be listed, or the name of the directory
  whose contents are to be listed.  If omitted entirely, the contents of the
  current directory are listed.
  </DD>
  </DL>
  <DL>
  <DT><B>long = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='long' Line='long = no'>
  <DD>Long format listing.  The long format listing lists each file on a separate
  line, noting the file permissions, file type, file size, modify date, owner,
  etc. of each file.
  </DD>
  </DL>
  <DL>
  <DT><B>ncols = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 0'>
  <DD>If nonzero, the number of columns of output in multicolumn format.
  </DD>
  </DL>
  <DL>
  <DT><B>maxch = 18</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxch' Line='maxch = 18'>
  <DD>The maximum number of characters to be displayed in each filename.
  Truncation may be desirable when listing a directory containing one or two
  files with very long filenames.
  </DD>
  </DL>
  <DL>
  <DT><B>sort = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sort' Line='sort = yes'>
  <DD>Sort the file list alphabetically.  If sorting is disabled the directory
  program lists the files in the order in which they are read from the
  directory, which may or may not be sorted.  The directory listing is produced
  line by line as files are read from the directory, rather than accumulating
  the entire file list in memory before composing the table, hence this is the
  fastest method of listing a directory, particularly if the directory is very
  large.
  </DD>
  </DL>
  <DL>
  <DT><B>all = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='all' Line='all = no'>
  <DD>List all files, including the hidden ("<TT>.</TT>" prefixed) files, and files with
  reserved filename extensions used internally by the VOS.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <B>directory</B> task lists or prints information describing some subset
  of the files in a directory or directories.  If no name template is given,
  "<TT>.</TT>" is assumed, i.e., all files in the current directory are listed.
  <P>
  The long format listing gives a file type string, followed by
  the name of the owner of the file, the file size, date and time at which
  the file was last modified, and lastly the file name.
  The file type string has fields noting if the file is a directory file (d),
  an executable file (x), a text or binary file (t or b), a protected file (p),
  and summarizing the file permissions (read or write, r or b) for the owner,
  the group, and the rest of the world.  A minus sign indicates that the file
  does not have that particular attribute.
  <P>
  All file names are printed in the IRAF virtual filename syntax, which is the
  same on all host machines.  IRAF filenames may be up to 32 characters in
  length, may contain any combination of alphanumeric characters, underscore,
  or period, and are case sensitive.  Some of the common filename extensions
  are listed below; these are mapped to and from the host filename extensions
  when a file is accessed, a directory is listed, or a filename template is
  expanded.
  <P>
  <PRE>
  	.a	object library
  	.c	C source file
  	.cl	CL source file
  	.e	executable (runnable) file
  	.f	Fortran source file
  	.gX	generic source file (X=[cx])
  	.h	global header file
  	.hlp	help file
  	.o	object file
  	.par	CL parameter file
  	.s	assembler source file
  	.x	SPP source file
  </PRE>
  <P>
  When listing large directories, the time required to accumulate and sort the
  entire directory in memory before producing the output listing may become
  significant (i.e., more than a few seconds).  If this happens, try setting
  the <I>sort</I> option to <I>no</I>, and the directory listing should appear
  immediately.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List all the files in the current directory in tabular format.
  <P>
  	cl&gt; dir
  <P>
  2. Print detailed information on all files in the current directory.
  <P>
  <PRE>
          cl&gt; dir l+
          -t-rwr-r- iraf         269 Oct 16  1983 README
          dt-rwrwr- iraf        1024 Feb  7 12:48 doc
          -t-rwr-r- iraf          60 Jan 30  1984 files.par
          -t-rwr-r- iraf         420 Jan 30  1984 files.x
          -b-rwrwr- system    187338 Jan 29 19:27 libpkg.a
          xb-rwr-r- iraf      363520 Jan 29 19:29 x_system.e
          -b-rwrwr- system      5037 Jan 19 22:15 x_system.o
          -t-rwr-r- iraf         633 Jan 19 22:01 x_system.x
  </PRE>
  <P>
  3. Print a single column listing of all the files with extension "<TT>.h</TT>"
  in the logical directory "<TT>lib$</TT>".
  <P>
  <PRE>
  	cl&gt; dir lib$*.h l+
  	lib$chars.h
  	lib$clio.h
  	lib$clpopn.h
  	    (etc)
  </PRE>
  <P>
  4. While in the "<TT>system</TT>" directory, print the contents of the parallel
  directory "<TT>dataio</TT>".
  <P>
  <PRE>
  	cl&gt; cd pkg$system
  	cl&gt; dir ../dataio
  </PRE>
  <P>
  5. Test if the file "<TT>alpha</TT>" exists in the current directory.  In the example,
  the output given indicates that the file was not found.
  <P>
  <PRE>
  	cl&gt; dir alpha
  	no files found
  </PRE>
  <P>
  6. Print the contents of the directory USR$2:[IRAF.LOCAL] on the remote VMS
  node "<TT>draco</TT>" (requires IRAF network access to the remote node).
  <P>
  <PRE>
  	cl&gt; dir draco!usr\$2:\[iraf.local]
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  There is no provision for wildcarding directories, e.g., "<TT>dir */*.x</TT>".
  The long format listing can currently only be sorted by filename (although
  the <I>sort</I> program may be used in a pipe).  The file existence test will
  not be performed if individual files are named as list elements within
  a filename template.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  files, pathnames
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
