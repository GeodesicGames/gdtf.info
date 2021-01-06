---
title: "Geometry Collect Documentation"
description: "This page describes allowed Geometry Collection values in the description.xml file that is bundled with a GDTF."
lead: "This page describes allowed Geometry Collection values in the description.xml file that is bundled with a GDTF."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "file-spec"
weight: 100
toc: true
---

## General

The physical description of the device parts is defined in the geometry collect. Geometry collect can contain a separate geometry or a tree of geometries. The geometry collect currently does not have any XML attributes (XML node `Geometries`). The currently defined children nodes of geometry collect are specified in
the following table:

| XML Node           | Amount | Description                                                             |
|--------------------|--------|-------------------------------------------------------------------------|
| Geometry           | Any    | General Geometry.                                                       |
| Axis               | Any    | Geometry with axis.                                                     |
| FilterBeam         | Any    | Geometry with a beam filter.                                            |
| FilterColor        | Any    | Geometry with color filter.                                             |
| FilterGobo         | Any    | Geometry with gobo.                                                     |
| FilterShaper       | Any    | Geometry with shaper.                                                   |
| Beam               | Any    | Geometry that describes a light output to project.                      |
| MediaServerLayer   | Any    | Geometry that describes a media representation layer of a media device. |
| MediaServerCamera  | Any    | Geometry that describes a camera or output layer of a media device.     |
| MediaServerMaster  | Any    | Geometry that describes a master control layer of a media device        |
| Display            | Any    | Geometry that describes a surface to display visual media.              |
| Geometry Reference | Any    | Reference to already described geometries.                              |

> NOTE  Position the geometry in its "Default" position. This is defined by the Default Value from the DMX Channel that controls the position of that geometry.

## General Geometry

It is a basic geometry type without specification (XML node `Geometry`). The currently defined XML attributes of the geometry are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                                                                                                    |
|--------------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of geometry. Recommendation for conventional is “Body”. Recommendation for a geometry that is representing the base housing of a moving head is “Base”.                                                                        |
| Model              | Name       | Link to the corresponding model.                                                                                                                                                                                                               |
| Position           | Matrix     |  Relative position of geometry; Default value: Identity Matrix                                                                                                                                                                                 |
| Name               | Name       | The unique name of the geometry. Recommendation for an axis- geometry is “Yoke”. Recommendation for an axis-geometry  representing the lamp housing of a moving head is “Head”. NOTE The Head of a moving head is usually mounted to the Yoke. |
| Position           | Matrix     | Relative position of geometry; Default value: Identity Matrix                                                                                                                                                                                  |
## Geometry Tyupe Axis

This type of geometry defines device parts using a rotation axis (XML node `Axis`). The currently defined XML attributes of the axis are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                                                                                                    |
|--------------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the geometry. Recommendation for an axis- geometry is “Yoke”. Recommendation for an axis-geometry  representing the lamp housing of a moving head is “Head”. NOTE The Head of a moving head is usually mounted to the Yoke. |
| Position           | Matrix     | Relative position of geometry; Default value: Identity Matrix                                                                                                                                                                                  |

The `Axis` has the same children types as the geometry collection.

## Geometry Type Beam Filter

This type of geometry defines device parts with a beam filter (XML node FilterBeam). The currently defined XML attributes of the beam filter are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                                                                                                             |
|--------------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the geometry. Recommendation for beam filter limiting the diffusion of light is “BarnDoor”. Recommendation for beam filter adjusting the diameter of the beam is “Iris”. NOTE BarnDoor and Iris are usually mounted to conventional. |
| Model              | Name       |  Link to the corresponding model                                                                                                                                                                                                                        |
| Position           | Matrix     | Relative position of geometry; Default value: Identity Matrix                                                                                                                                                                                           |

The beam has the same children types as the geometry collect.

## Geometry Type Color Filter

This type of geometry is used to describe device parts which have a color filter (XML node `FilterColor`). The currently defined XML attributes of the color filter are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                          |
|--------------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of geometry. Recommendation for filter of a color or mechanical color changer is “FilterColor”. NOTE FilterColor is usually mounted to conventional. |
| Model              | Name       |  Link to the corresponding model                                                                                                                                     |
| Position           | Matrix     | Relative position of geometry; Default value: Identity Matrix                                                                                                        |

The color has the same children types as the geometry collect.

## Geometry Type Gobo Filter

This type of geometry is used to describe device parts which have gobo wheels (XML node `FilterGobo`). The currently defined XML attributes of the gobo filter are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                          |
|--------------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the geometry. Recommendation for filter of a gobo or mechanical gobo changer is “FilterGobo”. NOTE FilterGobo is usually mounted to conventional. |
| Model              | Name       |  Link to the corresponding model                                                                                                                                     |
| Position           | Matrix     | Relative position of geometry; Default value: Identity Matrix                                                                                                        |

The color has the same children types as the geometry collect.

## Geometry Type Shaper Filter

This type of geometry is used to describe device parts which have a shaper (XML node FilterShaper). The currently defined XML attributes of the shaper filter are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                                                |
|--------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the geometry; Recommendation for filter used to form the beam to a framed, triangular, or trapezoid shape, is “Shaper”. NOTE Shaper is usually mounted to conventional. |
| Model              | Name       |  Link to the corresponding model                                                                                                                                                           |
| Position           | Matrix     | Relative position of geometry; Default value: Identity Matrix                                                                                                                              |

The color has the same children types as the geometry collect.

## Geometry Type Beam

This type of geometry is used to describe device parts which have a light source (XML node Beam). The currently defined XML attributes of the Beam are specified in the following table:

| XML Attribute Name  | Value Type | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name                | Name       | The unique name of the geometry. Recommendation for a light source of a conventional or moving head or a projector is “Beam”.  NOTE 1 Beam is usually mounted to Head or Body. Recommendation for a self- emitting single light source is “Pixel”.  NOTE 2 Pixel is usually mounted to Head or Body. Recommendation for a number of Pixel that are controlled at the same time is “Array”. NOTE 3 Array is usually mounted to Head or Body. Recommendation for a light source of a moving mirror is “Mirror”. NOTE 4 Mirror is usually mounted to Yoke. |
| Model               | Name       |  Link to the corresponding model                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Position            | Matrix     | Relative position of geometry; Default value: Identity Matrix                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| LampType            | Enum       | Defines type of the light source; The currently defined types are: Discharge, Tungsten, Halogen, LED; Default value “Discharge”                                                                                                                                                                                                                                                                                                                                                                                                                         |
| PowerConsumption    | Float      | Power consumption; Default value: 1 000; Unit: Watt                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| LuminousFlux        | Float      | Intensity of all the represented light emitters; Default value: 10 000; Unit: lumen                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ColorTemperature    | Float      | Color temperature; Default value: 6 000; Unit: kelvin                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| BeamAngle           | Float      | Beam angle; Default value: 25,0; Unit: degree                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| FieldAngle          | Float      | Field angle; Default value: 25,0; Unit: degree                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ThrowRatio          | Float      | Throw Ratio of the lens for BeamType Rectangle; Default value: 1; Unit: None                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| RectangleRatio      | Float      | Ratio from Width to Height of the Rectangle Type Beam; Default value: 1.7777; Unit: None                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| BeamRadius          | Float      | Beam radius on starting point. Default value: 0,05; Unit: meter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| BeamType            | Enum       | Beam Type; Specified values: “Wash”, “Spot”, “None”, “Rectangle“. Default value “Wash”                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ColorRenderingIndex | Uint       | The CRI according to ANSI/IES TM-30 is a quantitative measure of the ability of the light source showing the object color naturally as it does as daylight reference. Size 1 byte. Default value 100.                                                                                                                                                                                                                                                                                                                                                   |

The beam has the same children types as the geometry collect

Use the Geometry Type "Beam" to describe the position of the fixture’s light output (usually the position of the lens) and not the position of the light source inside the device. The origin of the Geometry Type "Beam" is the origin of the rendered beam. The origin of the Geometry Type "Beam" should not be covered by any faces of other geometries in order to not block the rendered beam.

The `BeamType` describes how the Beam will be rendered

- "Wash" - A conical beam with soft edges.
- "Spot - A conical beam with hard edges.
- "Rectangle" - A pyramid-shaped beam with hard edges.
- "None" - No beam will be drawn, only the geometry itself will emit light.

The beam geometry emits its light into negative Z direction (and Y-up).

## Geometry Type Media Server Layer

This type of geometry is used to describe the layer of a media device that is used for representation of media files (XML node `MediaServerLayer`). The currently defined XML attributes of the media server layer are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                       |
|--------------------|------------|---------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the geometry.                                                                  |
| Model              | Name       | Link to the corresponding model that will be used to display the alignment in media server space. |
| Position           | Matrix     | Relative position of geometry; Default value: Identity Matrix                                     |

The media server layer has the same children types as the geometry collect.

## Geometry Type Media Server Camera

This type of geometry is used to describe the camera or output of a media device (XML node
MediaServerCamera). The currently defined XML attributes of the media server camera are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                       |
|--------------------|------------|---------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the geometry.                                                                  |
| Model              | Name       | Link to the corresponding model that will be used to display the alignment in media server space. |
| Position           | Matrix     | Relative position of geometry; Default value: Identity Matrix                                     |

The media server camera has the same children types as the geometry collect.

The media server camera-view faces in the positive Y-direction (and Z-up).

## Geometry Type Media Server Master

This type of geometry is used to describe the master control of one or several media devices (XML node MediaServerMaster). The currently defined XML attributes of the media server master are specified in the following table:

| XML Attribute Name | Value Type | Description                                                   |
|--------------------|------------|---------------------------------------------------------------|
| Name               | Name       | The unique name of the geometry.                              |
| Model              | Name       | Link to the corresponding model.                              |
| Position           | Matrix     | Relative position of geometry; Default value: Identity Matrix |

The media server master has the same children types as the geometry collect.

## Geometry Type Display

This type of geometry is used to describe a self-emitting surface which is used to display visual media (XML node `Display`). The currently defined XML attributes of the display are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                               |
|--------------------|------------|-------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the geometry.                                                          |
| Model              | Name       | Link to the corresponding model.                                                          |
| Position           | Matrix     | Relative position of geometry; Default value: Identity Matrix                             |
| Texture            | Resource   | Name of the mapped texture in Model file that will be swapped out for the media resource. |

The display has the same children types as the geometry collect.

## Geometry Type Reference

### General

The Geometry Type Reference is used to describe multiple instances of the same geometry. Example: LED panel with multiple pixels. (XML node `GeometryReference`). The currently defined XML attributes of reference are specified in the following table:

> NOTE Geometry Reference also allows easier definition of the DMX Channels for these geometries.

| XML Attribute Name | Value Type | Description                                                                                                                                                                                                                                                                                                |
|--------------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the geometry.                                                                                                                                                                                                                                                                           |
| Position           | Matrix     | Relative position of geometry; Default value: Identity Matrix                                                                                                                                                                                                                                              |
| Geometry           | Name       | Name of the referenced geometry. Only top level geometries are allowed to be referenced.                                                                                                                                                                                                                   |
| Model              | Name       | Optional; Link to the corresponding model. The model only replaces the model of the parent of the referenced geometry. The models of the children of the referenced geometry are not affected. The starting point is Models Collect. If model is not set, the model is taken from the referenced geometry. |

As children, the Geometry Type Reference has a list of a `Break` nodes. The count of the children depends on the number of different breaks in the DMX channels of the referenced geometry. If the referenced geometry, for example, has DMX channels with DMX break 2 and 4, the geometry reference has to have 2 children. The first child with DMX offset for DMX break 2 and the second child for DMX break 4. If one or more of the DMX channels of the referenced geometry have the special value “Overwrite” as a DMX break, the DMX break for those channels and the DMX offsets need to be defined.

## Break

This XML node specifies the DMX offset for the DMX channel of the referenced geometry (XML node Break). The currently defined XML attributes of the break are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                              |
|--------------------|------------|----------------------------------------------------------------------------------------------------------|
| DMXOffset          | DMXAddress | DMX offset; Default value:1 (Means no offset for the corresponding DMX Channel)                          |
| DMXBreak           | Uint       | Defines the unique number of the DMX Break for which the Offset is given. Size: 1 byte; Default value 1. |
