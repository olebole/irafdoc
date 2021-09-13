.. _ccdgroups:

ccdgroups — Group CCD images into image lists
=============================================

**Package: ccdred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ccdgroups -- Group CCD images into image lists
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  ccdgroups images output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of CCD images to be grouped.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output root group filename.  The image group lists will be put in files
  with this root name followed by a number.
  </DD>
  </DL>
  <DL>
  <DT><B>group = "<TT>ccdtype</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='group' Line='group = "ccdtype"'>
  <DD>Group type.  There are currently four grouping types:
  <DL>
  <DT><B>ccdtype</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ccdtype' Line='ccdtype'>
  <DD>Group by CCD image type.
  </DD>
  </DL>
  <DL>
  <DT><B>subset</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='subset' Line='subset'>
  <DD>Group by subset parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>position</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='position' Line='position'>
  <DD>Group by position in right ascension (in hours) and declination (in degrees).
  The groups are defined by a radius parameter (in arc seconds).
  </DD>
  </DL>
  <DL>
  <DT><B>title</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='title' Line='title'>
  <DD>Group by identical titles.
  </DD>
  </DL>
  <DL>
  <DT><B>date</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='date' Line='date'>
  <DD>Group by identical dates.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>radius = 60.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 60.'>
  <DD>Grouping radius when grouping by positions.  This is given in arc seconds.
  </DD>
  </DL>
  <DL>
  <DT><B>ccdtype = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdtype' Line='ccdtype = ""'>
  <DD>CCD image types to select from the input image list.  If null ("<TT></TT>") then
  all image types are used.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The input images, possible restricted to a particular CCD image type,
  are grouped into image lists.  The "<TT>ccdtype</TT>" or "<TT>subset</TT>" groups
  produce output image lists with the given root name and the CCD type
  or subset as an extension (without a period).  For the other group
  types the
  image lists have file names given by
  the root output name and a numeric extension (without a period).
  If the package parameter <I>ccdred.verbose</I> is yes then the
  image name and output group list is printed for each image.  The image lists can
  be used with the @ list feature for processing separate groups of observations.
  Note that grouping by CCD image type and subset is often not necessary since
  the <B>ccdred</B> tasks automatically use this information (see
  <B>ccdtypes</B> and <B>subsets</B>).
  <P>
  Besides CCD image type and subsets there are currently three ways to
  group images.  These are by position in the sky, by title, and by
  date.  Further groups may be added as suggested.  The title grouping is
  useful if consistent titles are used when taking data.  The date
  grouping is useful if multiple nights of observations are not organized
  by directories (it is recommended that data from separate nights be
  kept in separate directories).  The position grouping finds
  observations within a given radius on the sky of the first member of
  the group (this is not a clustering algorithm).  The right ascension
  and declination coordinates must be in standard units, hours and
  degrees respectively.  The grouping radius is in arc seconds.  This
  grouping type is useful for making sets of data in which separate
  calibration images are taken at each position.
  <P>
  The date, title, and coordinates are accessed through the instrument
  translation file.  The standard names used are "<TT>date-obs</TT>", "<TT>title</TT>", "<TT>ra</TT>",
  and "<TT>dec</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. For each object 5 exposures were taken to be combined in order to remove
  cosmic rays.  If the titles are the same then (with ccdred.verbose=yes):
  <P>
  <PRE>
      cl&gt; ccdgroups *.imh group group=title ccdtype=object
      ccd005.imh  --&gt; group1
      ccd006.imh  --&gt; group1
      ccd007.imh  --&gt; group1
      ccd008.imh  --&gt; group1
      ccd009.imh  --&gt; group1
      ccd012.imh  --&gt; group2
      ccd013.imh  --&gt; group2
      ccd014.imh  --&gt; group2
      ccd015.imh  --&gt; group2
      ccd016.imh  --&gt; group2
      [... etc ...]
      cl&gt; combine @group1 obj1 proc+
      cl&gt; combine @group2 obj2 proc+
      [... etc ...]
  </PRE>
  <P>
  Note the numeric suffixes to the output root name "<TT>group</TT>".
   
  2. CCD observations were made in groups with a flat field, the object, and
  a comparison spectrum at each position.  To group and process this data:
  <P>
  <PRE>
      cl&gt; ccdgroups *.imh obs group=position &gt;&gt; logfile
      cl&gt; ccdproc @obs1
      cl&gt; ccdproc @obs2
      cl&gt; ccdproc @obs3
  </PRE>
  <P>
  Since no flat field is specified for the parameter <I>ccdproc.flat</I>
  the flat field is taken from the input image list.
  <P>
  3. If for some reason you want to group by date and position it is possible
  to use two steps.
  <P>
  <PRE>
      cl&gt; ccdgroups *.imh date group=date
      cl&gt; ccdgroups @data1 pos1
      cl&gt; ccdgroups @data2 pos2
  </PRE>
   
  4. To get groups by CCD image type:
   
  <PRE>
      cl&gt; ccdgroups *.imh "" group=ccdtype
      ccd005.imh  --&gt; zero
      ccd006.imh  --&gt; zero
      ccd007.imh  --&gt; zero
      ccd008.imh  --&gt; dark
      ccd009.imh  --&gt; flat
      ccd012.imh  --&gt; flat
      ccd013.imh  --&gt; object
      ccd014.imh  --&gt; object
      ccd015.imh  --&gt; object
      ccd016.imh  --&gt; object
      [... etc ...]
  </PRE>
   
  Note the use of a null root name and the extension is the standard
  CCDRED types (not necessarily those used in the image header).
   
  5. To get groups by subset:
   
  <PRE>
      cl&gt; ccdgroups *.imh filt group=subset
      ccd005.imh  --&gt; filt
      ccd006.imh  --&gt; filtB
      ccd007.imh  --&gt; filtB
      ccd008.imh  --&gt; filtB
      ccd009.imh  --&gt; filtV
      ccd012.imh  --&gt; filtV
      ccd013.imh  --&gt; filtV
      ccd014.imh  --&gt; filtB
      ccd015.imh  --&gt; filtB
      ccd016.imh  --&gt; filtB
      [... etc ...]
  </PRE>
   
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdlist, ccdtypes, instruments, subsets
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
