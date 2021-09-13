.. _polypars:

polypars — Edit the polyphot parameters
=======================================

**Package: apphot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  polypars -- edit the polygonal aperture photometry parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  polypars
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>zmag = 25.00</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zmag' Line='zmag = 25.00'>
  <DD>The zero point offset for the magnitude scale.
  </DD>
  </DL>
  <DL>
  <DT><B>mkpolygon = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mkpolygon' Line='mkpolygon = no'>
  <DD>Draw the polygons on the screen.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The zero point of the magnitude scale is determined by <I>zmag</I>.
  <P>
  If the <I>mkpolygon</I> switch is enabled polygons are marked on the screen.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List the polygonal aperture photometry parameters.
  <P>
  <PRE>
  	ap&gt; lpar polypars
  </PRE>
  <P>
  2. Edit the polygonal aperture photometry parameters.
  <P>
  <PRE>
  	ap&gt; polypars
  </PRE>
  <P>
  3. Edit the POLYPARS parameters from within the POLYPHOT task.
  <P>
  <PRE>
      da&gt; epar polyphot
  <P>
  	... edit a few polyphot parameters
  <P>
  	... move to the polypars parameter and type :e
  <P>
  	... edit the polypars parameters and type :wq
  <P>
  	... finish editing the polyphot parameters and type :wq
  </PRE>
  <P>
  4. Save the current POLYPARS parameter set in a text file polynite1.par.
  This can also be done from inside a higher level task as in the
  above example.
  <P>
  <PRE>
      da&gt; polypars
  <P>
  	... edit some parameters
  <P>
  	... type ":w polynite1.par"  from within epar
  <P>
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  polyphot. polymark
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
