ldumpf — List the permanent files on a Cyber DUMPF tape
=======================================================

**Package: mtlocal**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>ldumpf (Jun87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.mtlocal</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>ldumpf (Jun87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>ldumpf</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  ldumpf -- list the permanent files on a Cyber DUMPF tape.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  ldumpf dumpf_file file_list
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_dumpf_file">dumpf_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dumpf_file' Line='dumpf_file'>
  <DD>The DUMPF data source, i.e., the name of a magtape device or a DUMPF
  format disk file.   If reading from tape, the files to be listed are
  specified by the <I>file_list</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_file_list">file_list</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list'>
  <DD>A string listing the DUMPF files to be listed from <I>dumpf_file</I>.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Cyber permanent files stored on DUMPF tapes are listed.  The permanent file
  name, cycle number, owner id, dates of last attach, last alteration and
  the creation date are printed.  Task <B>ldumpf</B> lists the contents of a 
  DUMPF tape;
  to convert IPPS rasters stored on DUMPF tapes to IRAF images, use task
  <B>rdumpf</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  List all permanent files on a DUMPF tape:
  <P>
  	cl&gt; ldumpf mta 1-999
  <P>
  List information for the 4th permanent file on the tape:
  <P>
  	cl&gt; ldumpf mta 4
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The Cyber format readers, including task <I>ldumpf</I>, have not been 
  implemented on SUN/IRAF and AOS/IRAF.
  <P>
  The current version of IRAF magtape I/O does not read beyond the first
  volume of a multivolume tape.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rdumpf
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>