# Normal RoadMap Data
Codes applied for the roadmap data analysis part.


## Downsamling & Creating sorted & indexed bam files from tagAlign files
If you see 
'-bash: shuf: command not found'
run following code:
```bash
brew install coreutils
```

``` bash
for tg in *.tagAlign.gz
do 
	zless $tg | shuf -n 15000000 | bedtobam -i - -g hg19.txt | samtools sort -o "${tg%%.*}".sorted.bam 
	samtools index "${tg%%.*}".sorted.bam
done 
```

### Check the number of Reads for each bam file
```bash
for file in *.sorted.bam; do samtools idxstats "${file%%.*}".sorted.bam | cut -f3 | awk 'BEGIN {total=0} {total += $1} END {print total}'; done 
```


## Counting the Number of Reads around TSS 
```bash

```

for file in *.tagAlign; do   bedtools bedtobam -i "${file%%.*}".tagAlign -g hg19.txt > "${file%%.*}".bam; done
for file in *.bam; do samtools idxstats "${file%%.*}".bam | cut -f3 | awk 'BEGIN {total=0} {total += $1} END {print total}'; done 


bedtools bedtobam -i "${file%%.*}".tagAlign -g hg19chrom.sizes > "${file%%.*}"

zless $tg | shuf -n 15000000 | bedtobam -i - -g hg19.txt

E075-H3K27me3.sorted.bam
E075-H3K4me1.sorted.bam	
E075-H3K4me3.sorted.bam
E075-H3K9me3.sorted.bam
E087-H3K27me3.sorted.bam
E087-H3K4me1.sorted.bam




