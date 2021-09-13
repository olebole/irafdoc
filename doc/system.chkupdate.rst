.. _chkupdate:

chkupdate — Check for an available IRAF update
==============================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  chkupdate - Check for an available IRAF update
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  chkupdate
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>interval = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interval' Line='interval = 0'>
  <DD>Number of days between updates checks.  A value less than zero will disable
  the checks entirely, a value of zero will cause a check to be made with 
  each login.
  </DD>
  </DL>
  <DL>
  <DT><B>ref_file = "<TT>iraf$.release_date</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ref_file' Line='ref_file = "iraf$.release_date"'>
  <DD></DD>
  </DL>
  <DL>
  <DT><B>release = "<TT>)_.release</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='release' Line='release = ")_.release"'>
  <DD>Current IRAF release version.  This value is inherited from the CL 'release'
  parameter by default.
  </DD>
  </DL>
  <DL>
  <DT><B>baseurl = "<TT>http://iraf.noao.edu/ftp</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='baseurl' Line='baseurl = "http://iraf.noao.edu/ftp"'>
  <DD>Base URL to the IRAF release timestamp directory.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print verbose output?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task compares the currently installed IRAF version with what is
  available from the NOAO servers and will indicate whether an update is
  available.  The task is executed from the login.cl each time you login 
  to the CL, however the comparison is only done if 1) the uparm$update 
  file used to indicate the time of last check does not exist, 2) the 
  <I>interval</I> parameter is zero to indicate the check should be done
  with each login, or 3) more than <I>interval</I> days have passed since
  the last time the servers were contacted.  An <I>interval</I> value less
  that zero may be used to disable the version updates entirely.
  <P>
  The update check is done by comparing the file timestamp of the file
  named in the <I>ref_file</I> parameter with a distribution timestamp file
  on the NOAO servers.  The URL to this file is constructed from the 
  <I>baseurl</I> and <I>release</I> parameters in addition to the <I>arch</I>
  environment value, yielding a unique URL for each version and each platform.
  If the contents of the file contain a timestamp more recent than the 
  timestamp of the <I>ref_file</I> value, a message is printed to indicate
  an update is available, otherwise a message is printed indicating the
  installed system is current.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Check whether an IRAF update is available, regardless of when we last
  checked.
  <P>
  <PRE>
  	cl&gt; chkupdate interval=0
  </PRE>
  <P>
  2. Check for an IRAF update once a month.
  <P>
  <PRE>
  	cl&gt; chkupdate.interval = 30
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Notes</H3>
  <! BeginSection: 'NOTES'>
  <UL>
  This task is called automatically from the login.cl file at startup.
  <P>
  Modifying the timestamp information of the <I>ref_file</I> parameter, e.g.
  by moving the IRAF tree, may invalidate the output.
  </UL>
  <! EndSection:   'NOTES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'NOTES' 'SEE ALSO'  >
  
