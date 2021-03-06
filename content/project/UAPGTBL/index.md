---
title: UAPG-TBL Simulation
summary: Unsteady Pressure Gradient Turbulent Boundary Layer Simulation
tags:
- Turbulence
math: true
date: "2021-08-14T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: Built by Francesco Ambrogi
  focal_point: Smart

#links:
#- icon: twitter
#  icon_pack: fab
#  name: Follow
#  url: 
#url_code: ""
#url_pdf: ""
#url_slides: ""
#url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
#slides: example

---

Both in nature and industrial applications, turbulent boundary layers in which the pressure gradient varies both in space and time are extremely common. On an airfoil, for instance, the variation of angle of attack induces unsteadiness in the pressure gradient which greatly affects the flow physics and the airfoil behavior. The fast-changing body curvature of a shark swimming and maneuvering generates strong pressure gradients which, of course, are space and time dependent. Numerical simulation of such case studies is extremely important to increase our physical understanding of separated flows and improve future modeling capabilities.

In the present project, the large eddy simulation (LES) technique is used to investigate a turbulent boundary layer under unsteady pressure gradient generated by imposing a suction-blowing velocity profile at the top boundary. The adverse pressure gradient is strong enough to generate a separated flow. The non dimensional parameter which characterizes the unsteadiness is the reduced frequency $\widetilde{k}$  defined as:

$$ \widetilde{k} = \frac{\pi f L_{PG}}{U_{o}} $$

Where $f$ is the imposed frequency, $L_{PG}$ is the length over which the Pressure Gradient varies, and $U_{o}$ is the free-stream velocity at the inflow plane. Several cases have been investigated over a range of reduced frequency and compared with the steady cases at the same pressure gradient.

Simulations are performed using a well validated code, with second order differences for all terms, semi-implicit time advancement, and MPI parallelization. The unresolved stresses are modeled using the Vreman eddy viscosity model.

![UPG-TBL](/images/upgtbl.gif)

The animation shows contours of the instantaneous streamwise velocity $u$ for a reduced frequency of 10, 1 and 0.2 respectively. The animation clearly shows the differences between the two cases: when f is high enough the separation bubble does not have time to develop, yet the size of the separation region is comparable to a steady case. When $k$ decreases, the extent of the separation bubble in the wall normal direction increases but the length of the separation region is  reduced compared with the steady case.
