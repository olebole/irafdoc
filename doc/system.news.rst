news — Page through the system news file
========================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>news (Mar90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>news (Mar90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>news</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  news -- print the revisions summary for the current IRAF version
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  news
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>news</I> task uses the standard IRAF file pager to review a formatted
  summary of the system revisions for the version of IRAF being run.
  The revisions summaries for older versions of the system are also provided:
  use the <I>N</I> and <I>P</I> pager keys to display the next or previous
  system revisions summary.  The revisions summary is given in the file
  "<TT>doc$newsfile</TT>".
  <P>
  For reasons of brevity, only the revisions summary is printed.  For detailed
  information on the revisions made to a particular science package, type
  <P>
      cl&gt; help &lt;pkg&gt;.revisions op=sys
  <P>
  where "<TT>pkg</TT>" is the name of the CL package for which revisions information
  is desired.  For detailed information on the revisions to the system
  software and programming interfaces, examine the system notes file,
  given in the file "<TT>notes.*</TT>" in the directory "<TT>iraf$local</TT>".  The system
  notes files for older versions of the system will be found in the "<TT>doc</TT>"
  directory.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The revisions summary is often lengthy and may be easier to read if a
  printed copy is made.
  <P>
  Redirecting the output of <I>news</I>, e.g., to <I>lprint</I>, doesn't work
  at present.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Page the revisions summary for the current IRAF release.
  <P>
      cl&gt; news
  <P>
  2. Print the revisions summary.
  <P>
      cl&gt; lprint doc$newsfile
  <P>
  3. Page the system notes file.  Anyone who develops software for IRAF
  should review this file with each new release, to see what has changed.
  Documentation for new system facilities is often given in the system
  notesfile.
  <P>
      cl&gt; page iraf$local/notes.*
  <P>
  4. Review the revisions summary for the IMAGES package.
  <P>
      cl&gt; phelp images.revisions op=sys
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  help, phelp, page
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'BUGS' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>