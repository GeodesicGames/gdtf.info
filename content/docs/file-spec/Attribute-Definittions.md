---
title: "Attribute Definitions"
description: "This page describes the attributes found in the description.xml file that is bundled with a GDTF."
lead: "This page describes the attributes found in the description.xml file that is bundled with a GDTF."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "file-spec"
weight: 50
toc: true
---

## Defintions

This section defines the attribute definitions for the Fixture Type Attributes.

NOTE 1 More information on the definitions of attributes can be found in Annex A “Attribute Definitions”.
NOTE 2 All currently defined Fixture Type Attributes can be found in Annex B “Attribute Listing”.
NOTE 3 All currently defined Activation Groups can be found in Annex B "Attribute Listing".
NOTE 4 All currently defined Feature Groups can be found in Annex B "Attribute Listing".

The current attribute definition node does not have any XML attributes (XML node
AttributeDefinitions). Children of the attribute definition are specified in the table below:

## Activation Groups

### General

This section defines groups of Fixture Type Attributes that are intended to be used together.

Example: Usually Pan and Tilt are Fixture Type Attributes that shall be activated together to be able to store and recreate any position.

The current activation groups node does not have any XML attributes (XML node ActivationGroups). As children, it can have a list of activation group.

### Activation Group

This section defines the activation group Attributes (XML node ActivationGroup). Currently defined XML attributes of the activation group are specified as follows:

| XML Attribute Name | Value Type | Description                              |
|--------------------|------------|------------------------------------------|
| Name               | Name       | The unique name of the activation group. |

The ActivationGroup node does not have any children.

## Feature Groups

### General

This section defines the logical grouping of Fixture Type Attributes (XML node FeatureGroups).

NOTE 1 A feature group can contain more than one logical control unit.

A feature group Position shall contain PanTilt and XYZ as separate Feature.

NOTE 2 Usually Pan and Tilt create a logical unit to enable position control, so it is necessary to group them in a Feature PanTilt.

As children, the Feature Groups has a list of a feature group.

### Feature Group

#### General

This section defines the feature group (XML node `FeatureGroup`). The currently defined XML attributes of the feature group are specified in the table below:

| XML Attribute Name | Value Type | Description                           |
|--------------------|------------|---------------------------------------|
| Name               | Name       | The unique name of the feature group. |
| Pretty             | String     | The pretty name of the feature group. |

The `FeatureGroup` node has a list of `Feature` nodes as children.

| XML Attribute Name | Value Type | Description                     |
|--------------------|------------|---------------------------------|
| Name               | Name       | The unique name of the feature. |

#### Feature

This section defines the feature (XML node Feature). The currently defined XML attributes of the feature are specified in the table below:

| XML Attribute Name | Value Type | Description                     |
|--------------------|------------|---------------------------------|
| Name               | Name       | The unique name of the feature. |

The `Feature` node does not have any children.

## Attributes

### General

This section defines the Fixture Type Attributes (XML node Attributes). As children, the Attributes has a list of a attribute.

### Attribute

This section defines the Fixture Type Attribute (XML node Attribute). The currently defined XML attributes of the attribute Node are specified in Table 9.

| XML Attribute Name | Value Type | Description                                                                                                                                                                                                                                                                                                                                                                                                                          |
|--------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the attribute.                                                                                                                                                                                                                                                                                                                                                                                                    |
| Pretty             | String     | The pretty name of the attribute.                                                                                                                                                                                                                                                                                                                                                                                                    |
| ActivationGroup    | Node       | Optional link to the activation group. The starting point is the `ActivationGroups` node.                                                                                                                                                                                                                                                                                                                                            |
| Feature            | Node       | Link to the corresponding feature. The starting point is the `FeatureGroups` node.                                                                                                                                                                                                                                                                                                                                                   |
| MainAttribute      | Node       | Optional link to the main attribute. The starting point is the `Attribute` node                                                                                                                                                                                                                                                                                                                                                      |
| PhysicalUnit       | Enum       | The currently defined unit values are: “None”, “Percent”, “Length” (m), “Mass” (kg), “Time” (s), “Temperature” (K), “LuminousIntensity”(cd), “Angle” (degree), “Force” (N), “Frequency” (Hz), “Current” (A), “Voltage” (V), “Power” (W), “Energy” (J), “Area” (m2), “Volume” (m3), “Speed” (m/s), “Acceleration” (m/s2), “AngularSpeed” (degree/s), “AngularAccc” (degree/s2), “WaveLength” (nm), “ColorComponent”. Default: “None”. |
| Color              | ColorCIE   | Optional: Defines the color for the attribute.                                                                                                                                                                                                                                                                                                                                                                                       |

The `Attribute` node does not have any children.
