.. _astradius:

astradius — Find images within a circle on the sky
==================================================

**Package: astutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  astradius -- find images within a circle on the sky
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  astradius images racenter deccenter epcenter radius
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images for which the radius to a point on the sky is to be
  determined.
  </DD>
  </DL>
  <DL>
  <DT><B>racenter, deccenter, epcenter</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='racenter' Line='racenter, deccenter, epcenter'>
  <DD>Right ascension in hours, declination in degrees, and epoch of a position
  on the sky to use as the center of a circle.
  </DD>
  </DL>
  <DL>
  <DT><B>radius</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius'>
  <DD>Search radius in arc seconds about the center position.
  </DD>
  </DL>
  <DL>
  <DT><B>keywpars = "<TT></TT>" (pset)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keywpars' Line='keywpars = "" (pset)'>
  <DD>Parameter set defining the image header keywords.  This task requires
  keywords for the right ascension, declination, and epoch.  If
  there is no epoch in the image header keywords for the date of observation
  and the universal time are used for the epoch.  The default parameter
  set (specified by the empty string) is <B>keywpars</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>commands = "<TT>astutil$astradius.dat</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='commands' Line='commands = "astutil$astradius.dat"'>
  <DD>Command file used to compute the distance from the coordinate center
  and print a result if the distance is less than the specified radius.
  The command file uses the syntax described for <B>astcalc</B>.
  Users may copy and modify this file if desired.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Astradius</B> computes the spherical distance from a specified point on
  the sky for each image in a list of images (<I>images</I>).  The point on
  the sky is specified by the parameters <I>racenter</I>, <I>deccenter</I>, and
  <I>epcenter</I> which give a right ascension in hours, a declination in
  degrees, and an epoch.  Each image is required to have keywords for the
  right ascension (hours), declination (degrees), and epoch.  However, if no
  epoch is defined in the image header then an epoch is computed from the
  observation date and universal time.  The spherical distance is compared to
  a specified radius (<I>radius</I>) in arc seconds.  If the distance is less
  than the radius the image name and title are printed.
  <P>
  The image header keywords giving the observation coordinates are defined
  by the parameter set selected with the <I>keywpars</I> parameter.
  If no value is given then the parameters from the <B>keywpars</B>
  parameter set task are used.  The keywords required are those
  select by the <I>keywpars.ra</I>, <I>keywpars.dec</I>, and
  <I>keywpars.epoch</I>.  If the epoch is absent or zero then the
  keywords selected by <I>keywpars.date_obs</I> and <I>keywpars.ut</I>
  are used to compute an epoch.
  <P>
  <B>Astradius</B> is a simple script which calls <B>astcalc</B>.  The
  command file is specified by the parameter <I>commands</I>.  The
  default file precesses the observation coordinates to the epoch
  of the search center coordinates and then computes the spherical
  distance between the search center and the observation.  Finally
  it tests the distance against the specified radius and prints
  the image name and title if the observation is within the radius.
  Users may copy the default command file and modify it.  The
  command syntax is described in the help for <B>astcalc</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Page the script task and the command file.
  <P>
  <PRE>
      cl&gt; page astutil$astradius.cl,astutil$astradius.dat
      # ASTRADIUS -- Find images within a radius.
  <P>
      procedure astradius (images, racenter, deccenter, epcenter, radius)
  <P>
      string  images = ""             {prompt="List of images"}
      string  racenter = ""           {prompt="RA center (hours)"}
      string  deccenter = ""          {prompt="DEC center (degrees)"}
      real    epcenter = 2000.        {prompt="Epoch of center"}
      real    radius = 60.            {prompt="Radius in arc seconds"}
      pset    keywpars = ""           {prompt="Keywords for RA, DEC, EPOCH\n"}
  <P>
      file    commands = "astutil$astradius.dat"      {prompt="ASTCALC file"}
  <P>
      begin
  	    astcalc (commands=commands, images=images, table="", verbose=no)
      end
  <P>
       Print images which are within a given radius in the sky.
  <P>
      # Get parameters.
      racenter = clget ("astradius.racenter")
      deccenter = clget ("astradius.deccenter")
      epcenter = clget ("astradius.epcenter")
      radius = clget ("astradius.radius")
      ra = imget(clget("keywpars.ra"))
      dec = imget(clget("keywpars.dec"))
  <P>
      epoch = imget(clget("keywpars.epoch"))
      if (str(epoch) == "" || real(epoch) == 0.)
  	date = imget(clget("keywpars.date_obs"))
  	ut = imget(clget("keywpars.ut"))
  	epoch = epoch (date, ut)
      endif
  <P>
      # Precess image coordinates to center epoch and compute separation.
      radec = precess (ra, dec, epoch, epcenter)
      ra1 = ra_precess (ra, dec, epoch, epcenter)
      dec1 = dec_precess (ra, dec, epoch, epcenter)
      sep = arcsep (racenter, deccenter, ra1, dec1)
  <P>
      # Print result if within radius.
      if (sep &lt; real (radius))
  	printf ("%-15s %s\n", $I, imget ("title"))
      endif
  </PRE>
  <P>
  2. Find images within an arc minute of a particular position.
  <P>
  <PRE>
  cl&gt; astradius
  List of images: *.imh
  RA center (hours): 13:31
  DEC center (degrees): 47:00
  Epoch of center (2000.):
  Radius in arc seconds (60.):
  obj0020.imh         m51 B 600s
  obj0021.imh         m51 V 600s
  obj0022.imh         m51 R 600s
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>ASTRADIUS V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='ASTRADIUS' Line='ASTRADIUS V2.11'>
  <DD>This task is new in this release.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  astcalc, hselect
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
