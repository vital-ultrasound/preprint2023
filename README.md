<h1 align="center">:page_facing_up: A Machine Learning Case Study for AI-empowered echocardiography of Intensive Care Unit Patients in low- and middle-income countries </h1>
<div align="center">

Preprint2023

[![article](https://img.shields.io/badge/article-arXiv-orange.svg)](https://arxiv.org/abs/2212.14510) 
[![GitHub Actions Status](https://github.com/vital-ultrasound/2022-echocardiography-proceedings/workflows/CI-LaTeX/badge.svg)](https://github.com/vital-ultrasound/2022-echocardiography-proceedings/actions) 
[![new-literature](https://img.shields.io/badge/abstract-CIPDF-blue.svg)](https://github.com/vital-ultrasound/preprint2023/blob/pdfs/preprint2023.pdf)  
(This work is 100% Reproducible)   
</div>

## Abstract
We present a Machine Learning (ML) study case to illustrate the challenges of clinical translation for a real-time AI-empowered echocardiography system with data of ICU patients in LMICs.
Such ML case study includes data preparation, curation and labelling from 2D Ultrasound videos of 31 ICU patients in LMICs and model selection, validation and deployment of three thinner neural networks to classify apical four-chamber view.
Results of the ML heuristics showed the promising implementation, validation and application of thinner networks to classify 4CV with limited datasets.
We conclude this work mentioning the need for (a) datasets to improve diversity of demographics, diseases, and (b) the need of further investigations of thinner models to be run and implemented in low-cost hardware to be clinically translated in the ICU in LMICs.
The code and other resources to reproduce this work are available at https://github.com/vital-ultrasound/ai-assisted-echocardiography-for-low-resource-countries.

## Licence and Citation 
This work is under Creative Commons Attribution-Share Alike license [![License: CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/80x15.png)](https://creativecommons.org/licenses/by-sa/4.0/). 
Hence, you are free to reuse it and modify it as much as you want and as long as you cite [this work](https://github.com/budai4medtech/miua2022) as original reference and you re-share your work under the same terms.


### BibTeX to cite
```
@misc{https://doi.org/10.48550/arxiv.2212.14510,
  author = {Xochicale, Miguel and 
	    Thwaites, Louise and 
            Yacoub, Sophie and 
            Pisani, Luigi and 
            Phung, Tran Huy Nhat and 
            Kerdegari, Hamideh and 
            King, Andrew and 
            Gomez, Alberto}, 
  title = {A Machine Learning Case Study for AI-empowered echocardiography of 
           Intensive Care Unit Patients in low- and middle-income countries},
  doi = {10.48550/ARXIV.2212.14510},
  url = {https://arxiv.org/abs/2212.14510},
  keywords = {Medical Physics (physics.med-ph), 
	      Machine Learning (cs.LG), 
	      Image and Video Processing (eess.IV), 
	      FOS: Physical sciences, 
              FOS: Physical sciences, 
	      FOS: Computer and information sciences, 
	      FOS: Electrical engineering, electronic engineering, information engineering},
  publisher = {arXiv},
  year = {2022},
  copyright = {Creative Commons Attribution 4.0 International}
}
```


## Clone repo
After generating your SSH keys as suggested [here](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
You can then clone the repository in the suggested path by typing (or copying) the following lines in a terminal:
```
mkdir -p $HOME/repositories/vital-ultrasound  && cd $HOME/repositories/vital-ultrasound
git clone git@github.com:vital-ultrasound/preprint2023.git

```

## Workflow 
See [README](abstract/workflow-paper/README.md) for detailed instructions on a workflow for build the TeX-based paper in your local machine or with the CI build.

## Contact and issues
Please [open an issue](https://github.com/vital-ultrasound/ml4h/issues) for issues and questions and tag [@mxochicale](https://github.com/mxochicale) for further questions.
