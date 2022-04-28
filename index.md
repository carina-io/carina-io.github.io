# Carina

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/carina-io/carina/blob/main/LICENSE)

> [English](https://github.com/carina-io/carina/blob/main/README.md) | [中文](https://github.com/carina-io/carina/blob/main/README_zh.md)

## Background

Storage systems are complex! There are more and more kubernetes native storage systems nowadays and stateful applications are shifting into cloud native world, for example, modern databases and middlewares. However, both modern databases and its storage providers try to solve some common problems in their own way. For example, they both deal with data replications and consistency. This introduces a giant waste of both capacity and performance and needs more mantainness effort. And besides that, stateful applications strive to be more peformant, eliminating every possible latency, which is unavoidable for modern distributed storage systems. Enters carina.

Carina is a standard kubernetes CSI plugin. Users can use standard kubernetes storage resources like storageclass/PVC/PV to request storage media. Its key features includes:

* Completely kubernetes native and easy to install
* Using local disks and partition them into different groups based on disk type, user can provison different type of disks using different storage class.
* Scaning physical disks and building a RAID as required. If disk fails, just plugin a new one and it's done.
* Node capacity and performance aware, so scheduling pods more smartly.
* Extremly low overhead. Carina sit besides the core data path and provide raw disk performance to applications.
* Auto tiering. Admins can configure carina to combine the large-capacity-but-low-performant disk and small-capacity-but-high-performant disks as one storageclass, so user can benifit both from capacity and performance.
* If nodes fails, carina will automatically detach the local volume from pods thus pods can be rescheduled.