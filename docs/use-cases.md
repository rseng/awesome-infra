# Use Cases

> Are there repeated/typical use cases for cloud apps we encounter in our work?

For each entry here, try to answer:

 - What are they? Try to be specific
 - What are our pain points for providing these solutions

## Automated Services (e.g., Build)

**rseng-developer**

Historically, for the subset of technologies that we want to use (e.g., containers) that we were not previously able to build on our local HPC, nor were we easily able to build in public continuous integration, an RSEng at an institution might spin up a custom service to provide this. The example that comes to mind is Singularity Hub, which ran from ~2015 to 2020 and provided:

 - connection to GitHub repositories with Singularity recipes
 - automated builds on events (e.g., commit or release)
 - storage of the final SIF for easy pull (and sharing) down to a system
 
More generally, these services are trying to handle the handicapped nature of being a user on a shared system - you typically don't have permissions to do what you want, and the tendency for RSEng-specific software to not be supported by commercial products. For this example, the main problem was that you couldn't push a Singularity container to an OCI registry, and thus there was no easy way to build and deploy these artifacts.

The pain points for providing this service on cloud were costs and reproducibility. E.g., by the end of the registry life, there were over 9TB of containers, with costs (controlled) but still about $500/month. It was the job of the single RSEng to raise money for the service. In terms of reproducibility, the promise was kept, as the registry was moved to a static archive at Dartmouth (and all containers built on the platform are still pull-able). Of course we have to ask - what is going to sustain this second resource in the future, cloud or not?

This need is no longer there, as it is possible to push SIF to registries that support ORAS (OCI Registry As Storage) and it's also very easy to build in GitHub/GitLab and other CI actions. To summarize:

> RSEng need to provide services around automation for compute or storage of artifacts that isn't possible to do with local or commercial resources.  
 
## Lab Apps

**lab-embedded-rseng**

For this example, we have a large lab that hires an RSEng to help with putting together a system for making orders of genetic parts. In this case, this was an early version of the [FreeGenes](https://stanford.freegenes.org/) project. It's not possible to deploy a consistent web service (that exposes a web portal) on HPC resources, and generally institutions don't have compute available anywhere else for this kind of thing. The RSEng thus needs to build a custom web interface and experiment or "shopping cart" system to manage and distribute resources for the lab. This is an ongoing need as there is no one size fits all solution.

The pain point in providing this kind of solution is that it tends to be an entirely new development endevour each time. You would need to provide (and maintain) common templates with plugins for assembling custom interfaces. It's also challenging in terms of establishing branding (e.g., design and logos) which is typically a stretch for the RSEng skill set.

## Run Anywhere

**rseng-developer**

While many academic institutions have HPC clusters, some researchers do not, or rather choose to use cloud resources. This introduces the idea of "run anywhere" - or the reality that when Researcher A does an analysis on an HPC system, it should seamlessly be able to move to a different kind of environment. Typically, this is best afforded by workflow management tools that start with simple configs that can be run in multiple contexts (e.g., Nextflow or Snakemake).

The challenges here are that it's really hard to choose such a manager, and once you do, it's hard to debug when something goes wrong on a cloud, or it's hard to learn a new syntax.

## HPC Integration

**rseng-developer**

When we run tests on a public CI service, what we cannot easily do is connect our testing to our local resources (where they might ultimately run). If the cloud could emulate these environments we could arguably create a better testbed for testing. Of course, this would be challenging in terms of costs, and requiring a researcher to have a cloud account. More generally, when a center tries to do some kind of tutorial on the cloud, the hardest parts tend to be getting people setup with credentials and then over the initial learning curve of using some cloud interface.
