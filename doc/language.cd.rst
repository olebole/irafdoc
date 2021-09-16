.. _cd:

cd — Change directory
=====================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  chdir, cd -- change the current working directory
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  chdir [newdir]  or  cd [newdir]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>newdir</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newdir' Line='newdir'>
  <DD>The new working directory.
  The special name "<TT>.</TT>" refers to the current directory; "<TT>..</TT>" refers to the next
  higher directory.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Chdir</I> is used to change the current working directory.
  When called without any arguments, <I>chdir</I> sets the default directory
  to "<TT>home$</TT>", the users home directory.
  The new directory can be specified as an IRAF logical name,
  as a sub-directory of the current directory,
  as a path from either a logical directory or the current directory,
  or as an operating system dependent name.
  <P>
  The names <I>chdir</I> and <I>cd</I> are synonyms.  Note that the command
  <I>back</I> may be called after a <I>chdir</I> to return to the previous
  directory without typing its name.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Return to our home directory.
  <P>
  	cl&gt; cd
  <P>
  2. Go to the package logical directory "<TT>pkg$</TT>".
  <P>
  	cl&gt; chdir pkg
  <P>
  3. Go down one level to the directory "<TT>dataio</TT>", a subdirectory of "<TT>pkg</TT>".
  <P>
  	cl&gt; cd dataio
  <P>
  4. From "<TT>dataio</TT>", go back up to "<TT>pkg</TT>" and down into "<TT>images</TT>".
  <P>
  	cl&gt; cd ../images
  <P>
  5. Go to the "<TT>tv</TT>" directory, a subdirectory of "<TT>images</TT>", regardless of the
  current directory
  <P>
  	cl&gt; cd pkg$images/tv
  <P>
  6. On a VMS system, define a new logical directory on a different disk device
  and go there.  Note that the character $ is not permitted in host file or
  directory names.
  <P>
  <PRE>
  	cl&gt; set dd = scr1:[data]
  	cl&gt; cd dd
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  back, pathnames
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
