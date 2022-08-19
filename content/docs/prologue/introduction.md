---
title: "Introduction"
description: "The GDTF file format is meant to provide a single file format for the lighting industry to use for interoperability in lighting."
lead: "The GDTF file format is meant to provide a single file format for the lighting industry to use for interoperability in lighting."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "prologue"
weight: 10
toc: true
---

## Get started

If you'd like to take a look at what's inside a GDTF file, rename `yourfile.gdtf` to `yourfile.zip`, and unzip it. You can now browse through the containing folders to see what's included. **It is not required for every file to specify all information**. For example, you may find files without any wheels specified. There may be yet another GDTF with no 3D information. So check out a few of them to get a feel for what's included.

### Finding GDTF files

GDTF files can be found on:

* [gdtf-share](https://gdtf-share.com)
* [NRG Sille](https://www.nrgsille.com/downloads?Collection=GDTF+included)
* [Open GDTF Library](https://github.com/heliostate/OpenGDTFLibrary)
* If you know of others, feel free to [update this page](https://github.com/heliostate/OpenGDTFLibrary)

You can also export some GDTF files from Vectorworks and MA3.

### Creating GDTF files

Currently, you can use the [fixture builder on gdtf-share](https://fixturebuilder.gdtf-share.com/), or you can create the GDTFs manually by specifying all the files, and zipping them up (uncompressed zip file).


## Contributing

If you would like to contribute to this site, feel free to open pull requests at [this site's repository](https://github.com/GeodesicGames/gdtf.info). If you have GDTFs to share with the community share them at the [Open GDTF Library](https://github.com/heliostate/OpenGDTFLibrary).

## Original text from the spec
Nowadays lighting fixtures (luminaires and other controllable devices) have become more and more complex. Additionally, the development of these devices has become faster than ever. New devices are designed with very complex structures and multiple instances, they have more complex color-mixing systems and mode dependencies. To give the user access to the enormous flexibility of the existing devices a way to provide the accurate Fixture Type data is needed to control and pre-visualize the particular devices as good as possible and as quickly as needed. GDTF is that measure. There are many different lighting consoles and software manufacturers on the market and all of them are using different ways and different file formats to get the fixture control information into their systems. As the development of new high-end fixtures takes place at an amazing speed, this creates a ‘lack’ of available control data on the side of the console and pre-visualization software manufacturers. Also, fixture manufacturers are often approached by their clients directly to support them with accurate fixture types. As there are so many different consoles and visualizers on the market this process requires vast knowledge of many different systems. Fixture manufacturers would need to understand how every console or visualizer works, and how to provide the required data. Moreover, a way of format description is needed that not only allows to provide all of the required control information, but also structures it already in a hierarchical way that follows the structure of the device to be described. The lighting designer who would like to use these devices has to deal with such obstacles. They often receive the device control data of a specific new fixture later than expected. Also, the data can be incomplete, because it was not created with the latest information needed from the manufacturer of the fixture. This very clearly demonstrates that our industry is missing a standardized way of defining the description of intelligent and complex devices.

This document defines a data format. After the DIN SPEC has been published, the format will continue to be developed further, but it is important to make an initial version publicly available. Topics for which no specifications can be made at this time, but for which it is foreseeable that this will be necessary, are therefore already specified in this DIN SPEC, but with the note that no specifications can be made at this time.
