The repo is a collection of simple code snippets that I often forget..

## General Pandas
- [Assign a column based on multiple conditions](https://gist.github.com/hurrialice/02f0460b88bc7a34b9b73717139c2a74)
- `x in pd.Series` always returns `False`
- `pd.Series([True, False, np.nan]).astype(bool)` will turn NA to True

## Numpy
- Slicing
  - [multiple slicing solutions](https://stackoverflow.com/questions/43413582/selecting-multiple-slices-from-a-numpy-array-at-once)
  - [More examples on choosing strides and shape](https://towardsdatascience.com/advanced-numpy-master-stride-tricks-with-25-illustrated-exercises-923a9393ab20)
  - [Concating multiple slices with `np.r_`](https://stackoverflow.com/questions/44375899/select-specific-columns-in-numpy-array-using-colon-notation)
  
- Broadcasting

## Figures
- [GaddyGram from aggregated MAF](https://gist.github.com/hurrialice/a01d8c0a758856e2ebac22363db703a1)
- [Upset plot comparing calls from different sources](https://gist.github.com/hurrialice/43812e5df996c2abce3dd2578cb13d58)
- Add y=x to existing figure without changing axis
  ```
  x = np.linspace(*ax.get_xlim())
  ax.plot(x, x)
  ```
- [Q-Q plot](https://gist.github.com/hurrialice/939b1a427e69edb284c26288ae34b1f1)
- Trace plot
- [centering diverging cmap](http://chris35wills.github.io/matplotlib_diverging_colorbar/)
- [adding hatches to a heatmap/clustermap](https://stackoverflow.com/questions/55285013/adding-hatches-to-seaborn-heatmap-plot); note the use of `np.ma` module!
- [discrete color codes](https://www.python-graph-gallery.com/197-available-color-palettes-with-matplotlib). I am still trying to find an elegant way to annotate colors but [this question might be relevant](https://stackoverflow.com/questions/14777066/matplotlib-discrete-colorbar) 

## Interacting with MAF/VCF
- [Several useful commands with awk/sed/grep](https://gist.github.com/hurrialice/b09d05c7d67cd1f4301ca6c32a223ab5)
- [Reheader VCF with another reference fasta index (e.g. different contig names)](http://samtools.github.io/bcftools/bcftools.html#reheader) by `bcftools reheader -f XXX.fasta.fai old.vcf -o new.vcf`
- [Appending header lines to VCF](http://samtools.github.io/bcftools/bcftools.html#annotate) by `bcftools annotate -h <hdr> -a <annot> -s <sample>`
- Chane sample name of VCF: `bcftools reheader -samples <samples.list>`, as in the order of original VCF
- [bcftools cheatsheet](https://gist.github.com/elowy01/93922762e131d7abd3c7e8e166a74a0b)
- convert a site/sample level information from a VCF to a table (note, it is not MAF! so be careful abut the position changes) with [GATK VariantsToTable](https://gist.github.com/hurrialice/333b3936906cb06fef3609331034ec4f)

## Interacting with BAM/CRAM
- [samtools mpileup](https://cloud.tencent.com/developer/article/1441634)
- `export GCS_OAUTH_TOKEN=$(gcloud auth application-default print-access-token)`
- `samtools mpileup` [regrex patterns in python](https://gist.github.com/hurrialice/3cf2c6888cecb3125cc4298eadf6c50a):
  ```
    'insertion': "\+[0-9]+[ACGTNacgtn]+", # no base qual!!
    'deletion': "-[0-9]+[ACGTNacgtn]+", # no base qual!!
    'start_of_read' : '\^',# correspondes to mapq of a read
    'end_of_read': '\$', # no corresponding basequal
    'refbase': '[.,]',
    'altbase': '[^0-9][ACGTNacgtn]'
  ```


## IGV
- [Get signed URL from GDC UUID](https://gist.github.com/hurrialice/fe3e1f02eaf1038968d6ed4d278a08bd)

## Misc
- [Cytoband file parser](https://gist.github.com/julianhess/b2bdb38733f3c61885c2564a17d53c12) *Credit to Julian Hess*
- [Dummy Bed file generation from fasta.fai (with contig length)](https://gist.github.com/hurrialice/6f5c2dad514840c71081abced4890696)
- [Kill Vscode remote on host](https://stackoverflow.com/questions/56892931/how-to-kill-vscode-remote-services-on-ubuntu-host) to emulate log out and log back in, otherwise it still runs as a background process
- [ipdb cheatsheet](https://wangchuan.github.io/coding/2017/07/12/ipdb-cheat-sheet.html)
- python requests library
  - [advanced use]('https://docs.python-requests.org/en/latest/user/advanced/')
  - [pagination example](https://gist.github.com/hurrialice/0366d0d9bf573ec22e97bba3fb39011e) with generator
- [Homebrewing without sudo](https://www.scivision.dev/macos-homebrew-non-sudo/)
- [Conda basic commands](https://gist.github.com/hurrialice/f3118ce4d0472f7ba8d6cbe20e50c81a); [conda config with basic R4 + bioconductor](https://gist.github.com/hurrialice/7c6ebb6514ba8c39095cc28f2374ec7b)
- Genomics Common Sense
  - Exome is 1-2% of genome
  - Length for chr1 is `249,250,621` in hg19; and `248,956,422` in hg38 
