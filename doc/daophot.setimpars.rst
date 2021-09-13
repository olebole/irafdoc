setimpars — Save/restore parameter sets for a particular image
==============================================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>setimpars (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>setimpars (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>setimpars</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  setimpars -- save / restore the daophot parameters for a particular image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  setimpars image restore update
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The image for which the daophot parameters are to be saved or restored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_restore">restore</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='restore' Line='restore'>
  <DD>If restore = yes, parfile is "<TT></TT>", and the file "<TT>image.pars</TT>" exists, SETIMPARS
  sets the current algorithm parameters by reading in the file "<TT>image.pars</TT>". If
  parfile is not "<TT></TT>", then restore is automatically assumed to be yes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update'>
  <DD>If update = yes, SETIMPARS saves the new current values of the DAOPHOT algorithm
  parameters in the file <I>image.pars</I> and any previously existing file of the same name is overwritten.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_review">review = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='review' Line='review = no'>
  <DD>Review and/or edit the values of the parameters in the parameter sets DATAPARS,
  FINDPARS, CENTERPARS, FITSKYPARS, PHOTPARS, and DAOPARS by calling up the EPAR
  task for each of the named parameter sets in turn?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_parfile">parfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='parfile' Line='parfile'>
  <DD>The name of the input file containing the values of the DAOPHOT algorithm
  parameters to be restored. If defined <I>parfile</I> must have been written
  by SETIMPARS.  If parfile is null ("<TT></TT>"), SETIMPARS searches for a file named
  <I>image.pars</I> in the user's current directory. If no file is found, the
  DAOPHOT algorithm parameters are restored from the files <I>datapars</I>,
  <I>findpars</I>, <I>centerpars</I>, <I>fitskypars</I>, <I>photpars</I>, and
  <I>daopars</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_datapars">datapars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datapars' Line='datapars = ""'>
  <DD>The name of the file containing the DATAPARS parameter values. Datapars must be
  a named DATAPARS parameter set file written by the EPAR task, or "<TT></TT>" in which
  case the default DATAPARS parameter set in the user's uparm directory is used.
  If the parameter <I>unlearn</I> is "<TT>yes</TT>" and datapars is "<TT></TT>", DATAPARS is
  unlearned.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_findpars">findpars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='findpars' Line='findpars = ""'>
  <DD>The name of the file containing the FINDPARS parameter values. Findpars
  must be a named FINDPARS parameter set file written by the EPAR task, or "<TT></TT>"
  in which case the default FINDPARS parameter set in the user's uparm
  directory is used. If the parameter <I>unlearn</I> is "<TT>yes</TT>" and findpars
  is "<TT></TT>", FINDPARS is unlearned.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_centerpars">centerpars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='centerpars' Line='centerpars = ""'>
  <DD>The name of the file containing the CENTERPARS parameter values.  Centerpars
  must be a named CENTERPARS parameter set file written by the EPAR task, or "<TT></TT>"
  in which case the default CENTERPARS parameter set in the user's uparm
  directory is used. If the parameter <I>unlearn</I> is "<TT>yes</TT>" and centerpars
  is "<TT></TT>", CENTERPARS is unlearned.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fitskypars">fitskypars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitskypars' Line='fitskypars = ""'>
  <DD>The name of the file containing the FITSKYPARS parameter values. Fitskypars
  must be a named FITSKYPARS parameter set file written by the EPAR task, or "<TT></TT>"
  in which case the default FITSKYPARS parameter set in the user's uparm
  directory is used. If the parameter <I>unlearn</I> is "<TT>yes</TT>" and fitskypars
  is "<TT></TT>", FITSKYPARS is unlearned.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_photpars">photpars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photpars' Line='photpars = ""'>
  <DD>The name of the file containing the PHOTPARS parameter values. Photpars must be
  a named PHOTPARS parameter set file written by the EPAR task, or "<TT></TT>" in which
  case the default PHOTPARS parameter set in the user's uparm directory is used.
  If the parameter <I>unlearn</I> is "<TT>yes</TT>" and photpars is "<TT></TT>", PHOTPARS is
  unlearned.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_daopars">daopars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='daopars' Line='daopars = ""'>
  <DD>The name of the file containing the DAOPARS parameter values. Daopars must be a
  named DAOPARS parameter set file written by the EPAR task, or "<TT></TT>" in which case
  the default DAOPARS parameter set in the user's uparm directory is used. If the
  parameter <I>unlearn</I> is "<TT>yes</TT>" and daopars is "<TT></TT>", DAOPARS is unlearned.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_unlearn">unlearn = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='unlearn' Line='unlearn = no'>
  <DD>Return the values of the parameters in the parameter sets DATAPARS, FINDPARS,
  CENTERPARS, FITSKYPARS, PHOTPARS, and DAOPARS to their default values?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  SETIMPARS saves and restores the DAOPHOT task and algorithm parameters for the
  image <I>image</I>. On startup SETIMPARS initializes all the DAOPHOT package
  input and output coordinates and photometry file names, input and output images,
  and input and output plot files to their default values or <I>image</I> whichever
  is appropriate. Next SETIMPARS reads in the values of the algorithm parameters
  from <I>parfile</I> if it is defined, or from the file <I>image.pars</I> if it
  exists and <I>restore</I> is "<TT>yes</TT>", or from the named parameter set files
  <I>datapars</I>, <I>findpars</I>, <I>centerpars</I>, <I>fitskypars</I>,
  <I>photpars</I>, and <I>daopars</I> if they exist, or from the default parameters
  sets in the user's uparm directory. If <I>unlearn</I> is "<TT>yes</TT>", these default
  parameter sets are unlearned.
  <P>
  If <I>review</I> is "<TT>yes</TT>", the user can review and or edit the newly set
  algorithm parameters in DATAPARS, FINDPARS, CENTERPARS, FITSKYPARS, PHOTPARS,
  and DAOPARS using the IRAF EPAR task.
  <P>
  If <I>update</I> is "<TT>yes</TT>", SETIMPARS saves the new current values of the DAOPHOT
  algorithm parameters DATAPARS, FINDPARS, CENTERPARS, FITSKYPARS, PHOTPARS, and
  DAOPARS in the file <I>image.pars</I>. Any previously existing file of the same
  name is overwritten.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Save the current values of the daophot task and algorithm parameters for
  the image m92v.
  <P>
  <PRE>
  	da&gt; setimpars m92v no yes
  <P>
  	    ... m92v parameters are saved in m92v.pars
  </PRE>
  <P>
  2. Make some minor alterations in the current values of the m92v algorithm
  parameters and save the new parameters set.
  <P>
  <PRE>
  	da&gt; setimpars m92v no yes
  <P>
  	    ... m92v parameters are saved in new version of m92v.pars
  </PRE>
  <P>
  3. Begin work on the image m92b. Initialize the values of the daophot task
  and algorithm parameters for m92b using those stored for m92v. After doing
  some preliminary editing and reductions for m92b, save the parameters,
  and return to work on m92v.
  <P>
  <PRE>
  	da&gt; setimpars m92b yes no parfile=m92v.pars
  <P>
  	    ... current parameters for m92v are set using saved
  		m92v parameters
  <P>
  	da&gt; daoedit m92b
  <P>
  	    ... edit the parameters as necessary for the new image
  <P>
  	da&gt; daofind m92b
  <P>
  	    ... find the stars in m92b
  <P>
  	da&gt; phot m92b
  <P>
  	    ... do the initial photometry for stars in m92b
  <P>
  	da&gt; setimpars m92b no yes
  <P>
  	    ... current m92b parameters are saved in m92b.pars
  <P>
  	da&gt; setimpars m92v yes no
  <P>
  	    ... m92v parameters are restored from m92v.pars
  </PRE>
  <P>
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
  daoedit,datapars,findpars,centerpars,fitskypars,photpars,daopars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>