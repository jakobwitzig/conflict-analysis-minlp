## Online Supplement of:

# *Conflict Analysis for MINLP*

##### Timo Berthold<sup>1</sup> and Jakob Witzig<sup>2</sup>

###### <sup>1</sup> FICO Germany GmbH, Takustr. 7, 14195 Berlin, <timoberthold@fico.com>

###### <sup>2</sup> Zuse Institute Berlin, Takustr. 7, 14195 Berlin, <witzig@zib.de>
___

This online supplement provides tables in CSV format with detailed results of the computational experiments conducted for the paper "Conflict Analysis for MINLP".
A preprint is available as technical repprt published by Zuse Institute Berlin, 2020.

In our computational study, we address three questions:
* When solving general MINLPs with an LP-based branch-and-bound, what is the impact of using a combined approach of applying dual proof analysis in addition to conflict graph analysis?
* Given that local linearization cuts often prohibit finding globally valid proof constraints: What is the impact of our suggested strategy to generate local dual proofs when solving nonconvex MINLPs with an LP-based branch-and-bound?
* When solving general MINLPs with an NLP-based branch-and-bound approach, what is the impact of our newly proposed nonlinear dual proofs?

As test set we used MINLPLib (http://www.minlplib.org/, git hash a71254dc).

To address performance variability, all experiments were run with three different constraint permutations. All data provided in this repository represents data where all settings considered in a respective experiment finished without error (e.g., numerical violations). Thus, for some instance less than three observations are available.

The repository is organized as follows. CSV data files of all experiments conducted within an LP-based branch-and-bound or NLP-based branch-and-bound are stored in `lp-based` or `nlp-based`.

#### Experiments

The following experiments where conducted:
###### LP-based branch-and-bound:
* SCIP without LP-based infeasibility analysis (baseline) vs. LP-based conflict graph analysis vs. combined approach of LP-based conflict graph and dual proof analysis (`lp-based/MINLP_discrete_lpinf_all.csv`)
* SCIP without LP-based infeasibility analysis (baseline) vs. combined approach of LP-based conflict graph and dual proof analysis w/ and w/o local dual proofs (`lp-based/MINLP_discrete_local_dual_proofs_all.csv`)

###### NLP-based branch-and-bound:
* SCIP w/o conflict analysis at all vs. enabled conflict graph analysis due to propagation vs. enabled NLP-based dual proof analysis (`nlp-based/MINLP_discrete_local_dual_proofs_all.csv`)
* Same as above but w/ and w/o adding solutions and analyzing infeasibility during coefficient diving and conflict diving, respectively (`conflictdiving/MMMc_default_coef_conf__noconfs_nosols_clean.csv`)

#### CSV data details

All instance features, e.g., solving time or explored tree nodes, are always given with respect to a setting.

###### LP-based branch-and-bound

* `nolpinf` : SCIP without analyzing infeasibilties derived from the LP relaxation
* `confgraph` : SCIP applying conflict graph analysis solely when analyzing infeasibilities derived from the LP relaxation
* `combined` : SCIP using both conflict graph and dual proof analysis when analyzing infeasibilities derived from the LP relaxation
* `combined-local` : Same as `combined` but using locally valid dual proofs in addition

###### NLP-based branch-and-bound

* `noconlfict` : SCIP without conflict analysis
* `nonlpinf` : SCIP without analyzing infeasibilties derived from the NLP relaxation but applying conflict graph analysis to infeasibilities derived from constraint propagation
* `nlpinf` : SCIP using both conflict graph analysis to analyze infeasibilities derived from constraint propagation and nonlinear dual proof analysis to analyze infeasible NLP relaxations

###### Used instance features

* `ProblemName` : The name of the instance
* `T_s` : Absolute solving time in seconds
* `TQ+1_s` : Relative solving time with a shift of 1
* `N_s` : Absolute number of explored tree nodes
* `NQ+100_s` : Relative number of explored tree nodes with a shift of 100
* `DI` : Absolute dual integral
* `DIQ` : Relative dual integral

#### How to Cite?

```
@techreport{BertholdWitzig2020,
  author      = {Timo Berthold and Jakob Witzig},
  title       = {Conflict Analysis for MINLP},
  institution = {ZIB},
  address     = {Takustr.~7, 14195 Berlin},
  number      = {20-20},
  language    = {eng},
  year        = {2020}
}
```