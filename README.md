# mPBPK_antibodies_pregnancy
This software is intended for research and exploratory analysis only. It should not be used for clinical decision-making, diagnosis, treatment, or patient management before any prospective clinical validations. The results generated by this tool are for informational purposes only. The developers assume no responsibility or liability for any outcomes resulting from the use of this R Shiny code.


Variables used in the models are defined below. TV indicates typical value


## Parameters:
### Physiological Parameters:
GAinitial         : Gestational age (weeks) indicating simulation start time, defaults to 0 (beginning of pregnancy)  
TVVlymph          : Volume of lymph (L)  
TVL               : Total lymph flow (L/day)  
TVKp              : Fraction of interstitial space available for antibody distribution  
TVRfT             : Vascular reflection coefficient for tight tissues  
TVRfL             : Vascular reflection coefficient for leaky tissues  
TVRflymph         : Lymphatic vascular reflection coefficient  
TVCLm             : Additional maternal clearance term for the antibody if applicable (L/day)
TVkef             : Fetal clearance term for the antibody (1/day)  
TVKm              : Additional maternal non-linear clearance of the antibody, if applicable. Km is concentration at half-maximum elimination rate (nM)
TVVmax            : Additional maternal non-linear clearance of the antibody, if applicable. Vmax is maximum elimination rate (nmoles/day)  


### Physiological Parameters Endosome 1 (Vascular) Parameters:
TVCLup            : Endothelial nonspecific pinocytosis rate (L/day)  
TVCLe             : Lysosome catabolism clearance (L/day)  
TVkrec            : Endosome recycling rate constant (1/day)  
TVVe1             : Endosome volume for nonspecific pinocytosis (L)  
TVkon             : Antibody FcRn association rate constant (nM-1.day-1) in endosomes  
TVkoff            : Antibody-FcRn complex (FcRnA) dissociation rate constant (1/day) in endosomes  

### Antibodies PK Parameters
ka                : Absorption rate constant for the antibody, if applicable (day-1)  
BA                : Subcutaneous (SC) bioavailability for the antibody, if applicable  

## Compartments: All are in amounts, except for FcRn and FcRnA are concentrations:
### Plasma Compartment
depot             : Depot compartment for SC administration  
A_plasma          : Antibody in plasma  
m_auc             : Maternal AUC  
  
### Tight Tissue Compartment
A_Tight           : Antibody in tight tissue  

### Leaky Tissue Compartment
A_Leaky           : Antibody in leaky tissue  

### Lymph Compartment
A_lymph           : Antibody in lymph  
  
### Endosome 1 Compartment
A_e1              : Antibody in endosome 1  
FcRn_e1           : FcRn endosome 1  
FcRnA_e1          : FcRn-Antibody endosome 1  

### Placenta Blood
A_placenta_blood  : Antibody in the vascular compartment of the placenta  

### Endosome 2 Compartment - synchiotrophoblast
A_e2              : Antibody in endosome 2  
FcRn_e2           : FcRn in endosome 2  
FcRnA_e2          : FcRn-Antibody in endosome 2  

### Endosome 3 Compartment - fetal endothelial cells
A_e3              : Antibody in endosome 3  
FcRn_e3           : FcRn in endosome 3  
FcRnA_e3          : FcRn-Antibody in endosome 3  

### Fetal Blood Compartment
A_plasma_fetal    : Antibody in Fetal Blood  
f_auc             : Fetal AUC  


## Initial conditions and derived variables:
FcRn_e1_0         : Concentration of FcRn in endasome 1 (nM) (initial condition)  
GA                : Gestational age (weeks).  
M2                : Total FcRn concentration in endosome 2 (nM). FcRn expression equation as a variable to be included in the differential equations  
M3                : Total FcRn concentration in endosome 3 (nM). FcRn expression equation as a variable to be included in the differential equations  

ETA               : Interindividual variability term, numbered for the respective parameter.  
VisfT             : Volume of interstitial fluid/intracellular water in the tight tissue (L)  
VisfL             : Volume of interstitial fluid/intracellular water in the leaky tissue (L)  
LT                : Lymph flow in the tight tissues (L/day)  
LL                : Lymph flow in the leaky tissues (L/day)  

Vplasma           : Volume of plasma (L)  
Visf              : Volume of interstitial fluid/Intracellular Water (L)  
Vplacenta         : Volume of placenta (L)  
Qplacenta         : Blood flow to the placenta (L/day)  
Vplacenta_blood   : Volume of placenta blood (L)  
Vplasma_fetal     : Volume of the fetus blood (L)  
CLupp             : Endothelial nonspecific pinocytosis rate (L/day) in placenta  
CLep              : Lysosome catabolism clearance (L/day) in placental endosome  
Ve2               : Endosome volume for nonspecific pinocytosis (L) for placental endosome  
Ve3               : Endosome volume for nonspecific pinocytosis (L) for fetal endosome  

## Derived variables after simulation:
AB_Plasma         : Antibody concentration in maternal plasma (nM)  
AB_CB             : Antibody concentration in fetal plasma (nM)  
f_m               : Fetal to maternal ratio  
FcRn_e1_total     : Total FcRn concentration in endosome 1 (nM)  
FcRn_e2_total     : Total FcRn concentration in endosome 2 (nM)  
FcRn_e3_total     : Total FcRn concentration in endosome 3 (nM)  
tad               : Time since the last dose (days)  
time              : Simulation time (days)  

## Additional derived variables in the shiny code and the exported dataset:
end_value         : Total simulation time (days)  
mw_value          : Molecular weight of the antibodu (daltons)  
ii                : Dosing interval (days)  
addl              : Additional doses  
cmt               : Compartment  
delta             : Simulation intervals (days, ex. every 1 day or 0.1 day)  
Delivery          : Delivery week (weeks)  
disease           : Disease code used for ustekinumab PK parameters. 0 = Ulcerative colitis, 1=Crohn's Disease.  
pregnancy         : Pregnancy total time (days)  
pregnancy_week    : Pregnancy total time (weeks)  
irep              : Simulation replicate  
conc_m            : Antibody concentration in maternal plasma (μg/mL)  
conc_f            : Antibody concentration in fetal plasma (μg/mL)  
week              : Simulation time (weeks)  
tad_week          : Time since the last dose (weeks)  
