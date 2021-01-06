---
title: "Revision Collect Documentation"
description: "This page describes allowed revision values in the description.xml file that is bundled with a GDTF."
lead: "This page describes allowed revision values in the description.xml file that is bundled with a GDTF."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "file-spec"
weight: 120
toc: true
---

## General

This section defines the history of device type. Revision collect currently does not have any XML attributes (XML node `Revisions`). As children, the Revision Collect has a list of `Revision` nodes.

## Revision

This section defines one revision of the device type (XML node `Revision`). Revisions are optional. Every time a GDTF file is uploaded to the database, a revision with the actual time and UserID is created by the database. The currently defined XML attributes of the revision are specified in the following table 

| XML Attribute Name | Value Type | Description                                                                          |
|--------------------|------------|--------------------------------------------------------------------------------------|
| Text               | String     | User-defined text for this revision; Default value: empty                            |
| Date               | Date       | Revision date and time                                                               |
| UserID             | Uint       | UserID of the user that has uploaded the GDTF file to the database; Default value: 0 |
