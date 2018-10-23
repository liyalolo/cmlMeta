# cmlMeta

20181022,day1
1.pIRS
https://academic.oup.com/bioinformatics/article/28/11/1533/267409
ftp://ftp.genomics.org.cn/pub/pIRS/

date >>sim.log
nohup sh /DATA01/Project/liyanli/pIRS/testReads/test_hg38.pIRS.sh >>sim.log 2>>sim.log
echo "done" >>sim.log
date >> sim.log


pirs=/DATA01/Project/liyanli/pIRS/pIRS_111/pirs
hg38=/DATA01/Project/liyanli/genome/ensembl38/Homo_sapiens.GRCh38.dna.primary_assembly.fa
ecoli=/DATA01/Project/liyanli/genome/ecoli/GCF_000005845.2_ASM584v2_genomic.fna.gz

#$pirs diploid -i $hg38 -s 0.001 -d 0.0001 -o hg38
#$pirs simulate
$pirs simulate -i $ecoli -x 50


pirs=/DATA01/Project/liyanli/pIRS/pIRS_111/pirs
hg38=/DATA01/Project/liyanli/genome/ensembl38/Homo_sapiens.GRCh38.dna.primary_assembly.fa
ecoli=/DATA01/Project/liyanli/genome/ecoli/GCF_000005845.2_ASM584v2_genomic.fna.gz

#$pirs diploid -i $hg38 -s 0.001 -d 0.0001 -o hg38
$pirs simulate -i $hg38 -I hg38.snp.indel.inversion.fa.gz  -x 3 -o hg38_illumina -a 1 -g 1 >simulate_500.o 2>simulate_500.e
$pirs simulate -i $ecoli -x 50 -o ecoli_illumina -a 1 >simulate_500.eco.o 2>simulate_500.eco.e


2.BMTagger
https://bioconda.github.io/index.html#set-up-channels
sh Miniconda2-latest-Linux-x86_64.sh

conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
conda install bwa
conda create -n aligners bwa bowtie hisat star

https://bioconda.github.io/recipes/bmtagger/README.html
conda install bmtagger

3.prinseq
http://prinseq.sourceforge.net/
