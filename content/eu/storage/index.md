---
title: Storage Management on the European Galaxy server
---

Storage provides our users freedom to play around with their data and enables exploratory research, but it is also a limited resource for public Galaxy instances.
Thanks to the [de.NBI cloud](https://www.denbi.de/cloud) and the [Uni-Freiburg compute center](https://www.rz.uni-freiburg.de) the European Galaxy server
is managing 4PB of data today (2025/01).
Users access this storage for free; governments are paying for the freedom of science and against being locked into some commercial system.
Everyone gets a fair share of the storage, on the [EU Galaxy server](https://usegalaxy.eu) those are 250 GB for every user, also called `quota`.

This system has served us well for many years. However, different user groups have varying storage needs, and some also contribute
financially to the global Galaxy infrastructure. Until now, we have addressed this by generously extending storage quotas upon request via our quota-request form.
We remain committed to expanding our storage capacity through future grants and we will also keep the quota-request form.

That said, long-term sustainability is a growing challenge as the number of users increases. To address this, the Galaxy community
has introduced advanced Research Data Management (RDM) features, including:

* [More effective data cleaning tools](#manage-your-storage-and-quota)
* [More efficient data import mechanisms](#smart-data-import)
* [Short-term storage for method development](#short-term-storage)
* [Advanced options to export data as FAIR Digital Objects](#data-export)
* [Options for users to integrate their own storage into Galaxy](#user-owned-storage)
* [A co-financing model for research groups in cooperation with our compute center](#towards-a-sustainable-storage-enabling-co-financing-of-public-infrastructure)
* [Glossary](#glossary)
    
----

# Manage your Storage and Quota

On the European Galaxy server every user has a 250 GB quota. This means you can use 250 GB of storage for free.
Once you reach this limit you cannot start new jobs. [Learn more about quotas.](https://galaxyproject.org/support/account-quotas/)

<div align="center">
    <img src="/images/undraw-illustrations/segment-analysis.svg" alt="Icon that depicts a person that cleans up some data." height="100"/>
</div>

## Data cleaning

Efficient data management is essential for optimizing storage and ensuring a smooth workflow in Galaxy. Below are key strategies to clean up your data effectively:

- **Remove unnecessary intermediate steps**: Identify and bulk-remove datasets generated by tools like Trimmomatic to free up space. You can search for specific outputs within a history and delete them accordingly.
- **Automate cleanup within workflows**: Configure workflows to automatically discard unnecessary intermediate results.
- **Visualize disk usage**: Use the [`storage manager`](https://usegalaxy.eu/storage/) to explore storage consumption by history or individual datasets.
- **Download and delete data**: Follow the [Galaxy Training Network (GTN) guide](https://training.galaxyproject.org/training-material/topics/galaxy-interface/tutorials/download-delete-data/tutorial.html) for instructions on managing your data efficiently.
- **Understand data deletion in Galaxy**: When you delete data, it is not immediately removed from the system. Instead, it remains recoverable for a few days before being permanently purged. This prevents accidental loss. Learn more about [delete vs. delete permanently](https://galaxyproject.org/learn/managing-datasets/#delete-vs-delete-permanently).

By following these best practices, you can keep your Galaxy workspace organized and ensure that only essential data is retained.

<!--
OR AS TEXT?

Efficient data management is essential for optimizing storage and ensuring a smooth experience in Galaxy.
By following a few key strategies, you can effectively clean up your data and ensure optimal usage of storage space.

One of the most effective methods is to remove unnecessary intermediate steps. Many tools, such as Trimmomatic, generate temporary datasets
that may no longer be needed after analysis. You can search for specific outputs within a history and delete them in bulk to free up space.
Additionally, automating this process within workflows can help discard unnecessary intermediate results, streamlining your analysis without manual intervention.

To gain insights into your disk usage, the [`storage manager`](https://usegalaxy.eu/storage/) provides a visual representation of storage consumption
by history or individual datasets. This can help you identify large or redundant files that may no longer be needed.

If you need to download and delete data, the
[Galaxy Training Network (GTN) guide](https://training.galaxyproject.org/training-material/topics/galaxy-interface/tutorials/download-delete-data/tutorial.html)
offers comprehensive instructions on managing your datasets efficiently.

It is important to understand how data deletion works in Galaxy. When you delete data, it is not immediately removed from the system.
Instead, it remains recoverable for a few days before being permanently purged. This prevents accidental loss and provides an opportunity for data restoration if needed.
More details about the difference between deleting and permanent deletion can be found [here](https://galaxyproject.org/learn/managing-datasets/#delete-vs-delete-permanently).

-->

<div align="center">
    <img src="/images/undraw-illustrations/clean-up.svg" alt="Icon that depicts a person that cleans up some data." height="100"/>
</div>

## Smart data import

If your RAW data is available on your institutional repository or provided by a core facility you can include those repositories into Galaxy as well.
We call those `repositories` (or technically "remote file sources") and you can configure those under your [user settings](https://usegalaxy.eu/file_source_instances/index).
Just to give a few examples, you can include repositories based on [InvenioRDM](https://inveniosoftware.org/products/rdm/), [Dataverse](https://dataverse.org),
FTP, Google Drive, DropBox, AWS, S3 and [WebDav](https://en.wikipedia.org/wiki/WebDAV),
which includes NextCloud, OpenCloud, [EUDAT B2Drop](https://www.eudat.eu/service-catalogue/b2drop) and many others.

<div align="center">
    <a href="https://training.galaxyproject.org/training-material/faqs/galaxy/manage_your_repositories.html"><button type="button" class="btn btn-success">Learn how to add repositories</button></a>
</div>

👉 If you know about **public** repositories that can be useful for more Galaxy users, please get in [contact](mailto:contact@usegalaxy.eu)
and we add it to our default `repositories` for all users.

A relatively unknown feature in Galaxy is what we call `deferred data`. You can import data as `deferred`, which will not download the data into your history
and therefore not count towards your Quota. `deferred data` will be temporarily downloaded when you do the first calculation on top of it, but it will
not be ingested into Galaxy storage. This feature is especially useful if you have large RAW data that is reduced in size in the first step. Please note that
this feature only works if the data is accessible for Galaxy, e.g. via a URL.

## Data export

Sharing data in public repositories enhances transparency, reproducibility, and collaboration in scientific research.
It allows other researchers to validate findings, build upon existing work, and accelerate scientific discovery.
Additionally, open data promotes greater visibility and impact for researchers while fostering innovation across disciplines.

As Galaxy is publicly funded, much like most scientific research, we strongly encourage you to share your data, workflows, and reports with the scientific community.
To facilitate this, Galaxy provides multiple options for uploading and exporting data to public repositories and remote storage locations.

### Export to Public Archives

* [European Nucleotide Archive (ENA)](https://www.ebi.ac.uk/ena/browser/): Galaxy offers tools to submit raw sequencing data directly to the ENA.
* [OMERO](https://www.openmicroscopy.org/omero/) Integration: For researchers working with biological imaging data, Galaxy integrates with OMERO, an open-source platform for managing, visualizing,
  and analyzing large image datasets. This allows seamless access to OMERO-stored images within Galaxy for efficient data analysis and sharing.

### Export to Writable Repositories

Under your Galaxy [user preferences](https://usegalaxy.eu/file_source_instances/), you can configure writable `repositories`,
enabling exports to various external storage systems. This flexibility allows you to manage and share data across different platforms and repositories,
enhancing collaboration and accessibility. Galaxy supports the [Fair Digital Object (FDO)](https://fairdo.org/) [RO-Crate](https://www.researchobject.org/ro-crate/) so all exports can be machine readable.

Galaxy integrates with InvenioRDM-compatible repositories, including [Zenodo](https://zenodo.org/), to streamline research data management.
You can export your research results directly to Zenodo, where they are assigned a Digital Object Identifier (DOI) for proper
citation and increased visibility. Additionally, Galaxy enables importing files from Zenodo,
supporting reproducible and reusable research workflows. More informations available at our [blog post](https://galaxyproject.org/news/2025-03-10-inveniordm-integration-update/).

<div align="center">
    <a href="https://training.galaxyproject.org/training-material/faqs/galaxy/manage_your_repositories.html"><button type="button" class="btn btn-success">Learn how to add repositories</button></a>
</div>

If you are interested in Import and Export of data to various platforms, you might want to check out our dedicated blog posts about [InvenioRDM/Zenodo](https://galaxyproject.org/news/2025-03-10-inveniordm-integration-update/) and [eLabFTW](https://galaxyproject.org/news/2025-04-02-elabftw-integration/).

<div align="center">
    <img src="/images/undraw-illustrations/export-files.svg" alt="Icon that depicts a person that exports some data." height="100"/>
</div>

-----

# Storage classes

<!-- Color palette: https://www.color-hex.com/color-palette/9983 -->
<!-- Projects/Communities/Citation/Team cards -->

<div class="card-deck">
  <div class="card border-secondary bg-light mb-1 mx-1" style="width: 18rem">
    <div class="card-body">
      <h3 class="card-title text-dark" style="text-align: center;">Long term</h3>
      <p class="card-text">Belongs to your 250 GB of quota, you are responsible for data cleaning. Data can be shared.</p>
      <br/>
      <div class="text-center">
        <img src="/images/undraw-illustrations/projects.svg" alt="projects" height="100"/>
        <br/><br/>
      </div>
      <hr/>
      <div class="text-center">
        <img src="/images/icons/icon_object_store_quota.png" alt="Icon that a storage quota" title="Storage has a 250 GB quota" height="50"/>
      </div>
    </div>
  </div>
  <div class="card border-secondary bg-light mb-1 mx-1" style="width: 18rem">
    <div class="card-body">
      <h3 class="card-title text-dark" style="text-align: center;">Short term</h3>
      <p class="card-text">2 TB of quota, data older than 60 days will be deleted. Data can be shared.</p>
      <br/><br/><br/>
      <div class="text-center">
        <img src="/images/undraw-illustrations/throw-away.svg" alt="Icon that depicts a person that throws away some data." height="100"/>
        <br/><br/>
      </div>
      <hr/>
      <div class="text-center">
        <img src="/images/icons/icon_object_store_noquota.png" alt="Icon that depicts no storage quota." title="Storage has a 250 GB quota" height="50"/>&nbsp; 
        <img src="/images/icons/icon_object_store_short_term.png" alt="Icon that depicts short-term storage." title="Data on this storage will be deleted after 60 days" height="50"/>
      </div>
    </div>
  </div>
  <div class="card border-secondary bg-light mb-1 mx-1" style="width: 18rem;">
    <div class="card-body">
      <h3 class="card-title text-dark" style="text-align: center;">Unshareable</h3>
      <p class="card-text">Belongs to your 250 GB quota, you are responsible for data cleaning, data on this storage cannot be shared.</p>
      <br/><br/>
      <div class="text-center">
        <img src="/images/undraw-illustrations/safe.svg" alt="Icon that depicts safe data." height="100"/>
        <br/><br/>
      </div>
      <hr/>
      <div class="text-center">
        <img src="/images/icons/icon_object_store_quota.png" alt="Icon that depicts a quota." height="50" title="Storage has a 250 GB quota"/>&nbsp;
        <img src="/images/icons/icon_object_store_unshareable_restricted_private.png" alt="Icon that depicts unshareable, restricted and private storage."
            title="Data on this storage is not shareable" height="50"/>        
      </div>
    </div>
  </div>
  <div class="card border-secondary bg-light mb-1 ml-1 mr-3" style="width: 18rem">
    <div class="card-body">
      <h3 class="card-title text-dark" style="text-align: center;">User Owned</h3>
      <p class="card-text">Include your own storage into Galaxy</p>
      <br/><br/><br/><br/><br/>
      <div class="text-center">
        <img src="/images/undraw-illustrations/personal-data.svg" alt="team" height="100"/>
        <br/><br/>
      </div>
      <hr/>
      <div class="text-center" style="align: button">
        <img src="/images/icons/icon_object_store_user_defined.png" alt="Icon that depicts a user-defined storage." title="User defined storage" height="50"/>
      </div>
    </div>
  </div>
</div>

## Long term storage

POSIX/NFS-based storage maintained by the compute center of the University of Freiburg.
In contrast to the `Short term storage` data will not be deleted on this storage.
You need to [clean up your data](#manage-your-storage-and-quota) to stay below your quota of 250 GB.
The data is stored on a high-available data storage and you are allowed to share the data with everyone.


## Short term storage

S3-based object storage is maintained by the compute center of the University of Freiburg.
This storage, also called scratch-storage, with data `purged` after 60 days after creation and so it is only appropriate for short-term methods development and such.
The rapid deletion of stored data enables us to provide this storage with a large quota of 2 TB for everyone. This storage is not backed up.

The automatic cleaning of this storage works like this:
* every weekend Galaxy will iterate over all datasets included in the `Short term storage`
* data older then **60** days will be `deleted`
* a few days later all `deleted` datasets are `purged`

⚠️ To enable collaborative exploratory data analysis we do allow sharing of data in this short-term storage, but please be aware that as old data is deleted,
this might confuse your collaboration partner.

<div align="center">
    <img src="/images/undraw-illustrations/throw-away.svg" alt="Icon that depicts a person that throws away some data." height="100"/>
</div>

## Unshareable storage

S3-based object storage is maintained by the compute center of the University of Freiburg.
Data on this storage cannot be shared between users or published.
All your data in Galaxy is by default only available to you and cannot be seen by other users. However, using normal storage, you can always share data, and histories with others.
This special `Unshareable storage`, also called `private storage`, prevents sharing and provides an additional safeguard to you and your data. 
The data on this storage is counted to the same 250 GB quota as the `Long-term storage`. You are responsible for data cleaning on this storage.

<div align="center">
    <img src="/images/undraw-illustrations/safe.svg" alt="Icon that depicts safe data." height="100"/>
</div>

## User owned storage

Every user can [include their own storage](https://usegalaxy.eu/object_store_instances/index).
If your Institute provides you with S3, iRODS, [OneData](https://onedata.org/) ... this option is for you. Because Galaxy
is not managing this storage, there will be no quota assigned, but the limit of your storage applies 😎

Once you have registered your storage in Galaxy you can run tools and workflows against it. You can set a history to default to this storage or you can set it as global 
default storage for your account. See a tutorial [here](https://galaxyproject.org/news/2024-09-20-esg-byos-im/).

<div align="center">
    <a href="https://training.galaxyproject.org/training-material/faqs/galaxy/manage_your_galaxy_storage.html"><button type="button" class="btn btn-success">Learn how to add more storage</button></a>
</div>

⚠️ This type of storage provides you a lot of flexibility, however, data access to this storage needs to be transferred over potentially long distances. This
has implications for carbon emissions and performance.

<div align="center">
    <img src="/images/undraw-illustrations/personal-data.svg" alt="team" height="100"/>
</div>

----

# Towards a sustainable storage, enabling co-financing of public infrastructure

[tl;dr](https://en.wikipedia.org/wiki/TL;DR) Research groups and networks can co-finance the Europan Galaxy server storage and decide about quota and data policies for their users.

<div align="center">
    <img src="/images/undraw-illustrations/growth-chart.svg" alt="team" height="100"/>
</div>

We have enabled an additional strategy that makes it possible to include storage provided by partner consortia in a very transparent way
into the European Galaxy Server to increase the quota to all consortia members.

Demonstrator I: The [NFDI](https://www.nfdi.de) (National Research Data Infrastructure) is building RDM communities in Germany and one of them
is [DataPLANT](https://nfdi4plants.org). DataPLANT has access to the [bwSFS](https://rdmg.uni-freiburg.de/de/posts/bwsfs/), a state-funded storage for scientists
and in this case in particular for fundamental plant research. In cooperation with [DataPLANT](https://www.nfdi4plants.org) and the
[Compute Center of the University of Freiburg](https://www.rz.uni-freiburg.de/) we have included part of this storage into
Galaxy and have configured Galaxy to store data from users associated with DataPLANT on this particular storage only.
This enables DataPLANT now to decide about their preferred quota limits, and the level of data backup policies and fosters the participation of NFDI with the Galaxy project.

Demonstrator II: [NFDI4BioImage](https://nfdi4bioimage.de/home/) is supporting the Galaxy Imaging community by providing dedicated storage resources. In this demonstrator,
the [Center for Information Technology (CIT)](https://www.uni-muenster.de/IT/)
at the University of Münster has set up an S3-based storage solution for a specific working group requiring 300TB of RAW data storage.
The group now seamlessly stores their RAW data in this dedicated environment, accessing it directly from within Galaxy for analysis. Additionally,
they can export their results back into the storage, ensuring a smooth and integrated workflow.

The system is very flexible and we could enable research networks, like Collaborative Research Centres, NFDIs, EOSC-Nodes, in the same way, to participate in the European Galaxy project and offer
sustainable storage solutions for their researchers. It is to be noted that this covers the technical aspect of storage infrastructure but is only a small aspect of
RDM - for which [de.NBI](https://www.denbi.de), [NFDI](https://www.nfdi.de) and Galaxy provide additional solutions.
Please get in contact with us if you want to learn more about [RDM](https://rdmkit.elixir-europe.org/galaxy_assembly).

----

# Request larger Quotas for your project

With our [quota-increase form](https://usegalaxy.eu/quota-increase), you can request a temporary extension of your user quota in UseGalaxy.eu.
For example you can request 1TB of quota for the next 6 months.

Since UseGalaxy.eu is a public service that we provide for free, we request you to be **responsible and fair** when using the shared resources.

Before you request an additional quota, please make sure that:
- You are processing your data in batches
- You are following our tips to clean up your account
- None of the above options is working for you

Please bear in mind that the change will be effective only after being granted, which can take a few working days.
After the requested extension period ends, your quota will be back to the standard 250 GB. Your data won't be removed, but you won't be able to launch any jobs
in Galaxy until you free up space and are again under 250 GB.

# Glossary

* **Files** in Galaxy are those things that you upload to Galaxy.
* **Dataset** is one or multiple `files` plus metadata. Galaxy will determine metadata during files uploads, for example datatype, size, but also more advanced metadata like hdf5 properties.
* **Quota** is the storage limit of your virtual disk in Galaxy. On the European Galaxy instance, the quota is 250 GB. All your uploaded data (not the deferred data) counts towards your quota.
  If you exceed your quota, no jobs will be started anymore. You need to remove data to be able to run new jobs (and produce new data). Alternatively,
  you can also use your [`own storage`](#user-owned-storage) or the [`short term store`](#short-term-storage).
* **Storage Dashboard** helps you to manage your Galaxy Storage. You can find large datasets, remove them, archive histories.

  You can find the storage dashboard at https://usegalaxy.eu/storage/
* **Galaxy Storage** is used by Galaxy to store your uploads, the result of tool runs or the results of your workflows, including intermediate datasets.
    * Galaxy histories are stored on the `Galaxy storage`.
    * Galaxy storage always needs to be writeable.
    * It can have a `quota` assigned or can be without quota and you can extend the `Galaxy storage` with the your [`own storage`](#user-owned-storage).
    * The Galaxy storage is storing `datasets`, repositories are storing `files`.
    * We also call them `object stores` internally. Popular examples are S3, Google Cloud storage, OneData.
    * You can add Galaxy storage at https://usegalaxy.eu/object_store_instances/
* **Repository** refers to a file storage that you can include in Galaxy to import or export data to.
    * Repositories can be read-only or writable.
    * Repositories in Galaxy are storing `files`, the Galaxy storage is storing `datasets`.
    * Technically, we call it `remote files` or `remote file sources`.
    * Popular examples are Owncloud, Nextcloud, Dropbox or FTP.
    * You can add repositories at https://usegalaxy.eu/file_source_instances/

<slot name="/eu/common/data-policy" />

