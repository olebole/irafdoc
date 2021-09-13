grpselect — Select groups of a specified size from a daophot database
=====================================================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>grpselect (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>grpselect (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>grpselect</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  grpselect -- select groups from a group file by group size
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  grpselect ingroupfile outgroupfile min_group max_group
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_ingroupfile">ingroupfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ingroupfile' Line='ingroupfile'>
  <DD>The list of input group files. Ingroupfile must have been written by the
  DAOPHOT PSF, GROUP, or NSTAR tasks. Ingroupfile may be an APPHOT/DAOPHOT text
  database or an STSDAS table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outgroupfile">outgroupfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outgroupfile' Line='outgroupfile'>
  <DD>The list of output group files. There must be one output group file for every
  input group file. Outgroupfile has the same file type as <I>ingroupfile</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_min_group">min_group</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='min_group' Line='min_group'>
  <DD>The minimum group size to select from the input group file(s).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_max_group">max_group</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='max_group' Line='max_group'>
  <DD>The maximum group size to select from the input group file(s).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = "<TT>)_.verbose</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print messages about the progress of the task? Verbose may be set to the value
  of the daophot package parameter (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  GRPSELECT creates a new GROUP file <I>outgroupfile</I> by selecting groups from
  the input GROUP file <I>ingroupfile</I> within a range of group sizes specified
  by <I>min_group</I> and <I>max_group</I>. If <I>ingroupfile</I> is a DAOPHOT text
  database, <I>outgroupfile</I> is a text database. Conversely if <I>ingroupfile</I>
  is a DAOPHOT STSDAS table database, <I>outgroupfile</I> is an STSDAS table 
  database.
  <P>
  A typical use for GRPSELECT is to create a new database containing only groups
  which are less than the value of the <I>maxgroup</I> parameter in the DAOPARS
  task for direct input into the NSTAR task.  The remaining stars in the larger
  groups are reduced by running GRPSELECT once more, selecting only groups
  greater than <I>maxgroup</I>, rerunning GROUP on the output with a less
  stringent value of the DAOPARS parameter task <I>critovlap</I> to reduce the
  group sizes and inputting the result into NSTAR.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Select groups with between 1 and 70 stars from the GROUP task output file
  ypix.grp.1 and write them into a new file named ypixsmall.grp.
  <P>
  <PRE>
      da&gt; grpselect ypix.grp.1 ypixsmall.grp 1 70
  <P>
  </PRE>
  <P>
  2. Select groups larger than 70 from the same input group file and rerun
  group with a new value of the critoverlap parameter on the results. 
  <P>
  <PRE>
      da&gt; grpselect ypix.grp.1 ypixlarge.grp 71 400
      da&gt; group dev$ypix ypixlarge.grp ypix.psf.1 default crit=5.0
  <P>
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
  group
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>