imgets — Return the value of an image header parameter as a string
==================================================================

**Package: imutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imgets (Jan85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imgets (Jan85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imgets</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imgets -- get the value of an image header parameter as a string
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  imgets image param
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Name of the image to be accessed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_param">param</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='param' Line='param'>
  <DD>Name of the parameter whose value is to be returned.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_value">value = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value = ""'>
  <DD>The value of the parameter, returned as a string.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The value of the parameter <I>param</I> of the image <I>image</I> is returned
  as a string in the output parameter <I>value</I>.  The CL type coercion
  functions <I>int</I> and <I>real</I> may be used to decode the returned
  value as an integer or floating point value.  Both standard image header
  parameters and special application or instrument dependent parameters may be
  accessed.  If the parameter cannot be found a warning message is printed and
  the value "<TT>0</TT>" is returned.  Parameter names are case sensitive.
  <P>
  The following standard image header parameters may be accessed with
  <B>imgets</B>:
  <P>
  <PRE>
  	i_pixtype			pixel type (short, real, etc.)
  	i_naxis				number of dimensions
  	i_naxis[1-7]			length of the axes (x=1,y=2)
  	i_minpixval			minimum pixel value or INDEF
  	i_maxpixval			maximum pixel value or INDEF
  	i_title				image title string
  	i_pixfile			pixel storage file name
  </PRE>
  <P>
  This task is most useful for image parameter access from within CL scripts.
  The task <B>imheader</B> is more useful for just looking at the image header
  parameters.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Fetch the instrument parameter "<TT>HA</TT>" (hour angle) from the image header of
  the image "<TT>nite1.1001</TT>", and compute and print the hour angle in degrees:
  <P>
  <PRE>
  <PRE>
  	cl&gt; imgets nite1.1001 HA
  	cl&gt; = real(imgets.value) * 15.0
  	42.79335
  </PRE>
  </PRE>
  <P>
  2. Print the number of pixels per line in the same image.
  <P>
  <PRE>
  <PRE>
  	cl&gt; imgets nite1.1001 i_naxis1
  	cl&gt; = int(imgets.value)
  	1024
  </PRE>
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imheader, hedit, hselect
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>