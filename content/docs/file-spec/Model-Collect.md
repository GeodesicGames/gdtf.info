---
title: "Model Collect Documentation"
description: "This page describes allowed Model Collection values in the description.xml file that is bundled with a GDTF."
lead: "This page describes allowed Model Collection values in the description.xml file that is bundled with a GDTF."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "file-spec"
weight: 90
toc: true
---

## General

Each device is divided into smaller parts: body, yoke, head and so on. These are called geometries. Each geometry has a separate model description and a physical description. Model collect contains model descriptions of the fixture parts. The model collect currently does not have any XML attributes (XML node Models). As children, Model Collect has a list of `Model` nodes.

## Model

This section defines the type and dimensions of the model (XML node `Model`). The currently defined XML attributes of the model are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|--------------------|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the model                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Length             | Float      | Unit: meter; Default value: 0                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Width              | Float      | Unit: meter; Default value: 0                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Height             | Float      | Unit: meter; Default value: 0                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| PrimitiveType      | Enum       | Type of 3D model; The currently defined values are: "Undefined", "Cube", "Cylinder", "Sphere", "Base", "Yoke", "Head", "Scanner", "Conventional", "Pigtail", "Base1_1", "Scanner1_1", "Conventional1_1"; Default value: “Undefined”                                                                                                                                                                                                                                                                                                                                                                                     |
| File               | Resource   | Optional; File name without extension and without subfolder containing description of the model. Use the following as a resource file:  - 3DS file to provide 3D model. - STEP file to provide 3D model as a parametric model; - SVG file to provide the 2D symbol.  It is possible to add several files with the same name but different formats. Preferable format for the 3D model is 3ds. The resource files are located in subfolders of a folder called ./models. The names of the subfolders correspond to the file format of the resource files (3ds, step, svg). The path for 3ds files would be ./models/3ds. |

The model currently does not have any children.

All models of a device combined should not exceed a maximum vertices count of 1 200.

The device shall be drawn in a hanging position displaying the front view; the pan axis is Z aligned and the tilt axis is X aligned.

The metric system consists of the Right-handed Cartesian Coordinates XYZ: X – from left (−X) to right (+X), Y – from the outside of the monitor (−Y) to the inside of the monitor (+Y), Z – from bottom (−Z) to top (+Z). 0,0,0 – center base plate (see the following image).

{{< figure src="/HangingFixtureExample.png" alt="Hanging Fixture Example" class="border-0" >}}

The mesh of each fixture part shall be drawn around its own suspension point. The zero point of a device does not necessarily have to contain the offset related to the yoke, but it must be centered on its axis of rotation. The offset is defined by the geometry and has to be related to its parent geometry and not to the base.

> NOTE In general, the offsets are mostly negative, because the device is displayed in a hanging position.

{{< figure src="/FixtureOffsetPartsExample.png" alt="Fixture Parts Offset" class="border-0" >}}

In the image above, the green arrow displays the offset of the yoke related to the base. The magenta arrow displays the offset of the head related to the yoke. The offsets are to be defined by the position matrix of the according geometry (See the Geometry Section). It is important that the axis of rotation of each device part is exactly positioned (see the image below).

{{< figure src="/FixtureRotationAxes.png" alt="Fixture Rotation Axes" class="border-0" >}}

The dimension XML attributes of model (see table above) are always used, no matter the scaling and ratio of the 3ds file. The mesh is explicitly scaled to this dimension. The length defines the dimension of the model on the X axis, the width on the Y axis and the height on the Z axis.
