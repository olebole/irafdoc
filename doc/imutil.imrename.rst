.. _imrename:

imrename — Rename one or more images
====================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imrename -- rename one or more images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  imrename oldnames newnames
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>oldnames</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oldnames' Line='oldnames'>
  <DD>An image template specifying the names of the images to be renamed.
  </DD>
  </DL>
  <DL>
  <DT><B>newnames</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newnames' Line='newnames'>
  <DD>Either an image template specifying the new names for the images,
  or the name of the directory to which the images are to be renamed (moved).
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If verbose output is enabled a message will be printed on the standard output
  recording each rename operation.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <B>imrename</B> task renames one or more images.  The ordinary <I>rename</I>
  task cannot be used to rename images since an image may consist of more than
  one file.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
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
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcopy, imdelete, imheader
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
