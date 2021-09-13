.. _touch:

touch — Change file access and modification times
=================================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  touch -- change file access and modification times
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  touch files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>List of files to be created or touched.
  </DD>
  </DL>
  <DL>
  <DT><B>create = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='create' Line='create = yes'>
  <DD>If enabled, the file will be created as a zero-length text file if it doesn't
  already exist.
  </DD>
  </DL>
  <DL>
  <DT><B>atime = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='atime' Line='atime = yes'>
  <DD>Change the access time of the file.  Will not change the modification time
  unless <I>mtime</I> is also set.
  </DD>
  </DL>
  <DL>
  <DT><B>mtime = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mtime' Line='mtime = yes'>
  <DD>Change the modification time of the file.  Will not change the access time
  unless <I>atime</I> is also set.
  </DD>
  </DL>
  <DL>
  <DT><B>time = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='time' Line='time = ""'>
  <DD>Time and date to set for the file.  The format of this string may be any
  of DD/MM/YY or CCYY-MM-DD (in which case time is assumed to be midnight of
  that day), or CCYY-MM-DDTHH:MM:SS[.SSS...] to specify both date and time.
  If not specified, the current system time is used unless the <I>ref_file</I>
  parameter is set.  If specified, <I>ref_file</I> will be ignored.
  </DD>
  </DL>
  <DL>
  <DT><B>ref_file = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ref_file' Line='ref_file = ""'>
  <DD>Use the corresponding times of the specified file for modifying the
  times of the <I>input_files</I>.  If not specified, the current time is
  used unless the <I>time</I> parameter is set.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print verbose output of the files and times being reset.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>touch</I> task sets the access and modification times of each file
  in the <I>files</I> list.  The file will be created if it does not already
  exist when the <I>create</I> parameter is set.  The time used can be
  specified by <I>time</I> parameter or by the corresponding fields of the
  file specified by <I>ref_file</I>, otherwise the current system time will
  be used.  The task will update both the modification and access times of
  the file unless disabled by the <I>atime</I> or <I>mtime</I> parameter.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1.  Update the times of all SPP source files in the current directory:
  <P>
  	cl&gt; touch *.x
  <P>
  2.  Create an empty file on a remode node:
  <P>
  	cl&gt; touch ursa!/data/trigger_file
  <P>
  3.  Reset the file modification time to 2:33:45 pm on June 5, 2003:
  <P>
  	cl&gt; touch nite1.fits time="<TT>2003-06-05T14:23:45</TT>"
  <P>
  4.  Reset the file modification time to match dev$hosts:
  <P>
  	cl&gt; touch nite1.fits ref_file=dev$hosts
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
