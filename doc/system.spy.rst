.. _spy:

spy: Show processor status
==========================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  spy -- tell who is logged in and what they are doing
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  spy [v]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Spy</i> prints a summary of who is on the system and what they are doing.
  The optional argument <i>v</i> (short for <i>verbose</i>) causes more detailed
  information to be given.  The operation of this task is machine dependent,
  as is the quantity and format of the information returned.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <pre>
  cl&gt; spy
    4:36pm  up 24 days,  5:42,  2 users,  load average: 0.29, 0.15, 0.18
  User     tty       login@  idle   JCPU   PCPU  what
  roger    ttyh8     4:21pm    15      8      5  -csh 
  alice    ttyh9     4:26pm           44     27  w 
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  diskspace
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
