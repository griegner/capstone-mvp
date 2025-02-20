## capstone-mvp
> DSC 180AB: multivariate prediction from human brain functional MRI data

### Description
Multivariate prediction from functional MRI is a technique for understanding how brain activation patterns map to thoughts or experiences, akin to mind reading. Instead of analyzing brain regions in isolation, this approach considers how joint patterns of activity distributed across the brain can predict psychological or clinical outcomes. In this capstone project, we will learn how to 1) work with neuroimaging data in Python, 2) select informative features, and 3) train models using supervised machine learning. We will focus on interpretability and think about how the model parameters might help us better understand the relationship between brain structure and function.

### Mentors
Armin Schwartzman, Professor: armins@ucsd.edu  
Gabriel Riegner, PhD student: gariegner@ucsd.edu

### Schedule
**Section A05**: Wednesdays 3:30-4:30PM @ HDSI 336

**w01 (02 OCT): introduction and image processing basics**
1. [Handbook of fMRI](https://www.cs.mtsu.edu/~xyang/fMRIHandBook.pdf): chapters 1.1, 1.2, 1.3, 1.4, 1.7, 1.8; 2.1, 2.2

**w02 (09 OCT): image processing basics using nilearn**
1. [3D and 4D niimgs: handling and visualizing](https://nilearn.github.io/stable/auto_examples/00_tutorials/plot_3d_and_4d_niimg.html#sphx-glr-auto-examples-00-tutorials-plot-3d-and-4d-niimg-py)
2. [Basic nilearn example: manipulating and looking at data](https://nilearn.github.io/stable/auto_examples/00_tutorials/plot_nilearn_101.html#basic-nilearn-example-manipulating-and-looking-at-data)
3. [Plotting tools in nilearn](https://nilearn.github.io/stable/auto_examples/01_plotting/plot_demo_plotting.html)

**w03 (16 OCT): statistical inference, modeling brain connectivity, multivariate prediction**  
Figure out which of these three analysis areas you are most interested in / most comfortable with.
1. [Handbook of fMRI](https://www.cs.mtsu.edu/~xyang/fMRIHandBook.pdf): chapters 6, 7, 8, 9
2. [Statistical inference example](https://nilearn.github.io/stable/auto_examples/04_glm_first_level/plot_bids_features.html)
3. [Brain connectivity example](https://nilearn.github.io/stable/auto_examples/03_connectivity/plot_sphere_based_connectome.html)
4. [Multivariate prediction example](https://nilearn.github.io/stable/auto_examples/00_tutorials/plot_decoding_tutorial.html#sphx-glr-auto-examples-00-tutorials-plot-decoding-tutorial-py)

**w04 (23 OCT): dataset description**  
The first task for both projects is to download the respective datasets and provide a short description, including information on the experimental design, preprocessing steps (if applicable), and any relevant data characteristics. 

*Functional connectivity project*:  
For this project, we will use the resting fMRI data from the Human Connectome Project (HCP). A comprehensive description of the project can be found in [this paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC3724347/). However, for our immediate needs, you can refer to the [resting fMRI description](https://www.humanconnectome.org/storage/app/media/documentation/s1200/HCP1200-DenseConnectome+PTN+Appendix-July2017.pdf). Note that you will need to create an account on the [HCP database](https://db.humanconnectome.org/app/template/Login.vm;jsessionid=67A8B8766DEEA4CF0597C483C9203BE2) to access the data. To start, you only need to download the node timeseries data for individual subjects, not the full volumetric brain images. The goal here is to compute a pairwise correlation matrix that captures the functional connectivity between each pair of brain regions/nodes.

*Statistical inference project*:  
For the visual working memory task, it is important to determine if the BIDS (Brain Imaging Data Structure) dataset has been preprocessed and to identify the software used for preprocessing (e.g., fMRIPrep, FSL). Once we have this information, we can describe the experimental design that was followed during data collection and define a subject-level model of the task. The goal here is to estimate a statistical map that reflects brain activity associated with the specific memory task.

**w05 (30 OCT): references for next steps**

*Functional connectivity project*:  
1. I added a [notebook](notebooks/nregions-100_hcp.ipynb) on different ways to visualize the HCP atlases/parcellations. 
2. Nilearn's [connectome](https://nilearn.github.io/stable/modules/connectome.html) API has a few methods for computing functional connectivity over multiple subjects -- see `ConnectivityMeasure(kind='tangent')` and `GroupSparseCovariance()`. These may be interesting to exlpore for group-level modeling.


*Statistical inference project*:  
1. [Here](https://nilearn.github.io/stable/auto_examples/04_glm_first_level/plot_design_matrix.html#examples-of-design-matrices) are some examples of different design matrices. You can use the [make_first_level_design_matrix()](https://nilearn.github.io/stable/modules/generated/nilearn.glm.first_level.make_first_level_design_matrix.html#nilearn.glm.first_level.make_first_level_design_matrix) function to create a design matrix from the `*events.tsv` files in your BIDS dataset.
2. The tutorial [here](https://nilearn.github.io/stable/glm/glm_intro.html) is more general but provides some useful intuitions.

**w06 (06 NOV): references for next steps**

*Functional connectivity project*:  
1. I added a [notebook](notebooks/nregions-100_atlasreader.ipynb) to map each ICA component (from the HCP atlas) to a named brain region (from a reference atlas). These labels can be passed to [nilearn.plotting.plot_matrix](https://nilearn.github.io/dev/modules/generated/nilearn.plotting.plot_matrix.html#nilearn.plotting.plot_matrix)

*Statistical inference project*:  
1. Here's an [example notebook](https://nilearn.github.io/dev/auto_examples/04_glm_first_level/plot_spm_multimodal_faces.html) that is quite similar to your setting. The estimator you want to use is the [nilearn.glm.first_level.FirstLevelModel](https://nilearn.github.io/dev/modules/generated/nilearn.glm.first_level.FirstLevelModel.html#nilearn.glm.first_level.FirstLevelModel).

**w07 (13 NOV): brain images from CFMRI tour**  

The brain images (anatomical and functional) from the tour are in the `cfmri/` folder.

**w08 (20 NOV): references for next steps**

*Functional connectivity project*:
1. For plotting functions you can use [plot_matrix()](https://nilearn.github.io/stable/modules/generated/nilearn.plotting.plot_matrix.html#nilearn.plotting.plot_matrix) with the 'reorder' argument to organize the correlation matrix into blocks of clusters. Also, [view_connectome()](https://nilearn.github.io/stable/modules/generated/nilearn.plotting.view_connectome.html#nilearn.plotting.view_connectome) plots the edges on a glass brain using a plotly backend.

*Statistical inference project*:  
1. For preprocessing the fMRI dataset in BIDS format, we can use [fMRIPrep](https://fmriprep.org/en/stable/index.html#) which requires ~16 CPU + 8GB RAM + 200GB disk storage. 

**w09 (27 NOV): references for next steps**

*Functional Connectivity project*
1. Covariates for each subject are at [ConnetomeDB](https://db.humanconnectome.org) -> 'WU-Minn HCP Data - 1200 Subjects' -> 'Behavioral Data'

*Statistical inference project*
1. You can generate coordinate tables and region labels from statistical MRI maps using [atlasreader](https://github.com/miykael/atlasreader). 

```
pip install atlasreader
```

```python
from atlasreader import create_output
stats_map = ... # variable storing the stats map nifti object
create_output(stats_map, cluster_extent=10) # saves info on each spatial cluster
```

**WI25 (08 JAN - 14 MAR)**  

Working with fMRI data preprocessed with [fMRIPrep](https://fmriprep.org/en/stable/index.html).

*Project using resting-state fMRI*  
1. See [fmriprep/sub-00_*](./fmriprep/) for the resting-state data we collected at CFMRI, which includes preprocessed images in MNI space and precomputed confounds. These confounds aim to mitigate the effects of non-neural signals (head motion, respiratory/cardiac effects, and scanner noise) on functional connectivity.
2. From these files, you can estimate a pairwise correlation matrix by following this [example notebook](./notebooks/fmriprep-rest-example.ipynb).

*Project using task fMRI*  
1. See [fmriprep/sub-208_*](./fmriprep/) for an example run from the preprocessed colorwheel task. For a first-level analysis, you will need three files: (1) '\*_desc-confounds_timeseries.tsv' which are used to mitigate the effects of non-neural signals, (2) '\*_events.tsv' which include the onsets/durations of the colorwheel task, and (3) '\*_desc-preproc_bold.nii.gz' which are the preprocessed images in MNI space.
2. From these files, you can fit a first-level GLM following this [example notebook](./notebooks/fmriprep-task-example.ipynb)