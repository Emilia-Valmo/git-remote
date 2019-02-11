# Glossary terms

## Proteins

Proteins are the main objects in the database, and each protein possesses the following attributes.

### Name <a id="proteins-name"></a>

The name of the fluorescent protein.  No two proteins in the database can have the same name

### Slug

An abbreviated, URL-friendly version of the name \(must be unique in the database\).  All lowercase, with no spaces or periods  For instance:

* mRFP1.2  →  mrfp12
* PA-CFP2  →  pa-cfp2

Slugs are automatically generated based on the name, and are visible in the URL on any  protein page, for instance, mNeonGreen:  [https://www.fpbase.org/protein/mneongreen/](https://www.fpbase.org/protein/mneongreen/)

### Sequence

Amino acid sequence.  No two proteins in the database can have the same amino acid sequence.  Sequences are specified with single-letter amino acid codes, with no degenerate codes, and no stop codons.  Sequences should start with M \(Methionine\) and should not contain His tags or other non-FP fusions.

### Molecular Weight

The molecular weight is calculated automatically from the amino acid sequence.

### Cofactor

Some "fluorescent" proteins \(for instance, [those derived from bacterial phytochrome photoreceptors](https://www.fpbase.org/organism/1076/)\) aren't independently/intrinsically fluorescent; rather, they autocatalytically bind and activate the fluorescence of an extrinsic chromophore \(here, referred to as the "cofactor"\).  Often this is a small molecule, most commonly biliverdin \(BV\).  This cofactor must be present in the environment in order to observe fluorescence.  Biliverdin, for example, is a product of heme catabolism, and is therefore present to some extent in most mammalian systems.

### Oligomerization

The dimerization tendency of the fluorescent protein \(monomer, dimer, etc...\).

{% hint style="warning" %}
Many proteins are monomers at low concentrations but dimerize as the concentration increases, so a single classification is unlikely to be a complete characterization of the protein.  Furthermore, some proteins \(such as [TagRFP](https://www.fpbase.org/protein/tagrfp/)\) are described as monomers in early publications, and later found to be weak dimers.  So a simple, single classification of oligomerization tendency is usually insufficient.

See also: [OSER Measurement]().
{% endhint %}

### States

The various states that the protein can be in \(e.g. "red", "green", "off"\).  See [States]() below.

### Transitions

Proteins can have zero or more \(usually light-induced\) transitions between different fluorescent or non-fluorescent [states](). See [Transitions]() below.

### Switch Type

Each protein is classified into one of the following photo-switching types, based on the number of states and transitions that the protein displays:

* **Basic**: A single \(constitutively\) fluorescent state \(e.g. [EGFP](https://www.fpbase.org/protein/egfp/)\).
* **Photoactivatable:** Two states, one transition, from dark state to fluorescent state \(e.g. [PA-GFP](https://www.fpbase.org/protein/pa-gfp/)\).
* **Photoconvertible:** Two states, one transition, from one fluorescent state to another \(e.g. [EosFP](https://www.fpbase.org/protein/eosfp/)\).
* **Photoswitchable**: Two \(reversible\) transitions between two states \(e.g. [Dronpa](https://www.fpbase.org/protein/dronpa/)\).
* **Multi-Photochromic**: Usually greater than 2 states, exhibiting both conversion and switching \(e.g. [IrisFP](https://www.fpbase.org/protein/irisfp/)\).
* **Timer**:  Transitions between 2 or more states over time \(e.g. [DsRed-Timer](https://www.fpbase.org/protein/dsred-timer/)\).
* **Multistate**: Generic categorization for proteins with more than one state.

{% hint style="info" %}
In reality, all fluorescent proteins have many potential states that they can be in, as they progress through maturation pathways or depending on their environment \(pH, etc.\).  So classifying any protein as "basic" is an oversimplification.  The intention here is to classify proteins for their intended purpose \(or, if it becomes known after development that a particularly 
{% endhint %}

### Parental Organism

The original [organism]() from which the protein was cloned and evolved \(e.g. _Aequorea Victoria_ for all proteins that were evolved from the original [avGFP](https://www.fpbase.org/protein/avgfp/)\).  In cases where the protein was computationally designed from a synthetic template, the NCBI [synthetic construct](https://www.ncbi.nlm.nih.gov/Taxonomy/Browser/wwwtax.cgi?id=32630) is used as a parental "organism".

## Fluorescence States <a id="states"></a>

States represent a collection of attributes related to the fluorescent properties of the protein.  A protein can have multiple states, and [transitions]().

### Name

The name of the state \(e.g. "ON", "Green", "default", etc.\).  For single-state proteins, the name "default" is used.

### Excitation Maximum <a id="ex-max"></a>

The excitation maximum of the state in nanometers.  This value is stored independently of any [Spectra]() \(and may be slightly different\).

### Emission Maximum <a id="em-max"></a>

The emission maximum of the state in nanometers. This value is stored independently of any [Spectra]() \(and may be slightly different\).

### Spectra

States can have different [spectra]() for absorption, excitation, two-photon excitation, and emission.

### Extinction Coefficient

The molar extinction coefficient _\(M-1 cm-1\)_ of the state is a measure of how strongly the protein absorbs light at a given wavelength.

### Quantum Yield

Quantum yield represents the ratio of photons emitted to photons absorbed. It is the likelihood that, once excited by a photon, the protein \(state\) will emit a photon.

### Brightness

Molecular brightness is calculated as the product of [Extinction Coefficient]() and [Quantum Yield]().  

{% hint style="warning" %}
Practical brightness of a fluorescent protein depends on additional protein characteristics such as folding and maturation efficiency and pKa.  Molecular brightness may not reflect the actual brightness of a given protein in a biological experiment.
{% endhint %}

### pKa

pKa is a measure of the acid sensitivity of a fluorescent protein. It is the pH at which fluorescence intensity drops to 50% of its maximum value.

## Hill Coefficient

Whereas pKa shows the pH at which a fluorescence drops to 50% of its maximal value, the Hill coefficient describes the slope of the fluorescence-versus-pH relationship.  Many papers do not report Hill coefficients, so this value is unrecorded for many proteins in the database.

{% hint style="info" %}
The pH robustness is often misinterpreted by only looking at pKa values.  For instance, an FP with a low [pKa]() and a low [Hill coefficient]() does not show a pH range in which the fluorescence remains constant.  Therefore, these FPs are still pH-sensitive, even with a low pKa.  On the other hand, an FP with a low pKa and a high Hill coefficient is pH-insensitive as this FP has a plateau at pH values above the pKa.  Thus, pH-insensitive FPs are better identified based on these two parameters combined \(see figure below\).  In addition, pH-sensitivity has always been described _in vitro_, neglecting the effect of cytosolic components on the pH quenching.  How representative _in vitro_ pH-sensitivity is for the _in vivo_ performance is unknown.

🔗 [Botman et al. 2018. _bioRxiv_](https://doi.org/10.1101/431874) __
{% endhint %}

### Maturation

Maturation is the time \(in minutes\) required \(due to protein folding and chromophore maturation\) for fluorescence to obtain half-maximal value.

{% hint style="warning" %}
While maturation is currently stored in FPbase a single number \(corresponding to the half-life of maturation\), maturation does not always follow mono-exponential kinetics, making this value an oversimplification.  For an excellent examination of the complexity of fluorescent protein maturation kinetics in _E coli,_ see [Balleza et al \(2018\)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5765880/) 
{% endhint %}

### Fluorescence Lifetime <a id="lifetime"></a>

The average amount of time \(in nanoseconds\) after photon absorption that it takes the fluorophore to relax to the ground state is referred to as the fluorescence lifetime.

### Bleach Measurements <a id="state-bleach-measurements"></a>

Each fluorescent protein state can have many [bleach measurements](), performed across multiple [references]() and imaging modalities.

### Environmental Requirements

This hidden database field is reserved for proteins that can have multiple states, not necessarily through photoactivation or switching, but through environmental factors such as pH or calcium.

## Transitions

Transition objects in the database capture the \(currently only light-induced\) transition between two [**states**](). 

## Organisms <a id="organism"></a>

Organisms are stored in the database as an [NCBI Taxonomy ID](https://www.ncbi.nlm.nih.gov/taxonomy).  All corresponding data \(such as scientific name, genus, species, rank, etc.\) are pulled from NCBI.

## Spectra

## Bleach Measurement <a id="bleach"></a>

Measurements of photostability and photobleaching are tremendously error-prone, and depend heavily on the specifics of the experiment. We have chosen not to give a single "photostability" metric to each state, but rather allow each state to have one or more bleach measurements, described below

## OSER Measurement <a id="oser"></a>

While FP oligomerization tendency is often measured _in vitro_ using methods such as size-exclusion chromatography, these measurements do not always reflect the behavior of the FP in a cellular environment.  The OSER assay is a commonly-used, biologically relevant assay of FP tendencies to oligomerize.  In an OSER assay, the FP in question is fused to the cytoplasmic end of an endoplasmic reticulum \(ER\) signal anchor membrane protein \(CytERM\) and expressed in cells. Cells are scored based on the ability of CytERM to homo-oligomerize with proteins on opposing membranes and restructure the ER from a tubular network into organized smooth ER \(OSER\) whorl structures \([Costantini et al. 2012](https://doi.org/10.1111/j.1600-0854.2012.01336.x)\).

{% embed url="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3324619/" %}

## References

