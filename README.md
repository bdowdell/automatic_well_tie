# Automated Seismic-to-Well Ties using Dynamic Time Warping approaches

Testing out [dtw-python](https://dynamictimewarping.github.io/python/#quickstart) for automating the seismic-to-well tie process.

[dtw-python @ PyPi](https://pypi.org/project/dtw-python/)

## Abstract

Seismic-to-well ties are a crucial piece in the seismic interpretation workflow.  Well logs represent the ground truth information and present a geoscientist with valuable information.  Without well data, a seismic survey is "uncalibrated" meaning that the rock properties leading to a certain seismic response are unknown.  Once obtained, well data are used to calibrate seismic through the seismic-to-well tie process.  Seismic data, unlike well data, natively lives in the Two-Way Time (TWT) domain.  In order to calibrate the seismic, a Time-Depth relation must be derived so that the interpreter knows when in time a specific subsurface depth occurs.  While there are a set of typical steps which all interpreters generally follow, tying a well to seismic data is almost akin to a time-honored art.  The process is largely deterministic and multiple interpreters can derive multiple ways of tying a well.  In fact, even the same intepreter can come up with multiple ways of tying a well.  In addition to this, the seismic-to-well tie process tends to be tedious and time intensive.  For areas with very few wells within a seismic survey, this is not really a problem, but once the number of wells needing to be tied grows above 20-50, it can be a lengthy endeavor.  Dynamic Time Warping (DTW) is a method of aligning two signals via warping one signal to match the other and is almost instantaeous.  Various authors have already shown the possibilities and value of using DTW in the seismic-to-well tie process.  Here we present another case study implemented using Python and the dtw-python library.

## Introduction

Seismic data, whether 2D or 3D in geometry, is an integral component in the exploration and development of hydrocarbon reservoirs.  Reflection sesimic's native domain is Two-Way Time, which is the time it takes a seismic wave to propagate downward through the subsurface and bounce, or reflect, back up to the surface where it is recorded.  When a well is drilled into the subsurface, the measurement from the surface to the objective is in depth units.  Wells are typically considered to be ground truth information and are used to calibrate the seismic response so we can predict away from the well bore what we may find.  In order to do this, we must first relate the seismic, in Two-Way Time, to the well log, in depth.

The typical method of performing this calibration is the seismic-to-well tie which is commonly referred to as "tying the well".  A seismic-to-well tie is a multistep process that tends to be borderline artistic in an otherwise highly scientific discipline.  While there are some fast-held cardinal rules one should not violate, each interpreter has his or her own method for achieving a seismic-to-well tie.  In general, the steps consist of combining velocity and density measurements from the well (logs) to measure Acoustic Impedance.  Contrasts in acoustic impedance between the different layers give rise to reflection coefficients.  If two bounding layers have very similar acoustic properties (i.e. velocities and densities are similar), then the reflection coefficient will be neglible and the layer may not produce a reflection.  Large contrasts between layers result in large reflection coefficients meaning a reflection will be generated at the interface of those two layers.  Acoustic Impedance describes the layer properties of the subsurface while reflection coefficients describe the interfaces of the layers.  A wavelet is estimated from the seismic in a zone about the well, and this wavelet is then convolved with the reflection coefficients to produce a synthetic seismic trace representing the subsurface sampled directly by the well bore.  The synthetic is then compared to the seismic trace at the well bore's position and is iteratively "tied" by making time adjustments to the synthetic trace either through bulk time shifts or stretching and squeezing the synthetic until an acceptable correlation coefficient between the synthetic and seismic trace is derived.  Once this process is deemed complete by the interpreter, a Time-to-Depth relationship is established tying the seismic, in Two-Way Time, to the well logs, in depth.

***In progress***

## References:

1. Compton, S. and D. Hale, (2014), *Estimating VP/VS ratios using smooth dynamic image warping,* GEOPHYSICS 79: V201-V215 [doi: 10.1190/geo2014-0022.1](https://doi.org/10.1190/geo2014-0022.1).

1. Compton, S. and D. Hale (2013), *Estimating Vp/Vs ratios using smooth dynamic time warping*, Center for Wave Phenomena report, [765](https://cwp.mines.edu/wp-content/uploads/sites/112/2019/11/CWP-765.pdf).

1. Cui, T. and G.F. Margrave (2015), *Seismic-to-well ties by smooth dynamic time warping*, CREWES Research Report, [27](https://www.crewes.org/ForOurSponsors/ResearchReports/2015/CRR201511.pdf).

1. Cui, T. and G.F. Margrave (2015), *Drift time estimation by dynamic time warping*, [GeoConvention New Horizons](https://geoconvention.com/wp-content/uploads/abstracts/2015/088_GC2015_Drift_time_estimation_by_dynamic_time_warping.pdf).

1. Giorgino, S., (2009) *Computing and Visualizing Dynamic Time Warping Alignments in R: The dtw Package*, J. Stat. Soft., 31, [doi: 10.18637/jss.v031.i07](https://doi.org/10.18637/jss.v031.i07).

1. Hale, D., (2013), *Dynamic warping of seismic images*, GEOPHYSICS 78: S105-S115, [doi: 10.1190/geo2012-0327.1](https://doi.org/10.1190/geo2012-0327.1).

1. Hale, D. and S. Compton (2013), *Smooth dynamic warping*, Center for Wave Phenomena Report, [764](https://cwp.mines.edu/wp-content/uploads/sites/112/2018/08/CWP-764-min.pdf).

1. Herrera, R.H. and M. v. d. Baan, (2014), *A semiautomatic method to tie well logs to seismic data*, GEOPHYSICS 79: V47-V54 [doi: 10.1190/geo2013-0248.1](https://doi.org/10.1190/geo2013-0248.1).

1. Herrera, R.H.,  S. Fomel, and M. v. d. Baan, (2014), *Automatic approaches for seismic to well tying*, Interpretation 2: SD9-SD17 [doi: 10.1190/INT-2013-0130.1](https://doi.org/10.1190/INT-2013-0130.1).

1. Herrera, R.H. and M. v. d. Baan, (2012), *Guided seismic-to-well tying based on dynamic time warping*, SEG Technical Program Expanded Abstracts : 1-5 [doi: 10.1190/segam2012-0712.1](https://doi.org/10.1190/segam2012-0712.1).

1. Muñoz, A. and D. Hale, (2015), *Automatic simultaneous multiple well ties*, GEOPHYSICS 80: IM45-IM51 [doi: 10.1190/geo2014-0449.1](https://doi.org/10.1190/geo2014-0449.1).

1. Muñoz, A. and D. Hale (2012), *Automatically tying well logs to seismic data*, Center for Wave Phenomena Report, [725](https://cwp.mines.edu/wp-content/uploads/sites/112/2018/08/CWP725-min.pdf).

1. Tormene, T., Giorgino, S. Quaglini, and M. Stefanelli (2008), *Matching Incomplete Time Series with Dynamic Time Warping: An Algorithm and an Application to Post-Stroke Rehabilitation*, Artificial Intelligence in Medicine, 45(1), 11-34, [doi:10.1016/j.artmed.2008.11.007](https://doi.org/10.1016/j.artmed.2008.11.007).

1. Sakoe, H., and S. Chiba, 1978, *Dynamic programming algorithm optimization for spoken word recognition*, IEEE Transactions on Acoustics, Speech, and Signal Processing, 26, 43–49, [doi: 10.1109/TASSP.1978.1163055.IETABA0096-3518](https://doi.org/10.1109/TASSP.1978.1163055.IETABA0096-3518)

1. Wang, K., J. Lomask, and F. Segovia, (2017), *Automatic, geologic layer-constrained well-seismic tie through blocked dynamic warping*, Interpretation 5: SJ81-SJ90. [doi: 10.1190/INT-2016-0160.1](https://doi.org/10.1190/INT-2016-0160.1)

1. White, R. E., and R. Simm, 2003, *Tutorial: Good practice in well ties*, First Break, 21, 75–83.

1. Wu, X., and G. Caumon, (2017), *Simultaneous multiple well-seismic ties using flattened synthetic and real seismograms*, Geophysics, 82, no. 1, IM13–IM20, [doi: 10.1190/geo2016-0295.1.GPYSA70016-8033](https://doi.org/10.1190/geo2016-0295.1.GPYSA70016-8033).

