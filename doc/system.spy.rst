.. _spy:

spy — Show processor status
===========================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  spy -- tell who is logged in and what they are doing
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  spy [v]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Spy</I> prints a summary of who is on the system and what they are doing.
  The optional argument <I>v</I> (short for <I>verbose</I>) causes more detailed
  information to be given.  The operation of this task is machine dependent,
  as is the quantity and format of the information returned.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  cl&gt; spy
    4:36pm  up 24 days,  5:42,  2 users,  load average: 0.29, 0.15, 0.18
  User     tty       login@  idle   JCPU   PCPU  what
  roger    ttyh8     4:21pm    15      8      5  -csh 
  alice    ttyh9     4:26pm           44     27  w 
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  diskspace
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
