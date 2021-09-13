mkttydata — Build cache for termcap/graphcap device entries
===========================================================

**Package: softools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkttydata (Jun90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>softools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkttydata (Jun90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkttydata</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkttydata -- build a cache for graphcap/termcap device entries
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkttydata devices termcap_file output_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_devlist">devlist</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='devlist' Line='devlist'>
  <DD>A comma delimited list of the devices whose termcap or graphcap entries
  are to be compiled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_termcap_file">termcap_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='termcap_file' Line='termcap_file'>
  <DD>The name of the termcap or graphcap file be searched, e.g., "<TT>dev$termcap</TT>",
  or "<TT>dev$graphcap</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output_file">output_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output_file' Line='output_file'>
  <DD>The name of the output file to be written, an SPP include file containing
  a number of declarations and data initialization statements.
  This should be "<TT>dev$cachet.dat</TT>" if the standard termcap is being compiled,
  and "<TT>dev$cacheg.dat</TT>" if the standard graphcap is being compiled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Causes a message to be printed for each device entry compiled.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>mkttydata</I> task is used by the IRAF system manager to precompile
  the <I>termcap</I> or <I>graphcap</I> entries for commonly used video or
  graphics terminals.  This can be advantageous on slow systems since otherwise
  the termcap or graphcap file must be searched at runtime every time the
  screen is cleared or a graph is plotted, reducing the performance and
  interactive response of the system.  Since each IRAF site will commonly use
  a different set of devices, entries can only be cached by the local system
  manager after the system is installed.  [NOTE, Jun 1990: the above is
  still true, but with the addition of features such as shared libraries and
  multiple architecture support to some versions of IRAF, relinking IRAF is
  more difficult and it is easier to make mistakes.  Furthermore, modern
  systems are getting very fast.  For most sites it will be easier, and safer,
  to merely copy frequently referenced device entries to the head of the
  termcap or graphcap file and skip the sysgen.]
  <P>
  The input to <I>mkttydata</I> consists of a list of devices and a reference
  to either the termcap or graphcap file.  The output is an SPP include file
  which is referenced by the procedures in the TTY package.  After updating
  the cache files, a full system sysgen is required to recompile the affected
  modules, update them in the system libraries, and relink all executables.
  <P>
  Enter the following values for the <I>termcap_file</I> and <I>output_file</I>
  parameters to build the termcap and graphcap cache files.  Note that for
  caching to work the value of <I>termcap_file</I> must match that of
  the <I>termcap</I> or <I>graphcap</I> environment variable, hence do not
  enter "<TT>graphcap</TT>" rather than "<TT>dev$graphcap</TT>", just because you happen to
  be in the dev directory.
  <P>
  <P>
  <PRE>
  <PRE>
  			<I>termcap_file</I>	<I>output_file</I>
  	
  	termcap		dev$termcap	dev$cachet.dat
  	graphcap	dev$graphcap	dev$cacheg.dat
  </PRE>
  </PRE>
  <P>
  <P>
  After updating these files, perform a sysgen-relink to update the
  system libraries and relink all executables (this takes a while, and
  requires IRAF permissions and full sources).  Instructions for performing
  the sysgen-relink are given in the <I>Site Manager's Guide</I> for your
  IRAF system.  The exact procedure for performing a sysgen-relink depends
  upon the host system.  In particular, if the system support multiple
  architectures, each architecture must be restored and relinked separately.
  Note that systems configured for multiple architecture support are
  shipped configured "<TT>generic</TT>", and you must restore an architecture before
  relinking or the entire IRAF system will be recompiled (which is time
  consuming, and inadvisable due to the possibility of system or compiler
  differences introducing bugs into IRAF).
  <P>
  After this finishes, log out and back in and you should notice the
  difference when running tasks like <I>page</I>, <I>clear</I>, and <I>implot</I>.
  <P>
  Note that once a device entry is cached it cannot be modified without
  going through this all over again, while if the entry is not cached it
  can be edited and the new entry used immediately.  It is therefore not
  desirable to cache new termcap or graphcap entries until they have stopped
  changing.  Even after a device entry has been cached, however, it is possible
  to test new entries by changing the entry name, or by changing the value
  of the <I>termcap</I> or <I>graphcap</I> environment variable.  If these
  values are different than they were when the entries were cached, the cached
  entries will not be used, even if the device name matches that of a cached
  entry.
  <P>
  For additional information on graphcap see the "<TT>GIO Design</TT>" document.
  For additional information on termcap see the Berkeley UNIX "<TT>Programmer's
  Guide: Reference Manual</TT>", section 5.  IRAF uses a standard UNIX termcap.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Update the graphcap cache.
  <P>
      cl&gt; mktty vt640,vt240,4012,cit414a dev$graphcap dev$cacheg.dat
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  There is a fixed limit on the amount of data that can be cached.
  If the limit is exceedd the affected TTY modules will fail to compile.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  showcap, IRAF Site Manager's Guide
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>