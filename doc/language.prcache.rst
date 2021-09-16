.. _prcache:

prcache — Show process cache, or lock a process into the cache
==============================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  prcache -- cache a subprocess
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  prcache task [task ...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>task</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='task' Line='task'>
  <DD>The name of a compiled IRAF task (not the filename of an executable file).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The CL maintains a small cache to store executable images.  When the
  user invokes a task which calls an executable the cache is searched
  for the image before any attempt to load the executable image from
  disk.  After completion of the task the CL retains the executable image
  in the process cache, until the space is needed by some other
  executable.  Thus if a few commands are being executed frequently,
  the overhead of loading the image into core from disk is bypassed,
  which can result in a significant improvement in the response of the CL.
  <P>
  By default, when the cache is full and a new executable must be run,
  the CL searches for the slot containing the task which has remained
  dormant the longest and replaces it with the new task.
  <P>
  The <I>prcache</I> command gives the user some control over this process.
  Using it without any arguments shows the tasks which are currently
  stored in the process cache.  For each slot one gets a line like the
  following.
  <P>
      [07] lyra!17763(4563X)           H  bin$x_images.e
  <P>
  Here, 07 is the process slot number as required by <I>flprcache</I> to
  disconnect the process.  The name "<TT>lyra</TT>" is the name of the node in the
  local network on which the process is executing; this is not normally
  the local node.  In the example, 17763 (hex 4563X) is the process number
  (pid) of the executable.  H indicates that the task is hibernating,
  i.e. the task was waiting in the cache to be invoked.  R would show that
  the task was running.  An L appended to either of these would show that the task
  had been locked into the cache by a previous prcache command.
  The last element on the line is the file name of the executable
  file which was loaded when the task was first invoked.
  <P>
  If one or more task names are given as arguments, those tasks are locked
  into the cache, and will not be replaced by the CL without specific user
  intervention.  If these tasks are not already in the cache, the
  corresponding executables are started, and the tasks are loaded into the cache.
  <P>
  Note that the `process cache' described here, and the `parameter cache'
  described in the `cache' command are entirely distinct, and a given
  task may be found in either, both, or neither of the two caches.
  <P>
  Also note that only executable images reside in the process cache.
  Thus, for example, if the <I>news</I> command is executed, it does not
  appear in the process cache, but the executable
  `system$x_system.e' does, because <I>news</I> calls <I>page</I>,
  which is one of the many entries into the system executable.
  <P>
  Locked process cache slots may only be freed with the <I>flprcache</I> command.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Flush the system process and lock it back into the cache.
  <P>
  <PRE>
  	cl&gt; flpr dir
  	cl&gt; prc dir
  </PRE>
  <P>
  2. Print the current contents of the process cache.
  <P>
  <PRE>
  	cl&gt; prc
  	    [10] lyra!17764(4564X)           H  bin$x_plot.e
  	    [07] lyra!17763(4563X)           H  bin$x_images.e
  	    [04] lyra!17455(442FX)           HL bin$x_system.e
  		   0
  </PRE>
  <P>
  3. Flush all processes which are not locked into the cache.  This may be
  necessary after aborting a task to initialize (by re-executing) the
  associated process, which may not have recovered completely from the
  abort.
  <P>
  	cl&gt; flpr
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The user is responsible for making sure that he does not lock all
  the slots in the cache.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  flprcache
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
