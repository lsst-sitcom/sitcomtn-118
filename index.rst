##########################
Giant Donut Test (WET-005)
##########################

Abstract
========

This technote relates to the WET-005 Test from the Active Optics Commissioning (AOS) test list. This test uses both regular and giant donuts to validate the wavefront estimation pipeline and identify high-frequency mirror errors. Additionally, this test compares the effect of elevation on the optical path differences (opd). 


Background
==========

The process for this test relies on two major AOS software packages, the wavefront estimation pipeline (WEP) and the optical feedback control (OFC). First a donut is passed through the WEP to obtain the wavefront zernikes of Noll index 4-22. Then, these zernikes are passed through the OFC to get an estimate of the 50 degrees of freedom of the telescope system. These values are then compared back to the injected values and tested at three different elevations. 
