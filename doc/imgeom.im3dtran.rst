.. _im3dtran:

im3dtran — Transpose a list of 3-D images
=========================================

**Package: imgeom**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  im3dtran -- Transpose a 3D image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  im3dtran input output 
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input 3d image.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The output transposed 3D image. If the output image name is the same as
  the input image name then the original image will be overwritten. The number
  of output images must equal the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B>new_x = 3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='new_x' Line='new_x = 3'>
  <DD>The new x axis.  The default (3) replaces new x with old z.
  </DD>
  </DL>
  <DL>
  <DT><B>new_y = 2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='new_y' Line='new_y = 2'>
  <DD>The new y axis = old axis.  The default (2) does not change the y axis.
  </DD>
  </DL>
  <DL>
  <DT><B>new_z = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='new_z' Line='new_z = 1'>
  <DD>The new z axis.  The default (1) replaces new z with old x.
  </DD>
  </DL>
  <DL>
  <DT><B>len_blk = 128</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='len_blk' Line='len_blk = 128'>
  <DD>The size in pixels of the linear internal subraster. Im3dtran will try to
  transpose a subraster up to len_blk cubed at one time.  Runtime is much
  faster with larger <B>len_blk</B>, but the task may run out of memory.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions taken by the task.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  IM3DTRAN transposes the input images <I>input</I> in 3 dimensions and
  writes the transposed images to <I>output</I>. The 6 possible axis 
  mappings are specified by setting the parameters <I>new_x</I>, <I>new_y</I>,
  and <I>new_z</I>.
  <P>
  IM3DTRAN can be used to rotate a datacube 90 degrees in any direction by
  combining the transpose operation with an axis  flip.  For
  example, Consider a datacube is visualized with its origin at the lower
  left front
  when seen by the viewer, with its abscissa being the x axis, its ordinate
  the y axis, and its depth the z axis, with z increasing away from the viewer
  or into the datacube [this
  is a left-handed coordinate system].  To rotate the datacube
  by 90 degrees clockwise about the y axis when viewed from the +y direction;
  the old z axis must become the new x axis, and the old x axis must become
  the new z axis, while the new y axis remains old y axis.  In this case the
  axis that must be flipped prior to transposition is the x axis as shown
  in example 2.
  <P>
  The parameter <B>len_blk</B> controls how much memory is used during the
  transpose operation.  <B>len_blk</B> elements are used in each axis at a
  time, or a cube len_blk elements on a side.  If <B>len_blk</B> is too large,
  the task will abort with an "<TT>out of memory</TT>" error.  If it is too small,
  the task can take a very long time to run.  The maximum size of len_blk
  depends on how much memory is available at the time IM3DTRAN is run,
  and the size and datatype of the image to be transposed.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Transpose axes 1 2 and 3 of a list of input images to axes 2 1 and 3 of
  a list of output images.
  <P>
  <PRE>
  	cl&gt; im3dtran image1,image2,image3 tr1,tr2,tr3 2 1 3
  </PRE>
  <P>
  2.  For an input datacube with columns = x = abscissa, lines = y = ordinate,
  and bands = z = depth increasing away from viewer, and with the image
  origin at the lower left front, rotate datacube 90 degrees clockwise
  around the y axis when viewed from +y (top):
  <P>
  <PRE>
  	cl&gt; im3dtran input[-*,*,*] output 3 2 1
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Timings</H3>
  <! BeginSection: 'TIMINGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'TIMINGS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imtranspose, imjoin, imstack, imslice
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIMINGS' 'BUGS' 'SEE ALSO'  >
  
