Data was obtained by running the following query at http://skyserver.sdss.org/dr16/en/tools/search/sql.aspx

SELECT TOP 500000

p.objid,p.ra,p.dec,p.u,p.g,p.r,p.i,p.z,

p.run, p.rerun, p.camcol, p.field,

s.specobjid, s.class, s.z as redshift,

s.plate, s.mjd, s.fiberid

FROM PhotoObj AS p

JOIN SpecObj AS s ON s.bestobjid = p.objid

WHERE

p.u BETWEEN 0 AND 19.6

AND g BETWEEN 0 AND 20
