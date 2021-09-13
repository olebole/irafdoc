im3dtran — 3d image transpose (used for rotates as well)
========================================================

**Package: vol**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>im3dtran (Jan89)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>volumes</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>im3dtran (Jan89)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>im3dtran</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  im3dtran -- 3d image transpose, any axis to any other axis
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  im3dtran input output 
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input 3d image (datacube).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Transposed datacube.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_len_blk">len_blk = 128</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='len_blk' Line='len_blk = 128'>
  <DD>Size in pixels of linear internal subraster.  IM3DTRAN will try to transpose
  a subraster up to len_blk cubed at one time.  Runtime is much faster with
  larger <B>len_blk</B>, but the task may run out of memory.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_new_x">new_x = 3</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='new_x' Line='new_x = 3'>
  <DD>New x axis = old axis (1=x, 2=y, 3=z).  Default (3) replaces new x with old z.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_new_y">new_y = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='new_y' Line='new_y = 2'>
  <DD>New y axis = old axis.  Default (2) is identity.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_new_z">new_z = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='new_z' Line='new_z = 1'>
  <DD>New z axis = old axis.  Default (1) replaces new z with old x.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  IM3DTRAN is very similar to IMAGES.IMTRANSPOSE, except that it can accomplish
  3d image transposes.  In 3 dimensions, it is necessary to specify which old
  axes map to the new axes.  In all cases, IM3DTRAN maps old axis element 1 to
  new axis element 1, i.e. it does not flip axes, just transposes them.
  <P>
  If one wants to use IM3DTRAN to rotate a datacube 90 degrees in any direction,
  it is necessary to use a combination of flip and transpose (just like in the
  2d case).  For example, let the original datacube be visualized with its
  origin at the lower left front when seen by the viewer, with the abscissa
  being the x axis (dim1), ordinate the y axis (dim2), and depth being the
  z axis (dim3), z increasing away from the viewer or into the datacube [this
  is a left-handed coordinate system].  One then wants to rotate the datacube
  by 90 degrees clockwise about the y axis when viewed from +y (the "<TT>top</TT>");
  this means the old z axis becomes the new x axis, and the old x axis becomes
  the new z axis, while new y remains old y.  In this case the axis that must
  be flipped prior to transposition is the <B>x axis</B>; see Example 1.
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  1.  For an input datacube with columns = x = abscissa, lines = y = ordinate,
      and bands = z = depth increasing away from viewer, and with the image
      origin at the lower left front, rotate datacube 90 degrees clockwise
      around the y axis when viewed from +y (top):
  <P>
      cl&gt; im3dtran input[-*,*,*] output 3 2 1
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_timings">TIMINGS</A></H2>
  <! BeginSection: 'TIMINGS'>
  <UL>
  <P>
  [Not available yet]
  <P>
  </UL>
  <! EndSection:   'TIMINGS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  [Not available yet]
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  pvol i2sun
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIMINGS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>