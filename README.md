# BI_Listeria_project
Authors: 
- Tarbeeva Svetlana
- Kozlova Anna

### Introduction
*Listeria monocytogenes* is a pathogenic bacterium commonly found in food processing environments, particularly in meat production facilities. Its ability to form biofilms on various surfaces poses a significant risk for food contamination and subsequent foodborne illnesses. To better understand the factors contributing to biofilm growth and the development of resistance, the application of advanced sequencing technologies such as Oxford Nanopore Technologies (ONT) sequencing has emerged as a valuable tool. 

### Aim, tasks and data
In this study, we aimed to investigate the growth of biofilms containing *Listeria monocytogenes*. We obtained ONT sequencing data from meat and poultry processing plants, as well as panoramic MS (Mass Spectrometry) analysis data. The data were provided by [Institute of biomedical chemistry](https://www.ibmc.msk.ru/). These biofilms were previously treated with disinfectants based on Quaternary Ammonium Compounds, acetic acid, and chlorine. Our goal was to determine why the biofilms developed in unexpected areas and identify the determinants of their resistance.

### Workflow
Initially, the ONT sequencing files were converted from FAST5 to FASTQ format using basecaller software. 
```
guppy_basecaller -i ~/work1/Lm_137/pass/ -s ~/work1/Lm_137/guppy_res_pass_137 --flowcell FLO-MIN106 --kit SQK-RBK004 --device auto
```
To evaluate the quality of the sequencing data, standard quality assessment protocols were planned, but were unfortunately not performed initially. 
Several genome assemblers, including wtdbg2, widely recognized fleu, and raven, were tested, and their results were compared using the quast tool. 

```
./wtdbg2 -x rs -g 3m -i lm_big137.fq.gz -t 16 -fo assembl_lm_137
./wtpoa-cns -t 16 -i assembl_lm_137.ctg.lay.gz -fo assembl_lm_137.raw.fa

raven lm_big137.fq.gz > raven_Ls137.fa

flye --nano-raw lm_big137.fq.gz --out-dir /home/fox/work1/meat

```


```
bonito basecaller dna_r9.4.1_e8_fast@v3.4 pass > 137p_bonito_basecalled.fastq
```
### Results

### Conclusion and further plans

### Literature
