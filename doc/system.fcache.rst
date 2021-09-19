.. _fcache:

fcache: List, clean or manipulate the file cache
================================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  fcache -- list, clean or manipulate the file cache
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  fcache cmd
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>cmd</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cmd' Line='cmd' -->
  <dd>Cache command to execute.  A description of each command is given below.
  </dd>
  </dl>
  <dl>
  <dt><b>pattern = <tt>"*"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pattern' Line='pattern = "*"' -->
  <dd>Filename substring pattern to match when initializing the cache with
  the <i>init</i> command.
  </dd>
  </dl>
  <dl>
  <dt><b>src = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='src' Line='src = ""' -->
  <dd>Source string used to generate the cache filename.  This is typically
  the full path to a local file being cached or a URL.
  </dd>
  </dl>
  <dl>
  <dt><b>fname = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fname' Line='fname = ""' -->
  <dd>Name of the file in the cache.
  </dd>
  </dl>
  <dl>
  <dt><b>extn = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='extn' Line='extn = ""' -->
  <dd>Cache filename extension.
  </dd>
  </dl>
  <dl>
  <dt><b>age = -1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='age' Line='age = -1' -->
  <dd>Age of the file (in days) to be purged with the <i>purge</i> command.  A value
  less than zero means that the <i>cache_age</i> environment variable should 
  is used to set the age, a value of zero means to delete all files in the 
  cache  (same as the <i>init</i> command), a value greater than zero means 
  that files older than this age will be deleted.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>Print status information as the task processes the command.
  </dd>
  </dl>
  <dl>
  <dt><b>wait = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wait' Line='wait = yes' -->
  <dd>Block on operation?  If 'yes' then the task will block until the requested
  file becomes available in the cache.
  </dd>
  </dl>
  <dl>
  <dt><b>cache = <tt>"cache$"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cache' Line='cache = "cache$"' -->
  <dd>Cache directory to be used.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>FCACHE</i> command is used to list or manage the system file cache
  named by the <i>cache</i> parameter.  If the <i>cache</i> directory does not
  exist, it will be created when required.  The <i>cache_age</i> environment
  variable determines the default maximum age of files in the cache, older
  files are automatically removed by the login.cl as part of the startup
  process.
  </p>
  <p>
  The IRAF file cache is used primarily to cache local copies of URLs in the
  system to prevent repeated downloads when accessing URLs from tasks.  This
  allows a URL to be passed to multiple tasks without explicitly requiring
  the user to create a named (temporary) file themselves.
  </p>
  <p>
  The <i>cmd</i> parameter determines the action to take, other parameters are
  used as needed depending on the command according to the following table:
  </p>
  <pre>
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
  </pre>
  <p>
  The <i>lookup</i> command works in two ways:  If a <i>src</i> string is
  provided then the <i>fname</i> parameter will contain the matching cached
  file (and <i>extn</i> will contain the optional extension), if the <i>fanme</i>
  parameter is specified then on output <i>src</i> will contain the original
  filename/URL.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Remove all <tt>"url"</tt> files from the cache.
  </p>
  <pre>
      cl&gt; fcache init pattern="url"
  </pre>
  <p>
  2. List the contents of the file cache.
  </p>
  <pre>
      cl&gt; fcache list
  </pre>
  <p>
  3. Destroy a cache directory (i.e. remove it entirely).
  </p>
  <pre>
      cl&gt; fcache destroy cache="/tmp/cache"
  </pre>
  <p>
  4. Purge all cache files older than 7 days:
  </p>
  <pre>
      cl&gt; fcache purge age=7
  </pre>
  <p>
  5. Determine if a URL is already in the cache:
  </p>
  <pre>
      cl&gt; fcache add src="/tmp/dpix.fits"
      cl&gt; fcache list
           f1128531670  1  /tmp/dpix.fits
            f789045894  1  http://iraf.noao.edu/vao/dpix.fits
      cl&gt; fcache access src="/tmp/dpix.fits"
      yes
      cl&gt; fcache access src="http://iraf.noao.edu/vao/dpix.fits"
      yes
  </pre>
  <p>
  6. Delete a cached URL:
  </p>
  <pre>
      cl&gt; fcache delete src="http://iraf.noao.edu/vao/dpix.fits"
  </pre>
  <p>
  7. Add a local file to the cache, then look it up:
  </p>
  <pre>
      cl&gt; fcache add src="/tmp/test.fits"
      cl&gt; fcache lookup src="/tmp/test.fits"
      cl&gt; =fcache.fname
      f1295587026
      cl&gt; fcache lookup fname="f1295587026"
      cl&gt; =fcache.src
      /tmp/test.fits
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  head
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
