# Modelica package with conflict

This repo contains a Minimal Reproducible Example of the issue of having a Modelica package (here `PackageWithConflict`) when one its submodel has a conflict (here [PackageWithConflict/MyModel.mo](PackageWithConflict/MyModel.mo)). 

The goal is to test the behavior of OMEdit when loading this package, so for the sake of testing, I have voluntarily commited an unresolved conflict, although in practice this will happen on the developper's computer outside of a commit of course.
