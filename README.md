<h1 align="center">:page_facing_up: A Machine Learning Case Study for AI-empowered echocardiography of Intensive Care Unit Patients in low- and middle-income countries </h1>
<div align="center">

2nd Machine Learning for Health symposium 2022 (ML4H 2022) • November 28th, 2022 • Hybrid/New Orleans 2022

[![article](https://img.shields.io/badge/article-arXiv-orange.svg)](https://arxiv.org/abs/.) 
[![article](https://img.shields.io/badge/video-YouTube-red.svg)](https://www.youtube.com/watch?v=) 
[![GitHub Actions Status](https://github.com/vital-ultrasound/2022-echocardiography-proceedings/workflows/CI-LaTeX/badge.svg)](https://github.com/vital-ultrasound/2022-echocardiography-proceedings/actions) [![new-literature](https://img.shields.io/badge/check-abstract-blue.svg)](https://github.com/vital-ultrasound/2022-echocardiography-proceedings/blob/pdfs/ml4h2022.pdf)  
(This work is 100% Reproducible)   
</div>

## Abstract
We present a Machine Learning (ML) study case to illustrate the challenges of clinical translation for a real-time AI-empowered echocardiography system with data of ICU patients in LMICs.
Such ML case study includes data preparation, curation and labelling from 2D Ultrasound videos of 31 ICU patients in LMICs and model selection, validation and deployment of three thinner neural networks to classify apical four-chamber view (4CV).
Results of the reproducible ML heuristics showed the promising implementation, validation and application of thinner networks to classify 4CV and limited datasets.
We conclude this work mentioning the need for (a) datasets to improve diversity of demographics, diseases, (b) AI-empowered devices to deploy and validate ML models and (c) the need of further investigations of thinner models to be run and implemented in low-cost hardware to be clinically translated in the ICU in LMICs.
The code and other resources to reproduce this work are available at \url{https://github.com/vital-ultrasound/echocardiography}.

## Clone repo
After generating your SSH keys as suggested [here](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent), you can then clone the repository in the suggested path by typing (or copying) the following lines in a terminal:
```
mkdir -p $HOME/repositories/vital-ultrasound  && cd $HOME/repositories/vital-ultrasound  ## suggested path
git clone git@github.com:vital-ultrasound/ML4H2022.git
```

## Workflow 
See [README](workflow/README.md) for detailed instructions on a workflow for build the TeX-based paper in your local machine or with the CI build.

## Contact 
If you have specific questions about the content of this repository, you can contact [Miguel Xochicale](mailto:miguel.xochicale@kcl.ac.uk?subject="[2022-proceedings-for-echocardiography]"). 
If your question might be relevant to other people, please instead [open an issue](https://github.com/vital-ultrasound/2022-echocardiography-proceedings/issues).
