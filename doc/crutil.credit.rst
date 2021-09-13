.. _credit:

credit — Interactively edit cosmic rays using an image display
==============================================================

**Package: crutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  credit -- interactively edit cosmic rays using an image display
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  credit input output
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  See parameters for <B>imedit</B>.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
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
  <H3>Examples</H3>
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
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imedit, epix
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
