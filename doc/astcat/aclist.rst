.. _aclist:

aclist: List the supported astrometric catalogs
===============================================

**Package: astcat**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  aclist catalogs
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>catalogs</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='catalogs' Line='catalogs' -->
  <dd>The names of the astrometric catalogs to be listed. If catalogs = <span style="font-family: monospace;">"*"</span> then
  all the astrometric catalogs in the catalog configuration file are listed.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>List the catalog query and output formats after the catalog name ?
  </dd>
  </dl>
  <dl>
  <dt><b>catdb = <span style="font-family: monospace;">")_.catdb"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='catdb' Line='catdb = ")_.catdb"' -->
  <dd>The catalog configuration file. The value of catdb defaults to the value
  of the package parameter of the same name. The default catalog configuration
  file is <span style="font-family: monospace;">"astcat$lib/catdb.dat"</span>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Aclist lists the supported astrometric catalogs specified by the
  <i>catalogs</i> parameter. If catalogs = <span style="font-family: monospace;">"*"</span> then all the supported catalogs
  are listed, otherwise only the catalog names specified by the user are
  listed. Valid catalog names have the form <span style="font-family: monospace;">"catalog@site"</span>, e.g. <span style="font-family: monospace;">"usno2@noao"</span>.
  If <i>verbose</i> = <span style="font-family: monospace;">"yes"</span>, then the catalog query and output formats are
  listed after the catalog name.
  </p>
  <p>
  The catalog names, addresses, query formats, and query output formats are
  specified in the catalog configuration file <i>catdb</i>. By default the catalog
  configuration file name defaults to the value of the package parameter catdb.
  The default catalog configuration file is <span style="font-family: monospace;">"astcat$lib/catdb.dat"</span>.
  Users can add records to this file or create their own configuration
  file using catdb as a model.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. List all the astrometric catalogs in the catalog configuration file.
  </p>
  <pre>
  cl&gt; aclist *
  </pre>
  <p>
  2. List the query format and the output format for the usno2@noao catalog.
  </p>
  <pre>
  cl&gt; aclist usno2@noao verbose+
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
  aslist
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
