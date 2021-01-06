---
title: "Supported Protocol Collection Documentation"
description: "This page describes allowed supported protocol values in the description.xml file that is bundled with a GDTF."
lead: "This page describes allowed supported protocol values in the description.xml file that is bundled with a GDTF."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "file-spec"
weight: 140
toc: true
---

## General

If the device supports one or several additional protocols, these protocols specific information have to be specified. The supported protocol collect currently does not have any XML attributes (XML node `Protocols`). Children of supported protocol collect are specified in the following table:

| XML Node         | Mandatory | Description                            |
|------------------|-----------|----------------------------------------|
| RDM              | No        | Describes RDM information              |
| Art-Net          | No        | Describes Art-Net information          |
| sACN             | No        | Describes sACN information             |
| PosiStageNet     | No        | Describes PosiStageNet information     |
| OpenSoundControl | No        | Describes OpenSoundControl information |
| CITP             | No        | Describes CITP information             |

## RDM Section

If the device supports the RDM protocol, this section defines the corresponding information (XML node `FTRDM`). The currently defined XML attributes of RDM are specified in the following table:

| XML Attribute Name | Value Type | Description            |
|--------------------|------------|------------------------|
| ManufacturerID     | Hex        | Manufacturer ESTA ID   |
| DeviceModelID      | Hex        | Unique device model ID |

As children, the FTRDM has a list of `SoftwareVersionID` nodes.

### SoftwareVersionID

#### General

For each supported software version add an XML node `SoftwareVersionID`. The currently defined XML attributes are specified in the following table:

| XML Attribute Name | Value Type | Description         |
|--------------------|------------|---------------------|
| Value              | Hex        | Software version ID |

As children, the `SoftwareVersionID` node has a list of `DMXPersonality` nodes.

#### DMXPersonality

To define the supported software versions add an XML node DMXPersonality. The currently defined XML attributes are specified in the following table:

| XML Attribute Name | Value Type | Description                                                       |
|--------------------|------------|-------------------------------------------------------------------|
| Value              | Hex        | Hex Value of the DMXPersonality                                   |
| DMXMode            | Name       | Link to the DMX Mode that can be used with this software version. |

The `DMXPersonality` node does not have any children.

## Art-Net Section

This section has not yet been defined (XML node `Art-Net`).

## Streaming ACN Section

This section has not yet been defined (XML node `sACN`).

## PosiStageNet Section

This section has not yet been defined (XML node `PosiStageNet`).

## OpenSoundControl Section

This section has not yet been defined (XML node `OpenSoundControl`).

## CITP Section

This section has not yet been defined (XML node `CITP`).
