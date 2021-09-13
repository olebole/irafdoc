.. _gdevices:

gdevices — List available imaging or other graphics devices
===========================================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  gdevices -- list available imaging or other graphics devices
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  gdevices
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>devices = "<TT>^imt</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='devices' Line='devices = "^imt"'>
  <DD>A list of patterns identifying the class of devices for which information
  is to be output.  If multiple patterns are given they should be separated
  by commas.  The default pattern matches all stdimage (e.g. IMTOOL) devices.
  </DD>
  </DL>
  <DL>
  <DT><B>graphcap = "<TT>graphcap</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphcap' Line='graphcap = "graphcap"'>
  <DD>The graphcap file to be scanned (any termcap format file will do).  By default
  the graphcap file specified by the graphcap environment variable, usually
  "<TT>dev$graphcap</TT>", is scanned.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>gdevices</B> prints a table of the available devices in a given class of
  devices, giving for each device a list of the aliases by which the device
  is known, the imaging resolution in X and Y, and a short description of the
  device (if present in the graphcap file entry).
  <P>
  By default <I>gdevices</I> lists the available stdimage devices as defined in
  the active graphcap file, however, by manipulating the <I>devices</I> and
  <I>graphcap</I> parameters any class of devices in any file can be listed.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the available stdimage (e.g. IMTOOL or SAOIMAGE) devices.
  <P>
  <PRE>
      cl&gt; gdev
  #                     ALIASES    NX   NY  DESCRIPTION
                           imtx   512  512  Imtool display server
             imt1 imt512 imtool   512  512  Imtool display server
                    imt2 imt800   800  800
                   imt3 imt1024  1024 1024
                   imt4 imt1600  1600 1600
                   imt5 imt2048  2048 2048
                   imt6 imt4096  4096 4096
  			         (etc.)
  </PRE>
  <P>
  2. List the available IMDKERN devices.
  <P>
  <PRE>
      cl&gt; gdev dev=imd
  #                     ALIASES    NX   NY  DESCRIPTION
     imdblack imdbla imdB imdbl  2048 2048
      imdwhite imdwhi imdW imdw  2048 2048
  			         (etc.)
  </PRE>
  <P>
  3. List the VMS graphics devices.
  <P>
  <PRE>
      cl&gt; gdev dev=VMS
  #                     ALIASES    NX   NY  DESCRIPTION
                        iism70v   512  512  NOAO Vela hosted IIS model
                         iism75   512  512  IIS model 75 image display
                          ui300  3130 2370  UNIX interface to the NOAO
                           vver  2112 1636  VMS generic interface to th
  			         (etc.)
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The method used to extract device entries involves multiple scans of the
  graphcap file hence is not very efficient.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  system.devices, dev$graphcap
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
