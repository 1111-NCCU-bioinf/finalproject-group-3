# TADs are 3D structural units of higher-order chromosome organization in Drosophila
## Members
* 劉育佑, 111753145
* 翁佑祥, 111753226
* 周庭威, 111753223
* 張禎尹, 111753136

## Demo 

Juicer Full Instruction
```
mkdir ./opt 
cd opt
git clone https://github.com/theaidenlab/juicer.git
ln -s juicer/CPU scripts
cd scripts/common
wget http://hicfiles.tc4ga.com.s3.amazonaws.com/public/juicer/juicer_tools.1.7.6_jcuda.0.8.jar
ln -s juicer_tools.1.7.6_jcuda.0.8.jar juicer_tools.jar
cd ../..
mkdir references
cd references 
cp <path>/[Reference Fasta File Name].fasta  
bwa index  [Reference Fasta File Name].fasta
cd ..
mkdir restriction_sites
cd restriction_sites/
python2 ../juicer/misc/generate_site_positions.py  MboI  hg38_MboI ../references/[Reference Fasta File Name].fasta 
awk 'BEGIN{OFS="\t"}{print $1, $NF}' [Restriction_site_file_name].txt > [Restriction_site_file_name].chrom.sizes
cd ..
mkdir fastq && cd fastq  #Get_Test_fasta
nohup wget http://juicerawsmirror.s3.amazonaws.com/opt/juicer/work/HIC003/fastq/HIC003_S2_L001_R1_001.fastq.gz &
nohup wget http://juicerawsmirror.s3.amazonaws.com/opt/juicer/work/HIC003/fastq/HIC003_S2_L001_R2_001.fastq.gz &
cd ..
# Run Juicer
bash scripts/juicer.sh  -d <path/opt>  -D <path/opt> -y restriction_sites/hg38_MboI.txt  -z references/Homo_sapiens_assembly38.fasta -p restriction_sites/[Restriction_site_file_name].chrom.sizes -s MboI 
```

Juicer Launch Instruction
```
bash scripts/juicer.sh  -d <path/opt> \
-D <path/opt> \
-y restriction_sites/hg38_MboI.txt  \
-z references/Homo_sapiens_assembly38.fasta \
-p restriction_sites/hg38.chrom.sizes \
-s MboI 
```


HiC PRo Launch Instruction
```
HiC-Pro -c config-hicpro.txt -i [rawdata directory] -o [output file directory]
```


```R
Rscript code/your_script.R --input data/training --output results/performance.tsv
```

## Folder organization and its related information
idea by Noble WS (2009) [A Quick Guide to Organizing Computational Biology Projects.](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1000424) PLoS Comput Biol 5(7): e1000424.

### docs
* Presentation powerpoint , 1112_bioinformatics_FP_studentID.ppt/pptx/pdf (i.e.,1112_bioinformatics_FP_556688.ppt), by **01.12**
* Any related document for the project
  * i.e., software user guide

### data
Input Data:
* Source:NCBI GSE99107 https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE99107
* Format: .sra/.FASTQ/.FASTA/.gz
* Size: about 1 TB

### code
* Packages we use 
  * HiC Explorer
  * HiC Pro
    * Python2.7
    * hicpro
    * samtools
    * bowtie2 
    * R
    * pysam 
    * bx-python 
    * numpy 
    * scipy 
    * ggplot2(R)
    * RColorBrewer(R)

  * Juicer
  * JuiceBox
* Analysis steps

### results
* Which part of the paper do you reproduce?
* Any improvement or change by your package?

## References
* Packages 
  * Juicer Website:https://aidenlab.org/documentation.html
  * Juicer Github: https://github.com/aidenlab/juicer
  * BWA :  http://bio-bwa.sourceforge.net/
  * Hi-C Pro : https://github.com/nservant/HiC-Pro
* Related publications
  * Hi-C Pro Servant N., Varoquaux N., Lajoie BR., Viara E., Chen CJ., Vert JP., Dekker J., Heard E., Barillot E. HiC-Pro: An optimized and flexible pipeline for Hi-C processing. Genome Biology 2015, 16:259 doi:10.1186/s13059-015-0831-x
  * 
