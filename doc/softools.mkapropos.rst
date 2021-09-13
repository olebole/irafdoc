mkapropos — Make the apropos database (from STSDAS).
====================================================

**Package: softools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkapropos (Aug16)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>softools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkapropos (Aug16)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkapropos</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkapropos -- Make the apropos database.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkapropos pkglist aproposdb
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The 'mkapropos' task descends a tree of help directory ('.hd') files
  and compiles a text database from the information found there, specifically
  from the package menu files ('.men').
  <P>
  The apropos database is used to speed global searches when information
  is requested for a particular subject.
  Each line of the apropos database contains the name of the task or package,
  along with a brief description (from the '.men' files) and its package.
  <P>
  By default, 'mkapropos' parameters are set to recompile the standard
  IRAF and NOAO apropos database (placed in 'lib$apropos.db'), although any other
  similar database may be recompiled, for example, for other add-on packages such
  as 'stsdas', 'xray' and 'ctio'. 
  <P>
  Additionally, you can build apropos databases for your own packages.
  <P>
  This is the mkapropos from stsdas.toolbox.tools, copied into Ureka/AstroConda
  IRAF's softools to facilitate building IRAF packages before stsdas is installed.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_pkglist">pkglist = "<TT>iraf, noao</TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pkglist' Line='pkglist = "iraf, noao" [string]'>
  <DD>The names of the packages to examine when building the apropos database.
  By default, the
  IRAF, NOAO, and STSDAS packages are used.   Any IRAF external package may be 
  included.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_helpdir">helpdir = "<TT>lib/root.hd</TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='helpdir' Line='helpdir = "lib/root.hd" [string]'>
  <DD>The filename of the root help directory file ('.hd' file)
  defining the help tree to be updated. This string is appended to each of the
  packages listed in the 'pkglist' parameter above. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_aproposdb">aproposdb = "<TT>lib$apropos.db</TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aproposdb' Line='aproposdb = "lib$apropos.db" [string]'>
  <DD>The filename of the apropos database to be written. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no [boolean]'>
  <DD>Print a detailed description of the help database as it is compiled?
  <P>
  A more concise summary listing only the packages and the number
  of help modules in each package is printed by default.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Update the stsdas package apropos database.
  <P>
  <PRE>
    cl&gt; mkapropos stsdas lib/root.hd stsdas$lib/apropos.db
  </PRE>
  <P>
  2. Update a user apropos database.
  <P>
  <PRE>
    cl&gt; mkap pkglist=home helpdir=myroot.hd aproposdb=my.db
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apropos, mkhelpdb
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>