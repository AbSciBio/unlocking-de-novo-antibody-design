# Unlocking _de novo_ antibody design with generative artificial intelligence
Sequences of antibodies and binding, functionality, developability, and cross-reactivity data from the study [Unlocking _de novo_ antibody design with generative artificial intelligence](https://www.biorxiv.org/content/10.1101/2023.01.08.523187v4). 

We present SPR data for _zero-shot_ HCDR3 designs (`zero-shot-designs.csv`); SPR data for binders and non-binders (`spr-controls.csv`); and functionality, developability, and cross-reactivity data for candidate mAbs (`functionality-developability-cross_reactivity-data.csv`).

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
Data in `spr-controls.csv` are organized with the following columns:
* `HCDR1`: Heavy chain CDR1 amino acid sequence
* `HCDR2`: Heavy chain CDR2 amino acid sequence
* `HCDR3`: Heavy chain CDR3 amino acid sequence
* `KD (nM)`: Binding affinity (dissociation constant in nanomolar units) - Only present for binders
* `Binder`: Boolean indicating if variant is a binder (True) or non-binder (False)
-----------------------------------------------------------------------------------------------------
Data in `functionality-developability-cross_reactivity-data.csv` are organized with the following columns:
* `Candidate`: Represents candidate number or trastuzumab (positive control).
* `HCDR3`: Heavy chain CDR3 amino acid sequence
* `KD (nM)`: Binding affinity (dissociation constant in nanomolar units) - Original binding affinity measured against human HER2, matches `zero-shot-binders.csv`
* `Length`: Length of HCDR3 sequence
* `HCDR3 Edit Distance to Trastuzumab`: Number of mutations from designed HCDR3 to trastuzumab's HCDR3
* `Fab KD (nM) (hHER2)`: Binding affinity to human HER2 in Fab format (dissociation constant in nanomolar units)
* `Fab KD SD`: Standard deviation of `Fab KD (nM) (hHER2)` measurement across replicates
* `mAb KD (nM) (hHER2)`: Binding affinity to human HER2 in mAb format (dissociation constant in nanomolar units)
* `mAb KD SD`: Standard deviation of `mAb KD (nM) (hHER2)` measurement across replicates
* `cELISA EC50 (pM)`: Cell-surface antigen binding EC50 (in picomolar units)
* `cELISA EC50 SD`: Standard deviation of `cELISA EC50 (pM)` measurement across replicates
* `ADCC EC50 (pM)`: Antibody-dependent cell cytotoxicity (ADCC) EC50 (in picomolar units)
* `ADCC EC50 SD`: Standard deviation of `ADCC EC50 (pM)` measurement across replicates
* `mAb Binding - Human HER2`: Binding affinity (nM) and standard deviation to human HER2 in mAb format; reported as mean ± SD, NB = no binding
* `mAb Binding - Cynomolgus HER2`: Binding affinity (nM) and standard deviation to cynomolgus HER2 in mAb format; reported as mean ± SD, NB = no binding
* `mAb Binding - Mouse HER2`: Binding affinity (nM) and standard deviation to mouse HER2 in mAb format; reported as mean ± SD, NB = no binding
* `mAb Binding - Canine HER2`: Binding affinity (nM) and standard deviation to canine HER2 in mAb format; reported as mean ± SD, NB = no binding
* `mAb Binding - Human HER1`: Binding affinity (nM) and standard deviation to human HER1 in mAb format; reported as mean ± SD, NB = no binding
* `mAb Binding - Human HER3`: Binding affinity (nM) and standard deviation to human HER3 in mAb format; reported as mean ± SD, NB = no binding
* `mAb Binding - Human HER4`: Binding affinity (nM) and standard deviation to human HER4 in mAb format; reported as mean ± SD, NB = no binding
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
  title = {Unlocking de novo antibody design with generative artificial intelligence},
  url = {http://dx.doi.org/10.1101/2023.01.08.523187},
  DOI = {10.1101/2023.01.08.523187},
  publisher = {Cold Spring Harbor Laboratory},
  author = {Shanehsazzadeh,  Amir and Bachas,  Sharrol and McPartlon,  Matt and Kasun,  George and Sutton,  John M. and Steiger,  Andrea K. and Shuai,  Richard and Kohnert,  Christa and Rakocevic,  Goran and Gutierrez,  Jahir M. and Chung,  Chelsea and Luton,  Breanna K. and Diaz,  Nicolas and Levine,  Simon and Alverio,  Julian and Knight,  Bailey and Radach,  Macey and Morehead,  Alex and Bateman,  Katherine and Spencer,  David A. and McDargh,  Zachary and Cejovic,  Jovan and Kopec-Belliveau,  Gaelin and Haile,  Robel and Yassine,  Edriss and McCloskey,  Cailen and Natividad,  Monica and Chapman,  Dalton and Bennett,  Joshua and Hossain,  Jubair and Ventura,  Abigail B. and Canales,  Gustavo M. and Gowda,  Muttappa and Jackson,  Kerianne A. and Stanton,  Jennifer T. and Ura,  Marcin and Stojanovic,  Luka and Yapici,  Engin and Moran,  Katherine and Caguiat,  Rodante and Brown,  Amber and Abdulhaqq,  Shaheed and Guo,  Zheyuan and Klug,  Lillian R. and Gander,  Miles and Meier,  Joshua},
  year = {2023},
  month = jan 
}
```
## License
The data in this repository are licensed under the Clear BSD License found in the `LICENSE` file in the root directory of this source tree.
