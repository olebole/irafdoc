credit — Interactively edit cosmic rays using an image display
==============================================================

**Package: crutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>credit (Apr98)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.crutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>credit (Apr98)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>credit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  credit -- interactively edit cosmic rays using an image display
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  credit input output
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  See parameters for <B>imedit</B>.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task is a version of <B>imedit</B>.  See the help for that task
  for a description of the parameters and algorithms.
  <P>
  For the purpose of editing cosmic rays the most useful editing option
  is <TT>'b'</TT> to replace cosmic rays in a circular annulus using local sky
  values.  This can be done interactively or using a list of positions
  along with the <I>default</I> parameter value.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To replace cosmic rays interactively.
  <P>
  <PRE>
      cl&gt; credit obj012 crobj012 crmask012
  </PRE>
  <P>
  2.  To use a two column list of positions and remove the cosmic rays using
  the <TT>'b'</TT> key algorithm.
  <P>
  <PRE>
      cl&gt; credit obj012 crobj012 cursor=crlist.dat display-
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imedit, epix
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>