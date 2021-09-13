.. _imcopy:

imcopy — Copy an image
======================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imcopy -- copy images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  imcopy input output
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Images to be copied.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output images or directory.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print each operation as it takes place?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Each of the input images, which may be given as a general image template
  including sections, is copied to the corresponding output image list,
  which may also be given as an image template, or the output directory.
  If the output is a list of images then the number of input images must be
  equal to the number of output images and the input and output images are paired
  in order.  If the output image name exists and contains a section then the
  input image (provided it is the same size as the section) will be copied
  into that section of the input image.  If the output image name does not
  have a section specification and if it is the same as the input image name
  then the input image is copied to a temporary file which replaces the input
  image when the copy is successfully concluded.  Note that these are the only
  cases where clobber checking is bypassed; that is, if an output image name
  is not equal to the input image name or a subsection of an existing image
  and the file already exists then a clobber error will occur if
  clobber checking is in effect.
  <P>
  The verbose options prints for each copy lines of the form:
  <PRE>
  <P>
  input image -&gt; output image
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. For a simple copy of an image:
  <P>
  	cl&gt; imcopy image imagecopy
  <P>
  2. To copy a portion of an image:
  <P>
  	cl&gt; imcopy image[10:20,*] subimage
  <P>
  3. To copy several images:
  <P>
  	cl&gt; imcopy image1,image2,frame10 a,b,c
  <P>
  4. To trim an image:
  <P>
  	cl&gt; imcopy image[10:20,*] image
  <P>
  In the above example the specified section of the input image replaces the
  original input image.  To trim several images using an image template:
  <P>
  	cl&gt; imcopy frame*[1:512,1:512] frame*
  <P>
  In this example all images beginning with "<TT>frame</TT>" are trimmed to 512 x 512.
  <P>
  5. To copy a set of images to a new directory:
  <P>
  <PRE>
  	cl&gt; imcopy image* directory
  			or
  	cl&gt; imcopy image* directory$
  			or
  	cl&gt; imcopy image* osdirectory
  </PRE>
  <P>
  where "<TT>osdirectory</TT>" is an operating system directory name (i.e. /user/me
  in UNIX).
  <P>
  6. To copy a section of an image in an already existing image of
     sufficient size to contain the input section.
  <P>
  <PRE>
  	cl&gt; imcopy image[1:512,1:512] outimage[257:768,257:768]
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The distinction between copying to a section of an existing image
  and overwriting a input image is rather inobvious.
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  >
  
