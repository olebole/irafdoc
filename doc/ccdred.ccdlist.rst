ccdlist — List CCD processing information
=========================================

**Package: ccdred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>ccdlist (Jun87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.ccdred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>ccdlist (Jun87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>ccdlist</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  ccdlist -- List CCD processing information
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  ccdlist images
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>CCD images to be listed.  A subset of the these may be selected using the
  CCD image type parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ccdtype">ccdtype = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdtype' Line='ccdtype = ""'>
  <DD>CCD image type to be listed.  If no type is specified then all the images
  are listed.  If an image type is specified then only images
  of that type are listed.  See <B>ccdtypes</B> for a list of the package
  image types.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_names">names = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='names' Line='names = no'>
  <DD>List the image names only?  Used with the CCD image type parameter to make
  a list of the images of the specified type.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_long">long = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='long' Line='long = no'>
  <DD>Long format listing?  The images are listed in a long format containing some
  image parameters and the processing history.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ccdproc">ccdproc (pset)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdproc' Line='ccdproc (pset)'>
  <DD>CCD processing parameter set.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Information from the specified input images is listed on the standard
  output.  A specific CCD image type may be selected from the input
  images by the parameter <I>ccdtype</I>.  There are three list formats;
  the default one line per image format, an image name only format, and a
  multi-line long format.  The default one line format consists of the
  image name, image size, image pixel type, CCD image type, subset ID (if
  defined), processing flags, and title.  This format contains the same
  information as that produced by <B>imheader</B> as well as CCD specific
  information.  The processing flags identifying the processing operations
  performed on the image are given by the following single letter codes.
  <P>
  <PRE>
  	B - Bad pixel replacement
  	O - Overscan bias subtraction
  	T - Trimming
  	Z - Zero level subtraction
  	D - Dark count subtraction
  	F - Flat field calibration
  	I - Iillumination correction
  	Q - Fringe correction
  </PRE>
  <P>
  The long format has the same first line as the default format plus additional
  instrument information such as the exposure time and the full processing
  history.  In addition to listing the completed processing, the operations
  not yet done (as specified by the <B>ccdproc</B> parameters) are also
  listed.
  <P>
  The image name only format is intended to be used to generate lists of
  images of the same CCD image type.  These lists may be used as "<TT>@</TT>" file
  lists in IRAF tasks.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To list the default format for all images:
  <P>
  <PRE>
      cl&gt; ccdlist *.imh
      ccd001.imh[544,512][short][unknown][V]:FOCUS L98-193
      ccd007.imh[544,512][short][object][V]:N2968 V 600s
      ccd015.imh[544,512][short][object][B]:N3098 B 500s
      ccd024.imh[544,512][short][object][R]:N4036 R 600s
      ccd045.imh[544,512][short][flat][V]:dflat 6v+blue 5s
      ccd066.imh[544,512][short][flat][B]:dflat 6v+blue 5s
      ccd103.imh[544,512][short][flat][R]:dflat 6v+blue 5s
      ccd104.imh[544,512][short][zero][]:bias
      ccd105.imh[544,512][short][dark][]:dark 3600s
  </PRE>
  <P>
  These images have not been processed.
  <P>
  2. To restrict the listing to just the object images:
  <P>
  <PRE>
      cl&gt; ccdlist *.imh ccdtype=object
      ccd007.imh[544,512][short][object][V]:N2968 V 600s
      ccd015.imh[544,512][short][object][B]:N3098 B 500s
      ccd024.imh[544,512][short][object][R]:N4036 R 600s
  </PRE>
  <P>
  3. The long list for image "<TT>ccd007</TT>" is obtained by:
  <P>
  <PRE>
      cl&gt; ccdlist ccd007 l+
      ccd007[544,512][short][object][V]:N2968 R 600s
  	exptime = 200. darktime = 200.
          [TO BE DONE] Overscan strip is [520:540,*]
          [TO BE DONE] Trim image section is [3:510,3:510]
          [TO BE DONE] Flat field correction
  </PRE>
  <P>
  4. After processing the images have the short listing:
  <P>
  <PRE>
      cl&gt; ccdlist *.imh ccdtype=object
      ccd007.imh[508,508][real][object][V][OTF]:N2968 V 600s
      ccd015.imh[508,508][real][object][B][OTF]:N3098 B 500s
      ccd024.imh[544,512][short][object][R][OTF]:N4036 R 600s
  </PRE>
  <P>
  The processing indicated is overscan subtraction, trimming, and flat fielding.
  <P>
  5. The long listing for "<TT>ccd007</TT>" after processing is:
  <P>
  <PRE>
      cl&gt; ccdlist ccd007 l+
      ccd007[508,508][real][object][V][OTF]:N2968 R 600s
  	exptime = 200. darktime = 200.
          Jun  2 18:18 Overscan section is [520:540,*] with mean=481.8784
          Jun  2 18:18 Trim data section is [3:510,3:510]
          Jun  2 18:19 Flat field image is FlatV.imh with scale=138.2713
  </PRE>
  <P>
  6. To make a list file containing all the flat field images:
  <P>
      cl&gt; ccdlist *.imh ccdtype=flat name+ &gt; flats
  <P>
  This file can be used as an @ file for processing.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdtypes ccdgroups
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>