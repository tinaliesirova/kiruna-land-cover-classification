# Automated Land Cover Classification (Kiruna, Sweden)
## Overview

This project evaluates pixel-based and object-based land cover classification workflows using high-resolution aerial imagery from Kiruna, Sweden.

Two supervised Support Vector Machine (SVM) classification models were developed. The first model was trained using manually digitised training samples on the original imagery, while the second model was trained on segmented image objects following image segmentation. Classification outputs were compared and further refined through reclassification and class aggregation to improve thematic consistency and cartographic readability.

The project highlights the advantages and limitations of pixel/ object-based image analysis for land cover mapping in complex environments.

## Study Area
Kiruna, Sweden.

## Data Sources
Aerial imagery provided for educational purposes through the Swedish GET Tool (https://maps.slu.se/get/) and Umea University (Sweden).

Derived classification maps and analytical outputs presented in this repository were created by the author.

## Tools
ArcGIS Pro


# Methods

## Data Exploration

The aerial imagery was visually inspected to identify dominant land cover types, class boundaries, and areas likely to cause classification confusion. Initial land cover classes were defined based on observable landscape characteristics within the study area.

## Pixel-Based Classification

### Training Data Collection and Model Training

Representative training samples were manually digitised for nine land cover classes:

- Trees (city)
- Lake
- Sediment
- Grass
- Roof
- Road
- Bedrock
- Forest Shrub
- Forest

A total of 208 training samples were created and evaluated using the training sample inspection tools in ArcGIS Pro.

The inspection process was used to:

- Assess class separability
- Identify overlapping classes
- Detect potentially mislabelled training samples
- Evaluate the suitability of the training dataset prior to model training

Following quality assessment, the training samples were used to train a supervised Support Vector Machine (SVM) classifier directly on the original imagery.

### Classification Results

The resulting land cover map was visually assessed against the source imagery to identify classification errors and areas of class confusion.

Key observations included:

- High local variability within vegetation classes
- Pixel-level noise ("salt-and-pepper" effect)
- Misclassification along class boundaries
- Water bodies partially classified as forested areas, particularly in shaded sections of the imagery

These limitations motivated the development of an object-based classification workflow using image segmentation.

## Image Segmentation

The imagery was segmented to create spatially homogeneous image objects for object-based classification.

An initial segmentation was performed; however, visual inspection showed that many segments were too large and merged distinct landscape features into single objects. This level of generalisation reduced the suitability of the segments for subsequent classification.

The segmentation parameters were therefore adjusted and the imagery was segmented a second time using:

- Spectral Detail: 20
- Spatial Detail: 15
- Minimum Segment Size: 5 pixels

The revised segmentation produced smaller and more meaningful image objects that better represented roads, vegetation patches, buildings, and water bodies, providing a more suitable basis for object-based classification.

## Object-Based Classification

Following image segmentation, a new set of training samples was created directly on the second segmented image.

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

The object-based classification output was visually assessed against the source imagery.

Several classification issues remained after segmentation and supervised classification, including:

- Forest areas being partially classified as lake
- Small forest roads being classified as bedrock or sediment

To simplify the classification scheme and reduce class overlap, the classes Bedrock and Forest Shrub were merged using the Reclassify-tool.

This reduced thematic complexity and improved the interpretability of the final map, although some confusion between forest and lake classes remained.

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

## Key observations:

- Forest and shrubland dominated the landscape.
- Urban features such as roads and buildings were clearly identified.
- Water bodies were problematic to successfully separate from vegetation in shadow.
- Class merging improved the interpretability of the final map.


# Skills Demonstrated
- Training sample generation
- Pixel-based classification
- Object-based classification
- Support Vector Machine (SVM) modelling
- Image segmentation
- Land cover mapping
- Raster analysis
- Reclassification and class aggregation
- Spatial data interpretation
- Cartographic visualisation
