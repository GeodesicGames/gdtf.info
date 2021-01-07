---
title: "DMX Mode Collection"
description: "This page describes allowed DMX Mode Collection values in the description.xml file that is bundled with a GDTF."
lead: "This page describes allowed DMX Mode Collection values in the description.xml file that is bundled with a GDTF."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "file-spec"
weight: 110
toc: true
---

## General

This section is describes all DMX modes of the device. If firmware revisions change a DMX footprint, then such revisions should be specified as new DMX mode. The DMX mode collect currently does not have any attributes (XML node `DMXModes`). As a child the fixture type DMX mode collect has DMX modes.

## DMX Mode

Each DMX mode describes logical control a part of the device in a specific mode (XML node `DMXMode`). The currently defined XML attributes of the DMX mode are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                   |
|--------------------|------------|-----------------------------------------------------------------------------------------------|
| Name               | Name       | The unique name of the DMX mode                                                               |
| Geometry           | Name       | Name of the first geometry in the device; Only top level geometries are allowed to be linked. |

DMX mode children are specified in the following table

| XML node    | Mandatory | Description                                       |
|-------------|-----------|---------------------------------------------------|
| DMXChannels | Yes       |  Description of all DMX channels used in the mode |
| Relations   | No        | Description of relations between channels         |
| FTMacros    | No        | Is used to describe macros of the manufacturer.   |

### DMX Channel Collect

#### General

This section defines the DMX footprint of the device. The DMX channel collect currently does not have any attributes (XML node `DMXChannels`). As children, the DMX Channel Collect has a list of a `DMXChannel` nodes.

#### DMX Channel

##### General

This section defines the DMX channel (XML node `DMXChannel`). The name of a DMX channel cannot be user-defined and must consist of a geometry name and the attribute name of the first logical channel with the separator "_". Currently defined XML attributes of the DMX channel are specified in the following table:

| XML Attribute Name        | Value Type    | Description                                                                                                                                                                                                    |
|-----------------|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DMXBreak        | Int          | Number of the DMXBreak; Default value: 1; Special value: “Overwrite” – means that this number will be overwritten by Geometry Reference; Size: 4 bytes                                                         |
| Offset          | Array of Int | Relative addresses of the current DMX channel from highest to least significant; Seperator of values is ","; Special value: “None” – does not have any addresses; Default value: “None”; Size per int: 4 bytes |
| InitialFunction | Node         | Link to the channel function that will be activated by default for this DMXChannel;                                                                                                                            |
| Highlight       | DMXValue     | Highlight value for current channel; Special value: “None”. Default value: “None”.                                                                                                                             |
| Geometry        | Name         | Name of the geometry the current channel controls.                                                                                                                                                             |

As children, the DMX Channel has a list of `LogicalChannel` nodes.

##### Logical Channel

The Fixture Type Attribute is assinged to a LogicalChannel and defines the function of the LogicalChannel. All logical channels that are children of the same DMX channel are mutually exclusive. In a DMX mode, only one logical channel with the same attribute can reference the same geometry at a time. The name of a Logical Channel cannot be user-defined and is equal to the linked attribute name. The XML node of the logical channel is LogicalChannel. The currently defined XML attributes of the logical channel are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                                                  |
|--------------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Attribute          | Node       | Link to the attribute; The starting point is the Attribute Collect (See Annex A)                                                                                                             |
| Snap               | Enum       | If snap is enabled, the logical channel will not fade between values. Instead, it will jump directly to the new value.; Value: “Yes”, “No”, “On”, “Off”. Default value: “No”                 |
| Master             | Enum       | Defines if all the subordinate channel functions react to a Group Control defined by the control system. Values: “None”, “Grand”, “Group”; Default value: “None”.                            |
| MibFade            | Float      | Minimum fade time for moves in black action. MibFade is defined for the complete DMX range. Default value: 0; Unit: second                                                                   |
| DMXChangeTimeLimit | Float      | Minimum fade time for the subordinate channel functions to change DMX values by the control system. DMXChangeTimeLimit is defined for the complete DMX range. Default value: 0; Unit: second |

##### Channel Function

The Fixture Type Attribute is assinged to a Channel Function and defines the function of its DMX Range. (XML node `ChannelFunction`). The currently defined XML attributes of channel function are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                   |
|--------------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | Unique name; Default value: Name of attribute and number of channel function.                                                                                 |
| Attribute          | Node       | Link to attribute; Starting point is the attributes node. Default value: “NoFeature”.                                                                         |
| OriginalAttribute  | String     | The manufacturer's original name of the attribute; Default: empty                                                                                             |
| DMXFrom            | DMXValue   | Start DMX value; The end DMX value is calculated as a DMXFrom of the next channel function – 1 or the maximum value of the DMX channel. Default value: "0/1". |
| Default            | DMXValue   | Default DMX value of channel function when activated by the control system.                                                                                   |
| PhysicalFrom       | Float      | Physical start value; Default value: 0                                                                                                                        |
| PhysicalTo         | Float      | Physical end value; Default value: 1                                                                                                                          |
| RealFade           | Float      | Time in seconds to move from min to max of the Channel Function; Default value: 0                                                                             |
| RealAcceleration   | Float      | Time in seconds to accelerate from stop to maximum velocity; Default value: 0                                                                                 |
| Wheel              | Node       | Optional link to wheel; Starting point: Wheel Collect                                                                                                         |
| Emitter            | Node       | Optional link to emitter in the physical description; Starting point: Emitter Collect                                                                         |
| Filter             | Node       | Optional link to filter in the physical description; Starting point: Filter Collect                                                                           |
| ModeMaster         | Node       | Link to DMX Channel or ChannelFunction; Starting point DMX mode                                                                                               |
| ModeFrom           | DMXValue   | Only used together with ModeMaster; DMX start value; Default value: 0/1                                                                                       |
| ModeTo             | DMXValue   | Only used together with ModeMaster; DMX end value; Default value: 0/1                                                                                         |

##### Channel Set

This section defines the channel sets of the channel function (XML node `ChannelSet`). The currently defined XML attributes of the channel set are specified in the following table:

| XML Attribute Name | Value Type | Description                                                                                                                                                                                                                                                        |
|--------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | The name of the channel set. Default: Empty                                                                                                                                                                                                                        |
| DMXFrom            | DMXValue   | Start DMX value; The end DMX value is calculated as a DMXFrom of the next channel set – 1 or the maximum value of the current channel function; Default value: 0/1                                                                                                 |
| PhysicalFrom       | Float      | Physical start value                                                                                                                                                                                                                                               |
| PhysicalTo         | Float      | Physical end value                                                                                                                                                                                                                                                 |
| WheelSlotIndex     | Int        | If the channel function has a link to a wheel, a corresponding slot index needs to be specified. The wheel slot index results from the order of slots of the wheel which is linked in the channel function. The wheel slot index is normalized to 1. Size: 4 bytes |

The `ChannelSet` node does not have any children.

### Relation Collect

#### General

This section describes the dependencies between DMX channels and channel functions, such as multiply and override. The relation collect currently does not have any XML attributes (XML node `Relations`). As children, the Relation Collect has a list of `Relation` nodes.

The relation does not have any children.

### Macro Collect

#### General

This section describes DMX sequences to be executed by the control system. The macro collect currently does not have any XML attributes (XML node `FTMacros`). As children, the Macro Collect has a list of `Macro` nodes.

#### Macro

##### General

This section defines a DMX sequence. (XML node `FTMacro`). The currently defined XML attributes of the macro are specified in the following table:

| XML Attribute Name | Value Type | Description                   |
|--------------------|------------|-------------------------------|
| Name               | Name       | The unique name of the macro. |

Macro children are specified in the following table:

| XML node | Mandatory | Description             |
|----------|-----------|-------------------------|
| MacroDMX | No        | Defines a DMX sequence. |

##### Macro DMX

This section defines the sequence of DMX values which are sent by a control system. (XML node `MacroDMX`). As children, the Macro DMX has a list of `MacroDMXStep` nodes.

##### Macro DMX Step

This section defines a DMX step (XML node MacroDMXStep). The currently defined XML attributes of the macro DMX step are specified in the following table:

| XML Attribute Name | Value Type | Description                                          |
|--------------------|------------|------------------------------------------------------|
| Duration           | Float      | Duration of a step; Default value: 1; Unit: seconds. |

As children, the Macro DMX-Step has a list of a `DMXValue`.

##### DMX Value

This section defines the value for DMX channel (XML node MacroDMXValue). The currently defined XML attributes of the DMX Value are specified in the following table:

| XML Attribute Name | Value Type | Description                                         |
|--------------------|------------|-----------------------------------------------------|
| Value              | DMXValue   | Value of the DMX channel                            |
| DMXChannel         | Node       | Link to a DMX channel. Starting node `DMXChannels`. |

The DMX value does not have any children.
