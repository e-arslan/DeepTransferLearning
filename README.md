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






