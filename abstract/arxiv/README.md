# arXiv submission
## Steps for arxiv preparation
1. Edit paths and image files in `A_copy-tex-figures.bash`

2. Run script to copy tex files and images to arxiv/files path
```
bash A_copy-tex-figures.bash
```
	2.1 Also copy relevant `*.cls` files

3. edit paths for figures in `file\main.tex` as follows
```
%\graphicspath{{../figures}} %goes to path: figures/
\includegraphics[width=\textwidth]{drawing-v01.png}
\includegraphics[width=\linewidth]{drawing-v00.png}
\bibliography{../../references/references}
```

4. compile `main.tex` file
```
cd files/
bash ../B_pdflatex-bibtex.bash
```
Check that reference were appropietely called `evince main.pdf`

	4.1 edit reference section as follows
	```
	%%\bibliography{../references/references}
	\input{main.bbl} %% uncomment for arxiv version
	```

	4.2 compile `main.tex`
	```
	cd files/
	bash ../C_pdflatex-pdflatex.bash
	```

	4.3 check pdf 
	```
	cd files/
	evince main.pdf
	```

	4.4 clean project 
	```
	cd files/
	bash ../D_clean-tex-project.bash
	```

5. compress it as zip 
```
cd ../
bash E_zip_files.bash v00
bash E_zip_files.bash v01
```

:tada: zip is ready to be submitted in arXiv


6. CI-PDF Optional 
Create files and edit bib path file
```
cp -r files files-for-ci-pdf
cd files-for-ci-pdf
vim main.tex ## change path for \bibliography
```
Amend yml, adding branch and change relevant paths and filenames for tex and pdf
```
vim .github/workflows/citex.yml
```

## Submission

1. Go to arxiv and START NEW SUBMISSION with the above zip file
	* Primary classification for submission
	* title
	* author list: : (First names first; do not use et al.; separate with commas or 'and'; Review author requirements)
	* abstract.
	* Add other cathegories:
		Medical Physics (physics.med-ph)   
		Artificial Intelligence (cs.AI)    Remove
		Hardware Architecture (cs.AR)    Remove
		Machine Learning (cs.LG)    Remove
		Image and Video Processing (eess.IV) 

More for metadata: https://arxiv.org/help/prep#title

See [Submission Log](SubmissionLog.md) for further deteails.
