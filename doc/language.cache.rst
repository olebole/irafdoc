.. _cache:

cache — Cache parameter files, or print the current cache list
==============================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  cache -- cache the parameters for a task in fast memory
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  cache task [task ...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>task</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='task' Line='task'>
  <DD>The name of a task whose parameter set is to be cached in fast memory.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>cache</I> command loads the parameters of a task in memory.
  The CL normally reads the parameters for a task from disk whenever the
  task is executed.  Cacheing the parameters for frequently executed tasks
  can speed up execution significantly.  This is particularly important when
  the tasks are called from within a loop.
  <P>
  If the <I>cache</I> command is entered without any arguments a list of the
  currently "<TT>cached</TT>" tasks is printed.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Cache the parameters for the tasks <I>directory</I> and <I>page</I>.
  <P>
  	cl&gt; cache dir page
  <P>
  2. Cache the parameters for the tasks called in a loop within the body of
  a procedure script.  Note the use of command mode in the script.
  <P>
  <PRE>
  	begin
  		cache ("alpha", "beta")
  		for (i=1;  i &lt;= 10;  i+=1) {
  		    alpha (i)
  		    beta (i)
  		}
  	end
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The parameter cache should not be confused with the process cache associated
  with the <I>prcache</I> and <I>flprcache</I> commands.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  unlearn, update, lparam, eparam
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
