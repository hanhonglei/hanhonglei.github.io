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
2. Recently, advances in machine learning and particularly convolutional neuronal networks (CNNs) have fostered the convergence of topdown and bottom-up features for saliency prediction, producing more accurate models [^37][^41][^38][^32][^27].
3. What makes VR different from desktop viewing conditions is the fact that head orientation is used as a natural interface to control perspective.
4. For more information on user behavior in VR, we refer to Ruhland et al. [^33]
5. The paper structure of user data study. In data capture section, use Conditions, Participants, and Procedure.
6. For experiments in VR, 86 users participated in our study (68 male, 18 female, age 17-22).
7. Equipped with a pupil-labs1 stereoscopic eye tracker recording at 120 Hz. The DK2 offers a field of view of 106° x 87°.
8. In desktop condition, they recorded where the users interactively place the virtual camera in the panorama as a proxy for head orientation.
9. We used thresholding based on dispersion and duration of the fixations[^34]. For the VR experiments, we set the minimum duration to 150 ms [^34] and the maximum dispersion to 1° [^1].
10. Tobii eyeX has significant jitter led to skipped fixations.
11. Comparison metrics. We use the Inter-Observer Visual Congruency (IOVC) metric [^25] when investigating whether two groups of users fixated in the same regions of a scene. Measuring the percentage of the other set of fixations that fall in the top 25% most salient regions of that map and vice versa, then
averaging the two percentages. For comparisons between continuous saliency maps, we use the Pearson correlation (CC) metric, and the Earth’s Mover Distance
(EMD).
12. Users tend to fixate around the equator of the panoramas, with very few fixations in latitudes far from the equator.
13. Following a similar procedure to Judd et al. [^19] we analyze the consistency of human fixations by computing the Shannon entropy of the saliency map.
14. The starting condition has little impact on which regions of the scene are attended to over the course of 30 seconds.
15. Our data reveals that head follows gaze with an average delay of 58 ms, where the largest cross-correlation is observed. This is consistent with previous works [^13][^10] reporting delays in head movement when shifting to a non-predictable target.
16. when users are not fixating, head speeds are above average.
17. Whenever head speed falls below the threshold of 19°, the likelihood that the user is currently fixating is high.
18. We conclude that head saliency maps, which are easily obtainable with inertial measurement units, can be a valuable tool to analyze the approximate regions that users attend to in a scene without the need for additional eye-tracking hardware.

## References
[^1]: P. Blignaut. Fixation identification: The optimum threshold for a dispersion algorithm. Attention, Perception, & Psychophysics, 71(4):881–895, 2009. 3

[^25]: O. Le Meur, T. Baccino, and A. Roumy. Prediction of the inter-observer visual congruency (iovc) and application to image ranking. In Proc. ACM Int. Conf. on Multimedia, pages 373–382. ACM, 2011. 3

[^10]: A. Doshi and M. M. Trivedi. Head and eye gaze dynamics during visual attention shifts in complex environments. Journal of Vision, 12(2):9, 2012. 6

[^13]: E. G. Freedman. Coordination of the eyes and head during visual orienting. Experimental brain research, 190(4):369– 387, 2008. 2, 6

[^19]: T. Judd, K. Ehinger, F. Durand, and A. Torralba. Learning to predict where humans look. In Proc. IEEE ICCV, 2009. 2, 3, 4

[^27]: G. Li and Y. Yu. Visual saliency based on multiscale deep features. In Proc. IEEE CVPR, pages 5455–5463, 2015. 2

[^32]: J. Pan, E. Sayrol, X. Giro-i Nieto, K. McGuinness, and N. E. O’Connor. Shallow and deep convolutional networks for saliency prediction. In Proc. IEEE CVPR, June 2016. 2,7

[^33]: K. Ruhland, C. E. Peters, S. Andrist, J. B. Badler, N. I. Badler, M. Gleicher, B. Mutlu, and R. McDonnell. A review of eye gaze in virtual agents, social robotics and hci: Behaviour generation, user interaction and perception. In Computer Graphics Forum, volume 34, pages 299–326, 2015. 2

[^34]: D. D. Salvucci and J. H. Goldberg. Identifying fixations and saccades in eye-tracking protocols. In Proc. ACM ETRA, pages 71–78. ACM, 2000. 3, 6

[^37]: E. Vig, M. Dorr, and D. Cox. Large-scale optimization of hierarchical features for saliency prediction in natural images. In Proc. IEEE CVPR, pages 2798–2805, 2014. 2

[^38]: L. Wang, H. Lu, X. Ruan, and M.-H. Yang. Deep networks for saliency detection via local estimation and global search. In Proc. IEEE CVPR, pages 3183–3192, 2015. 2

[^41]: R. Zhao,W. Ouyang, H. Li, and X.Wang. Saliency detection by multi-context deep learning. In Proc. IEEE CVPR, pages 1265–1274, 2015. 2

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>