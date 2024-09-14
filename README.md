# staticMLAMR
Auto AMR prediction via ML with MALDI-TOF MS for clinical microbiology lab.

Only some LR models are available for testing. It will soon be updated with a complete set of pretrained models.

Colab link: 
https://colab.research.google.com/github/iron-lion/staticMLAMR/blob/main/notebook/colabMLAMR.ipynb

## How to use
### Single spectra run
Prepare a single compressed file with .zip/.tar.gz of MALDI-TOF MS spectra profile.

Directory structure should be like this.
```
sample_id.zip

sample_id
        ㄴ 1
           ㄴ  1SLin
                   ㄴ pdata - ...
                   ㄴ acqu
                   ㄴ acqus
                   ㄴ fid
                   ㄴ sptype
```


### Batch run
Copy your spectra profiles onto /content/data/raw

Raw data should have following structure.
```
example
./data/raw/Escherichia_coli/[sample_id1]/1/1SLin...
./data/raw/Escherichia_coli/[sample_id2]/1/1SLin...
./data/raw/Staphylococcus_aureus/[sample_id3]/1/1SLin...
./data/raw/Klebsiella_pneumoniae/[sample_id4]/1/1SLin...
./data/raw/Klebsiella_pneumoniae/[sample_id4]/1/1SLin...
```

## Results
Prediction results will be saved in results directory
```
example
./results/Escherichia_coli/[sample_id1]_raw.csv
./results/Escherichia_coli/[sample_id1]_summary.csv
./results/Escherichia_coli/[sample_id2]_raw.csv
./results/Escherichia_coli/[sample_id2]_summary.csv
...
```

### raw result file
```
 train_site	ML	species	antibiotics	seed	S	R
0	UMG-0	lr	Escherichia	Ampicillin	409	0.495833470639805	0.504166529360195
0	UMG-0	lr	Escherichia	Ciprofloxacin	545	0.895790219002116	0.104209780997884
0	UMG-0	lr	Escherichia	Ciprofloxacin	164	0.765351701679898	0.234648298320102
0	UMG-0	lr	Escherichia	Cefotaxim	545	0.813916171479991	0.186083828520009
```
It will show pred_prob from each pre-trained ML models

### summary result file
```
Antibiotics	Resistant	Susceptible
Ampicillin	2	9
Ampicillin+Sulbactam	0	11
Cefotaxim	0	11
Ceftazidime	0	11
Ceftriaxone	0	11
Ciprofloxacin	0	11
Gentamicin	10	1
Piperacillin-Tazobactam	0	11
```
It will show count of predicted labels from set of models
