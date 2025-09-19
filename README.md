# Wing-Opt
Adjoint-based shape optimisation of a 2D/sectional wing

## Scope and Components

This repository provides a framework for adjoint-based aerodynamic shape optimisation of a 2D/sectional wing using open-source tools. The goal is to minimise drag subject to lift and geometric constraints.


### Solver
Steady RANS (SU2) with at least one turbulence model (Spalart–Allmaras or k–ω SST).

### Sensitivities
SU2 discrete adjoint to compute d(Drag)/d(ShapeControlPoints).

### Geometry 
Parametric airfoil (B-spline or Hicks–Henne bump parameters) or 2D car section.

### Mesh
Unstructured triangular/quad mesh with boundary-layer refinement (Gmsh). Ensure y+ targets for chosen turbulence model.

### Optimiser
L-BFGS-B or SLSQP for constrained gradient-based optimisation. For multi-start / global search use a Bayesian optimiser (GP) wrapping the adjoint pipeline (multi-fidelity if you add a coarse mesh).

### V&V
Method of manufactured solutions for a simple case OR grid convergence + comparison to XFOIL/published polars for physical validation.

## Software stack

SU2 (adjoint-enabled) — run via Docker or local build.

Gmsh for geometry & meshes.

Python for workflow orchestration and postprocessing: numpy, scipy, matplotlib, meshio, pygmsh (optional), scikit-learn or GPy / GPyTorch for surrogate.

ParaView for visualization.
