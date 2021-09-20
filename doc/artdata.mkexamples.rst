.. _mkexamples:

mkexamples: Make artificial data examples
=========================================

**Package: artdata**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  mkexamples - Make artificial data example images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mkexamples name image
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>name</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='name' Line='name' -->
  <dd>Example name (abbreviations are not allowed):
  <pre>
       galcluster - Galaxy cluster
         globular - Globular cluster
         galfield - Galaxy field
        starfield - Starfield
  
           henear - Helium-neon-argon spectrum (uncalibrated)
         heneardc - Helium-neon-argon spectrum (calibrated)
  
            ecarc - Echelle thorium-argon spectrum (uncalibrated)
          ecarcdc - Echelle thorium-argon spectrum (calibrated)
  
         spectrum - Absorption spectrum (calibrated)
          echelle - Echelle absorption spectrum (calibrated)
  
          ecarc2d - Echelle thorium-argon slit spectrum
          ecobj2d - Echelle object slit spectrum
  
            lsarc - Long slit helium-neon-argon spectrum
  	  lsobj - Long slit object spectrum
  
       multifiber - Multifiber spectrum
  </pre>
  </dd>
  </dl>
  <dl>
  <dt><b>image</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image' Line='image' -->
  <dd>Output image name.
  </dd>
  </dl>
  <dl>
  <dt><b>oseed = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='oseed' Line='oseed = 1' -->
  <dd>Random number seed affecting object generation.  Different object seeds
  will produces different examples of objects or spectral lines or number
  of apertures/orders.  This
  usually modifies the seed parameters in <b>starlist</b>, <b>gallist</b>,
  and <b>mk1dspec</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>nseed = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nseed' Line='nseed = 1' -->
  <dd>Random number noise seed.  Different noise seeds will produce examples
  with different noise, generally of the same level but simply having
  a different pattern.  This is usually the seed parameter in
  <b>mkobjects</b> or <b>mknoise</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>comments = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='comments' Line='comments = no' -->
  <dd>Add comments to the image header describing various artificial data
  parameters?
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print message indicating image being created?
  </dd>
  </dl>
  <dl>
  <dt><b>errors = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='errors' Line='errors = yes' -->
  <dd>Print messages if the image already exists, bad example name, or other
  errors?
  </dd>
  </dl>
  <dl>
  <dt><b>list = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='list' Line='list = no' -->
  <dd>List script used to generate the example rather than create an image?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The task is intended to generate a few artificial images of various types to
  be used as examples of the artificial data package and in various
  demonstrations and test procedures for other packages.  The examples are not 
  exhaustive.  The only adjustable parameters are variations of the
  random number seeds.  Varying the noise seed allows several observations
  of the same example while varying the object seed allows several observations
  of different <span style="font-family: monospace;">"fields"</span>, spectral lines, or number of apertures/orders.
  </p>
  <p>
  If the example name is not given on the command line a menu of example
  names is first printed and then a prompt for the name is given.
  The name may be a submenu or an example.  The
  names may not be abbreviated.  If desired the simple command
  script used to generate the example may be paged.  Otherwise the
  specified image will be generated.  Keep in mind that some of the
  examples (particularly those generating galaxy images) may take a
  significant amount of time.  On a SPARCstation the examples all run in
  under five minutes.  A check is made to see if the image already
  exists.  If the image exists then the task exits.  If the <i>errors</i>
  parameter is specified an error message is printed.
  </p>
  <p>
  A reason for the error output to be turned off is in test scripts and
  demonstrations where the image will be created the first time and reused
  in further tests or demonstrations.  In such cases the verbose option is
  generally set so that the user is aware that an image is being created
  and some delay is to be expected.
  </p>
  <p>
  This task is a procedure script which selects and lists or executes
  any file in the mkexamples$ logical directory with the example name and the
  extension <span style="font-family: monospace;">".cl"</span>.  Thus, to add additional examples create a simple
  command script (not a procedure script) and place it in the mkexamples
  directory along with an entry in the menu file mkexamples$mkexamples.men.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Create a globular cluster example.
  </p>
  <pre>
      ar&gt; mkexample
  	    		MKEXAMPLE Menu
  
       galcluster - Galaxy cluster
         globular - Globular cluster
         galfield - Galaxy field
        starfield - Starfield
  
         onedspec - Menu of one dimensional spectra
         twodspec - Menu of two dimensional spectra
       threedspec - Menu of three dimensional spectra
      Example name: globular
      Image name: globular
      Creating example globular in image globular ...
  </pre>
  <p>
  2.  Try and create the same example again.
  </p>
  <pre>
      ar&gt; mkexample globular globular
      ERROR: Image globular already exists
  </pre>
  <p>
  3.  List the script which creates the globular example.
  </p>
  <pre>
      ar&gt; mkexample globular list+
      # GLOBULAR - Globular cluster
  
      file	image, dat
  
      image = s1
      dat = mktemp ("art")
  
      starlist (dat, 5000, "", "", interactive=no, spatial="hubble",
  	xmin=1., xmax=512., ymin=1., ymax=512., xcenter=INDEF,
  	ycenter=INDEF, core_radius=30., base=0., sseed=i,
  	luminosity="bands", minmag=-7., maxmag=0., mzero=-4., power=0.6,
  	alpha=0.74, beta=0.04, delta=0.294, mstar=1.28, lseed=i,
  	nssample=100, sorder=10, nlsample=100, lorder=10,
  	rbinsize=10., mbinsize=0.5, graphics="stdgraph", cursor="")
  
      mkobjects (image, output="", ncols=512, nlines=512,
  	title="Example artificial globular cluster",
  	header="artdata$stdheader.dat", background=1000., objects=dat,
  	xoffset=0., yoffset=0., star="moffat", radius=1.0, beta=2.5,
  	ar=1., pa=0., distance=1., exptime=1., magzero=7.,
  	gain=3., rdnoise=10., poisson=yes, seed=j)
  
      delete (dat, verify=no)
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>MKEXAMPLES V2.10.3</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='MKEXAMPLES' Line='MKEXAMPLES V2.10.3' -->
  <dd>The examples have been expanded to include submenus.  The submenus organize
  the various types of spectra.  Additional spectral examples have been
  added.  The oseed parameter selects the number of apertures in the
  onedspec spectra and the number of orders in the echelle examples.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  mkobjects, mknoise, mk1dspec, mk2dspec, mkechelle
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  -->
  
