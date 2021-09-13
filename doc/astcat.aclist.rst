aclist — List the supported astrometric catalogs
================================================

**Package: astcat**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>aclist (Feb00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>astcat</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>aclist (Feb00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>aclist</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  aclist -- list the supported astrometric catalogs
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  aclist catalogs
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_catalogs">catalogs</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catalogs' Line='catalogs'>
  <DD>The names of the astrometric catalogs to be listed. If catalogs = "<TT>*</TT>" then
  all the astrometric catalogs in the catalog configuration file are listed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>List the catalog query and output formats after the catalog name ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_catdb">catdb = "<TT>)_.catdb</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catdb' Line='catdb = ")_.catdb"'>
  <DD>The catalog configuration file. The value of catdb defaults to the value
  of the package parameter of the same name. The default catalog configuration
  file is "<TT>astcat$lib/catdb.dat</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Aclist lists the supported astrometric catalogs specified by the
  <I>catalogs</I> parameter. If catalogs = "<TT>*</TT>" then all the supported catalogs
  are listed, otherwise only the catalog names specified by the user are
  listed. Valid catalog names have the form "<TT>catalog@site</TT>", e.g. "<TT>usno2@noao</TT>".
  If <I>verbose</I> = "<TT>yes</TT>", then the catalog query and output formats are
  listed after the catalog name.
  <P>
  The catalog names, addresses, query formats, and query output formats are
  specified in the catalog configuration file <I>catdb</I>. By default the catalog
  configuration file name defaults to the value of the package parameter catdb.
  The default catalog configuration file is "<TT>astcat$lib/catdb.dat</TT>".
  Users can add records to this file or create their own configuration
  file using catdb as a model.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List all the astrometric catalogs in the catalog configuration file.
  <P>
  <PRE>
  cl&gt; aclist *
  </PRE>
  <P>
  2. List the query format and the output format for the usno2@noao catalog.
  <P>
  <PRE>
  cl&gt; aclist usno2@noao verbose+
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  aslist
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>