
*all information here is public*


- Illumina Kit available:
<img width="967" alt="image" src="https://user-images.githubusercontent.com/30106174/158073774-78a75dc6-6016-459b-99a5-56066d0612a8.png">

- Profiling vs analysis
  - profiling focuses on counts against a reference, usually single end lib will suffice
  - analysis aim to find sequence (e.g. novel fusion gene structure discovery), usually needs 2X reads than profiling (5-25M for polyA on human-sized transcriptome). 
- PE vs SE: read 1 better cov at 3'; read 2 better cov at 5', PE will decrease %dup
- RNA input 
  - RIN (for mammalian species only; >8 means good). Poly-A enrichment methods needs RIN>8 otherwise would have 3' bias, Ribo-depletion methods are more robust to low RIN, nbut needs 2X reads to achieve same coverage
  - Bioanalyzer/Fragment trace (look for size and unexpected peaks)
    - all Illumina RNA kits use chemical fragmentation (divalent cations + heat)
    - perfect prep BA trace
    - <img width="960" alt="Screen Shot 2022-03-13 at 1 10 42 PM" src="https://user-images.githubusercontent.com/30106174/158077233-67530a59-f8dc-423e-891b-fb8e0b215ee5.png">
    - perfect prep FA trace
    - <img width="967" alt="image" src="https://user-images.githubusercontent.com/30106174/158077391-9c5e7f30-cf58-4268-b362-fa27ba9fe961.png">
    - Peak max will be much larger than expected size, for PCR-free ligation (which results in forked adaptors given no PCR linearization)
    - perfect prep RNA FA trace (peak will be very broad given no insert size selection), newer tech (Illumina RNA XXX) will have peak ~300-400 for polyA, 375-475 for Ribo0+
    - <img width="561" alt="image" src="https://user-images.githubusercontent.com/30106174/158077555-ef3a0029-c4d3-46b2-8317-7a36ccce59eb.png">
    - Common problems:
      - Overloaded chip <img width="985" alt="image" src="https://user-images.githubusercontent.com/30106174/158078825-d107fa38-eacc-4b33-9e22-e3c83cb1dec8.png">
      - No library peak ![image](https://user-images.githubusercontent.com/30106174/158079193-d60a78c4-3670-4834-ae41-3303881d2c93.png)
      - large peak: insufficient bead clean up <img width="945" alt="image" src="https://user-images.githubusercontent.com/30106174/158079255-e70e50e0-d35b-4c0f-b4d7-1a26f7e76786.png">
      - large peak: PCR artifact <img width="775" alt="image" src="https://user-images.githubusercontent.com/30106174/158079280-3d606352-368f-4180-a5ca-faba9040767d.png">
      - Adaptor dimer ~120bp, should be removed before putting on flowcell because shorter fragments cluster better so take up more resources, esp using patterned flowcell <img width="1120" alt="image" src="https://user-images.githubusercontent.com/30106174/158079391-953f2f5c-e150-43b8-b256-781b9938e21b.png">



    
  - Quantify input: fluorometric method (e.g. Ribo-green) preferred, DNA might impact esp in FFPE, qPCR is most accurate
    - <img width="676" alt="image" src="https://user-images.githubusercontent.com/30106174/158077881-fc474d4c-d945-418c-931d-78796482cf16.png">
    - Traces vs quant for different RNA kits
    - <img width="1123" alt="image" src="https://user-images.githubusercontent.com/30106174/158079004-58166476-c8d7-4df0-a094-341f7bd80167.png">

- Stranded vs non-directional workflows
  - Truseq RNA v2
  - <img width="691" alt="image" src="https://user-images.githubusercontent.com/30106174/158076402-0d1ed870-6229-41fd-8335-068808c44ef5.png">
  - Truseq Stranded mRNA (dUTP in 2nd strand syn, pol will not pass U so only top strand is amplified)
  - <img width="691" alt="image" src="https://user-images.githubusercontent.com/30106174/158076437-3a56c308-efab-4e14-a5a6-3b9f5dc10b78.png">
  - RNA index anchors, T-overhang results in low base diversity at first cycles
  - Truseq Stranded total RNA 
  - <img width="901" alt="image" src="https://user-images.githubusercontent.com/30106174/158076746-6c45e8ea-e19a-48f8-b542-a4d5954753c4.png">
  - <img width="1250" alt="image" src="https://user-images.githubusercontent.com/30106174/158076840-c6c3c500-63dd-435b-9feb-1dda2bc5bc58.png">
  - [Great notes on strandness of RNA-seq](https://rnabio.org/module-09-appendix/0009/12/01/StrandSettings/)

