Dynamical-mass-of-a-galaxy-cluster
extracting data from the SDSS archive and performing analysis of cluster redshift, characterstic size of cluster an estimating the dynamical mass of the cluster

STEP 1
importing data
the data from the SDSS archive is extracted using the following SQL query
SELECT 
s.objid,sz.ra as ra,sz.dec as dec,pz.z as photoz,pz.zerr as photozerr,sz.z as specz,sz.zerr as 
speczerr,b.distance as proj_sep,s.modelMag_u as umag,s.modelMagErr_u as 
umagerr,s.modelMag_g as gmag,s.modelMagErr_g as gmagerr,s.modelMag_r as rmag, 
s.modelMagerr_r as rmagerr,s.type as obj_type 
 
FROM BESTDR16..PhotoObjAll as s 
JOIN dbo.fGetNearbyObjEq(258.1294,64.0926,10.0) AS b ON b.objID = S.objID 
JOIN Photoz as pz ON pz.objid = s.objid 
JOIN specObjAll as sz ON sz.bestobjid = s.objid 
 
WHERE s.type=3 and sz.z > 0.05 and sz.z < 0.20

STEP 2
to organize the vast astronomical catalog, the data is aggregated
STEP 3
the mean redshift, standard redshift and the maximum and minimum limits are extracted
STEP 4
a histogram and a boxplot are used to plot the distribution of the redshit to the frequency
STEP 5
a new velocity column is created using the formula v=c*z
where c is the speed of light 
and z is the redshift
a histogram is plotted with the velocity and frequency as its axes
STEP 6
![image](https://github.com/user-attachments/assets/d849e56d-9a20-4899-8317-96312fc5368b)
using the above formula, velocity dispersion of the cluster if found

STEP 7
determining the size and mass of the cluster
![image](https://github.com/user-attachments/assets/4c573c2e-410d-4a14-a444-f8de15356d22)


