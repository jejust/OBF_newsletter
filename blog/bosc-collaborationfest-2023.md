# BOSC CollaborationFest 2023 Report


CollaborationFest, CoFest for short, is a collaborative work event that brings together experts in fields as diverse as plant biology and personalized medicine. CoFest has been held immediately before or after BOSC, continuously over the past 13 years. Hervé Ménager and Jérémy Just co-organized [CoFest 2023](https://www.open-bio.org/events/bosc-2023/obf-bosc-collaborationfest-2023/), held the two days before BOSC 2023 in Lyon, France. The event was hosted by the nearby [École Normale Supérieure de Lyon](https://www.ens-lyon.fr/en/). 29 people participated in person, and others participated online. Thanks to our local hosts, many local and first-time attendees were able to join us. Figuring out how best to integrate remote participants with in-person ones is still challenging.


As in previous years, CoFest participants were involved in a wide variety of projects focused on topics such as the documentation of existing software (e.g., BioPython tutorial, update of the BLAST Book), the review and discussion of novel technologies (e.g., Large Language Models), the performance improvement of single-cell RNA-seq data processing (MultiK package), the implementation of new features in existing protein visualization software (iCn3D viewer), and several FAIR-related projects (workflows, development guidelines, provenance, and ontologies). In total, the participants worked on ten different projects, with tangible accomplishments for several subtasks of these projects. In addition, cross-project discussions facilitated progress on many projects, exchanging perspectives and pointers between participants. Notably, one of the projects that was worked on at CoFest has already led to a peer-reviewed publication: ~Making Biomedical Research Software FAIR.~


%%FIXME: Picture of the project list with ecocup and mug




## iCn3D protein viewer

Abstract: iCn3D is a web-based 3D structure viewer synchronizing 1D, 2D, and 3D view, e.g., https://www.ncbi.nlm.nih.gov/Structure/icn3d/?refseqid=NP_001243728.1&showanno=1. The 1D sequence view shows all kind of annotations (e.g., domains, SNP, etc) in tracks. This project will show the start and end positions of exons in the sequence, and show the sequence of isoforms of the protein and their exons. Thus users can clearly see the exon skipping and potentially relate the exon skipping to the protein functions.


In 2023 BOSC Hackathon, [iCn3D viewer](https://www.ncbi.nlm.nih.gov/Structure/icn3d/) got a new feature to show isoforms and exons as tracks with the button "Add Track" in the "Sequences & Annotations" window via the menu "Analysis > Sequences & Annotations". One example is at [https://structure.ncbi.nlm.nih.gov/icn3d/share.html?pA3pPu7LxdiuZDVX7](https://structure.ncbi.nlm.nih.gov/icn3d/share.html?pA3pPu7LxdiuZDVX7):

  %% Image iCn3D_viewer.png

Users can also predict structures from sequences using ESMFold directly in iCn3D via the menu "File > Predict by Seq. > ESMFold". Other features of iCn3D are listed in its GitHub page: https://github.com/ncbi/icn3d.


## Report updating Ian Korf~s BLAST book

What was done:
 * Scoping discussion on Slack,
 * Side-by-side option table (_old_ vs _new_ options),
 * Practical testing of old examples from the book using the new syntax.

Future work:
 * Write down the updated examples as a [web page](https://github.com/jejust/blast_book_plus)



## Report on Biopython

What was done:
 * Progress on LaTeX to RST/Sphinx conversion of Tutorial (Tables, Citations)
 * Helped Clément with a FASTQ script - (speed up reads extraction, 6x faster)

Future work:
 * Try to get the converted Tutorial to build without errors

Questions to CoFest group:
 * What file format would you prefer for the Tutorial (HTML, PDF, eBook, ~)?



## Report on MultiK parallelization using future

What was done:
 * The first main loop (out of two) was parallelized
     * works when used locally & remotely on reduced dataset
     * 10x performance for the whole function
 * Crashing using full dataset remotely (`Error: Detected a non-exportable reference (~externalptr~) used in the future expression`)

Future work:
 * Investigate the crash further
 * Parallelize the second main loop of MultiK



## Report on project "Bionano tools dependencies extraction from a docker image"

What was done:
 * Installation of Bionano docker,
 * Inspection of Bionano tools installation script.

Future work:
 * Detailed list of dependencies, starting from python / R package and software present in the docker image,
 * (Bio)Conda recipe documentation exploration.



## Report on project: open source LLMs

What was done:
 * Shared documentation to collect ideas and useful links
     * Tips for choosing/testing open source LLMs
     * Some ideas for applications and benchmarking of the models

Future work:
 * Summarize the document and merge into the paper being prepared by the LLM group from BioHackathon Japan that will be submitted to biohackrxiv
     * https://biohackrxiv.org/discover 
     * http://preview.biohackrxiv.org/ 



## FAIR Biomedical Research Software (FAIR-BioRS)

What was done:
 * Worked with some attendees to explore how the guidelines would apply to their project
 * Scope discussion, and at least one pull request merged
 * Notes from discussion available at https://etherpad.osuosl.org/p/Cofest2023-fair-BioRS
 * Discussion to wrap up on the paper and plan for future outreach/communication effort

This project had already benefited from BOSC CoFest 2022, and is now published in a peer-reviewed paper: _[Making Biomedical Research Software FAIR](https://doi.org/10.1038/s41597-023-02463-x)._



Future work:
 * Outreach/communication effort

Questions to CoFest group:
 * Would you use the guidelines to make your research software reusable? If not, why, how can they be improved?



## Report on CWL v1.2.1 release work

108 proposed clarifications to the Common Workflow Language v1.2 standards need summarizing

What was done:
 * all done!

See:
 * [Introduction to the CWL Command Line Tool draft standard v1.2.1](https://deploy-preview-262--cwl-v1-2-dev.netlify.app/commandlinetool#Introduction_to_the_CWL_Command_Line_Tool_draft_standard_v1.2.1)
 * [Changelog_for_v1.2.1](https://deploy-preview-262--cwl-v1-2-dev.netlify.app/workflow#Changelog_for_v1.2.1)

Future work
 * Get these changes reviewed & merged

Questions to CoFest group:
 * [reviews](https://github.com/common-workflow-language/cwl-v1.2/pull/262/files) are very welcome! (Especially by those with CWL experience)



## Report on project WR RO-Crate queries

What was done: 
 * Made [SPARQL queries](https://github.com/RenskeW/runcrate-analysis/tree/main/test-prov) to answer provenance questions from ro-crate-manifest.json

Future work: 
 * Add more queries to the list

Questions to CoFest group:
 * How to use SPARQL queries as unit tests?



## WfExS-backend changes to support envvars and get conformant to Workflow Run RO-Crate 0.2

 * Added support to describe environment variables needed by a workflow execution.
 * Integrated used environment variables as inputs in Workflow Run RO-Crate, using FormalParameter. There is no standard way to signal which FormalParameters are a traditional workflow parameter and which are environment variables (besides the id).
 * _(partially implemented)_ Output files and directories are not using an nih URI any more.
 * _(work in progress)_ Better representation of CWL workflow dependencies, so the usage of an external ontology does not appear as a ~hard~ dependency itself.





_We would like to thank the entire BOSC community for maintaining the positive atmosphere that makes such events a success!_
