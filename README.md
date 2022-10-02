The repo is a collection of simple code snippets that I often forget..

## General python
  - [ipdb cheatsheet](https://wangchuan.github.io/coding/2017/07/12/ipdb-cheat-sheet.html)
  - [Conda basic commands](https://gist.github.com/hurrialice/f3118ce4d0472f7ba8d6cbe20e50c81a); [conda config with basic R4 + bioconductor](https://gist.github.com/hurrialice/7c6ebb6514ba8c39095cc28f2374ec7b)
  - Enable `%%R` magic by `%load_ext rpy2.ipython`; more on [rmagic](https://ipython.org/ipython-doc/2/config/extensions/rmagic.html)
    - [Useful Bioconductor utilities](https://gist.github.com/hurrialice/9de64bbccfdc96a1ed761f7fee4b40b7) :sleepy:
  - python requests library
    - [advanced use](https://docs.python-requests.org/en/latest/user/advanced/)
    - [pagination example](https://gist.github.com/hurrialice/0366d0d9bf573ec22e97bba3fb39011e) with generator
    - 
### Pandas
  - [Assign a column based on multiple conditions](https://gist.github.com/hurrialice/02f0460b88bc7a34b9b73717139c2a74)
  - TODO: taking care of indices during merge / concat operations
  - `x in pd.Series` always returns `False`
  - `pd.Series([True, False, np.nan]).astype(bool)` will turn NA to True
  - MultiIndex handling
    - `adat.index = pd.MultiIndex.from_frame(<pd.dataframe>)`
    - `adat.sort_index(level=['relationship','Subject ID']).sort_index(level = ["Dilution"], axis=1)` # reorder a multindex dataframe
    - `adat2.reindex_like(adat1)` # reorder adat2 to adat1-matching indices with certain filling logic

### Numpy
  - Slicing
    - [multiple slicing solutions](https://stackoverflow.com/questions/43413582/selecting-multiple-slices-from-a-numpy-array-at-once)
    - [More examples on choosing strides and shape](https://towardsdatascience.com/advanced-numpy-master-stride-tricks-with-25-illustrated-exercises-923a9393ab20)
    - [Concating multiple slices with `np.r_`](https://stackoverflow.com/questions/44375899/select-specific-columns-in-numpy-array-using-colon-notation)
  - [Broadcasting](https://numpy.org/doc/stable/user/basics.broadcasting.html)

### Matplotlib
  - [GaddyGram from aggregated MAF](https://gist.github.com/hurrialice/a01d8c0a758856e2ebac22363db703a1)
  - [Upset plot comparing calls from different sources](https://gist.github.com/hurrialice/43812e5df996c2abce3dd2578cb13d58)
  - Add y=x to existing figure without changing axis
    ```
    x = np.linspace(*ax.get_xlim())
    ax.plot(x, x)
    ```
  - [Q-Q plot](https://gist.github.com/hurrialice/939b1a427e69edb284c26288ae34b1f1)
  - [centering diverging cmap](http://chris35wills.github.io/matplotlib_diverging_colorbar/)
  - [adding hatches to a heatmap/clustermap](https://stackoverflow.com/questions/55285013/adding-hatches-to-seaborn-heatmap-plot); note the use of `np.ma` module!
  - [discrete color codes](https://www.python-graph-gallery.com/197-available-color-palettes-with-matplotlib). I am still trying to find an elegant way to annotate colors but [this question might be relevant](https://stackoverflow.com/questions/14777066/matplotlib-discrete-colorbar). If to draw a scatterplot with categorized colors from a column, just use `col.map(color_dict)` in which `color_dict` is a preset mapping of colors, usually taking from [company's visual guide](https://illumina-playbook.webflow.io/visual-system#color). 
    ```
    ilmn = ['#E91207','#ED8B00', '#FFB81C', '#DE1B76', '#7D55C7', '#0077C8']
    sns.palplot(sns.color_palette(ilmn)) # show colors
    plt.scatter(...., c=[sns.color_palette(ilmn)[x] for x in df.colname.map(CMAPDICT)]))
    ```
  - [custom legend](https://stackoverflow.com/questions/44098362/using-mpatches-patch-for-a-custom-legend)
  - [Extendable quick QC plot on tabular metrics file](https://gist.github.com/hurrialice/9771dd82bd334363b8746fdcb91c88cd)
  - [twin axis with seaborn gridplot](https://stackoverflow.com/questions/65785304/using-ax-twinx-with-sns-facetgrid-and-sns-lineplot)
  - TODO: pairwise alignment dotplot plot for given read name

## General R (to be filled)
  - [Vannila R example for several statistical tests](https://gist.github.com/hurrialice/75ec1c321132ae052bce76a89ab9acb0), proficient use of `lapply` families, `split`, `unnest`, `Map`.
  - R stats functions, different glm designs
  - Tidyverse family of libraries (`dplyr`, `purrr`, ...)
  - `SummerizedExpriments` for efficient organization of assays, other reliable `Bioconductor` packages
  - `ggplot2` family of bioinformatics related plotting

## NGS manipulation

  - [Cytoband file parser](https://gist.github.com/julianhess/b2bdb38733f3c61885c2564a17d53c12) *Credit to Julian Hess*
  - Simulate reads from haplotig with [NEAT](https://github.com/ncsa/NEAT) from give error model
  
### Variants (MAF/VCF)
  - [Several useful commands with awk/sed/grep](https://gist.github.com/hurrialice/b09d05c7d67cd1f4301ca6c32a223ab5)
  - [Reheader VCF with another reference fasta index (e.g. different contig names)](http://samtools.github.io/bcftools/bcftools.html#reheader) by `bcftools reheader -f XXX.fasta.fai old.vcf -o new.vcf`
  - [Appending header lines to VCF](http://samtools.github.io/bcftools/bcftools.html#annotate) by `bcftools annotate -h <hdr> -a <annot> -s <sample>`
  - Change sample name of VCF: `bcftools reheader -samples <samples.list>`, as in the order of original VCF
  - [bcftools cheatsheet](https://gist.github.com/elowy01/93922762e131d7abd3c7e8e166a74a0b)
  - convert a site/sample level information from a VCF to a table (note, it is not MAF! so be careful abut the position changes) with [GATK VariantsToTable](https://gist.github.com/hurrialice/333b3936906cb06fef3609331034ec4f), or [bcftools query](https://samtools.github.io/bcftools/howtos/query.html) with `-f`. Both ways work to tabulate info/format fields and can be piped to `awk`
  - Matching indel positions between VCF vs MAF
    ```
    # insertion
    ms = vs
    me = ms + 1
    # mask the first base for (vref, valt)
    mref,malt = (-,G)

    # deletion
    ms = vs + 1
    # mask the first base for (vref, valt)
    malt = '-'
    me = ms + len(mref) -1
    ```
  - [bcftools expression syntax](https://samtools.github.io/bcftools/bcftools.html#expressions)
  - Working with VCF info flags (binary tag):
    - with `bcftools annotate`, explicitly include an additional column for 1/0/.; where as `.` denotes keeping existing flag
    - with `bcftools annotate`, use `-m <TAG>` to denote the presence of a TAG
    - Correct header for a binary flag looks like: 
      ```
      echo -e "##INFO=<ID=pathogenic_intron,Number=0,Type=Flag,Description="Intronic variants that is marked P/LP from clinvar"" > pathogenic_intron.hdr
      ```
    - Filtering by `bcftools filter -i 'pathogenic_intron=1' ` for presence of that tag
  - `bcftools merge` for non-overlapping sample (be careful with [FILTER info loss](https://github.com/samtools/bcftools/issues/920)); `bcftools concat` for identical order of sample with different regions / variant types (different FORMAT headers will be properly handled too) , however output needs to be sorted
  - [GVCF](https://gatk.broadinstitute.org/hc/en-us/articles/360035531812-GVCF-Genomic-Variant-Call-Format): The key difference between a regular VCF and a GVCF is that the GVCF has records for all sites, whether there is a variant call there or not. Related GATK [Joint calling](https://gatk.broadinstitute.org/hc/en-us/articles/360035890431-The-logic-of-joint-calling-for-germline-short-variants) framework
  - Compression (TODO: this part needs more work)
    - Compress and index a vcf
      ```
      bgzip file.vcf # or bcftools view file.vcf -Oz -o file.vcf.gz
      tabix file.vcf.gz # or bcftools index file.vcf.gz
      ```
    - `bcftools convert` vcf/bcf/gvcf
    - `-O`: Output compressed BCF (b), uncompressed BCF (u), compressed VCF (z), uncompressed VCF (v). Use the -Ou option when piping between bcftools; subcommands to speed up performance by removing unnecessary compression/decompression and VCF<->BCF conversion. [Size comparison](https://github.com/davetang/learning_vcf_file#comparing-output-types)
  - consensus sequence from VCF, usually better to have input vcf normalized (indel left aligned with `bcftools norm --fasta-ref`)
    ```
    samtools faidx ref.fa 8:11870-11890 | bcftools consensus in.vcf.gz > out.fa
    ```
  - filter hom-ref from a VCF, gives you any site where at least one sample has an alt.
    ```
    bcftools view -i 'GT[*]="alt"' input.vcf
    ```
  - `bcftools +mendelian` plugin option: `-l +` will remove any inconsistent records, `-d` will only mask `GT` field to `./.`
  - make a `bedtools`-compatible genome file by `awk -v OFS='\t' {'print $1,$2'} ${reffa}.fai > ${reffa}.genome`
  - bcftools region option:
  ```
    -r, --regions <region>              restrict to comma-separated list of regions
    -R, --regions-file <file>           restrict to regions listed in a file
    -t, --targets [^]<region>           similar to -r but streams rather than index-jumps. Exclude regions with "^" prefix
    -T, --targets-file [^]<file>        similar to -R but streams rather than index-jumps. Exclude regions with "^" prefix
  ```
  > Yet another difference between the two is that -r checks both start and end positions of indels, whereas -t checks start positions only.
  - [MiniBAM](https://github.com/walaj/VariantBam)

### Alignments (BAM/CRAM)
  - [Explaining read flags](https://broadinstitute.github.io/picard/explain-flags.html)
  - Filtering by read tag with `samtools view -d TAG:VAL` or `samtools view -d TAG` for binary flag
  - `export GCS_OAUTH_TOKEN=$(gcloud auth application-default print-access-token)` so that samtools will stream `gs://`
  - Note that `-r` in `samtools view` denotes read group instead of region. Be aware...
  - [samtools mpileup]((https://cloud.tencent.com/developer/article/1441634)) with [regrex patterns in python](https://gist.github.com/hurrialice/3cf2c6888cecb3125cc4298eadf6c50a):
  - [parsing outputs from samtools view](https://www.biostars.org/p/15953/), however inflating BAM should generally be avoided
    - <img width="667" alt="image" src="https://user-images.githubusercontent.com/30106174/159592863-b68a58e1-3f55-47d5-b01d-d453858a9236.png"> 
    - Max MAPQ with `samtools view ${bam} chr1:20000000-21000000 | awk  'BEGIN{a=   0}{if ($5>0+a) a=$5} END{print a}'`
    - Mean MAPQ with `samtools view aln.bam chr22:20000000-21000000 | awk '{sum+=$5} END { print "Mean MAPQ =",sum/NR}'`
    - [bioawk](https://github.com/lh3/bioawk) functions similar to `bcftools query`
  - TODO: curl only a subset of a (super-large) BAM by region with BAI

## IGV
  - [Get signed URL from GDC UUID](https://gist.github.com/hurrialice/fe3e1f02eaf1038968d6ed4d278a08bd)
  - [visualizing Pacbio long reads in IGV](https://www.youtube.com/watch?v=nLpmeD57ToA)
    - Note: [IGV handles long reads hardclip](https://github.com/igvteam/igv/issues/731) differently from short reads (appear to be a truncated magneta arrow) and it can be misleading! It makes more sense to make dotplot aligning reads to ref.
  - [write IGV xml from a list of bam paths](https://gist.github.com/hurrialice/7527efbe7661a924bf8f70766c17e448) with `bash /usr/writeIGV.sh ~{reference_version} ~{sep=" " input_files} ~{sep=" " input_names_prefix}  > "~{file_name}.xml"`; [python equivalent](https://gist.github.com/hurrialice/ef2838cb82628801717eed40836e3ed5)
  - Starting from IGV 2.13 it will stream s3 buckets from `[default]` profile
  - Starting from IGV 2.14 it displays 5mC with better color code [TODO; add explanation here], quick visuals can be done with [methylation-artist](https://github.com/adamewing/methylartist)
  - TODO: linked-reads display 

## Misc
  - [Kill Vscode remote on host](https://stackoverflow.com/questions/56892931/how-to-kill-vscode-remote-services-on-ubuntu-host) to emulate log out and log back in, otherwise it still runs as a background process
  - [Homebrewing without sudo](https://www.scivision.dev/macos-homebrew-non-sudo/)
  - [Missing link to libcrypto openssl on OSX](https://gist.github.com/aklap/e885721ef15c8668ed0a1dd64d2ea1a7)
  - Length for chr1 is `249,250,621` in hg19; and `248,956,422` in hg38 
