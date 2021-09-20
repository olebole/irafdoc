.. _flprcache:

flprcache: Flush the process cache
==================================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  flprcache process
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>process</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='process' Line='process' -->
  <dd>Either the task number as printed by <i>prcache</i>, or the name of one
  of the tasks in the process.  If no process is named, all processes
  are flushed from the cache (unless they are locked in the cache).
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  When an executable task is first run, the CL spawns the associated executable
  file as a subprocess and then runs the task.  When the task completes the
  process does not exit, rather it remains connected to the CL as a subprocess,
  but becomes idle waiting for another command from the CL.  The set of such
  idle processes forms what is referred to as the CL <span style="font-family: monospace;">"process cache"</span>.
  The purpose of the process cache is to minimize the overhead required to
  run a task; the first time a task is called response is slow since the
  process has to be executed, but thereafter response is fast provided the
  process remains in the cache.
  </p>
  <p>
  The <i>flprcache</i> command flushes the process cache, terminating
  the connected subprocesses therein.  If an argument is specified only the
  specific cache slot is cleared, otherwise all cache slots are flushed.
  Processes which have been <span style="font-family: monospace;">"locked"</span> in the cache with <i>prcache</i> are
  not flushed unless explicitly named.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Run <i>prcache</i> to get the process slot number, then flush the process
  by slot number.
  </p>
  <p>
  	cl&gt; flpr 5
  </p>
  <p>
  2. Flush all idle processes which are not locked in the cache.
  </p>
  <p>
  	cl&gt; flpr
  </p>
  <p>
  3. Flush the <span style="font-family: monospace;">"x_system.e"</span> process by naming the <span style="font-family: monospace;">"directory"</span> task, which
  is contained in that process.  Lock a fresh copy of the process in the cache.
  This initializes the process, and may be necessary if a system task is
  interrupted at the wrong time.
  </p>
  <p>
  	cl&gt; flpr dir; prc dir
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  In some circumstances the CL may believe that a process in the
  process cache is running when this is not the case.  The CL will
  not attempt to communicate with a running process, and will be
  unable to kill the process.  If this happens the CL will hang up
  during logout and will have to be interrupted, causing a panic abort
  (this is harmless since the CL is then restarted).
  The user may eventually be required to kill the sub-process using
  operating system facilities.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  prcache
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
