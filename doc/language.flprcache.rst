.. _flprcache:

flprcache — Flush the process cache
===================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  flprcache -- flush the process cache
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  flprcache process
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>process</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='process' Line='process'>
  <DD>Either the task number as printed by <I>prcache</I>, or the name of one
  of the tasks in the process.  If no process is named, all processes
  are flushed from the cache (unless they are locked in the cache).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  When an executable task is first run, the CL spawns the associated executable
  file as a subprocess and then runs the task.  When the task completes the
  process does not exit, rather it remains connected to the CL as a subprocess,
  but becomes idle waiting for another command from the CL.  The set of such
  idle processes forms what is referred to as the CL "<TT>process cache</TT>".
  The purpose of the process cache is to minimize the overhead required to
  run a task; the first time a task is called response is slow since the
  process has to be executed, but thereafter response is fast provided the
  process remains in the cache.
  <P>
  The <I>flprcache</I> command flushes the process cache, terminating
  the connected subprocesses therein.  If an argument is specified only the
  specific cache slot is cleared, otherwise all cache slots are flushed.
  Processes which have been "<TT>locked</TT>" in the cache with <I>prcache</I> are
  not flushed unless explicitly named.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Run <I>prcache</I> to get the process slot number, then flush the process
  by slot number.
  <P>
  	cl&gt; flpr 5
  <P>
  2. Flush all idle processes which are not locked in the cache.
  <P>
  	cl&gt; flpr
  <P>
  3. Flush the "<TT>x_system.e</TT>" process by naming the "<TT>directory</TT>" task, which
  is contained in that process.  Lock a fresh copy of the process in the cache.
  This initializes the process, and may be necessary if a system task is
  interrupted at the wrong time.
  <P>
  	cl&gt; flpr dir; prc dir
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  In some circumstances the CL may believe that a process in the
  process cache is running when this is not the case.  The CL will
  not attempt to communicate with a running process, and will be
  unable to kill the process.  If this happens the CL will hang up
  during logout and will have to be interrupted, causing a panic abort
  (this is harmless since the CL is then restarted).
  The user may eventually be required to kill the sub-process using
  operating system facilities.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  prcache
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
