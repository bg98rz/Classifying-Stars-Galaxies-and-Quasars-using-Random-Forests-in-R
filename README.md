# Classifying Stars, Galaxies, and Quasars using Random Forests in R

Data: SDSS DR14 Data Release, Collected July 2016, 10,000 observations of individual astronomical artefacts.
Availabe via query at: http://skyserver.sdss.org/CasJobs/

In recent years, the advent of sophisticated optical infrastructure has enabled the discovery and analysis of millions of astronomical objects. Artefacts including galaxies, quasars, exoplanets, and supernovae have been shown to be distributed throughout the entire observable universe, each bound to one another by the great gravitational forces which maintain the structure of the cosmic web (Bond et al. 1996).

  Given the ever-increasing sophistication of optical hardware, and greater data storage capabilities, we now have access to a vast archive of astronomical information. Instruments such as the Hubble Telescope, and the SDSS Telescope, generate many terabytes of data each month (National Aeronautics & Space Association, 2014), however, after deployment in 2022; the LSST (Large Synoptic Survey Telescope) alone will generate roughly fifteen terabytes of data per night (LSST Project, 2019). In order to leverage the data for knowledge discovery, it is necessary to explore, classify, and catalogue any artefacts distributed throughout it.

This project explores the automated classification of 3 separate astronomical artefacts, namely galaxy, stars and Quasi-Stellar Objects (Quasar), utilising data from the SDSS DR14 data release. Several random forest models were trained using 75% of the dataset and evaluated using the remaining 25%, ultimately achieving a maximum classification accuracy of roughly 99.3% during testing.

### Class Descriptions

  - Quasi-stellar Object (QSO) = A quasar is an extremely luminous active galactic nucleus, 
                                 in which a supermassive black hole with mass ranging from 
                                 millions to billions of times the mass of the Sun is surrounded 
                                 by a gaseous accretion disk.
                                 
![GitHub Logo](https://scx2.b-cdn.net/gfx/news/hires/2016/1-whatareactiv.jpg)
Image taken by the Hubble Space Telescope of a 5000-light-year-long jet ejected from the active galaxy M87. Credit: NASA/The Hubble Heritage Team (STScI/AURA)                                 
  
  - Galaxy = A galaxy is a gravitationally bound system of billions of stars, 
             stellar remnants, interstellar gas, dust, and dark matter.
     
     
  - Star = A star is an astronomical object consisting of a 
           luminous spheroid of plasma held together by its 
           own gravity.
           
             
### Table Descriptions

  - mtry = A parameter of the random forest model, denotes
           the number of variables to be considered at each
           node in the desicion trees which make up the random
           forests.
           
  
