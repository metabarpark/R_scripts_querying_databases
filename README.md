# R_scripts_querying_databases

R scripts to automatically retrieve data from databases such as BOLD, Genbank, Fishbase... and add the taxonomy identification (taxid).


# get_Reference_Database_from_BOLD.R

This script was used for building the reference database for the Fields fragment of COI of elasmobranchs. If you use it please consider citing the following publications:

- Bakker J, Wangensteen OS, Chapman DD, Boussarie G, Buddo D, Guttridge TL, Hertler H, Mouillot D, Vigliola L, Mariani S. (2017). Environmental DNA reveals tropical shark diversity in contrasting levels of anthropogenic impact. Scientific reports, 7, 16886.

- Boussarie G, Bakker J, Wangensteen OS, Mariani S, Bonnin L, Juhel J-B, Kiszka JJ, Kulbicki M, Manel S, Robbins WD, Vigliola L, Mouillot D (2018) Environmental DNA illuminates the dark diversity of sharks. Submitted.

The script will automatically download from BOLD the sequences for any given taxon. Then in silico ecopcr will be performed with the given set of primers (note than the primer binding region must be included in the sequences downloaded from the database for this procedure to work). The script will add the taxonomy identifier (taxid) from the NCBI Taxonomy dump, so that the output is a reference database in fasta format, including the taxids for every sequence, that can be used for taxonomic assigment using ecotag. The sequences with a known species name, but without a valid taxid in the NCBI Taxonomy dump, will be assigned new taxids that can be added to a local taxonomy database in ecopcr-database format. Finally, for those sequences without a valid species name or taxid, a data frame is created including additional information of the specimens, that can be curated manually and added to the final reference database.

Note that some additional curating procedures need to be performed on the output fasta file before it can work fine with ecotag. Deleting sequences with unknown bases (Ns) is required. A refining step is also recommended, to remove the redundancy and minimize the size of the files and the computing times, by removing those sequences which are exactly equal, and belong to the same taxid. This could be done using a combination of obiuniq and obigrep.
