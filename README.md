# Centrifugal Pump CFD Simulation Using SimScale

## 1. Project Overview

This project explores internal flow behavior in a centrifugal pump geometry using Computational Fluid Dynamics (CFD) in SimScale. The study focuses on pressure distribution, velocity magnitude, computational mesh characteristics, and numerical solution behavior.

The project provides practical experience with CFD preprocessing, boundary-condition specification, turbulence modeling, mesh generation, post-processing, and convergence assessment.

The pump geometry was obtained from an existing SimScale community project and used as the starting point for this study. The geometry source is acknowledged below, and the simulation setup and analysis are described according to my actual contributions.

## 2. Project Objectives

- Visualize pressure and velocity distributions within the pump geometry.
- Examine the flow path through the impeller and volute passages.
- Explore the application of turbulence modeling to internal fluid flow.
- Review mesh characteristics and numerical solution behavior.
- Assess solver residuals and monitored quantities.
- Identify modeling limitations and potential improvements.

## 3. Software and Physical Models

| Parameter       | Specification |

| CFD platform    | SimScale |
| Working fluid   | Water |
| Flow assumption | Incompressible |
| Turbulence model| k-ω SST |
| Analysis type   | Configured as steady-state; time-based controls are also present and should be verified |
| Rotating region | Not configured |
| Mesh identifier | Mesh 14 |
| Number of cells | Approximately 1.6 million |
| Number of nodes | Approximately 487,200 |

## 4. Geometry and Boundary Conditions

The model uses a centrifugal pump geometry consisting of an impeller region and surrounding volute passage.

| Boundary              | Condition |
| Inlet                 | Volumetric flow rate |
| Inlet flow rate       | 8.5 × 10⁻³ m³/s (8.5 L/s) |
| Outlet                | Pressure outlet |
| Outlet gauge pressure | 0 Pa |
| Solid surfaces        | Wall |

The inlet flow rate and outlet pressure are specified in the SimScale boundary-condition settings.

A gauge pressure of 0 Pa represents pressure relative to the selected pressure reference, rather than zero absolute pressure.

## 5. Mesh Generation

The computational mesh was generated using the SimScale meshing workflow.

### Recorded Mesh Settings

- **Mesh:** Mesh 14
- **Cells:** Approximately 1.6 million
- **Nodes:** Approximately 487,200
- **Meshing algorithm:** Standard
- **Sizing:** Automatic
- **Fineness:** 5
- **Curvature:** Automatic
- **Physics-based meshing:** Enabled
- **Hex element core:** Enabled
- **Automatic boundary layers:** Disabled
- **Automatic extrusion meshing:** Disabled

The mesh visualization is included to illustrate the discretization of the pump geometry.

[Computational mesh](images/mesh.png)

**Mesh assessment:** The cell and node counts describe the mesh size but do not establish mesh quality or mesh independence. Further work could include local mesh inspection, quality checks, and a mesh-sensitivity study.

## 6. Numerical Setup

The recorded numerical settings include:

- Manual relaxation type.
- Pressure reference value of 0 Pa.
- Absolute residual tolerance of 10⁻⁶ for velocity, pressure, turbulent kinetic energy (k), and specific dissipation rate (ω).
- Potential flow initialization enabled.
- End time set to 1000 s.
- Time step set to 1 s.
- Write control set to time step, with a write interval of 1000.

The run completed successfully according to the SimScale event log, with a reported runtime of approximately 23 minutes and 3.09 core-hours.

**Important:** The time-based controls and residual histories should be interpreted in the context of the actual solver configuration. The configured residual tolerances are not the same as the residual values achieved during the run.

## 7. Results and Visualization

### 7.1 Velocity Magnitude

[Velocity magnitude contour](images/velocity-magnitude.png)

The velocity-magnitude contour illustrates the spatial variation in flow speed through the modeled pump geometry. It can be used to identify regions of relatively higher and lower velocity and to explore the non-uniformity of the internal flow.

### 7.2 Pressure Distribution

[Pressure contour](images/pressure-contour.png)

The pressure contour illustrates the computed pressure field throughout the modeled geometry.

The interpretation of pressure levels depends on the selected pressure variable and reference. Quantitative conclusions about pressure rise attributable to pump operation require an appropriate representation of impeller rotation.

### 7.3 Computational Mesh

[Mesh visualization](images/mesh.png)

The mesh visualization shows how the computational domain is discretized. Mesh resolution and quality are important for representing curved passages and local flow gradients.

### 7.4 Solver Residuals

[Solver residuals](images/residuals.png)

The residual history shows an overall decrease in the monitored velocity components and turbulence variables during the run. The pressure residual remains comparatively higher, at approximately the 10⁻² level near the end of the plotted interval.

Although the residuals decrease, the plot does not show that all variables reached the configured absolute tolerance of 10⁻⁶. Therefore, the residual history alone does not establish complete numerical convergence.

## 8. Engineering Discussion

The pressure and velocity contours provide a basis for examining internal flow behavior within the pump geometry. The mesh and solver histories provide additional information about the numerical representation and evolution of the solution.

The residual history shows an overall reduction in several variables, but the remaining pressure residual and oscillations in the monitored quantities warrant further investigation before steady-state convergence can be confirmed.

### Rotating Impeller Limitation

No rotating region or rotating reference frame was configured in this model. A centrifugal pump normally transfers energy to the fluid through its rotating impeller. Without an appropriate representation of this rotation, the current model does not fully represent the pump's energy-transfer mechanism.

Consequently, the results should be interpreted as flow-field observations within the modeled geometry rather than validated predictions of pump head, efficiency, or operating performance.

## 9. Limitations and Future Work

Potential improvements include:

- Configuring an appropriate rotating-impeller model.
- Verifying the solver type and its time-stepping or iteration settings.
- Examining solver termination criteria and convergence diagnostics.
- Identifying the variables represented in the monitored-quantity plot.
- Checking mass conservation and the stability of relevant flow quantities.
- Performing mesh-quality checks and a mesh-sensitivity study.
- Comparing validated predictions against pump theory, experimental data, or published reference results.
- Investigating streamlines and additional flow-field visualizations.

## 10. Geometry Acknowledgment

The pump geometry was obtained from an existing SimScale community project.

The original geometry is acknowledged here. Any additional reused components, such as the mesh, boundary conditions, solver configuration, or results, should also be identified if applicable.

## 11. Simulation Link

**SimScale project:** [https://www.simscale.com/projects/mehwish_akhtar/centrifugal_pump-coursera-_-_copy_258705908/]

## 12. Skills Demonstrated

- Computational Fluid Dynamics (CFD)
- SimScale
- Internal fluid-flow analysis
- Turbulence modeling
- Boundary-condition specification
- Computational meshing
- Pressure and velocity post-processing
- Solver residual interpretation
- Numerical convergence assessment

