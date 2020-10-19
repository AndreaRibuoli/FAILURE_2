# FAILURE_2
Missing BUILD CL source 

When installed with PASERIE/INSTALL will fail because of missing BUILD CL source file.
The installer will test compilation for an ILE CL and, should it fail, for an OPM CL.

Being declared in **GUIDANCE.TXT** the installer will request the transfering of **QCLSRC/BUILD** source. 
At this stage there is no **QCLSRC** directory and the error will be identified with the `VERBOSE` option.


