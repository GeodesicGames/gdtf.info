---
title: "Wheel Collection"
description: "This section defines all physical or virtual wheels of the device."
lead: "This section defines all physical or virtual wheels of the device."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "file-spec"
weight: 70
toc: true
---

## General

This section defines all physical or virtual wheels of the device. It currently does not have any XML attributes (XML node `Wheels`). As children, Wheel Collect has a list of a `Wheel`.

> Note: Physical or virtual wheels represent the changes to the light beam within the device. Typically color, gobo, prism, animation, content and others are described by wheels

## Wheel

### General

Each wheel describes a single physical or virtual wheel of the fixture type. If the real device has wheels you can change, then all wheel configurations have to be described. Wheel has the following XML node: Wheel. The currently defined XML attributes of the wheel are specified in the following table

| XML Attribute Name | Value Type | Description                  |
|--------------------|------------|------------------------------|
| Name               | Name       | The unique name of the wheel |

As children, `Wheel` nodes have a list of `Slot` nodes

### Wheel Slot

#### General

The wheel slot represents the slot on the wheel (XML node `Slot`). The currently defined XML attributes of the wheel slot are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                                                                                                                                                                                               |
|--------------------|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the wheel slot                                                                                                                                                                                                                                                                                                         |
| Color              | ColorCIE   | Color of the wheel slot, Default value: {0.3127, 0.3290, 100.0} (white) For Y give relative value compared to overall output defined in property Luminous Flux of related Beam Geometry (transmissive case).                                                                                                                              |
| Filter             | Node       |  Optional link to filter in the physical description; Do not define color if filter is used; Starting point: Filter Collect                                                                                                                                                                                                               |
| MediaFileName      | Resource   | Optional; PNG file name without extension containing image for specific gobos etc.  — Maximum resolution of picture: 1 024x1 024; — Recommended resolution of gobo: 256x256; - Recommended resolution of animation wheel: 256x256  These resource files are located in a folder called ./wheels in the zip archive. Default value: empty. |

> NOTE More information on the definitions of images used in wheel slots to visualize gobos, animation wheels or color wheels can be found in Annex E “Wheel Slot Image Definition”.

The link between a slot and a channel set is done via the wheel slot index. The wheel slot index of a slot is derived from the order of a wheel’s slots. The wheel slot index is normalized to 1.

If the wheel slot has a prism, it has to have one or several children called prism facet. If the wheel slot has an `AnimationWheel`, it has to have one child called `AnimationWheel`.

#### Prism Facet

This section can only be defined for the prism wheel slot and has a description of the prism facet (XML node Facet). The currently defined XML attributes of the prism facet are specified in the following table

| XML Attribute Name | Value Type | Description                                                          |
|--------------------|------------|----------------------------------------------------------------------|
| Color              | ColorCIE   | Color of prism facet, Default value: {0.3127, 0.3290, 100.0} (white) |
| Rotation           | Rotation   | Specify the rotation, translation and scaling for the facet.         |

The prism facet cannot have any children.

#### Animation System

This section can only be defined for the animation system disk and it describes the animation system behavior (XML node AnimationSystem). The currently defined XML attributes of the AnimationSystem are specified in the following table.

| XML Attribute Name | Value Type     | Description                                                                                                                                                                                                              |
|--------------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| P1                 | Array of PIxel | First Point of the Spline describing the path of animation system in the beam in relation to the middle of the Media File; Array of two floats; Seperator of values is ","; First Pixel is X-axis and second is Y-axis.  |
| P2                 | Array of Pixel | Second Point of the Spline describing the path of animation system in the beam in relation to the middle of the Media File; Array of two floats; Seperator of values is ","; First Pixel is X-axis and second is Y-axis. |
| P3                 | Array of Pixel | Third Point of the Spline describing the path of animation system in the beam in relation to the middle of the Media File; Array of two floats; Seperator of values is ","; First Pixel is X-axis and second is Y-axis.  |
| Radius             | Pixel          | Radius of the circle that defines the section of the Animation system which will be shown in the beam.                                                                                                                   |

Here is an example of AnimationSystem.

{{< figure src="/AnimationExample.png" alt="Animateion Example" class="border-0" >}}
