.. _aslist:

aslist: List the supported image surveys
========================================

**Package: astcat**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  aslist -- list the supported image surveys
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  aslist catalogs
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>imsurveys</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='imsurveys' Line='imsurveys' -->
  <dd>The names of the image surveys to be listed. If surveys = <tt>"*"</tt> then
  all the image surveys in the image survey configuration file are listed.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>List the image survey wcs and keyword information  after the image survey
  name ?
  </dd>
  </dl>
  <dl>
  <dt><b>imdb = <tt>")_.imdb"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='imdb' Line='imdb = ")_.imdb"' -->
  <dd>The image survey configuration file. The value of imdb defaults to the value
  of the package parameter of the same name. The default image survey
  configuration file is <tt>"astcat$lib/imdb.dat"</tt>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Aslist lists the supported image surveys specified by the
  <i>imsurveys</i> parameter. If imsurveys = <tt>"*"</tt> then all the supported image
  surveys are listed, otherwise only the image survey names specified by the
  user are listed. Valid image survey names have the form imsurvey@site, e.g.
  <tt>"dss1@cadc"</tt>.  If <i>verbose</i> = <tt>"yes"</tt>, then the image survey wcs and
  keyword information is listed after the image survey name.
  </p>
  <p>
  The image survey names, addresses, query formats, output formats, wcs formats,
  and keyword formats, are specified in the image survey configuration file
  <i>imdb</i>. By default the image survey configuration file names defaults to
  the value of the imdb package parameters. The default image survey
  configuration file is <tt>"astcat$lib/imdb.dat"</tt>.  Users can add records
  to this file or create their own configuration file.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. List all the image surveys in the image survey configuration file.
  </p>
  <pre>
  cl&gt; aslist *
  </pre>
  <p>
  2. List the wcs and keyword information for the dss1@cadc image survey.
  </p>
  <pre>
  cl&gt; aslist dss1@cadc verbose+
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  aclist
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
