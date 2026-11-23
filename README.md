# Kiruna Land Cover Classification
## Overview
This project explores land cover classification of high-resolution imagery from Kiruna, Sweden, using image segmentation and classification workflows in ArcGIS Pro.

The objective was to produce a meaningful land cover map and evaluate the effectiveness of different classification approaches.

## Study Area
Kiruna, Sweden.

## Data Sources
Aerial imagery provided for educational purposes through the Swedish GET Tool (https://maps.slu.se/get/)  and university coursework.

Derived classification maps and analytical outputs presented in this repository were created by the author.

## Tools
ArcGIS Pro


# Methods

## Data Exploration

The aerial imagery was visually inspected to identify dominant land cover types, class boundaries, and areas likely to cause classification confusion. Initial land cover classes were defined based on observable landscape characteristics within the study area.

## Training Data Collection

Representative training samples were manually digitised for each land cover class.

Classes included:

- Trees (city)
- Lake
- Sediment
- Grass
- Roof
- Road
- Bedrock
- Forest Shrub
- Forest

A total of 208 training samples were created and used to train an SVM classifier.

## Pixel-Based Classification

An initial supervised classification was performed directly on the imagery using the training samples.

The resulting map was evaluated against the source imagery to identify classification errors and areas of class confusion.

Key observations included:

- High local variability within vegetation classes
- Pixel-level noise ("salt-and-pepper" effect)
- Misclassification along class boundaries, especially water bodies with areas in shadow

## Image Segmentation

To improve classification performance, the imagery was segmented into spatially homogeneous image objects prior to a second classification run.

Segmentation grouped neighbouring pixels with similar spectral characteristics into larger objects representing meaningful landscape features.

## Object-Based Classification

Following image segmentation, a new set of training samples was created directly on the segmented image objects.

The revised classification scheme consisted of eight classes:

- Trees
- Lake
- Sediment
- Grass
- Roof
- Road
- Bedrock
- Forest Shrub

A total of 245 training samples were created and used to train a second SVM classifier.

The forest class used in the pixel-based classification was removed because of class confusion and overlap with other vegetation classes.


## Classification Refinement

The object-based classification output was compared with the original pixel-based result and visually assessed against the source imagery.

Several classes showing substantial overlap were merged to improve thematic consistency and overall map readability.

Refinements included:

- Reduction of class fragmentation
- Simplification of overlapping vegetation classes
- Improvement of spatial coherence across the classified landscape

## Quality Assessment

Classification outputs were visually assessed using the original aerial imagery as reference.

The object-based workflow produced:

- Reduced salt-and-pepper noise
- More homogeneous land cover classes
- Improved delineation of landscape features
- Better cartographic readability

The most noticeable improvement was observed for water bodies, which were frequently assigned to forest classes in the initial pixel-based classification. Following image segmentation and object-based classification, these areas were more accurately represented as lake features.

Additional post-processing was performed through reclassification and class merging to reduce thematic overlap and improve the interpretability of the final map product.

## Cartographic Presentation

Final land cover maps were produced to visualise and communicate the spatial distribution of land cover classes within the Kiruna study area.


# Results
The final classification successfully differentiated major land cover classes within the study area. 

##Key observations:

- Forest and shrubland dominated the landscape.
- Urban features such as roads and buildings were clearly identified.
- Water bodies were problematic to successfully separate from vegetation in shadow.
- Class merging improved the interpretability of the final map.


# Skills Demonstrated
- Training data preparation
- Pixel-based classification
- Object-based classification
- Support Vector Machine (SVM) modelling
- Image segmentation
- Land cover mapping
- Raster analysis
- Reclassification and class aggregation
- Spatial data interpretation
- Cartographic visualisation
