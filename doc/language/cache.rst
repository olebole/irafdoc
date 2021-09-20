.. _cache:

cache: Cache parameter files, or print the current cache list
=============================================================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  cache task [task ...]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>task</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='task' Line='task' -->
  <dd>The name of a task whose parameter set is to be cached in fast memory.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>cache</i> command loads the parameters of a task in memory.
  The CL normally reads the parameters for a task from disk whenever the
  task is executed.  Cacheing the parameters for frequently executed tasks
  can speed up execution significantly.  This is particularly important when
  the tasks are called from within a loop.
  </p>
  <p>
  If the <i>cache</i> command is entered without any arguments a list of the
  currently <span style="font-family: monospace;">"cached"</span> tasks is printed.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Cache the parameters for the tasks <i>directory</i> and <i>page</i>.
  </p>
  <p>
  	cl&gt; cache dir page
  </p>
  <p>
  2. Cache the parameters for the tasks called in a loop within the body of
  a procedure script.  Note the use of command mode in the script.
  </p>
  <pre>
  	begin
  		cache ("alpha", "beta")
  		for (i=1;  i &lt;= 10;  i+=1) {
  		    alpha (i)
  		    beta (i)
  		}
  	end
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The parameter cache should not be confused with the process cache associated
  with the <i>prcache</i> and <i>flprcache</i> commands.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  unlearn, update, lparam, eparam
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
