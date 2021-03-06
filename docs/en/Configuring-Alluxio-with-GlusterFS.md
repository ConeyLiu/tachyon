---
layout: global
title: Configuring Alluxio with GlusterFS
nickname: Alluxio with GlusterFS
group: Under Store
priority: 2
---

This guide describes how to configure Alluxio with [GlusterFS](http://www.gluster.org/) as the under
storage system.

# Initial Setup

First, the Alluxio binaries must be on your machine. You can either
[compile Alluxio](Building-Alluxio-Master-Branch.html), or
[download the binaries locally](Running-Alluxio-Locally.html).

Then, if you haven't already done so, create your configuration file from the template:

{% include Common-Commands/copy-alluxio-env.md %}

# Configuring Alluxio

Assuming the GlusterFS bricks are co-located with Alluxio nodes, the GlusterFS volume is mounted at
`/alluxio_vol`, the following environment variable assignment needs to be added to 
`conf/alluxio-env.sh`:

{% include Configuring-Alluxio-with-GlusterFS/underfs-address.md %}

# Running Alluxio Locally with GlusterFS

After everything is configured, you can start up Alluxio locally to see that everything works.

{% include Common-Commands/start-alluxio.md %}

This should start an Alluxio master and an Alluxio worker. You can see the master UI at
[http://localhost:19999](http://localhost:19999).

Next, you can run a simple example program:

{% include Common-Commands/runTests.md %}

After this succeeds, you can visit your GlusterFS volume to verify the files and directories created
by Alluxio exist. For this test, you should see files named like:

{% include Configuring-Alluxio-with-GlusterFS/glusterfs-file.md %}

To stop Alluxio, you can run:

{% include Common-Commands/stop-alluxio.md %}
