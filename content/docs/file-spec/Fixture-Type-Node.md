---
title: "Fixture Type Node Documentation"
description: "This page describes allowed values in the description.xml file that is bundled with a GDTF."
lead: "This page describes allowed values in the description.xml file that is bundled with a GDTF."
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

## About this section

Every GDTF file contains a `description.xml` file bundled with it. The documentation in this section describes the `FixtureType` node which is the top-most node in the hierarchy of the `description.xml` file with any children. There is a higher level node, the `GDTF` node, but it has only 1 child: `FixtureType`.

## Definition

The FixtureType node is the starting point of the description of the fixture type within the XML file. The defined Fixture Type Node attributes of the fixture type are specified in Table 3.

| XML Attribute Name | Value Type | Description                                                                                                                                                                                                                                                                                                                                              |
|--------------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Name       | Name of the fixture type.                                                                                                                                                                                                                                                                                                                                |
| ShortName          | String     | Shortened Name of the fixture type.                                                                                                                                                                                                                                                                                                                      |
| LongName           | String     | Detailed name of the fixture type.                                                                                                                                                                                                                                                                                                                       |
| Manufacturer       | String     | Manufacturer of the fixture type.                                                                                                                                                                                                                                                                                                                        |
| Description        | String     | Description of the fixture type.                                                                                                                                                                                                                                                                                                                         |
| FixtureTypeID      | GUID       | Unique number of the fixture type.                                                                                                                                                                                                                                                                                                                       |
| Thumbnail          | Resource   | Optional; File name without extension containing description of the thumbnail. Use the following as a resource file: — png file to provide the rasterized picture. Maximum resolution of picture: 1 024 x 1 024; — svg file to provide the vector graphic. These resource files are located in the root directory of the zip file. Default value: empty. |
| RefFT              | GUID       | GUID of the referenced fixture type                                                                                                                                                                                                                                                                                                                      |
| CanHaveChildren    | Enum       | Describes if it is possible to mount other devices to this device.  Value: "Yes", "No". Default value "Yes"                                                                                                                                                                                                                                              |

`FixtureType` nodes can have the children specified in the following table:

| Child Node           | Mandatory | Description                                                                                 |
|----------------------|-----------|---------------------------------------------------------------------------------------------|
| AttributeDefinitions | Yes       | Defines all Fixture Type Attributes that are used in the fixture type.                      |
| Wheels               | No        | Defines the physical or virtual color wheels, gobo wheels, media server content and others. |
| PhysicalDescriptions | No        | Contains additional physical descriptions                                                   |
| Models               | No        | Contains models of physically separated parts of the device.                                |
| Geometries           | Yes       | Describes physically separated parts of the device.                                         |
| DMXModes             | Yes       | Contains descriptions of the DMX modes.                                                     |
| Revisions            | No        | Describe the history of the fixture type.                                                   |
| FTPresets            | No        | Is used to transfer user-defined and fixture type specific presets to other show files.     |
| Protocols            | No        | Specifies supported protocols.                                                              |
