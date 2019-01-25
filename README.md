[![Python](https://img.shields.io/badge/Python-3.5-green.svg?style=flat-square)](/)

guppy_bcsplit
===============

## Installation

I saw someone on the Nanopore community unsure of how to use the program so these are some install steps that I used. Until ```guppy``` can demultiplex files natively (which should be soon), other programs will have to be used. If you've already run ```guppy_barcoder``` this script will work for you. Thanks to Michael Schmid for making the script.



I installed guppy_bcsplit in a conda environment and was was having issues with python 3.x so I used ```python 2.7```. ```biopython``` is required for ```guppy_bcsplit``` to function and was designed for ```python2.7``` initially.



Create a new conda environment with python2.7

```conda create --name guppybc python=2.7```



Activate your environment:

```source activate guppybc```



```biopython``` is required for guppy_bcsplit to work since it imports the ```Bio``` module from ```SeqIO```.

I used pip to install this time but I normally will use a conda install.

```pip install biopython```

You could try a ```conda install``` instead:

```conda install -c bioconda biopython```



I like to keep the clone in my environment folder so it's easier for me to find.

```cd ~/miniconda3/envs/guppybc/guppy_bcsplit```



Now copy the git repository:

```git clone https://github.com/ms-gx/guppy_bcsplit.git```

It's only one python file so you could easily put it anywhere.

Unless you change your PATH you'll have to ```cd``` and execute the script where it's located with ```./guppy_bcsplit.py```:


If you have multiple fastq files, you'll need to concatenate them first:

```cat source_folder/*.fastq >> destination_folder/name.fastq``` 


## Commands

Unless you've added guppy_bcsplit to PATH you will need ```cd``` and run it from the folder with ```./guppy_bcsplit.py```

The following commands for guppy_bcsplit are:



```-b``` is the folder containing the guppy barcoding summary file generated by ```guppy```.



```-f``` is the folder containing the ```.fastq``` files. If you wanted to point to a specific file, just add name ```.fastq``` after the folder



```-p``` is the prefix that gets attached to ```barcodeXX``` so it will look like ```prefix_barcodexx.fastq```.



```-s``` is the folder where guppy_bcsplit will output a summary text of how many of each barcodes and unclassified reads there were.



```./guppy_bcsplit.py -b folder_containing_guppy_barcode_summary/barcoding_summary.txt -f folder_containing_guppy_fastq_concatenated/ -p prefix -s folder/guppy_bcsplit_summary.txt```



```guppy_bcsplit``` should now demultiplex your barcodes and unclassified to separate ```.fastq``` files and create a summary output.
