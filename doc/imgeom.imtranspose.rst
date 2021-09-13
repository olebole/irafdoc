imtranspose — Transpose a list of 2-D images
============================================

**Package: imgeom**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imtranspose (Aug84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imgeom</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imtranspose (Aug84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imtranspose</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imtranspose -- transpose two dimensional images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  imtranspose input output
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be transposed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output transposed images. If the output image name is the same as
  the input image name then the output image will replace the input image.
  The number of output images must be the same as the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_len_blk">len_blk = 512</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='len_blk' Line='len_blk = 512'>
  <DD>The one dimensional length of the transpose blocks.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Imtranspose transposes the list of images in input by interchanging
  their rows and columns and writing the results to images specified in
  output. The number of input and output images must be the same.
  <P>
  The transpose is done in square blocks whose dimensions are equal <I>len_blk</I>.
  <P>
  The imtranspose tasks can be used to perform counter-clockwise or
  clockwise ninety degree rotations by flipping the y or x axis respectively
  in the input image section specification.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To transpose an image:
  <P>
  	cl&gt; imtranspose image1 image2
  <P>
  2. To transpose an image in place:
  <P>
  	cl&gt; imtranspose image1 image1
  <P>
  3. To rotate an image 90 degrees counter-clockwise and clockwise:
  <P>
  	cl&gt; imtranspose image1[*,-*] image2
  <P>
  	cl&gt; imtranspose image1[-*,*] image2
  <P>
  3. To transpose a set of 3 images listed 1 per line in the file imlist to
  the new images trans001, trans002, and trans003:
  <P>
  	cl&gt; imtranspose @imlist trans001,trans002,trans003
  <P>
  4. To transpose a set of images in place:
  <P>
  	cl&gt; imtranspose frame* frame*
  <P>
  5. To rotate an image 90 degrees counter-clockwise in place:
  <P>
  	cl&gt; imtranspose image[*,-*] image
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  It is currently not legal to transpose images with a wcs type of MULTISPEC.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>