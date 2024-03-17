Overview
================================================================================

The Universal Multi-Domain Local Ensemble Transform Kalman Filter (UMD-LETKF) is
a rewrite of the LETKF originally developed by [Hunt2007]_, coded by [Miyoshi2005]_,
with additional modifications for the ocean by Steve Penny.

It is built with the following design choices in mind:

* **model agnostic library** - A single generic LETKF library is provided that can
  be compiled once and then used in all domains of a coupled LETKF system. Redundancies
  in code are eliminated this way. Most specialization for a given domain are done through
  configuration files, and a generic driver is provided that should handle most use
  cases. A custom driver can easily be built to interface with the library if model
  specific code needs to be added.


* **object oriented design** - Several default implementations of classes for
  :ref:`configuration_observation` I/O, :ref:`model state<configuration_state>` I/O,
  and :ref:`configuration_localization` are provided. If different functionality
  is required, the user can create their own derived classes and register them with
  the LETKF library.


* **multi-model strong coupling** - By being model agnostic, the code should allow
  for easy transition from weakly coupled to strongly coupled DA. The same LETKF
  code can be used for multiple independent executables (one for each domain), and
  cross-domain observations can be assimilated by selecting the appropriate observation
  I/O and localization classes.

      
