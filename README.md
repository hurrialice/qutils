The repo is a collection of simple code snippets that I often forget..

## General Pandas
- [Assign a column based on multiple conditions](https://gist.github.com/hurrialice/02f0460b88bc7a34b9b73717139c2a74)

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

## Interacting with MAF/VCF
- [Several useful commands with awk/sed/grep](https://gist.github.com/hurrialice/b09d05c7d67cd1f4301ca6c32a223ab5)
- [Reheader VCF with another reference fasta index (e.g. different contig names)](http://samtools.github.io/bcftools/bcftools.html#reheader) by `bcftools reheader -f XXX.fasta.fai old.vcf -o new.vcf`
- [Appending header lines to VCF](http://samtools.github.io/bcftools/bcftools.html#annotate) by `bcftools annotate -h <file>`

## IGV
- [Get signed URL from GDC UUID](https://gist.github.com/hurrialice/fe3e1f02eaf1038968d6ed4d278a08bd)

## Misc
- [Cytoband file parser](https://gist.github.com/julianhess/b2bdb38733f3c61885c2564a17d53c12) *Credit to Julian Hess*
- [Dummy Bed file generation from fasta.fai (with contig length)](https://gist.github.com/hurrialice/6f5c2dad514840c71081abced4890696)
- [Kill Vscode remote on host](https://stackoverflow.com/questions/56892931/how-to-kill-vscode-remote-services-on-ubuntu-host) to emulate log out and log back in, otherwise it still runs as a background process
