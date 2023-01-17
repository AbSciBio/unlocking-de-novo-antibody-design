# Unlocking _de novo_ antibody design with generative artificial intelligence
Sequences of binding antibodies and corresponding affinity values identified in the study [Unlocking _de novo_ antibody design with generative artificial intelligence](https://www.biorxiv.org/content/10.1101/2023.01.08.523187v1). 

We present data for _zero-shot_ HCDR3 designs (`zero-shot-designs.csv`) and multi-step multi-HCDR designs (`multi-step-binders.csv`).

-----------------------------------------------------------------------------------------------------
Data in `zero-shot-designs.csv` are organized with the following columns:
* `HCDR3`: Heavy chain CDR3 amino acid sequence
* `KD (M)`: Binding affinity (dissociation constant in molar units)
* `KD (nM)`: Binding affinity (dissociation constant in nanomolar units)
* `-log(KD (M))`: Negative logarithm (base 10) of `KD (M)`
* `HCDR3 Edit Distance to Trastuzumab`: Number of mutations from designed HCDR3 to trastuzumab's HCDR3
* `Minimum HCDR3 Edit Distance to SAbDab`: Minimum number of mutations from designed HCDR3 to the HCDR3s in the [Structural Antibody Database (SAbDab)](https://opig.stats.ox.ac.uk/webapps/newsabdab/sabdab/). Note: SAbDab was retrieved on August 29th, 2022.
* `Minimum HCDR3 Edit Distance to OAS`: Minimum number of mutations from designed HCDR3 to the HCDR3s in the [Observed Antibody Space](http://opig.stats.ox.ac.uk/webapps/oas/). Note: OAS was retrieved on February 1st, 2022.
* `Minimum HCDR123 Edit Distance to OAS`: Computed as follows:
  * For an antibody in OAS take the heavy chain CDR1 (HCDR1), heavy chain (HCDR2), and HCDR3 from said antibody.
  * Compute the number of mutations from trastuzumab's HCDR1 to the OAS HCDR1, from trastuzumab's HCDR2 to the OAS HCDR2, and from the designed HCDR3 to the OAS HCDR3.
  *  Take the sum of the above three values.
  *  Report the minimum across all antibodies in OAS.
-----------------------------------------------------------------------------------------------------
Data in `multi-step-designs.csv` are organized with the following columns:
* `HCDR1`: Heavy chain CDR1 amino acid sequence
* `HCDR2`: Heavy chain CDR2 amino acid sequence
* `HCDR3`: Heavy chain CDR3 amino acid sequence
* `KD (M)`: Binding affinity (dissociation constant in molar units)
* `KD (nM)`: Binding affinity (dissociation constant in nanomolar units)
* `-log(KD (M))`: Negative logarithm (base 10) of `KD (M)`
* `HCDR1 Edit Distance to Trastuzumab`: Number of mutations from designed HCDR1 to trastuzumab's HCDR1
* `HCDR2 Edit Distance to Trastuzumab`: Number of mutations from designed HCDR2 to trastuzumab's HCDR2
* `HCDR3 Edit Distance to Trastuzumab`: Number of mutations from designed HCDR3 to trastuzumab's HCDR3
* `Edit Distance to Trastuzumab`: Number of mutations from designed antibody to trastuzumab (sum of the above 3 columns)
* `Minimum HCDR1 Edit Distance to SAbDab`: Minimum number of mutations from designed HCDR1 to the HCDR3s in SAbDab
* `Minimum HCDR2 Edit Distance to SAbDab`: Minimum number of mutations from designed HCDR2 to the HCDR2s in SAbDab
* `Minimum HCDR3 Edit Distance to SAbDab`: Minimum number of mutations from designed HCDR3 to the HCDR3s in SAbDab
* `Minimum HCDR123 Edit Distance to SAbDab`: Computed as follows:
  * For an antibody in SAbDab take the HCDR1, HCDR2, and HCDR3 from said antibody.
  * Compute the number of mutations from the designed HCDR1 to the OAS HCDR1, from the designed HCDR3 to the OAS HCDR2, and from the designed HCDR3 to the OAS HCDR3.
  *  Take the sum of the above three values.
  *  Report the minimum across all antibodies in SAbDab.
* `Minimum HCDR1 Edit Distance to OAS`: Minimum number of mutations from designed HCDR1 to the HCDR1s in OAS
* `Minimum HCDR2 Edit Distance to OAS`: Minimum number of mutations from designed HCDR2 to the HCDR2s in OAS
* `Minimum HCDR3 Edit Distance to OAS`: Minimum number of mutations from designed HCDR3 to the HCDR3s in OAS
* `Minimum HCDR123 Edit Distance to OAS`: Minimum sum of mutations from designed HCDR1, HCDR2, HCDR3 to the tuples of HCDR1, HCDR2, HCDR3 in OAS (computed analogously to `Minimum HCDR123 Edit Distance to SAbDab` but using OAS in place of SAbDab)
-----------------------------------------------------------------------------------------------------
Details about Trastuzumab-HER2 model system:
* Antibody: [Trastuzumab](https://www.science.org/doi/10.1126/science.1165480)
   *  Heavy Chain Sequence: `EVQLVESGGGLVQPGGSLRLSCAASGFNIKDTYIHWVRQAPGKGLEWVARIYPTNGYTRYADSVKGRFTISADTSKNTAYLQMNSLRAEDTAVYYCSRWGGDGFYAMDYWGQGTLVTVSSASTKGPSVFPLAPSSKSTSGGTAALGCLVKDYFPEPVTVSWNSGALTSGVHTFPAVLQSSGLYSLSSVVTVPSSSLGTQTYICNVNHKPSNTKVDKKVEPKSCDKTH`
   *  Heavy Chain CDRs ([IMGT Annotation](https://www.imgt.org/))
       * HCDR1: `GFNIKDTY`
       * HCDR2: `IYPTNGYT`
       * HCDR3: `SRWGGDGFYAMDY`  
   *  Light Chain Sequence: `DIQMTQSPSSLSASVGDRVTITCRASQDVNTAVAWYQQKPGKAPKLLIYSASFLYSGVPSRFSGSRSGTDFTLTISSLQPEDFATYYCQQHYTTPPTFGQGTKVEIKRTVAAPSVFIFPPSDEQLKSGTASVVCLLNNFYPREAKVQWKVDNALQSGNSQESVTEQDSKDSTYSLSSTLTLSKADYEKHKVYACEVTHQGLSSPVTKSFNRGEC`
* Antigen: [Human Epidermal Growth Factor Receptor 2 (HER2)](https://pubmed.ncbi.nlm.nih.gov/25276427/)
   * Sequence: `TQVCTGTDMKLRLPASPETHLDMLRHLYQGCQVVQGNLELTYLPTNASLSFLQDIQEVQGYVLIAHNQVRQVPLQRLRIVRGTQLFEDNYALAVLDNGDPLNNTTPVTGASPGGLRELQLRSLTEILKGGVLIQRNPQLCYQDTILWKDIFHKNNQLALTLIDTNRSRACHPCSPMCKGSRCWGESSEDCQSLTRTVCAGGCARCKGPLPTDCCHEQCAAGCTGPKHSDCLACLHFNHSGICELHCPALVTYNTDTFESMPNPEGRYTFGASCVTACPYNYLSTDVGSCTLVCPLHNQEVTAEDGTQRCEKCSKPCARVCYGLGMEHLREVRAVTSANIQEFAGCKKIFGSLAFLPESFDGDPASNTAPLQPEQLQVFETLEEITGYLYISAWPDSLPDLSVFQNLQVIRGRILHNGAYSLTLQGLGISWLGLRSLRELGSGLALIHHNTHLCFVHTVPWDQLFRNPHQALLHTANRPEDECVGEGLACHQLCARGHCWGPGPTQCVNCSQFLRGQECVEECRVLQGLPREYVNARHCLPCHPECQPQNGSVTCFGPEADQCVACAHYKDPPFCVARCPSGVKPDLSYMPIWKFPDEEGACQPCPINCTHSCVDLDDKGCPAEQRASPLT` 
* Complex Structure: [PDB:1N8Z](https://www.rcsb.org/structure/1N8Z)
-----------------------------------------------------------------------------------------------------
## Citations
If you find these data or results useful, we ask that you cite our work: 
```
@article{shanehsazzadeh2023denovoab,
  author = {Shanehsazzadeh, Amir and Bachas, Sharrol and Kasun, George and Sutton, John M. and Steiger, Andrea K. and Shuai, Richard and Kohnert, Christa and Morehead, Alex and Brown, Amber and Chung, Chelsea and Luton, Breanna K. and Diaz, Nicolas and McPartlon, Matt and Knight, Bailey and Radach, Macey and Bateman, Katherine and Spencer, David A. and Cejovic, Jovan and Kopec-Belliveau, Gaelin and Haile, Robel and Yassine, Edriss and McCloskey, Cailen and Natividad, Monica and Chapman, Dalton and Stojanovic, Luka and Rakocevic, Goran and Hannum, Gregory and Yapici, Engin and Moran, Katherine and Caguiat, Rodante and Abdulhaqq, Shaheed and Guo, Zheyuan and Klug, Lillian R. and Gander, Miles and Meier, Joshua},
  title = {Unlocking de novo antibody design with generative artificial intelligence},
  year = {2023},
  doi = {10.1101/2023.01.08.523187},
  publisher = {Cold Spring Harbor Laboratory},
  URL = {https://www.biorxiv.org/content/10.1101/2023.01.08.523187v1},
  journal = {bioRxiv}
}
```
## License
The data in this repository are licensed under the Clear BSD License found in the `LICENSE` file in the root directory of this source tree.
