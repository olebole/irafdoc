.. _hidetask:

hidetask — Make a task invisible to the user
============================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  hidetask -- hide a task from the user
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  hidetask task,[task,...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>task</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='task' Line='task'>
  <DD>The name of a task to be made hidden.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  If a task is only to be called from other tasks, and is not normally
  invoked directly by the user, then it may be useful to `hide' the task,
  i.e., omit it from the list of tasks listed in the "<TT>?</TT>" and "<TT>??</TT>" commands.
  The <I>hidetask</I> command performs this function.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Define the task "<TT>_rew</TT>" and hide it from the user.  The purpose of the
  leading underscore (not required) is to ensure that the user does not
  accidentally run the task.
  <P>
  <PRE>
  cl&gt; task $_rew = "home$rew.e"
  cl&gt; hide _rew
  </PRE>
  <P>
  2. Display the contents of the <I>language</I> package, including all
  hidden tasks (the _ does the trick).
  <P>
  <PRE>
  cl&gt; ?_ lan
      language:
        ?             chdir         defpar        history       radix
        ??            cl            deftask       jobs          redefine
        _allocate     clbye         edit          keep          scan
        _curpack      clear         ehistory      kill          service
        _deallocate   clpackage     envget        language      set
        _devstatus    d_f           eparam        logout        show
        access        d_l           error         lparam        sleep
        back          d_off         flprcache     mktemp        task
        beep          d_on          fprint        osfn          time
        bye           d_p           fscan         package       unlearn
        cache         d_t           gflush        prcache       update
        cd            defpac        hidetask      print         wait
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
