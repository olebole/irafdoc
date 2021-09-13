demos — Demonstrations and tests
================================

**Package: hydra**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>demos (Sep90)</B></FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>demos (Sep90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>demos</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  demos -- Demonstration and Test Procedures
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_packages">PACKAGES</A></H2>
  <! BeginSection: 'PACKAGES'>
  <UL>
  noao.imred.argus, noao.imred.goldcams, noao.imred.kpcoude.fiber
  noao.imred.kpcoude.slit, noao.imred.nessie, noao.imred.specred
  noao.twodspec.longslit
  </UL>
  <! EndSection:   'PACKAGES'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  demos demoname
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_demoname">demoname</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='demoname' Line='demoname'>
  <DD>Demonstration or test procedure name.  Each package may have a different
  set of demonstrations.  If the demo name is not specified on the command
  line a menu of names is printed and then the name is queried.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Many packages have demonstration and test procedures.  These are generally
  based on artificial data and use the <I>stty playback</I> (see <B>stty</B>)
  mechanism of the CL.  A playback replaces interactive terminal input 
  with previously stored input but otherwise is an actual execution of
  the entered commands.  This allows both demonstration of various types
  and an actual test of the software on a particular IRAF system.
  <P>
  Generally the <B>demos</B> procedures create their own data if not present
  from a previous execution.  After the procedure is completed the data,
  logfiles, etc. are left so that they may be examined further and
  the user may try some experiments.  Thus, it might be useful to create
  a new directory for the demo using <B>mkdir</B> and "<TT>cd</TT>" to it.
  <P>
  Currently, most of the demos are test procedures which do not contain
  comments and suitable delays to act as a demonstration.  These will
  be added in time.  Also some of the demos just create the demo/test
  data if one just wants some relevant data for experimentation with
  the package.
  <P>
  One should be aware that since the tasks are actually run parameters
  are sometimes changed.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  From the <B>goldcam</B> package list the menu and execute the
  qtest demo.
  <P>
  <PRE>
  	go&gt; mkdir demo
  	go&gt; cd demo
  	go&gt; demos
  		MENU of GOLDCAM Demonstrations
  <P>
  		qtest - Quick test of GOLDCAM (no comments, no delays)
  <P>
  	Demo name (qtest): 
  	&lt;Demo follows&gt;
  </PRE>
  <P>
  2.  From the <B>nessie</B> package create some simple test data.
  <P>
  <PRE>
  	ne&gt; demos mkqdata
  	Creating image demoobj ...
  	Creating image demoflat ...
  	Creating image demoarc1 ...
  	Creating image demoarc2 ...
  	ne&gt; demos mkqdata
  	ne&gt;
  </PRE>
  <P>
  Note that the second execution does not create the data again.
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  artdata.mkexamples, ccdred.ccdtest.demo
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'PACKAGES' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>