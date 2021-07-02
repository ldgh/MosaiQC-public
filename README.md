# MosaiQC

Smart Cleaning automates the complete LDGH cleaning pipeline, including the steps:
- Remove chr 0
- Remove duplicate data
- Remove missing data
- Infer individual sex
- Remove A|T and C|G variants
- Anotate the variants for DBSNP ID
- LiftOver

Beta testers: 
Mateus Gouveia (Rotimi's group, NHGRI/NIH),
Esteban Parra group (University of Toronto),
Marilia Scliar (Mayana Zatz group, University of Sao Paulo),
Ignacio Mata Lab at the Genomic Medicine Institute (Cleveland Clinics, OH, US)


## Requirements
Smart Cleaning script was implemented using python language. But the following programs are required:
- Plink

## Files Required
### database
File with the description of the databases that will be cleaning. 
This file contains five columns separated by \t. The columns are: 
- Population name (posteriorly will be used in the final file name)
- plink bfile input location
- first chromosome in the file
- last chromosome in the file 
- input file genome version

Example:
```
#POP	Grupo	Caminho	ChrInicial	ChrFinal	build
M1	/home/thiago/Testes_ABC/SUDAN_extraido	1	1	37

```
### reference
File with the path of reference files.
This file contains two columns separated by \t. The columns are: 
- Name of reference dataset
- Path to the reference file
Example:
```
DBSNP	/media/thiago/Data/Unificado/Ref/dbSNP_HG38_HG37_last_version_chr*_corrected.txt.gz
KGP	/media/thiago/Data/Unificado/Ref/HumanOmni5Exome-4-v1-1-B-auxilliary-file.txt

```
### programs

File with the path to the programs used.
This file contains two columns separated by \t. The columns are: 
- Name of program
- Path to the program
Example:

```
plink	/home/thiago/Programs/plink

```
## Parameters
#### Mandatory Parameters
```
    --programs or -p          File with the path to the programs used
    --reference or -r         File with the path of reference files
    --database or -d          File with the description of the databases
    --folder or -f            Folder to store the intermediary files and output files
    
```
#### Optional Parameters
```
    --change or -c           Change the genome version for that choosed by the user
    --chromosomeX or -x      Set the program make sexual chromosome steps. If you select, you have to put the genome version -see: https://www.cog-genomics.org/plink/1.9/data#split_x 
    --steps or -s            Steps to be performed ant their respective parameters
    --lastautossomal or -l   Number of the last autosomal chromosome (default 22)
```
#### Execution example
```
 python3 main.py -d database.txt -r reference.txt  -p programas.txt -c 37 -f /media/DadosCongelados/DadosLimpos/
 
```
