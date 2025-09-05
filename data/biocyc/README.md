# BioCyc data files

The BioCyc database [^1] contains useful information about genomes and pathway, which can be utelised by a number of functions in refineGEMs, e.g. the gap-filler for the corresponding database.

However, BioCyc requires a subscription for the required Smart Tables. To enable these features for the user without being too restrictive, the functions (and in the the workflows of SPECIMEN) can be run with and without these files. If you have a BioCyc subscription and want to try out any of the functionalities working with the database, here are some instructions for the Smart Tables, that can be used as input:

**BioCycGapFiller**

The BioCyc gap-filler requires two files from BioCyc as input, one for the genes, one for the reactions.

- Genes: 
    - Make a copy of the `All genes of <organism>` Smart Table
    - Add the columns `Accession-2` and `Reactions of gene`
    - Remove all columns except of the added one, except, if the idetifiers matiching your models are not storen in `Accession-2` but in `Accesion-1`
        - If necessary, rename `Accession-1` to `Accession-2`
    - Delete empty rows
    - Export to spreadsheet file with the option `frame IDs`
- Reactions:
    - Make a copy of the `All reactions of <organism>` Smart Table
    - Add the columns `Object ID` and `Spontaneous?`. You should now have four columns in total (the other being `Reaction` and `EC-Number`)
    - Export to spreadsheet file with the option `common names`

**Reaction direction**

As BioCyc is one of the only databases to save reaction directions, one can add this information using `refinegems.curation.curate.reaction_direction.` To get the data file, start with the `All reactions of <organism>` Smart Table and add and remove columns until you have the following format:

 ``Reactions (MetaCyc ID) | EC-Number | KEGG reaction | METANETX | Reaction-Direction``

-----
[^1] Karp, P.D., et al., The BioCyc collection of microbial genomes and metabolic pathways
Briefings in Bioinformatics (2019).