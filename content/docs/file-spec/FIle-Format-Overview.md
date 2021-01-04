---
title: "File Format Overview"
description: "This page describes the bundled files of GDTF."
lead: "This page describes the bundled files of GDTF."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "file-spec"
weight: 40
toc: true
---

## Definition

To describe the device type, an uncompressed zip file with the extension "*.gdtf" is used. The archive shall contain a description XML file and resource files. Some of the resource files are located in a folder structure. There are two folders defined: "./wheels" and "./models". The folder "./models" has two subfolders for a better structural overview called "./models/3ds" and "./models/svg". The description.xml file contains the description of the device type and all DMX modes as well as all firmware revisions of the device.

./description.xml

./thumbnail.png

./thumbnail.svg

./wheels/gobo1.png

./wheels/gobo2.png

./models/3ds/base.3ds

./models/3ds/yoke.3ds

./models/svg/base.svg

./models/svg/yoke.svg

The ZIP archive name is specified as follows:

```
ManufacturerName@FixtureTypeName@OptionalComment
```

```
EXAMPLE generic@led@comment
```

UTF-8 has to be used to encode the XML file. Each XML file internally consists of XML nodes. Each XML node could have XML attributes and XML children. Each XML attribute has a value. If a XML attribute is not specified, the default value of this XML attribute will be used. If the XML attribute value is specified as a
string, the format of the string will depend on the XML attribute type. All XML attribute types are specified in the table below

| Value Type | Format                                                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|------------|---------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Unit       | Integer                                                                                                 | Unsigned Integer                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Int        | Integer                                                                                                 | Signed integer                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Hex        | Integer                                                                                                 | Number in hexacecimal notatino; Default value: 0                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Float      | float                                                                                                   | Floating point numeric; Separator: "."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| String     | Literal                                                                                                 | Text                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Name       | restricted Literal                                                                                      | Unique object names; The allowed characters are listed in Annex C Default value: object type with an index in parent.                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Date       | yyyy-mm-ddThh:mm:ss                                                                                     | Date and time corresponding to UTC +00:00 (Coordinated Universal Time): yyyy – year, mm – month, dd – day, hh – hours (24 format), mm – minutes, ss – seconds.  `Example: "2016-06-21T11:22:48"`                                                                                                                                                                                                                                                                                                                                                                                                    |
| Node       | Name.Name.Name...                                                                                       | Link to an element: “Name” is the value of the attribute “Name” of a defined XML node. The starting point defines each attribute separately.                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ColorCIE   | floatx, floaty, floatY                                                                                  | CIE color representation xyY 1931                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Matrix     | {float,float,float,float} {float,float,float,float} {float,float,float,float} {float,float,float,float} | The transformation matrix consists 4 x 4 floats. Stored in a row- major order. For example, each row of the matrix is stored as a  4-component vector. The mathematical definition of the matrix is in a column-major order. For example, the matrix rotation is stored in the first three columns, and the translation is stored in the 4th column. The metric system consists of the Right-handed Cartesian Coordinates XYZ: X – from left (−X) to right (+X), Y – from the outside of the monitor (−Y) to the inside of the monitor (+Y), Z – from bottom (−Z) to top (+Z). 0,0,0 – center base. |
| Rotation   | {float, float, float} {float, float, float} {float, float, float}                                       | The Rotation matrix consists of 3*3 floats. Stored as row-major matrix, i.e. each row of the matrix is stored as a 3-component vector. Mathematical definition of the matrix is column-major, i.e. the  matrix rotation is stored in the three columns. Metric system, right- handed Cartesian coordinates XYZ:  X – from left (−X) to right (+X), Y – from the outside of the monitor (-Y) to the inside of the monitor (+Y), Z – from the bottom (−Z) to the top (+Z).                                                                                                                            |
| Enum       | Literal                                                                                                 | Possible values are predefined                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| DMXAddress | Int, Alternative format: Universe.Address                                                               | Absolute DMX address (size 4 bytes); Alternative format: Universe – integer universe number, starting with 1; Address: address within universe from 1 to 512. Format: integer                                                                                                                                                                                                                                                                                                                                                                                                                       |
| DMXValue   | Uint/n for ByteMirroring values Uint/ns for ByteShifting values                                         | Special type to define DMX value where n is the byte count. The byte count can be individually specified without depending on the resolution of the DMX Channel. By default byte mirroring is used for the conversion. So 255/1 in a 16 bit channel will result in 65535. You can use the byte shifting operator to use byte shifting for the conversion. So 255/1s in a 16 bit channel will result in 65280.                                                                                                                                                                                       |
| GUID       | XXXXXXXX-XXXX- XXXX-XXXX- XXXXXXXXXXXX                                                                  | Unique ID corresponding to RFC 4122: X–1 digit in hexadecimal notation.  Example: "308EA87D-7164-42DE-8106-A6D273F57A51".                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Resource   | String                                                                                                  | File name of the resource file without extension and without subfolder                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Pixel      | Pixel                                                                                                   | Integer value representing one Pixel inside a MediaFile. Pixel count starts with zero in the top left corner                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

The first XML node is always the XML description node:

```
<?xml version="1.0" encoding="UTF-8"?>
```

The second XML node is the GDTF node. The attribute of this node is the DataVersion (table below):

```
<GDTF DataVersion="1.1">
```

The example above shows the XML node for the GDTF version 1.1.

| XML Attribute Name | Value Type | Description                                                                                                                                                  |
|--------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DataVersion        | Unit.unit  | The DataVersion attribute defines the minimal version of compatibility. The Version format is “Major.Minor”, where major and minor is Uint with size 1 byte. |
