# voter-demographics

## Getting setup

```
mkvirtualenv voter-demographics
pip install -r requirements.txt
```

## Getting the data

```
curl -O http://thedataweb.rm.census.gov/pub/cps/supps/nov12pub.zip
unzip nov12pub.zip
in2csv -s schema.csv nov12pub.dat > nov12pub.csv
csvcut -c pwsswgt,gestfips,ptdtrace,pehspnon,pesex,prtage,pes1,pes2,pes3,pes4,pes5,pes6,pes7,pes8 nov12pub.csv > data.csv
python make_readable.py
python analyze.py
```

Output is `states.csv`.

**Note:** this file does not include margin-of-error calculations. See the Census Bureau documentation for details on how to calculate this for each derived statistic. In many cases the error can be quite large.

## Sources

* [CPS Data Download FTP](http://thedataweb.rm.census.gov/ftp/cps_ftp.html)
* [National Bureau of Economic Research schema files for CPS data](http://www.nber.org/data/cps_progs.html)

## Documentation

* [Census Bureau Docs for CPS Voter Supplement](http://www.census.gov/prod/techdoc/cps/cpsnov12.pdf)
