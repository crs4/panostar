<img src="assets/logo.png" align="right" width="180" alt="Project Logo">

# State-of-the-art in deep learning approaches for automatic single-panorama indoor modeling and exploration [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

### Authors

* **Giovanni Pintore** *CRS4, Italy* [![ORCID](https://img.shields.io/badge/ORCID-0000--0001--8944--1045-green)](https://orcid.org/0000-0001-8944-1045)
* **Marco Agus** *HBKU, Qatar* [![ORCID](https://img.shields.io/badge/ORCID-0000--0003--2752--3525-green)](https://orcid.org/0000-0003-2752-3525)
* **Jens Schneider** *HBKU, Qatar* [![ORCID](https://img.shields.io/badge/ORCID-0000--0002--0546--2816-green)](https://orcid.org/0000-0002-0546-2816)
* **Enrico Gobbetti** *CRS4, Italy* [![ORCID](https://img.shields.io/badge/ORCID-0000--0003--0831--2458-green)](https://orcid.org/0000-0003-0831-2458)

<br clear="right"/>

### Abstract
A single surround-view panoramic image provides complete coverage of the environment visible from a single viewpoint and inherently supports dynamic exploration, especially when viewed through a head-mounted display. For these reasons, single or linked 360-degree panoramas have become a widely adopted modality for indoor scene acquisition and virtual tour creation. Despite their popularity, panoramas present inherent limitations: they statically represent the captured scene, do not provide an explicit 3D architectural structure or geometry, and exhibit minimal parallax due to their single viewpoint. These limitations restrict their applicability and often require significant modeling efforts to generate missing data. In our survey, we provided an up-to-date, integrative overview of recent techniques to address these challenges, bringing together complementary perspectives from machine learning, computer vision, and computer graphics. 

> **Note:** This repository accompanies our survey published in Computer Graphics Forum and presented at [Eurographics 2026](https://eg2026.github.io/). It provides direct links to relevant works, organized by topic. We will strive to keep this repository updated also after the survey publication.

---

### How to Cite

If you find this survey or the organized repository helpful for your research, please cite our work as follows:

**APA:**
> Pintore, G., Agus, M., Schneider, J., & Gobbetti, E. (2026). State-of-the-art in deep learning approaches for automatic single-panorama indoor modeling and exploration. *Computer Graphics Forum*, 45(2), doi: 10.1111/cgf.70396

**BibTeX:**
```bibtex
@article{Pintore:2026:SDL,
  title={State-of-the-art in deep learning approaches for automatic single-panorama indoor modeling and exploration,
  author={Giovanni Pintore and Marco Agus and Jens Schneider and Enrico Gobbetti},
  journal={Computer Graphics Forum},
  volume={45},
  number={2},
  pages={1},
  year={2026},
  doi={10.1111/cgf.70396}
}
```
---

### Acknowledgments

This work was supported by NPRP-S 14th Cycle grant 0403-210132 AIN2 from the Qatar National Research
Fund (a member of Qatar Foundation) and by the Sardinian Regional Authorities under the project XDATA (Art9 LR 20/2015).

---





<a name="table-of-contents"></a>

## Table of Contents

* [Related surveys](#related-surveys)
* [Background](#background)
  * [360-degree image capture and processing representation](#360-degree-image-capture-and-processing-representation)
  * [Gravity alignment](#gravity-alignment)
  * [Architectural and data-driven priors](#architectural-and-data-driven-priors)
  * [Open research data](#open-research-data)
* [Automatic geometric and structural modeling](#automatic-geometric-and-structural-modeling)
  * [Depth and other pixel-wise information inference](#depth-and-other-pixel-wise-information-inference)
  * [Single-image room layout estimation](#single-image-room-layout-estimation)
  * [Positioning and connecting single rooms](#positioning-and-connecting-single-rooms)
* [Novel view synthesis and immersive model exploration](#novel-view-synthesis-and-immersive-model-exploration)
  * [View synthesis from a single panorama](#view-synthesis-from-a-single-panorama)
  * [Dynamic modifications](#dynamic-modifications)
  * [View synthesis](#view-synthesis)
  * [Exploration](#exploration)
* [Emerging pre-trained and foundation models](#emerging-pre-trained-and-foundation-models)
  * [Transfer and composition of conventional vision foundation models for 360-degree tasks](#transfer-and-composition-of-conventional-vision-foundation-models-for-360-degree-tasks)
  * [Native 360-degree foundation models](#native-360-degree-foundation-models)
  * [Opportunities and Limitations](#opportunities-and-limitations)
* [Applications](#applications)

---

## Related surveys
Our work examines methods for automatically transforming indoor panoramic shots into representations that support structural and geometric recovery, dynamic exploration, and basic editing. Our focus lies on techniques that operate mostly from asingle panoramic image, covering both analysis (for model reconstruction) and synthesis (for immersive viewing, navigation, and editing). Several other surveys provide complementary information. We list here relevant works.


**References:**

\[1\] H. Ai, Z. Cao, and L. Wang, "A Survey of Representation Learning, Optimization
Strategies, and Applications for Omnidirectional
Vision," *Int J Comput Vis*, 2025, doi: [10.1007/s11263-025-02391-w](https://doi.org/10.1007/s11263-025-02391-w).
<br>

\[2\] T. L. da Silveira, P. G. Pinto, J. Murrugarra-Llerena, and C. R. Jung, "3D scene geometry estimation from 360°
imagery: A survey," *ACM Computing Surveys*, 2022, doi: [10.1145/3519021](https://doi.org/10.1145/3519021).
<br>

\[3\] S. Gao, K. Yang, H. Shi, K. Wang, and J. Bai, "Review on Panoramic Imaging and Its Applications in
Scene Understanding," *IEEE TIM*, 2022, doi: [10.1109/TIM.2022.3216675](https://doi.org/10.1109/TIM.2022.3216675).
<br>

\[4\] J. Li, W. Gao, Y. Wu, Y. Liu, and Y. Shen, "High-quality indoor scene 3D reconstruction with
RGB-D cameras: A brief review," *Computational Visual Media*, 2022, doi: [10.1007/s41095-021-0250-8](https://doi.org/10.1007/s41095-021-0250-8).
<br>

\[5\] M. Meng, Y. Zhu, Y. Zhao, Z. Li, and Z. Zhu, "3D Indoor Scene Geometry Estimation from a Single
Omnidirectional Image: A Comprehensive Survey," *Computational Visual Media*, 2025, doi: [10.26599/CVM.2025.9450438](https://doi.org/10.26599/CVM.2025.9450438).
<br>

\[6\] A. G. Patil, S. G. Patil, M. Li, M. Fisher, M. Savva, and H. Zhang, "Advances in Data-Driven Analysis and Synthesis of
3D Indoor Scenes," *Computer Graphics Forum*, 2024, doi: [10.1111/cgf.14927](https://doi.org/10.1111/cgf.14927).
<br>

\[7\] G. Pintore, C. Mura, F. Ganovelli, L. Fuentes-Perez, R. Pajarola, and E. Gobbetti, "State-of-the-art in Automatic 3D Reconstruction of
Structured Indoor Environments," *Comput. Graph. Forum*, 2020, doi: [10.1111/cgf.14021](https://doi.org/10.1111/cgf.14021).
<br>

\[8\] M. Tukur, S. Jashari, M. Alzubaidi, B. A. Salami, Y. Boraey, S. Yong, D. Saleh, G. Pintore, E. Gobbetti, J. Schneider, N. Fetais, and M. Agus, "Panoramic Imaging in Immersive Extended Reality: A
Scoping Review of Technologies, Applications,
Perceptual Studies, and User Experience Challenges," *Frontiers in Virtual Reality*, 2025, doi: [10.3389/frvir.2025.1622605](https://doi.org/10.3389/frvir.2025.1622605).
<br>

\[9\] H. Wang and M. Li, "A new era of indoor scene reconstruction: A survey," *IEEE Access*, 2024, doi: [10.1109/ACCESS.2024.3440260](https://doi.org/10.1109/ACCESS.2024.3440260).
<br>

\[10\] J. Yu, A. C. P. Grassi, and G. Hirtz, "Applications of Deep Learning for Top-View
Omnidirectional Imaging: A Survey," *Proc. CVPRW*, 2023, doi: [10.1109/CVPRW59228.2023.00683](https://doi.org/10.1109/CVPRW59228.2023.00683).
<br>

\[11\] J. Zhu, C. Gao, Q. Sun, M. Wang, and Z. Deng, "A survey of indoor 3D reconstruction based on
RGB-D cameras," *IEEE Access*, 2024, doi: [10.1109/ACCESS.2024.3443065](https://doi.org/10.1109/ACCESS.2024.3443065).
<br>

\[12\] M. Zollhöfer, P. Stotko, A. Görlitz, C. Theobalt, M. Niessner, R. Klein, and A. Kolb, "State-of-the-art on 3D reconstruction with RGB-D
cameras," *Computer graphics forum*, 2018, doi: [10.1111/cgf.13386](https://doi.org/10.1111/cgf.13386).
<br>

\[13\] C. Zou, J. W. Su, C. H. Peng, A. Colburn, Q. Shan, P. Wonka, H. K. Chu, and D. Hoiem, "Manhattan Room Layout Reconstruction from a Single
360 Image: A Comparative Study of State-of-the-Art
Methods," *International Journal of Computer Vision*, 2021, doi: [10.1007/s11263-020-01426-8](https://doi.org/10.1007/s11263-020-01426-8).
<br>


[↑ Back to Top](#table-of-contents)

---

## Background
In addition to reviewing state-of-the-art methods, we outline key background concepts, including omnidirectional representations, gravity alignment, architectural priors, and major datasets supporting 360-degree indoor research.


[↑ Back to Top](#table-of-contents)

---

### 360-degree image capture and processing representation



**References:**

\[1\] R. Cabral and Y. Furukawa, "Piecewise Planar and Compact Floorplan Reconstruction
from Images," *Proc. CVPR*, 2014, doi: [10.1109/CVPR.2014.546](https://doi.org/10.1109/CVPR.2014.546).
<br>

\[2\] M. L. Champel, R. Doré, and N. Mollet, "Key factors for a high-quality VR experience," *Applications of Digital Image Processing XL*, 2017, doi: [10.1117/12.2274336](https://doi.org/10.1117/12.2274336).
<br>

\[3\] J. M. Coughlan and A. L. Yuille, "Manhattan World: Compass direction from a single
image by Bayesian inference," *Proc. ICCV*, 1999, doi: [10.1109/ICCV.1999.790349](https://doi.org/10.1109/ICCV.1999.790349).
<br>

\[4\] T. L. da Silveira, P. G. Pinto, J. Murrugarra-Llerena, and C. R. Jung, "3D scene geometry estimation from 360°
imagery: A survey," *ACM Computing Surveys*, 2022, doi: [10.1145/3519021](https://doi.org/10.1145/3519021).
<br>

\[5\] E. Delage, H. Lee, and A. Y. Ng, "A Dynamic Bayesian Network Model for Autonomous
3D Reconstruction from a Single Indoor Image," *Proc. CVPR*, 2006, doi: [10.1109/CVPR.2006.23](https://doi.org/10.1109/CVPR.2006.23).
<br>

\[6\] M. Eder, M. Shvets, J. Lim, and J. M. Frahm, "Tangent Images for Mitigating Spherical Distortion," *Proc. CVPR*, 2020, doi: [10.1109/CVPR42600.2020.01244](https://doi.org/10.1109/CVPR42600.2020.01244).
<br>

\[7\] Y. Furukawa, B. Curless, S. M. Seitz, and R. Szeliski, "Reconstructing building interiors from images," *Proc. ICCV*, 2009, doi: [10.1109/ICCV.2009.5459145](https://doi.org/10.1109/ICCV.2009.5459145).
<br>

\[8\] C. Godard, O. M. Aodha, and G. J. Brostow, "Unsupervised Monocular Depth Estimation with
Left-Right Consistency," *Proc. CVPR*, 2017, doi: [10.1109/CVPR.2017.699](https://doi.org/10.1109/CVPR.2017.699).
<br>

\[9\] V. Hedau, D. Hoiem, and D. Forsyth, "Recovering the spatial layout of cluttered rooms," *Proc. ICCV*, 2009, doi: [10.1109/ICCV.2009.5459411](https://doi.org/10.1109/ICCV.2009.5459411).
<br>

\[10\] J. Huang, Z. Chen, D. Ceylan, and H. Jin, "6-DOF VR videos with a single 360-camera," *Proc. IEEE VR*, 2017, doi: [10.1109/VR.2017.7892229](https://doi.org/10.1109/VR.2017.7892229).
<br>

\[11\] S. Im, H. Ha, F. Rameau, H. G. Jeon, G. Choe, and I. S. Kweon, "All-Around Depth from Small Motion with a Spherical
Panoramic Camera," *Proc. ECCV*, 2016, doi: [10.1007/978-3-319-46487-9_10](https://doi.org/10.1007/978-3-319-46487-9_10).
<br>

\[12\] T. Jokela, J. Ojala, and K. Väänänen, "How people use 360-degree cameras," *Proc. International Conference on Mobile and
Ubiquitous Multimedia*, 2019, doi: [10.1145/3365610.3365645](https://doi.org/10.1145/3365610.3365645).
<br>

\[13\] D. C. Lee, M. Hebert, and T. Kanade, "Geometric reasoning for single image structure
recovery," *Proc. CVPR*, 2009, doi: [10.1109/CVPR.2009.5206872](https://doi.org/10.1109/CVPR.2009.5206872).
<br>

\[14\] G. Pintore, F. Ganovelli, R. Pintus, R. Scopigno, and E. Gobbetti, "3D floor plan recovery from overlapping spherical
images," *Computational Visual Media*, 2018, doi: [10.1007/s41095-018-0125-9](https://doi.org/10.1007/s41095-018-0125-9).
<br>

\[15\] G. Pintore, R. Pintus, F. Ganovelli, R. Scopigno, and E. Gobbetti, "Recovering 3D existing-conditions of indoor
structures from spherical images," *Computers \& Graphics*, 2018, doi: [10.1016/j.cag.2018.09.013](https://doi.org/10.1016/j.cag.2018.09.013).
<br>

\[16\] G. Pintore, C. Mura, F. Ganovelli, L. Fuentes-Perez, R. Pajarola, and E. Gobbetti, "State-of-the-art in Automatic 3D Reconstruction of
Structured Indoor Environments," *Comput. Graph. Forum*, 2020, doi: [10.1111/cgf.14021](https://doi.org/10.1111/cgf.14021).
<br>

\[17\] G. Pintore, E. Almansa, M. Agus, and E. Gobbetti, "Deep3DLayout: 3D Reconstruction of an Indoor
Layout from a Spherical Panoramic Image," *ACM TOG*, 2021, doi: [10.1145/3478513.3480480](https://doi.org/10.1145/3478513.3480480).
<br>

\[18\] M. Rey-Area, M. Yuan, and C. Richardt, "360MonoDepth: High-Resolution 360° Monocular
Depth Estimation," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.00374](https://doi.org/10.1109/CVPR52688.2022.00374).
<br>

\[19\] G. Schindler and F. Dellaert, "Atlanta world: an expectation maximization
framework for simultaneous low-level edge grouping
and camera calibration in complex man-made
environments," *Proc. CVPR*, 2004, doi: [10.1109/CVPR.2004.1315033](https://doi.org/10.1109/CVPR.2004.1315033).
<br>


[↑ Back to Top](#table-of-contents)

---

### Gravity alignment



**References:**

\[1\] B. Davidson, M. S. Alvi, and J. F. H. Henriques, "360 Camera Alignment via Segmentation," *Proc. ECCV*, 2020, doi: [10.1007/978-3-030-58604-1_35](https://doi.org/10.1007/978-3-030-58604-1_35).
<br>

\[2\] R. Jung, A. S. J. Lee, A. Ashtari, and J. Bazin, "Deep360Up: A Deep Learning-Based Approach for
Automatic VR Image Upright Adjustment," *Proc. IEEE VR*, 2019, doi: [10.1109/VR.2019.8798326](https://doi.org/10.1109/VR.2019.8798326).
<br>

\[3\] G. Pintore, M. Agus, E. Almansa, J. Schneider, and E. Gobbetti, "SliceNet: deep dense depth estimation from a single
indoor panorama using a slice-based representation," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.01137](https://doi.org/10.1109/CVPR46437.2021.01137).
<br>

\[4\] W. Xian, Z. Li, M. Fisher, J. Eisenmann, E. Shechtman, and N. Snavely, "UprightNet: geometry-aware camera orientation
estimation from single images," *Proc. ICCV*, 2019, doi: [10.1109/ICCV.2019.01007](https://doi.org/10.1109/ICCV.2019.01007).
<br>


[↑ Back to Top](#table-of-contents)

---

### Architectural and data-driven priors



**References:**

\[1\] M. Berger, A. Tagliasacchi, L. M. Seversky, P. Alliez, G. Guennebaud, J. A. Levine, A. Sharf, and C. T. Silva, "A Survey of Surface Reconstruction from Point Clouds," *Computer Graphics Forum*, 2017, doi: [10.1111/cgf.12802](https://doi.org/10.1111/cgf.12802).
<br>

\[2\] J. M. Coughlan and A. L. Yuille, "Manhattan World: Compass direction from a single
image by Bayesian inference," *Proc. ICCV*, 1999, doi: [10.1109/ICCV.1999.790349](https://doi.org/10.1109/ICCV.1999.790349).
<br>

\[3\] Stanford-University, "BuildingParser Dataset," *Public dataset*, 2017, url: [https://sdss.redivis.com/datasets/9q3m-9w5pa1a2h](https://sdss.redivis.com/datasets/9q3m-9w5pa1a2h).
<br>

\[4\] M. Rey-Area, M. Yuan, and C. Richardt, "360MonoDepth Matterport3D," *Public dataset*, 2022, url: [https://researchdata.bath.ac.uk/1126/](https://researchdata.bath.ac.uk/1126/).
<br>

\[5\] M. Rey-Area, M. Yuan, and C. Richardt, "360MonoDepth Replica," *Public dataset*, 2022, url: [https://manurare.github.io/360monodepth/](https://manurare.github.io/360monodepth/).
<br>

\[6\] I. Armeni, Z. Y. He, J. Gwak, A. R. Zamir, M. Fischer, J. Malik, and S. Savarese, "The 3DSceneGraph Dataset," *Public dataset*, 2019, url: [https://github.com/StanfordVL/3DSceneGraph/](https://github.com/StanfordVL/3DSceneGraph/).
<br>

\[7\] Z. Li, L. Wang, X. Huang, C. Pan, and J. Yang, "FutureHouse Dataset," *Public dataset*, 2022, url: [https://github.com/LZleejean/FutureHouse](https://github.com/LZleejean/FutureHouse).
<br>

\[8\] F. Xia, A. R. Zamir, Z. He, A. Sax, J. Malik, and S. Savarese, "GibsonV2," *Public dataset*, 2018, url: [https://github.com/StanfordVL/GibsonEnv/tree/master/gibson/data](https://github.com/StanfordVL/GibsonEnv/tree/master/gibson/data).
<br>

\[9\] Matterport, "Matterport3D," *Public dataset*, 2017, url: [https://github.com/niessner/Matterport](https://github.com/niessner/Matterport).
<br>

\[10\] C. Zou, J. W. Su, C. H. Peng, A. Colburn, Q. Shan, P. Wonka, H. K. Chu, and D. Hoiem, "MatterportLayout," *Public dataset*, 2017, url: [https://github.com/ericsujw/Matterport3DLayoutAnnotation](https://github.com/ericsujw/Matterport3DLayoutAnnotation).
<br>

\[11\] G. Albanis, N. Zioulis, P. Drakoulis, V. Gkitsas, V. Sterzentsenko, F. Alvarez, D. Zarpalas, and P. Daras, "Pano3D," *Public dataset*, 2021, url: [https://vcl3d.github.io/Pano3D/download/](https://vcl3d.github.io/Pano3D/download/).
<br>

\[12\] Y. Zhang, S. Song, P. Tan, and J. Xiao, "PanoContext dataset," *Public dataset*, 2014, url: [https://panocontext.cs.princeton.edu/](https://panocontext.cs.princeton.edu/).
<br>

\[13\] M. Khan, J. Abu-Khalaf, and D. Suter, "PanoSCU Dataset," *Public dataset*, 2025, url: [https://doi.org/10.25958/4p6j-z657](https://doi.org/10.25958/4p6j-z657).
<br>

\[14\] J. Xu, J. Zheng, Y. Xu, R. Tang, and S. Gao, "PNVS Dataset," *Public dataset*, 2021, url: [https://github.com/bluestyle97/PNVS](https://github.com/bluestyle97/PNVS).
<br>

\[15\] ShanghaiTech-University and Kujiale-com, "Shanghaitech-Kujiale Indoor 360° (SKI360)
dataset," *Public dataset*, 2020, url: [https://svip-lab.github.io/dataset/indoor_360.html](https://svip-lab.github.io/dataset/indoor_360.html).
<br>

\[16\] J. Zheng, J. Zhang, J. Li, R. Tang, S. Gao, and Z. Zhou, "Indoor3Dmapping dataset," *Public dataset*, 2020, url: [https://structured3d-dataset.org/](https://structured3d-dataset.org/).
<br>

\[17\] S. Cruz, W. Hutchcroft, Y. Li, N. Khosravan, I. Boyadzhiev, and S. B. Kang, "Zillow Indoor Dataset (ZInD)," *Public dataset*, 2021, url: [https://github.com/zillow/zind](https://github.com/zillow/zind).
<br>

\[18\] T. Deb, L. Wang, Z. Bessinger, N. Khosravan, E. Penner, and S. B. Kang, "ZInD-Tell Dataset," *Public dataset*, 2024, url: [https://github.com/zillow/zindtell](https://github.com/zillow/zindtell).
<br>

\[19\] E. Delage, H. Lee, and A. Y. Ng, "A Dynamic Bayesian Network Model for Autonomous
3D Reconstruction from a Single Indoor Image," *Proc. CVPR*, 2006, doi: [10.1109/CVPR.2006.23](https://doi.org/10.1109/CVPR.2006.23).
<br>

\[20\] Y. Furukawa, B. Curless, S. M. Seitz, and R. Szeliski, "Reconstructing building interiors from images," *Proc. ICCV*, 2009, doi: [10.1109/ICCV.2009.5459145](https://doi.org/10.1109/ICCV.2009.5459145).
<br>

\[21\] V. Hedau, D. Hoiem, and D. Forsyth, "Recovering the spatial layout of cluttered rooms," *Proc. ICCV*, 2009, doi: [10.1109/ICCV.2009.5459411](https://doi.org/10.1109/ICCV.2009.5459411).
<br>

\[22\] D. C. Lee, M. Hebert, and T. Kanade, "Geometric reasoning for single image structure
recovery," *Proc. CVPR*, 2009, doi: [10.1109/CVPR.2009.5206872](https://doi.org/10.1109/CVPR.2009.5206872).
<br>

\[23\] G. Pintore, F. Ganovelli, R. Pintus, R. Scopigno, and E. Gobbetti, "3D floor plan recovery from overlapping spherical
images," *Computational Visual Media*, 2018, doi: [10.1007/s41095-018-0125-9](https://doi.org/10.1007/s41095-018-0125-9).
<br>

\[24\] G. Pintore, C. Mura, F. Ganovelli, L. Fuentes-Perez, R. Pajarola, and E. Gobbetti, "State-of-the-art in Automatic 3D Reconstruction of
Structured Indoor Environments," *Comput. Graph. Forum*, 2020, doi: [10.1111/cgf.14021](https://doi.org/10.1111/cgf.14021).
<br>

\[25\] G. Pintore, M. Agus, E. Almansa, J. Schneider, and E. Gobbetti, "SliceNet: deep dense depth estimation from a single
indoor panorama using a slice-based representation," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.01137](https://doi.org/10.1109/CVPR46437.2021.01137).
<br>

\[26\] G. Schindler and F. Dellaert, "Atlanta world: an expectation maximization
framework for simultaneous low-level edge grouping
and camera calibration in complex man-made
environments," *Proc. CVPR*, 2004, doi: [10.1109/CVPR.2004.1315033](https://doi.org/10.1109/CVPR.2004.1315033).
<br>

\[27\] J. Xiao, K. A. Ehinger, A. Oliva, and A. Torralba, "Recognizing scene viewpoint using panoramic place
representation," *Proc. CVPR*, 2012, doi: [10.1109/CVPR.2012.6247991](https://doi.org/10.1109/CVPR.2012.6247991).
<br>

\[28\] N. Zioulis, A. Karakottas, D. Zarpalas, and P. Daras, "OmniDepth: Dense Depth Estimation for Indoors
Spherical Panoramas," *Proc. ECCV*, 2018, doi: [10.1007/978-3-030-01231-1_28](https://doi.org/10.1007/978-3-030-01231-1_28).
<br>

\[29\] C. Zou, J. W. Su, C. H. Peng, A. Colburn, Q. Shan, P. Wonka, H. K. Chu, and D. Hoiem, "3D Manhattan Room Layout Reconstruction from a
Single 360 Image," *ArXiv e-print arXiv:1910.04099*, 2019, doi: [10.48550/arXiv.1910.04099](https://doi.org/10.48550/arXiv.1910.04099).
<br>

\[30\] C. Zou, J. W. Su, C. H. Peng, A. Colburn, Q. Shan, P. Wonka, H. K. Chu, and D. Hoiem, "Manhattan Room Layout Reconstruction from a Single
360 Image: A Comparative Study of State-of-the-Art
Methods," *International Journal of Computer Vision*, 2021, doi: [10.1007/s11263-020-01426-8](https://doi.org/10.1007/s11263-020-01426-8).
<br>


[↑ Back to Top](#table-of-contents)

---

### Open research data



**References:**

\[1\] G. Albanis, N. Zioulis, P. Drakoulis, V. Gkitsas, V. Sterzentsenko, F. Alvarez, D. Zarpalas, and P. Daras, "Pano3D: A holistic benchmark and a solid baseline
for 360° depth estimation," *Proc. CVPR Workshops*, 2021, doi: [10.1109/CVPRW53098.2021.00413](https://doi.org/10.1109/CVPRW53098.2021.00413).
<br>

\[2\] I. Armeni, O. Sener, A. R. Zamir, H. Jiang, I. Brilakis, M. Fischer, and S. Savarese, "3D Semantic Parsing of Large-scale Indoor Spaces," *Proc. CVPR*, 2016, doi: [10.1109/CVPR.2016.170](https://doi.org/10.1109/CVPR.2016.170).
<br>

\[3\] I. Armeni, Z. Y. He, J. Gwak, A. R. Zamir, M. Fischer, J. Malik, and S. Savarese, "3D Scene Graph: A structure for unified semantics,
3D space, and camera," *Proc. CVPR*, 2019, doi: [10.1109/ICCV.2019.00576](https://doi.org/10.1109/ICCV.2019.00576).
<br>

\[4\] B. Attal, S. Ling, A. Gokaslan, C. Richardt, and J. Tompkin, "MatryODShka: Real-time 6DoF video view synthesis
using multi-sphere images," *Proc. ECCV*, 2020, doi: [10.1007/978-3-030-58452-8_26](https://doi.org/10.1007/978-3-030-58452-8_26).
<br>

\[5\] A. Chang, A. Dai, T. Funkhouser, M. Halber, M. Niessner, M. Savva, S. Song, A. Zeng, and Y. Zhang, "Matterport3D: Learning from RGB-D Data in Indoor
Environments," *Proc. 3DV*, 2017, doi: [10.1109/3DV.2017.00081](https://doi.org/10.1109/3DV.2017.00081).
<br>

\[6\] S. Cruz, W. Hutchcroft, Y. Li, N. Khosravan, I. Boyadzhiev, and S. B. Kang, "Zillow indoor dataset: Annotated floor plans with
360° panoramas and 3D room layouts," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.00217](https://doi.org/10.1109/CVPR46437.2021.00217).
<br>

\[7\] Stanford-University, "BuildingParser Dataset," *Public dataset*, 2017, url: [https://sdss.redivis.com/datasets/9q3m-9w5pa1a2h](https://sdss.redivis.com/datasets/9q3m-9w5pa1a2h).
<br>

\[8\] M. Rey-Area, M. Yuan, and C. Richardt, "360MonoDepth Matterport3D," *Public dataset*, 2022, url: [https://researchdata.bath.ac.uk/1126/](https://researchdata.bath.ac.uk/1126/).
<br>

\[9\] M. Rey-Area, M. Yuan, and C. Richardt, "360MonoDepth Replica," *Public dataset*, 2022, url: [https://manurare.github.io/360monodepth/](https://manurare.github.io/360monodepth/).
<br>

\[10\] I. Armeni, Z. Y. He, J. Gwak, A. R. Zamir, M. Fischer, J. Malik, and S. Savarese, "The 3DSceneGraph Dataset," *Public dataset*, 2019, url: [https://github.com/StanfordVL/3DSceneGraph/](https://github.com/StanfordVL/3DSceneGraph/).
<br>

\[11\] Z. Li, L. Wang, X. Huang, C. Pan, and J. Yang, "FutureHouse Dataset," *Public dataset*, 2022, url: [https://github.com/LZleejean/FutureHouse](https://github.com/LZleejean/FutureHouse).
<br>

\[12\] F. Xia, A. R. Zamir, Z. He, A. Sax, J. Malik, and S. Savarese, "GibsonV2," *Public dataset*, 2018, url: [https://github.com/StanfordVL/GibsonEnv/tree/master/gibson/data](https://github.com/StanfordVL/GibsonEnv/tree/master/gibson/data).
<br>

\[13\] A. A. Sánchez Alcázar, G. Pintore, and M. Sgrenzaroli, "Indoor3Dmapping dataset," *Public dataset*, 2022, url: [https://doi.org/10.5281/zenodo.6367381](https://doi.org/10.5281/zenodo.6367381).
<br>

\[14\] Matterport, "Matterport3D," *Public dataset*, 2017, url: [https://github.com/niessner/Matterport](https://github.com/niessner/Matterport).
<br>

\[15\] C. Zou, J. W. Su, C. H. Peng, A. Colburn, Q. Shan, P. Wonka, H. K. Chu, and D. Hoiem, "MatterportLayout," *Public dataset*, 2017, url: [https://github.com/ericsujw/Matterport3DLayoutAnnotation](https://github.com/ericsujw/Matterport3DLayoutAnnotation).
<br>

\[16\] G. Albanis, N. Zioulis, P. Drakoulis, V. Gkitsas, V. Sterzentsenko, F. Alvarez, D. Zarpalas, and P. Daras, "Pano3D," *Public dataset*, 2021, url: [https://vcl3d.github.io/Pano3D/download/](https://vcl3d.github.io/Pano3D/download/).
<br>

\[17\] Y. Zhang, S. Song, P. Tan, and J. Xiao, "PanoContext dataset," *Public dataset*, 2014, url: [https://panocontext.cs.princeton.edu/](https://panocontext.cs.princeton.edu/).
<br>

\[18\] M. Khan, J. Abu-Khalaf, and D. Suter, "PanoSCU Dataset," *Public dataset*, 2025, url: [https://doi.org/10.25958/4p6j-z657](https://doi.org/10.25958/4p6j-z657).
<br>

\[19\] J. Xu, J. Zheng, Y. Xu, R. Tang, and S. Gao, "PNVS Dataset," *Public dataset*, 2021, url: [https://github.com/bluestyle97/PNVS](https://github.com/bluestyle97/PNVS).
<br>

\[20\] J. Straub, T. Whelan, L. Ma, Y. Chen, E. Wijmans, S. Green, J. J. Engel, R. Mur-Artal, C. Ren, S. Verma, A. Clarkson, M. Yan, B. Budge, Y. Yan, X. Pan, J. Yon, Y. Zou, K. Leon, N. Carter, J. Briales, T. Gillingham, E. Mueggler, L. Pesqueira, M. Savva, D. Batra, H. M. Strasdat, R. D. Nardi, M. Goesele, S. Lovegrove, and R. Newcombe, "The Replica Dataset," *Public dataset*, 2019, url: [https://github.com/facebookresearch/Replica-Dataset](https://github.com/facebookresearch/Replica-Dataset).
<br>

\[21\] ShanghaiTech-University and Kujiale-com, "Shanghaitech-Kujiale Indoor 360° (SKI360)
dataset," *Public dataset*, 2020, url: [https://svip-lab.github.io/dataset/indoor_360.html](https://svip-lab.github.io/dataset/indoor_360.html).
<br>

\[22\] J. Zheng, J. Zhang, J. Li, R. Tang, S. Gao, and Z. Zhou, "Indoor3Dmapping dataset," *Public dataset*, 2020, url: [https://structured3d-dataset.org/](https://structured3d-dataset.org/).
<br>

\[23\] S. Cruz, W. Hutchcroft, Y. Li, N. Khosravan, I. Boyadzhiev, and S. B. Kang, "Zillow Indoor Dataset (ZInD)," *Public dataset*, 2021, url: [https://github.com/zillow/zind](https://github.com/zillow/zind).
<br>

\[24\] T. Deb, L. Wang, Z. Bessinger, N. Khosravan, E. Penner, and S. B. Kang, "ZInD-Tell Dataset," *Public dataset*, 2024, url: [https://github.com/zillow/zindtell](https://github.com/zillow/zindtell).
<br>

\[25\] T. Deb, L. Wang, Z. Bessinger, N. Khosravan, E. Penner, and S. B. Kang, "ZInD-Tell: Towards Translating Indoor Panoramas
into Descriptions," *Proc. CVPR Workshops*, 2024, doi: [10.1109/CVPRW63382.2024.00210](https://doi.org/10.1109/CVPRW63382.2024.00210).
<br>

\[26\] L. Jin, Y. Xu, J. Zheng, J. Zhang, R. Tang, S. Xu, J. Yu, and S. Gao, "Geometric Structure Based and Regularized Depth
Estimation from 360 Indoor Imagery," *Proc. CVPR*, 2020, doi: [10.1109/CVPR42600.2020.00097](https://doi.org/10.1109/CVPR42600.2020.00097).
<br>

\[27\] M. Khan, Y. Qiu, Y. Cong, J. Abu-Khalaf, D. Suter, and B. Rosenhahn, "PanoSCU: A Simulation-Based Dataset for Panoramic
Indoor Scene Understanding," *IEEE Access*, 2025, doi: [10.1109/ACCESS.2025.3561055](https://doi.org/10.1109/ACCESS.2025.3561055).
<br>

\[28\] E. Kolve, R. Mottaghi, W. Han, E. VanderBilt, L. Weihs, A. Herrasti, M. Deitke, K. Ehsani, D. Gordon, Y. Zhu, A. Kembhavi, A. Gupta, and A. Farhadi, "AI2-THOR: An interactive 3D environment for
visual AI," *arXiv preprint arXiv:1712.05474*, 2017, doi: [10.48550/arXiv.1712.05474](https://doi.org/10.48550/arXiv.1712.05474).
<br>

\[29\] Z. Li, L. Wang, X. Huang, C. Pan, and J. Yang, "PhyIR: Physics-based Inverse Rendering for
Panoramic Indoor Images," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.01238](https://doi.org/10.1109/CVPR52688.2022.01238).
<br>

\[30\] T. Li, Z. Zhang, Y. Wang, Y. Cui, Y. Li, D. Zhou, B. Yin, and X. Yang, "Self-supervised indoor scene point cloud completion
from a single panorama," *The Visual Computer*, 2025, doi: [10.1007/s00371-024-03509-w](https://doi.org/10.1007/s00371-024-03509-w).
<br>

\[31\] P. Moulon, P. Monasse, R. Perrot, and R. Marlet, "OpenMVG: Open multiple view geometry," *International Workshop on Reproducible Research in
Pattern Recognition*, 2016, doi: [10.1007/978-3-319-56414-2_5](https://doi.org/10.1007/978-3-319-56414-2_5).
<br>

\[32\] A. G. Patil, S. G. Patil, M. Li, M. Fisher, M. Savva, and H. Zhang, "Advances in Data-Driven Analysis and Synthesis of
3D Indoor Scenes," *Computer Graphics Forum*, 2024, doi: [10.1111/cgf.14927](https://doi.org/10.1111/cgf.14927).
<br>

\[33\] G. Pintore, M. Agus, and E. Gobbetti, "AtlantaNet: Inferring the 3D Indoor Layout from a
Single 360 Image Beyond the Manhattan World
Assumption," *Proc. ECCV*, 2020, doi: [10.1007/978-3-030-58598-3_26](https://doi.org/10.1007/978-3-030-58598-3_26).
<br>

\[34\] G. Pintore, C. Mura, F. Ganovelli, L. Fuentes-Perez, R. Pajarola, and E. Gobbetti, "State-of-the-art in Automatic 3D Reconstruction of
Structured Indoor Environments," *Comput. Graph. Forum*, 2020, doi: [10.1111/cgf.14021](https://doi.org/10.1111/cgf.14021).
<br>

\[35\] G. Pintore, M. Agus, E. Almansa, J. Schneider, and E. Gobbetti, "SliceNet: deep dense depth estimation from a single
indoor panorama using a slice-based representation," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.01137](https://doi.org/10.1109/CVPR46437.2021.01137).
<br>

\[36\] M. Rey-Area, M. Yuan, and C. Richardt, "360MonoDepth: High-Resolution 360° Monocular
Depth Estimation," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.00374](https://doi.org/10.1109/CVPR52688.2022.00374).
<br>

\[37\] M. A. Shabani, W. Song, M. Odamaki, H. Fujiki, and Y. Furukawa, "Extreme structure from motion for indoor panoramas
without visual overlaps," *Proc. ICCV*, 2021, doi: [10.1109/ICCV48922.2021.00565](https://doi.org/10.1109/ICCV48922.2021.00565).
<br>

\[38\] J. Straub, T. Whelan, L. Ma, Y. Chen, E. Wijmans, S. Green, J. J. Engel, R. Mur-Artal, C. Ren, S. Verma, A. Clarkson, M. Yan, B. Budge, Y. Yan, X. Pan, J. Yon, Y. Zou, K. Leon, N. Carter, J. Briales, T. Gillingham, E. Mueggler, L. Pesqueira, M. Savva, D. Batra, H. M. Strasdat, R. D. Nardi, M. Goesele, S. Lovegrove, and R. Newcombe, "The Replica Dataset: A Digital Replica of Indoor
Spaces," *ArXiv e-print arXiv:1906.05797*, 2019, doi: [10.48550/arXiv.1906.05797](https://doi.org/10.48550/arXiv.1906.05797).
<br>

\[39\] F. Xia, A. R. Zamir, Z. He, A. Sax, J. Malik, and S. Savarese, "Gibson Env: real-world perception for embodied
agents," *Proc. CVPR*, 2018, doi: [10.1109/CVPR.2018.00945](https://doi.org/10.1109/CVPR.2018.00945).
<br>

\[40\] J. Xiao, K. A. Ehinger, A. Oliva, and A. Torralba, "Recognizing scene viewpoint using panoramic place
representation," *Proc. CVPR*, 2012, doi: [10.1109/CVPR.2012.6247991](https://doi.org/10.1109/CVPR.2012.6247991).
<br>

\[41\] J. Xu, J. Zheng, Y. Xu, R. Tang, and S. Gao, "Layout-guided novel view synthesis from a single
indoor panorama," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.01617](https://doi.org/10.1109/CVPR46437.2021.01617).
<br>

\[42\] Y. Zhang, S. Song, P. Tan, and J. Xiao, "PanoContext: A Whole-Room 3D Context Model for
Panoramic Scene Understanding," *Proc. ECCV*, 2014, doi: [10.1007/978-3-319-10599-4_43](https://doi.org/10.1007/978-3-319-10599-4_43).
<br>

\[43\] J. Zheng, J. Zhang, J. Li, R. Tang, S. Gao, and Z. Zhou, "Structured3D: A Large Photo-realistic Dataset for
Structured 3D Modeling," *Proc. ECCV*, 2020, doi: [10.1007/978-3-030-58545-7_30](https://doi.org/10.1007/978-3-030-58545-7_30).
<br>

\[44\] C. Zhuang, Z. Lu, Y. Wang, J. Xiao, and Y. Wang, "SPDET: Edge-aware self-supervised panoramic depth
estimation transformer with spherical geometry," *IEEE TPAMI*, 2023, doi: [10.1109/TPAMI.2023.3272949](https://doi.org/10.1109/TPAMI.2023.3272949).
<br>

\[45\] N. Zioulis, A. Karakottas, D. Zarpalas, and P. Daras, "OmniDepth: Dense Depth Estimation for Indoors
Spherical Panoramas," *Proc. ECCV*, 2018, doi: [10.1007/978-3-030-01231-1_28](https://doi.org/10.1007/978-3-030-01231-1_28).
<br>

\[46\] C. Zou, J. W. Su, C. H. Peng, A. Colburn, Q. Shan, P. Wonka, H. K. Chu, and D. Hoiem, "Manhattan Room Layout Reconstruction from a Single
360 Image: A Comparative Study of State-of-the-Art
Methods," *International Journal of Computer Vision*, 2021, doi: [10.1007/s11263-020-01426-8](https://doi.org/10.1007/s11263-020-01426-8).
<br>


[↑ Back to Top](#table-of-contents)

---

## Automatic geometric and structural modeling
These methods infer geometric, structural, and visual properties of indoor scenes from a single omnidirectional panorama (or approximately one per room in multi-room settings). Approaches range from pixel-level augmentation (e.g., depth, normals) to higher-level structural abstractions of room layouts and objects, and extend to sparse multi-room reasoning that recovers layouts and inter-room connectivity for navigation and exploration.


[↑ Back to Top](#table-of-contents)

---

### Depth and other pixel-wise information inference



**References:**

\[1\] H. Ai, Z. Cao, Y. P. Cao, Y. Shan, and L. Wang, "HRDFuse: Monocular 360° Depth Estimation by
Collaboratively Learning Holistic-With-Regional Depth
Distributions," *Proc. CVPR*, 2023, doi: [10.1109/CVPR52729.2023.01275](https://doi.org/10.1109/CVPR52729.2023.01275).
<br>

\[2\] H. Ai and L. Wang, "Elite360D: Towards Efficient 360 Depth Estimation
via Semantic-and Distance-Aware Bi-Projection Fusion," *Proc. CVPR*, 2024, doi: [10.1109/CVPR52733.2024.00947](https://doi.org/10.1109/CVPR52733.2024.00947).
<br>

\[3\] Y. Cao, Z. Wu, and C. Shen, "Estimating Depth From Monocular Images as
Classification Using Deep Fully Convolutional
Residual Networks," *IEEE TCSVT*, 2018, doi: [10.1109/TCSVT.2017.2740321](https://doi.org/10.1109/TCSVT.2017.2740321).
<br>

\[4\] Z. Cao, J. Zhu, W. Zhang, H. Ai, H. Bai, H. Zhao, and L. Wang, "PanDA: Towards Panoramic Depth Anything with
Unlabeled Panoramas and Mobius Spatial Augmentation," *Proc. CVPR*, 2025, doi: [10.1109/CVPR52734.2025.00100](https://doi.org/10.1109/CVPR52734.2025.00100).
<br>

\[5\] H. Cheng, C. Chao, J. Dong, H. Wen, T. Liu, and M. Sun, "Cube Padding for Weakly-Supervised Saliency
Prediction in 360 Videos," *Proc. CVPR*, 2018, doi: [10.1109/CVPR.2018.00154](https://doi.org/10.1109/CVPR.2018.00154).
<br>

\[6\] D. Eigen, C. Puhrsch, and R. Fergus, "Depth Map Prediction from a Single Image using a
Multi-Scale Deep Network," *Proc. NeurIPS*, 2014, url: [https://dl.acm.org/doi/abs/10.5555/2969033.2969091](https://dl.acm.org/doi/abs/10.5555/2969033.2969091).
<br>

\[7\] D. Eigen and R. Fergus, "Predicting Depth, Surface Normals and Semantic Labels
with a Common Multi-scale Convolutional Architecture," *Proc. ICCV*, 2015, doi: [10.1109/ICCV.2015.304](https://doi.org/10.1109/ICCV.2015.304).
<br>

\[8\] H. Fu, M. Gong, C. Wang, K. Batmanghelich, and D. Tao, "Deep Ordinal Regression Network for Monocular Depth
Estimation," *Proc. CVPR*, 2018, doi: [10.1109/CVPR.2018.00214](https://doi.org/10.1109/CVPR.2018.00214).
<br>

\[9\] G. Payen de La Garanderie, A. Atapour Abarghouei, and T. P. Breckon, "Eliminating the Blind Spot: Adapting 3D Object
Detection and Monocular Depth Estimation to 360
Panoramic Imagery," *Proc. ECCV*, 2018, doi: [10.1007/978-3-030-01261-8_48](https://doi.org/10.1007/978-3-030-01261-8_48).
<br>

\[10\] K. He, X. Zhang, S. Ren, and J. Sun, "Deep Residual Learning for Image Recognition," *Proc. CVPR*, 2016, doi: [10.1109/CVPR.2016.90](https://doi.org/10.1109/CVPR.2016.90).
<br>

\[11\] C. Huang, F. Shao, H. Chen, B. Mu, and L. Xu, "GADFNet: Geometric Priors Assisted Dual-Projection
Fusion Network for Monocular Panoramic Depth
Estimation," *IEEE Trans. Circuits and Systems for Video
Technology*, 2025, doi: [10.1109/TCSVT.2025.3553472](https://doi.org/10.1109/TCSVT.2025.3553472).
<br>

\[12\] H. Jiang, Z. Sheng, S. Zhu, Z. Dong, and R. Huang, "Unifuse: Unidirectional fusion for 360 panorama depth
estimation," *IEEE Robotics and Automation Letters*, 2021, doi: [10.1109/LRA.2021.3058957](https://doi.org/10.1109/LRA.2021.3058957).
<br>

\[13\] H. Jiang, Z. Song, Z. Lou, R. Xu, and M. Tan, "Depth Anything in 360°: Towards Scale
Invariance in the Wild," *arXiv preprint arXiv:2512.22819*, 2025, doi: [10.48550/arXiv.2512.22819](https://doi.org/10.48550/arXiv.2512.22819).
<br>

\[14\] I. Laina, C. Rupprecht, V. Belagiannis, F. Tombari, and N. Navab, "Deeper Depth Prediction with Fully Convolutional
Residual Networks," *Proc. 3DV*, 2016, doi: [10.1109/3DV.2016.32](https://doi.org/10.1109/3DV.2016.32).
<br>

\[15\] S. Lambert-Lacroix and L. Zwald, "The adaptive BerHu penalty in robust regression," *Journal of Nonparametric Statistics*, 2016, doi: [10.1080/10485252.2016.1190359](https://doi.org/10.1080/10485252.2016.1190359).
<br>

\[16\] J. Lee, M. Heo, K. Kim, and C. Kim, "Single-Image Depth Estimation Based on Fourier Domain
Analysis," *Proc. CVPR*, 2018, doi: [10.1109/CVPR.2018.00042](https://doi.org/10.1109/CVPR.2018.00042).
<br>

\[17\] J. Lee, H. Park, B. U. Lee, and K. Joo, "HUSH: Holistic Panoramic 3D Scene Understanding
using Spherical Harmonics," *Proc. CVPR*, 2025, doi: [10.1109/CVPR52734.2025.01547](https://doi.org/10.1109/CVPR52734.2025.01547).
<br>

\[18\] Y. Li, Y. Guo, Z. Yan, X. Huang, Y. Duan, and L. Ren, "Omnifusion: 360 monocular depth estimation via
geometry-aware fusion," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.00282](https://doi.org/10.1109/CVPR52688.2022.00282).
<br>

\[19\] F. Liu, C. Shen, and G. Lin, "Deep convolutional neural fields for depth estimation
from a single image," *Proc. CVPR*, 2015, doi: [10.1109/CVPR.2015.7299152](https://doi.org/10.1109/CVPR.2015.7299152).
<br>

\[20\] G. Pintore, M. Agus, E. Almansa, J. Schneider, and E. Gobbetti, "SliceNet: deep dense depth estimation from a single
indoor panorama using a slice-based representation," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.01137](https://doi.org/10.1109/CVPR46437.2021.01137).
<br>

\[21\] G. Pintore, M. Agus, A. Signoroni, and E. Gobbetti, "DDD: Deep indoor panoramic Depth estimation with
Density maps consistency," *STAG: Smart Tools and Applications in Graphics*, 2024, doi: [10.2312/stag.20241336](https://doi.org/10.2312/stag.20241336).
<br>

\[22\] G. Pintore, M. Agus, A. Signoroni, and E. Gobbetti, "DDD++: Exploiting Density map consistency for Deep
Depth estimation in indoor environments," *Graphical Models*, 2025, doi: [10.1016/j.gmod.2025.101281](https://doi.org/10.1016/j.gmod.2025.101281).
<br>

\[23\] R. Ranftl, K. Lasinger, D. Hafner, K. Schindler, and V. Koltun, " Towards Robust Monocular Depth Estimation: Mixing
Datasets for Zero-Shot Cross-Dataset Transfer ," *IEEE Transactions on Pattern Analysis \& Machine
Intelligence*, 2022, doi: [10.1109/TPAMI.2020.3019967](https://doi.org/10.1109/TPAMI.2020.3019967).
<br>

\[24\] M. Rey-Area, M. Yuan, and C. Richardt, "360MonoDepth: High-Resolution 360° Monocular
Depth Estimation," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.00374](https://doi.org/10.1109/CVPR52688.2022.00374).
<br>

\[25\] A. Saxena, M. Sun, and A. Y. Ng, "Make3D: Learning 3D Scene Structure from a Single
Still Image," *IEEE TPAMI*, 2009, doi: [10.1109/TPAMI.2008.132](https://doi.org/10.1109/TPAMI.2008.132).
<br>

\[26\] Z. Shen, C. Lin, K. Liao, L. Nie, Z. Zheng, and Y. Zhao, "PanoFormer: Panorama Transformer for Indoor 360
Depth Estimation," *Proc. ECCV*, 2022, doi: [10.1007/978-3-031-19769-7_12](https://doi.org/10.1007/978-3-031-19769-7_12).
<br>

\[27\] Z. Shen, Z. Zheng, C. Lin, L. Nie, K. Liao, S. Zheng, and Y. Zhao, "Disentangling Orthogonal Planes for Indoor Panoramic
Room Layout Estimation with Cross-Scale Distortion
Awareness," *Proc. CVPR*, 2023, doi: [10.1109/CVPR52729.2023.01663](https://doi.org/10.1109/CVPR52729.2023.01663).
<br>

\[28\] Y. C. Su and K. Grauman, "Learning Spherical Convolution for Fast Features from
360 Imagery," *Proc. NeurIPS*, 2017, url: [https://dl.acm.org/doi/abs/10.5555/3294771.3294822](https://dl.acm.org/doi/abs/10.5555/3294771.3294822).
<br>

\[29\] Y. Su and K. Grauman, "Kernel Transformer Networks for Compact Spherical
Convolution," *Proc. CVPR*, 2019, doi: [10.1109/CVPR.2019.00967](https://doi.org/10.1109/CVPR.2019.00967).
<br>

\[30\] C. Sun, M. Sun, and H. T. Chen, "HoHoNet: 360° Indoor Holistic Understanding
with Latent Horizontal Features," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.00260](https://doi.org/10.1109/CVPR46437.2021.00260).
<br>

\[31\] K. Tateno, N. Navab, and F. Tombari, "Distortion-Aware Convolutional Filters for Dense
Prediction in Panoramic Images," *Proc. ECCV*, 2018, doi: [10.1007/978-3-030-01270-0_43](https://doi.org/10.1007/978-3-030-01270-0_43).
<br>

\[32\] P. Wang, X. Shen, Z. Lin, S. Cohen, B. Price, and A. Yuille, "Towards unified depth and semantic prediction from a
single image," *Proc. CVPR*, 2015, doi: [10.1109/CVPR.2015.7298897](https://doi.org/10.1109/CVPR.2015.7298897).
<br>

\[33\] F. E. Wang, H. N. Hu, H. T. Cheng, J. T. Lin, S. T. Yang, M. L. Shih, H. K. Chu, and M. Sun, "Self-supervised learning of depth and camera motion
from 360 videos," *Proc. ACCV*, 2018, doi: [10.1007/978-3-030-20873-8_4](https://doi.org/10.1007/978-3-030-20873-8_4).
<br>

\[34\] F. E. Wang, Y. H. Yeh, M. Sun, W. C. Chiu, and Y. H. Tsai, "BiFuse: Monocular 360 Depth Estimation via
Bi-Projection Fusion," *Proc. CVPR*, 2020, doi: [10.1109/CVPR42600.2020.00054](https://doi.org/10.1109/CVPR42600.2020.00054).
<br>

\[35\] F. E. Wang, Y. H. Yeh, Y. H. Tsai, W. C. Chiu, and M. Sun, "Bifuse++: Self-supervised and efficient bi-projection
fusion for 360 depth estimation," *IEEE TPAMI*, 2022, doi: [10.1109/TPAMI.2022.3203516](https://doi.org/10.1109/TPAMI.2022.3203516).
<br>

\[36\] N. H. A. Wang and Y. L. Liu, "Depth anywhere: Enhancing 360 monocular depth
estimation via perspective distillation and unlabeled
data augmentation," *Proc. NeurIPS*, 2024, url: [https://dl.acm.org/doi/10.5555/3737916.3741972](https://dl.acm.org/doi/10.5555/3737916.3741972).
<br>

\[37\] X. Wang, Z. He, Q. Zhang, Y. Yang, T. Zhao, and J. Jiang, "Geometry-Aware Self-Supervised Indoor 360°
Depth Estimation via Asymmetric Dual-Domain
Collaborative Learning," *IEEE Trans. Multimedia*, 2025, doi: [10.1109/TMM.2025.3535340](https://doi.org/10.1109/TMM.2025.3535340).
<br>

\[38\] D. Xu, W. Wang, H. Tang, H. Liu, N. Sebe, and E. Ricci, "Structured Attention Guided Convolutional Neural
Fields for Monocular Depth Estimation," *Proc. CVPR*, 2018, doi: [10.1109/CVPR.2018.00412](https://doi.org/10.1109/CVPR.2018.00412).
<br>

\[39\] Q. Yan, Q. Wang, K. Zhao, J. Chen, B. Li, X. Chu, and F. Deng, "SphereFusion: Efficient Panorama Depth Estimation via
Gated Fusion," *Proc. 3DV*, 2025, doi: [10.1109/3DV66043.2025.00084](https://doi.org/10.1109/3DV66043.2025.00084).
<br>

\[40\] L. Yang, B. Kang, Z. Huang, Z. Zhao, X. Xu, J. Feng, and H. Zhao, "Depth Anything V2," *Proc. NeurIPS*, 2024, doi: [10.52202/079017-0688](https://doi.org/10.52202/079017-0688).
<br>

\[41\] Y. Zhang, S. Song, P. Tan, and J. Xiao, "PanoContext: A Whole-Room 3D Context Model for
Panoramic Scene Understanding," *Proc. ECCV*, 2014, doi: [10.1007/978-3-319-10599-4_43](https://doi.org/10.1007/978-3-319-10599-4_43).
<br>

\[42\] N. Zioulis, A. Karakottas, D. Zarpalas, and P. Daras, "OmniDepth: Dense Depth Estimation for Indoors
Spherical Panoramas," *Proc. ECCV*, 2018, doi: [10.1007/978-3-030-01231-1_28](https://doi.org/10.1007/978-3-030-01231-1_28).
<br>

\[43\] N. Zioulis, A. Karakottas, D. Zarpalas, F. Alvarez, and P. Daras, "Spherical View Synthesis for Self-Supervised
360° Depth Estimation," *Proc. 3DV*, 2019, doi: [10.1109/3DV.2019.00081](https://doi.org/10.1109/3DV.2019.00081).
<br>


[↑ Back to Top](#table-of-contents)

---

### Single-image room layout estimation



**References:**

\[1\] A. X. Chang, T. Funkhouser, L. Guibas, P. Hanrahan, Q. Huang, Z. Li, S. Savarese, M. Savva, S. Song, H. Su, J. Xiao, L. Yi, and F. Yu, "ShapeNet: An Information-Rich 3D Model
Repository," *arXiv preprint arXiv:1512.03012*, 2015, doi: [10.48550/arXiv.1512.03012](https://doi.org/10.48550/arXiv.1512.03012).
<br>

\[2\] Z. Chen, V. Badrinarayanan, C. Y. Lee, and A. Rabinovich, "GradNorm: Gradient normalization for adaptive loss
balancing in deep multitask networks," *Proc. ICML*, 2018, doi: [10.48550/arXiv.1711.02257](https://doi.org/10.48550/arXiv.1711.02257).
<br>

\[3\] X. Chen, H. Zhao, G. Zhou, and Y. Q. Zhang, "PQ-Transformer: Jointly Parsing 3D Objects and
Layouts from Point Clouds," *Proc. CVPR*, 2022, doi: [10.1109/LRA.2022.3143224](https://doi.org/10.1109/LRA.2022.3143224).
<br>

\[4\] Y. Dai, N. Fei, and Z. Lu, "Improvable gap balancing for multi-task learning," *Uncertainty in Artificial Intelligence*, 2023, doi: [10.48550/arXiv.2307.15429](https://doi.org/10.48550/arXiv.2307.15429).
<br>

\[5\] M. Rey-Area, M. Yuan, and C. Richardt, "360MonoDepth Replica," *Public dataset*, 2022, url: [https://manurare.github.io/360monodepth/](https://manurare.github.io/360monodepth/).
<br>

\[6\] M. Dong, L. Huan, H. Xiong, S. Shen, and X. Zheng, "Shape anchor guided holistic indoor scene
understanding," *Proc. ICCV*, 2023, doi: [10.1109/ICCV51070.2023.02003](https://doi.org/10.1109/ICCV51070.2023.02003).
<br>

\[7\] Y. Dong, C. Fang, L. Bo, Z. Dong, and P. Tan, "PanoContext-Former: Panoramic total scene
understanding with a transformer," *Proc. CVPR*, 2024, doi: [10.1109/CVPR52733.2024.02653](https://doi.org/10.1109/CVPR52733.2024.02653).
<br>

\[8\] A. Dosovitskiy, L. Beyer, A. Kolesnikov, D. Weissenborn, X. Zhai, T. Unterthiner, M. Dehghani, M. Minderer, G. Heigold, S. Gelly, J. Uszkoreit, and N. Houlsby, "An image is worth 16x16 words: Transformers for image
recognition at scale," *arXiv preprint arXiv:2010.11929*, 2020, doi: [10.48550/arXiv.2010.11929](https://doi.org/10.48550/arXiv.2010.11929).
<br>

\[9\] V. Gkitsas, V. Sterzentsenko, N. Zioulis, G. Albanis, and D. Zarpalas, "PanoDR: Spherical Panorama Diminished Reality for
Indoor Scenes," *Proc. CVPR Workshops*, 2021, doi: [10.1109/CVPRW53098.2021.00412](https://doi.org/10.1109/CVPRW53098.2021.00412).
<br>

\[10\] V. Hedau, D. Hoiem, and D. Forsyth, "Recovering the spatial layout of cluttered rooms," *Proc. ICCV*, 2009, doi: [10.1109/ICCV.2009.5459411](https://doi.org/10.1109/ICCV.2009.5459411).
<br>

\[11\] D. Hoiem, A. A. Efros, and M. Hebert, "Recovering Surface Layout from an Image," *International Journal of Computer Vision*, 2007, doi: [10.1007/s11263-006-0031-y](https://doi.org/10.1007/s11263-006-0031-y).
<br>

\[12\] R. Hu and A. Singh, "Uniting Vision-and-Language Tasks via Text
Generation," *Proc. ICML*, 2021, doi: [10.48550/arXiv.2102.02779](https://doi.org/10.48550/arXiv.2102.02779).
<br>

\[13\] S. Huang, S. Qi, and Y. Zhu, "Cooperative Holistic Scene Understanding: Unifying
3D Object, Layout, and Camera Pose Estimation," *Proc. NeurIPS*, 2018, url: [https://dl.acm.org/doi/abs/10.5555/3326943.3326963](https://dl.acm.org/doi/abs/10.5555/3326943.3326963).
<br>

\[14\] S. Ikehata, H. Yang, and Y. Furukawa, "Structured Indoor Modeling," *Proc. ICCV*, 2015, doi: [10.1109/ICCV.2015.156](https://doi.org/10.1109/ICCV.2015.156).
<br>

\[15\] Z. Jiang, Z. Xiang, J. Xu, and M. Zhao, "LGT-Net: Indoor Panoramic Room Layout Estimation
with Geometry-Aware Transformer Network," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.00170](https://doi.org/10.1109/CVPR52688.2022.00170).
<br>

\[16\] L. Jin, Y. Xu, J. Zheng, J. Zhang, R. Tang, S. Xu, J. Yu, and S. Gao, "Geometric Structure Based and Regularized Depth
Estimation from 360 Indoor Imagery," *Proc. CVPR*, 2020, doi: [10.1109/CVPR42600.2020.00097](https://doi.org/10.1109/CVPR42600.2020.00097).
<br>

\[17\] A. Kendall, Y. Gal, and R. Cipolla, "Multi-task learning using uncertainty to weigh losses
for scene geometry and semantics," *Proc. CVPR*, 2018, doi: [10.1109/CVPR.2018.00781](https://doi.org/10.1109/CVPR.2018.00781).
<br>

\[18\] J. Lambert, Y. Li, I. Boyadzhiev, L. Wixson, M. Narayana, W. Hutchcroft, J. Hays, F. Dellaert, and S. B. Kang, "Salve: Semantic alignment verification for floorplan
reconstruction from sparse panoramas," *Proc. ECCV*, 2022, doi: [10.1007/978-3-031-19821-2_37](https://doi.org/10.1007/978-3-031-19821-2_37).
<br>

\[19\] D. C. Lee, M. Hebert, and T. Kanade, "Geometric reasoning for single image structure
recovery," *Proc. CVPR*, 2009, doi: [10.1109/CVPR.2009.5206872](https://doi.org/10.1109/CVPR.2009.5206872).
<br>

\[20\] J. H. Lee, C. Lee, and C. S. Kim, "Learning multiple pixelwise tasks based on loss scale
balancing," *Proc. ICCV*, 2021.
<br>

\[21\] J. Lee, H. Park, B. U. Lee, and K. Joo, "HUSH: Holistic Panoramic 3D Scene Understanding
using Spherical Harmonics," *Proc. CVPR*, 2025, doi: [10.1109/CVPR52734.2025.01547](https://doi.org/10.1109/CVPR52734.2025.01547).
<br>

\[22\] M. Lewis, Y. Liu, N. Goyal, M. Ghazvininejad, A. Mohamed, O. Levy, V. Stoyanov, and L. Zettlemoyer, "BART: Denoising sequence-to-sequence pre-training
for natural language generation, translation, and
comprehension," *arXiv preprint arXiv:1910.13461*, 2019, doi: [10.48550/arXiv.1910.13461](https://doi.org/10.48550/arXiv.1910.13461).
<br>

\[23\] Y. Li, I. Boyadzhiev, Z. Liu, L. Shapiro, and A. Colburn, "BADGR: Bundle Adjustment Diffusion Conditioned by
Gradients for Wide-Baseline Floor Plan
Reconstruction," *Proc. CVPR*, 2025, doi: [10.1109/CVPR52734.2025.01564](https://doi.org/10.1109/CVPR52734.2025.01564).
<br>

\[24\] B. Liu, X. Liu, X. Jin, P. Stone, and Q. Liu, "Conflict-averse gradient descent for multi-task
learning," *Proc. NeurIPS*, 2021, doi: [10.48550/arXiv.2110.14048](https://doi.org/10.48550/arXiv.2110.14048).
<br>

\[25\] Z. Liu, Z. Zhang, Y. Cao, H. Hu, X. Tong, B. Dai, and S. Lin, "Group-Free 3D Object Detection via Transformers," *Proc. ICCV*, 2021, doi: [10.1109/ICCV48922.2021.00294](https://doi.org/10.1109/ICCV48922.2021.00294).
<br>

\[26\] Z. Liu, Y. Lin, Y. Cao, H. Hu, Y. Wei, Z. Zhang, S. Lin, and B. Guo, "Swin Transformer: Hierarchical Vision Transformer
using Shifted Windows," *Proc. ICCV*, 2021, doi: [10.1109/ICCV48922.2021.00986](https://doi.org/10.1109/ICCV48922.2021.00986).
<br>

\[27\] H. Liu, Y. Zheng, G. Chen, S. Cui, and X. Han, "Towards High-Fidelity Single-View Holistic
Reconstruction of Indoor Scenes," *Proc. ECCV*, 2022, doi: [10.1007/978-3-031-19769-7_25](https://doi.org/10.1007/978-3-031-19769-7_25).
<br>

\[28\] L. Mescheder, M. Oechsle, M. Niemeyer, S. Nowozin, and A. Geiger, "Occupancy Networks: Learning 3D Reconstruction in
Function Space," *Proc. CVPR*, 2019, doi: [10.1109/CVPR.2019.00459](https://doi.org/10.1109/CVPR.2019.00459).
<br>

\[29\] Y. Nie, J. Hou, X. Han, and M. Nießner, "Total3DUnderstanding: Joint Layout, Object Pose and
Mesh Reconstruction for Indoor Scenes from a Single
Image," *Proc. CVPR*, 2020, doi: [10.1109/CVPR42600.2020.00013](https://doi.org/10.1109/CVPR42600.2020.00013).
<br>

\[30\] G. Pintore, M. Agus, and E. Gobbetti, "AtlantaNet: Inferring the 3D Indoor Layout from a
Single 360 Image Beyond the Manhattan World
Assumption," *Proc. ECCV*, 2020, doi: [10.1007/978-3-030-58598-3_26](https://doi.org/10.1007/978-3-030-58598-3_26).
<br>

\[31\] G. Pintore, C. Mura, F. Ganovelli, L. Fuentes-Perez, R. Pajarola, and E. Gobbetti, "State-of-the-art in Automatic 3D Reconstruction of
Structured Indoor Environments," *Comput. Graph. Forum*, 2020, doi: [10.1111/cgf.14021](https://doi.org/10.1111/cgf.14021).
<br>

\[32\] G. Pintore, E. Almansa, M. Agus, and E. Gobbetti, "Deep3DLayout: 3D Reconstruction of an Indoor
Layout from a Spherical Panoramic Image," *ACM TOG*, 2021, doi: [10.1145/3478513.3480480](https://doi.org/10.1145/3478513.3480480).
<br>

\[33\] G. Pintore, M. Agus, E. Almansa, and E. Gobbetti, "Instant Automatic Emptying of Panoramic Indoor
Scenes," *IEEE TVCG*, 2022, doi: [10.1109/TVCG.2022.3202999](https://doi.org/10.1109/TVCG.2022.3202999).
<br>

\[34\] G. Pintore, U. Shah, M. Agus, and E. Gobbetti, "NadirFloorNet: reconstructing multi-room floorplans
from a small set of registered panoramic images," *Proc. CVPR*, 2025, doi: [10.1109/CVPRW67362.2025.00186](https://doi.org/10.1109/CVPRW67362.2025.00186).
<br>

\[35\] G. Pintore, S. Jashari, M. Agus, and E. Gobbetti, "PanoFloor: Reconstruction and Immersive Exploration
of Large Multi-Room Scenes from a Minimal Set of
Registered Panoramic Images Using Denoised Density
Maps," *Proc. ISMAR*, 2025, doi: [10.1109/ISMAR67309.2025.00052](https://doi.org/10.1109/ISMAR67309.2025.00052).
<br>

\[36\] C. R. Qi, W. Liu, C. Wu, H. Su, and L. J. Guibas, "Frustum PointNets for 3D Object Detection from
RGB-D Data," *Proc. CVPR*, 2018, doi: [10.1109/CVPR.2018.00102](https://doi.org/10.1109/CVPR.2018.00102).
<br>

\[37\] A. Radford, J. W. Kim, C. Hallacy, A. Ramesh, G. Goh, S. Agarwal, G. Sastry, A. Askell, P. Mishkin, J. Clark, G. Krueger, and I. Sutskever, "Learning Transferable Visual Models From Natural
Language Supervision," *Proc. ICML*, 2021, url: [https://icml.cc/virtual/2021/oral/9194](https://icml.cc/virtual/2021/oral/9194).
<br>

\[38\] C. Raffel, N. Shazeer, A. Roberts, K. Lee, S. Narang, M. Matena, Y. Zhou, W. Li, and P. J. Liu, "Exploring the limits of transfer learning with a
unified text-to-text transformer," *J. Mach. Learn. Res.*, 2020.
<br>

\[39\] S. Ren, K. He, R. Girshick, and J. Sun, "Faster R-CNN: Towards Real-Time Object Detection with
Region Proposal Networks," *IEEE Transactions on Pattern Analysis and Machine
Intelligence*, 2017, doi: [10.1109/TPAMI.2016.2577031](https://doi.org/10.1109/TPAMI.2016.2577031).
<br>

\[40\] J. Schult, F. Engelmann, T. Kontogianni, and B. Leibe, "Mask3D: Mask Transformer for 3D Semantic Instance
Segmentation," *Proc. ICCV*, 2023, doi: [10.1109/ICRA48891.2023.10160590](https://doi.org/10.1109/ICRA48891.2023.10160590).
<br>

\[41\] O. Sener and V. Koltun, "Multi-task learning as multi-objective optimization," *Proc. NeurIPS*, 2018, doi: [10.48550/arXiv.1810.04650](https://doi.org/10.48550/arXiv.1810.04650).
<br>

\[42\] M. A. Shabani, W. Song, M. Odamaki, H. Fujiki, and Y. Furukawa, "Extreme structure from motion for indoor panoramas
without visual overlaps," *Proc. ICCV*, 2021, doi: [10.1109/ICCV48922.2021.00565](https://doi.org/10.1109/ICCV48922.2021.00565).
<br>

\[43\] Z. Shen, Z. Zheng, C. Lin, L. Nie, K. Liao, S. Zheng, and Y. Zhao, "Disentangling Orthogonal Planes for Indoor Panoramic
Room Layout Estimation with Cross-Scale Distortion
Awareness," *Proc. CVPR*, 2023, doi: [10.1109/CVPR52729.2023.01663](https://doi.org/10.1109/CVPR52729.2023.01663).
<br>

\[44\] V. Sitzmann, J. Martel, A. Bergman, D. Lindell, and G. Wetzstein, "Implicit Neural Representations with Periodic
Activation Functions," *Proc. NeurIPS*, 2020, doi: [10.48550/arXiv.2006.09661](https://doi.org/10.48550/arXiv.2006.09661).
<br>

\[45\] S. Song and J. Xiao, "Deep Sliding Shapes for Amodal 3D Object Detection
in RGB-D Images," *Proc. CVPR*, 2016, doi: [10.1109/CVPR.2016.94](https://doi.org/10.1109/CVPR.2016.94).
<br>

\[46\] C. Sun, C. W. Hsiao, M. Sun, and H. T. Chen, "HorizonNet: Learning room layout with 1D
representation and pano stretch data augmentation," *Proc. CVPR*, 2019, doi: [10.1109/CVPR.2019.00114](https://doi.org/10.1109/CVPR.2019.00114).
<br>

\[47\] C. Sun, W. E. Tai, Y. L. Shih, K. W. Chen, Y. J. Syu, Y. C. F. Wang, and H. T. Chen, "Seg2Reg: Differentiable 2D Segmentation to 1D
Regression Rendering for 360° Room Layout
Reconstruction," *Proc. CVPR*, 2024, doi: [10.1109/CVPR52733.2024.00993](https://doi.org/10.1109/CVPR52733.2024.00993).
<br>

\[48\] H. Touvron, M. Cord, M. Douze, F. Massa, A. Sablayrolles, and H. Jégou, "Training Data-efficient Image Transformers \&
Distillation through Attention," *Proc. ICML*, 2021, url: [https://proceedings.mlr.press/v139/touvron21a](https://proceedings.mlr.press/v139/touvron21a).
<br>

\[49\] P. V. Tran, "SSLayout360: Semi-supervised indoor layout
estimation from 360deg panorama," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.01510](https://doi.org/10.1109/CVPR46437.2021.01510).
<br>

\[50\] Y. J. Tsai, J. C. Jhang, J. Zheng, W. Wang, A. Y. Chen, M. Sun, C. H. Kuo, and M. H. Yang, "No more ambiguity in 360° room layout via
bi-layout estimation," *Proc. CVPR*, 2024, doi: [10.1109/CVPR52733.2024.02650](https://doi.org/10.1109/CVPR52733.2024.02650).
<br>

\[51\] S. Tulsiani, T. Zhou, A. A. Efros, and J. Malik, "Multi-View Supervision for Single-View Reconstruction
via Differentiable Ray Consistency," *IEEE Transactions on Pattern Analysis and Machine
Intelligence*, 2022, doi: [10.1109/TPAMI.2019.2898859](https://doi.org/10.1109/TPAMI.2019.2898859).
<br>

\[52\] A. Vaswani, N. Shazeer, N. Parmar, J. Uszkoreit, L. Jones, A. N. Gomez, L. Kaiser, and I. Polosukhin, "Attention is all you need," *Proc. NeurIPS*, 2017.
<br>

\[53\] F. E. Wang, Y. H. Yeh, M. Sun, W. C. Chiu, and Y. H. Tsai, "LED2-Net: Monocular 360 Layout Estimation via
Differentiable Depth Rendering," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.01276](https://doi.org/10.1109/CVPR46437.2021.01276).
<br>

\[54\] Y. Wang, T. Ye, L. Cao, W. Huang, F. Sun, F. He, and D. Tao, "Bridged transformer for vision and point cloud 3D
object detection," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.01180](https://doi.org/10.1109/CVPR52688.2022.01180).
<br>

\[55\] J. Xu, J. Zheng, Y. Xu, R. Tang, and S. Gao, "Layout-guided novel view synthesis from a single
indoor panorama," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.01617](https://doi.org/10.1109/CVPR46437.2021.01617).
<br>

\[56\] S. T. Yang, F. E. Wang, C. H. Peng, P. Wonka, M. Sun, and H. K. Chu, "DuLa-Net: A Dual-Projection Network for Estimating
Room Layouts from a Single RGB Panorama," *Proc. CVPR*, 2019, doi: [10.1109/CVPR.2019.00348](https://doi.org/10.1109/CVPR.2019.00348).
<br>

\[57\] T. Yu, S. Kumar, A. Gupta, S. Levine, K. Hausman, and C. Finn, "Gradient surgery for multi-task learning," *Proc. NeurIPS*, 2020, doi: [10.48550/arXiv.2001.06782](https://doi.org/10.48550/arXiv.2001.06782).
<br>

\[58\] H. Yu, L. He, B. Jian, W. Feng, and S. Liu, "PanelNet: Understanding 360 indoor environment via
panel representation," *Proc. CVPR*, 2023, doi: [10.1109/CVPR52729.2023.00091](https://doi.org/10.1109/CVPR52729.2023.00091).
<br>

\[59\] C. Zhang, Z. Cui, C. Chen, S. Liu, B. Zeng, H. Bao, and Y. Zhang, "DeepPanoContext: Panoramic 3D scene understanding
with holistic scene context graph and relation-based
optimization," *Proc. ICCV*, 2021, doi: [10.1109/ICCV48922.2021.01240](https://doi.org/10.1109/ICCV48922.2021.01240).
<br>

\[60\] Y. Zhang, S. Song, P. Tan, and J. Xiao, "PanoContext: A Whole-Room 3D Context Model for
Panoramic Scene Understanding," *Proc. ECCV*, 2014, doi: [10.1007/978-3-319-10599-4_43](https://doi.org/10.1007/978-3-319-10599-4_43).
<br>

\[61\] Y. Zhao, C. Wen, Z. Xue, and Y. Gao, "3D Room Layout Estimation from a Cubemap of
Panorama Image via Deep Manhattan Hough Transform," *Proc. ECCV*, 2022, doi: [10.1007/978-3-031-19769-7_37](https://doi.org/10.1007/978-3-031-19769-7_37).
<br>

\[62\] C. Zou, A. Colburn, Q. Shan, and D. Hoiem, "LayoutNet: Reconstructing the 3D Room Layout from
a Single RGB Image," *Proc. CVPR*, 2018, doi: [10.1109/CVPR.2018.00219](https://doi.org/10.1109/CVPR.2018.00219).
<br>

\[63\] C. Zou, J. W. Su, C. H. Peng, A. Colburn, Q. Shan, P. Wonka, H. K. Chu, and D. Hoiem, "3D Manhattan Room Layout Reconstruction from a
Single 360 Image," *ArXiv e-print arXiv:1910.04099*, 2019, doi: [10.48550/arXiv.1910.04099](https://doi.org/10.48550/arXiv.1910.04099).
<br>

\[64\] C. Zou, J. W. Su, C. H. Peng, A. Colburn, Q. Shan, P. Wonka, H. K. Chu, and D. Hoiem, "Manhattan Room Layout Reconstruction from a Single
360 Image: A Comparative Study of State-of-the-Art
Methods," *International Journal of Computer Vision*, 2021, doi: [10.1007/s11263-020-01426-8](https://doi.org/10.1007/s11263-020-01426-8).
<br>


[↑ Back to Top](#table-of-contents)

---

### Positioning and connecting single rooms



**References:**

\[1\] R. Cabral and Y. Furukawa, "Piecewise Planar and Compact Floorplan Reconstruction
from Images," *Proc. CVPR*, 2014, doi: [10.1109/CVPR.2014.546](https://doi.org/10.1109/CVPR.2014.546).
<br>

\[2\] J. Chen, C. Liu, J. Wu, and Y. Furukawa, "Floor-SP: Inverse CAD for floorplans by
sequential room-wise shortest path," *Proc. CVPR*, 2019, doi: [10.1109/ICCV.2019.00275](https://doi.org/10.1109/ICCV.2019.00275).
<br>

\[3\] J. Chen, Y. Qian, and Y. Furukawa, "HEAT: Holistic Edge Attention Transformer for
Structured Reconstruction," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.00384](https://doi.org/10.1109/CVPR52688.2022.00384).
<br>

\[4\] J. Chen, R. Deng, and Y. Furukawa, "Polydiffuse: Polygonal shape reconstruction via
guided set diffusion models," *NeurIPS*, 2024, url: [https://dl.acm.org/doi/abs/10.5555/3666122.3666212](https://dl.acm.org/doi/abs/10.5555/3666122.3666212).
<br>

\[5\] Y. Furukawa, B. Curless, S. M. Seitz, and R. Szeliski, "Reconstructing building interiors from images," *Proc. ICCV*, 2009, doi: [10.1109/ICCV.2009.5459145](https://doi.org/10.1109/ICCV.2009.5459145).
<br>

\[6\] K. He, G. Gkioxari, P. Dolláar, and R. Girshick, "Mask R-CNN," *Proc. ICCV*, 2017, doi: [10.1109/ICCV.2017.322](https://doi.org/10.1109/ICCV.2017.322).
<br>

\[7\] S. Ikehata, H. Yang, and Y. Furukawa, "Structured Indoor Modeling," *Proc. ICCV*, 2015, doi: [10.1109/ICCV.2015.156](https://doi.org/10.1109/ICCV.2015.156).
<br>

\[8\] J. Lambert, Y. Li, I. Boyadzhiev, L. Wixson, M. Narayana, W. Hutchcroft, J. Hays, F. Dellaert, and S. B. Kang, "Salve: Semantic alignment verification for floorplan
reconstruction from sparse panoramas," *Proc. ECCV*, 2022, doi: [10.1007/978-3-031-19821-2_37](https://doi.org/10.1007/978-3-031-19821-2_37).
<br>

\[9\] Y. Li, I. Boyadzhiev, Z. Liu, L. Shapiro, and A. Colburn, "BADGR: Bundle Adjustment Diffusion Conditioned by
Gradients for Wide-Baseline Floor Plan
Reconstruction," *Proc. CVPR*, 2025, doi: [10.1109/CVPR52734.2025.01564](https://doi.org/10.1109/CVPR52734.2025.01564).
<br>

\[10\] C. Liu, J. Wu, and Y. Furukawa, "FloorNet: A unified framework for floorplan
reconstruction from 3D scans," *Proc. ECCV*, 2018, doi: [10.1007/978-3-030-01231-1_13](https://doi.org/10.1007/978-3-030-01231-1_13).
<br>

\[11\] A. Monszpart, N. Mellado, G. J. Brostow, and N. J. Mitra, "RAPter: rebuilding man-made scenes with regular
arrangements of planes.," *ACM TOG*, 2015, doi: [10.1145/2766995](https://doi.org/10.1145/2766995).
<br>

\[12\] N. Nauata and Y. Furukawa, "Vectorizing world buildings: Planar graph
reconstruction by primitive detection and
relationship inference," *Proc. ECCV*, 2020, doi: [10.1007/978-3-030-58598-3_42](https://doi.org/10.1007/978-3-030-58598-3_42).
<br>

\[13\] G. Pintore, F. Ganovelli, A. J. Villanueva, and E. Gobbetti, "Automatic modeling of cluttered floorplans from
panoramic images," *Computer Graphics Forum*, 2019.
<br>

\[14\] G. Pintore, U. Shah, M. Agus, and E. Gobbetti, "NadirFloorNet: reconstructing multi-room floorplans
from a small set of registered panoramic images," *Proc. CVPR*, 2025, doi: [10.1109/CVPRW67362.2025.00186](https://doi.org/10.1109/CVPRW67362.2025.00186).
<br>

\[15\] G. Pintore, S. Jashari, M. Agus, and E. Gobbetti, "PanoFloor: Reconstruction and Immersive Exploration
of Large Multi-Room Scenes from a Minimal Set of
Registered Panoramic Images Using Denoised Density
Maps," *Proc. ISMAR*, 2025, doi: [10.1109/ISMAR67309.2025.00052](https://doi.org/10.1109/ISMAR67309.2025.00052).
<br>

\[16\] G. Pu, Y. Zhao, and Z. Lian, "Pano2Room: Novel View Synthesis from a Single
Indoor Panorama," *Proc. SIGGRAPH Asia Conference Papers*, 2024, doi: [10.1145/3680528.3687616](https://doi.org/10.1145/3680528.3687616).
<br>

\[17\] M. A. Shabani, W. Song, M. Odamaki, H. Fujiki, and Y. Furukawa, "Extreme structure from motion for indoor panoramas
without visual overlaps," *Proc. ICCV*, 2021, doi: [10.1109/ICCV48922.2021.00565](https://doi.org/10.1109/ICCV48922.2021.00565).
<br>

\[18\] N. Silberman, D. Hoiem, P. Kohli, and R. Fergus, "Indoor segmentation and support inference from rgbd
images," *Proc. ECCV*, 2012, doi: [10.1007/978-3-642-33715-4_54](https://doi.org/10.1007/978-3-642-33715-4_54).
<br>

\[19\] S. Stekovic, M. Rad, F. Fraundorfer, and V. Lepetit, "Montefloor: Extending MCTS for reconstructing
accurate large-scale floor plans," *Proc. CVPR*, 2021, doi: [10.1109/ICCV48922.2021.01573](https://doi.org/10.1109/ICCV48922.2021.01573).
<br>

\[20\] J. W. Su, K. Y. Tung, C. H. Peng, P. Wonka, and H. K. Chu, "SLIBO-Net: Floorplan Reconstruction via Slicing Box
Representation with Local Geometry Regularization," *Proc. NeurIPS*, 2023, url: [https://dl.acm.org/doi/abs/10.5555/3666122.3668240](https://dl.acm.org/doi/abs/10.5555/3666122.3668240).
<br>

\[21\] Y. Yue, T. Kontogianni, K. Schindler, and F. Engelmann, "Connecting the Dots: Floorplan Reconstruction Using
Two-Level Queries," *Proc. CVPR*, 2023, doi: [10.1109/CVPR52729.2023.00088](https://doi.org/10.1109/CVPR52729.2023.00088).
<br>


[↑ Back to Top](#table-of-contents)

---

## Novel view synthesis and immersive model exploration
While geometric and structural descriptions provide a strong foundation, they are not enough for interactive use. We review techniques for exploration from a single enriched panorama, including methods that recover stereo cues and motion parallax and support advanced navigation in sparsely-sampled multi-room environments, and approaches that go beyond plain navigation.


[↑ Back to Top](#table-of-contents)

---

### View synthesis from a single panorama



**References:**

\[1\] H. AlZayer, H. Lin, and K. Bala, "Autophoto: Aesthetic photo capture using
reinforcement learning," *Proc. IROS*, 2021, doi: [10.1109/IROS51168.2021.9636788](https://doi.org/10.1109/IROS51168.2021.9636788).
<br>

\[2\] B. Attal, S. Ling, A. Gokaslan, C. Richardt, and J. Tompkin, "MatryODShka: Real-time 6DoF video view synthesis
using multi-sphere images," *Proc. ECCV*, 2020, doi: [10.1007/978-3-030-58452-8_26](https://doi.org/10.1007/978-3-030-58452-8_26).
<br>

\[3\] M. T. Bagdasarian, P. Knoll, Y. Li, F. Barthel, A. Hilsmann, P. Eisert, and W. Morgenstern, "3DGS.zip: A survey on 3D gaussian splatting
compression methods," *Computer Graphics Forum*, 2025, doi: [10.1111/cgf.70078](https://doi.org/10.1111/cgf.70078).
<br>

\[4\] J. Bai, L. Huang, J. Guo, W. Gong, Y. Li, and Y. Guo, "360-GS: Layout-Guided Panoramic Gaussian Splatting
for Indoor Roaming," *Proc. 3DV*, 2025, doi: [10.1109/3DV66043.2025.00101](https://doi.org/10.1109/3DV66043.2025.00101).
<br>

\[5\] T. Bertel, N. D. Campbell, and C. Richardt, "MegaParallax: Casual 360° panoramas with
motion parallax," *IEEE TVCG*, 2019, doi: [10.1109/TVCG.2019.2898799](https://doi.org/10.1109/TVCG.2019.2898799).
<br>

\[6\] T. Bertel, M. Yuan, R. Lindroos, and C. Richardt, "OmniPhotos: Casual 360° VR Photography," *ACM TOG*, 2020, doi: [10.1145/3414685.3417770](https://doi.org/10.1145/3414685.3417770).
<br>

\[7\] S. Boorboor, Y. Kim, P. Hu, J. M. Moses, B. A. Colle, and A. E. Kaufman, "Submerse: Visualizing storm surge flooding
simulations in immersive display ecologies," *IEEE TVCG*, 2023, doi: [10.1109/TVCG.2023.3332511](https://doi.org/10.1109/TVCG.2023.3332511).
<br>

\[8\] P. Bourke, "Capturing omni-directional stereoscopic spherical
projections with a single camera," *Proc. IEEE VSMM*, 2010, doi: [10.1109/VSMM.2010.5665988](https://doi.org/10.1109/VSMM.2010.5665988).
<br>

\[9\] M. Broxton, J. Flynn, R. Overbeck, D. Erickson, P. Hedman, M. DuVall, J. Dourgarian, J. Busch, M. Whalen, and P. Debevec, "Immersive Light Field Video with a Layered Mesh
Representation," *ACM TOG*, 2020, doi: [10.1145/3386569.3392485](https://doi.org/10.1145/3386569.3392485).
<br>

\[10\] S. Cai, A. Obukhov, D. Dai, and L. Van Gool, "Pix2nerf: Unsupervised conditional P-GAN for
single image to neural radiance fields translation," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.00395](https://doi.org/10.1109/CVPR52688.2022.00395).
<br>

\[11\] D. Charatan, S. L. Li, A. Tagliasacchi, and V. Sitzmann, "PixelSplat: 3D Gaussian Splats from image pairs
for scalable generalizable 3D reconstruction," *Proc. CVPR*, 2024, doi: [10.1109/CVPR52733.2024.01840](https://doi.org/10.1109/CVPR52733.2024.01840).
<br>

\[12\] Z. Chen, Y. P. Cao, Y. C. Guo, C. Wang, Y. Shan, and S. H. Zhang, "PanoGRF: generalizable spherical radiance fields
for wide-baseline panoramas," *Proc. NeurIPS*, 2023, doi: [10.48550/arXiv.2306.01531](https://doi.org/10.48550/arXiv.2306.01531).
<br>

\[13\] J. Xu, J. Zheng, Y. Xu, R. Tang, and S. Gao, "PNVS Dataset," *Public dataset*, 2021, url: [https://github.com/bluestyle97/PNVS](https://github.com/bluestyle97/PNVS).
<br>

\[14\] C. Deng, C. Jiang, C. R. Qi, X. Yan, Y. Zhou, L. Guibas, and D. Anguelov, "NeRDI: Single-view NeRF synthesis with
language-guided diffusion as general image priors," *Proc. CVPR*, 2023, doi: [10.1109/CVPR52729.2023.01977](https://doi.org/10.1109/CVPR52729.2023.01977).
<br>

\[15\] M. Di Benedetto, F. Ganovelli, M. Balsa Rodriguez, A. Jaspe Villanueva, R. Scopigno, and E. Gobbetti, "ExploreMaps: Efficient Construction and Ubiquitous
Exploration of Panoramic View Graphs of Complex 3D
Environments," *Comput. Graph. Forum*, 2014, doi: [10.1111/cgf.12334](https://doi.org/10.1111/cgf.12334).
<br>

\[16\] Y. Dong, C. Fang, L. Bo, Z. Dong, and P. Tan, "PanoContext-Former: Panoramic total scene
understanding with a transformer," *Proc. CVPR*, 2024, doi: [10.1109/CVPR52733.2024.02653](https://doi.org/10.1109/CVPR52733.2024.02653).
<br>

\[17\] M. Feixas, M. Sbert, and F. González, "A unified information-theoretic framework for
viewpoint selection and mesh saliency," *ACM Trans. Appl. Percept.*, 2009, doi: [10.1145/1462055.1462056](https://doi.org/10.1145/1462055.1462056).
<br>

\[18\] A. Gokaslan, A. F. Cooper, J. Collins, L. Seguin, A. Jacobson, M. Patel, J. Frankle, C. Stephenson, and V. Kuleshov, "CommonCanvas: Open Diffusion Models Trained on
Creative-Commons Images," *Proc. CVPR*, 2024, doi: [10.1109/CVPR52733.2024.00788](https://doi.org/10.1109/CVPR52733.2024.00788).
<br>

\[19\] J. Gu, A. Trevithick, K. E. Lin, J. M. Susskind, C. Theobalt, L. Liu, and R. Ramamoorthi, "NeRFDiff: Single-image view synthesis with
NeRF-guided distillation from 3D-aware diffusion," *Proc. ICML*, 2023, url: [https://dl.acm.org/doi/abs/10.5555/3618408.3618881](https://dl.acm.org/doi/abs/10.5555/3618408.3618881).
<br>

\[20\] P. Hedman, S. Alsisan, R. Szeliski, and J. Kopf, "Casual 3D photography," *ACM Transactions on Graphics (TOG)*, 2017, doi: [10.1145/3130800.3130828](https://doi.org/10.1145/3130800.3130828).
<br>

\[21\] P. Hedman and J. Kopf, "Instant 3D Photography," *ACM TOG.*, 2018, doi: [10.1145/3197517.3201384](https://doi.org/10.1145/3197517.3201384).
<br>

\[22\] J. Huang, Z. Chen, D. Ceylan, and H. Jin, "6-DOF VR videos with a single 360-camera," *Proc. IEEE VR*, 2017, doi: [10.1109/VR.2017.7892229](https://doi.org/10.1109/VR.2017.7892229).
<br>

\[23\] H. Huang, Y. Chen, T. Zhang, and S. K. Yeung, "360Roam: Real-Time Indoor Roaming Using
Geometry-Aware 360° Radiance Fields," *arXiv preprint arXiv:2208.02705*, 2022, doi: [10.48550/arXiv.2208.02705](https://doi.org/10.48550/arXiv.2208.02705).
<br>

\[24\] A. Jain, M. Tancik, and P. Abbeel, "Putting NeRF on a diet: Semantically consistent
few-shot view synthesis," *Proc. ICCV*, 2021, doi: [10.1109/ICCV48922.2021.00583](https://doi.org/10.1109/ICCV48922.2021.00583).
<br>

\[25\] B. Kerbl, G. Kopanas, T. Leimkühler, and G. Drettakis, "3D Gaussian Splatting for Real-Time Radiance Field
Rendering," *ACM TOG*, 2023, doi: [10.1145/3592433](https://doi.org/10.1145/3592433).
<br>

\[26\] S. Kulkarni, P. Yin, and S. Scherer, "360FusionNeRF: Panoramic Neural Radiance Fields
with Joint Guidance," *Proc. IROS*, 2023, doi: [10.1109/IROS55552.2023.10341346](https://doi.org/10.1109/IROS55552.2023.10341346).
<br>

\[27\] D. Li, Y. Zhang, C. Häne, D. Tang, A. Varshney, and R. Du, "OmniSyn: Synthesizing 360 videos with wide-baseline
panoramas," *Proc. VRW*, 2022, doi: [10.48550/arXiv.2202.08752](https://doi.org/10.48550/arXiv.2202.08752).
<br>

\[28\] K. E. Lin, Z. Xu, B. Mildenhall, P. P. Srinivasan, Y. Hold-Geoffroy, S. DiVerdi, Q. Sun, K. Sunkavalli, and R. Ramamoorthi, "Deep multi depth panoramas for view synthesis," *Proc. ECCV*, 2020, doi: [10.1007/978-3-030-58601-0_20](https://doi.org/10.1007/978-3-030-58601-0_20).
<br>

\[29\] B. Luo, F. Xu, C. Richardt, and J. H. Yong, "Parallax360: Stereoscopic 360° Scene
Representation for Head-Motion Parallax," *IEEE TVCG*, 2018, doi: [10.1109/TVCG.2018.2794071](https://doi.org/10.1109/TVCG.2018.2794071).
<br>

\[30\] T. Marrinan and M. E. Papka, "Real-time omnidirectional stereo rendering:
generating 360° surround-view panoramic
images for comfortable immersive viewing," *IEEE TVCG*, 2021, doi: [10.1109/TVCG.2021.3067780](https://doi.org/10.1109/TVCG.2021.3067780).
<br>

\[31\] K. Matzen, M. F. Cohen, B. Evans, J. Kopf, and R. Szeliski, "Low-cost 360 Stereo Photography and Video Capture," *ACM TOG*, 2017, doi: [10.1145/3072959.3073645](https://doi.org/10.1145/3072959.3073645).
<br>

\[32\] B. Mildenhall, P. P. Srinivasan, M. Tancik, J. T. Barron, R. Ramamoorthi, and R. Ng, "NeRF: representing scenes as neural radiance fields
for view synthesis," *Commun. ACM*, 2021, doi: [10.1145/3503250](https://doi.org/10.1145/3503250).
<br>

\[33\] S. Peleg and M. Ben-Ezra, "Stereo panorama with a single camera," *Proc. CVPR*, 1999, doi: [10.1109/CVPR.1999.786969](https://doi.org/10.1109/CVPR.1999.786969).
<br>

\[34\] G. Pintore, F. Bettio, M. Agus, and E. Gobbetti, "Deep scene synthesis of Atlanta-world interiors
from a single omnidirectional image," *IEEE TVCG*, 2023, doi: [10.1109/TVCG.2023.3320219](https://doi.org/10.1109/TVCG.2023.3320219).
<br>

\[35\] G. Pintore, A. J. Villanueva, M. Hadwiget, E. Gobbetti, J. Schneider, and M. Agus, "PanoVerse: automatic generation of stereoscopic
environments from single indoor panoramic images for
Metaverse applications," *Proc. ACM Web3D*, 2023, doi: [10.1145/3611314.3615914](https://doi.org/10.1145/3611314.3615914).
<br>

\[36\] G. Pintore, A. Jaspe-Villanueva, M. Hadwiger, J. Schneider, M. Agus, F. Marton, F. Bettio, and E. Gobbetti, "Deep synthesis and exploration of omnidirectional
stereoscopic environments from a single surround-view
panoramic image," *Computers \& Graphics*, 2024, doi: [10.1016/j.cag.2024.103907](https://doi.org/10.1016/j.cag.2024.103907).
<br>

\[37\] G. Pintore, S. Jashari, M. Agus, and E. Gobbetti, "PanoFloor: Reconstruction and Immersive Exploration
of Large Multi-Room Scenes from a Minimal Set of
Registered Panoramic Images Using Denoised Density
Maps," *Proc. ISMAR*, 2025, doi: [10.1109/ISMAR67309.2025.00052](https://doi.org/10.1109/ISMAR67309.2025.00052).
<br>

\[38\] G. Pu, Y. Zhao, and Z. Lian, "Pano2Room: Novel View Synthesis from a Single
Indoor Panorama," *Proc. SIGGRAPH Asia Conference Papers*, 2024, doi: [10.1145/3680528.3687616](https://doi.org/10.1145/3680528.3687616).
<br>

\[39\] P. Rademacher and G. Bishop, "Multiple-center-of-projection images," *Proc. SIGGRAPH*, 1998, doi: [10.1145/280814.280871](https://doi.org/10.1145/280814.280871).
<br>

\[40\] M. Rey-Area and C. Richardt, "360° 3D Photos from a Single 360°
Input Image," *IEEE TVCG*, 2025, doi: [10.1109/TVCG.2025.3549538](https://doi.org/10.1109/TVCG.2025.3549538).
<br>

\[41\] R. Rombach, A. Blattmann, D. Lorenz, P. Esser, and B. Ommer, "High-resolution image synthesis with latent diffusion
models," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.01042](https://doi.org/10.1109/CVPR52688.2022.01042).
<br>

\[42\] A. Serrano, I. Kim, Z. Chen, S. DiVerdi, D. Gutierrez, A. Hertzmann, and B. Masia, "Motion parallax for 360 RGBD video," *IEEE TVCG*, 2019, doi: [10.1109/TVCG.2019.2898757](https://doi.org/10.1109/TVCG.2019.2898757).
<br>

\[43\] K. Song and L. Zhang, "Novel view synthesis with wide-baseline stereo pairs
based on local--global information," *Computers \& Graphics*, 2025, doi: [10.1016/j.cag.2024.104139](https://doi.org/10.1016/j.cag.2024.104139).
<br>

\[44\] G. Sridevi and S. Srinivas Kumar, "Image inpainting based on fractional-order nonlinear
diffusion for image reconstruction," *Circuits, Systems, and Signal Processing*, 2019, doi: [10.1007/s00034-019-01029-w](https://doi.org/10.1007/s00034-019-01029-w).
<br>

\[45\] R. Tucker and N. Snavely, "Single-view view synthesis with multiplane images," *Proc. CVPR*, 2020, doi: [10.1109/CVPR42600.2020.00063](https://doi.org/10.1109/CVPR42600.2020.00063).
<br>

\[46\] M. Tukur, G. Pintore, E. Gobbetti, J. Schneider, and M. Agus, "SPIDER: A framework for processing, editing and
presenting immersive high-resolution spherical indoor
scenes," *Graphical Models*, 2023, doi: [10.1016/j.gmod.2023.101182](https://doi.org/10.1016/j.gmod.2023.101182).
<br>

\[47\] T. Uchida, Y. Kanamori, and Y. Endo, "3D View Optimization for Improving Image
Aesthetics," *Proc. ICASSP*, 2025, doi: [10.1109/ICASSP49660.2025.10888966](https://doi.org/10.1109/ICASSP49660.2025.10888966).
<br>

\[48\] J. Waidhofer, R. Gadgil, A. Dickson, S. Zollmann, and J. Ventura, "PanoSynthVR: Toward Light-weight 360-Degree View
Synthesis from a Single Panoramic Input," *Proc. ISMAR*, 2022, doi: [10.1109/ISMAR55827.2022.00075](https://doi.org/10.1109/ISMAR55827.2022.00075).
<br>

\[49\] G. Wang, P. Wang, Z. Chen, W. Wang, C. C. Loy, and Z. Liu, "PERF: Panoramic Neural Radiance Field from a
Single Panorama," *IEEE TPAMI*, 2024, doi: [10.1109/TPAMI.2024.3387307](https://doi.org/10.1109/TPAMI.2024.3387307).
<br>

\[50\] Z. Wei, J. Zhang, X. Shen, Z. Lin, R. Mech, M. Hoai, and D. Samaras, "Good view hunting: Learning photo composition from
dense view pairs," *Proc. CVPR*, 2018, doi: [10.1109/CVPR.2018.00570](https://doi.org/10.1109/CVPR.2018.00570).
<br>

\[51\] O. Wiles, G. Gkioxari, R. Szeliski, and J. Johnson, "Synsin: End-to-end view synthesis from a single
image," *Proc. CVPR*, 2020, doi: [10.1109/CVPR42600.2020.00749](https://doi.org/10.1109/CVPR42600.2020.00749).
<br>

\[52\] D. Xie, P. Hu, X. Sun, S. Pirk, J. Zhang, R. Mech, and A. E. Kaufman, "GAIT: Generating aesthetic indoor tours with deep
reinforcement learning," *Proc. ICCV*, 2023, doi: [10.1109/ICCV51070.2023.00681](https://doi.org/10.1109/ICCV51070.2023.00681).
<br>

\[53\] J. Xu, B. Stenger, T. Kerola, and T. Tung, "Pano2CAD: Room Layout from a Single Panorama Image," *Proc. WACV*, 2017, doi: [10.1109/WACV.2017.46](https://doi.org/10.1109/WACV.2017.46).
<br>

\[54\] J. Xu, J. Zheng, Y. Xu, R. Tang, and S. Gao, "Layout-guided novel view synthesis from a single
indoor panorama," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.01617](https://doi.org/10.1109/CVPR46437.2021.01617).
<br>

\[55\] D. Xu, Y. Jiang, P. Wang, Z. Fan, H. Shi, and Z. Wang, "SinNeRF: Training neural radiance fields on complex
scenes from a single image," *Proc. ECCV*, 2022, doi: [10.1007/978-3-031-20047-2_42](https://doi.org/10.1007/978-3-031-20047-2_42).
<br>

\[56\] Y. Yang, S. Jin, R. Liu, and J. and Yu, "Automatic 3D Indoor Scene Modeling From Single
Panorama," *Proc. CVPR*, 2018, doi: [10.1109/CVPR.2018.00413](https://doi.org/10.1109/CVPR.2018.00413).
<br>

\[57\] J. Yu, Z. Lin, J. Yang, X. Shen, X. Lu, and T. S. Huang, "Free-form image inpainting with gated convolution," *Proc. ICCV*, 2019, doi: [10.1109/ICCV.2019.00457](https://doi.org/10.1109/ICCV.2019.00457).
<br>

\[58\] Y. Zeng, J. Fu, H. Chao, and B. Guo, "Learning pyramid-context encoder network for
high-quality image inpainting," *Proc. CVPR*, 2019, doi: [10.1109/CVPR.2019.00158](https://doi.org/10.1109/CVPR.2019.00158).
<br>

\[59\] C. Zhang, Z. Cui, C. Chen, S. Liu, B. Zeng, H. Bao, and Y. Zhang, "DeepPanoContext: Panoramic 3D scene understanding
with holistic scene context graph and relation-based
optimization," *Proc. ICCV*, 2021, doi: [10.1109/ICCV48922.2021.01240](https://doi.org/10.1109/ICCV48922.2021.01240).
<br>

\[60\] Q. Zhao, L. Wan, W. Feng, J. Zhang, and T. T. Wong, "Cube2Video: Navigate between cubic panoramas in
real-time," *IEEE Trans. Multimedia*, 2013, doi: [10.1109/TMM.2013.2280249](https://doi.org/10.1109/TMM.2013.2280249).
<br>

\[61\] T. Zhou, R. Tucker, J. Flynn, G. Fyffe, and N. Snavely, "Stereo Magnification: Learning View Synthesis Using
Multiplane Images," *ACM TOG*, 2018, doi: [10.1145/3197517.3201323](https://doi.org/10.1145/3197517.3201323).
<br>

\[62\] H. Zhou, X. Cheng, W. Yu, Y. Tian, and L. Yuan, "HoloDreamer: Holistic 3D panoramic world
generation from text descriptions," *arXiv preprint arXiv:2407.15187*, 2024, doi: [10.48550/arXiv.2407.15187](https://doi.org/10.48550/arXiv.2407.15187).
<br>


[↑ Back to Top](#table-of-contents)

---

### Dynamic modifications



**References:**

\[1\] A. Dolhasz, C. Ma, D. Gausebeck, K. Chen, G. Miller, L. Hayne, G. Hovden, A. Sabik, O. Brandt, and M. Slavcheva, "Defurnishing with X-Ray Vision: Joint Removal of
Furniture from Panoramas and Mesh," *Proc. CVPR*, 2025, doi: [10.1109/CVPRW67362.2025.00624](https://doi.org/10.1109/CVPRW67362.2025.00624).
<br>

\[2\] C. Fang, Y. Dong, K. Luo, X. Hu, R. Shrestha, and P. Tan, "Ctrl-Room: Controllable Text-to-3D Room Meshes
Generation with Layout Constraints," *Proc. 3DV*, 2025, doi: [10.1109/3DV66043.2025.00069](https://doi.org/10.1109/3DV66043.2025.00069).
<br>

\[3\] V. Gkitsas, V. Sterzentsenko, N. Zioulis, G. Albanis, and D. Zarpalas, "PanoDR: Spherical Panorama Diminished Reality for
Indoor Scenes," *Proc. CVPR Workshops*, 2021, doi: [10.1109/CVPRW53098.2021.00412](https://doi.org/10.1109/CVPRW53098.2021.00412).
<br>

\[4\] Z. Huang, J. He, J. Ye, L. Jiang, W. Li, Y. Chen, and T. Han, "Scene4U: Hierarchical Layered 3D Scene
Reconstruction from Single Panoramic Image for Your
Immerse Exploration," *Proc. CVPR*, 2025, doi: [10.1109/CVPR52734.2025.02489](https://doi.org/10.1109/CVPR52734.2025.02489).
<br>

\[5\] Z. Li, L. Wang, X. Huang, C. Pan, and J. Yang, "PhyIR: Physics-based Inverse Rendering for
Panoramic Indoor Images," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.01238](https://doi.org/10.1109/CVPR52688.2022.01238).
<br>

\[6\] R. Liang, Z. Gojcic, M. Nimier-David, D. Acuna, N. Vijaykumar, S. Fidler, and Z. Wang, "Photorealistic Object Insertion with Diffusion-Guided
Inverse Rendering," *Proc. ECCV*, 2024, doi: [10.1007/978-3-031-73030-6_25](https://doi.org/10.1007/978-3-031-73030-6_25).
<br>

\[7\] L. Lyu, V. Deschaintre, Y. Hold-Geoffroy, M. Hasan, J. S. Yoon, T. Leimkühler, C. Theobalt, and I. Georgiev, "IntrinsicEdit: Precise generative image
manipulation in intrinsic space," *ACM Trans. Graph.*, 2025, doi: [10.1145/3731173](https://doi.org/10.1145/3731173).
<br>

\[8\] G. Pintore, M. Agus, E. Almansa, and E. Gobbetti, "Instant Automatic Emptying of Panoramic Indoor
Scenes," *IEEE TVCG*, 2022, doi: [10.1109/TVCG.2022.3202999](https://doi.org/10.1109/TVCG.2022.3202999).
<br>

\[9\] G. Pu, Y. Zhao, and Z. Lian, "Pano2Room: Novel View Synthesis from a Single
Indoor Panorama," *Proc. SIGGRAPH Asia Conference Papers*, 2024, doi: [10.1145/3680528.3687616](https://doi.org/10.1145/3680528.3687616).
<br>

\[10\] U. Shah, M. Tukur, M. Alzubaidi, G. Pintore, E. Gobbetti, M. Househ, J. Schneider, and M. Agus, "MultiPanoWise: holistic deep architecture for
multi-task dense prediction from a single panoramic
image," *Proc. CVPRW - OmniCV*, 2024, doi: [10.1109/CVPRW63382.2024.00138](https://doi.org/10.1109/CVPRW63382.2024.00138).
<br>

\[11\] U. Shah, S. Jashari, M. Tukur, M. Househ, J. Schneider, G. Pintore, E. Gobbetti, and M. Agus, "Virtual Staging of Indoor Panoramic Images via
Multi-task Learning and Inverse Rendering," *IEEE CG\&A*, 2025, doi: [10.1109/MCG.2025.3605806](https://doi.org/10.1109/MCG.2025.3605806).
<br>

\[12\] S. Shen, Z. Bao, W. Xu, and C. Xiao, "IllumiDiff: Indoor Illumination Estimation From a
Single Image With Diffusion Model," *IEEE TVCG*, 2025, doi: [10.1109/TVCG.2025.3553853](https://doi.org/10.1109/TVCG.2025.3553853).
<br>

\[13\] M. Slavcheva, D. Gausebeck, K. Chen, D. Buchhofer, A. Sabik, C. Ma, S. Dhillon, O. Brandt, and A. Dolhasz, "An Empty Room is All We Want: Automatic Defurnishing
of Indoor Panoramas," *Proc. CVPRW*, 2024, doi: [10.1109/CVPRW63382.2024.00734](https://doi.org/10.1109/CVPRW63382.2024.00734).
<br>

\[14\] M. Tukur, A. U. Rehman, G. Pintore, E. Gobbetti, J. Schneider, and M. Agus, "PanoStyle: Semantic, Geometry-Aware and Shading
Independent Photorealistic Style Transfer for Indoor
Panoramic Scenes," *Proc. ICCVW*, 2023, doi: [10.1109/ICCVW60793.2023.00170](https://doi.org/10.1109/ICCVW60793.2023.00170).
<br>

\[15\] M. Tukur, S. Jashari, D. Abou Hassanain, F. Bettio, J. Schneider, G. Pintore, E. Gobbetti, and M. Agus, "PanoStyleVR: style-based similarity metrics for
Web-based immersive panoramic style transfer," *Proceedings of the 30th International Conference on
3D Web Technology*, 2025, doi: [10.1145/3746237.3746287](https://doi.org/10.1145/3746237.3746287).
<br>

\[16\] W. Wang, C. Qing, J. Tan, and X. Xu, "Multi-view Panoramic Image Style Transfer with
Multi-scale Attention and Global Sharing," *ACM Trans. Multimedia Comput. Commun. Appl.*, 2025, doi: [10.1145/3735137](https://doi.org/10.1145/3735137).
<br>

\[17\] X. Xing, K. Groh, S. Karaoglu, T. Gevers, and A. Bhattad, "Luminet: Latent intrinsics meets diffusion models for
indoor scene relighting," *Proc. CVPR*, 2025, doi: [10.1109/CVPR52734.2025.00050](https://doi.org/10.1109/CVPR52734.2025.00050).
<br>

\[18\] S. Yang, J. Tan, M. Zhang, T. Wu, G. Wetzstein, Z. Liu, and D. Lin, "LayerPano3D: Layered 3D Panorama for
Hyper-Immersive Scene Generation," *Proc. SIGGRAPH Conference Papers*, 2025, doi: [10.1145/3721238.3730643](https://doi.org/10.1145/3721238.3730643).
<br>

\[19\] W. Ye, C. Ji, Z. Chen, J. Gao, X. Huang, S. H. Zhang, W. Ouyang, T. He, C. Zhao, and G. Zhang, "DiffPano: Scalable and Consistent Text to Panorama
Generation with Spherical Epipolar-Aware Diffusion," *Proc. NeurIPS*, 2024, doi: [10.48550/arXiv.2410.24203](https://doi.org/10.48550/arXiv.2410.24203).
<br>

\[20\] W. Ye, Y. Wang, Y. Liu, W. Lin, and X. Xiang, "Panoramic Arbitrary Style Transfer with Deformable
Distortion Constraints," *Journal of Visual Communication and Image
Representation*, 2025, doi: [10.1016/j.jvcir.2024.104344](https://doi.org/10.1016/j.jvcir.2024.104344).
<br>

\[21\] H. X. Yu, H. Duan, C. Herrmann, W. T. Freeman, and J. Wu, "WonderWorld: Interactive 3D Scene Generation from
a Single Image," *Proc. CVPR*, 2025, doi: [10.1109/CVPR52734.2025.00555](https://doi.org/10.1109/CVPR52734.2025.00555).
<br>

\[22\] C. Zhang, Q. Wu, C. C. Gambardella, X. Huang, D. Phung, W. Ouyang, and J. Cai, "Taming Stable Diffusion for Text to 360°
Panorama Image Generation," *Proc. CVPR*, 2024, doi: [10.1109/CVPR52733.2024.00607](https://doi.org/10.1109/CVPR52733.2024.00607).
<br>

\[23\] T. Zhi, B. Chen, I. Boyadzhiev, S. B. Kang, M. Hebert, and S. G. Narasimhan, "Semantically supervised appearance decomposition for
virtual staging from a single panorama," *ACM TOG*, 2022, doi: [10.1145/3528223.3530148](https://doi.org/10.1145/3528223.3530148).
<br>

\[24\] S. Zhou, Z. Fan, D. Xu, H. Chang, P. Chari, T. Bharadwaj, S. You, Z. Wang, and A. Kadambi, "DreamScene360: Unconstrained Text-to-3D Scene
Generation with Panoramic Gaussian Splatting," *Proc. ECCV*, 2025, doi: [10.1007/978-3-031-72658-3_19](https://doi.org/10.1007/978-3-031-72658-3_19).
<br>


[↑ Back to Top](#table-of-contents)

---

### View synthesis



**References:**

\[1\] B. Attal, S. Ling, A. Gokaslan, C. Richardt, and J. Tompkin, "MatryODShka: Real-time 6DoF video view synthesis
using multi-sphere images," *Proc. ECCV*, 2020, doi: [10.1007/978-3-030-58452-8_26](https://doi.org/10.1007/978-3-030-58452-8_26).
<br>

\[2\] T. Bertel, M. Yuan, R. Lindroos, and C. Richardt, "OmniPhotos: Casual 360° VR Photography," *ACM TOG*, 2020, doi: [10.1145/3414685.3417770](https://doi.org/10.1145/3414685.3417770).
<br>

\[3\] S. Cai, A. Obukhov, D. Dai, and L. Van Gool, "Pix2nerf: Unsupervised conditional P-GAN for
single image to neural radiance fields translation," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.00395](https://doi.org/10.1109/CVPR52688.2022.00395).
<br>

\[4\] C. Deng, C. Jiang, C. R. Qi, X. Yan, Y. Zhou, L. Guibas, and D. Anguelov, "NeRDI: Single-view NeRF synthesis with
language-guided diffusion as general image priors," *Proc. CVPR*, 2023, doi: [10.1109/CVPR52729.2023.01977](https://doi.org/10.1109/CVPR52729.2023.01977).
<br>

\[5\] J. Gu, A. Trevithick, K. E. Lin, J. M. Susskind, C. Theobalt, L. Liu, and R. Ramamoorthi, "NeRFDiff: Single-image view synthesis with
NeRF-guided distillation from 3D-aware diffusion," *Proc. ICML*, 2023, url: [https://dl.acm.org/doi/abs/10.5555/3618408.3618881](https://dl.acm.org/doi/abs/10.5555/3618408.3618881).
<br>

\[6\] P. Hedman and J. Kopf, "Instant 3D Photography," *ACM TOG.*, 2018, doi: [10.1145/3197517.3201384](https://doi.org/10.1145/3197517.3201384).
<br>

\[7\] J. Huang, Z. Chen, D. Ceylan, and H. Jin, "6-DOF VR videos with a single 360-camera," *Proc. IEEE VR*, 2017, doi: [10.1109/VR.2017.7892229](https://doi.org/10.1109/VR.2017.7892229).
<br>

\[8\] A. Jain, M. Tancik, and P. Abbeel, "Putting NeRF on a diet: Semantically consistent
few-shot view synthesis," *Proc. ICCV*, 2021, doi: [10.1109/ICCV48922.2021.00583](https://doi.org/10.1109/ICCV48922.2021.00583).
<br>

\[9\] B. Kerbl, G. Kopanas, T. Leimkühler, and G. Drettakis, "3D Gaussian Splatting for Real-Time Radiance Field
Rendering," *ACM TOG*, 2023, doi: [10.1145/3592433](https://doi.org/10.1145/3592433).
<br>

\[10\] B. Luo, F. Xu, C. Richardt, and J. H. Yong, "Parallax360: Stereoscopic 360° Scene
Representation for Head-Motion Parallax," *IEEE TVCG*, 2018, doi: [10.1109/TVCG.2018.2794071](https://doi.org/10.1109/TVCG.2018.2794071).
<br>

\[11\] B. Mildenhall, P. P. Srinivasan, M. Tancik, J. T. Barron, R. Ramamoorthi, and R. Ng, "NeRF: representing scenes as neural radiance fields
for view synthesis," *Commun. ACM*, 2021, doi: [10.1145/3503250](https://doi.org/10.1145/3503250).
<br>

\[12\] G. Pintore, F. Ganovelli, E. Gobbetti, and R. Scopigno, "Mobile Mapping and Visualization of Indoor Structures
to Simplify Scene Understanding and Location
Awareness," *Proc. ECCV Workshops*, 2016.
<br>

\[13\] G. Pintore, F. Bettio, M. Agus, and E. Gobbetti, "Deep scene synthesis of Atlanta-world interiors
from a single omnidirectional image," *IEEE TVCG*, 2023, doi: [10.1109/TVCG.2023.3320219](https://doi.org/10.1109/TVCG.2023.3320219).
<br>

\[14\] G. Pintore, A. Jaspe-Villanueva, M. Hadwiger, J. Schneider, M. Agus, F. Marton, F. Bettio, and E. Gobbetti, "Deep synthesis and exploration of omnidirectional
stereoscopic environments from a single surround-view
panoramic image," *Computers \& Graphics*, 2024, doi: [10.1016/j.cag.2024.103907](https://doi.org/10.1016/j.cag.2024.103907).
<br>

\[15\] G. Pu, Y. Zhao, and Z. Lian, "Pano2Room: Novel View Synthesis from a Single
Indoor Panorama," *Proc. SIGGRAPH Asia Conference Papers*, 2024, doi: [10.1145/3680528.3687616](https://doi.org/10.1145/3680528.3687616).
<br>

\[16\] M. Tukur, G. Pintore, E. Gobbetti, J. Schneider, and M. Agus, "SPIDER: A framework for processing, editing and
presenting immersive high-resolution spherical indoor
scenes," *Graphical Models*, 2023, doi: [10.1016/j.gmod.2023.101182](https://doi.org/10.1016/j.gmod.2023.101182).
<br>

\[17\] J. Waidhofer, R. Gadgil, A. Dickson, S. Zollmann, and J. Ventura, "PanoSynthVR: Toward Light-weight 360-Degree View
Synthesis from a Single Panoramic Input," *Proc. ISMAR*, 2022, doi: [10.1109/ISMAR55827.2022.00075](https://doi.org/10.1109/ISMAR55827.2022.00075).
<br>

\[18\] G. Wang, P. Wang, Z. Chen, W. Wang, C. C. Loy, and Z. Liu, "PERF: Panoramic Neural Radiance Field from a
Single Panorama," *IEEE TPAMI*, 2024, doi: [10.1109/TPAMI.2024.3387307](https://doi.org/10.1109/TPAMI.2024.3387307).
<br>

\[19\] J. Xu, J. Zheng, Y. Xu, R. Tang, and S. Gao, "Layout-guided novel view synthesis from a single
indoor panorama," *Proc. CVPR*, 2021, doi: [10.1109/CVPR46437.2021.01617](https://doi.org/10.1109/CVPR46437.2021.01617).
<br>

\[20\] D. Xu, Y. Jiang, P. Wang, Z. Fan, H. Shi, and Z. Wang, "SinNeRF: Training neural radiance fields on complex
scenes from a single image," *Proc. ECCV*, 2022, doi: [10.1007/978-3-031-20047-2_42](https://doi.org/10.1007/978-3-031-20047-2_42).
<br>

\[21\] T. Zhou, R. Tucker, J. Flynn, G. Fyffe, and N. Snavely, "Stereo Magnification: Learning View Synthesis Using
Multiplane Images," *ACM TOG*, 2018, doi: [10.1145/3197517.3201323](https://doi.org/10.1145/3197517.3201323).
<br>


[↑ Back to Top](#table-of-contents)

---

### Exploration



**References:**

\[1\] T. Marrinan and M. E. Papka, "Real-time omnidirectional stereo rendering:
generating 360° surround-view panoramic
images for comfortable immersive viewing," *IEEE TVCG*, 2021, doi: [10.1109/TVCG.2021.3067780](https://doi.org/10.1109/TVCG.2021.3067780).
<br>

\[2\] K. Matzen, M. F. Cohen, B. Evans, J. Kopf, and R. Szeliski, "Low-cost 360 Stereo Photography and Video Capture," *ACM TOG*, 2017, doi: [10.1145/3072959.3073645](https://doi.org/10.1145/3072959.3073645).
<br>

\[3\] G. Pintore, F. Bettio, M. Agus, and E. Gobbetti, "Deep scene synthesis of Atlanta-world interiors
from a single omnidirectional image," *IEEE TVCG*, 2023, doi: [10.1109/TVCG.2023.3320219](https://doi.org/10.1109/TVCG.2023.3320219).
<br>

\[4\] G. Pintore, A. Jaspe-Villanueva, M. Hadwiger, J. Schneider, M. Agus, F. Marton, F. Bettio, and E. Gobbetti, "Deep synthesis and exploration of omnidirectional
stereoscopic environments from a single surround-view
panoramic image," *Computers \& Graphics*, 2024, doi: [10.1016/j.cag.2024.103907](https://doi.org/10.1016/j.cag.2024.103907).
<br>

\[5\] M. Tukur, A. U. Rehman, G. Pintore, E. Gobbetti, J. Schneider, and M. Agus, "PanoStyle: Semantic, Geometry-Aware and Shading
Independent Photorealistic Style Transfer for Indoor
Panoramic Scenes," *Proc. ICCVW*, 2023, doi: [10.1109/ICCVW60793.2023.00170](https://doi.org/10.1109/ICCVW60793.2023.00170).
<br>


[↑ Back to Top](#table-of-contents)

---

## Emerging pre-trained and foundation models
Single-panorama indoor inference is highly ill-posed and relies on strong priors typically learned from large annotated datasets, whose creation and use are costly and often task-specific. Foundation models trained on large-scale data are emerging as a possible alternative by enabling reusable representations that can be adapted to many tasks. In 360-degree analysis, they are mainly used either by repurposing standard vision models for omnidirectional problems or by developing models specifically designed for panoramic imagery.


**References:**

\[1\] T. B. Brown, B. Mann, N. Ryder, M. Subbiah, J. Kaplan, P. Dhariwal, A. Neelakantan, P. Shyam, G. Sastry, A. Askell, S. Agarwal, A. Herbert-Voss, G. Krueger, T. Henighan, R. Child, A. Ramesh, D. M. Ziegler, J. Wu, C. Winter, C. Hesse, M. Chen, E. Sigler, M. Litwin, S. Gray, B. Chess, J. Clark, C. Berner, S. McCandlish, A. Radford, I. Sutskever, and D. Amodei, "Language models are few-shot learners," *Proc. NeurIPS*, 2020, doi: [10.48550/arXiv.2005.14165](https://doi.org/10.48550/arXiv.2005.14165).
<br>

\[2\] M. Chen, A. Radford, R. Child, J. Wu, H. Jun, D. Luan, and I. Sutskever, "Generative pretraining from pixels," *Proc. PMLR*, 2020, url: [https://proceedings.mlr.press/v119/chen20s.html](https://proceedings.mlr.press/v119/chen20s.html).
<br>

\[3\] J. Kaplan, S. McCandlish, T. Henighan, T. B. Brown, B. Chess, R. Child, S. Gray, A. Radford, J. Wu, and D. Amodei, "Scaling laws for neural language models," *arXiv preprint arXiv:2001.08361*, 2020, doi: [10.48550/arXiv.2001.08361](https://doi.org/10.48550/arXiv.2001.08361).
<br>

\[4\] A. Kirillov, E. Mintun, N. Ravi, H. Mao, C. Rolland, L. Gustafson, T. Xiao, S. Whitehead, A. C. Berg, W. Y. Lo, P. Dollár, and R. Girshick, "Segment Anything," *Proc. ICCV*, 2023, doi: [10.1109/ICCV51070.2023.00371](https://doi.org/10.1109/ICCV51070.2023.00371).
<br>

\[5\] H. Naveed, A. U. Khan, S. Qiu, M. Saqib, S. Anwar, M. Usman, N. Akhtar, N. Barnes, and A. Mian, "A Comprehensive Overview of Large Language Models," *ACM Trans. Intell. Syst. Technol.*, 2025, doi: [10.1145/3744746](https://doi.org/10.1145/3744746).
<br>

\[6\] A. Radford, J. W. Kim, C. Hallacy, A. Ramesh, G. Goh, S. Agarwal, G. Sastry, A. Askell, P. Mishkin, J. Clark, G. Krueger, and I. Sutskever, "Learning Transferable Visual Models From Natural
Language Supervision," *Proc. ICML*, 2021, url: [https://icml.cc/virtual/2021/oral/9194](https://icml.cc/virtual/2021/oral/9194).
<br>

\[7\] M. Xu, Z. Zhang, H. Hu, J. Wang, L. Wang, F. Wei, X. Bai, and Z. Liu, "End-to-End Semi-Supervised Object Detection with Soft
Teacher," *Proc. ICCV*, 2021, doi: [10.1109/ICCV48922.2021.00305](https://doi.org/10.1109/ICCV48922.2021.00305).
<br>


[↑ Back to Top](#table-of-contents)

---

### Transfer and composition of conventional vision foundation models for 360-degree tasks



**References:**

\[1\] H. Ai, Z. Cao, Y. P. Cao, Y. Shan, and L. Wang, "HRDFuse: Monocular 360° Depth Estimation by
Collaboratively Learning Holistic-With-Regional Depth
Distributions," *Proc. CVPR*, 2023, doi: [10.1109/CVPR52729.2023.01275](https://doi.org/10.1109/CVPR52729.2023.01275).
<br>

\[2\] H. Ai, Z. Cao, and L. Wang, "A Survey of Representation Learning, Optimization
Strategies, and Applications for Omnidirectional
Vision," *Int J Comput Vis*, 2025, doi: [10.1007/s11263-025-02391-w](https://doi.org/10.1007/s11263-025-02391-w).
<br>

\[3\] Z. Cao, J. Zhu, H. Ai, L. Jiang, Y. Lyu, and H. Xiong, "ST$^2$360D: Spatial-to-Temporal Consistency for
Training-free 360 Monocular Depth Estimation," *Proc. NeurIPS*, 2025, url: [https://neurips.cc/virtual/2025/loc/san-diego/poster/
117039](https://neurips.cc/virtual/2025/loc/san-diego/poster/
117039).
<br>

\[4\] S. Chen, H. Guo, S. Zhu, F. Zhang, Z. Huang, J. Feng, and B. Kang, "Video Depth Anything: Consistent Depth Estimation
for Super-Long Videos," *Proc. CVPR*, 2025, doi: [10.1109/CVPR52734.2025.02126](https://doi.org/10.1109/CVPR52734.2025.02126).
<br>

\[5\] A. Gokaslan, A. F. Cooper, J. Collins, L. Seguin, A. Jacobson, M. Patel, J. Frankle, C. Stephenson, and V. Kuleshov, "CommonCanvas: Open Diffusion Models Trained on
Creative-Commons Images," *Proc. CVPR*, 2024, doi: [10.1109/CVPR52733.2024.00788](https://doi.org/10.1109/CVPR52733.2024.00788).
<br>

\[6\] H. Jiang, Z. Song, Z. Lou, R. Xu, and M. Tan, "Depth Anything in 360°: Towards Scale
Invariance in the Wild," *arXiv preprint arXiv:2512.22819*, 2025, doi: [10.48550/arXiv.2512.22819](https://doi.org/10.48550/arXiv.2512.22819).
<br>

\[7\] S. Kulkarni, P. Yin, and S. Scherer, "360FusionNeRF: Panoramic Neural Radiance Fields
with Joint Guidance," *Proc. IROS*, 2023, doi: [10.1109/IROS55552.2023.10341346](https://doi.org/10.1109/IROS55552.2023.10341346).
<br>

\[8\] Y. Li, Y. Guo, Z. Yan, X. Huang, Y. Duan, and L. Ren, "Omnifusion: 360 monocular depth estimation via
geometry-aware fusion," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.00282](https://doi.org/10.1109/CVPR52688.2022.00282).
<br>

\[9\] X. Luo, J. B. Huang, R. Szeliski, K. Matzen, and J. Kopf, "Consistent video depth estimation," *ACM Trans. Graph.*, 2020, doi: [10.1145/3386569.3392377](https://doi.org/10.1145/3386569.3392377).
<br>

\[10\] C. H. Peng and J. Zhang, "High-Resolution Depth Estimation for 360°
Panoramas through Perspective and Panoramic Depth
Images Registration," *Proc. WACV*, 2023, doi: [10.1109/WACV56688.2023.00313](https://doi.org/10.1109/WACV56688.2023.00313).
<br>

\[11\] G. Pu, Y. Zhao, and Z. Lian, "Pano2Room: Novel View Synthesis from a Single
Indoor Panorama," *Proc. SIGGRAPH Asia Conference Papers*, 2024, doi: [10.1145/3680528.3687616](https://doi.org/10.1145/3680528.3687616).
<br>

\[12\] M. Rey-Area, M. Yuan, and C. Richardt, "360MonoDepth: High-Resolution 360° Monocular
Depth Estimation," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.00374](https://doi.org/10.1109/CVPR52688.2022.00374).
<br>

\[13\] M. Rey-Area and C. Richardt, "360° 3D Photos from a Single 360°
Input Image," *IEEE TVCG*, 2025, doi: [10.1109/TVCG.2025.3549538](https://doi.org/10.1109/TVCG.2025.3549538).
<br>

\[14\] R. Rombach, A. Blattmann, D. Lorenz, P. Esser, and B. Ommer, "High-resolution image synthesis with latent diffusion
models," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.01042](https://doi.org/10.1109/CVPR52688.2022.01042).
<br>

\[15\] Z. Shen, Z. Zheng, C. Lin, L. Nie, K. Liao, S. Zheng, and Y. Zhao, "Disentangling Orthogonal Planes for Indoor Panoramic
Room Layout Estimation with Cross-Scale Distortion
Awareness," *Proc. CVPR*, 2023, doi: [10.1109/CVPR52729.2023.01663](https://doi.org/10.1109/CVPR52729.2023.01663).
<br>

\[16\] N. H. A. Wang and Y. L. Liu, "Depth anywhere: Enhancing 360 monocular depth
estimation via perspective distillation and unlabeled
data augmentation," *Proc. NeurIPS*, 2024, url: [https://dl.acm.org/doi/10.5555/3737916.3741972](https://dl.acm.org/doi/10.5555/3737916.3741972).
<br>

\[17\] L. Yang, B. Kang, Z. Huang, X. Xu, J. Feng, and H. Zhao, "Depth Anything: Unleashing the Power of Large-Scale
Unlabeled Data," *Proc. CVPR*, 2024, doi: [10.1109/CVPR52733.2024.00987](https://doi.org/10.1109/CVPR52733.2024.00987).
<br>

\[18\] L. Yang, B. Kang, Z. Huang, Z. Zhao, X. Xu, J. Feng, and H. Zhao, "Depth Anything V2," *Proc. NeurIPS*, 2024, doi: [10.52202/079017-0688](https://doi.org/10.52202/079017-0688).
<br>


[↑ Back to Top](#table-of-contents)

---

### Native 360-degree foundation models



**References:**

\[1\] Z. Cao, J. Zhu, W. Zhang, H. Ai, H. Bai, H. Zhao, and L. Wang, "PanDA: Towards Panoramic Depth Anything with
Unlabeled Panoramas and Mobius Spatial Augmentation," *Proc. CVPR*, 2025, doi: [10.1109/CVPR52734.2025.00100](https://doi.org/10.1109/CVPR52734.2025.00100).
<br>

\[2\] B. Cottier, R. Rahman, L. Fattorini, N. Maslej, T. Besiroglu, and D. Owen, "The rising costs of training frontier AI models," *arXiv preprint arXiv:2405.21015*, 2025, doi: [10.48550/arXiv.2405.21015](https://doi.org/10.48550/arXiv.2405.21015).
<br>

\[3\] H. Jiang, Z. Song, Z. Lou, R. Xu, and M. Tan, "Depth Anything in 360°: Towards Scale
Invariance in the Wild," *arXiv preprint arXiv:2512.22819*, 2025, doi: [10.48550/arXiv.2512.22819](https://doi.org/10.48550/arXiv.2512.22819).
<br>

\[4\] X. Liu, T. Zhou, C. Wang, Y. Wang, Y. Wang, Q. Cao, W. Du, Y. Yang, J. He, Y. Qiao, and others, "Toward the unification of generative and
discriminative visual foundation model: a survey," *The Visual Computer*, 2025, doi: [10.1007/s00371-024-03608-8](https://doi.org/10.1007/s00371-024-03608-8).
<br>

\[5\] N. Maslej, L. Fattorini, R. Perrault, Y. Gil, V. Parli, N. Kariuki, E. Capstick, A. Reuel, E. Brynjolfsson, J. Etchemendy, and others, "Artificial intelligence index report 2025," *arXiv preprint arXiv:2504.07139*, 2025, doi: [10.48550/arXiv.2310.03715](https://doi.org/10.48550/arXiv.2310.03715).
<br>

\[6\] M. Wallingford, A. Bhattad, A. Kusupati, V. Ramanujan, M. Deitke, A. Kembhavi, R. Mottaghi, W. C. Ma, and A. Farhadi, "From an image to a scene: Learning to imagine the
world from a million 360 videos," *Proc. NeurIPS*, 2024, doi: [10.48550/arXiv.2412.07770](https://doi.org/10.48550/arXiv.2412.07770).
<br>

\[7\] T. Wiedemer, Y. Li, P. Vicol, S. S. Gu, N. Matarese, K. Swersky, B. Kim, P. Jaini, and R. Geirhos, "Video models are zero-shot learners and reasoners," *arXiv preprint arXiv:2509.20328*, 2025, doi: [10.48550/arXiv.2509.20328](https://doi.org/10.48550/arXiv.2509.20328).
<br>

\[8\] L. Yang, B. Kang, Z. Huang, X. Xu, J. Feng, and H. Zhao, "Depth Anything: Unleashing the Power of Large-Scale
Unlabeled Data," *Proc. CVPR*, 2024, doi: [10.1109/CVPR52733.2024.00987](https://doi.org/10.1109/CVPR52733.2024.00987).
<br>

\[9\] L. Yang, B. Kang, Z. Huang, Z. Zhao, X. Xu, J. Feng, and H. Zhao, "Depth Anything V2," *Proc. NeurIPS*, 2024, doi: [10.52202/079017-0688](https://doi.org/10.52202/079017-0688).
<br>


[↑ Back to Top](#table-of-contents)

---

### Opportunities and Limitations
Foundation models are increasingly used for single-view 360-degree inference by enabling knowledge reuse and improved generalization, though most approaches adapt general vision models rather than 360-specific ones. However, their high training and deployment cost, in terms of data, computation, and energy, and the growing concentration within large industrial actors, place them largely beyond the reach of individual researchers. Moreover, inference cost is typically high. Lightweight task-specific models are thus likely to remain important alongside them.


**References:**

\[1\] R. Bommasani, S. Kapoor, K. Klyman, S. Longpre, A. Ramaswami, D. Zhang, M. Schaake, D. E. Ho, A. Narayanan, and P. Liang, "Considerations for governing open foundation models," *Science*, 2024, doi: [10.1126/science.adp1848](https://doi.org/10.1126/science.adp1848).
<br>

\[2\] N. Maslej, L. Fattorini, R. Perrault, Y. Gil, V. Parli, N. Kariuki, E. Capstick, A. Reuel, E. Brynjolfsson, J. Etchemendy, and others, "Artificial intelligence index report 2025," *arXiv preprint arXiv:2504.07139*, 2025, doi: [10.48550/arXiv.2310.03715](https://doi.org/10.48550/arXiv.2310.03715).
<br>


[↑ Back to Top](#table-of-contents)

---

## Applications
Panorama-first workflows are enabling practical applications across domains such as AEC/BIM documentation, education and safety training, cultural heritage dissemination, remote collaboration, and real estate marketing, where plausible and easily captured models are often more valuable than precise measurements.


**References:**

\[1\] M. De Fino, C. Ceppi, and F. Fatiguso, "Virtual tours and informational models for improving
territorial attractiveness and the smart management
of architectural heritage: The 3D-IMP-ACT project," *The International Archives of the Photogrammetry,
Remote Sensing and Spatial Information Sciences*, 2020, doi: [10.5194/isprs-archives-XLIV-M-1-2020-473-2020](https://doi.org/10.5194/isprs-archives-XLIV-M-1-2020-473-2020).
<br>

\[2\] M. De Fino, S. Bruno, and F. Fatiguso, "Dissemination, assessment and management of historic
buildings by thematic virtual tours and 3D models," *Virtual Archaeology Review*, 2022, doi: [10.4995/var.2022.15426](https://doi.org/10.4995/var.2022.15426).
<br>

\[3\] R. Dieb, A. Alsalloum, and N. Webb, "Interactive 360° media for the dissemination
of endangered world heritage sites: the ancient city
of Palmyra in Syria," *Built Heritage*, 2024, doi: [10.1186/s43238-024-00126-3](https://doi.org/10.1186/s43238-024-00126-3).
<br>

\[4\] R. Eiris, M. Gheisari, and B. Esmaeili, "Desktop-based safety training using 360-degree
panorama and static virtual reality techniques: A
comparative experimental study," *Automation in construction*, 2020, doi: [10.1016/j.autcon.2019.102969](https://doi.org/10.1016/j.autcon.2019.102969).
<br>

\[5\] R. Eiris, J. Wen, and M. Gheisari, "iVisit-Collaborate: Collaborative problem-solving in
multiuser 360-degree panoramic site visits," *Computers \& Education*, 2022, doi: [10.1016/j.compedu.2021.104365](https://doi.org/10.1016/j.compedu.2021.104365).
<br>

\[6\] X. Fang, H. Li, H. Wu, L. Fan, T. Kong, and Y. Wu, "A fast end-to-end method for automatic interior
progress evaluation using panoramic images," *Engineering Applications of Artificial Intelligence*, 2023, doi: [10.1016/j.engappai.2023.106733](https://doi.org/10.1016/j.engappai.2023.106733).
<br>

\[7\] J. Isingizwe, R. Eiris, and A. J. Al-Bayati, "Enhancing safety training engagement through
immersive storytelling: A case study in the
residential construction," *Safety Science*, 2024, doi: [10.1016/j.ssci.2024.106631](https://doi.org/10.1016/j.ssci.2024.106631).
<br>

\[8\] M. Khan, Y. Qiu, Y. Cong, J. Abu-Khalaf, D. Suter, and B. Rosenhahn, "PanoSCU: A Simulation-Based Dataset for Panoramic
Indoor Scene Understanding," *IEEE Access*, 2025, doi: [10.1109/ACCESS.2025.3561055](https://doi.org/10.1109/ACCESS.2025.3561055).
<br>

\[9\] J. S. Kim, T. Leathem, and J. Liu, "Comparing virtual reality modalities and 360
photography in a construction management classroom," *55th ASC Annual International Conference Proceedings*, 2019, url: [http://ascpro0.ascweb.org/archives/cd/2019/paper/
CERT284002019.pdf](http://ascpro0.ascweb.org/archives/cd/2019/paper/
CERT284002019.pdf).
<br>

\[10\] Z. Li, L. Wang, X. Huang, C. Pan, and J. Yang, "PhyIR: Physics-based Inverse Rendering for
Panoramic Indoor Images," *Proc. CVPR*, 2022, doi: [10.1109/CVPR52688.2022.01238](https://doi.org/10.1109/CVPR52688.2022.01238).
<br>

\[11\] G. Pintore, R. Pintus, F. Ganovelli, R. Scopigno, and E. Gobbetti, "Recovering 3D existing-conditions of indoor
structures from spherical images," *Computers \& Graphics*, 2018, doi: [10.1016/j.cag.2018.09.013](https://doi.org/10.1016/j.cag.2018.09.013).
<br>

\[12\] G. Pintore, M. Agus, E. Almansa, and E. Gobbetti, "Instant Automatic Emptying of Panoramic Indoor
Scenes," *IEEE TVCG*, 2022, doi: [10.1109/TVCG.2022.3202999](https://doi.org/10.1109/TVCG.2022.3202999).
<br>

\[13\] U. Shah, S. Jashari, M. Tukur, M. Househ, J. Schneider, G. Pintore, E. Gobbetti, and M. Agus, "Virtual Staging of Indoor Panoramic Images via
Multi-task Learning and Inverse Rendering," *IEEE CG\&A*, 2025, doi: [10.1109/MCG.2025.3605806](https://doi.org/10.1109/MCG.2025.3605806).
<br>

\[14\] Y. Shinde, K. Lee, B. Kiper, M. Simpson, and S. Hasanzadeh, "A Systematic Literature Review on 360°
Panoramic Applications in Architecture, Engineering,
and Construction (AEC) Industry," *Journal of Information Technology in Construction
(ITcon)*, 2023.
<br>

\[15\] P. Subramanian and M. Gheisari, "Using 360-degree panoramic photogrammetry and laser
scanning techniques to create point cloud data: A
comparative pilot study," *Proc. Associated Schools of Construction Annual
Conference*, 2019, url: [http://ascpro0.ascweb.org/archives/cd/2019/paper/
CPRT305002019.pdf](http://ascpro0.ascweb.org/archives/cd/2019/paper/
CPRT305002019.pdf).
<br>

\[16\] M. Tukur, A. U. Rehman, G. Pintore, E. Gobbetti, J. Schneider, and M. Agus, "PanoStyle: Semantic, Geometry-Aware and Shading
Independent Photorealistic Style Transfer for Indoor
Panoramic Scenes," *Proc. ICCVW*, 2023, doi: [10.1109/ICCVW60793.2023.00170](https://doi.org/10.1109/ICCVW60793.2023.00170).
<br>

\[17\] M. Tukur, S. Jashari, M. Alzubaidi, B. A. Salami, Y. Boraey, S. Yong, D. Saleh, G. Pintore, E. Gobbetti, J. Schneider, N. Fetais, and M. Agus, "Panoramic Imaging in Immersive Extended Reality: A
Scoping Review of Technologies, Applications,
Perceptual Studies, and User Experience Challenges," *Frontiers in Virtual Reality*, 2025, doi: [10.3389/frvir.2025.1622605](https://doi.org/10.3389/frvir.2025.1622605).
<br>

\[18\] S. Wang, Y. Lu, Z. Xia, Z. Chen, Y. Wang, L. Zhong, and T. Zhong, "Integrating visual-SLAM and multi-view panoramas
for efficient indoor 3D layout reconstruction in
building projects," *Advanced Engineering Informatics*, 2025, doi: [10.1016/j.aei.2025.103629](https://doi.org/10.1016/j.aei.2025.103629).
<br>

\[19\] W. Wang, C. Qing, J. Tan, and X. Xu, "Multi-view Panoramic Image Style Transfer with
Multi-scale Attention and Global Sharing," *ACM Trans. Multimedia Comput. Commun. Appl.*, 2025, doi: [10.1145/3735137](https://doi.org/10.1145/3735137).
<br>

\[20\] Y. Xia, S. Weng, S. Yang, J. Liu, C. Zhu, M. Teng, Z. Jia, H. Jiang, and B. Shi, "PanoWan: Lifting Diffusion Video Generation Models
to 360° with Latitude/Longitude-aware
Mechanisms," *arXiv preprint arXiv:2505.22016*, 2025, doi: [10.48550/arXiv.2505.22016](https://doi.org/10.48550/arXiv.2505.22016).
<br>

\[21\] S. Yang, J. Tan, M. Zhang, T. Wu, G. Wetzstein, Z. Liu, and D. Lin, "LayerPano3D: Layered 3D Panorama for
Hyper-Immersive Scene Generation," *Proc. SIGGRAPH Conference Papers*, 2025, doi: [10.1145/3721238.3730643](https://doi.org/10.1145/3721238.3730643).
<br>

\[22\] W. Ye, Y. Wang, Y. Liu, W. Lin, and X. Xiang, "Panoramic Arbitrary Style Transfer with Deformable
Distortion Constraints," *Journal of Visual Communication and Image
Representation*, 2025, doi: [10.1016/j.jvcir.2024.104344](https://doi.org/10.1016/j.jvcir.2024.104344).
<br>

\[23\] T. Zhi, B. Chen, I. Boyadzhiev, S. B. Kang, M. Hebert, and S. G. Narasimhan, "Semantically supervised appearance decomposition for
virtual staging from a single panorama," *ACM TOG*, 2022, doi: [10.1145/3528223.3530148](https://doi.org/10.1145/3528223.3530148).
<br>

\[24\] S. Zhou, Z. Fan, D. Xu, H. Chang, P. Chari, T. Bharadwaj, S. You, Z. Wang, and A. Kadambi, "DreamScene360: Unconstrained Text-to-3D Scene
Generation with Panoramic Gaussian Splatting," *Proc. ECCV*, 2025, doi: [10.1007/978-3-031-72658-3_19](https://doi.org/10.1007/978-3-031-72658-3_19).
<br>


[↑ Back to Top](#table-of-contents)

---
