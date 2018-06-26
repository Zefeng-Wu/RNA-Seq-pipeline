# RNA-Seq-pipeline

Here we developed a general pipeline to perform RNA-seq data analysis


## Tophat mapping
    for m in $(ls *.fastq | awk 'BEGIN{FS="_"}{print $1}' | uniq); do tophat -p 8 -g 1 -N 2 --no-discordant  --no-mixed -G /home/wuzefeng/MyResearch/genome.db/Maize/gtf/Zea_mays.AGPv3.31.chr.gtf -o /home/wuzefeng/opt/53maize_rna-seq/2tophat/${m} -I 30000 ~/MyResearch/genome.db/Maize/dna/Maize ${m}_1.fastq ${m}_2.fastq ;done
    
## Cufflinks calculate gene expression 

    for m in $(ls ../2tophat);do cufflinks -o $m -p 6 -G /home/wuzefeng/MyResearch/genome.db/Maize/gtf/Zea_mays.AGPv3.31.chr.gtf ../2tophat/$m/accepted_hits.bam;done

