wcscopy — Copy the wcs from one image to another
================================================

**Package: immatch**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>wcscopy (Jun95)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.immatch</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>wcscopy (Jun95)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>wcscopy</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  wcscopy -- copy the wcs of a reference image to a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  wcscopy images refimages
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>The list of input images which will inherit the wcs of the reference image.
  If the image does not exists a dataless image header is created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reference">reference</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>The list of reference images containing the reference wcs. The number of
  reference images must be one or equal to the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about the progress of the task?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  WCSCOPY copies the world coordinate system information in the header of the
  reference image <I>reference</I> to the headers of the input images
  <I>images</I>, replacing any existing world coordinate system information
  in the input image headers in the process. WCSCOPY assumes that the
  world coordinate system information in the header of the reference 
  image is accurate and that all the input images have write permission.
  If the input image does not exist a data-less image header is created.
  The WCS is treated as an independent object and
  there is no check made on the dimensionality and sizes of the images.
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  Information  on  IRAF  world  coordinate  systems including
  more detailed descriptions of the "<TT>logical</TT>", "<TT>physical</TT>", and "<TT>world</TT>"
  coordinate systems can be
  found  in  the  help  pages  for  the  WCSEDIT  and  WCRESET  tasks. 
  Detailed   documentation   for  the  IRAF  world  coordinate  system 
  interface MWCS can be found in  the  file  "<TT>iraf$sys/mwcs/MWCS.hlp</TT>".
  This  file  can  be  formatted  and  printed  with the command "<TT>help
  iraf$sys/mwcs/MWCS.hlp fi+ | lprint</TT>".  Information on the spectral
  coordinates systems and their suitability for use with WCSXYMATCH
  can be obtained by typing "<TT>help specwcs | lprint</TT>".
  Details of  the  FITS  header
  world  coordinate  system  interface  can  be  found in the document
  "<TT>World Coordinate Systems Representations Within  the  FITS  Format</TT>"
  by Hanisch and Wells, available from our anonymous ftp archive.
      
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Make sure that the world coordinates systems of a list of input images
  that have been registered to a reference image with the xregister task
  are identical to the world coordinate system of the reference image.
  <P>
  <PRE>
  	cl&gt; xregister @inlist refimage [200:400,200:400] shifts \<BR>
  	    output=@outlist xwindow=21 ywindow=21
  	cl&gt; wcscopy @outlist refimage
  </PRE>
  <P>
  2.  Create a data-less WCS image by specifying a new image.
  <P>
  <PRE>
  	cl&gt; wcscopy new dev$wpix
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
  tprecess,imalign,xregister,geomap,register,geotran,wcsmap,wregister,wcsedit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>