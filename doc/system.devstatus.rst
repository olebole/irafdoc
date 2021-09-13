devstatus — Print the status of a device (mta, mtb, ...)
========================================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>devstatus (Jan86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>devstatus (Jan86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>devstatus</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  devstatus -- print status information for a device
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  devstatus device
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_device">device</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device'>
  <DD>The device for which status information is requested.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print additional system dependent device information (may not be implemented
  on all systems).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Devstatus</B> tells whether the named device has been allocated.
  In the case of a magtape drive allocated to the current user, additional
  information is printed noting the tape position and the type of operation
  last performed.  If the device is not currently allocated, i.e., available
  for allocation, or if the device has already been allocated by another user,
  one of the following messages is printed:
  <P>
  <PRE>
  	device is not currently allocated
  	device is allocated to XXXX
  </PRE>
  <P>
  A list of the allocatable devices, including the host system names for the
  devices, can be obtained by paging the file <B>dev$devices</B> providing
  that file has been properly configure by the Site Manager at installation
  time.  The dev$tapecap file is used to define the tape devices available
  on the system.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Get status information for the logical tape drive "<TT>mta</TT>", which we have
  just allocated.  Note that the tape position is printed only if we are the
  owner of the drive.
  <P>
  <PRE>
  	cl&gt; dev mtb
  	# Magtape unit `mta' allocated to `smith' Fri 12:04:16 07-Jan-86
  	file = 1
  	record = 1
  	unit just allocated: no i/o has yet occurred
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Information can only be requested for a single device at a time.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  allocate, deallocate
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>