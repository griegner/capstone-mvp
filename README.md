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
The first step for both projects is to download the respective dataset and write a basic description -- experimental design, preprocessing steps that have been applied, etc. 

1. Functional connectivity project:  
We can start with the resting state fMRI from the Human Connectome project. [Here](https://pmc.ncbi.nlm.nih.gov/articles/PMC3724347/) is a paper describing the project. For our purposes, we can just refer to [this](https://www.humanconnectome.org/storage/app/media/documentation/s1200/HCP1200-DenseConnectome+PTN+Appendix-July2017.pdf) short data description, which also has download instructions. This will require you to make an account on their [database]( https://db.humanconnectome.org/app/template/Login.vm;jsessionid=67A8B8766DEEA4CF0597C483C9203BE2). Please note that we don’t need to download the volumetric brain images, only the node timeseries for individual subjects. The end goal here would be to estimate a pairwise correlation matrix between every pair of nodes/regions. 

2. Statistical inference project:  
For the visual working memory dataset it would be helpful to know if the BIDS dataset has been preprocessed and by which software. Then we can describe the experimental design that was used and how we'd create an subject-level model of it. The end goal here would be to estimate an activate map corresponding to the task/stimulus of interest. 

**w04 (23 OCT): dataset description**  
The first task for both projects is to download the respective datasets and provide a short description, including information on the experimental design, preprocessing steps (if applicable), and any relevant data characteristics. 

*Functional connectivity project*:  
For this project, we will use the resting fMRI data from the Human Connectome Project (HCP). A comprehensive description of the project can be found in [this paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC3724347/). However, for our immediate needs, you can refer to the [resting fMRI description](https://www.humanconnectome.org/storage/app/media/documentation/s1200/HCP1200-DenseConnectome+PTN+Appendix-July2017.pdf). Note that you will need to create an account on the [HCP database](https://db.humanconnectome.org/app/template/Login.vm;jsessionid=67A8B8766DEEA4CF0597C483C9203BE2) to access the data. To start, you only need to download the node timeseries data for individual subjects, not the full volumetric brain images. The goal here is to compute a pairwise correlation matrix that captures the functional connectivity between each pair of brain regions/nodes.

*Statistical inference project*:  
For the visual working memory task, it is important to determine if the BIDS (Brain Imaging Data Structure) dataset has been preprocessed and to identify the software used for preprocessing (e.g., fMRIPrep, FSL). Once we have this information, we can describe the experimental design that was followed during data collection and define a subject-level model of the task. The goal here is to estimate a statistical map that reflects brain activity associated with the specific memory task.