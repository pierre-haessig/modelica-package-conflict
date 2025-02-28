# Modelica package with conflict

This repo contains a Minimal Reproducible Example of the issue of having a Modelica package (here `PackageWithConflict`) when one its submodel has a conflict (here [PackageWithConflict/MyModel.mo](PackageWithConflict/MyModel.mo)). 

The goal is to test the behavior of OMEdit when loading this package, so for the sake of testing, I have voluntarily commited an unresolved conflict, although in practice this will happen on the developper's computer outside of a commit of course.

As per OpenModelica 1.24.4 (Feb 2025), opening the package reports a syntax error in `MyModel.mo` and blocks the loading of the entire package:

> [3] 16:47:22 Syntax Error
> [/home/.../PackageWithConflict/MyModel.mo: 4:1-4:1]: No viable alternative near token: <

because indeed the file contains 3 invalid lines injected by git merge:

```modelica
within PackageWithConflict;

model MyModel "A model file where the is a conflict"
<<<<<<< HEAD
  Real y;
=======
  Real x;
>>>>>>> divergent-branch
equation

end MyModel;
```

(See https://github.com/pierre-haessig/modelica-package-conflict/network for the branching pattern which created the conflict)

The componion OpenModelica issue is at https://github.com/OpenModelica/OpenModelica/issues/13663
