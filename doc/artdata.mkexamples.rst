.. _mkexamples:

mkexamples — Make artificial data examples
==========================================

**Package: artdata**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkexamples - Make artificial data example images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkexamples name image
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>name</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='name' Line='name'>
  <DD>Example name (abbreviations are not allowed):
  <P>
  <PRE>
       galcluster - Galaxy cluster
         globular - Globular cluster
         galfield - Galaxy field
        starfield - Starfield
  <P>
           henear - Helium-neon-argon spectrum (uncalibrated)
         heneardc - Helium-neon-argon spectrum (calibrated)
  <P>
            ecarc - Echelle thorium-argon spectrum (uncalibrated)
          ecarcdc - Echelle thorium-argon spectrum (calibrated)
  <P>
         spectrum - Absorption spectrum (calibrated)
          echelle - Echelle absorption spectrum (calibrated)
  <P>
          ecarc2d - Echelle thorium-argon slit spectrum
          ecobj2d - Echelle object slit spectrum
  <P>
            lsarc - Long slit helium-neon-argon spectrum
  	  lsobj - Long slit object spectrum
  <P>
       multifiber - Multifiber spectrum
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Output image name.
  </DD>
  </DL>
  <DL>
  <DT><B>oseed = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oseed' Line='oseed = 1'>
  <DD>Random number seed affecting object generation.  Different object seeds
  will produces different examples of objects or spectral lines or number
  of apertures/orders.  This
  usually modifies the seed parameters in <B>starlist</B>, <B>gallist</B>,
  and <B>mk1dspec</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>nseed = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nseed' Line='nseed = 1'>
  <DD>Random number noise seed.  Different noise seeds will produce examples
  with different noise, generally of the same level but simply having
  a different pattern.  This is usually the seed parameter in
  <B>mkobjects</B> or <B>mknoise</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>comments = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='comments' Line='comments = no'>
  <DD>Add comments to the image header describing various artificial data
  parameters?
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print message indicating image being created?
  </DD>
  </DL>
  <DL>
  <DT><B>errors = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='errors' Line='errors = yes'>
  <DD>Print messages if the image already exists, bad example name, or other
  errors?
  </DD>
  </DL>
  <DL>
  <DT><B>list = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='list' Line='list = no'>
  <DD>List script used to generate the example rather than create an image?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The task is intended to generate a few artificial images of various types to
  be used as examples of the artificial data package and in various
  demonstrations and test procedures for other packages.  The examples are not 
  exhaustive.  The only adjustable parameters are variations of the
  random number seeds.  Varying the noise seed allows several observations
  of the same example while varying the object seed allows several observations
  of different "<TT>fields</TT>", spectral lines, or number of apertures/orders.
  <P>
  If the example name is not given on the command line a menu of example
  names is first printed and then a prompt for the name is given.
  The name may be a submenu or an example.  The
  names may not be abbreviated.  If desired the simple command
  script used to generate the example may be paged.  Otherwise the
  specified image will be generated.  Keep in mind that some of the
  examples (particularly those generating galaxy images) may take a
  significant amount of time.  On a SPARCstation the examples all run in
  under five minutes.  A check is made to see if the image already
  exists.  If the image exists then the task exits.  If the <I>errors</I>
  parameter is specified an error message is printed.
  <P>
  A reason for the error output to be turned off is in test scripts and
  demonstrations where the image will be created the first time and reused
  in further tests or demonstrations.  In such cases the verbose option is
  generally set so that the user is aware that an image is being created
  and some delay is to be expected.
  <P>
  This task is a procedure script which selects and lists or executes
  any file in the mkexamples$ logical directory with the example name and the
  extension "<TT>.cl</TT>".  Thus, to add additional examples create a simple
  command script (not a procedure script) and place it in the mkexamples
  directory along with an entry in the menu file mkexamples$mkexamples.men.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create a globular cluster example.
  <P>
  <PRE>
      ar&gt; mkexample
  	    		MKEXAMPLE Menu
  <P>
       galcluster - Galaxy cluster
         globular - Globular cluster
         galfield - Galaxy field
        starfield - Starfield
  <P>
         onedspec - Menu of one dimensional spectra
         twodspec - Menu of two dimensional spectra
       threedspec - Menu of three dimensional spectra
      Example name: globular
      Image name: globular
      Creating example globular in image globular ...
  </PRE>
  <P>
  2.  Try and create the same example again.
  <P>
  <PRE>
      ar&gt; mkexample globular globular
      ERROR: Image globular already exists
  </PRE>
  <P>
  3.  List the script which creates the globular example.
  <P>
  <PRE>
      ar&gt; mkexample globular list+
      # GLOBULAR - Globular cluster
  <P>
      file	image, dat
  <P>
      image = s1
      dat = mktemp ("art")
  <P>
      starlist (dat, 5000, "", "", interactive=no, spatial="hubble",
  	xmin=1., xmax=512., ymin=1., ymax=512., xcenter=INDEF,
  	ycenter=INDEF, core_radius=30., base=0., sseed=i,
  	luminosity="bands", minmag=-7., maxmag=0., mzero=-4., power=0.6,
  	alpha=0.74, beta=0.04, delta=0.294, mstar=1.28, lseed=i,
  	nssample=100, sorder=10, nlsample=100, lorder=10,
  	rbinsize=10., mbinsize=0.5, graphics="stdgraph", cursor="")
  <P>
      mkobjects (image, output="", ncols=512, nlines=512,
  	title="Example artificial globular cluster",
  	header="artdata$stdheader.dat", background=1000., objects=dat,
  	xoffset=0., yoffset=0., star="moffat", radius=1.0, beta=2.5,
  	ar=1., pa=0., distance=1., exptime=1., magzero=7.,
  	gain=3., rdnoise=10., poisson=yes, seed=j)
  <P>
      delete (dat, verify=no)
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>MKEXAMPLES V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='MKEXAMPLES' Line='MKEXAMPLES V2.10.3'>
  <DD>The examples have been expanded to include submenus.  The submenus organize
  the various types of spectra.  Additional spectral examples have been
  added.  The oseed parameter selects the number of apertures in the
  onedspec spectra and the number of orders in the echelle examples.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkobjects, mknoise, mk1dspec, mk2dspec, mkechelle
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
