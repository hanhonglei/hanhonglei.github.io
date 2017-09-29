---
layout: post
title:  "Paper discussion - Saliency in VR: How do people explore virtual environments?"
date:   2017-09-28
categories: article paper research saliency vr review
---
# [Saliency in VR: How do people explore virtual environments?](https://arxiv.org/abs/1612.04335)

## Main contributions
Using the recorded data, we demonstrate that existing saliency models can be adapted to predict saliency for VR, as well as other factors that give insights
into how people explore virtual environments. We will make all captured data public, to foster future research on this topic.

## The results in the paper
1. Saliency in VR seems to be in good agreement with saliency in conventional displays; as a consequence, existing saliency predictors can be applied to VR using a few simple modifications described in this paper. 
2. Head and gaze interaction are coupled in natural or VR viewing conditions, but they differ when users fixate and when they do not – the collected data may enable models to be learned that could approximate gaze movement from head and image information alone, without costly eye trackers. 
3. While our simple time-dependent model can approximate where people look within the first few seconds after entering a new scene, accurate prediction is not possible for more than a few seconds at the moment.

## Details
1. They have recorded 780 head and gaze trajectories from 86 users exploring omnidirectional stereo panoramas using VR head-mounted displays.
2. Use panorama to denote VR immersive scene.
3. Try to compare how visual attention and saliency in VR are different from conventional viewing conditions.
4. Showed how to adapt existing saliency predictors to VR.

## Notes
1. It is crucial to understand how users explore virtual environments and to define what constitutes saliency in these immersive applications.
2. Recently, advances in machine learning and particularly convolutional neuronal networks (CNNs) have fostered the convergence of topdown and bottom-up features for saliency prediction, producing more accurate models [37, 41, 38, 32, 27].
3. What makes VR different from desktop viewing conditions is the fact that head orientation is used as a natural interface to control perspective.
4. For more information on user behavior in VR, we refer to Ruhland et al. [^33]
5. The paper structure of user data study. In data capture section, use Conditions, Participants, and Procedure.
6. For experiments in VR, 86 users participated in our study (68 male, 18 female, age 17-22).
7. Equipped with a pupil-labs1 stereoscopic eye tracker recording at 120 Hz. The DK2 offers a field of view of 106° x 87°.
8. In desktop condition, they recorded where the users interactively place the virtual camera in the panorama as a proxy for head orientation.
9. We used thresholding based on dispersion and duration of the fixations[34]. For the VR experiments, we set the minimum duration to 150 ms [^34] and the maximum dispersion to 1° [^1].
10. Tobii eyeX has significant jitter led to skipped fixations.
11. Comparison metrics. We use the Inter-Observer Visual Congruency (IOVC) metric [^25] when investigating whether two groups of users fixated in the same regions of a scene. Measuring the percentage of the other set of fixations that fall in the top 25% most salient regions of that map and vice versa, then
averaging the two percentages. For comparisons between continuous saliency maps, we use the Pearson correlation (CC) metric, and the Earth’s Mover Distance
(EMD).
12. Users tend to fixate around the equator of the panoramas, with very few fixations in latitudes far from the equator.
13. Following a similar procedure to Judd et al. [^19] we analyze the consistency of human fixations by computing the Shannon entropy of the saliency map.
14. The starting condition has little impact on which regions of the scene are attended to over the course of 30 seconds.
15. Our data reveals that head follows gaze with an average delay of 58 ms, where the largest cross-correlation is observed. This is consistent with previous works [13, 10] reporting delays in head movement when shifting to a non-predictable target.
16. when users are not fixating, head speeds are above average.
17. Whenever head speed falls below the threshold of 19°, the likelihood that the user is currently fixating is high.
18. We conclude that head saliency maps, which are easily obtainable with inertial measurement units, can be a valuable tool to analyze the approximate regions that users attend to in a scene without the need for additional eye-tracking hardware.

[^1]: P. Blignaut. Fixation identification: The optimum threshold for a dispersion algorithm. Attention, Perception, & Psychophysics, 71(4):881–895, 2009. 3
[^2]: A. Borji and L. Itti. State-of-the-art in visual attention modeling. IEEE Trans. PAMI, 35(1):185–207, 2013. 1
[3] Z. Bylinskii, T. Judd, A. Borji, L. Itti, F. Durand, A. Oliva,
and A. Torralba. Mit saliency benchmark. 6
[4] Z. Bylinskii, T. Judd, A. Oliva, A. Torralba, and F. Durand.
What do different evaluation metrics tell us about saliency
models? arXiv preprint arXiv:1604.03605, 2016. 2, 4
[5] Z. Bylinskii, A. Recasens, A. Borji, A. Oliva, A. Torralba,
and F. Durand. Where should saliency models look next? In
Proc. ECCV, pages 1–16, 2016. 1
[6] S. Chaabouni, J. Benois-Pineau, O. Hadar, and C. B. Amar.
Deep learning for saliency prediction in natural video. arXiv
preprint arXiv:1604.08010, 2016. 2
[7] M.-M. Cheng, N. J. Mitra, X. Huang, P. H. Torr, and S.-M.
Hu. Global contrast based salient region detection. IEEE
Trans. PAMI, 37(3):569–582, 2015. 2
[8] R. Cong, J. Lei, C. Zhang, Q. Huang, X. Cao, and C. Hou.
Saliency detection for stereoscopic images based on depth
confidence analysis and multiple cues fusion. IEEE Signal
Processing Letters, 23(6):819–823, 2016. 2
[9] M. Cornia, L. Baraldi, G. Serra, and R. Cucchiara. A deep
multi-level network for saliency prediction. In Proc. ICPR,
2016. 7
[10] A. Doshi and M. M. Trivedi. Head and eye gaze dynamics
during visual attention shifts in complex environments.
Journal of Vision, 12(2):9, 2012. 6
[11] A. T. Duchowski, N. Cournia, and H. Murphy. Gazecontingent
displays: a review. Cyberpsychol Behav.,
7(6):621–34, 2004. 2
[12] M. Feng, A. Borji, and H. Lu. Fixation prediction with a
combined model of bottom-up saliency and vanishing point.
In Proc. IEEE WACV, pages 1–7. IEEE, 2016. 1
[13] E. G. Freedman. Coordination of the eyes and head during
visual orienting. Experimental brain research, 190(4):369–
387, 2008. 2, 6
[14] A. Gibaldi, M. Vanegas, P. J. Bex, and G. Maiello. Evaluation
of the tobii eyex eye tracking controller and matlab
toolkit for research. Behavior Research Methods, pages 1–
24, 2016. 3
[15] S. Goferman, L. Zelnik-Manor, and A. Tal. Context-aware
saliency detection. IEEE Trans. PAMI, 34(10):1915–1926,
2012. 2
[16] F. Guo, J. Shen, and X. Li. Learning to detect stereo saliency.
In Proc. IEEE ICME, pages 1–6. IEEE, 2014. 2
[17] L. Itti, C. Koch, E. Niebur, et al. A model of saliency-based
visual attention for rapid scene analysis. IEEE Trans. PAMI,
20(11):1254–1259, 1998. 2
[18] Y. Jia and M. Han. Category-independent object-level
saliency detection. In Proc. IEEE CVPR, pages 1761–1768,
2013. 2
[^19] T. Judd, K. Ehinger, F. Durand, and A. Torralba. Learning to
predict where humans look. In Proc. IEEE ICCV, 2009. 2,
3, 4
[20] W. Kienzle, F. A.Wichmann, M. O. Franz, and B. Sch¨olkopf.
A nonparametric approach to bottom-up visual saliency. In
Proc. NIPS, pages 689–696, 2006. 2
[21] C. Koch and S. Ullman. Shifts in selective visual attention:
towards the underlying neural circuitry. In Matters of intelligence,
pages 115–141. Springer, 1987. 1
[22] T. Kollenberg, A. Neumann, D. Schneider, T.-K. Tews,
T. Hermann, H. Ritter, A. Dierker, and H. Koesling. Visual
search in the (un) real world: how head-mounted displays
affect eye movements, head movements and target detection.
In Proc. ACM ETRA, pages 121–124. ACM, 2010. 2, 6
[23] V. Laurutis and D. Robinson. The vestibulo-ocular reflex
during human saccadic eye movements. The Journal of Physiology,
373(1):209–233, 1986. 2, 6
[24] O. Le Meur and T. Baccino. Methods for comparing scanpaths
and saliency maps: strengths and weaknesses. Behavior
research methods, 45(1):251–266, 2013. 3
[^25] O. Le Meur, T. Baccino, and A. Roumy. Prediction of the
inter-observer visual congruency (iovc) and application to
image ranking. In Proc. ACM Int. Conf. on Multimedia,
pages 373–382. ACM, 2011. 3
[26] G. Leifman, D. Rudoy, T. Swedish, E. Bayro-Corrochano,
and R. Raskar. Learning gaze transitions from depth
to improve video saliency estimation. arXiv preprint
arXiv:1603.03669, 2016. 2
[27] G. Li and Y. Yu. Visual saliency based on multiscale deep
features. In Proc. IEEE CVPR, pages 5455–5463, 2015. 2
[28] R. Liu, J. Cao, Z. Lin, and S. Shan. Adaptive partial differential
equation learning for visual saliency detection. In Proc.
IEEE CVPR, pages 3866–3873, 2014. 2
[29] T. Liu, Z. Yuan, J. Sun, J. Wang, N. Zheng, X. Tang, and
H.-Y. Shum. Learning to detect a salient object. IEEE Trans.
PAMI, 33(2):353–367, 2011. 2
[30] R. Nakashima, Y. Fang, Y. Hatori, A. Hiratani, K. Matsumiya,
I. Kuriki, and S. Shioiri. Saliency-based gaze prediction
based on head direction. Vision research, 117:59–66,
2015. 2
[31] A. Nuthmann and J. M. Henderson. Object-based attentional
selection in scene viewing. Journal of Vision, 10(8):20, 2010.
4
[32] J. Pan, E. Sayrol, X. Giro-i Nieto, K. McGuinness, and N. E.
O’Connor. Shallow and deep convolutional networks for
saliency prediction. In Proc. IEEE CVPR, June 2016. 2,
7
[^33] K. Ruhland, C. E. Peters, S. Andrist, J. B. Badler, N. I.
Badler, M. Gleicher, B. Mutlu, and R. McDonnell. A review
of eye gaze in virtual agents, social robotics and hci: Behaviour
generation, user interaction and perception. In Computer
Graphics Forum, volume 34, pages 299–326, 2015. 2
[34] D. D. Salvucci and J. H. Goldberg. Identifying fixations and
saccades in eye-tracking protocols. In Proc. ACM ETRA,
pages 71–78. ACM, 2000. 3, 6
[35] V. Tanriverdi and R. J. K. Jacob. Interacting with eye movements
in virtual environments. In SIGCHI, pages 265–272,
2000. 2
[36] A. Torralba, A. Oliva, M. S. Castelhano, and J. M. Henderson.
Contextual guidance of eye movements and attention
in real-world scenes: the role of global features in object
search. Psychological review, 113(4):766, 2006. 2
[37] E. Vig, M. Dorr, and D. Cox. Large-scale optimization of hierarchical
features for saliency prediction in natural images.
In Proc. IEEE CVPR, pages 2798–2805, 2014. 2
[38] L. Wang, H. Lu, X. Ruan, and M.-H. Yang. Deep networks
for saliency detection via local estimation and global search.
In Proc. IEEE CVPR, pages 3183–3192, 2015. 2
[39] M. Yu, H. Lakshman, and B. Girod. A framework to evaluate
omnidirectional video coding schemes. In Proc. ISMAR,
2015. 8
[40] Q. Zhao and C. Koch. Learning saliency-based visual attention:
A review. Signal Processing, 93(6):1401–1407, 2013.
2
[41] R. Zhao,W. Ouyang, H. Li, and X.Wang. Saliency detection
by multi-context deep learning. In Proc. IEEE CVPR, pages
1265–1274, 2015. 2

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>