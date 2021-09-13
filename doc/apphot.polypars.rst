polypars — Edit the polyphot parameters
=======================================

**Package: apphot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>polypars (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.apphot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>polypars (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>polypars</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  polypars -- edit the polygonal aperture photometry parameters
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  polypars
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_zmag">zmag = 25.00</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zmag' Line='zmag = 25.00'>
  <DD>The zero point offset for the magnitude scale.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mkpolygon">mkpolygon = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mkpolygon' Line='mkpolygon = no'>
  <DD>Draw the polygons on the screen.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The zero point of the magnitude scale is determined by <I>zmag</I>.
  <P>
  If the <I>mkpolygon</I> switch is enabled polygons are marked on the screen.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
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
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  polyphot. polymark
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>