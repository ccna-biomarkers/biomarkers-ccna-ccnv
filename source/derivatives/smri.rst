Structural MRI (sMRI)
=====================

MAGeTbrain Pipeline
:::::::::::::::::::

MAGeTbrain (Multiple Automatically Generated Templates brain segmentation algorithm) is an automatic volumetric and surface segmentation pipeline based on linear and nonlinear registrations combined with a majority voting scheme.
It takes inputs consisting of volumetric brain scans of atlases with expertly segmented brain regions, and unlabelled subject scans in native space.
It performs its processing using a combination of custom python/bash scripts and tools from the MINC-toolkit package.

Volumetric Segmentation Measures
--------------------------------

Label files of the hippocampus and its subfields (CA1, CA2/3, Dentate/CA4, subiculum, and molecular layers), striatum, thalamus, pallidum, and cerebellum and its lobules 
Volumes in (mm^3) of the hippocampus and its subfields (CA1, CA2/3, Dentate/CA4, subiculum, and molecular layers), striatum, thalamus, pallidum, and cerebellum and its lobules 

Quality Control for Volumetric Segmentations
............................................

Quality control images are generated using post-processing showing selected slices of input images overlayed with candidate segmentations.
Quality control must be performed manually by the user to confirm successful segmentation.

Surface Segmentation Measures
-----------------------------

Vertex-wise measures of surface displacement (ie: local concavity/convexity)
Vertex-wise surface area for the hippocampus, striatum, thalamus, and pallidum

Quality Control for Surface Segmentations
.........................................

Quality of surface measures rely on successful processing on volume-based measures and as such QC is performed during section :ref:`Quality Control for Volumetric Segmentations`.