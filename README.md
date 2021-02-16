# EOSC-Nordic Climate Science Workbench roadmap

**Video presented at [BCC2020](https://bcc2020.github.io/) online conference**

[![DOI](https://zenodo.org/badge/283116460.svg)](https://zenodo.org/badge/latestdoi/283116460)

**Authors:**  [Fouilloux, Anne Claire](https://github.com/annefou); Hasan, Adil; Lukkarinen, Ari and Struthers, Hamish

<iframe title="vimeo-player" src="https://player.vimeo.com/video/437706026" width="640" height="463" frameborder="0" allowfullscreen></iframe>

# EOSC-Nordic Climate Community, EOSC-Life and EOSC-Pillar

[EOSC Nordic](https://www.eosc-nordic.eu) activities and synergies with other EOSC projects such as [EOSC-Life](https://www.eosc-life.eu/) and [EOSC-Pillar](https://www.eosc-pillar.eu).

In this working document, we try to identify areas where EOSC-Nordic and the Nordic Climate Community could collaborate with other EOSC related projects to fotser and advance take-up of of the European Open Science Cloud.

## EOSC-Nordic & EOSC-Pillar demonstrators

Both [EOSC-Pillar](https://www.eosc-pillar.eu) and [EOSC-Nordic](https://www.eosc-nordic.eu) have use cases and community driven pilots:


- [EOSC-Pillar Use cases](https://www.eosc-pillar.eu/use-cases-and-community-driven-pilots)
- [EOSC-Nordic Use cases](https://www.eosc-nordic.eu/demonstrating-eosc-nordic/)


# Roadmaps

## EOSC-Life tool roadmap


<img src="https://github.com/eosc-life/tools-collaboratory-roadmap/raw/master/images/EOSC-Life_T2.1.png" />
*Reference*: [https://github.com/eosc-life/tools-collaboratory-roadmap](https://github.com/eosc-life/tools-collaboratory-roadmap)

## EOSC-Nordic tool roadmap for the Climate community

Rather than reinventing the wheel, EOSC-Nordic chose to base its roadmap on the [EOSC-Life tools roadmap](https://github.com/eosc-life/tools-collaboratory-roadmap) and reuse as many components as possible for the Climate community. Strengthening collaboration with Galaxy Community and EOSC-Life is an integral part of its plan.

<img src="EOSC-Nordic_climate_tools_roadmap.png" />


# Data

## IDC - Intergalactic (reference) Data Commission

- [https://github.com/galaxyproject/idc/](https://github.com/galaxyproject/idc/) github repository is the entry point to contribute to the community-maintained CVMFS data repository, hosting approximately 6TB of public and open reference datasets.

## Climate (reference) Data

The size of climate datasets can be large (several PB) and making several copies on various Galaxy instance may not be a reasonnable approach.

The current approach for climate datasets is to use cloud storage and [zarr](https://zarr.readthedocs.io/en/stable/) so that anyone can seamingless access data remotely (faster access when locally available; should we then move tools to data?)

We usually distinguish "reference" data from "research data":

- **Reference data**: Climate data officially delivered by data providers (Copernicus, NOAA, EUMETSAT, WRCP). The goal will be to write Galaxy tool to facilitate access to these datasets within Galaxy. We may copy some datasets locally (for fast access and avoid duplication) and/or create workflows that automatically delete the raw dataset (as they can be retrieved again from the data provider).

**Remark**: some datasets are already stored on cloud storage such as [CMIP6](https://www.wcrp-climate.org/wgcm-cmip/wgcm-cmip6). See [CMIP6 public cloud storage datasets](https://console.cloud.google.com/marketplace/details/noaa-public/cmip6)

- **research data**: climate data generated by researchers may not contain sufficient metadata to be easily reused. Here we need to develop tools to "standardize" datasets and allow publication on cloud storage. 
As part of EOSC-Nordic, solutions based on the use of [owncloud](https://owncloud.org/), [zarr](https://zarr.readthedocs.io/en/stable/) and [intake catalog](https://intake.readthedocs.io/en/latest/catalog.html) (and [intake-esm](https://intake-esm.readthedocs.io/en/latest/), [intake-stac](https://intake-stac.readthedocs.io/en/latest/)) are investigated.

## Possible collaboration

The approach chosen by the climate community may be suitable for other communities.

We need to analyze and understand how all these different approaches can be supported by the Galaxy ecosystem (rather than trying to fit everyone within one framework).

The work planned within EOSC-Nordic framework and [WP5: Open Research data and services – demonstrators](https://www.eosc-nordic.eu/organisation/) could serve as a base for further collaboration work.

# Tools & packaging

So far we have use [bioconda](http://bioconda.github.io/) so that we would automatically get the corresponding docker container (see [https://github.com/BioContainers](https://github.com/BioContainers):


This means that our tools appear in [biocontainers.pro](https://biocontainers.pro/#/). [CESM](http://www.cesm.ucar.edu/) is a concrete example:
- [cesm in bioconda](https://bioconda.github.io/recipes/cesm/README.html)
- [cesm in biocontainers.pro](https://biocontainers.pro/#/tools/cesm)


## Possible collaboration

The collabroation is already effective. A few questions:

- Is it relevant to add all our tools to bioconda? Will the bioconda community be happy with it?
- Some of our tools & libraries are already in [conda-forge](https://conda-forge.org/) but we usually do not have the corresponding container. Should we rather use [conda-forge](https://conda-forge.org/) and then how would we automatically generate containers?

# Workflows

[Workflow hub](https://workflowhub.eu/) developments are driven by [EOSC-Life](https://www.eosc-life.eu/). Most of the work is generic and perfectly reusable by other communities.

A [workflow Hub Github organization](https://github.com/workflowhub-eu/) has been created.

[Workflow hub](https://workflowhub.eu/) is based on [SEEK](https://seek4science.org/),a web-based cataloguing and commons platform, for sharing heterogeneous scientific research datasets, models or simulations, processes and research outcomes. It preserves associations between them, along with information about the people and organisations.

- [ro-crate](http://www.researchobject.org/ro-crate/) is a community effort to establish a lightweight approach to packaging research data with their metadata. It is based on schema.org annotations in JSON-LD, and aims to make best-practice in formal metadata description accessible and practical for use in a wider variety of situations, from an individual researcher working with a folder of data, to large data-intensive computational research environments.

ro-crate objects can be downloaded from workflow hub.


## Workflow Hub Climate Team

Any workflows related to the Climate community and generated within Galaxy (either with interactive JupyterLab or with Galaxy tools) can be deposited to the [Climate Team](https://workflowhub.eu/projects/18).


## BioComputeObj

- [BioCompute Objects](https://www.biocomputeobject.org/): this project is very similar to workflow hub and [ro-crate](http://www.researchobject.org/ro-crate/). 
A R package [biocompute](https://cran.r-project.org/web/packages/biocompute/index.html) has been developed and allows the creation and manupulation of Bio Compute Objects. 


## Possible collaboration

- [galaxy2cwl](https://github.com/workflowhub-eu/galaxy2cwl): contribute to enhancement of **galaxy2cwl**.
- As the climate community also makes use of [cylc](https://cylc.github.io/), we could also contribute to workflow Hub by developing and maintaining a tool to convert to [CWL](https://www.commonwl.org/) e.g. **cylc2cwl**.

This work could be done by the [NICEST2](https://neic.no/nicest2/) (Nordic Collaboration on e-Infrastructures for Earth System Modeling) and [WP4: ESM workflows to efficiently run NorESM and EC-Earth on euroHPC](https://nordicesmhub.github.io/nicest2/2020/05/04/plan.html#wp4-esm-workflows-to-efficiently-run-noresm-and-ec-earth-on-eurohpc). 

- [ipython2cwl](https://ipython2cwl.readthedocs.io/en/latest/): is it any useful for converting our Jupyter notebooks into CWL? 

# Infrastructure

The Climate community mostly relies on the use of High Performance Computing for running operational simulations. However, with the use of Galaxy, we have demonstrated that cloud computing can provide a better framework for model development, teaching and most data analysis performed by researchers.

EOSC-Nordic investigates (at a policy level) on how to solve issues related to different access, accounting, authentication policies.

# Registries

## bio.tools 

[biotoolsregistry (bio.tools)](https://bio.tools/) is the Web application of the ELIXIR Tools & Data Services Registry. It allows the curation and discovery of bioinformatics resources including databases, tools, services and so on, available under a variety of interfaces.

The main objective of such registry is to help researchers to find existing tools thus avoid re-inventing the wheel. It is a community based registry which means that anyone can add new tools (you first need to register).

bio.tools depends upon a resource description model: [biotoolsSchema](https://github.com/bio-tools/biotoolsSchema). This description model is in XML and can be found [here](https://github.com/bio-tools/biotoolsSchema/blob/master/stable/biotools.xsd) or in [json format](https://github.com/bio-tools/biotoolsSchema/blob/master/jsonschema/biotoolsj.json).

The [EDAM](http://edamontology.org/page) ontology is used in biotoolsSchema for operations, types of data, data identifiers, data formats, and topics.

- Tools can be added either manually or automatically, harvesting scientific publications (mostly from [PubMed.gov](https://pubmed.ncbi.nlm.nih.gov/).

- The Climate Community could reuse what is done for [bio.tools](https://bio.tools/). The EDAM ontology would need to be extended.

### EDAM ontology

EOSC-Life makes use of the [EDAM](http://edamontology.org/page) ontology for bioinformatics operations, types of data, data identifiers, data formats, and topics.

EDAM ontology is used by [bio.tools](https://bio.tools/).

The EDAM ontology also covers the needs of the ecology community.

## biocontainers

As mentioned above, tools we have added to bioconda are also listed in [biocontainers.pro](https://biocontainers.pro/#/).

## Possible collaboration

### geo.tools & geocontainers.pro

With other communities interested in having registries for their tools and containers, the main question is whether we should "duplicate" or "generalize" what has been done for the Life Science community.

- should we have a more generic **science.tools** and **scicontainters.pro** or should we define (for each community) specific registries?
- it is probably useful to start with community web portals for registering tools (such as geotools for the Geosciences community) and later have a more generic science.tools (based on community tool registries).

### EDAM ontology

- Extend [EDAM](http://edamontology.org/page) ontology for Climate Science.

This work could be done within EOSC-Nordic WP5 and [NICEST2 WP3: FAIR climate data for NorESM and EC-Earth](https://nordicesmhub.github.io/nicest2/2020/05/04/plan.html#wp3-fair-climate-data-for-noresm-and-ec-earth). 
This would be beneficial for Climate tool registries, container registries and Galaxy tools.


# Training

## EOSC-Life Training Open Call

An application was submitted to [EOSC-Life Training Open Call](https://www.eosc-life.eu/services/open-call-training/) and accepted.

### Development of CLM-FATES training course

The main objective of the course is to learn how to compose and execute repeatable and reproducible modelling workflow with FATES (Functional Assembled Terrestrial Ecosystem Simulator). FATES is a numerical terrestrial ecosystem model for use in Earth System Models (ESM) that simulates and predicts growth, death, and regeneration of plants and subsequent tree size distributions. The simulation is done by allowing plants with different traits to compete for light, water, and nutrients, within an environment that tracks both natural and anthropogenic disturbance and recovery. FATES introduces ecosystem demography and dynamic vegetation into the structure of the land surface components of ESMs, allowing for full coupling to global atmosphere, ocean, and sea-ice processes. FATES is currently coupled to several Earth System Models, including CESM (Community Earth System Model), CTSM (Community Terrestrial Systems Model) and E3SM (Energy Exascale Earth System Model).

The learning objectives include:

- Understanding ecological, biogeochemical, biogeophysical, and hydrologic theory underpinning the CTSM.
- Running CLM-FATES in Galaxy for single-point locations where in-situ measurements are available.
- Analyzing CLM-FATES output and comparing it with observations.
- Sharing data (results from the simulations, in-situ data) using FAIR principles.
- Composing, executing and publishing the corresponding Galaxy workflow. 


During [BCC2020 CollaborationFest](https://bcc2020.github.io/cofest/) we have started to draft a Galaxy tutorial:
- [github repository with fates tutorial](https://github.com/NordicESMhub/galaxy-training-material/tree/fates/topics/climate/tutorials/fates)
- [Corresponding Pull Request in GTN](https://github.com/galaxyproject/training-material/pull/1993)

More information will come as the project starts.


