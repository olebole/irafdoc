.. _fcache:

fcache — List, clean or manipulate the file cache
=================================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  fcache -- list, clean or manipulate the file cache
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  fcache cmd
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>cmd</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cmd' Line='cmd'>
  <DD>Cache command to execute.  A description of each command is given below.
  </DD>
  </DL>
  <DL>
  <DT><B>pattern = "<TT>*</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pattern' Line='pattern = "*"'>
  <DD>Filename substring pattern to match when initializing the cache with
  the <I>init</I> command.
  </DD>
  </DL>
  <DL>
  <DT><B>src = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='src' Line='src = ""'>
  <DD>Source string used to generate the cache filename.  This is typically
  the full path to a local file being cached or a URL.
  </DD>
  </DL>
  <DL>
  <DT><B>fname = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fname' Line='fname = ""'>
  <DD>Name of the file in the cache.
  </DD>
  </DL>
  <DL>
  <DT><B>extn = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extn' Line='extn = ""'>
  <DD>Cache filename extension.
  </DD>
  </DL>
  <DL>
  <DT><B>age = -1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='age' Line='age = -1'>
  <DD>Age of the file (in days) to be purged with the <I>purge</I> command.  A value
  less than zero means that the <I>cache_age</I> environment variable should 
  is used to set the age, a value of zero means to delete all files in the 
  cache  (same as the <I>init</I> command), a value greater than zero means 
  that files older than this age will be deleted.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print status information as the task processes the command.
  </DD>
  </DL>
  <DL>
  <DT><B>wait = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wait' Line='wait = yes'>
  <DD>Block on operation?  If 'yes' then the task will block until the requested
  file becomes available in the cache.
  </DD>
  </DL>
  <DL>
  <DT><B>cache = "<TT>cache$</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = "cache$"'>
  <DD>Cache directory to be used.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>FCACHE</I> command is used to list or manage the system file cache
  named by the <I>cache</I> parameter.  If the <I>cache</I> directory does not
  exist, it will be created when required.  The <I>cache_age</I> environment
  variable determines the default maximum age of files in the cache, older
  files are automatically removed by the login.cl as part of the startup
  process.
  <P>
  The IRAF file cache is used primarily to cache local copies of URLs in the
  system to prevent repeated downloads when accessing URLs from tasks.  This
  allows a URL to be passed to multiple tasks without explicitly requiring
  the user to create a named (temporary) file themselves.
  <P>
  The <I>cmd</I> parameter determines the action to take, other parameters are
  used as needed depending on the command according to the following table:
  <P>
  <PRE>
      Command	Input Pars	Output Pars	Action
      -------	----------	-----------	------
      init	pattern				Initialize the cache
      purge	age				Purge old files
      destroy					Destroy the cache
      list					List cache contents
      lookup	src		fname,extn	Lookup a file in the cache
      access	src				Is file in cache?
      add		src extn	fname		Add file to the cache
      delete	src		fname		Delete file from cache
      wait	src				Wait for access to file
  </PRE>
  <P>
  The <I>lookup</I> command works in two ways:  If a <I>src</I> string is
  provided then the <I>fname</I> parameter will contain the matching cached
  file (and <I>extn</I> will contain the optional extension), if the <I>fanme</I>
  parameter is specified then on output <I>src</I> will contain the original
  filename/URL.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Remove all "<TT>url</TT>" files from the cache.
  <PRE>
      cl&gt; fcache init pattern="url"
  </PRE>
  <P>
  2. List the contents of the file cache.
  <PRE>
      cl&gt; fcache list
  </PRE>
  <P>
  3. Destroy a cache directory (i.e. remove it entirely).
  <PRE>
      cl&gt; fcache destroy cache="/tmp/cache"
  </PRE>
  <P>
  4. Purge all cache files older than 7 days:
  <PRE>
      cl&gt; fcache purge age=7
  </PRE>
  <P>
  5. Determine if a URL is already in the cache:
  <PRE>
      cl&gt; fcache add src="/tmp/dpix.fits"
      cl&gt; fcache list
           f1128531670  1  /tmp/dpix.fits
            f789045894  1  http://iraf.noao.edu/vao/dpix.fits
      cl&gt; fcache access src="/tmp/dpix.fits"
      yes
      cl&gt; fcache access src="http://iraf.noao.edu/vao/dpix.fits"
      yes
  </PRE>
  <P>
  6. Delete a cached URL:
  <PRE>
      cl&gt; fcache delete src="http://iraf.noao.edu/vao/dpix.fits"
  </PRE>
  <P>
  7. Add a local file to the cache, then look it up:
  <PRE>
      cl&gt; fcache add src="/tmp/test.fits"
      cl&gt; fcache lookup src="/tmp/test.fits"
      cl&gt; =fcache.fname
      f1295587026
      cl&gt; fcache lookup fname="f1295587026"
      cl&gt; =fcache.src
      /tmp/test.fits
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  head
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
