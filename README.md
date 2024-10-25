# WGS_Bscript
# Simple script for whole genome sequence

This bash script is prepared for whole genome sequencing data analysis on the Compute Canada server. The target is to use only the tools in the Compute Canada module without installing extra libraries or tools and create a simple workflow for paired-end short-read sequence analysis, including QC, trimming, assembly, and annotation. The test was conducted in the Compute Canada Beluga Server.

**Workflow**

**Preparation:**

1. ***Create a directory and get its pathway.***
  
2. ***Collect or make your own primer file (it should be '.fa' or '.fasta' file) and get its pathway***
  
3. ***Modified bash scrip***
  
  Download the wgs_bscript. Then change the head of this job (You might need to change the time, memory and node depending on the number of sequences)
  
  ```
  #!/bin/bash
  #SBATCH --account=your account name
  #SBATCH --time=48:00:00
  #SBATCH --job-name=the name of your job
  #SBATCH --output=%x-%j.out
  #SBATCH --mail-user=your email
  #SBATCH --mail-type=ALL
  #SBATCH --mem-per-cpu=186G  
  #SBATCH -n 2
  ```
  
  Provide the raw sequences data directory
  
  ```
  raw_data_path=/path/to/your/raw/data
  ```
  
  Define your working directory: where you want to put your results
  
  ```
  path=/path/to/your/working/directory/
  ```
  
  Add Nextera.fa in your working directory
  
  ```
  primer_path=/home/tiff08/scratch/github_script_test/primers.fa
  ```
  
  **Notes**
  
  1. ***In this script, it will recognize the "_R1_001.fastq.gz" and "_R2_001.fastq.gz" as the end of raw reads. And keep all the names in front. If this is not your case, please change lines 50, 51, and 52 to your desired format.***
    
  2. ***In this script, you can change all the versions of your tools from line 11 to 20.***
    
  3. ***In this script, you should change all the parameters of the tools based on your needs.***
