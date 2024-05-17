##########################
Giant Donut Test (WET-005)
##########################

.. note::

   **This technote is a work-in-progress.**

Abstract
========

This technote relates to the `WET-005 Test <https://jira.lsstcorp.org/browse/SITCOM-1147>`__ from the Active Optics Commissioning (AOS) Test List. This test uses both regular and giant donuts to validate the wavefront estimation pipeline and identify high-frequency mirror errors. Additionally, this test compares the effect of elevation on the optical path differences (opd). This test covers all six filters, as well as three different zenith angles at 0, 30, and 60 degrees. Currently, this data only reflects the Commissioning Camera (ComCam) and will eventually include the main LSST Camera (LSSTCam). 

The notebook used to generate the data for this technote can be found `here <https://github.com/lsst-sitcom/sitcomtn-118>`__.


Background
==========

The process for this test relies on two major AOS software packages, the wavefront estimation pipeline (WEP) and the optical feedback control (OFC). First, both an extrafocal and intrafocal donut is passed through the WEP to obtain the wavefront zernikes of Noll index 4-22. The WEP generally does this by taking advantage of the wavefront senors in each corner of the focal plane of the LSST Camera. At each corner, there is a split CCD with one half above and one half below the focal plane to provide intra- and extrafocal donuts for every exposure. Since ComCam does not have wavefront sensors, exposures were simulated above, below, and equal to the focal plane for each configuration to generate intra- and extrafocal donuts. 


Then, these zernike values are passed through the OFC, which takes zernike values and converts them into an estimation of the input degrees of freedom for the telescope system. There are 50 degrees of freedom for the Simonyi Telescope that reflect the position of the camera and M2 mirror, as well as the bending modes for the M1M3 monolith. These estimated values are then compared back to the input values and compared by elevation. 


Simulation
==========

Exposures were simulating using the `imSim <https://github.com/LSSTDESC/imSim>`__ package. ComCam is one raft consisting of nine CCDs. Since ComCam does not have wavefront sensors, a separate exposure was simulated to generate the intra-, extra-, and in-focus images. Therefore, an entire ComCam exposure was simulated for -7.5mm, -1.5mm, 0mm, 1.5mm, and 7.5mm of defocus. Each defocus was simulated in all six bands, at three zenith angles, for a total of 90 full ComCam exposures. 

The injected, true degrees of freedom were entirely set to zero with the exception of the defocus of the camera, which is the sixth degree of freedom. 

.. figure:: /_static/injectedDOF.png
    :name: Injected DOF
    :target: ../_static/injectedDOF.png
    :alt: Injected degrees of freedom for each camera defocus to generate donuts.
    :width: 70%
    :align: center

    *Figure 1: Injected degrees of freedom for each camera defocus to generate donuts.*





The following conditions were used to simulate the data, with an MJD corresponding to the evening of July 23rd, 2024. 

+--------------+--------------+--------------+
| Zenith Angle |      RA      |     Dec      |
+==============+==============+==============+
|    0.0 deg   | 14:07:46.30  | -26:48:07.50 |
+--------------+--------------+--------------+
|   30.0 deg   | 19:18:10.60  | -45:25:22.70 |
+--------------+--------------+--------------+
|   60.0 deg   | 11:58:29.00  | -85:56:23.60 |
+--------------+--------------+--------------+

All images are in the following location: /sdf/group/rubin/user/rp312/ComCam/Giant_Donut, and are not yet ingested into the AOS butler. 


Results
=======















