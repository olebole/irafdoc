gripes — Send suggestions, complaints, etc. to the system
=========================================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>gripes (Mar86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>gripes (Mar86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>gripes</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  gripes -- send gripes or suggestions to the system
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  gripes subject
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_subject">subject</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subject' Line='subject'>
  <DD>The subject of the gripe; any string, usually the name of package or task
  to which the gripe refers.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print instructions on how to enter text whenever <I>gripes</I> is run.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <B>gripes</B> task is used to post complaints, suggestions, or any other
  formal or informal comments regarding the IRAF system.  Each gripe is
  appended to the system gripesfile "<TT>hlib$gripesfile</TT>", a public file which
  can be read by anyone by simply typing "<TT>page hlib$gripesfile</TT>" within IRAF.
  Use <B>tail</B> instead of <B>page</B> to read only the most recent gripes.
  A copy of each gripe is also sent immediately to one or members of the IRAF
  group via electronic mail, to insure that the gripe gets read promptly (this
  feature is not available on all host systems).
  <P>
  Gripe text is read from the standard input.  A line containing only a period
  terminates the gripe, as does the end of file character (e.g., &lt;ctrl/z&gt;).
  If the line containing only "<TT>~e</TT>" is entered a text editor will be called up
  to edit the text of the gripe.
  <P>
  Users are encouraged to use the gripe facility at will.  Be assured that
  someone will at least read the gripe, although there is no guarantee that
  any action will be taken.  In many cases there will be no response from the
  system, but nonetheless the gripe will be seen and it may well influence
  the direction in which the system evolves.  Do not avoid posting gripes for 
  fear that you do not understand something about the system; if enough users
  find some aspect of the system or a program confusing then that is more
  than sufficient reason for a gripe.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1.  The user has discovered some nasty features of the <I>imdelete</I> task
  and enters the following gripe.  Note the use of the "<TT>.</TT>" to terminate
  the text.
  <P>
  <PRE>
  	cl&gt; gripe
  	Subject: image deletion
  	Enter text of gripe.  Type &lt;eof&gt; or <TT>'.'</TT> to quit:
  <P>
  	IMDEL * will delete non image files as well as images!
  	It should be possible to delete images with the normal
  	DELETE command.
  	.
  	cl&gt;
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  There is currently no provision for communicating gripes from a remote site
  back to the site that wrote the software, unless some person manually mails
  a gripe (or the accumulated gripesfile).
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  news
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>