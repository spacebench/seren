# AI-Driven Biology and Drug Discovery: Landscape Report

**Date:** August 21, 2026
**Scope:** What's actually working in AI drug discovery — protein engineering, molecular generation, target discovery, key companies, clinical progress, compute/data, market implications.

---

## 1. Protein Engineering

### Protein Language Models (PLMs)

- **ESM-2 / ESMFold** (Meta FAIR): Transformers treating protein sequence like text, pre-trained on ~65M UniRef50 sequences. Largest ESM-2 is 15B parameters. ESMFold predicts structure from sequence alone without MSA — ~60x faster than AlphaFold 2. ([youngju.dev deep dive](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **ESM-3** (EvolutionaryScale, June 2025): Multimodal generative model unifying sequence, structure, and function. Largest version is 98B parameters. Can generate novel proteins with desired functions. Showcased with esmGFP — designing a new GFP variant compressing ~500M years of evolutionary trajectory. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **ESM Atlas**: ~617M metagenomic protein structures predicted with ESMFold. Soil, ocean, and human microbiome proteins. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **Biohub ESM updates** (June 2026): Biohub released updated open-source ESM protein language models after recruiting EvolutionaryScale's team (Alex Rives et al.). ESMFold2 successfully generated lab-validated, high-affinity protein binders against five disease targets in cancer and immunology. ESMC (Cambrian) trained on ~2.8B sequences. ([Rosetta Commons](https://rosettacommons.org/2026/06/09/biohub-releases-open-source-models-that-utilize-evolution-to-design-disease-target-binders/); [Nature](https://www.nature.com/articles/d41586-026-01686-3))

### AlphaFold Ecosystem

- **AlphaFold 3** (May 2024): Models proteins + DNA + RNA + ligands + ions simultaneously. Diffusion-based coordinate generation. ~50% accuracy improvement over AF2 for protein-ligand interactions. Closed access via AlphaFold Server only. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **AlphaFold DB**: ~214M structures predicted for free, covering nearly every UniProt protein. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **AlphaFold 3 benchmark** in drug discovery: 91% accuracy in protein-ligand docking prediction. ([ICAHCR Blog](https://aihealth.scholarvault.in/blog/alphafold-drug-discovery-ai))

- **Boltz-1** (MIT, May 2024) and **Boltz-2** (2025): Open reproductions of AF3-class accuracy. MIT license — free for commercial use. Boltz-2 is ~1.5x faster and adds binding affinity prediction. De facto standard for pharma companies that can't use AF3. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **Chai-1** (Chai Discovery, Sep 2024): AF3-class, especially strong on antibody modeling. Chai-1r (2025) adds binding affinity prediction with RL-based reranking. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **Protenix** (ByteDance, 2024): Fully open AF3 reproduction under Apache 2.0. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **ColabFold**: ~1M users by 2025. Democratized AF2 on Google Colab. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

### De Novo Protein Design

- **RFdiffusion** (Baker Lab, 2023): Diffusion model generating protein backbones from scratch. Used for binder, enzyme, and antibody design. One of the core Nobel-cited technologies. ([Nature 2023](https://www.nature.com/articles/s41586-023-06415-8))

- **RFdiffusion All-Atom** (2024): Designs backbones + side chains + ligands simultaneously. Generates proteins with measurably higher binding affinity. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **RFdiffusion3** (Dec 2025): Foundation model for biodesign. Generates proteins interacting with any type of molecule commonly found inside cells. ([IPD UW](https://www.ipd.uw.edu/2025/12/rfdiffusion3-now-available/))

- **ProteinMPNN** (Baker Lab, 2022): Given a backbone, generates amino acid sequence. Standard pipeline: RFdiffusion → ProteinMPNN → AlphaFold2 validation. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **Limitations**: A 2025 bioRxiv study found RFdiffusion exhibits low success rate in de novo design of functional protein binders for biochemical detection, with low-affinity designs and inconsistent recombinant expression. ([bioRxiv](https://www.biorxiv.org/content/10.1101/2025.02.07.636769v1))

### Antibody Engineering

- **Chai-2** (Chai Discovery, 2025): Zero-shot generative antibody design platform. ~20% hit rate across 52 designed targets. Compresses antibody design cycle from 12-24 months to 4-8 weeks. ([nextomoro](https://nextomoro.com/chai-discovery))

- **Absci** (NASDAQ: ABSI): AI-designed anti-TL1A antibody (ABS-101) entered Phase 1/2a. Extended half-life vs first-generation anti-TL1A competitors. Seeking out-licensing partner. ([IntuitionLabs](https://intuitionlabs.ai/articles/ai-discovered-drugs-clinical-trials-2026))

- **Absci + partners**: Collaborations with GSK, Merck. Designs and expresses target-binding antibodies within six weeks. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

---

## 2. Molecular Generation

### Generative Models

- **Chemistry42** (Insilico Medicine): Generative chemistry engine using deep generative models + RL. Generated INS018_055 (rentosertib) for IPF. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **MolMIM** (NVIDIA BioNeMo, 2024): Molecular generation model. Generates molecules with similar but improved properties from an input molecule. Accelerates hit-to-lead phase. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **DiffDock** (MIT, 2023): Diffusion-based docking model. Directly generates protein-ligand binding poses. Tens of times faster than AutoDock Vina. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **GPS** (Michigan State, March 2026): Deep learning model predicting gene expression from chemical structure alone. No biological experiments required. Identified novel candidates for hepatocellular carcinoma (tested in mice, reduced tumor size) and IPF. Published in Cell. ([Healthcare Discovery](https://healthcarediscovery.ai/ai-drug-discovery-pipeline-2026-clinical-trials/))

### Platforms Generating Candidates Reaching Trials

- **Generate Biomedicines** Chroma model: Generates novel protein structures conditioned on desired function. Lead candidate GB-0895 (anti-TSLP antibody for severe asthma) reached Phase III. ([Healthcare Discovery](https://healthcarediscovery.ai/ai-drug-discovery-pipeline-2026-clinical-trials/))

- **Recursion + Exscientia merged platform**: REC-1245 progressed from target to IND in under 18 months. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

---

## 3. Target Discovery

### AI-Driven Target Identification

- **PandaOmics** (Insilico Medicine): Mines transcriptomic and proteomic datasets for novel disease drivers. Identified TNIK as a novel target for IPF — never before pursued as a therapeutic target. ([Healthcare Discovery](https://healthcarediscovery.ai/ai-drug-discovery-pipeline-2026-clinical-trials/))

- **Recursion Maps**: Phenotypic screening based on cell imaging. ~1M cell images analyzed per experiment. Models drug-gene-disease relationships as a graph. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

### Single-Cell and Spatial Biology

- **Single-cell/spatial omics** are transforming target discovery. Technologies enable molecular profiling at single-cell resolution within intact tissue architecture. ([Wiley review](https://onlinelibrary.wiley.com/doi/full/10.1002/mco2.70713))

- **Geneformer** (MIT Broad, 2023): Transformer over single-cell transcriptomic data. Pre-trained on ~30M cells. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **scGPT** (U Toronto + Wang Lab, 2023): Single-cell foundation model pre-trained on 33M cells. Multitasks across cell type classification, batch correction, perturbation prediction. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **Human Cell Atlas**: ~100M cells profiled by 2025. Global consortium building single-cell maps. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **10x Genomics Atera** (AACR 2026): New spatial biology platform. Spatial biology moving from small-scale experiments toward production-scale datasets for AI-driven discovery. ([Single Cell World](https://thesinglecellworld.substack.com/p/aacr-2026-it-wasnt-just-about-atera))

- **MOSAIC** (Owkin): Multi-Omics Spatial Atlas In Cancer initiative. ([10x Genomics](https://www.10xgenomics.com/blog/our-top-5-single-cell-and-spatial-innovations-from-2025))

### Companies Validating Targets Computationally

- **BenevolentAI**: Knowledge graph approach identified baricitinib for COVID-19, leading to FDA EUA. Restructured in 2024, recovering. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **Open Targets** (GSK + Sanofi + BMS + consortium): Drug target prioritization database combining genetics, clinical, and chemistry data. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

- **Atomwise**: AtomNet CNN-based docking model. 200+ target collaborations with Pfizer, Bayer, Merck, etc. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

---

## 4. Key Companies

### Insilico Medicine (HKEX: 3696)

- **Founded:** 2014. Hong Kong, New York, Shanghai.
- **Platform:** Pharma.AI (PandaOmics + Chemistry42 + InClinico).
- **Lead drug:** Rentosertib (INS018_055), TNIK inhibitor for IPF. Published positive Phase IIa results in Nature Medicine (June 2025). Mean FVC improvement +98.4 mL vs -20.3 mL placebo. ([Nature Medicine](https://www.nature.com/nm/); [Healthcare Discovery](https://healthcarediscovery.ai/ai-drug-discovery-pipeline-2026-clinical-trials/))
- **Timeline:** Target-to-Phase 2 in under 30 months (vs 6-8 years traditional).
- **IPO:** Listed on Hong Kong Stock Exchange Dec 30, 2025 — "largest biotech IPO in HK this year." ([PRNewswire](https://prnewswire.com))
- **Revenue:** $102.5M-$106.5M in H1 2026 (up 272-287% YoY). Net profit $33.5M-$39.5M. ([Insilico press release](https://insilico.com/news/6f8yhr6sl1-insilico-medicine-releases-positive-prof))
- **Clinical assets:** 28+ drugs using generative AI, nearly half at clinical stage. CEO Zhavoronkov, March 2026. ([CNBC](https://cnbc.com))
- **Partnerships:** 13 of top 20 pharma companies. Eli Lilly ($2.75B deal, March 2026), Takeda, SK Biopharmaceuticals. Combined disclosed value $5.85B. ([Noah Bio](https://www.noah.bio/insight/903d640b-23ef-4216-ac0b-c487667a87e0))

### Isomorphic Labs (Alphabet)

- **Founded:** 2021. Spun off from DeepMind.
- **Tech:** AlphaFold-derived protein structure prediction + proprietary design engine.
- **Funding:** $600M Series A (March 2025, led by Thrive Capital). $2.1B Series B (May 2026). ([DealForma](https://dealforma.com/ai-ml-drug-discovery-and-licensing-rd-ma-ventures-and-ipos-2025-review/); [Noah Bio](https://www.noah.bio/insight/903d640b-23ef-4216-ac0b-c487667a87e0))
- **Partnerships:** Eli Lilly (>$1.7B milestones), Novartis (~$1.2B), Johnson & Johnson. ([Vision Life Sciences](https://visionlifesciences.com/insights/ai-drug-discovery-deal-tracker))
- **Clinical status:** 17 drug programs. First oncology candidate targeted for Phase 1 by end 2026 (revised from end 2025). ([Isomorphic Labs via Nexi Fund](https://nexi.fund/isomorphic-labs-drug-design-engine-2026))
- **Internal pipeline:** Phase 2 advancement for independently-owned program (not partnership). ([DeFi Crypto News](https://deficryptonews.co/isomorphic-labs-ai-drug-discovery-clinical-trials-2026))

### Recursion Pharmaceuticals (NASDAQ: RXRX)

- **Founded:** 2013. Salt Lake City.
- **Merged with Exscientia** (Jan 2024, ~$700M). Now largest publicly listed AI drug discovery company by pipeline breadth. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))
- **Platform:** Recursion OS — phenotypic imaging + multi-omics + AI chemistry. ~6B cell images. BioHive-1/2 supercomputers (NVIDIA). ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))
- **Pipeline:** 10+ clinical readouts guided across 18-month window. Pipeline discipline: trimmed weaker programs in 2025. ([Curionic](https://www.curionic.net/2026/07/isomorphic-labs-vs-recursion-vs-insilico-medicine-ai-drug-discovery-2026.html))
- **Key readouts:** REC-1245 (RBM39 degrader, solid tumors) Phase I data H1 2026. REC-394 (C. difficile) Phase 2 Q1 2026. ([Pharma Insight Lab](https://note.com/pharma_insight/n/n3ca11cb1a7dc?hl=en))
- **Partnerships:** Sanofi, Roche/Genentech ($150M research funding), Bayer, Merck KGaA. $450M upfront/milestones received to date. $20B+ total potential milestones. ([Pharma Insight Lab](https://note.com/pharma_insight/n/n3ca11cb1a7dc?hl=en))

### Generate Biomedicines (NASDAQ: GENB)

- **Founded:** 2018 by Flagship Pioneering.
- **Platform:** Chroma — generative model designing novel protein structures conditioned on desired function.
- **Lead drug:** GB-0895, anti-TSLP antibody for severe asthma. Engineered for once-every-6-months dosing (vs monthly for Amgen's tezepelumab). First AI-designed antibody to reach Phase III. ([Healthcare Discovery](https://healthcarediscovery.ai/ai-drug-discovery-pipeline-2026-clinical-trials/))
- **Trials:** SOLAIRIA-1 and SOLAIRIA-2, ~1,600 patients. First patient dosed January 2026. ([PRNewswire](https://www.prnewswire.com/news-releases/generatebiomedicines-to-initiate-global-phase-3-studies-of-gb-0895-a-long-acting-anti-tslp-antibody-for-severe-asthma-engineered-with-ai-302628234.html))
- **IPO:** $400M raise on Nasdaq (Feb 2026). ([Reuters](https://www.reuters.com/business/healthcare-pharmaceuticals/drug-developer-generate-biomedicines-raises-400-million-us-ipo-2026-02-27))
- **Other pipeline:** GB-0669 (inhalable monoclonal antibody for COVID-19, Phase 1 completed with acceptable safety/PK data). ([Healthcare Discovery](https://healthcarediscovery.ai/ai-designed-drugs-human-trials-2026-status-report/))

### Chai Discovery

- **Founded:** March 2024 by Joshua Meier (ex-OpenAI), Jack Dent, Matthew McPartlon, Jacques Boitreaud.
- **Funding:** $30M seed (Sep 2024, led by Thrive Capital + OpenAI + Dimension) → $70M Series A (Aug 2025) → $130M Series B (Dec 2025, $1.3B valuation). Total $225M+. ([nextomoro](https://nextomoro.com/chai-discovery))
- **Products:** Chai-1 (open, multi-modal structure prediction); Chai-2 (closed, zero-shot antibody design, ~20% hit rate). ([nextomoro](https://nextomoro.com/chai-discovery))
- **Partnership:** Eli Lilly collaboration (Jan 2026) for biologics discovery. Custom model development. ([BusinessWire](https://www.businesswire.com/news/home/20260108131261/en/Chai-Discovery-Announces-Collaboration-with-Eli-Lilly-and-Company-to-Accelerate-Biologics-Discovery))
- **Valuation:** $3.8B (July 2026 Series C of $400M). ([IntuitionLabs](https://intuitionlabs.ai/articles/ai-drug-discovery-fda-approvals))

### Absci (NASDAQ: ABSI)

- **Founded:** 2011. Vancouver, WA.
- **Focus:** "Generative AI for antibody discovery." Combines ML + wet lab.
- **Clinical:** ABS-101 (anti-TL1A for IBD) — Phase 1 interim data showed extended half-life. Seeking out-licensing partner. ABS-201 (androgenetic alopecia) — Phase 1/2a. ([IntuitionLabs](https://intuitionlabs.ai/articles/ai-discovered-drugs-clinical-trials-2026))
- **Total funding:** $228M. ([Crunchbase](https://www.crunchbase.com/organization/absci))
- **Partnerships:** GSK, Merck, EQRx. ([CBInsights](https://www.cbinsights.com/company/absci))

### EvolutionaryScale

- **Founded:** 2024. Spun out of Meta FAIR's protein team.
- **Product:** ESM-3 generative protein language model.
- **Funding:** $142M Series A (2024), invested by Amazon, NVIDIA. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))
- **Current status:** Team recruited by Biohub (June 2026). ([Rosetta Commons](https://rosettacommons.org/2026/06/09/biohub-releases-open-source-models-that-utilize-evolution-to-design-disease-target-binders/))

### Cradle Bio

- **Founded:** 2021. Netherlands/Switzerland.
- **Focus:** Protein engineering (industrial enzymes, pharmaceutical proteins).
- **Partnerships:** Novartis, BASF, AstraZeneca.
- **Funding:** $73M Series B (2024). ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

### Basecamp Research

- Founded by researchers from the Exploratorium for Biological Data. Collects proprietary biodiversity data to train protein models. (Not detailed in fetched sources — gap.)

### Earendil Labs

- **Funding:** $787M — record-setting for biologics AI. (2026)
- **Partnerships:** Sanofi ($125M upfront, up to $1.72B milestones for two bispecific antibodies targeting autoimmune/IBD). Plans multiple IND submissions in 2026-27. ([IntuitionLabs](https://intuitionlabs.ai/articles/ai-biologics-discovery-pharma-investment-trends))

### Lila Sciences (Flagship Pioneering)

- **Funding:** $500M+ in 2025 ($350M Series A total). Focus: AI-driven "scientific superintelligence" + automated research. NVIDIA invested. ([DealForma](https://dealforma.com/ai-ml-drug-discovery-and-licensing-rd-ma-ventures-and-ipos-2025-review/))

### Other Notable Companies

- **Schrödinger** (NASDAQ SDGR): Molecular dynamics + quantum chemistry software. Own pipeline in collaboration with Nimbus Therapeutics.
- **Atomwise:** AtomNet CNN docking. 200+ target collaborations.
- **Pathos AI:** $365M Series D (May 2025). AI foundation model for oncology.
- **BenevolentAI:** Knowledge graph approach. Restructured 2024, recovering.
- **Formation Bio:** AI-accelerated clinical trials. Deals with Sanofi (€545M) and Lilly (~$2B). ([IntuitionLabs](https://intuitionlabs.ai/articles/ai-biologics-discovery-pharma-investment-trends))
- **Helixon:** $1.7B licensing deal with Sanofi (2025) for AI-generated antibodies. ([ScienceDirect review](https://www.sciencedirect.com/science/article/abs/pii/S0031699725075118))

---

## 5. Clinical Progress

### Pipeline Overview (Mid-2026)

| Stage | Programs | Notes |
|---|---|---|
| Phase III/Pivotal | 15-20 | GB-0895 (asthma), zasocitinib (psoriasis) |
| Phase II | 56 | Rentosertib (IPF), others |
| Phase I | ~94 | Wider pipeline |
| Total Clinical | 173+ | Up from ~24 in late 2023 |

([Healthcare Discovery](https://healthcarediscovery.ai/ai-drug-discovery-pipeline-2026-clinical-trials/); [POC.HK](https://en.poc.hk/ai-drug-discovery-2026-clinical-inflection))

### Key Clinical Milestones

- **Rentosertib (Insilico Medicine)**: First AI-designed drug with positive efficacy signal. Phase IIa published Nature Medicine June 2025. +98.4 mL FVC improvement at 60mg QD. Preparing Phase IIb/III global enrollment. ([Healthcare Discovery](https://healthcarediscovery.ai/ai-drug-discovery-pipeline-2026-clinical-trials/))

- **GB-0895 (Generate Biomedicines)**: First AI-designed antibody to reach Phase III. SOLAIRIA-1/2 trials dosing ~1,600 patients. First patient dosed Jan 2026. ([PRNewswire](https://www.prnewswire.com/news-releases/generatebiomedicines-to-initiate-global-phase-3-studies-of-gb-0895-a-long-acting-anti-tslp-antibody-for-severe-asthma-engineered-with-ai-302628234.html))

- **Zasocitinib (Takeda/Nimbus/Schrödinger)**: TYK2 inhibitor. Beat deucravacitinib in head-to-head Phase III psoriasis trial (June 2026). Heading toward FDA submission. Origin traces to physics-based free energy perturbation modeling. ([Takeda](https://www.takeda.com/newsroom/newsreleases/2026/zasocitinib-outperforms-deucravacitinib-study/))

- **Isomorphic Labs**: First oncology candidate entering Phase 1 by end 2026. Delayed from end 2025. ([Nexi Fund](https://nexi.fund/isomorphic-labs-drug-design-engine-2026))

- **Generate Biomedicines GB-0669**: Inhaled antibody for COVID-19. Phase 1 completed with acceptable safety and PK/PD data (late 2025). ([Healthcare Discovery](https://healthcarediscovery.ai/ai-designed-drugs-human-trials-2026-status-report/))

- **KumaMax** (Takeda/IPD UW): Enzyme designed for celiac disease. Human trials underway. From David Baker's lab. ([Peptide Journal](https://www.peptidejournal.org/research/de-novo-peptide-design-computer-to-clinical-trial))

- **GBP510** (SK Bioscience/IPD UW): COVID-19 vaccine designed computationally. WHO Emergency Use Listing. Approved in UK and South Korea. ([Peptide Journal](https://www.peptidejournal.org/research/de-novo-peptide-design-computer-to-clinical-trial))

### FDA Approvals

- **No AI-discovered drug has received FDA approval** as of August 2026.
- First approval projected for late 2026-2027. Analysts place probability at ~60%. ([Healthcare Discovery](https://healthcarediscovery.ai/ai-drug-discovery-pipeline-2026-clinical-trials/); [POC.HK](https://en.poc.hk/ai-drug-discovery-2026-clinical-inflection))

### Success Rates

- **Phase I:** 80-90% (vs ~52% historical average). ([Biotech Intelligence](https://biotech-intelligence.com/ai-driven-drug-discovery-clinical-development-machine-learning-reshaping-pharma-rd-2026/); [Healthcare Discovery](https://healthcarediscovery.ai/ai-drug-discovery-pipeline-2026-clinical-trials/))
- **Phase II:** ~40% (comparable to historical 29-40%, not clearly superior). Small sample sizes. ([Healthcare Discovery](https://healthcarediscovery.ai/ai-drug-discovery-pipeline-2026-clinical-trials/))
- **Integrated Phase I-to-approval probability:** 9-18% (vs 5-10% historical). ([IntuitionLabs](https://intuitionlabs.ai/articles/ai-drug-discovery-fda-approvals))

### The Honest Assessment

AI compresses discovery timelines (30 months vs 6-8 years to candidate). But Phase II/III attrition remains biology-dependent, not compute-dependent. As one analysis put it: "AI speeds up finding a promising molecule. It doesn't yet shorten proving that molecule actually works and is safe in people." ([Curionic](https://www.curionic.net/2026/07/isomorphic-labs-vs-recursion-vs-insilico-medicine-ai-drug-discovery-2026.html))

---

## 6. Compute and Data

### Training Data

- **PDB:** ~230,000 experimental protein structures (2025). Core training data for structure prediction. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))
- **UniProt:** ~250M sequences. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))
- **AlphaFold DB:** ~214M predicted structures. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))
- **ESM Atlas:** ~617M metagenomic structures. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))
- **ChEMBL:** ~2.3M compounds, ~20M activity measurements. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))
- **JUMP-CP:** 116K compounds + 12K gene perturbations, phenotypic profiles. Released May 2024. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

### Compute Infrastructure

- **NVIDIA collaboration:** Recursion's BioHive-2 built on ~600 H100s. NVIDIA invested in Recursion. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))
- **NVIDIA + Lilly lab** (Jan 2026): Co-innovation AI lab. ([Biotech Intelligence](https://biotech-intelligence.com/ai-driven-drug-discovery-clinical-development-machine-learning-reshaping-pharma-rd-2026/))
- **ML force fields:** AIMNet2, ANI, MACE deliver quantum-chemistry-level accuracy at speed. Equivariant models (NequIP, Allegro) becoming de facto standard. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))

### Key Bottlenecks

- **Wet-lab validation data shortage:** The biggest bottleneck as of 2026. Computational predictions outpace experimental confirmation. ([youngju.dev](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en))
- **Data quality:** 68% of tech executives identify poor data quality and governance as the main reason AI initiatives fail. ([Biotech Intelligence](https://biotech-intelligence.com/ai-driven-drug-discovery-clinical-development-machine-learning-reshaping-pharma-rd-2026/))
- **Data sharing restrictions:** Privacy regulations and cost barriers limit access to biological, pharmacological, and clinical annotations. ([Biotech Intelligence](https://biotech-intelligence.com/ai-driven-drug-discovery-clinical-development-machine-learning-reshaping-pharma-rd-2026/))
- **Context collapse:** Computational design optimizes binding in isolation; real biology involves membranes, crowded cytoplasm, pH gradients. Gap between in vitro and clinical remains substantial. ([Peptide Journal](https://www.peptidejournal.org/research/de-novo-peptide-design-computer-to-clinical-trial))

---

## 7. Market Implications

### Market Size

- **2025:** Global AI-in-drug-discovery market valued at $6.93B. ([Precedence Research via IntuitionLabs](https://intuitionlabs.ai/articles/ai-drug-discovery-fda-approvals))
- **2026:** Projected $7.62B. ([Precedence Research via IntuitionLabs](https://intuitionlabs.ai/articles/ai-drug-discovery-fda-approvals))
- **2035:** Projected $17.81B at 9.9% CAGR. ([Precedence Research via IntuitionLabs](https://intuitionlabs.ai/articles/ai-drug-discovery-fda-approvals))
- **Potential value of generative AI in pharma overall:** $60-110B annually. ([Biotech Intelligence](https://biotech-intelligence.com/ai-driven-drug-discovery-clinical-development-machine-learning-reshaping-pharma-rd-2026/))

### Investment and Deals

- **$34B flowing into AI drug discovery** between 2022-2025. ([Biotech Intelligence](https://biotech-intelligence.com/ai-driven-drug-discovery-clinical-development-machine-learning-reshaping-pharma-rd-2026/))
- **$22B+ in disclosed capital** to AI biotech/CDD between Jan 2025 and July 2026 (M&A, collaborations, licensing, equity). ([Noah Bio](https://www.noah.bio/insight/903d640b-23ef-4216-ac0b-c487667a87e0))
- **168 AI-related strategic alliances** signed across industry in 2025. ([IntuitionLabs](https://intuitionlabs.ai/articles/ai-drug-discovery-fda-approvals))
- **AI drug discovery partnerships:** 114 deals in 2025 totaling $43.4B in potential value (vs 84 deals/$11.8B in 2024). ([DealForma](https://dealforma.com/ai-ml-drug-discovery-and-licensing-rd-ma-ventures-and-ipos-2025-review/))
- **Total biobucks:** $15B+ in announced AI drug discovery partnerships in 2025, but typical upfront is just 2% of headline value. ([Biotech Intelligence](https://biotech-intelligence.com/ai-driven-drug-discovery-clinical-development-machine-learning-reshaping-pharma-rd-2026/))
- **VC investment:** $11B across 348 rounds in 2025 (up from $8.9B/264 rounds in 2024). ([DealForma](https://dealforma.com/ai-ml-drug-discovery-and-licensing-rd-ma-ventures-and-ipos-2025-review/))
- **M&A:** 99 transactions totaling $12.3B in 2025 (vs 34/$3.2B in 2024). Siemens/Dotmatics ($5.1B), GE HealthCare/Intelerad ($2.3B) were largest. ([DealForma](https://dealforma.com/ai-ml-drug-discovery-and-licensing-rd-ma-ventures-and-ipos-2025-review/))

### Notable Deal Examples

| Deal | Value | Date |
|---|---|---|
| Insilico Medicine + Eli Lilly | Up to $2.75B | March 2026 |
| XtalPi + DoveTree | Up to $6B | Aug 2025 |
| Monte Rosa + Novartis | Up to $5.4B | Sep 2025 |
| AstraZeneca + CSPC Pharma | Up to $5.2B | June 2025 |
| Isomorphic Labs Series A | $600M | March 2025 |
| Isomorphic Labs Series B | $2.1B | May 2026 |
| Chai Discovery Series B | $130M ($1.3B val) | Dec 2025 |
| Chai Discovery Series C | $400M ($3.8B val) | July 2026 |
| Generate Biomedicines IPO | $400M | Feb 2026 |
| Earendil Labs funding | $787M | 2026 |
| Eli Lilly + Purdue | $250M | May 2025 |

Sources: [DealForma](https://dealforma.com/ai-ml-drug-discovery-and-licensing-rd-ma-ventures-and-ipos-2025-review/); [Noah Bio](https://www.noah.bio/insight/903d640b-23ef-4216-ac0b-c487667a87e0); [IntuitionLabs](https://intuitionlabs.ai/articles/ai-biologics-discovery-pharma-investment-trends); [nextomoro](https://nextomoro.com/chai-discovery); [Vision Life Sciences](https://visionlifesciences.com/insights/ai-drug-discovery-deal-tracker)

### IPO Market

- 5 AI drug discovery IPOs in 2025, raising $1.3B (up from $424M in 2024). Key: Caris Life Sciences ($494M at $5.9B valuation), Lumexa Imaging ($463M). ([DealForma](https://dealforma.com/ai-ml-drug-discovery-and-licensing-rd-ma-ventures-and-ipos-2025-review/))
- Insilico Medicine HK IPO Dec 2025. Generate Biomedicines IPO Feb 2026.

### China Factor

- Chinese-originated drugs projected to comprise ~40% of all new licensing deals. ([Noah Bio](https://www.noah.bio/insight/903d640b-23ef-4216-ac0b-c487667a87e0))
- Licensing deal value reached 10-year high of $232B in 2025, with 40% of assets in-licensed by big pharma originating from China (up from ~30% in 2024). ([Noah Bio](https://www.noah.bio/insight/903d640b-23ef-4216-ac0b-c487667a87e0))
- Next deal wave: AI-originated assets out-licensed from China — faster, cheaper proof-of-concept feeding global pipelines. ([Vision Life Sciences](https://visionlifesciences.com/insights/ai-drug-discovery-deal-tracker))

### Investment Thesis

The sector is transitioning from hype to proof. Key dynamics:

1. **Patent cliff urgency:** >$200B in revenue losing exclusivity this decade, pushing pharma toward AI partnerships.
2. **Shift from asset to platform deals:** Pharma buying AI infrastructure, not single molecules.
3. **Upfronts stay modest:** $30-50M typical; headline values are overwhelmingly contingent biobucks.
4. **Selective capital:** VCs becoming more selective after 2021 peak ($22B in AI health VC → $10.5B in 2024). ([IntuitionLabs](https://intuitionlabs.ai/articles/ai-biologics-discovery-pharma-investment-trends))
5. **The 2026 inflection:** 15-20 Phase III readouts expected. First approval projected 2026-2027. This is the "prove it" year.

---

## Sources

All URLs accessed August 2026 unless otherwise noted.

- [Healthcare Discovery — AI Drug Discovery Pipeline 2026](https://healthcarediscovery.ai/ai-drug-discovery-pipeline-2026-clinical-trials/)
- [Healthcare Discovery — AI-Designed Drugs in Human Trials 2026](https://healthcarediscovery.ai/ai-designed-drugs-human-trials-2026-status-report/)
- [IntuitionLabs — AI Drug Discovery FDA Approvals 2026](https://intuitionlabs.ai/articles/ai-drug-discovery-fda-approvals)
- [IntuitionLabs — AI-Discovered Drugs in Clinical Trials 2026](https://intuitionlabs.ai/articles/ai-discovered-drugs-clinical-trials-2026)
- [IntuitionLabs — AI Biologics Discovery Pharma Investment Trends](https://intuitionlabs.ai/articles/ai-biologics-discovery-pharma-investment-trends)
- [Biotech Intelligence — AI-Driven Drug Discovery 2026](https://biotech-intelligence.com/ai-driven-drug-discovery-clinical-development-machine-learning-reshaping-pharma-rd-2026/)
- [DealForma — AI-ML Drug Discovery 2025 Review](https://dealforma.com/ai-ml-drug-discovery-and-licensing-rd-ma-ventures-and-ipos-2025-review/)
- [Noah Bio — Pharma Investment in AI Biotech 2025-2026](https://www.noah.bio/insight/903d640b-23ef-4216-ac0b-c487667a87e0)
- [Vision Life Sciences — AI Drug Discovery Deal Tracker 2026](https://visionlifesciences.com/insights/ai-drug-discovery-deal-tracker)
- [youngju.dev — AI for Biology & Drug Discovery 2026 Complete Guide](https://www.youngju.dev/blog/culture/2026-05-16-ai-biology-drug-discovery-2026-alphafold-3-rosettafold-esm-atlas-boltz-chai-rfdiffusion-isomorphic-recursion-deep-dive.en)
- [Curionic — Isomorphic vs Recursion vs Insilico 2026](https://www.curionic.net/2026/07/isomorphic-labs-vs-recursion-vs-insilico-medicine-ai-drug-discovery-2026.html)
- [Nexi Fund — Isomorphic Labs 2026](https://nexi.fund/isomorphic-labs-drug-design-engine-2026)
- [nextomoro — Chai Discovery](https://nextomoro.com/chai-discovery)
- [Pharma Insight Lab — Insilico/Isomorphic/Recursion](https://note.com/pharma_insight/n/n3ca11cb1a7dc?hl=en)
- [Insilico Medicine — H1 2026 Profit Alert](https://insilico.com/news/6f8yhr6sl1-insilico-medicine-releases-positive-prof)
- [Nature Medicine — Rentosertib Phase IIa](https://www.nature.com/nm/)
- [Nature — ESMFold2 / Biohub](https://www.nature.com/articles/d41586-026-01686-3)
- [Rosetta Commons — Biohub ESM Release](https://rosettacommons.org/2026/06/09/biohub-releases-open-source-models-that-utilize-evolution-to-design-disease-target-binders/)
- [ICAHCR — AlphaFold & Drug Discovery 2026](https://aihealth.scholarvault.in/blog/alphafold-drug-discovery-ai)
- [PRNewswire — Generate Biomedicines Phase 3](https://www.prnewswire.com/news-releases/generatebiomedicines-to-initiate-global-phase-3-studies-of-gb-0895-a-long-acting-anti-tslp-antibody-for-severe-asthma-engineered-with-ai-302628234.html)
- [BusinessWire — Chai Discovery + Eli Lilly](https://www.businesswire.com/news/home/20260108131261/en/Chai-Discovery-Announces-Collaboration-with-Eli-Lilly-and-Company-to-Accelerate-Biologics-Discovery)
- [POC.HK — AI Drug Discovery 2026](https://en.poc.hk/ai-drug-discovery-2026-clinical-inflection)
- [BioRxiv — RFdiffusion Limitations](https://www.biorxiv.org/content/10.1101/2025.02.07.636769v1)
- [IPD UW — RFdiffusion3](https://www.ipd.uw.edu/2025/12/rfdiffusion3-now-available/)
- [Peptide Journal — De Novo Peptide Design](https://www.peptidejournal.org/research/de-novo-peptide-design-computer-to-clinical-trial)
- [Wiley — Single-Cell and Spatial Omics 2026](https://onlinelibrary.wiley.com/doi/full/10.1002/mco2.70713)
- [10x Genomics — 2025 Innovations](https://www.10xgenomics.com/blog/our-top-5-single-cell-and-spatial-innovations-from-2025)
- [Single Cell World — AACR 2026](https://thesinglecellworld.substack.com/p/aacr-2026-it-wasnt-just-about-atera)
- [ScienceDirect — AI Drug Discovery Review 2026](https://www.sciencedirect.com/science/article/abs/pii/S0031699725075118)
- [Reuters — Generate Biomedicines IPO](https://www.reuters.com/business/healthcare-pharmaceuticals/drug-developer-generate-biomedicines-raises-400-million-us-ipo-2026-02-27)
- [CNBC — Insilico Medicine March 2026](https://cnbc.com)
- [Takeda — Zasocitinib Phase III](https://www.takeda.com/newsroom/newsreleases/2026/zasocitinib-outperforms-deucravacitinib-study/)
- [CBInsights — Absci](https://www.cbinsights.com/company/absci)
- [Crunchbase — Absci](https://www.crunchbase.com/organization/absci)
