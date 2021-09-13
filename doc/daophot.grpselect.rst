.. _grpselect:

grpselect — Select groups of a specified size from a daophot database
=====================================================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  grpselect -- select groups from a group file by group size
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  grpselect ingroupfile outgroupfile min_group max_group
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>ingroupfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ingroupfile' Line='ingroupfile'>
  <DD>The list of input group files. Ingroupfile must have been written by the
  DAOPHOT PSF, GROUP, or NSTAR tasks. Ingroupfile may be an APPHOT/DAOPHOT text
  database or an STSDAS table.
  </DD>
  </DL>
  <DL>
  <DT><B>outgroupfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outgroupfile' Line='outgroupfile'>
  <DD>The list of output group files. There must be one output group file for every
  input group file. Outgroupfile has the same file type as <I>ingroupfile</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>min_group</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='min_group' Line='min_group'>
  <DD>The minimum group size to select from the input group file(s).
  </DD>
  </DL>
  <DL>
  <DT><B>max_group</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='max_group' Line='max_group'>
  <DD>The maximum group size to select from the input group file(s).
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = "<TT>)_.verbose</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print messages about the progress of the task? Verbose may be set to the value
  of the daophot package parameter (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
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
  <H3>Examples</H3>
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
  group
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
