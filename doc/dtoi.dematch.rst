dematch — Match a list of density values to exposure values
===========================================================

**Package: dtoi**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>dematch (Feb87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>imred.dtoi</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>dematch (Feb87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>dematch</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  dematch -- match density to log exposure values
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  dematch database 
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_database">database</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>Database containing density list, probably from <I>spotlist</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wedge">wedge = "<TT></TT>", filter = "<TT></TT>", emulsion = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wedge' Line='wedge = "", filter = "", emulsion = ""'>
  <DD>Information used to retrieve log exposure values from <B>wedgefile</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wedgefile">wedgefile = "<TT>noao$lib/hdwedge.dat</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wedgefile' Line='wedgefile = "noao$lib/hdwedge.dat"'>
  <DD>Name of file containing wedge intensity information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nskip">nskip = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nskip' Line='nskip = 0'>
  <DD>Number of faint spots skipped, used as an offset into the list of
  log exposure values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print the log exposure information to STDOUT as well as to <B>database</B>.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>dematch</I> matches density values to log exposure values.  A database
  of density values is input, as well as information needed to 
  retrieve log exposure values from a reference file.  The two sources of 
  information are matched, and the matching log exposure values are added 
  as a record in the database.
  <P>
  Parameter <B>nskip</B> tells how many faint spots were not
  included in the density <B>database</B>.  This information is
  used to align the density, exposure values.  It doesn't matter if the 
  densities are listed in a monotonically increasing or decreasing
  order, as long as no spots were omitted between the first and last
  measured.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Match densities in db1 to log exposure values for wedge#117
  with a IIIAJ emulsion and a GG385 filter.
  <PRE>
  <P>
  	cl&gt; dematch db1 wedge=117 filt=gg385 emulsion=IIIAJ
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  spotlist, hdfit, hdtoi
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>