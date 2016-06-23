# QuagmiR
A python-based miRNA sequencing pipeline for isomiR quantification and analysis

## Dependencies
* Make sure that you have [Python 3.4+](https://www.python.org/downloads/) installed (type `python --version` in the console) 
* Make sure you have the latest version of pip: `pip3 install -U pip`
* Make sure you have [Miniconda](http://conda.pydata.org/docs/install/quick.html) installed

## Installation
1. Download repository: `git clone https://github.com/kevchn/quagmir`
2. Go into local quagmir folder: `cd quagmir`
3. Install Python dependencies: `conda create -n quagmir python=3 --file req.txt`

## Usage

1. Add your .fastq_ready samples into the data folder (a sample has been provided for testing):
  <pre>
  ├── LICENSE
  ├── README.md
  ├── config.yaml
  ├── Snakefile
  ├── data/
  │   ├── sample.fastq_ready
  │   └── <b>YOUR_FILE_HERE.fastq_ready</b>
  |   ├── collapsed/
  ├── motif-consensus.fa
  └── results/
  </pre>

2. Edit the **motif-consensus.fa** file to insert your miRNA information with the following format:
  ```
  >miRNA_name miRNA_motif
  miRNA_consensus_sequence

  >passenger-shRNA-mir21-ORF59-5p-1 ACACCCTGGCCGGGT
  CCGACACCCTGGCCGGGTTGT
  ```

3. Edit the **config.yaml** file to change configuration options if needed (default values fine in most use cases):
  ```
  min_ratio: .001
  min_read: 9
  ```

4. Run pipeline: `snakemake`

## Notes
The step of collapsing sample files takes the longest time, but once the samples are collapsed, and you need to re-run the pipeline, the pipeline will automatically start from the collapsed files and take a far shorter amount of time

Output will be a **sample.fastq_ready.results.txt** file for each sample in the **results/** folder

## Features
Coming soon
