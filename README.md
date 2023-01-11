# Title of your paper
### Members
* 劉育佑, 111753145
* 翁佑祥, 111753226
* 周庭威, 111753223
* 張禎尹, 111753136

### Demo 

You might provide an example commend or few commends to reproduce your analysis, i.e., the following R script

Juicer Launch Instruction
```
bash scripts/juicer.sh  -d <path/opt> \
-D <path/opt> \
-y restriction_sites/hg38_MboI.txt  \
-z references/Homo_sapiens_assembly38.fasta \
-p restriction_sites/hg38.chrom.sizes \
-s MboI 
```

```R
Rscript code/your_script.R --input data/training --output results/performance.tsv
```

## Folder organization and its related information
idea by Noble WS (2009) [A Quick Guide to Organizing Computational Biology Projects.](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1000424) PLoS Comput Biol 5(7): e1000424.

### docs
* Your presentation, 1112_bioinformatics_FP_studentID.ppt/pptx/pdf (i.e.,1112_bioinformatics_FP_556688.ppt), by **01.12**
* Any related document for the project
  * i.e., software user guide

### data
* Source
* Format
* Size

### code
* Which packages do you use? 
  * original packages in the paper
  * additional packages you found
* Analysis steps

### results
* Which part of the paper do you reproduce?
* Any improvement or change by your package?

## References
* Packages you use
* Related publications
