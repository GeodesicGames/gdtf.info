---
title: "Physical Descriptions"
description: "This page describes allowed physical descriptions values in the description.xml file that is bundled with a GDTF."
lead: "This page describes allowed physical descriptions values in the description.xml file that is bundled with a GDTF."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "file-spec"
weight: 80
toc: true
---

## General 

This section describes the physical constitution of the device. It currently does not have any XML Attributes (XML node PhysicalDescriptions). Children of Physical Description are specified in the following table:

| XML node    | Mandatory | Description                                                                        |
|-------------|-----------|------------------------------------------------------------------------------------|
| Emitters    | No        | Describes device emitters                                                          |
| Filters     | No        | Describes device filters                                                           |
| ColorSpace  | No        | Describes device color space                                                       |
| DMXProfiles | No        | Describes nonlinear correlation between DMX input and physical output of a channel |
| CRIs        | No        | Describes color rendering according to ANSI/IES TM-30 99 color samples             |
| Connectors  | No        | Describes physical connectors of the Device                                        |
| Properties  | No        | Describes physical properties of the device                                        |

## Emitter Collect

### General

This section contains the description of the emitters. Emitter Collect defines additive mixing of light sources, such as LEDs and tungsten lamps with permanently fitted filters. It currently does not have any XML Attributes (XML node Emitters). As children, the Emitter Collect has a list of an `Emitter` node.

### Emitter

This section defines the description of the emitter (XML node Emitter). The currently defined XML attributes of the emitter are specified in the following table:

As children, the Emitter Collect has a list of `Measurement` nodes.

## Filter Collect

### General

This section contains the description of the filters. The Filter Collect defines subtractive mixing of light sources by filters, such as subtractive mixing flags and media used in physical or virtual Color Wheels. It currently does not have any XML Attributes (XML node `Filters`). As children, the Filter Collect has a list of
`Filter` nodes.

### Filter

This section defines the description of the filter (XML node `Filter`). The currently defined XML attributes of the filter are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                                                                                                                                   |
|--------------------|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | Unique Name of the filter                                                                                                                                                                                                                                                     |
| Color              | ColorCIE   | Approximate absolute color point when this filter is the only item fully inserted into the beam and the fixture is at maximum intensity. For Y give relative value compared to overall output defined in property Luminous Flux of related Beam Geometry (transmissive case). |

## Measurement

### General

The measurement defines the relation between the requested output by a control channel and the physically achieved intensity. XML node for measurement is Measurement. The currently defined XML attributes of the measurement are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                                                                               |
|--------------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Physical           | Float      | For additive color mixing: uniquely given emitter intensity DMX percentage. Value range between > 0 and ≤ 100. For subtractive color mixing: uniquely given flag insertion DMX percentage. Value range between 0 and 100. |
| LuminousIntensity  | Float      | Used for additive color mixing: overall candela value for the enclosed set of measurements.                                                                                                                               |
| Transmission       | Float      | Used for subtractive color mixing: total amount of lighting energy passed at this insertion percentage.                                                                                                                   |
| InterpolationTo    | Enum       | Interpolation scheme from the previous value. The currently defined values are: "Linear", "Step", "Log"; Default: Linear                                                                                                  |

The order of the measurements corresponds to their ascending physical values.

Additional definition for additive color mixing: It is assumed that the physical value 0 exists and has zero output.

Additional definition for subtractive color mixing: The flag is removed with physical value 0 and it does not affect the beam. Physical value 100 is maximally inserted and affects the beam.

> NOTE Some fixtures can vary in color response. These fixtures define multiple measurement points and corresponding interpolations.

As children, the Measurement Collect has an optional list of a `MeasurementPoint` nodes.

### Measurement Point

The measurement point defines the energy of a specific wavelength of a spectrum. The XML node for measurement point is MeasurementPoint. The defined XML attributes of the measurement points are specified in the following table.

It is recommended, but not required, that measurement points are evenly spaced.

Regions with minimal light energy can be omitted, but the decisive range of spectrum must be included. Recommended measurement spacing is 1 nm. Measurement spacing should not exceed 4 nm.

| XML Attribute Name | Value Type | Description                            |
|--------------------|------------|----------------------------------------|
| Wavelength         | Float      | Center wavelength of measurement (nm). |
| Energy             | Float      | Lighting energy (W/m2/nm).             |

The `Measurement Point` node does not have any children.

## Color Space

This section defines the color space that is used for color mixing with indirect RGB, Hue/Sat, xyY or CMY control input. (XML node `ColorSpace`). The currently defined XML attributes of the color space are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                  |
|--------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mode               | Enum       | Definition of the Color Space that used for the indirect color mixing. The defined values are "Custom", "sRGB", "ProPhoto" and "ANSI". Default Value: "sRGB" |
| Red                | ColorCIE   | Optional; CIE xyY of the Red Primary; this is used only if the ColorSpace is "Custom".                                                                       |
| Green              | ColorCIE   | Optional; CIE xyY of the Green Primary; this is used only if the ColorSpace is "Custom".                                                                     |
| Blue               | ColorCIE   | Optional; CIE xyY of the Blue Primary; this is used only if the ColorSpace is "Custom".                                                                      |
| WhitePoint         | ColorCIE   | Optional; CIE xyY of the White Point; this is used only if the ColorSpace is "Custom".                                                                       |

The predefined modes for the color space XML Attributes are specified in the following table:

| Mode        | sRGB                                | ProPhoto                                 | ANSI            |
|-------------|-------------------------------------|------------------------------------------|-----------------|
| Description | Adobe sRGB, HDTV IEC 61966-2-1:1999 | Kodak ProPhoto ROMM RGB ISO 22028-2:2013 | ANSI E1.54-2015 |
| Red         | 0.6400, 0.3300, 0.2126              | 0.7347, 0.2653                           | 0.7347, 0.2653  |
| Green       | 0.3000, 0.6000, 0.7152              | 0.1596, 0.8404                           | 0.1596, 0.8404  |
| Blue        | 0.1500, 0.0600, 0.0722              | 0.0366, 0.0001                           | 0.0366, 0.001   |
| WhitePoint  | 0.3127, 0.3290, 1.0000              | 0.3457, 0.3585                           | 0.4254, 0.4044  |

The `ColorSpace` does not have any children.

## DMX Profile Collect

### General

This section defines DMX profile descriptions. Currently it does not have any XML attributes (XML node DMXProfiles). As children, DMX profile collect has a list of a DMX profile. 

### DMX Profile

This section defines the DMX profile description (XML node `DMXProfile`).

## Color Rendering Index Collect

### Color Rendering Index Group

#### General

This section contains Color Rendering Indexes (CRI) for a single color temperature (XML node CRIGroup). The currently defined XML attributes of the CRI group are specified in the following table:

| XML Attribute Name | Value Type | Description                                           |
|--------------------|------------|-------------------------------------------------------|
| ColorTemperature   | Float      | Color temperature; Default value: 6 000; Unit: Kelvin |

#### Color REndering Index

This section defines the CRI for one of the 99 color samples (XML node CRI). The currently defined XML attributes of the Color Rendering Index are specified in the following table:

| XML Attribute Name  | Value Type | Description                                                                               |
|---------------------|------------|-------------------------------------------------------------------------------------------|
| CES                 | Enum       | Color sample. The defined values are “CES01”, “CES02”, ... “CES99”. Default Value “CES01" |
| ColorRenderingIndex | Unit       | The color rendering index for this sample. Size: 1 byte; Default value: 100               |

## Connector Collect

### General

This section defines the physical connectors. It currently does not have any XML attributes (XML node `Connectors`). As children, the Connector Collect has a list of a `Connector` nodes.

### Connector

This section defines the connector (XML node `Connector`). The currently defined XML attributes of the connector are specified in the following table

| XML Attribute Name | Value Type | Description                                                                                                                                             |
|--------------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | Unique Name of the connector.                                                                                                                           |
| Type               | Name       | The type of the connector. Find a list of predefined types in Annex D                                                                                   |
| DMXBreak           | Unit       | Optional: Defines which DMX Break this connector belongs to.                                                                                            |
| Gender             | Int        | Connectors where the addition of the Gender value equals 0, can be connected; Default value: 0; Male Connectors are −1, Female are +1, Universal are 0. |
| Length             | Float      | Defines the length of the connector’s wire in meters. "0" means that there is no cable and the connector is built into the housing. Default value "0"   |


## Properties Collect

### General

This section defines the general properties of the device type (XML node Properties). The Properties Collect currently does not have any XML attributes. The currently defined children nodes of properties collect are specified in the following table:

| XML Node              | Amount | Description                                           |
|-----------------------|--------|-------------------------------------------------------|
| Operating Temperature | 0 or 1 | Temperature range in which the device can be operated |
| Weight                | 0 or 1 | Weight of the device including all accessories        |
| PowerConsumption      | Any    | Power information for a given connector.              |
| LegHeight             | 0 or 1 | Height of the legs                                    |

### OperatingTemperature

This section defines the ambient operating temperature range (XML node `OperatingTemperature`). The currently defined XML attributes of the `OperatingTemperature` node are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                 |
|--------------------|------------|-----------------------------------------------------------------------------|
| Low                | Float      | Lowest temperature the device can be operated. Unit: °C. Default value: 0   |
| High               | Float      | Highest temperature the device can be operated. Unit: °C. Default value: 40 |

The `OperatingTemperature` node does not have any children.

### Weight

This section defines the overall weight of the device (XML node Weight). The currently defined XML attributes of the weight are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                       |
|--------------------|------------|-----------------------------------------------------------------------------------|
| Value              | Float      | Weight of the device including all accessories. Unit: Kilogram.  Default value: 0 |

The `Weight` node currently does not have any children.

### PowerConsumption

This section defines the maxiumum power consumption per connector (XML node `PowerrConsumption`). The currently defined XML attributes of the PowerConsumption are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                              |
|--------------------|------------|------------------------------------------------------------------------------------------|
| Value              | Float      | Defines the power consumption of the connector at full load. Unit: VA. Default value: 0  |
| PowerFactor        | Float      | Defines the cosine of phase of voltage relative to current. Unit: None. Default value: 1 |
| Connector          | Node       | Name of the linked `Connector`                                                           |
| VoltageLow         | Float      | Defines the lowest possible operating voltage. Unit: Volt. Default value: 90             |
| VoltageHigh        | Float      | Defines the highest possible operating voltage. Unit: Volt. Default value: 240           |
| FrequencyLow       | Float      | Defines the lowest possible operating frequency. Unit: Hertz. Default value: 50          |
| FrequencyHigh      | Float      | Defines the highest possible operating frequency. Unit: Hertz. Default value: 60         |

The `PowerConsumption` node currently does not have any children.

### LegHeight

This section defines the height of the legs (XML node `LegHeight`). The currently defined XML attributes of the LegHeight are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                      |
|--------------------|------------|------------------------------------------------------------------------------------------------------------------|
| Value              | Float      | Defines height of the legs – distance between the floor and the bottom base plate. Unit: meter. Default value: 0 |

The `LegHeight` node currently does not have any children.
