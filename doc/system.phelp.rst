phelp — Paged HELP: collects and pages the output of HELP
=========================================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>phelp (Mar90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>phelp (Mar90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>phelp</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  phelp -- page the output of the HELP task
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  phelp template
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  The <I>phelp</I> parameters are the same as for <I>help</I> except that
  the <I>page</I> and <I>nlpp</I> parameters are omitted.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>phelp</I> task is a front end to <I>help</I> which spools the output
  of <I>help</I> in a scratch file, then calls the file pager <I>page</I> to
  view the output text.  The advantage is that while <I>help</I> pages its
  output, one can only move forward through the output text.  By using
  <I>phelp</I> it is possible to randomly scan the spooled help text, e.g.,
  skipping forward to get a quick overview and then backing up to read the
  details more carefully.  This capability is especially useful when viewing
  large multipage help pages, or when viewing a number of related help pages
  all at once.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Page the help page for the <I>mkpkg</I> task.
  <P>
      cl&gt; phelp mkpkg
  <P>
  2. View the help pages for all the tasks in the IMAGES package.
  <P>
      cl&gt; phelp images.*
  <P>
  When viewing multiple help pages as in this last example, note that the
  <TT>'N'</TT> and <TT>'P'</TT> keystrokes in the pager may be used to move to the next or
  previous help page.  "<TT>.</TT>" will return to the first help page (the start
  of the spooled help text) and <TT>'G'</TT> will skip to the end of file.  Type <TT>'?'</TT>
  while in the pager to get a summary of the most often used keystrokes.
  <P>
  3. Format and page the Lroff (IRAF HELP) format document "<TT>MWCS.hlp</TT>" in
  the system directory "<TT>mwcs</TT>".
  <P>
  <PRE>
      cl&gt; cd mwcs
      cl&gt; phelp MWCS.hlp fi+
  </PRE>
  <P>
  In this case the text being viewed is not part of the on-line help system,
  but is a technical document describing one of the IRAF programming interfaces.
  Any .hlp file may be viewed in this way.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <I>phelp</I> is not quite as fast as <I>help</I> since it must fully format
  the help text into a temporary file before the file can be viewed.  For
  small help pages, or to view only the first few screens of a help page,
  the <I>help</I> task will be faster.
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
  page, help, references
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>