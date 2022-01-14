# Public single cell datasets

Some public single cell datasets, and derivative products I've made from them.

## Datasets

### `Mnemiopsis_2018`

From [Sebé-Pedrós 2018](https://doi.org/10.1038/s41559-018-0575-6).

I created a file with blast hits for the protein data as follows:

```
wget ftp://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/complete/uniprot_
sprot.fasta.gz
gunzip uniprot_sprot.fasta.gz
makeblastdb -in uniprot_sprot.fasta -out uniprot_sprot -dbtype prot
blastp \
  -query Mnemiopsis_proteins.fasta \
  -db ./uniprot_sprot \
  -evalue 1e-6 \
  -max_target_seqs 10 \
  -outfmt "6 qseqid sseqid evalue pident length stitle sstrand" \
  -out mnemiopsis_blast.out \
  -num_threads=$SLURM_CPUS_PER_TASK
```

