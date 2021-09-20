.. _urlget:

urlget: Get a (http) URL to a named file
========================================

**Package: system**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  urlget url fname
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>url</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='url' Line='url' -->
  <dd>The URL to download.
  </dd>
  </dl>
  <dl>
  <dt><b>fname</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fname' Line='fname' -->
  <dd>The name of the file to create containing the URL contents.  If not
  specified, the trailing part of the URL is used as the filename.
  </dd>
  </dl>
  <dl>
  <dt><b>use_cache = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='use_cache' Line='use_cache = yes' -->
  <dd>Use the system file cache?  If 'yes' and the file already exists in the
  cache, the cached file will be copied to the output filename.
  If 'no' then the URL will be downloaded again.
  </dd>
  </dl>
  <dl>
  <dt><b>extn = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='extn' Line='extn = ""' -->
  <dd>Optional filename extension to put on the cached filename.  This can be
  used to force files to be saved as a particular type in the cache.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>Print verbose output?
  </dd>
  </dl>
  <dl>
  <dt><b>cache = <span style="font-family: monospace;">"cache$"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cache' Line='cache = "cache$"' -->
  <dd>Logical cache directory name.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>URLGET</i> task is used to download a URL (HTTP protocol only) to a 
  local file named by the <i>fname</i> parameter.  If no <i>fname</i> is given, 
  a filename is constructed from the last part of the URL (i.e.
  characters trailing any of the <span style="font-family: monospace;">'?'</span>, <span style="font-family: monospace;">'/'</span>, or <span style="font-family: monospace;">'&amp;'</span> delimiters).  Because 
  the URL may not point to a static file, use of the <i>fname</i> parameter
  is recommended.
  </p>
  <p>
  If the <i>use_cache</i> parameter is set, the URL will only be downloaded if
  it does not already exist in the file cache pointed to by the <i>cache</i>
  parameter, otherwise the cached file will be copied to the output filename.
  The <i>extn</i> parameter may be to used to force a specific file extension
  to be appended to the filename in the cache, this allows a URL to be passed
  to a task and treated as if it were a file of a specific type.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Download a FITS image from a URL (these are equivalent):
  </p>
  <pre>
      cl&gt; urlget http://iraf.noao.edu/foo.fits 
      cl&gt; urlget http://iraf.noao.edu/foo.fits foo.fits
  </pre>
  <p>
  2. Force a URL to be downloaded again:
  </p>
  <pre>
      cl&gt; urlget http://iraf.noao.edu/foo.fits use_cache=no
  </pre>
  <p>
  3. Download a URL with special characters:
  </p>
  <pre>
      cl&gt; urlget http://iraf.noao.edu/scripts/tget?f=foo.fits
  or
      cl&gt; s1 = "http://iraf.noao.edu/scripts/tget?f=foo.fits"
      cl&gt; urlget(s1)
  or
      cl&gt; s1 = "http://iraf.noao.edu/scripts/tget?f=foo.fits&amp;d=/iraf/web"
      cl&gt; urlget(s1,"foo.fits",verbose+)
  </pre>
  <p>
  Escaping special characters isn't required from the commandline since the
  URL is assumed to be whitespace or comma delimited.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
