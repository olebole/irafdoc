imrename — Rename one or more images
====================================

**Package: imutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imrename (Apr89)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imrename (Apr89)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imrename</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imrename -- rename one or more images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  imrename oldnames newnames
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_oldnames">oldnames</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oldnames' Line='oldnames'>
  <DD>An image template specifying the names of the images to be renamed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_newnames">newnames</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newnames' Line='newnames'>
  <DD>Either an image template specifying the new names for the images,
  or the name of the directory to which the images are to be renamed (moved).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If verbose output is enabled a message will be printed on the standard output
  recording each rename operation.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <B>imrename</B> task renames one or more images.  The ordinary <I>rename</I>
  task cannot be used to rename images since an image may consist of more than
  one file.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Rename the image "<TT>pix</TT>" to "<TT>wfpc.1</TT>".
  <P>
  	cl&gt; imrename pix wfpc.1
  <P>
  2. Rename all the "<TT>nite1*</TT>" images as "<TT>nite1_c</TT>".
  <P>
  	cl&gt; imrename nite1.*.imh nite1%%_c%.*.imh
  <P>
  3. Move the images in logical directory "<TT>dd</TT>" to the current directory.
  <P>
  	cl&gt; imrename dd$*.imh .
  <P>
  4. Move the pixel files associated with the images in the current directory
  to a subdirectory "<TT>pix</TT>" of the current directory.
  <P>
  <PRE>
  	cl&gt; reset imdir = HDR$pix/
  	cl&gt; imrename *.imh .
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcopy, imdelete, imheader
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>