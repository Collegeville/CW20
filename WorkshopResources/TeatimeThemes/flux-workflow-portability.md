# Flux: Solving Exascale Workflow Portability and Execution Challenges

*Teatime theme - Collegeville 2020*

*Dong H. Ahn, Lawrence Livermore National Laboratory*
*Stephen Herbein, Lawrence Livermore National Laboratory*

Successfully deploying modern workflows across multiple computing sites has
become exceedingly difficult. Modern scientific workflows require far more
complex interplays among physics simulations, data stores, analysis and
visualization tools, etc. These requirements outstrip the capabilities of
today’s scheduling systems. Programming and scalability challenges have caused
the creation of many ad-hoc approaches to workflow management which place a
significant burden on scientific developers for research, development, and
maintenance. These efforts are compounded by the lack of portability and common
interfaces across existing schedulers (e.g., Slurm, Moab, PBSPro, LSF,
Kubernetes).

In this teatime, we will discuss how our users use Flux, a next-generation
resource and job management framework, to solve these portability challenges as
well as other emerging batch-job and workflow scheduling problems, including:

- Task Co-scheduling
- Inter-Task Coordination & Communication
- System Throughput
- Job Provenance
